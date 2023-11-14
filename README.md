# PaddleOCR - Komorebi FORK

## Train

Para entrenar los modelos es necesario contar con lo ssiguientes archivos:
- `Archivo de configuración`: este archivo contiene la información sobre el modlo, los datos de entrenamiento y los hiperpárametros de este. Un ejemplo de archivo (utilizado para entrenar el OCR de matrícula) [configs/rec/rec_license_plates_ctc.yml](configs/rec/rec_license_plates_ctc.yml).
- Diccionario de caracteres que contienen los caractere que se utilizarán para entrenar el modelo. Esta variable debe ser modificada en el archivo de configuración `.yml`. 
- Conjunto de datos en el siguiente formato:
  - Carpeta de imágenes
  - Archivo `.txt` de dos columnas separadas por `/t` donde la primera columna será el nombre de la imagen y la segunda columna el texto correspondiente. Estos datos deben ser modificados en el archivo de configuración mencionado anteriormente. 


Una vez creados estos archivos, lanzaremos el script de entrenamiento:

```python
python3 tools/train.py -c <config/path/file.yml>
```

## Export models
Una vez entrenado un modelo es necesario exportarlo a modo inferencia. Para poder exportar el modelo,utilizaremos el siguiente script:

```python
python3 tools/export_model.py -c  <config/path/file.yml> -o Global.pretrained_model="path/tp/trained/model" Global.save_inference_dir="<destionation/path/for/inference/model"
```

## Predict
Evidentemente se puede utilizar un pipeline custom para hacer inferencia de los modelos. No obstante, PaddleOCR ofrece un script que puede usarse de forma sencilla para hacer una pre-validación:


```python
python tools/infer/predict_rec.py --rec_model_dir="inference/model/path" --image_dir="image/to/predict/path" --rec_char_dict_path="char/dict/path"
```
