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
ms.openlocfilehash: 13e2661b67ba3b717b8917e80118175acb09e756
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181668"
---
# <a name="how-the-runtime-locates-assemblies"></a>Jak běhové prostředí vyhledává sestavení

Chcete-li úspěšně nasadit aplikaci rozhraní .NET Framework, musíte pochopit, jak soubor COMMON Language runtime vyhledá a váže se k sestavením, která tvoří vaši aplikaci. Ve výchozím nastavení se za běhu pokusí vytvořit vazbu s přesnou verzí sestavení, se kterou byla aplikace vytvořena. Toto výchozí chování může být přepsáno nastavením konfiguračního souboru.

Běžný jazyk runtime provádí řadu kroků při pokusu o vyhledání sestavení a vyřešit odkaz na sestavení. Každý krok je vysvětlen v následujících částech. Termín zjišťování se často používá při popisu, jak runtime vyhledá sestavení; odkazuje na sadu heuristiky použité k vyhledání sestavení na základě jeho názvu a jazykové verze.

> [!NOTE]
> Informace o vazbě v souboru protokolu můžete zobrazit pomocí [prohlížeče protokolů vazby sestavení (Fuslogvw.exe),](../tools/fuslogvw-exe-assembly-binding-log-viewer.md)který je součástí sady Windows SDK.

## <a name="initiating-the-bind"></a>Zahájení vazby

Proces vyhledání a vazby na sestavení začíná, když se za běhu pokusí vyřešit odkaz na jiné sestavení. Tento odkaz může být statický nebo dynamický. Kompilátor zaznamenává statické odkazy v metadatech manifestu sestavení v době sestavení. Dynamické odkazy jsou konstruovány za chodu v <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>důsledku volání různých metod, jako je například .

Upřednostňovaným způsobem odkazování na sestavení je použití úplného odkazu, včetně názvu sestavení, verze, jazykové verze a tokenu veřejného klíče (pokud existuje). Runtime používá tyto informace k vyhledání sestavení podle kroků popsaných dále v této části. Za běhu používá stejný proces rozlišení bez ohledu na to, zda je odkaz pro statické nebo dynamické sestavení.

Můžete také vytvořit dynamický odkaz na sestavení tím, že volající metodě poskytnete pouze částečné informace o sestavení, například zadání pouze názvu sestavení. V tomto případě je prohledán pouze adresář aplikace pro sestavení a nedojde k žádné jiné kontrole. Provést částečný odkaz pomocí některé z různých metod pro <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>načítání sestavení, jako je například nebo .

Nakonec můžete vytvořit dynamický odkaz pomocí metody, jako <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> je například a poskytnout pouze částečné informace; potom kvalifikujete odkaz pomocí prvku [ \<qualifyAssembly>](../configure-apps/file-schema/runtime/qualifyassembly-element.md) v konfiguračním souboru aplikace. Tento prvek umožňuje zadat úplné referenční informace (název, verze, jazyková verze a případně token veřejného klíče) v konfiguračním souboru aplikace namísto v kódu. Tento postup byste použili, pokud byste chtěli plně kvalifikovat odkaz na sestavení mimo adresář aplikace nebo pokud byste chtěli odkazovat na sestavení v globální mezipaměti sestavení, ale chtěli jste pohodlí určení úplného odkazu v konfiguračního souboru, nikoli v kódu.

> [!NOTE]
> Tento typ částečného odkazu by neměl být používán se sestaveními, které jsou sdíleny mezi několika aplikacemi. Vzhledem k tomu, že nastavení konfigurace jsou použita pro každou aplikaci a ne na sestavení, sdílené sestavení pomocí tohoto typu částečného odkazu by vyžadovalo, aby každá aplikace používající sdílené sestavení měla kvalifikační informace v konfiguračním souboru.

Runtime používá následující kroky k vyřešení odkazu na sestavení:

1. [Určuje správnou verzi sestavení](#step1) kontrolou příslušných konfiguračních souborů, včetně konfiguračního souboru aplikace, souboru zásad vydavatele a konfiguračního souboru počítače. Pokud je konfigurační soubor umístěn ve vzdáleném počítači, musí doba runtime nejprve vyhledat a stáhnout konfigurační soubor aplikace.

2. [Zkontroluje, zda byl název sestavení vázán na před](#step2) a pokud ano, používá dříve načtené sestavení. Pokud předchozí požadavek na načtení sestavení se nezdařilo, požadavek se nezdařil okamžitě bez pokusu o načtení sestavení.

    > [!NOTE]
    > Ukládání chyb vazby sestavení do mezipaměti je nové v rozhraní .NET Framework verze 2.0.

3. [Zkontroluje globální mezipaměť sestavení](#step3). Pokud je zde sestavení nalezeno, runtime používá toto sestavení.

4. [Sondy pro sestavu](#step4) pomocí následujících kroků:

    1. Pokud zásady konfigurace a vydavatele nemají vliv na původní <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> odkaz a požadavek na vazby byl vytvořen pomocí metody, runtime zkontroluje rady při umístění.

    2. Pokud je v konfiguračních souborech nalezen základ kódu, runtime zkontroluje pouze toto umístění. Pokud se tato sonda nezdaří, za běhu určuje, že požadavek na vazbu se nezdařila a dojde k žádné jiné zjišťování.

    3. Sondy pro sestavení pomocí heuristiky popsané v [části sondování](#step4). Pokud sestavení není nalezen po zjišťování, za běhu požaduje Instalační službu systému Windows poskytnout sestavení. To funguje jako funkce instalace na vyžádání.

        > [!NOTE]
        > Neexistuje žádná verze kontroly sestavení bez silných názvů, ani kontrola za běhu v globální mezipaměti sestavení pro sestavení bez silných názvů.

<a name="step1"></a>

## <a name="step-1-examining-the-configuration-files"></a>Krok 1: Zkoumání konfiguračních souborů

Chování vazby sestavení lze konfigurovat na různých úrovních na základě tří souborů XML:

- Konfigurační soubor aplikace.

- Soubor zásad aplikace Publisher.

- Konfigurační soubor počítače.

Tyto soubory postupujte podle stejné syntaxe a poskytují informace, jako je například přesměrování vazby, umístění kódu a režimy vazby pro konkrétní sestavení. Každý konfigurační soubor může obsahovat [ \<element> assemblyBinding,](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) který přesměruje proces vazby. Podřízené prvky [ \<elementu assemblyBinding>](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) zahrnují element [ \<dependentAssembly>](../configure-apps/file-schema/runtime/dependentassembly-element.md). Mezi podřízené prvky [ \<dependentAssembly>](../configure-apps/file-schema/runtime/dependentassembly-element.md) patří [ \<element assemblyIdentity>](/visualstudio/deployment/assemblyidentity-element-clickonce-deployment), [ \<element vazbyRedirect>](../configure-apps/file-schema/runtime/bindingredirect-element.md)a element [ \<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md).

> [!NOTE]
> Informace o konfiguraci lze nalézt ve třech konfiguračních souborech; ne všechny prvky jsou platné ve všech konfiguračních souborech. Například režim vazby a informace o soukromé cestě mohou být pouze v konfiguračním souboru aplikace. Úplný seznam informací obsažených v jednotlivých souborech naleznete v [tématu Konfigurace aplikací pomocí konfiguračních souborů](../configure-apps/index.md).

### <a name="application-configuration-file"></a>Konfigurační soubor aplikace

Za prvé, běžný jazyk runtime zkontroluje konfigurační soubor aplikace pro informace, které přepíše informace o verzi uložené v manifestu volajícího sestavení. Konfigurační soubor aplikace lze nasadit s aplikací, ale není vyžadován pro spuštění aplikace. Načítání tohoto souboru je obvykle téměř okamžité, ale v situacích, kdy je základna aplikace ve vzdáleném počítači, například ve scénáři založeném na webu aplikace Internet Explorer, musí být konfigurační soubor stažen.

U klientských spustitelných souborů je konfigurační soubor aplikace umístěn ve stejném adresáři jako spustitelný soubor aplikace a má stejný základní název jako spustitelný soubor s příponou .config. Konfigurační soubor pro nástroj C:\Program Files\Myapp\Myapp.exe je například C:\Program Files\Myapp\Myapp.exe.config. V případě prohlížeče musí soubor HTML použít ** \<odkaz>** element explicitně přejděte na konfigurační soubor.

Následující kód poskytuje jednoduchý příklad konfiguračního souboru aplikace. Tento příklad <xref:System.Diagnostics.TextWriterTraceListener> přidá <xref:System.Diagnostics.Debug.Listeners%2A> do kolekce povolit záznam ladicí informace do souboru.

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

### <a name="publisher-policy-file"></a>Soubor zásad aplikace Publisher

Za druhé, runtime zkontroluje soubor zásad vydavatele, pokud existuje. Soubory zásad aplikace Publisher jsou distribuovány vydavatelem součásti jako oprava nebo aktualizace sdílené součásti. Tyto soubory obsahují informace o kompatibilitě vydané vydavatelem sdílené součásti, která směruje odkaz na sestavení na novou verzi. Na rozdíl od konfiguračních souborů aplikací a počítačů jsou soubory zásad vydavatele obsaženy ve vlastním sestavení, které musí být nainstalováno v globální mezipaměti sestavení.

Následuje příklad konfiguračního souboru zásad aplikace Publisher:

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

Chcete-li vytvořit sestavu, můžete použít nástroj [Al.exe (Assembly Linker)](../tools/al-exe-assembly-linker.md) s příkazem, například následujícím:

```console
Al.exe /link:asm6.exe.config /out:policy.3.0.asm6.dll /keyfile: compatkey.dat /v:3.0.0.0
```

`compatkey.dat`je soubor klíče se silným názvem. Tento příkaz vytvoří sestavení se silným názvem, které můžete umístit do globální mezipaměti sestavení.

> [!NOTE]
> Zásady aplikace Publisher ovlivňují všechny aplikace, které používají sdílenou komponentu.

Konfigurační soubor zásad vydavatele přepíše informace o verzi, které pocházejí z aplikace (to znamená z manifestu sestavení nebo z konfiguračního souboru aplikace). Pokud v konfiguračním souboru aplikace není žádný příkaz k přesměrování verze určené v manifestu sestavení, přepíše soubor zásad vydavatele verzi zadanou v manifestu sestavení. Pokud je však v konfiguračním souboru aplikace příkazrekonázy, zásady vydavatele tuto verzi přepíší, nikoli verzi zadanou v manifestu.

Soubor zásad vydavatele se používá při aktualizaci sdílené součásti a nová verze sdílené součásti by měla být zachycena všemi aplikacemi používajícími tuto komponentu. Nastavení v souboru zásad vydavatele přepíše nastavení v konfiguračním souboru aplikace, pokud konfigurační soubor aplikace nevynucuje nouzový režim.

#### <a name="safe-mode"></a>Nouzový režim
Soubory zásad aplikace Publisher jsou obvykle explicitně nainstalovány jako součást aktualizace Service Pack nebo programu. Pokud dojde k potížím s inovou sdílenou komponentou, můžete přepsání v souboru zásad vydavatele ignorovat v nouzovém režimu. Nouzový režim je určen ** \<publisherPolicy apply="yes**&#124;**no"/>** element, který se nachází pouze v konfiguračním souboru aplikace. Určuje, zda mají být informace o konfiguraci zásad vydavatele odebrány z procesu vazby.

Nouzový režim lze nastavit pro celou aplikaci nebo pro vybraná sestavení. To znamená, že můžete vypnout zásady pro všechna sestavení, která tvoří aplikaci, nebo ji zapnout pro některá sestavení, ale ne pro jiná. Chcete-li selektivně použít zásady vydavatele na sestavení, která tvoří aplikaci, ** \<nastavte publisherPolicy\=no/>** a určete, která sestavení chcete ovlivnit pomocí \<prvku **dependentAssembly**>. Chcete-li použít zásady vydavatele pro všechna sestavení, která tvoří aplikaci, ** \<nastavte publisherPolicy použít\=no/>** bez závislých prvků sestavení. Další informace o konfiguraci [najdete v tématu Konfigurace aplikací pomocí konfiguračních souborů](../configure-apps/index.md).

### <a name="machine-configuration-file"></a>Konfigurační soubor počítače
Za třetí, runtime zkontroluje konfigurační soubor počítače. Tento soubor, nazvaný Machine.config, je umístěn v místním počítači v podadresáři konfigurace kořenového adresáře, ve kterém je nainstalován soubor runtime. Tento soubor může být použit správci k určení omezení vazeb sestavení, které jsou místní pro tento počítač. Nastavení v konfiguračním souboru počítače mají přednost před všemi ostatními nastaveními konfigurace. to však neznamená, že by měla být do tohoto souboru vložena všechna nastavení konfigurace. Verze určená souborem zásad správce je konečná a nelze ji přepsat. Lokální změny zadané v souboru Machine.config ovlivní všechny aplikace. Další informace o konfiguračních souborech naleznete [v tématu Konfigurace aplikací pomocí konfiguračních souborů](../configure-apps/index.md).

<a name="step2"></a>

## <a name="step-2-checking-for-previously-referenced-assemblies"></a>Krok 2: Kontrola dříve odkazovaných sestavení

Pokud požadované sestavení bylo požadováno také v předchozích voláních, za běhu společného jazyka používá sestavení, které je již načteno. To může mít důsledky při pojmenování sestavení, které tvoří aplikaci. Další informace o pojmenování sestavení naleznete v tématu [Názvy sestavení](../../standard/assembly/names.md).

Pokud předchozí požadavek na sestavení se nezdařilo, následné požadavky na sestavení se nezdaří okamžitě bez pokusu o načtení sestavení. Počínaje rozhraním .NET Framework verze 2.0 jsou chyby vazby sestavení uloženy do mezipaměti a informace uložené v mezipaměti se používají k určení, zda se má pokusit načíst sestavení.

> [!NOTE]
> Chcete-li se vrátit k chování rozhraní .NET Framework verze 1.0 a 1.1, který neměl cache selhání vazby, patří [ \<disableCachingBindingFailures> Element](../configure-apps/file-schema/runtime/disablecachingbindingfailures-element.md) v konfiguračním souboru.

<a name="step3"></a>

## <a name="step-3-checking-the-global-assembly-cache"></a>Krok 3: Kontrola globální mezipaměti sestavení

U sestavení se silným názvem pokračuje proces vazby hledáním v globální mezipaměti sestavení. Globální mezipaměti sestavení ukládá sestavení, která lze použít několik aplikací v počítači. Všechna sestavení v globální mezipaměti sestavení musí mít silné názvy.

<a name="step4"></a>

## <a name="step-4-locating-the-assembly-through-codebases-or-probing"></a>Krok 4: Vyhledání sestavení prostřednictvím základů kódu nebo zjišťování

Po správné verze sestavení byla určena pomocí informací v odkazu volající sestavení a v konfiguračních souborů a poté, co má zkontrolovat v globální mezipaměti sestavení (pouze pro sestavení se silným názvem), společný jazyk runtime se pokusí najít sestavení. Proces vyhledání sestavení zahrnuje následující kroky:

1. Pokud [ \<](../configure-apps/file-schema/runtime/codebase-element.md) je v konfiguračním souboru aplikace nalezen element codeBase>, runtime zkontroluje zadané umístění. Pokud je nalezena shoda, toto sestavení se používá a dojde k žádné zjišťování. Pokud sestavení není nalezen, požadavek na vazbu se nezdaří.

2. Runtime pak sonduje pro odkazované sestavení pomocí pravidel uvedených dále v této části.

> [!NOTE]
> Pokud máte více verzí sestavení v adresáři a chcete odkazovat na určitou verzi tohoto sestavení, musíte `privatePath` použít [ \<element codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) namísto atributu [ \<>](../configure-apps/file-schema/runtime/probing-element.md) prvku zjišťování. Pokud použijete [ \<sondování>](../configure-apps/file-schema/runtime/probing-element.md) prvek, za běhu zastaví zjišťování při prvním najde sestavení, které odpovídá jednoduchý název sestavení odkazuje, zda je správná shoda nebo ne. Pokud se jedná o správnou shodu, použije se toto sestavení. Pokud není správná shoda, sondování zastaví a vazba se nezdaří.

### <a name="locating-the-assembly-through-codebases"></a>Vyhledání sestavení pomocí základů kódu

Informace o základu kódu lze poskytnout pomocí prvku [ \<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) v konfiguračním souboru. Tento základ kódu je vždy kontrolována před runtime pokusí sonda pro odkazované sestavení. Pokud soubor zásad vydavatele obsahující konečné přesměrování verze také obsahuje [ \<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) element, tento [ \<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) prvek je ten, který se používá. Pokud například konfigurační soubor aplikace určuje element [ \<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) element a soubor zásad vydavatele, který přepíše informace o aplikaci, také určuje element [ \<codeBase>,](../configure-apps/file-schema/runtime/codebase-element.md) použije se prvek [ \<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) v souboru zásad vydavatele.

Pokud není nalezena žádná shoda v umístění určeném [ \<elementem codeBase>,](../configure-apps/file-schema/runtime/codebase-element.md) požadavek na vazby se nezdaří a nejsou podniknuty žádné další kroky. Pokud za běhu určuje, že sestavení odpovídá kritériím volajícího sestavení, použije toto sestavení. Při načtení souboru určeného daným [ \<elementem codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) se za běhu zkontroluje, zda název, verze, jazyková verze a veřejný klíč odpovídají odkazu volajícího sestavení.

> [!NOTE]
> Odkazovaná sestavení mimo kořenový adresář aplikace musí mít silné názvy a musí být nainstalována v globální mezipaměti sestavení nebo zadána pomocí elementu [ \<codeBase>.](../configure-apps/file-schema/runtime/codebase-element.md)

### <a name="locating-the-assembly-through-probing"></a>Lokalizace sestavy pomocí sondování

Pokud v konfiguračním souboru aplikace není žádný [ \<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) prvek, spustí se pro sestavení pomocí čtyř kritérií:

- Základ aplikace, což je kořenové umístění, kde je aplikace spuštěna.

- Jazyková verze, což je atribut jazykové verze odkazovaného sestavení.

- Název, což je název odkazovaného sestavení.

- Atribut `privatePath` [ \<sondování>](../configure-apps/file-schema/runtime/probing-element.md) prvek, což je uživatelem definovaný seznam podadresářů pod kořenovým umístěním. Toto umístění lze zadat v konfiguračním <xref:System.AppDomainSetup.PrivateBinPath?displayProperty=nameWithType> souboru aplikace a ve spravovaném kódu pomocí vlastnosti pro doménu aplikace. Pokud je zadán ve spravovaném kódu, je nejprve sondován spravovaný kód `privatePath` následovaný cestou zadanou v konfiguračním souboru aplikace.

#### <a name="probing-the-application-base-and-culture-directories"></a>Zjišťování adresářů základů aplikací a kultury

Runtime vždy začne sondování v základně aplikace, která může být buď URL nebo kořenový adresář aplikace v počítači. Pokud odkazované sestavení není v základu aplikace nalezeno a nejsou k dispozici žádné informace o jazykové verzi, za běhu vyhledá všechny podadresáře s názvem sestavení. Adresáře sondované patří:

- [základ aplikace] / [název sestavení].dll

- [základ aplikace] / [název sestavení] / [název sestavení].dll

Pokud jsou pro odkazované sestavení zadány informace o jazykové verzi, jsou sondovány pouze následující adresáře:

- [základ aplikace] / [culture] / [název sestavení].dll

- [základ aplikace] / [culture] / [název sestavení] / [název sestavení].dll

#### <a name="probing-with-the-privatepath-attribute"></a>Zjišťování pomocí atributu privatePath

Kromě podadresářů jazykové verze a podadresářů pojmenovaných pro odkazované sestavení, runtime také `privatePath` sonduje adresáře určené pomocí atributu [ \<zjišťování>](../configure-apps/file-schema/runtime/probing-element.md) prvku. Adresáře zadané pomocí `privatePath` atributu musí být podadresáře kořenového adresáře aplikace. Sondování adresářů se liší v závislosti na tom, zda jsou informace o jazykové verzi zahrnuty v požadavku odkazované sestavení.

Runtime zastaví zjišťování při prvním nalezne sestavení, které odpovídá jednoduché název sestavení odkazuje, zda je správná shoda nebo ne. Pokud se jedná o správnou shodu, použije se toto sestavení. Pokud není správná shoda, sondování zastaví a vazba se nezdaří.

Pokud je zahrnuta jazyková verze, jsou sondována následující adresáře:

- [základ aplikace] / [binpath] / [culture] / [název sestavení].dll

- [základ aplikace] / [binpath] / [culture] / [název sestavení] / [název sestavení].dll

Pokud informace o jazykové verzi není zahrnuta, jsou sondována následující adresáře:

- [základ aplikace] / [binpath] / [název sestavení].dll

- [základ aplikace] / [binpath] / [název sestavení] / [název sestavení].dll

#### <a name="probing-examples"></a>Sondování Příklady

S ohledem na tyto informace:

- Odkazovaný název sestavení: myAssembly

- Kořenový adresář aplikace:`http://www.code.microsoft.com`

- zjišťování>prvek v konfiguračním souboru určuje: bin [ \<](../configure-apps/file-schema/runtime/probing-element.md)

- Kultura: de

Runtime sonduje následující adresy URL:

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

#### <a name="other-locations-probed"></a>Další sondovaná místa

Umístění sestavení lze také určit pomocí aktuální kontext vazby. K tomu nejčastěji <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> dochází při použití metody a ve scénářích interop com. Pokud sestavení používá <xref:System.Reflection.Assembly.LoadFrom%2A> metodu k odkazování na jiné sestavení, umístění volajícího sestavení se považuje za nápovědu o tom, kde najít odkazované sestavení. Pokud je nalezena shoda, toto sestavení je načteno. Pokud není nalezena žádná shoda, runtime pokračuje sémantikou hledání a poté se dotazuje Instalační služby systému Windows na poskytnutí sestavení. Pokud není k dispozici žádné sestavení, které odpovídá požadavku na vazbu, je vyvolána výjimka. Tato výjimka <xref:System.TypeLoadException> je ve spravovaném kódu, pokud <xref:System.IO.FileNotFoundException> byl odkazován typ nebo pokud sestavení, které je načteno, nebylo nalezeno.

Například pokud Assembly1 odkazy Assembly2 a Assembly1 `http://www.code.microsoft.com/utils`byl stažen z , toto umístění je považováno za nápovědu o tom, kde najít Assembly2.dll. Runtime pak sonduje pro sestavení `http://www.code.microsoft.com/utils/Assembly2.dll` `http://www.code.microsoft.com/utils/Assembly2/Assembly2.dll`v a . Pokud Assembly2 není nalezen v jednom z těchto umístění, runtime dotazuje Instalační služba systému Windows.

## <a name="see-also"></a>Viz také

- [Doporučené postupy pro načtení sestavení](best-practices-for-assembly-loading.md)
- [Nasazení](index.md)
