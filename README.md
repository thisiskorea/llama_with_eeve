# llama_with_eeve

다음 링크에서 사용할 수 있습니다: https://huggingface.co/kikikara/llama_with_eeve_new_03_150m


모델별 평가 점수

![image](https://github.com/user-attachments/assets/7d8ba4f0-5d3d-46cf-9bbe-d72bf2b48678)



학습 과정 파이프라인

![image](https://github.com/user-attachments/assets/1814f813-85d4-4456-9178-3480c72e42d4)


모델 학습에 사용한 dataset

![image](https://github.com/user-attachments/assets/83c6709f-c698-4b11-9ea0-9761f0cb68ed)

모델 사용 예시
```python
from transformers import AutoTokenizer, AutoModelForCausalLM, pipeline

tokenizer = AutoTokenizer.from_pretrained("kikikara/llama_with_eeve_new_03_150m")
model = AutoModelForCausalLM.from_pretrained("kikikara/llama_with_eeve_new_03_150m")

question = "너는 누구야?"

prompt = f"### System:\n당신은 비도덕적이거나, 성적이거나, 불법적이거나 또는 사회 통념적으로 허용되지 않는 발언은 하지 않습니다.\n사용자와 즐겁게 대화하며, 사용자의 응답에 가능한 정확하고 친절하게 응답함으로써 최대한 도와주려고 노력합니다.\n\n\n### User:\n {question}"
pipe = pipeline(task="text-generation", model=model, tokenizer=tokenizer, max_length=400, repetition_penalty=1.12)
result = pipe(prompt)

print(result[0]['generated_text'])```


