import os
from flask import Flask, render_template, request
from flask_socketio import SocketIO, emit
from datetime import datetime

# Flask ищет шаблоны в папке templates
app = Flask(__name__, template_folder='templates')
socketio = SocketIO(app, cors_allowed_origins="*")

users = {}

@app.route('/')
def index():
    return render_template('chat.html')

@socketio.on('connect')
def connect():
    print('Клиент подключился:', request.sid)

@socketio.on('disconnect')
def disconnect():
    if request.sid in users:
        username = users.pop(request.sid)
        emit('message', {'user': 'Система', 'text': f'{username} вышел из чата'}, broadcast=True)
    print('Клиент отключился:', request.sid)

@socketio.on('join')
def join(data):
    username = data.get('username', 'Аноним')
    users[request.sid] = username
    emit('message', {'user': 'Система', 'text': f'{username} вошёл в чат'}, broadcast=True)

@socketio.on('chat_message')
def chat_message(data):
    username = users.get(request.sid, 'Аноним')
    text = data.get('text', '')
    time = datetime.now().strftime('%H:%M')
    emit('message', {'user': username, 'text': text, 'time': time}, broadcast=True)

if __name__ == '__main__':
    # Render задаёт порт через переменную окружения
    port = int(os.environ.get("PORT", 5000))
    socketio.run(app, host='0.0.0.0', port=port)
