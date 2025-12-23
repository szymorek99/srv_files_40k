COMMON:
• cache.h : Jak sama nazwa wskazuje, cache (pamięć podręczna).
•	d3dtype.h : dx8 wektory i kolory.
•	service.h : Sekcja, w której definiowane są definicje. Uruchamia makra (#ifdef, #ifndef). Ogólnie, tutaj przypisane są stałe systemowe. Przykład: #define BLOCK_BUFF_FOR_GM itd.
•	VnumHelper.h : Kategoryzacja dostępnych przedmiotów w grze według ich vnum. Na przykład: 71136 to przedmiot związany z Halloween.
•	building.h : Budynki gildii.
•	item_length.h : Zawiera informacje związane z przedmiotami. Flagi, ulepszenia itp.
•	length.h : Zawiera informacje o grze ogólnie. Maksymalna liczba postaci do stworzenia na koncie, rozmiar ekwipunku, maksymalna ilość przechowywanego yang, typy postaci, typy mobów, typy czatów itp.
•	tables.h : Wysyła dane (pakiety) między grą a bazą danych zgodnie z informacjami zdefiniowanymi tutaj. Na przykład: Informacje i przedmioty postaci wprowadzanej do gry, ładowanie protos itp.
•	utils.h : funkcje pomocnicze do konwersji.

DATABASE:
• BlockCountry.cpp/h : Blokowanie według kraju. (Zabrania wchodzenia do gry z miejsc o zakresach IP określonych w bazie danych.)
•	Cache.cpp/h : Zawiera pamięci podręczne. Kiedy kupujesz lub sprzedajesz przedmioty w grze, nie są one od razu zapisywane do bazy danych. Są także przechowywane w pamięci i zapisywane w określonych odstępach czasu. Dlatego, jeśli występuje utrata przedmiotu podczas restartowania gry, jest to spowodowane złym działaniem podczas zamykania gry.
•	ClientManager.h : Ten nagłówek jest dla wielu plików cpp. 
•	ClientManager.cpp : Możemy to nazwać sercem rdzenia db. Przetwarza tutaj dane przychodzące z gry.
•	ClientManagerBoot.cpp : Pobiera dane z bazy danych podczas uruchamiania gry. (przedmioty sprzedawane na NPC, protos, gildie, budynki gildii itp.)
•	ClientManagerEventFlag.cpp : Pobiera te z wartością dwPID równą 0 w tabeli player.quest i definiuje je w grze jako flagi wydarzeń. Przykład: wydarzenie księżycowe, exp_rate itp.
•	ClientManagerGuild.cpp : Plik zawierający operacje takie jak tworzenie, usuwanie gildii i dodawanie członków do gildii.
•	ClientManagerHorseName.cpp : Nie wiem, czy trzeba to wyjaśniać, ale ten plik działa również, gdy nazywasz swojego konia cukierkami dla koni.
•	ClientManagerLogin.cpp : Wysyła niezbędne informacje do gry, gdy użytkownik loguje się i wybiera postać. Zapisuje również informacje z gry do bazy danych. To funkcja większości plików na tej liście. Zapisuje przychodzące dane i wysyła dane. Ten plik zawiera w skrócie informacje o koncie gracza.
•	ClientManagerParty.cpp : Grupy utworzone w grze.
•	ClientManagerPlayer.cpp : Przetwarza informacje o wybranej postaci podczas wchodzenia do gry. Przedmioty, statusy itp.
•	Config.cpp/h : Istnieją pliki takie jak CONFIG i conf.txt w bazie danych twoich plików serwerowych. Odbiera i przetwarza dane w nich zawarte.
•	CsvReader.cpp/h : Plik pomocniczy do czytania plików w twoich plikach serwerowych (item_names.txt, item_proto.txt, mob_names,txt, mob_proto.txt). Ten program postrzega rzeczy oddzielone od siebie każdą kartką jako oddzielne kolumny. Jeśli otworzysz protos programem Excel, zobaczysz, że są one schludnie podzielone na kolumny. (Te pliki są czytane w ClientManagerBoot.cpp, przetwarzane i wysyłane do gry.)
•	DBManager.cpp/h - DBManager_mainline.cpp : Napisane dla zapytań Sql.
•	Grid.cpp/h : W ekwipunku są płytki. Dla nich. Ich zadania są w skrócie następujące. Jeśli w określonym polu jest przedmiot, pobiera jego informacje. Sprawdza, czy przedmiot jest dostępny, czy nie. Możesz przejrzeć plik, aby uzyskać więcej informacji.
•	GuildManager.cpp/h : Gdzie przetwarzane są gildie. Pobiera wszystkie gildie z bazy danych podczas fazy rozruchu. Zapisuje podczas zamykania gry itp.
•	ItemAwardManager.cpp/h : Do odczytu danych w tabeli player.item_award.
•	ItemIDRangeManager.cpp/h : Są identyfikatory przedmiotów w tabeli player.item. Aby zdefiniować te identyfikatory.
•	LoginData.cpp/h : Pobiera kilka informacji o zalogowanym koncie. Status premium itp.
•	main.cpp/h : Nie wiem, czy trzeba to wyjaśniać, ale w projektach C++ jest główny plik. To dla niego. Tutaj zdefiniowane jest użycie wszystkich innych plików. Kroki, które należy podjąć, gdy db jest otwarty, są określone tutaj.
•	Marriage.cpp/h : Małżeństwo.
•	Monarch.cpp/h : Przeszedł, ponieważ ta funkcja nie jest używana.
•	MoneyLog.cpp/h : Rejestry logów yang gracza.
•	PrivManager.cpp/h : Otwieramy upuszczenia w grze. Transakcje z tym związane.
•	ProtoReader.cpp/h : Wymagane do odczytu protos.
•	stdafx.h : To jest plik nagłówkowy znajdujący się w projektach C++.
•	version.cpp : Coś związanego z wersją. W twoich plikach jest plik o nazwie VERSION.txt. Oto kod, który tworzy ten plik i drukuje wersję.

GAME:
•	affect.cpp/h : Efekty w lewym górnym rogu gry. (automatyczne zbieranie yang, zwiększenie ilości exp. itp. Jeśli ktoś ma dodane roski to i one.)
•	affect_flag.h : Zapewnia funkcje do kontrolowania efektów.
•	ani.cpp/h : Miejsce, gdzie kontrolowane są animacje postaci.
•	any_function.h : //Brak, czekam na jakieś informacje 😊
•	arena.cpp/h : Kontrola wymaganych działań dla systemu areny jest tutaj.
•	banword.cpp/h : Filtr przekleństw. (Cenzuruje słowa wpisane w tabeli player.banword.)
•	battle.cpp/h : Plik zawierający dynamikę walki.
•	BattleArena.cpp/h : Arena walk.
•	belt_inventory_helper.h : Gdy nosisz pas, mikstury są umieszczane w małej przestrzeni obok inwentarza. Ten plik kontroluje, które przedmioty można umieścić i ile slotów będzie otwartych. Taki grid 4x4
•	block_country.cpp/h : Kontrole blokowania dla krajów. Na przykład, jeśli chcesz zablokować logowania się do gry z USA. Ten plik ci w tym pomoze xd
•	BlueDragon.cpp/h : Niebieski smok (beran)
•	BlueDragon_Skill.h : Umiejętności niebieskiego smoka. Na przykład strzela do ciebie niebieskim ogniem.
•	buff_on_attributes.cpp/h : Daje bufory twojej postaci zgodnie z czarami przedmiotów, które nosisz.
•	buffer_manager.cpp/h : Zarządza bufami postaci.
•	building.cpp/h : Budynki gildii.
•	castle.cpp/h : W grze były zamki. O nich mowa, ale raczej nie używane.
•	char.h : Funkcje i struktury związane z postaciami i mobami znajdują się tutaj. Ten plik nagłówkowy jest używany przez więcej niż jeden plik cpp. Odpowiednio:
•	char.cpp : Gdzie przechowywane są informacje o postaci. Tutaj przechowywane są nazwa postaci, poziom i wiele innych rzeczy.
•	char_affect.cpp : Efekty postaci. Regeneracja zdrowia itp.
•	char_battle.cpp : Dynamika walki postaci. Obliczane jest, ile obrażeń zadasz, atakując moba lub gracza lub gdy zostaniesz zaatakowany, ustalane jest, ile zdrowia stracisz itp. Oblicza wszystko zależne od twoich umiejętności, statystyk, po poziom eq.
•	char_change_empire.cpp : Gdy zmieniasz flagę za pomocą olejku wygnania, działają funkcje w tym pliku.
•	char_dragonsoul.cpp : System alchemii.
•	char_horse.cpp : Koń, wierzchowce itp.
•	char_item.cpp : Wiele rzeczy, od operacji do wykonywania podczas używania przedmiotów po zarządzanie inwentarzem, znajduje się w tym pliku. Jest to jeden z plików o największej ilości kodu w rdzeniu gry.
•	char_quickslot.cpp : Dodajemy umiejętności i pewne przedmioty do paska zadań poniżej. Wymagane do działania tej funkcji.
•	char_resist.cpp : Efekty, które będą działać na twoją postać, takie jak trucizna i krwawienie.
•	char_skill.cpp : Umiejętności postaci.
•	char_state.cpp : Stany mobów, agresja, npc itp.
•	char_manager.cpp/h : Tutaj przechowywane są wszystkie informacje o postaciach.
•	check_server.h : Związane z kontrolą klucza serwera.
•	cipher.cpp/h : Związane z szyfrowaniem.
•	ClientPackageCryptInfo.cpp/h : Związane z zaszyfrowanymi pakietami.
•	cmd.h : Funkcje wymagane do uruchomienia, gdy piszemy polecenie. Ten plik nagłówkowy jest używany w więcej niż jednym pliku cpp. Po kolei:
•	cmd.cpp : Plik, w którym ustawiane są polecenia i niezbędne uprawnienia do ich użycia.
•	cmd_emotion.cpp : Emocje.
•	cmd_general.cpp : Polecenia ogólnie używane poza kodem GM. Polecenia tutaj mogą być również używane przez graczy.
•	cmd_gm.cpp : Komendy, których mogą używać GM-y.
•	cmd_oxevent.cpp : Pytania na OX.
•	config.cpp/h : W plikach kanałów twoich plików jest plik CONFIG. 
•	constants.cpp/h : Niektóre stałe. Na przykład: Obszar, w którym znajdują się stawki doświadczenia wymagane do listy zaklęć, awansu gildii i postaci.
•	crc32.cpp/h : Logika crc.
•	cube.cpp/h : System rzemiosła. Tworzenie mikstur, transformacje przedmiotów itp.
•	db.cpp/h : Związane z bazą danych. Wykonanie zapytania itp.
•	desc.cpp/h : Funkcje wymagane do wysyłania i odbierania pakietów.
•	desc_client.cpp/h : Ustanowienie połączenia gniazda, gdy połaczony jest nowy gracz.
•	desc_manager.cpp/h : Plik zawierający podłączonych graczy, konta i informacje o postaciach.
•	desc_p2p.cpp/h : Otwieranie i zamykanie nowego połączenia p2p.
•	dev_log.cpp/h : Komunikaty na czacie po włączeniu testserver.
•	dragon_soul_table.cpp/h : Stopnie kamienia alchemicznego.
•	DragonLair.cpp/h : Chodzi o niebieskiego smoka na dungu.
•	DragonSoul.cpp/h : System alchemii.
•	dungeon.cpp/h : Dla map zawartych w game99. Tworzenie wirtualnego rdzenia po zalogowaniu, przypisywanie graczy do tego samego obszaru w grupach itp.
•	empire_text_convert.cpp/h : Komunikacja nie jest możliwa z graczami, którzy nie są w tym samym królestwie. W miarę polepszania się jego języka, stopniowo stawało się to zrozumiałe. Ten plik reguluje, jak będzie wyglądał tekst, który piszesz, dla przeciwnego gracza.
•	entitiy.cpp/h entitiy_view.cpp : Aby wyświetlić zasoby (postać, mob itp.)
•	event.cpp/h : Do edycji zdarzeń czasowych.
•	exchange.cpp/h : Handel między graczami. (okno handlowe)
•	file_loader.cpp/h : Do czytania plików tekstowych w twoich plikach.
•	fishing.cpp/h : Wędkarstwo.
•	gm.cpp/h : Funkcje związane z GM-em
•	guild.cpp/h : Aby uzyskać dostęp do informacji o gildii.
•	guild_manager.cpp/h : Obszar, w którym przechowywane są wszystkie wspomnienia gildii.
•	guild_war.cpp : Wojna gildii.
•	horse_rider.cpp/h : Związane z jazdą konną.
•	horsename_manager.cpp/h : Nazwy koni graczy, którzy dodają specjalną nazwę do swoich koni.
•	input.h : Wymagane do przetwarzania pakietów. Ten plik nagłówkowy jest używany w więcej niż jednym pliku. Kolejno:
•	input_auth.cpp : Operacje logowania.
•	input_db.cpp : Transakcje do wykonania w wyniku komunikacji między DB a grą. 
•	input_login.cpp : Procedury do wykonania po wejściu do gry po wybraniu postaci.
•	input_main.cpp : Ten plik służy do relacji między klientem a serwerem. Pakiety przychodzące od klienta są analizowane tutaj, a akcje do podjęcia są określane. Na przykład, dodajesz przyjaciół. Wpisujesz nazwę osoby w kliencie i wysyłasz. Pakiet trafia tutaj, a dane wysłane do CInputMain::Messenger są przesyłane do funkcji zdefiniowanej do dodawania przyjaciół. Po dokonaniu niektórych sprawdzeń serwer wysyła dane do MessengerManager w celu dodania przyjaciela.
•	input_p2p.cpp : Używane w komunikacji między rdzeniami. Na przykład coś napisałeś na czacie
•	input_udp.cpp : Implementacja TCP/UDP.
•	ip_ban.cpp/h : Aby zapobiec łączeniu się z zbanowanymi adresami IP do gry.
•	item.h : Plik nagłówkowy zawierający funkcje i struktury związane z przedmiotami. Ten plik jest używany w więcej niż jednym pliku cpp. Kolejno:
•	item.cpp : Informacje o przedmiotach w grze są przechowywane tutaj. Powiedzmy, że zalogowałeś się do gry. Klasa w item.cpp zostanie utworzona dla każdego z twoich przedmiotów i dodana do wektorów w menedżerze.
•	item_addon.cpp : Uszkodzenia spowodowane przez przedmiot itp.
•	item_attribute.cpp : Plik zawierający operacje takie jak dodawanie zaklęć do przedmiotów, uzyskiwanie informacji o zaklęciach itp.
•	item_manager.h : Ten plik nagłówkowy jest używany w więcej niż jednym pliku cpp. Kolejno:
•	item_manager.cpp : Tu kontrolowane są wszystkie przedmioty. Tworzenie, znajdowanie, usuwanie przedmiotów.
•	item_manager_idrange.cpp : Utworzenie nowego identyfikatora, gdy tworzony jest nowy przedmiot.
•	item_manager_private_types.h : Związane z dropami. chyba
•	item_manager_read_tables.cpp : Czyta pliki txt w twoim pliku, takie jak mob_drop_item.txt , special_item_group.txt , common_drop_item.txt .
•	limit_time.h : Istnieją stałe związane z ustawieniami czasu.
•	locale.cpp : Istnieją zmiany w serwerze od kraju do kraju. Jeśli serwer jest ustawiony na polskę, istnieją funkcje pomocnicze do pobierania danych z katalogu locale/poland.
•	locale_service.cpp/h : Istnieją zdefiniowane stałe kraje. Określone jest, które pliki zostaną załadowane w zamian za te kraje. Jeśli ustawione jest na Polske, katalog locale/poland jest ładowany.
•	log.cpp/h : Dodaje zapis działań wykonanych w grze do bazy danych.
•	login_data.cpp/h : Przechowuje informacje o zalogowanych użytkownikach.
•	login_sim.h : Wysyła pakiety do bazy danych dla logowania.
•	lua_incl.h : To raczej cos z lua i questami.
•	lzo_manager.cpp/h : Związane z szyfrowaniem Lzo.
•	lzoconf.h : chętnie się dowiem
•	lzodefs.h : chętnie się dowiem
•	main.cpp : Projekty C++ posiadają plik główny. Użycie wszystkich innych plików jest zdefiniowane tutaj. Kroki do podjęcia podczas otwierania gry są tutaj określone.
•	map_location.cpp/h : Do lokalizacji map. Gdy podajesz aktualną lokalizację, otrzymuje indeks mapy, itp.
•	MarkManagar.h : Używane w wielu plikach cpp. Dodany plik dla ikon gildii. Inne używane pliki to:
•	MarkConvert.cpp : Konwersja obrazów.
•	MarkManager.cpp : Przechowuje informacje o wszystkich gildiach, które dodały obraz gildii.
•	MarkImage.cpp/h : Tworzenie, usuwanie, itp. obrazów ikon gildii.
•	marriage.cpp/h : System małżeński.
•	messenger_manager.cpp/h : Lista znajomych.
•	minilzo.h : Oddzielny plugin dla Lzo.
•	mining.cpp/h : Górnictwo.
•	mob_manager.cpp/h : Sloty w grze.
•	monarch.cpp/h : Funkcja nie uzywana, usunięte na Entry
•	motion.cpp/h : Związane z ruchami slotów i graczy. Odczytuje pliki w share/data.
•	object_allocator.h : Związane z klasami. Dodawanie obiektów, usuwanie itp.
•	over9refine.cpp/h : Transformacja.
•	OXEvent.cpp/h : System wydarzeń OX.
•	p2p.cpp/h : Połączenie P2P. Wykonuje operacje takie jak tworzenie nowego połączenia, jego zakończenie, wysyłanie pakietów, itp.
•	packet.h : Zawiera schematy danych do przesyłania między klientem a bazą danych
•	packet_info.cpp/h : Określa, które funkcje zostaną uruchomione, gdy pakiet dotrze od klienta do bazy danych.
•	party.cpp/h : Grupy graczy.
•	PetSystem.cpp/h : Klasyczne zwierzęta domowe.
•	polymorph.cpp/h : Transformacja.
•	priv_manager.cpp/h : Stawki dropu zgodnie z flagami.
•	protocol.h : Szyfruje dane wysyłane za pomocą pakietu.
•	pvp.cpp/h : Pojedynek między dwoma graczami.
•	quest.h : Zawiera pewne stałe i struktury dla questów.
•	questevent.cpp/h : Timery używane w naszych questach.
•	questlua.cpp/h : Odczytuje skompilowane questy.
•	questmanager.h : Zazwyczaj używany w plikach, gdzie dodawane są funkcje questu. Lista funkcji questa
•	questlua_affect.cpp : Operacje efektów przy użyciu funkcji questów.
•	questlua_arena.cpp : Plik odnośnie areny walk.
•	questlua_ba.cpp : Chyba to samo co na górze?
•	questlua_building.cpp : Dla budynków gildii. Kupowanie ziemi itp.
•	questlua_danceevent.cpp : Tańce postaci.
•	questlua_dragonlair.cpp : Dla kryształowego smoka
•	questlua_dragonsoul.cpp : System alchemii
•	questlua_dungeon.cpp : Funkcje zadania dla dungeonow. (Specjalne ogłoszenie dla tej mapy, liczba mobów, masowe teleportacje, itp.)
•	questlua_game.cpp : Funkcje zadania wymagane dla gry. (Otwieranie magazynu itp.)
•	questlua_global.cpp : Globalnie używane funkcje zadania. (drukowanie syserr, uzyskiwanie nazwy przedmiotu, dodawanie pytań o ox, itp.)
•	questlua_guild.cpp : Dodane funkcje zadania dla gildii.
•	questlua_horse.cpp : Dodane funkcje zadania dla konia.
•	questlua_item.cpp : Dodane funkcje zadania dla przedmiotów.
•	questlua_marriage.cpp : Małżeństwo.
•	questlua_mgmt.cpp : Nie używane
•	questlua_monarch.cpp : Nie używane
•	questlua_npc.cpp : Dodane funkcje zadania dla NPC, Mob.
•	questlua_party.cpp : Dodane funkcje zadania dla grup graczy.
•	questlua_pc.cpp : Dodane funkcje zadania dla gracza. (uzyskiwanie poziomu, informacje o yang, itp.)
•	questlua_pet.cpp : Dla petów.
•	questlua_quest.cpp : Questy.
•	questlua_speedserver.cpp : chętnie się dowiem
•	questlua_target.cpp : NPC gdy masz jakies zadanie ma taka strzalke nad glowa. Miedzy innymi o to chodzi xd
•	questmanager.cpp : Przechowuje wszystkie zadania w pamięci. Gdy gracz wchodzi do gry, wysyła informacje o zadaniu.
•	questnpc.cpp/h : Dla NPC i ich questów
•	questpc.cpp/h : Questy gracza
•	refine.cpp/h : Ulepszanie
•	regen.cpp/h : Regeny potworów itd
•	safebox.cpp/h : Magazyn.
•	sectree.cpp/h : Encje i mapy.
•	sectree_manager.cpp/h : Przechowuje wszystkie mapy i encje w pamięci.
•	sequence.cpp/h : Zakodowany kod wysyłany do weryfikacji w pakietach. Ta funkcja jest wyłączona w niektórych plikach.
•	shop.cpp/h : Sprzedaż NPC i rynki graczy.
•	shop_manager.cpp : Przechowuje informacje o sprzedaży NPC i wszystkich rynkach graczy.
•	shopEx.cpp/h : Tworzenie sprzedaży NPC.
•	shutdown_manager.cpp/h : Dla polecenia /shutdown.
•	skill.cpp/h : Umiejętności.
•	skill_power.cpp/h : Poziom umiejętności.
•	start_position.cpp/h : Domyślne punkty odrodzenia zgodnie z królestwem, w którym się znajdujesz.
•	stdafx.h : Jest to plik nagłówkowy znajdujący się w projektach C++.
•	target.cpp/h : Strzałki na NPC.
•	test_window.cpp : Dla plików server_attr znajdujących się w plikach mapy.
•	text_file_loader.cpp/h : Istnieje wiele plików txt zawierających ustawienia gry w plikach.
•	threeway_war.cpp/h : Wojna trójstronna. (3 gildie ?) Chetnie się dowiem
•	typedef.h : Wektory
•	unique_item.h : Podtypy typu Unikalny przedmiot.
•	utils.cpp/h : Istnieją funkcje do odbierania wartości wysyłanych za pomocą polecenia.
•	version.cpp : Coś związanego z wersją. Istnieje plik o nazwie VERSION.txt w Twoich plikach. To kod, który tworzy ten plik i drukuje wersję.
•	war_map.cpp/h : Strefy wojenne.
•	wedding.cpp/h : Mapa ślubna.
•	xmas_event.cpp/h : Wydarzenie noworoczne.
