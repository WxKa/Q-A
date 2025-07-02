#### RooCode Doctor

* to raczej poradnik niż aplikacja w jaki sposób możemy używać narzędzi dla programistów do zupełnie innych celów np. medycznych
* na pierwszy ogień RooCode, jak to zainstalować jest tu: https://www.youtube.com/watch?v=_Rs1kmaUlIQ
* z pewnością da się też to zrobić we wszystkich innych narzędziach: Cline, Aider; półpłatne: Cursor, Windsurf, Continue; płatne: Kilo, Devin, które oferują tryb 'Ask' i 'Code',
   z tym, że te półpłatne też mają ograniczenia co do używania bardziej zaawansowanych modeli LLM, wymagają opłat czyli tzw. wersji premium, dla snobów to nie lada gratka więc polecam,

#### I co dalej

* w VSCode, z zainstalowanym rozszerzeniem Roo-Code (prev. Cline) wybieramy katalog, w którym będą nasze dane, najlepiej w plikach txt, czyli czytelne, na początek można skorzystać z katalogu test w tym repozytorium,
* w VSCode klikamy z lewej strony na kangura i na dole mamy prompt,
* wybieramy tryb 'Ask', co jest istotne aby nie robić tego w trybie 'Orchestrator' albo 'Architect' bo wtedy Roo zacznie pisać jakieś programy i nie będziemy wiedzieli co z tym zrobić,
* zadajemy pytania do danych, które są w tym katalogu np. podaj listę pacjentów,
* możemy również powiedzieć: zapisz do pliku recepty.txt recepty z pliku leczenie.md
   - ponieważ w trybie 'Ask' nie można zapisywać, RooCode grzecznie poprosi, aby przełączył się w tryb 'Code', żeby to zapisać, można się na to ewentualnie zgodzić, ale tryb 'Code' zostaje, więc wracamy do 'Ask'.
* **DANE SĄ WYSYŁANE NA ZEWNĄTRZ** więc rzeczywiste dane muszą być wcześniej zanonimizowane.

#### Internals
* ostatnie analizy wykazują, że RooCode jednak nie używa serwera MCP w komunikacji z LLM, czyli AI, ale mimo wszystko może odczytywać wszystkie pliki z tego katalogu i je zapisywać,
* zapytałem się AI, jakim cudem AI może dociągać brakujące pliki:
   - Proces ten obejmuje podjęcie przez LLM decyzji o odczytaniu pliku, wywołanie narzędzia read_file ze ścieżką pliku, wykonanie żądania przez RooCode (ma zaimplementowane to read_file), a następnie zwrócenie zawartości pliku (lub błędu) do LLM w kolejnej wiadomości użytkownika,
   - Tworzy to ciągłą pętlę żądanie-odpowiedź, która pozwala LLM zebrać niezbędne informacje z systemu plików.
* podobnie jest z write_to_file, search_file, list_files, czyli LLM'y mają mechanizmy do pobierania lokalnych plików użytkownia i ich zapisywania lokalnie u użytkownika,
* żeby być precyzyjnym podaję pełen zestaw tzw: "tool_use": "execute_command", "read_file", "fetch_instructions", "write_to_file", "apply_diff", "search_files", "insert_content", "search_and_replace", "list_files", "list_code_definition_names", "browser_action", "use_mcp_tool", "access_mcp_resource", "ask_followup_question", "attempt_completion", "switch_mode",  "codebase_search", "new_task" na razie bez komentarza,
* na tej podstawie można stwierdzić, że MCP do niczego nie jest tu potrzebne, a komendy "use_mcp_tool" i "access_mcp_resource" sugerują, że MCP może być gdzieś dostępne w tle jako jakieś uzupełnienie, wersja rozszerzona,
* i co więcej, kanał komunikacyjny do obsługi MCP jest już stworzony więc w zasadzie po stronie LLM nic więcej nie trzeba robić - ale to będzie jeszcze zweryfikowane
