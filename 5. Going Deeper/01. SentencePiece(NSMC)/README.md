# AIFFEL Campus Online 5th Code Peer Review Templete
- 코더 : 김범준
- 리뷰어 : 홍서이

# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [o] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
  > 네이버 영화 리뷰 데이터에 hannanum, kkma, komoran, mecab, okt 토크나이저를 이용해 데이터 토큰화를 진행한 뒤 긍부정 분류기를 완성하였다.

- [o] 주석을 보고 작성자의 코드가 이해되었나요?
  >  주석이 달린 셀도 있고 아닌 셀도 있다.
```python
    s = spm.SentencePieceProcessor()
    s.Load('korean_spm.model')
 
    # SentencePiece를 활용한 sentence -> encoding
    tokensIDs = s.EncodeAsIds('아버지가방에들어가신다.')
    print(tokensIDs)

    # SentencePiece를 활용한 sentence -> encoded pieces
    print(s.SampleEncodeAsPieces('아버지가방에들어가신다.',1, 0.0))
    
    # SentencePiece를 활용한 encoding -> sentence 복원
    print(s.DecodeIds(tokensIDs))
```
- [o] 코드가 에러를 유발할 가능성이 없나요?
  > 없어보인다.
- [o] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  > 문장 길이를 제한하는 과정에서 적절하게 코드를 작성하였다.
```python
max_len = 150
min_len = 10

# 길이 조건에 맞추어 문장 선택
filtered_corpus = [s for s in cleaned_corpus if (len(s) < max_len) & (len(s) >= min_len)]

sentence_length = np.zeros((max_len), dtype=int)

for sen in filtered_corpus:
    sentence_length[len(sen)-1] += 1

plt.bar(range(max_len), sentence_length, width=1.0)
plt.title("Sentence Length Distribution")
plt.show()
```
- [o] 코드가 간결한가요?
  > 반복해서 사용하는 코드의 경우 함수형을 사용하여 잘 작성하였다.
```
def tokenize(corpus):  # corpus: Tokenized Sentence's List
    tokenizer = tf.keras.preprocessing.text.Tokenizer(filters='')
    tokenizer.fit_on_texts(corpus)
    
    tensor = tokenizer.texts_to_sequences(corpus)
    tensor = tf.keras.preprocessing.sequence.pad_sequences(tensor, padding='post')
    
    return tensor, tokenizer
```

# 참고 링크 및 코드 개선
- 제가 참고한 블로그 글입니다! 전체적인 텍스트데이터 처리 과정이 서술되어있어 참고하면 좋을 것 같습니다.
- https://haystar.tistory.com/11#toc14.
