FROM python:3
ENV PYTHONUNBUFFERED 1
RUN mkdir /code
WORKDIR /code
COPY requirements.txt /code/
RUN pip install -r requirements.txt
COPY /project /code/
CMD ["/usr/local/bin/gunicorn", "--bind", "127.0.0.1:8000", "/code/project/MYPROJECT.wsgi:application"]