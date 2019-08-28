---
title: Jak běhové prostředí vyhledává sestavení
ms.date: 03/30/2017
helpviewer_keywords:
- app.config files, assembly locations
- deploying applications [.NET Framework], assembly locations
- application configuration files, locating assemblies
- .NET Framework application deployment, locating assemblies
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 772ac6f4-64d2-4cfb-92fd-58096dcd6c34
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5d22b4292483a94153864cad3439933837aed3b2
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70043407"
---
# <a name="how-the-runtime-locates-assemblies"></a>Jak běhové prostředí vyhledává sestavení

K úspěšnému nasazení .NET Framework aplikace musíte pochopit, jak modul CLR (Common Language Runtime) hledá a váže sestavení, která tvoří vaši aplikaci. Ve výchozím nastavení se modul runtime pokusí vytvořit vazby s přesnou verzí sestavení, pomocí kterého byla aplikace sestavena. Toto výchozí chování lze přepsat nastavením konfiguračního souboru.

Modul CLR (Common Language Runtime) provádí několik kroků při pokusu o nalezení sestavení a vyřešení odkazu na sestavení. Jednotlivé kroky jsou vysvětleny v následujících oddílech. Termín zjišťování se často používá při popisu způsobu, jakým modul runtime vyhledává sestavení. odkazuje na sadu heuristik používaných k vyhledání sestavení na základě jeho názvu a jazykové verze.

> [!NOTE]
> Informace o vazbě můžete zobrazit v souboru protokolu pomocí [nástroje Assembly Binding Log Viewer (Fuslogvw. exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md), který je součástí Windows SDK.

## <a name="initiating-the-bind"></a>Inicializuje se vazba.

Proces vyhledávání a vazba sestavení začíná, když se modul runtime pokusí přeložit odkaz na jiné sestavení. Tento odkaz může být buď statický, nebo dynamický. Kompilátor zaznamenává statické odkazy v metadatech manifestu sestavení v době sestavení. Dynamické odkazy jsou vytvořeny průběžně v důsledku volání různých metod, <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>jako je například.

Upřednostňovaným způsobem, jak odkazovat na sestavení, je použít úplný odkaz, včetně názvu sestavení, verze, jazykové verze a tokenu veřejného klíče (pokud existuje). Modul runtime používá tyto informace k vyhledání sestavení podle kroků popsaných dále v této části. Modul runtime používá stejný proces rozlišení bez ohledu na to, zda je odkaz pro statické nebo dynamické sestavení.

Můžete také vytvořit dynamický odkaz na sestavení poskytnutím metody volání s pouze částečnými informacemi o sestavení, jako je například určení pouze názvu sestavení. V takovém případě bude pro sestavení prohledán pouze adresář aplikace a žádná další kontrola nebude provedena. Pomocí kterékoli z různých metod načítání sestavení, jako je například <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> nebo <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>, provedete částečný odkaz.

Nakonec můžete vytvořit dynamický odkaz pomocí metody <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> , jako je a poskytnout pouze částečné informace; vy pak můžete kvalifikovat odkaz [ \<pomocí elementu qualifyAssembly >](../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md) v konfiguračním souboru aplikace. Tento prvek umožňuje poskytnout úplné referenční informace (název, verzi, jazykovou verzi a případně token veřejného klíče) do konfiguračního souboru aplikace namísto v kódu. Tuto techniku byste měli použít, pokud jste chtěli plně kvalifikovat odkaz na sestavení mimo adresář aplikace, nebo pokud jste chtěli odkazovat na sestavení v globální mezipaměti sestavení (GAC), ale vy jste chtěli mít možnost zadat úplný odkaz v konfigurační soubor místo ve vašem kódu.

> [!NOTE]
> Tento typ částečného odkazu by neměl být použit se sestaveními, která jsou sdílena mezi několika aplikacemi. Vzhledem k tomu, že nastavení konfigurace se aplikují na aplikaci a ne na sestavení, sdílené sestavení používající tento typ částečného odkazu by vyžadovalo, aby každá aplikace, která používá sdílené sestavení, měla opravňující informace ve svém konfiguračním souboru.

Modul runtime používá následující postup k vyřešení odkazu na sestavení:

1. [Určuje správnou verzi sestavení](#step1) prozkoumáním příslušných konfiguračních souborů, včetně konfiguračního souboru aplikace, souboru zásad vydavatele a konfiguračního souboru počítače. Pokud se konfigurační soubor nachází ve vzdáleném počítači, musí modul runtime nejprve vyhledat a stáhnout konfigurační soubor aplikace.

2. [Kontroluje, zda byl název sestavení svázán před](#step2) a, pokud ano, používá dříve načtené sestavení. Pokud předchozí požadavek na načtení sestavení selhal, požadavek se okamžitě nezdařil bez pokusu o načtení sestavení.

    > [!NOTE]
    > V .NET Framework verze 2,0 je ukládání neúspěšných vazeb sestavení do mezipaměti nového.

3. [Kontroluje globální mezipaměť sestavení (GAC](#step3)). Pokud je sestavení nalezeno, modul runtime používá toto sestavení.

4. [Sondy pro sestavení](#step4) pomocí následujících kroků:

    1. Pokud zásady konfigurace a vydavatelů neovlivňují původní odkaz a v případě, že požadavek BIND byl vytvořen pomocí <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metody, modul runtime vyhledá pomocné parametry umístění.

    2. Pokud je v konfiguračních souborech nalezen základ kódu, modul runtime kontroluje pouze toto umístění. Pokud se tento test nepovede, modul runtime zjistí, že se požadavek vazby nezdařil a žádné jiné zjišťování neprobíhá.

    3. Sondy pro sestavení pomocí heuristiky popsaných v [části zjišťování](#step4). Pokud sestavení není po probingu nalezeno, modul runtime požaduje Instalační služba systému Windows k poskytnutí sestavení. Funguje jako funkce instalace na vyžádání.

        > [!NOTE]
        > Neexistuje žádná kontrola verze pro sestavení bez silného názvu, ani modul runtime neprovádí kontrolu globální mezipaměti sestavení (GAC) pro sestavení bez silných názvů.

<a name="step1"></a>

## <a name="step-1-examining-the-configuration-files"></a>Krok 1: Zkoumání konfiguračních souborů

Chování vazby sestavení lze nakonfigurovat na různých úrovních na základě tří souborů XML:

- Konfigurační soubor aplikace.

- Soubor zásad vydavatele.

- Konfigurační soubor počítače.

Tyto soubory se řídí stejnou syntaxí a poskytují informace, jako jsou přesměrování vazby, umístění kódu a režimy vazby pro konkrétní sestavení. Každý konfigurační soubor může obsahovat [ \<prvek assemblyBinding >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) , který přesměruje proces vazby. K podřízeným [ \<](../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md) [ \<elementům elementu assemblyBinding >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) patří prvek dependentAssembly >. Podřízené položky [ \<>](../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md) [ \<](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md) [ elementu\<dependentAssembly zahrnují prvek assemblyIdentity >](/visualstudio/deployment/assemblyidentity-element-clickonce-deployment), prvek bindingRedirect > a [ \<> základu kódu. ](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md).

> [!NOTE]
> Informace o konfiguraci najdete ve třech konfiguračních souborech. Ne všechny prvky jsou platné ve všech konfiguračních souborech. Například režim vazby a informace o soukromé cestě můžou být v konfiguračním souboru aplikace. Úplný seznam informací, které jsou obsaženy v jednotlivých souborech, najdete v tématu [Konfigurace aplikací pomocí konfiguračních souborů](../../../docs/framework/configure-apps/index.md).

### <a name="application-configuration-file"></a>Konfigurační soubor aplikace

Nejprve modul CLR kontroluje konfigurační soubor aplikace, kde se nacházejí informace, které přepisují informace o verzi uložené v manifestu volajícího sestavení. Konfigurační soubor aplikace může být nasazen s aplikací, ale není vyžadován pro spuštění aplikace. Načítání tohoto souboru je obvykle skoro okamžité, ale v situacích, kdy je základem aplikace na vzdáleném počítači, například ve webovém scénáři Internet Explorer, je nutné konfigurační soubor stáhnout.

V případě spustitelných souborů klienta se konfigurační soubor aplikace nachází ve stejném adresáři jako spustitelný soubor aplikace a má stejný základní název jako spustitelný soubor s příponou. config. Například konfigurační soubor pro C:\Program Files\Myapp\Myapp.exe je C:\Program Files\Myapp\Myapp.exe.config. Ve scénáři založeném na prohlížeči musí soubor HTML používat  **\<odkaz >** element, aby explicitně odkazoval na konfigurační soubor.

Následující kód poskytuje jednoduchý příklad konfiguračního souboru aplikace. Tento příklad přidá <xref:System.Diagnostics.TextWriterTraceListener> <xref:System.Diagnostics.Debug.Listeners%2A> do kolekce pro povolení zaznamenávání informací o ladění do souboru.

```xml
<configuration>
   <system.diagnostics>
      <trace useGlobalLock="false" autoflush="true" indentsize="0">
         <listeners>
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />
         </listeners>
      </trace>
   </system.diagnostics>
</configuration>
```

### <a name="publisher-policy-file"></a>Soubor zásad vydavatele

Za druhé, modul runtime prověřuje soubor zásad vydavatele, pokud nějaký existuje. Soubory zásad vydavatele jsou distribuovány vydavatelem součásti jako oprava nebo aktualizace sdílené součásti. Tyto soubory obsahují informace o kompatibilitě vyvolané vydavatelem sdílené součásti, která přesměruje odkaz na sestavení na novou verzi. Na rozdíl od konfiguračních souborů aplikace a počítače jsou soubory zásad vydavatele obsaženy ve vlastním sestavení, které musí být nainstalováno v globální mezipaměti sestavení (GAC).

Následuje příklad konfiguračního souboru zásad vydavatele:

```xml
<configuration>
    <runtime>
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">

            <dependentAssembly>
                <assemblyIdentity name="asm6" publicKeyToken="c0305c36380ba429" />
                <bindingRedirect oldVersion="3.0.0.0" newVersion="2.0.0.0"/>
            </dependentAssembly>

        </assemblyBinding>
    </runtime>
</configuration>
```

Chcete-li vytvořit sestavení, můžete použít nástroj [Al. exe (Assembly Linker)](../../../docs/framework/tools/al-exe-assembly-linker.md) pomocí příkazu, například následující:

```
Al.exe /link:asm6.exe.config /out:policy.3.0.asm6.dll /keyfile: compatkey.dat /v:3.0.0.0
```

`compatkey.dat`je soubor klíče se silným názvem. Tento příkaz vytvoří sestavení se silným názvem, které lze umístit do globální mezipaměti sestavení (GAC).

> [!NOTE]
> Zásady vydavatele mají vliv na všechny aplikace, které používají sdílenou součást.

Konfigurační soubor zásad vydavatele Přepisuje informace o verzi, které pocházejí z aplikace (tj. z manifestu sestavení nebo z konfiguračního souboru aplikace). Pokud v konfiguračním souboru aplikace není žádný příkaz pro přesměrování verze zadané v manifestu sestavení, přepíše soubor zásad vydavatele verzi určenou v manifestu sestavení. Nicméně pokud je v konfiguračním souboru aplikace k dispozici příkaz přesměrování, přepíše zásada vydavatele tuto verzi, nikoli hodnotu určenou v manifestu.

Soubor zásad vydavatele se používá v případě, že se aktualizuje sdílená komponenta a všechny aplikace, které tuto součást používají, by měly tuto novou verzi sdílené součásti vyskladnit. Nastavení v souboru zásad vydavatele přepíše nastavení v konfiguračním souboru aplikace, pokud konfigurační soubor aplikace neuplatňuje nouzový režim.

#### <a name="safe-mode"></a>Nouzový režim

Soubory zásad vydavatele se obvykle explicitně nainstalují jako součást aktualizace Service Pack nebo programu. Pokud dojde k potížím s upgradovanou sdílenou komponentou, můžete přepsat přepsání v souboru zásad vydavatele pomocí bezpečného režimu. Nouzový režim je určen podle  **\<publisherPolicy použít = "Ano**&#124;**ne"/>** , který je umístěn pouze v konfiguračním souboru aplikace. Určuje, jestli se mají z procesu vytváření vazeb odebrat informace o konfiguraci zásad vydavatele.

Nouzový režim lze nastavit pro celou aplikaci nebo pro vybraná sestavení. To znamená, že můžete vypnout zásady pro všechna sestavení, která tvoří aplikaci, nebo je zapnout pro některá sestavení, ale ne pro jiné. Chcete-li selektivně použít zásady vydavatele na sestavení, která tvoří aplikaci, nastavte  **\<publisherPolicy použít\=ne/>** a určete, která sestavení mají být ovlivněna pomocí \< **dependentAssembly.** element >. Chcete-li použít zásady vydavatele na všechna sestavení, která tvoří aplikaci, nastavte  **\<publisherPolicy\=použití No/>** bez závislých prvků sestavení. Další informace o konfiguraci najdete v tématu [Konfigurace aplikací pomocí konfiguračních souborů](../../../docs/framework/configure-apps/index.md).

### <a name="machine-configuration-file"></a>Konfigurační soubor počítače

Třetí, modul runtime prověřuje konfigurační soubor počítače. Tento soubor nazvaný Machine. config se nachází v místním počítači v podadresáři konfigurace kořenového adresáře, kde je modul runtime nainstalován. Tento soubor můžou správci použít k určení omezení vazeb sestavení, která jsou místní pro daný počítač. Nastavení v konfiguračním souboru počítače mají přednost před všemi ostatními konfiguračními nastaveními. to však neznamená, že by do tohoto souboru měla být vložena všechna nastavení konfigurace. Verze určená souborem zásad správce je finální a nemůže být přepsána. Přepsání zadaná v souboru Machine. config ovlivňují všechny aplikace. Další informace o konfiguračních souborech najdete v tématu [Konfigurace aplikací pomocí konfiguračních souborů](../../../docs/framework/configure-apps/index.md).

<a name="step2"></a>

## <a name="step-2-checking-for-previously-referenced-assemblies"></a>Krok 2: Kontrola dříve odkazovaných sestavení

Pokud požadované sestavení bylo také vyžádáno v předchozích voláních, modul CLR (Common Language Runtime) používá již načtené sestavení. To může mít důsledky při pojmenování sestavení, která tvoří aplikaci. Další informace o pojmenování sestavení naleznete v tématu [názvy sestavení](../../../docs/framework/app-domains/assembly-names.md).

Pokud předchozí požadavek na sestavení selhal, následné požadavky na sestavení se okamžitě nezdařily bez pokusu o načtení sestavení. .NET Framework počínaje verzí 2,0 se chyby vazeb sestavení ukládají do mezipaměti a k určení, jestli se má pokus načíst sestavení, se použijí informace uložené v mezipaměti.

> [!NOTE]
> Chcete-li se vrátit k chování .NET Framework verzí 1,0 a 1,1, které neobsahovaly neúspěšné vazby do mezipaměti [ \<](../../../docs/framework/configure-apps/file-schema/runtime/disablecachingbindingfailures-element.md) , zahrňte do konfiguračního souboru prvek disableCachingBindingFailures >.

<a name="step3"></a>

## <a name="step-3-checking-the-global-assembly-cache"></a>Krok 3: Kontroluje se globální mezipaměť sestavení (GAC).

V případě sestavení se silným názvem pokračuje proces vazby tím, že hledá globální mezipaměť sestavení (GAC). Globální mezipaměť sestavení (GAC) ukládá sestavení, která může být použita v několika aplikacích v počítači. Všechna sestavení v globální mezipaměti sestavení (GAC) musí mít silné názvy.

<a name="step4"></a>

## <a name="step-4-locating-the-assembly-through-codebases-or-probing"></a>Krok 4: Vyhledání sestavení prostřednictvím základů kódu nebo zjišťování

Po určení správné verze sestavení pomocí informací v odkazu volajícího sestavení a v konfiguračních souborech a poté, co se vrátí do globální mezipaměti sestavení (pouze pro sestavení se silným názvem), společný jazyk modul runtime se pokusí najít sestavení. Proces vyhledání sestavení zahrnuje následující kroky:

1. Pokud je v konfiguračním souboru aplikace nalezen element [ codebase>,modulruntimezkontrolujezadanéumístění.\<](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) Pokud je nalezena shoda, používá se toto sestavení a k žádnému zjišťování nedochází. Pokud sestavení není nalezeno, požadavek vazby se nezdařil.

2. Modul runtime pak sondy pro odkazované sestavení pomocí pravidel uvedených dále v této části.

> [!NOTE]
> Pokud máte v adresáři více verzí sestavení a chcete odkazovat na konkrétní verzi tohoto sestavení, je nutné použít `privatePath` [ \<> element codebase](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) namísto atributu [ \<zjišťování. element >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) . Použijete-li [ \<>](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) element probingu, modul runtime zastaví zkušební období při prvním nalezení sestavení, které odpovídá jednoduchému názvu sestavení, na který odkazuje, zda se jedná o správnou shodu. Pokud se jedná o správnou shodu, používá se toto sestavení. Pokud se nejedná o správnou shodu, zastaví se zjišťování a vazba se nezdařila.

### <a name="locating-the-assembly-through-codebases"></a>Vyhledání sestavení prostřednictvím základů kódu

Informace základu kódu lze poskytnout pomocí [ \<>ho prvku základu kódu](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) v konfiguračním souboru. Tento základ kódu je vždy zkontrolován před tím, než se modul runtime pokusí test pro odkazované sestavení. [ Obsahuje\<](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) -li soubor zásad vydavatele obsahující konečné přesměrování verze taky > element, [ \<](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) který je použit jako element codebase > je ten, který se používá. Například pokud konfigurační soubor aplikace určuje [ \<>](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) element, a soubor zásad vydavatele, který Přepisuje [ \<](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) informace o aplikaci, také určuje > element codebase, je použit element > základu kódu v souboru zásad vydavatele. [ \<](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md)

Pokud se nenajde žádná shoda v umístění určeném [ \<>](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) elementem codebase, požadavek vazby se nepovede a neproběhne žádné další kroky. Pokud modul runtime zjistí, že sestavení odpovídá kritériím volajícího sestavení, používá toto sestavení. Když je načten soubor určený pomocí daného [ \<elementu codebase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) element, modul runtime zkontroluje, zda se název, verze, jazyková verze a veřejný klíč shodují s odkazem volajícího sestavení.

> [!NOTE]
> Odkazovaná sestavení mimo kořenový adresář aplikace musí mít silné názvy a musí být buď nainstalovány v globální mezipaměti sestavení (GAC), nebo musí být zadána pomocí [ \<elementu > codebase](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) .

### <a name="locating-the-assembly-through-probing"></a>Vyhledání sestavení prostřednictvím zjišťování

Není-li v konfiguračním souboru aplikace žádný [ \<element > základů kódu](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) , běhové testy pro sestavení používají čtyři kritéria:

- Základ aplikace, což je kořenové umístění, kde je aplikace spouštěna.

- Culture, což je atribut Culture odkazovaného sestavení.

- Název, který je názvem odkazovaného sestavení.

- Atribut > elementu zjišťování, který je uživatelem definovaný seznam podadresářů v kořenovém umístění. [ \<](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) `privatePath` Toto umístění lze zadat v konfiguračním souboru aplikace a ve spravovaném kódu pomocí <xref:System.AppDomainSetup.PrivateBinPath?displayProperty=nameWithType> vlastnosti pro doménu aplikace. Při zadání ve spravovaném kódu se nejprve vyhledá spravovaný kód `privatePath` a za ním bude následovat Cesta zadaná v konfiguračním souboru aplikace.

#### <a name="probing-the-application-base-and-culture-directories"></a>Zjišťování adresářů základní a jazykové verze aplikace

Modul runtime vždy zahájí zjišťování v základu aplikace, což může být buď adresa URL, nebo kořenový adresář aplikace v počítači. Pokud odkazované sestavení není nalezeno v základu aplikace a nejsou k dispozici žádné informace o jazykové verzi, modul runtime vyhledá všechny podadresáře s názvem sestavení. Mezi adresáře, které jsou zjišťovány:

- [základ aplikace]/[název sestavení]. dll

- [základ aplikace]/[název sestavení]/[název sestavení]. dll

Pokud jsou pro odkazované sestavení určeny informace o jazykové verzi, jsou zjišťovány pouze následující adresáře:

- [základ aplikace]/[culture]/[název sestavení]. dll

- [základ aplikace]/[culture]/[název sestavení]/[název sestavení]. dll

#### <a name="probing-with-the-privatepath-attribute"></a>Zjišťování pomocí atributu nastavení privatePath

Kromě podadresářů kultury a podadresářů pojmenovaných pro odkazované sestavení modul runtime také zjišťuje adresáře zadané pomocí `privatePath` atributu [ \<> elementu zjišťování](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) . Adresáře zadané pomocí `privatePath` atributu musí být podadresáři kořenového adresáře aplikace. Zjištěné adresáře se liší v závislosti na tom, zda je v odkazované žádosti sestavení obsažena informace o jazykové verzi.

Modul runtime zastaví zkušební období při prvním nalezení sestavení, které odpovídá jednoduchému názvu sestavení, na který odkazuje, zda se jedná o správnou shodu. Pokud se jedná o správnou shodu, používá se toto sestavení. Pokud se nejedná o správnou shodu, zastaví se zjišťování a vazba se nezdařila.

Pokud je obsažena jazyková verze, jsou zjišťovány následující adresáře:

- [základ aplikace]/[BinPath]/[culture]/[název sestavení]. dll

- [základ aplikace]/[BinPath]/[culture]/[název sestavení]/[název sestavení]. dll

Pokud nejsou k dispozici informace o jazykové verzi, jsou zjišťovány následující adresáře:

- [Base aplikace]/[BinPath]/[název sestavení]. dll

- [Base aplikace]/[BinPath]/[název sestavení]/[název sestavení]. dll

#### <a name="probing-examples"></a>Příklady zjišťování

Tyto informace jsou uvedeny níže:

- Název odkazovaného sestavení: myAssembly

- Kořenový adresář aplikace:`http://www.code.microsoft.com`

- > element zjišťování v konfiguračním souboru určuje: bin. [ \<](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)

- Jazyková verze: de

Běhové testy protestují následující adresy URL:

- `http://www.code.microsoft.com/de/myAssembly.dll`

- `http://www.code.microsoft.com/de/myAssembly/myAssembly.dll`

- `http://www.code.microsoft.com/bin/de/myAssembly.dll`

- `http://www.code.microsoft.com/bin/de/myAssembly/myAssembly.dll`

##### <a name="multiple-assemblies-with-the-same-name"></a>Více sestavení se stejným názvem

Následující příklad ukazuje, jak nakonfigurovat více sestavení se stejným názvem.

```xml
<dependentAssembly>
   <assemblyIdentity name="Server" publicKeyToken="c0305c36380ba429" />
   <codeBase version="1.0.0.0" href="v1/Server.dll" />
   <codeBase version="2.0.0.0" href="v2/Server.dll" />
</dependentAssembly>
```

#### <a name="other-locations-probed"></a>Protestovaná jiná umístění

Umístění sestavení lze také určit pomocí aktuálního kontextu vazby. K tomu nejčastěji dochází při <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> použití metody a ve scénářích komunikace s objekty com. Pokud sestavení používá <xref:System.Reflection.Assembly.LoadFrom%2A> metodu pro odkazování na jiné sestavení, volání umístění sestavení je považováno za pomocný parametr, kde najít odkazované sestavení. Pokud je nalezena shoda, je sestavení načteno. Pokud není nalezena žádná shoda, modul runtime pokračuje s jeho sémantikou hledání a poté zadá dotaz na Instalační služba systému Windows k poskytnutí sestavení. Pokud není k dispozici žádné sestavení, které odpovídá požadavku vazby, je vyvolána výjimka. Tato výjimka je <xref:System.TypeLoadException> ve spravovaném kódu, pokud byl odkazován na typ, <xref:System.IO.FileNotFoundException> nebo pokud nebylo nalezeno sestavení, které bylo načteno.

Například pokud Assembly1 odkazuje na Assembly2 a assembly1 se stáhl z `http://www.code.microsoft.com/utils`, toto umístění je považováno za pomocný parametr, kde najít Assembly2. dll. Modul runtime pak sondy pro sestavení v `http://www.code.microsoft.com/utils/Assembly2.dll` a. `http://www.code.microsoft.com/utils/Assembly2/Assembly2.dll` Pokud Assembly2 nebyl nalezen v jednom z těchto umístění, modul runtime dotazuje Instalační služba systému Windows.

## <a name="see-also"></a>Viz také:

- [Doporučené postupy pro načtení sestavení](../../../docs/framework/deployment/best-practices-for-assembly-loading.md)
- [Nasazení](../../../docs/framework/deployment/index.md)
