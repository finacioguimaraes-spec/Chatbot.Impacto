# Chatbot.Impacto
Um chatbot para o Colegio impacto demorei um pouco mas foi pois precisava corrigir erros



import os
import streamlit as st
from openai import OpenAI

st.set_page_config(page_title="Chatbot Impacto", page_icon="🤖")
st.write("# Chatbot Impacto")

if "lista_mensagens" not in st.session_state:
    st.session_state["lista_mensagens"] = []

api_key = os.getenv("OPENAI_API_KEY")

if not api_key:
    st.error("A variável de ambiente OPENAI_API_KEY não foi definida.")
    st.stop()

modelo_ia = OpenAI(api_key=api_key)

arquivo = st.file_uploader("Selecione um arquivo")

for mensagem in st.session_state["lista_mensagens"]:
    with st.chat_message(mensagem["role"]):
        st.write(mensagem["content"])

texto_usuario = st.chat_input("Cole a sua pergunta aqui ou escreva")

if texto_usuario:
    mensagem_usuario = {"role": "user", "content": texto_usuario}
    st.session_state["lista_mensagens"].append(mensagem_usuario)

    with st.chat_message("user"):
        st.write(texto_usuario)

    try:
        response = modelo_ia.chat.completions.create(
            model="gpt-4o-mini",
            messages=st.session_state["lista_mensagens"]
        )

        texto_resposta_ia = response.choices[0].message.content

        mensagem_ia = {"role": "assistant", "content": texto_resposta_ia}
        st.session_state["lista_mensagens"].append(mensagem_ia)

        with st.chat_message("assistant"):
            st.write(texto_resposta_ia)

    except Exception as e:
        st.error(f"Erro ao chamar a API: {e}")import os
import streamlit as st
from openai import OpenAI

st.set_page_config(page_title="Chatbot Impacto", page_icon="🤖")
st.write("# Chatbot Impacto")

if "lista_mensagens" not in st.session_state:
    st.session_state["lista_mensagens"] = []

api_key = os.getenv("OPENAI_API_KEY")

if not api_key:
    st.error("A variável de ambiente OPENAI_API_KEY não foi definida.")
    st.stop()

modelo_ia = OpenAI(api_key=api_key)

arquivo = st.file_uploader("Selecione um arquivo")

for mensagem in st.session_state["lista_mensagens"]:
    with st.chat_message(mensagem["role"]):
        st.write(mensagem["content"])

texto_usuario = st.chat_input("Cole a sua pergunta aqui ou escreva")

if texto_usuario:
    mensagem_usuario = {"role": "user", "content": texto_usuario}
    st.session_state["lista_mensagens"].append(mensagem_usuario)

    with st.chat_message("user"):
        st.write(texto_usuario)

    try:
        response = modelo_ia.chat.completions.create(
            model="gpt-4o-mini",
            messages=st.session_state["lista_mensagens"]
        )

        texto_resposta_ia = response.choices[0].message.content

        mensagem_ia = {"role": "assistant", "content": texto_resposta_ia}
        st.session_state["lista_mensagens"].append(mensagem_ia)

        with st.chat_message("assistant"):
            st.write(texto_resposta_ia)

    except Exception as e:
        st.error(f"Erro ao chamar a API: {e}")import os
import streamlit as st
from openai import OpenAI

st.set_page_config(page_title="Chatbot Impacto", page_icon="🤖")
st.write("# Chatbot Impacto")

if "lista_mensagens" not in st.session_state:
    st.session_state["lista_mensagens"] = []

api_key = os.getenv("OPENAI_API_KEY")

if not api_key:
    st.error("A variável de ambiente OPENAI_API_KEY não foi definida.")
    st.stop()

modelo_ia = OpenAI(api_key=api_key)

arquivo = st.file_uploader("Selecione um arquivo")

for mensagem in st.session_state["lista_mensagens"]:
    with st.chat_message(mensagem["role"]):
        st.write(mensagem["content"])

texto_usuario = st.chat_input("Cole a sua pergunta aqui ou escreva")

if texto_usuario:
    mensagem_usuario = {"role": "user", "content": texto_usuario}
    st.session_state["lista_mensagens"].append(mensagem_usuario)

    with st.chat_message("user"):
        st.write(texto_usuario)

    try:
        response = modelo_ia.chat.completions.create(
            model="gpt-4o-mini",
            messages=st.session_state["lista_mensagens"]
        )

        texto_resposta_ia = response.choices[0].message.content

        mensagem_ia = {"role": "assistant", "content": texto_resposta_ia}
        st.session_state["lista_mensagens"].append(mensagem_ia)

        with st.chat_message("assistant"):
            st.write(texto_resposta_ia)

    except Exception as e:
        st.error(f"Erro ao chamar a API: {e}")
