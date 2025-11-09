FROM public.ecr.aws/lambda/python:3.13

# install uv
COPY --from=ghcr.io/astral-sh/uv:latest /uv /uvx /bin/

# copy pyproject.toml and install dependencies
COPY pyproject.toml ${LAMBDA_TASK_ROOT}/
RUN uv sync --frozen

# copy handler
COPY handler.py ${LAMBDA_TASK_ROOT}/

# set python path and handler
ENV PYTHONPATH=${LAMBDA_TASK_ROOT}
CMD ["handler.resize_handler"]
