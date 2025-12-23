# Metin2 Server Source – Documentation Overview

Ten dokument opisuje strukturę oraz przeznaczenie kluczowych plików źródłowych serwera Metin2.  
Podział został wykonany zgodnie z głównymi modułami projektu: **COMMON**, **DATABASE** oraz **GAME**.

---

## 📁 COMMON

Pliki współdzielone pomiędzy różnymi komponentami serwera.

- **cache.h** – Mechanizmy pamięci podręcznej (cache).
- **d3dtype.h** – Struktury DX8 (wektory, kolory).
- **service.h** – Definicje systemowe, makra (`#ifdef`, `#define`), np. `BLOCK_BUFF_FOR_GM`.
- **VnumHelper.h** – Kategoryzacja przedmiotów według vnum (np. eventowe – Halloween).
- **building.h** – Budynki gildii.
- **item_length.h** – Flagi, ulepszenia i właściwości przedmiotów.
- **length.h** – Globalne stałe gry (sloty postaci, ekwipunek, yang, typy mobów, czaty).
- **tables.h** – Struktury pakietów wymienianych między grą a bazą danych.
- **utils.h** – Funkcje pomocnicze i konwersje.

---

## 🗄️ DATABASE

Logika serwera bazy danych – synchronizacja stanu gry z MySQL.

### Core
- **main.cpp / main.h** – Punkt startowy DB Core.
- **ClientManager.cpp / .h** – Serce DB Core, obsługa komunikacji z game.
- **ClientManagerBoot.cpp** – Ładowanie danych przy starcie (protos, NPC shop, gildie).
- **ClientManagerLogin.cpp** – Obsługa logowania, danych konta i postaci.
- **DBManager.cpp / .h** – Obsługa zapytań SQL.
- **Config.cpp / .h** – Parsowanie plików `CONFIG`, `conf.txt`.

### Cache & Data
- **Cache.cpp / .h** – Buforowanie danych przed zapisem do DB.
- **Grid.cpp / .h** – System slotów (ekwipunek, dostępność itemów).
- **ItemAwardManager.cpp / .h** – Obsługa tabeli `player.item_award`.
- **ItemIDRangeManager.cpp / .h** – Zakresy ID przedmiotów.
- **LoginData.cpp / .h** – Informacje o stanie konta (premium itp.).

### Gildie i relacje
- **ClientManagerGuild.cpp**
- **GuildManager.cpp / .h**
- **Marriage.cpp / .h**
- **MoneyLog.cpp / .h**

### Inne
- **BlockCountry.cpp / .h** – Blokowanie logowań po IP/kraju.
- **CsvReader.cpp / .h** – Czytanie plików `.txt` (protos).
- **ProtoReader.cpp / .h** – Parser protosów.
- **version.cpp** – Generowanie `VERSION.txt`.

---

## 🎮 GAME

Główny rdzeń gry – logika rozgrywki, postacie, questy, systemy.

### Postacie & Walka
- **char.h / char.cpp** – Definicja postaci i mobów.
- **char_battle.cpp** – Obliczanie obrażeń.
- **char_affect.cpp** – Efekty (regen, buffy).
- **char_skill.cpp** – Umiejętności.
- **char_item.cpp** – Operacje na przedmiotach (jeden z największych plików).
- **char_dragonsoul.cpp** – Alchemia.
- **char_horse.cpp** – System koni.

### System walki i PvP
- **battle.cpp / .h**
- **pvp.cpp / .h**
- **arena.cpp / .h**
- **BattleArena.cpp / .h**

### Przedmioty
- **item.cpp / item.h** – Logika przedmiotów.
- **item_manager.cpp / .h** – Tworzenie, usuwanie, wyszukiwanie itemów.
- **item_attribute.cpp** – Atrybuty przedmiotów.
- **refine.cpp / .h** – Ulepszanie.
- **cube.cpp / .h** – Crafting.

### Questy & Lua
- **questmanager.cpp / .h** – Zarządzanie questami.
- **questlua.cpp / .h** – Integracja Lua.
- **questlua_pc.cpp** – Funkcje gracza.
- **questlua_item.cpp** – Przedmioty w questach.
- **questlua_dungeon.cpp** – Dungeon API.
- **questlua_guild.cpp**, **questlua_party.cpp**, **questlua_pet.cpp**
- **questevent.cpp / .h** – Timery questów.

### Komunikacja & Sieć
- **desc.cpp / .h** – Wysyłanie i odbiór pakietów.
- **input_main.cpp** – Obsługa pakietów klienta.
- **input_db.cpp** – Komunikacja game ↔ DB.
- **p2p.cpp / .h** – Połączenia między rdzeniami.
- **packet.h** – Definicje pakietów.
- **protocol.h** – Szyfrowanie pakietów.

### Gildie & Społeczność
- **guild.cpp / .h**
- **guild_manager.cpp / .h**
- **guild_war.cpp**
- **messenger_manager.cpp / .h**

### Mapy & Eventy
- **sectree.cpp / .h** – Mapy i encje.
- **dungeon.cpp / .h**
- **regen.cpp / .h**
- **OXEvent.cpp / .h**
- **xmas_event.cpp / .h**
- **threeway_war.cpp / .h**

### Inne systemy
- **shop.cpp / .h** – Sklepy NPC i graczy.
- **exchange.cpp / .h** – Handel.
- **safebox.cpp / .h** – Magazyn.
- **fishing.cpp / .h**
- **mining.cpp / .h**
- **PetSystem.cpp / .h**
- **wedding.cpp / .h**
- **shutdown_manager.cpp / .h**

---

## ℹ️ Informacje końcowe

- Projekt napisany w **C++**
- Architektura oparta o **multi-core (game / db / p2p)**
- Duże wykorzystanie **cache**, **pakietów binarnych** oraz **Lua (questy)**

---

> 📌 Dokument ma charakter edukacyjny i służy do nauki architektury serwera Metin2.
