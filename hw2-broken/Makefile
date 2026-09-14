# На Windows make по умолчанию берёт cmd.exe (или случайный sh.exe из PATH),
# и `bash` в рецептах уезжает в WSL — там нет uv и conda-окружения, все
# проверки падают с кодом 127. Явно фиксируем SHELL на Git Bash.
# Короткий путь (PROGRA~1) — чтобы пробел в «Program Files» не ломал SHELL.
ifeq ($(OS),Windows_NT)
SHELL := C:/PROGRA~1/Git/bin/bash.exe
endif

.PHONY: install inspect check clean

install:
	uv sync

inspect:
	uv run python -m src.inspect_model

check:
	bash tests/check.sh

clean:
	rm -rf docs/report.json src/__pycache__ tests/__pycache__
