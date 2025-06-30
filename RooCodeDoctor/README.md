#### RooCode Doctor

* to raczej poradnik niż aplikacja w jaki sposób możemy używać narzędzi dla programistów do zupełnie innych celów np. medycznych
* na pierwszy ogień RooCode, jak to zainstalować jest tu: https://www.youtube.com/watch?v=_Rs1kmaUlIQ

#### I co dalej

* w VSCode, z zainstalowanym rozszerzeniem Roo-Code (prev. Cline) wybieramy katalog, w którym będą nasze dane, najlepiej w plikach txt, czyli czytelne, na początek można skorzystać z katalogu test w tym repozytorium,
* w VSCode klikamy z lewej strony na kangura i na dole mamy prompt,
* wybieramy tryb 'Ask', co jest istotne aby nie robić tego w trybie 'Orchestrator' albo 'Architect' bo wtedy Roo zacznie pisać jakieś programy i nie będziemy wiedzieli co z tym zrobić,
* zadajemy pytania do danych, które są w tym katalogu np. podaj listę pacjentów,
* RooCode ma wbudowany serwer MCP za pomocą którego zdalny LLM, czyli AI, może odczytywać wszystkie pliki z tego katalogu ale też zapisywać
* i możemy np. powiedzieć: zapisz do pliku recepty.txt recepty z pliku leczenie.md
   - ponieważ w trybie 'Ask' nie można zapisywać, RooCode grzecznie poprosi, aby przełączył się w tryb 'Code', żeby to zapisał, można się na to ewentualnie zgodzić, ale tryb 'Code' zostaje, więc wracamy do 'Ask'.
* **DANE SĄ WYSYŁANE NA ZEWNĄTRZ** więc rzeczywiste dane muszą być wcześniej zanonimizowane.
