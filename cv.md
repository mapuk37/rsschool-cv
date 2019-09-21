**Artem Markov**  

**Contact Info:**  
* email: mr.venezuela37@gmail.com
* phone number: +79038892399
* skype: Aptemb4uk

**Summary:**    

My main goal is to change my profession. I have been working as electric engineer for some years. Some months ago I've realised that I'm tired of it and began to take an interest in programming. Firstly I've finished some courses of VBA for Excel and made some macros for my previous job. Then took an interest in web development and tried to study myself. Recently my friend advised me your courses and I think that it would help me to achieve my goal.

**Skills:**  
* HTML
* CSS
* JavaScript
* Python
* VBA

I know the basics of all these languages. As for IDEs I've used **WebStorm**, **PyCharm** and built-in **VB IDE in Excel**.

**Code Examples:**  

Here's a metrics server that I've made on Python courses.

    import asyncio

    METRIC = dict()

    class ClientServerProtocol(asyncio.Protocol):
      def connection_made(self, transport):
          self.transport = transport

      def data_received(self, data):
          self.transport.write(self._process(data.decode('utf-8').strip('\r\n')).encode('utf-8'))
          req = data.decode('utf-8').strip('\r\n').split(' ')
          cmd = req[0]

      def _process(self, command):
          req = command.split(' ')
          if req[0] == 'get':
              return self._process_get(req[1])
          elif req[0] == 'put':
              return self._process_put(req[1], req[2], req[3])
          else:
              return 'error\nwrong command\n\n'

      def _process_get(self, key):
          resp = 'ok\n'
          if key == '*':
              for key, values in METRIC.items():
                  for value in values:
                      resp = resp + key + ' ' + value[1] + ' ' + value[0] + '\n'
          else:
              if key in METRIC:
                  for value in METRIC[key]:
                      resp = resp + key + ' ' + value[1] + ' ' + value[0] + '\n'

          return resp + '\n'

      def _process_put(self, key, value, timestamp):
          if key == '*':
              return 'error\nkey cannot contain *\n\n'
          if not key in METRIC:
              METRIC[key] = list()
          if not (timestamp, value) in METRIC[key]:
              METRIC[key].append((timestamp, value))
              METRIC[key].sort(key=lambda tup: tup[0])
          return 'ok\n\n'

    def run_server(host, port):
      loop = asyncio.get_event_loop()
      coroutine = loop.create_server(ClientServerProtocol, host, port)
      server = loop.run_until_complete(coroutine)

      try:
          loop.run_forever()
      except KeyboardInterrupt:
          pass

      server.close()
      loop.run_until_complete(server.wait_closed())
      loop.close()

**Experience:**  

To tell the truth I have nothing to demonstrate connected with web development because it's my first course and previously I've just read theory and made excercises online. I have been trying to make some site by myself but it's far from finishing and now I feel that I would not have enough time to finish it. I have some macros on VB and some more tasks on Python made by me on Coursera intensive but it's not connected with web so I won't give a link for it. 

**Education:**  

* VBA macros at https://www.specialist.ru
* Introduction to Python at https://www.coursera.org 

**English:**  

I've been studying English from the kindergarten. Then I've entered english intensive class at school. After school I continued to learn English myself. So now I can say that my English level is Upper-Intermediate.
