FROM python:3.9

WORKDIR /app

EXPOSE 5050

COPY Pipfile Pipfile.lock ./ 

# --- Pip SSL bypass (pipenv kurulumu için) ---
RUN pip config set global.trusted-host "pypi.org pypi.python.org files.pythonhosted.org"

# Pipenv kurulumu
RUN pip install pipenv

# requirements.txt üret (yeni Pipenv sürümü)
RUN pipenv requirements > requirements.txt

# Paketleri yükle
RUN pip install -r requirements.txt

# --- Requests ve Python SSL verify bypass ---
ENV PYTHONHTTPSVERIFY=0  

# >>> BURASI YANLIŞTI — DÜZELTTİM <<<
COPY . ./

CMD ["python", "main.py"]
