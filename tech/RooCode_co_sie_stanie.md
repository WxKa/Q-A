#### prompt:

  co się stanie z zadaniu nadrzędnym, jeśli zadanie nadrzędne (Orchestrator, Architect ...) użyje new_task, czyli wywoła zadanie podrzędne, a to zadanie zakończy się i nie wywoła attempt_completion, w sensie, że zadanie nadrzędne zawsze oczekuje na zakończenie zadania podrzędnego
  
#### response:

  When a parent task (like Orchestrator or Architect) uses new_task to create a sub-task, the parent task's execution is paused, and control is transferred to the new sub-task. The parent task will wait for the sub-task to complete.

  If a sub-task finishes its work but does not explicitly call attempt_completion, the system will not register the sub-task as fully completed. This means the parent task will remain in a waiting state, as it expects a clear signal of the sub-task's resolution. For the parent task to resume or acknowledge the sub-task's outcome, the sub-task must use attempt_completion to signal its successful conclusion.
  
  
#### uwagi:

  tu pozwolę sobie dodać mój komentarz: I RooCode, krótko mówiąc wisi.
  zainteresowało mnie to, bo w sieci są informacje, że RooCode nieraz robi zwiechę i trzeba całe zadanie zaczynać od początku.
