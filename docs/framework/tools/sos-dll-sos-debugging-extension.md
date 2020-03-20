---
title: SOS.dll (rozšíření ladění SOS)
ms.date: 03/30/2017
helpviewer_keywords:
- debugging extensions
- SOS debugging extensions
- SOS.dll
ms.assetid: 9ac1b522-77ab-4cdc-852a-20fcdc9ae498
ms.openlocfilehash: 4c3a7f2798791f0c8a6b752f06bc2937fc970d40
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75715735"
---
# <a name="sosdll-sos-debugging-extension"></a>SOS.dll (rozšíření ladění SOS)

Rozšíření ladění SOS (SOS.dll) pomáhá ladit spravované programy v sadě Visual Studio a v ladicím programu systému Windows (WinDbg.exe) tím, že poskytuje informace o interním prostředí CLR (Common Language Runtime). Tento nástroj vyžaduje, aby měl projekt povoleno nespravované ladění. Knihovna SOS.dll je automaticky nainstalována společně s rozhraním .NET Framework. Chcete-li v sadě Visual Studio používat soubor SOS.dll, nainstalujte [sady WDK (Windows Driver Kit).](/windows-hardware/drivers/download-the-wdk)

## <a name="syntax"></a>Syntaxe

```console
![command] [options]
```

## <a name="commands"></a>Příkazy

|Příkaz|Popis|
|-------------|-----------------|
|**AnalyzeOOM** (**ao**)|Zobrazí informace pro poslední nedostatek paměti (OOM), ke kterým došlo na požadavek přidělení haldy uvolňování paměti. (Při uvolňování paměti serveru se případná chyba v důsledku vyčerpání paměti (OOM) zobrazí u každé haldy uvolňování paměti zvlášť.)|
|**BPMD** [**-nofuturemodule**\<] [*název metody* názvu> \<*modulu*>] [**-md**  < `MethodDesc`>] **-list** **-clear** \< *pending breakpoint number*> **-clearall**|Vytvoří ve zvoleném modulu zarážku u určené metody.<br /><br /> Pokud nebyl načten zvolený modul ani metoda, počká tento příkaz na notifikaci, že byl modul načten a zkompilován za běhu (JIT) před vytvořením zarážky.<br /><br /> Seznam čekajících zarážek můžete spravovat pomocí možností **-list**, **clear**a **-clearall:**<br /><br /> Možnost **-list** generuje seznam všech čekajících zarážek. Pokud má čekající zarážka nenulovou hodnotu ID modulu, pak je tato zarážka určena pro konkrétní funkci v konkrétním načteném modulu. Pokud má čekající zarážka nulovou hodnotu ID modulu, pak je tato zarážka určena modulům, které ještě nebyly načteny.<br /><br /> Pomocí možnosti **-clear** nebo **-clearall** odeberte čekající zarážky ze seznamu.|
|**CLRStack** [**-a**] [**-l**] [**-p**] [**-n**]|Poskytne trasování zásobníku pouze pro spravovaný kód.<br /><br /> Možnost **-p** zobrazí argumenty spravované funkce.<br /><br /> Možnost **-l** zobrazuje informace o místních proměnných v rámci. Rozšíření ladění SOS nemůže načíst místní názvy, takže výstup pro \<místní názvy je ve formátu *hodnota* *místní adresy* >  **=** \<>.<br /><br /> Možnost **-a**(all) je zkratka pro **-l** a **-p** v kombinaci.<br /><br /> Možnost **-n** zakáže zobrazení názvů zdrojových souborů a čísel řádků. Pokud ladicí program má zadánu možnost SYMOPT_LOAD_LINES, bude nástroj SOS vyhledávat symboly pro každý spravovaný rámec a v případě úspěchu zobrazí odpovídající název zdrojového souboru a číslo řádku. **Parametr -n** (Bez čísel řádků) lze zadat pro zakázání tohoto chování.<br /><br /> Nástroj SOS Debugging Extension nezobrazuje přechodné rámce pro platformy založené na architekturách x64 a IA-64.|
|**ComState**|Seznam modelu apartment modelu modelu `Context` modelu MODELU MODELU MODELU modelu MODELU pro každé vlákno a ukazatel, pokud je k dispozici.|
|**DumpArray** [**-start** \< *startIndex*>] [**-délka** \< *délky*>] [**-details**] [**-nofields**] \<adresa *objektu pole*><br /><br /> -nebo-<br /><br /> **DA** [**-start** \< *startIndex*>] [**-délka** \< *délky*>] [**-detail**] [**-nofields**] adresa *objektu pole*>|Prozkoumá prvky objektu pole (typ array).<br /><br /> Možnost **-start** určuje počáteční index, ve kterém mají být zobrazeny prvky.<br /><br /> Volba **-length** určuje, kolik prvků se má zobrazit.<br /><br /> Možnost **-details** zobrazí podrobnosti o elementu pomocí formátů **DumpObj** a **DumpVC.**<br /><br /> Možnost **-nofields** zabraňuje zobrazení polí. Tato možnost je k dispozici pouze v případě, že je zadána možnost **-detail.**|
|*Adresa sestavení* **DumpAssembly** \<>|Zobrazí informace o sestavení.<br /><br /> **Příkaz DumpAssembly** uvádí více modulů, pokud existují.<br /><br /> Adresu sestavení můžete získat pomocí příkazu **DumpDomain.**|
|*Adresa Třídy EEClass* **dumpclass** \<>|Zobrazí informace `EEClass` o struktuře přidružené k typu.<br /><br /> Příkaz **DumpClass** zobrazí statické hodnoty polí, ale nezobrazuje hodnoty nestatických polí.<br /><br /> Pomocí příkazu **DumpMT**, **DumpObj**, **Name2EE**nebo `EEClass` **Token2EE** získáte adresu struktury.|
|**DumpDomain** \<[*> adresy domény]*|Vyjmenovává <xref:System.Reflection.Assembly> každý objekt, který <xref:System.AppDomain> je načten v rámci zadané adresy objektu.  Při volání bez parametrů, **DumpDomain** příkaz <xref:System.AppDomain> uvádí všechny objekty v procesu.|
|**DumpHeap** [**-stat**] [**-strings**] [**-short**] [**-min** \< *size*>] [**-max** \< *size*>] [**-thinlock**] [**-startAtLowerBound**] [**-mt** \< *MethodTable address*>] [**-type** \<partial type *name*>][*start* [*end*]]|Zobrazí informace o haldě uvolnění paměti a statistiky uvolňování objektů.<br /><br /> **Příkaz DumpHeap** zobrazí upozornění, pokud zjistí nadměrnou fragmentaci v haldě systému uvolňování paměti.<br /><br /> Možnost **-stat** omezuje výstup na souhrn statistického typu.<br /><br /> Možnost **-strings** omezuje výstup na souhrn statistické hodnoty řetězce.<br /><br /> **Možnost -short** omezuje výstup pouze na adresu každého objektu. To umožňuje automatizovat snadným vytvořením kanálu pro výstup z příkazu do dalšího příkazu ladicího programu.<br /><br /> Volba **-min** ignoruje objekty, které `size` jsou menší než parametr určený v bajtech.<br /><br /> Volba **-max** ignoruje objekty, které `size` jsou větší než parametr určený v bajtech.<br /><br /> Možnost **-thinlock** hlásí ThinLocks.  Další informace naleznete v příkazu **SyncBlk.**<br /><br /> Možnost `-startAtLowerBound` vynutí haldy chůze začít na dolní mez dodané rozsah adres. Během fáze plánování často nelze haldu projít, jelikož je s objekty pohybováno. Tato možnost vynutí **DumpHeap** začít svou procházku na zadanou dolní mez. Aby tato možnost fungovala, je třeba zadat adresu platného objektu jako dolní mez. Na adrese chybného objektu lze zobrazit paměť a vyhledat další tabulky metody ručně. Pokud uvolňování paměti je aktuálně ve `memcopy`volání , můžete také najít adresu dalšího objektu přidáním velikosti počáteční adresu, která je zadána jako parametr.<br /><br /> Možnost **-mt** uvádí pouze ty objekty, které odpovídají zadané `MethodTable` struktuře.<br /><br /> Možnost **-type** uvádí pouze ty objekty, jejichž název typu je shodou podřetězce zadaného řetězce.<br /><br /> Parametr `start` začíná výpis ze zadané adresy.<br /><br /> Parametr `end` zastaví výpis na zadanou adresu.|
|**Objekt DumpIL** \< *ManagedMethod*> &#124;  \<ukazatel *DynamicMethodDesc*> &#124;  \<ukazatel *MethodDesc*>|Zobrazí kód v jazyce MSIL (Microsoft Intermediate Language) přidružený ke spravované metodě.<br /><br /> Dynamický kód jazyka MSIL je vysílán jinak, než kód jazyka MSIL, který je načten ze sestavení. Dynamický kód jazyka MSIL odkazuje spíše na objekty v poli spravovaných objektů, než na tokeny metadat.|
|**DumpLog** [**-addr** \< *addressOfStressLog*>] [<*Filenam* `e`>]|Zapíše obsah zátěžového protokolu uloženého v paměti do zadaného souboru. Pokud nebude název zadán, vytvoří příkaz v aktuálním adresáři soubor s názvem StressLog.txt.<br /><br /> Zátěžový protokol uložený v paměti pomáhá diagnostikovat zátěžová selhání bez pomoci zámků nebo vstupů a výstupů. Chcete-li protokol napětí povolit, nastavte následující klíče\\registru v části HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft . Netframework:<br /><br /> (DWORD) StressLog = 1<br /><br /> (DWORD) LogFacility = 0xffffffff<br /><br /> (DWORD) StressLogSize = 65536<br /><br /> Volitelná `-addr` možnost umožňuje zadat protokol napětí jiný než výchozí protokol.|
|**Adresa DumpMD** \< *MethodDesc*>|Zobrazí informace `MethodDesc` o struktuře na zadané adrese.<br /><br /> Pomocí příkazu **IP2MD** můžete `MethodDesc` získat adresu struktury ze spravované funkce.|
|**Adresa MethodTable ( DumpMT** [**-MD**] \< *MethodTable*>|Zobrazí informace o tabulce metod na zadané adrese. Zadáním volby **-MD** se zobrazí seznam všech metod definovaných objektem.<br /><br /> Každý spravovaný objekt obsahuje ukazatel tabulky metod.|
|**DumpMethodSig** \< *sigaddr*> <*moduleadd*`r`>|Zobrazí informace `MethodSig` o struktuře na zadané adrese.|
|**Adresa modulu DumpModule** [**-mt**] \< *Module address*>|Zobrazí informace o modulu na zadané adrese. Možnost **-mt** zobrazuje typy definované v modulu a typy, na které modul odkazuje<br /><br /> K načtení adresy modulu můžete použít příkaz **DumpDomain** nebo **DumpAssembly.**|
|\< *Adresa objektu* **DumpObj** [**-nofields**]><br /><br /> -nebo-<br /><br /> **DO** \< *Adresa objektu* DO>|Zobrazí informace o objektu na zadané adrese. Příkaz **DumpObj** zobrazí pole, `EEClass` informace o struktuře, tabulku metody a velikost objektu.<br /><br /> Příkaz **DumpStackObjects** můžete použít k načtení adresy objektu.<br /><br /> Všimněte si, že můžete spustit **DumpObj** příkaz u polí typu, `CLASS` protože jsou také objekty.<br /><br /> Možnost `-` **nofields** zabraňuje polím zobrazovaného objektu, je užitečná pro objekty, jako je String.|
|**DumpRuntimeTypes**|Zobrazí objekty typu runtime z haldy systému uvolňování paměti a vypíše názvy s nimi asociovaných typů a tabulky metod.|
|**DumpStack** [**-EE**] [`top` **-n**] [ *zásobník* `bottom` [ *stac*`k`]]|Zobrazí trasování zásobníku.<br /><br /> Možnost **-EE** způsobí, že příkaz **DumpStack** zobrazí pouze spravované funkce. Pomocí `top` parametrů `bottom` a můžete omezit rámce zásobníku zobrazené na platformách x86.<br /><br /> Možnost **-n** zakáže zobrazení názvů zdrojových souborů a čísel řádků. Pokud ladicí program má zadánu možnost SYMOPT_LOAD_LINES, bude nástroj SOS vyhledávat symboly pro každý spravovaný rámec a v případě úspěchu zobrazí odpovídající název zdrojového souboru a číslo řádku. **Parametr -n** (Bez čísel řádků) lze zadat pro zakázání tohoto chování.<br /><br /> Na platformách x86 a x64 příkaz **DumpStack** vytvoří podrobné trasování zásobníku.<br /><br /> Na platformách založených na IA-64 příkaz **DumpStack** napodobuje příkaz **K** ladicího programu. `top` Parametry `bottom` a jsou ignorovány na platformách založených na IA-64.|
|**DumpSig** \< *sigaddr*> \<*moduladdr*>|Zobrazí informace `Sig` o struktuře na zadané adrese.|
|**DumpSigElem** \< *sigaddr*> \<*moduladdr*>|Zobrazí jediný prvek objektu podpisu. Ve většině případů byste měli použít **DumpSig** k pohledu na jednotlivé podpisové objekty. Pokud však byl podpis nějakým způsobem poškozen, můžete použít **DumpSigElem** ke čtení platných částí.|
|**DumpStackObjects** [**-verify**`top` ]`bottom` [ *zásobník* [ *zásobník*]]<br /><br /> -nebo-<br /><br /> **DSO** [**-verify**`top` ]`bottom` [ *zásobník* [ *zásobník*]]|Zobrazí všechny spravované objekty nalezené v rámci aktuálního zásobníku.<br /><br /> Možnost **-verify** ověří každé `CLASS` nestatické pole pole objektu.<br /><br /> Pomocí příkazu **DumpStackObject** s příkazy pro trasování zásobníku, jako je příkaz **K** a příkaz **CLRStack,** určete hodnoty místních proměnných a parametrů.|
|\<*Adresa* *metody*>  **DumpVC** \<>|Zobrazí informace o polích třídy hodnot na konkrétní adrese.<br /><br /> Parametr **MethodTable** umožňuje příkazu **DumpVC** správně interpretovat pole. Třídy hodnot nemají jako první pole tabulku metod.|
|**EEHeap** [**-gc**] [**-nakladač**]|Zobrazí informace o paměti procesu spotřebované interními datovými strukturami CLR.<br /><br /> Možnosti **-gc** a **-loader** omezují výstup tohoto příkazu na datové struktury systému uvolňování paměti nebo zavaděče.<br /><br /> Informace pro systém uvolňování paměti obsahují rozsahy každého segmentu ve spravované haldě.  Pokud ukazatel spadá do rozsahu segmentu dané **-gc**, ukazatel je ukazatel objektu.|
|**EEStack** [**-short**] [**-EE**]|Spustí příkaz **DumpStack** ve všech vláknech v procesu.<br /><br /> Možnost **-EE** je předána přímo příkazu **DumpStack.** Parametr **-short** omezuje výstup na následující druhy vláken:<br /><br /> Vlákna, která byla uzamknuta.<br /><br /> Vlákna, která byla kvůli uvolňování paměti pozastavena.<br /><br /> Vlákna, která jsou aktuálně ve spravovaném kódu.|
|**EEVersion**|Zobrazí verzi CLR.|
|**EHInfo** \<[*MethodDesc* adresa\<>] [*Kód adresa*>]|Zobrazí bloky zpracování výjimek v zadané metodě.  Tento příkaz zobrazí adresy kódu a posuny pro `try` blok klauzule (blok) a blok obslužné rutiny `catch` (blok).|
|**Nejčastější dotazy**|Zobrazí nejčastější dotazy.|
|**FinalizeQueue** [**-detail**] &#124; [**-allReady**] [**-short**]|Zobrazí všechny objekty, které jsou registrovány pro dokončení.<br /><br /> Možnost **-detail** zobrazí další `SyncBlocks` informace o všech, které `RuntimeCallableWrappers` je třeba vyčistit, a všechny (RCWs), které čekají na vyčištění. Obě tyto datové struktury jsou uloženy do mezipaměti a vyčištěny finalizačním vláknem při spuštění.<br /><br /> Možnost `-allReady` zobrazí všechny objekty, které jsou připraveny k dokončení, bez ohledu na to, zda jsou již označeny uvolnění paměti jako takové, nebo budou označeny další uvolnění paměti. Objekty, které jsou na seznamu objektů připravených k dokončení, jsou dokončitelné objekty, které již nezačínají kořenem. Tato možnost může být velice nákladná, jelikož ověřuje, zda všechny objekty ve frontě dokončitelných objektů stále začínají kořenem.<br /><br /> Možnost `-short` omezuje výstup na adresu každého objektu. Pokud se používá ve spojení s **-allReady**, vyjmenovává všechny objekty, které mají finalizační metodu, které již nejsou zakořeněné. Pokud je použita nezávisle, vypíše všechny objekty ve frontách s dokončitelnými objekty a objekty připravenými k dokončení.|
|*Adresa objektu* **FindAppDomain** \<>|Určuje doménu aplikace objektu na zadané adrese.|
|**FindRoots** **-gen** \< *N*> &#124; \< **-gen libovolnou** adresu &#124;*objektu*>|Způsobí přerušení ladicího programu během ladění při dalším shromáždění zadané generace. Efekt se obnoví, jakmile dojde k přerušení. Pro přerušení dalšího shromažďování je třeba znovu zadat tento příkaz. * \<Adresa objektu>* podobě tohoto příkazu se používá po přerušení způsobené **-gen** nebo **-gen any** došlo. V té době, ladicí doba je ve správném stavu pro **FindRoots** identifikovat kořeny pro objekty ze současných odsouzených generací.|
|**GCHandles** [**-perdomain**]|Zobrazí statistické údaje o popisovačích systému uvolňování paměti v procesu.<br /><br /> Možnost **-perdomain** uspořádá statistiky podle domény aplikace.<br /><br /> Pomocí příkazu **GCHandles** vyhledejte nevracení paměti způsobené popisovačem uvolňování paměti. Neuvolnění paměti například nastane, když kód zachová velké pole, protože silný popisovač systému uvolňování paměti na něj stále ukazuje, zatímco je zrušen, aniž by bylo uvolněno pole.|
|**GCHandleLeaks**|Vyhledá v paměti jakékoli odkazy na silné a připojené popisovače systému uvolňování paměti v procesu a zobrazí výsledky. Pokud je nalezen popisovač, příkaz **GCHandleLeaks** zobrazí adresu odkazu. Pokud není popisovač v paměti nalezen, zobrazí tento příkaz upozornění.|
|*Adresa kódu* adresy>\< **GCInfo** \< *MethodDesc*>|Zobrazí data, která označují, kdy registry nebo umístění zásobníku obsahují spravované objekty. Pokud dojde k uvolnění paměti, musí uvolňovač vědět o umístění odkazů na objekty, aby je bylo možné aktualizovat novou hodnotou ukazatele na objekt.|
|**GCRoot** [**-nostacks**] \< *Adresa objektu*>|Zobrazí informace o odkazech (nebo kořenech) na objekt na zadané adrese.<br /><br /> Příkaz **GCRoot** zkontroluje celou spravovanou haldu a tabulku popisovačů pro popisovače v rámci jiných objektů a popisovačů v zásobníku. Každý zásobník následně vyhledá ukazatele na objekty a rovněž je prohledána fronta finalizační metody.<br /><br /> Tento příkaz neurčuje, zda je kořen zásobníku platný nebo zrušený. Pomocí příkazů **CLRStack** a **U** rozebrat snímek, který patří místní nebo argument hodnotu k určení, pokud kořen zásobníku je stále používán.<br /><br /> Možnost **-nostacks** omezuje hledání na popisovače systému uvolňování paměti a dosažitelné objekty.|
|**GCWhere**  *\<>adresy objektu*|Zobrazí umístění a velikost předaného argumentu v haldě uvolňování paměti. Pokud argument leží ve spravované haldě, ale není platnou adresou objektu, je zobrazena velikost 0 (nula).|
|**nápověda** \<*[příkaz* `faq`>] [ ]|Zobrazí všechny dostupné příkazy, pokud není zadán žádný parametr, nebo zobrazí detailní informace nápovědy o zadaném příkazu.<br /><br /> Parametr `faq` zobrazí odpovědi na často kladené otázky.|
|**HeapStat** [**-inclNekořenné** &#124; **-iu**]|Zobrazí velikosti generací pro každou haldu a celkové volné místo v každé generaci v každé haldě. Pokud je zadána možnost -**inclUnrooted,** sestava obsahuje informace o spravovaných objektech z haldy uvolňování paměti, která již není zakořeněna.|
|**HistClear řekl:**|Uvolní všechny prostředky používané rodinou `Hist` příkazů.<br /><br /> Obecně není třeba explicitně `HistClear`volat , `HistInit` protože každý vyčistí předchozí prostředky.|
|**HistInit (Něm.)**|Inicializuje struktury SOS ze zátěžového protokolu uloženého v laděné položce.|
|**obj_address HistOb** * \<>j*|Zkontroluje všechny záznamy přemístění zátěžového protokolu a zobrazí řetězec přemísťování uvolňování paměti, který může vést na adresu předanou jako argument.|
|**HistObjNajít**  *\<obj_address>*|Zobrazí všechny položky protokolu, které odkazují na objekt na zadané adrese.|
|**HistRoot** * \<kořenový>HistRoot*|Zobrazí informace týkající se propagace a přemístění zadaného kořenu.<br /><br /> Hodnotu kořenu lze použít ke sledování pohybu objektu skrz uvolňování paměti.|
|*Adresa kódu* **IP2MD** \<>|Zobrazí `MethodDesc` strukturu na zadanou adresu v kódu, který byl kompilován JIT.|
|`ListNearObj`(`lno` * \<* obj_address>|Zobrazí objekty před a za zadanou adresou. Tento příkaz vyhledá adresu v haldě uvolňování paměti vypadající jako platný začátek spravovaného objektu (podle platné tabulky metod) a objekt následující za adresou argumentu.|
|**MinidumpMode** [**0**] [**1**]|Zabrání ve spuštění nebezpečných příkazů pomocí minimálního výpisu.<br /><br /> Pass **0** zakázat tuto funkci nebo **1** povolit tuto funkci. Ve výchozím nastavení je hodnota **MinidumpMode** nastavena na **hodnotu 0**.<br /><br /> Minidumpy vytvořené pomocí příkazu **.dump /m** nebo **.dump** mají omezená data specifická pro CLR a umožňují správně spustit pouze podmnožinu příkazů SOS. Některé příkazy mohou selhat s neočekávanými chybami, jelikož požadované oblasti paměti nejsou zmapovány nebo jsou zmapovány pouze částečně. Tato možnost zabraňuje ve spuštění nebezpečných příkazů s minimálním výpisem.|
|**Název 2EE** \< *typ názvu*> \<modulu nebo název*metody*><br /><br /> -nebo-<br /><br /> \< *module name*> **Názevmodulu Name2EE** **!** \< *název typu nebo metody*>|Zobrazí `MethodTable` strukturu `EEClass` a strukturu pro zadaný typ nebo metodu v zadaném modulu.<br /><br /> Zadaný modul musí být načten v procesu.<br /><br /> Chcete-li získat správný název typu, procházejte modul pomocí [ildasm.exe (IL Disassembler)](ildasm-exe-il-disassembler.md). Můžete také `*` předat jako parametr název modulu pro vyhledávání všech načtených spravovaných modulů. Parametr *název modulu* může být také název ladicího programu `mscorlib` `image00400000`pro modul, například nebo .<br /><br /> Tento příkaz podporuje syntaxi ladicího programu systému `module` > `!` < `type` Windows <>. Typ musí být plně kvalifikovaný.|
|**ObjSize** \<[*Adresa objektu*>] &#124; [**-aggregate**] [**-stat**]|Zobrazí velikost zadaného objektu. Pokud nezadáte žádné parametry, příkaz **ObjSize** zobrazí velikost všech objektů nalezených ve spravovaných vláknech, zobrazí všechny popisovače systému uvolňování paměti v procesu a sečte velikost všech objektů, na které tyto popisovače poukázaly. Příkaz **ObjSize** obsahuje velikost všech podřízených objektů kromě nadřazeného objektu.<br /><br /> Možnost **-aggregate** lze použít ve spojení s argumentem **-stat,** abyste získali podrobné zobrazení typů, které jsou stále zakořeněné. Pomocí **!dumpheap -stat** a **!objsize -aggregate -stat**můžete určit, které objekty již nejsou zakořeněny, a diagnostikovat různé problémy s pamětí.|
|**PrintException** [**-vnořené**]\<[**-lines**] [ Adresa*objektu výjimky*>]<br /><br /> -nebo-<br /><br /> **PE** [**-vnořené**] [\<Adresa*objektu výjimky*>]|Zobrazí a formátuje pole libovolného <xref:System.Exception> objektu odvozeného z třídy na zadané adrese. Pokud nezadáte adresu, příkaz **PrintException** zobrazí poslední výjimku vydanou v aktuálním vlákně.<br /><br /> Možnost **-vnořené** zobrazí podrobnosti o vnořených objektech výjimek.<br /><br /> Možnost **-lines** zobrazí zdrojové informace, pokud jsou k dispozici.<br /><br /> Tento příkaz můžete použít k `_stackTrace` formátování a zobrazení pole, což je binární pole.|
|**ProcInfo** [**-env**] [**-time**] [**-mem**]|Zobrazí proměnné prostředí pro proces, čas jádra CPU a statistiky využití paměti.|
|**RCWCleanupList** \< *RCWCleanupList adresa*>|Zobrazí seznam obálek volatelných za běhu (RCW), které čekají na vyčištění, na zadané adrese.|
|> \<*Název souboru* *základní adresy* **SaveModule** \<>|Zapíše bitovou kopii, která je načtena do paměti na zadané adrese, do zadaného souboru.|
|**SOSFlush**|Vyprázdní interní mezipaměť SOS.|
|**StopOnException** [**-derived**] [**-create** &#124; **-create2**] \< *Exception*> \<*Pseudo-register number*>|Způsobí, že se ladicí program zastaví, pokud je vyvolána zadaná výjimka, ale bude pokračovat, pokud je vyvolána jiná výjimka.<br /><br /> Možnost **-derived** zachytí zadanou výjimku a každou výjimku, která je odvozena od zadané výjimky.|
|**SyncBlk** [**-all** &#124; \< *syncblk číslo*>]|Zobrazí zadanou `SyncBlock` strukturu `SyncBlock` nebo všechny struktury.  Pokud nepředáte žádné argumenty, příkaz **SyncBlk** zobrazí `SyncBlock` strukturu odpovídající objektům, které jsou vlastněny vláknem.<br /><br /> Struktura `SyncBlock` je kontejner pro další informace, které není nutné vytvořit pro každý objekt. Může obsahovat data zprostředkovatele komunikace s objekty COM, hodnoty hash a informace o zamykání pro operace bezpečné pro přístup z více vláken.|
|**Threadpool**|Zobrazí informace o spravovaném fondu vláken, včetně počtu pracovních požadavků ve frontě, počtu vláken portů dokončení a počtu časovačů.|
|\<*Token* *názvu*> modulu **Token2EE** \<>|Změní zadaný token metadat v zadaném modulu na `MethodTable` strukturu nebo `MethodDesc` strukturu.<br /><br /> Můžete předat `*` parametr název modulu a zjistit, co tento token mapuje v každém načteném spravovaném modulu. Můžete také předat název ladicího programu pro modul, například `mscorlib` nebo `image00400000`.|
|**Vlákna** [**-live**] [**-special**]|Zobrazí všechna spravovaná vlákna v procesu.<br /><br /> Příkaz **Podprocesy** zobrazí zkrácené ID ladicího programu, ID vlákna CLR a ID vlákna operačního systému.  Kromě toho příkaz **Podprocesy** zobrazí sloupec Domain, který označuje doménu aplikace, ve které je vlákno spuštěno, sloupec APT, který zobrazuje režim apartment COM, a sloupec Exception, který zobrazuje poslední výjimku vyzdviženou ve vlákně.<br /><br /> Možnost **-live** zobrazuje vlákna přidružená k živému vláknu.<br /><br /> Možnost **-special** zobrazí všechna speciální vlákna vytvořená CLR. Speciální vlákna zahrnují vlákna uvolňování paměti (v souběžné masce a uvolňování paměti <xref:System.AppDomain> serveru), pomocná vlákna ladicího programu, vlákna finalizační metody, uvolnění vláken a vlákna časovače fondu vláken.|
|*Pole hodnoty stavu* stavu vlákna ** \< ****>**|Zobrazí stav vlákna. Parametr `value` je hodnota `State` pole ve výstupu sestavy **Vlákna.**<br /><br /> Příklad:<br /><br /> `0:003> !Threads     ThreadCount:      2     UnstartedThread:  0     BackgroundThread: 1     PendingThread:    0     DeadThread:       0     Hosted Runtime:   no                                           PreEmptive   GC Alloc           Lock            ID OSID ThreadOBJ    State     GC       Context       Domain   Count APT Exception        0    1  250 0019b068      a020 Disabled 02349668:02349fe8 0015def0     0 MTA        2    2  944 001a6020      b220 Enabled  00000000:00000000 0015def0     0 MTA (Finalizer)     0:003> !ThreadState b220         Legal to Join         Background         CLR Owns         CoInitialized         In Multi Threaded Apartment`|
|**Název souboru TraverseHeap** [**-xml]** \< *filename*>|Zapíše informace o haldě do zadaného souboru ve formátu srozumitelném pro profiler modulu CLR. Volba **-xml** způsobí, že příkaz **TraverseHeap** naformátuje soubor jako XML.<br /><br /> Profilovač CLR si můžete stáhnout ze služby [Stažení softwaru](https://go.microsoft.com/fwlink/?LinkID=67325).|
|**U** [**-gcinfo**] [**-ehinfo**] [**-n** \<] *MethodDesc adresa*> &#124; \<adresa *kódu*>|Zobrazí anotované demontáž spravované metody určené ukazatelem `MethodDesc` struktury pro metodu nebo kódovou adresou v těle metody. Příkaz **U** zobrazí celou metodu od začátku do konce s anotacemi, které převádějí tokeny metadat na názvy.<br /><br /> Možnost **-gcinfo** způsobí, že příkaz `GCInfo` **U** zobrazí strukturu metody.<br /><br /> Možnost **-ehinfo** zobrazí informace o výjimce pro metodu. Tyto informace můžete také získat pomocí příkazu **EHInfo.**<br /><br /> Možnost **-n** zakáže zobrazení názvů zdrojových souborů a čísel řádků. Pokud má ladicí program zadánu možnost SYMOPT_LOAD_LINES, bude nástroj SOS vyhledávat symboly pro každý spravovaný rámec a v případě úspěchu zobrazí odpovídající název zdrojového souboru a číslo řádku. Můžete zadat **možnost -n** zakázat toto chování.|
|**Ověřit Haldu**|Zkontroluje, zda halda systému uvolňování paměti vykazuje známky poškození a zobrazí všechny nalezené chyby.<br /><br /> Poškození haldy může být způsobeno voláními vyvolání platformy, která nejsou správně vytvořena.|
|Ověřit *Adresu objektu* **Obj** \<>|Zkontroluje, zda objekt, který je předán jako argument, jeví známky poškození.|
|**Vmmap**|Projde prostor virtuálních adres a zobrazí typy ochran aplikované na jednotlivé oblasti.|
|**VMStat**|Poskytuje souhrnné zobrazení prostoru virtuálních adres, seřazených podle typů ochran aplikovaných na danou paměť (volná, rezervovaná, potvrzená, soukromá, mapovaná, bitová kopie). Sloupec TOTAL obsahuje hodnotu ze sloupce AVERAGE vynásobenou hodnotou ze sloupce BLK COUNT.|

## <a name="remarks"></a>Poznámky

Rozšíření ladění SOS umožňuje zobrazit informace o kódu, který je spuštěn uvnitř CLR. Nástroj SOS Debugging Extension lze například použít k zobrazení informací o spravované haldě, vyhledání poškození haldy, zobrazení vnitřních datových typů používaných modulem runtime a zobrazení informací o spravovaném kódu běžícím uvnitř modulu runtime.

Chcete-li použít rozšíření ladění SOS v sadě Visual Studio, nainstalujte [sady WDK (Windows Driver Kit)](/windows-hardware/drivers/download-the-wdk). Informace o integrovaném prostředí ladění v sadě Visual Studio naleznete v [tématu Ladění prostředí](/windows-hardware/drivers/debugger/debuggers-in-the-debugging-tools-for-windows-package).

Rozšíření ladění SOS můžete také použít tak, že jej načtete do [ladicího programu WinDbg.exe](/windows-hardware/drivers/debugger/debugger-download-tools) a provedete příkazy v rámci programu WinDbg.exe.

K načtení nástroje SOS Debugging Extension do ladicího programu WinDbg.exe je třeba v tomto nástroji zadat následující příkaz:

```console
.loadby sos clr
```

Nástroj WinDbg.exe i sada Visual Studio používají verzi knihovny SOS.dll odpovídající aktuálně používané verzi knihovny Mscorwks.dll. Ve výchozím nastavení by měla být použita verze knihovny SOS.dll, která odpovídá aktuální verzi knihovny Mscorwks.dll.

Pro zpracování souboru výpisu paměti vytvořeného na jiném počítači je třeba se ujistit, že soubor Mscorwks.dll, který byl distribuován s instalací, je v cestě k symbolům, a že je načtena odpovídající verze knihovny SOS.dll.

Pro načtení konkrétní verze knihovny SOS.dll je třeba do ladicího programu systému Windows zadat následující příkaz:

```console
.load <full path to sos.dll>
```

## <a name="examples"></a>Příklady

Následující příkaz zobrazí obsah pole na `00ad28d0`adrese .  Zobrazí se druhý prvek a pět následujících.

```console
!dumparray -start 2 -length 5 -detail 00ad28d0
```

Následující příkaz zobrazí obsah sestavení na `1ca248`adrese .

```console
!dumpassembly 1ca248
```

Následující příkaz zobrazí informace o haldě systému uvolňování paměti.

```console
!dumpheap
```

Následující příkaz zapíše obsah zátěžového protokolu z paměti do (výchozího) souboru s názvem StressLog.txt v aktuálním adresáři.

```console
!DumpLog
```

Následující příkaz zobrazí `MethodDesc` strukturu na `902f40`adrese .

```console
!dumpmd 902f40
```

Následující příkaz zobrazuje informace o modulu na adrese `1caa50`.

```console
!dumpmodule 1caa50
```

Následující příkaz zobrazí informace o objektu na adrese `a79d40`.

```console
!DumpObj a79d40
```

Následující příkaz zobrazí pole třídy hodnot `00a79d9c` na adrese pomocí tabulky `0090320c`metod na adrese .

```console
!DumpVC 0090320c 00a79d9c
```

Následující příkaz zobrazí paměť procesu využitou systémem uvolňování paměti.

```console
!eeheap -gc
```

Následující příkaz zobrazí všechny objekty, které jsou naplánovány k dokončení.

```console
!finalizequeue
```

Následující příkaz určuje aplikační doménu objektu `00a79d98`na adrese .

```console
!findappdomain 00a79d98
```

Následující příkaz zobrazí všechny popisovače systému uvolňování paměti v aktuálním procesu.

```console
!gcinfo 5b68dbb8
```

Následující příkaz zobrazí `MethodTable` `EEClass` struktury a `Main` pro metodu `MainClass` ve `unittest.exe`třídě v modulu .

```console
!name2ee unittest.exe MainClass.Main
```

Následující příkaz zobrazí informace o tokenu `02000003` metadat na `unittest.exe`adrese v modulu .

```console
!token2ee unittest.exe 02000003
```

## <a name="see-also"></a>Viz také

- [Nástroje](index.md)
- [Příkazové řádky](developer-command-prompt-for-vs.md)
