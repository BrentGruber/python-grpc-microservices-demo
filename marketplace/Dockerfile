FROM python

RUN mkdir /service
COPY proto/ /service/proto/
COPY marketplace/ /service/marketplace/
WORKDIR /service/marketplace
RUN python -m pip install --upgrade pip
RUN python -m pip install -r requirements.txt
RUN python -m grpc_tools.protoc -I ../proto --python_out=. --grpc_python_out=. ../proto/recommendations.proto

EXPOSE 5000
ENV FLASK_APP=marketplace.py
ENV FLASK_RUN_HOST=0.0.0.0
ENTRYPOINT ["python", "-m", "flask", "run"]