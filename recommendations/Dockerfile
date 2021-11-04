FROM python

RUN mkdir /service
COPY proto/ /service/proto/
COPY recommendations/ /service/recommendations/
WORKDIR /service/recommendations
RUN python -m pip install --upgrade pip
RUN pip install pipenv
RUN pipenv install --system --deploy
RUN python -m grpc_tools.protoc -I ../proto --python_out=. --grpc_python_out=. ../proto/recommendations.proto

EXPOSE 50051
ENTRYPOINT ["python", "recommendations.py"]