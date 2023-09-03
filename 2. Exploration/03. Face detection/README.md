# AIFFEL Campus Online 5th Code Peer Review Templete
- 코더 : 김범준
- 리뷰어 : 이수봉


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [X] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
  
- [X] 주석을 보고 작성자의 코드가 이해되었나요?
  > 코드블럭 마다 주석으로 코드의 설명이 있었습니다.
- [X] 코드가 에러를 유발할 가능성이 없나요?
  > 에러를 유발할 가능성이 있는 코드가 없었습니다.
- [X] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  > 작성한 코드에 대해서 한줄씩 설명을 해었습니다.
- [X] 코드가 간결한가요?
  > 불필요한 코드 없이 간결하였습니다.

# 예시
1. 코드의 작동 방식을 주석으로 기록합니다.
2. 코드의 작동 방식에 대한 개선 방법을 주석으로 기록합니다.
3. 참고한 링크 및 ChatGPT 프롬프트 명령어가 있다면 주석으로 남겨주세요.
```python

for dlib_rect, landmark in zip(dlib_rects, list_landmarks):
    print(landmark[32])
    x = landmark[32][0]
    y = int(landmark[30][1] + (landmark[33][1] - landmark[30][1]) / 3)
    w = h = dlib_rect.width()
    print (f'(x,y) : ({x},{y})')
    print (f'(w,h) : ({w},{h})')
    
# Assigning the midpoint of the nose to the variable x and y
# Assigning the width of the original image to the variable w and h
# To accurately determine the midpoint of the nose, I made adjustments to the variable 'y'

#-------------------------------------------------------------------------

# for dlib_rect, landmark in zip(dlib_rects, list_landmarks):
#     print(landmark[32])
#     x = landmark[32][0]
#     y = landmark[32][1] - dlib_rect.height()//2
#     w = h = dlib_rect.width()
#     print (f'(x,y) : ({x},{y})')
#     print (f'(w,h) : ({w},{h})')

# The codes below are the one before the adjustment of variable 'y'

refined_x = x - w // 2 + 20
refined_y = y - h // 2

print(f'(refined_x, refined_y): ({refined_x},{refined_y})')

# The code was iteratively executed to observe the applied location of the sticker, 
# and the refined values of refined_x and refined_y were adjusted manually for experimentation purposes.
```

# 참고 링크 및 코드 개선
```python
# 다양한 이미지에서 적용이 가능하도록 refined_x, refined_y의 값이 상숫값이 아니라 이미지에 맞게 수정되면 좋을 것 같음

for dlib_rect, landmark in zip(dlib_rects, list_landmarks):
    print(landmark[32])
    w = h = dlib_rect.width()
    x = x = landmark[30][0] - w//2
    y = (landmark[30][1]+landmark[33][1])//2 - h//2
    print (f'(x,y) : ({x},{y})')
    print (f'(w,h) : ({w},{h})')

```
