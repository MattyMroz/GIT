# 📝 Notatki Git

## 🚀 Inicjalizacja i konfiguracja

### `git init`
Inicjalizuje nowe repozytorium Git w bieżącym katalogu.
- `--bare` - tworzy repozytorium bez katalogu roboczego (do współdzielenia)

### `git clone [url]`
Pobiera kopię istniejącego repozytorium.
- `--depth [liczba]` - płytki klon z ograniczoną historią
- `--branch [nazwa]` - klonuje określoną gałąź

### `git config`
Konfiguruje ustawienia Git.
- `git config --global user.name "Imię Nazwisko"` - ustawia nazwę użytkownika
- `git config --global user.email "email@example.com"` - ustawia email
- `--list` - wyświetla wszystkie ustawienia
- `git config --local user.name "Imię Nazwisko"` - ustawia nazwę użytkownika lokalnie
- `git config --local user.email "email@example.com"` - ustawia email lokalnie

## 💾 Podstawowe operacje

### `git add [pliki]`
Dodaje zmiany do poczekalni (staging area).
- `git add .` - dodaje wszystkie zmiany
- `git add -p` - interaktywne dodawanie fragmentów zmian

### `git commit`
Zapisuje zmiany w repozytorium.
- `git commit -m "wiadomość"` - commit z krótką wiadomością
- `git commit -am "wiadomość"` - dodaje wszystkie śledzone pliki i commituje
- `--amend` - modyfikuje ostatni commit

### `git status`
Pokazuje stan plików w repozytorium.
- `-s` lub `--short` - skrócony format wyjścia

### `git log`
Wyświetla historię commitów.
- `--oneline` - skrócony format (jedna linia na commit)
- `--graph` - graficzna reprezentacja historii
- `--pretty=format:"%h %an %s"` - niestandardowy format wyjścia

## 🌿 Gałęzie (branches)

### `git branch`
Zarządza gałęziami.
- `git branch [nazwa]` - tworzy nową gałąź
- `git branch -d [nazwa]` - usuwa gałąź
- `git branch -a` - wyświetla wszystkie gałęzie (lokalne i zdalne)

### `git checkout`
Przełącza między gałęziami lub przywraca pliki.
- `git checkout [nazwa-gałęzi]` - przełącza na gałąź
- `git checkout -b [nazwa-gałęzi]` - tworzy i przełącza na nową gałąź
- `git checkout [plik]` - przywraca plik do stanu z ostatniego commita

### `git switch` (nowsze alternatywa dla checkout)
Przełącza między gałęziami.
- `git switch [nazwa-gałęzi]` - przełącza na gałąź
- `git switch -c [nazwa-gałęzi]` - tworzy i przełącza na nową gałąź

### `git merge [gałąź]`
Łączy zmiany z innej gałęzi do aktualnej.
- `--no-ff` - zawsze tworzy commit scalający
- `--squash` - łączy wszystkie commity w jeden

## 🔄 Synchronizacja z repozytorium zdalnym

### `git remote`
Zarządza zdalnymi repozytoriami.
- `git remote add [nazwa] [url]` - dodaje zdalne repozytorium
- `git remote -v` - wyświetla zdalne repozytoria

### `git fetch`
Pobiera zmiany ze zdalnego repozytorium bez scalania.
- `git fetch --all` - pobiera ze wszystkich zdalnych repozytoriów

### `git pull`
Pobiera i scala zmiany ze zdalnego repozytorium.
- `git pull --rebase` - pobiera i nakłada lokalne zmiany na wierzch

### `git push`
Wysyła lokalne zmiany do zdalnego repozytorium.
- `git push -u origin [gałąź]` - wysyła i ustawia upstream
- `--force` - wymusza push (ostrożnie!)

## 🔄 Cofanie zmian

### `git reset`
Cofa zmiany do określonego punktu.
- `git reset --soft HEAD~1` - cofa ostatni commit, zachowuje zmiany w poczekalni
- `git reset --hard HEAD~1` - cofa ostatni commit, usuwa zmiany
- `git reset [plik]` - usuwa plik z poczekalni

### `git revert [commit]`
Tworzy nowy commit, który cofa zmiany z określonego commita.

### `git restore`
Przywraca pliki do określonego stanu.
- `git restore [plik]` - odrzuca zmiany w pliku roboczym
- `git restore --staged [plik]` - usuwa plik z poczekalni

## 🧹 Porządkowanie

### `git stash`
Tymczasowo odkłada zmiany.
- `git stash push -m "opis"` - odkłada zmiany z opisem
- `git stash pop` - przywraca ostatnio odłożone zmiany
- `git stash list` - wyświetla listę odłożonych zmian

### `git clean`
Usuwa nieśledzone pliki.
- `git clean -n` - pokazuje, co zostanie usunięte
- `git clean -f` - usuwa nieśledzone pliki
- `git clean -fd` - usuwa nieśledzone pliki i katalogi

## 🔍 Zaawansowane

### `git rebase`
Zmienia bazę gałęzi.
- `git rebase [gałąź]` - przenosi commity na wierzch innej gałęzi
- `git rebase -i HEAD~3` - interaktywny rebase ostatnich 3 commitów

### `git cherry-pick [commit]`
Aplikuje zmiany z określonego commita.

### `git tag`
Zarządza tagami (oznaczeniami).
- `git tag [nazwa]` - tworzy lekki tag
- `git tag -a [nazwa] -m "opis"` - tworzy tag z adnotacją
- `git tag -l` - wyświetla tagi

## 📊 Przykładowy workflow Git

1. `git clone https://github.com/user/repo.git` - klonowanie repozytorium
2. `git checkout -b feature/nowa-funkcja` - utworzenie nowej gałęzi
3. *edycja plików*
4. `git status` - sprawdzenie zmian
5. `git add .` - dodanie zmian do poczekalni
6. `git commit -m "Dodano nową funkcję"` - zatwierdzenie zmian
7. `git push -u origin feature/nowa-funkcja` - wysłanie gałęzi do zdalnego repo
8. *utworzenie Pull Request w interfejsie GitHub/GitLab/Bitbucket*
9. `git checkout main` - powrót do głównej gałęzi
10. `git pull` - pobranie najnowszych zmian
11. `git merge feature/nowa-funkcja` - scalenie zmian (alternatywnie przez PR)
12. `git push` - wysłanie zmian do zdalnego repozytorium
13. `git branch -d feature/nowa-funkcja` - usunięcie lokalnej gałęzi po scaleniu

## 🔄 Alternatywny workflow z rebase

1. `git clone https://github.com/user/repo.git` - klonowanie repozytorium
2. `git checkout -b feature/nowa-funkcja` - utworzenie nowej gałęzi
3. *edycja plików*
4. `git add .` - dodanie zmian
5. `git commit -m "Dodano nową funkcję"` - zatwierdzenie zmian
6. `git checkout main` - przełączenie na główną gałąź
7. `git pull` - pobranie najnowszych zmian
8. `git checkout feature/nowa-funkcja` - powrót do gałęzi funkcji
9. `git rebase main` - przeniesienie zmian na wierzch głównej gałęzi
10. `git push -f origin feature/nowa-funkcja` - wymuszenie aktualizacji zdalnej gałęzi
11. *utworzenie Pull Request*
12. `git checkout main` - powrót do głównej gałęzi po zaakceptowaniu PR
13. `git pull` - pobranie scalonych zmian
14. `git branch -d feature/nowa-funkcja` - usunięcie lokalnej gałęzi