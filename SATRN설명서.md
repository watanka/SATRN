## SATRN 모델 사용 설명서
--------------------

### 데이터 구성
-----------
0. 전처리 (tool.ipynb 참고)
    - chk_rot : rotate된 이미지 필터
    - find_file_w_spc : 특수문자 처리 e.g) (1),(2),(3),...(20) 목차를 나타내는 숫자들 특수문자로 변환

1. 원본 데이터(full size)를 .json 또는 .txt annotation 기준으로 자른다. 
    output 형태 imgname-0.jpg & imgname-0.txt (이미지 파일과 txt파일 이름 같음)
    ```text
    annot.txt
    imgname.txt [label]
    ```
2. tfrecord화
src/create_tfrecord_v2.py 사용

3. 학습 시 데이터 경로를 도커에 마운트 시키거나 ./data에 직접 넣어 사용.

```bash
$src python create_tfrecord_v2.py --gt_exp=[gt_dir/*.txt] --output_dir=[output_dir] --dataset_name=[datasetname]
```
- gt 디렉토리는 *.txt 끝날 것
- output_dir는 끝에 '/' 없이

### 모델 구성
-------------
- 모델 configuration은 src/configs/SATRN.yaml 확인.
- charset은 src/resources/krn_charset.txt 사용. 



