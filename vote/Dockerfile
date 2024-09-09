FROM python:latest

RUN apt-get update

ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

WORKDIR /vote

COPY requirements.txt /vote
RUN pip install --upgrade pip
RUN pip install -r requirements.txt

# FROM base AS dev
RUN pip install watchdog
ENV FLASK_ENV=development
# CMD ["python", "app.py"]

COPY . /vote

EXPOSE 90

CMD ["gunicorn", "app:app", "-b", "0.0.0.0:80", "--log-file", "-", "--access-logfile", "-", "--workers", "4", "--keep-alive", "0"]
