# Purpose
대화의 문맥을 분석해 감정 상태를 판단한다.

turn1, trun2, turn3 세 개의 대화를 분석하여 감정 상태를 판단한다.

https://competitions.codalab.org/competitions/19790



# Data
## Data example
turn1 | turn2 | turn3 | label
|:--------|:--------:|:--------:|:--------:|
Hahah i loved it | Yay! Glad you loved it X3 😅 | You always make us happy | happy
Say something about you dear | You Know | Yes | others
See the thing is i love a girl but i am afraid to confess that to her | "go ahead. You feel good and are matured enough to manage relationships, ga." | But the thing is she doesnt even wants to talk with me :/ | sad
What is there for Lunch..?? | Coffee coffee and more coffee | Fuck off fuck off and more fuck off | angry
who are they | i'm in.! Whats up.? | nothing up only down | sad
My one main friend backstabbed me a few weeks ago | Awesome. What house did you get in? | Excuse I just told you a sad story and your gonna say awesome wtf is wrong with you | angry
Do u know cooking ? | Ofcourse Bro... I simply love cooking. ☺😊👍😍 | Nice | others

## Data 설명
* label은 turn3를 기준으로 매겨졌다.
* label은 총 4개로 happy, sad, angry, others로 나누어진다.



# Model 
1. BI_LSTM 
   * CuDNN 사용한 Bi LSTM 레이어 2개 쌓았다.
   * Glove Pre-trained Embedding 사용

2. TextCNN 
   * filter_size : 3, 4, 5
   * filter_num : 128
   * Glove Pre-trained Embedding 사용
   
3. ELMo
   * tf-hub에서 제공하는 embedding matrix 사용
   * embedding size가 1024 차원이다.