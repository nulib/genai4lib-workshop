FROM python:3
RUN /usr/sbin/useradd -m -U jupyter-user
RUN /usr/local/bin/pip install jupyterlab
COPY --chown=jupyter-user:jupyter-user ./notebooks/requirements.txt /var/notebooks/requirements.txt
RUN /usr/local/bin/pip install -r /var/notebooks/requirements.txt
RUN apt update -qq && apt install -y nodejs npm && apt clean
COPY --chown=jupyter-user:jupyter-user ./notebooks /var/notebooks
ADD http://www.cs.columbia.edu/CAVE/databases/SLAM_coil-20_coil-100/coil-20/coil-20-proc.zip /tmp/coil-20-proc.zip
RUN mkdir -p /var/coil-20 && cd /var/coil-20 && unzip /tmp/coil-20-proc.zip && rm /tmp/coil-20-proc.zip
USER jupyter-user
WORKDIR /home/jupyter-user
COPY --chown=jupyter-user:jupyter-user ./jupyter/jupyter_lab_config.py /home/jupyter-user/.jupyter/jupyter_lab_config.py
COPY --chown=jupyter-user:jupyter-user ./jupyter/db_conf.json /home/jupyter-user/work/.database/db_conf.json
COPY --chown=jupyter-user:jupyter-user ./jupyter/user-settings /home/jupyter-user/.jupyter/lab/user-settings
ENTRYPOINT ["jupyter", "lab", "--config", "/home/jupyter-user/.jupyter/jupyter_lab_config.py", "--notebook-dir", "/var/notebooks/"]