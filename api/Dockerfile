FROM python:3.9

WORKDIR /app

EXPOSE 5050

COPY Pipfile Pipfile.lock ./

# Pip SSL bypass (pipenv kurulumu için)
RUN pip config set global.trusted-host "pypi.org pypi.python.org files.pythonhosted.org"
RUN pip config set global.cert false

# Pipenv kurulumu
RUN pip install pipenv

# requirements.txt üret (yeni Pipenv sürümünde)
RUN pipenv requirements > requirements.txt

# Paketleri yükle
RUN pip install -r requirements.txt

COPY . .

CMD ["python", "main.py"]
