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
ms.openlocfilehash: 250e1764084ba3f7750867f2eea89e87cc7239eb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59342335"
---
# <a name="how-the-runtime-locates-assemblies"></a>Jak běhové prostředí vyhledává sestavení
Pokud chcete úspěšně nasadit aplikaci rozhraní .NET Framework, musíte pochopit, jak modul common language runtime vyhledává a vazby k sestavením, které tvoří vaši aplikaci. Ve výchozím nastavení modul runtime pokusí vytvořit vazbu s přesnou verzi sestavení, na kterou byla aplikace vytvořena s. Toto výchozí chování můžete přepsat pomocí nastavení konfiguračního souboru.  
  
 Modul common language runtime provádí několik kroků při pokusu o nalezení sestavení a přeložit odkaz na sestavení. Každý krok je vysvětlené v následujících částech. Zjišťování termín se často používá při popisu, jak modul runtime vyhledává sestavení; odkazuje na sadu heuristik používaná k nalezení sestavení na základě jeho názvu a jazykovou verzi.  
  
> [!NOTE]
>  V souboru protokolu pomocí můžete zobrazit informace o vazbě [Assembly Binding Log Viewer (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md), které je součástí [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].  
  
## <a name="initiating-the-bind"></a>Zahajuje se vazba  
 Proces vyhledávání a vytvoření vazby na sestavení začíná, když modul runtime pokusí přeložit odkaz na jiné sestavení. Tento odkaz může být statická nebo dynamická. Záznamy kompilátoru statické odkazy v metadatech sestavení manifestu v okamžiku sestavení. Dynamické odkazy jsou vytvořeny v reálném čase v důsledku volání různých metod, jako například <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>.  
  
 Preferovaný způsob, jak odkazovat na sestavení, je použití úplné informace, včetně názvu sestavení, verzi, jazykovou verzi a token veřejného klíče (pokud existuje). Modul runtime používá tyto informace k nalezení sestavení, následující kroky popsané dále v této části. Modul runtime používá stejný postup řešení bez ohledu na to, zda je odkaz pro statické nebo dynamické sestavení.  
  
 Dynamické odkaz na sestavení můžete provést také tím, že poskytuje volání metody s pouze částečná informace o sestavení, např. Zadejte pouze název sestavení. V tomto případě pouze adresáře aplikace se hledá sestavení a žádná další kontrola vyvolá. Provedete částečný odkaz pomocí různých metod pro načtení sestavení, jako <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> nebo <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>.  
  
 A konečně, dokážete dynamické referenční pomocí metody, jako <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> a poskytují jenom částečné informace; potom kvalifikovat pomocí odkazu [ \<qualifyassembly – >](../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md) prvek v aplikaci konfigurační soubor. Tento prvek umožňuje poskytnout úplné referenční informace (název, verzi, jazykovou verzi a pokud je k dispozici, token veřejného klíče) v konfiguračním souboru aplikace místo v kódu. Pokud byste chtěli k plnému určení odkaz na sestavení mimo adresář aplikace, nebo pokud chcete odkazovat na sestavení v globální mezipaměti sestavení, ale chtěli jsme v pohodlí zadáte úplný přehled v použijete tento postup konfigurační soubor místo v kódu.  
  
> [!NOTE]
>  Tento typ částečný odkaz neměli použít se sestaveními, která jsou sdílena mezi několika aplikacemi. Protože nastavení konfigurace se použijí na aplikace a ne na sestavení, sdílené sestavení pomocí tohoto typu částečný odkaz by vyžadovaly každou aplikaci pomocí sdílené sestavení má oprávněným informace v souboru konfigurace.  
  
 Modul runtime používá následující kroky pro odkaz na sestavení:  
  
1. [Určuje verzi sestavení správné](#step1) prozkoumáním použít konfigurační soubory, včetně konfiguračního souboru aplikace, soubor zásad vydavatele a konfigurační soubor počítače. Pokud konfigurační soubor se nachází na vzdáleném počítači, musíte modul runtime vyhledat a stáhnout konfigurační soubor aplikace nejprve.  
  
2. [Kontroluje, zda název sestavení bylo svázáno se před](#step2) a pokud ano, pomocí dříve načteného sestavení. Předchozí požadavek na načtení sestavení se nezdařilo, pokud je žádost úspěšná okamžitě bez pokusu o načtení sestavení.  
  
    > [!NOTE]
    >  Ukládání do mezipaměti selhání vazby sestavení je v rozhraní .NET Framework verze 2.0 nová.  
  
3. [Zkontroluje globální mezipaměti sestavení](#step3). Pokud je sestavení nalezeno existuje, modul runtime používá toto sestavení.  
  
4. [Sondy pro sestavení](#step4) pomocí následujících kroků:  
  
    1.  Pokud zásady Konfigurace a vydavatel nemají vliv na původní odkaz a pokud vazba byla vytvořena pomocí <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metody, modul runtime vyhledává pomocné parametry umístění.  
  
    2.  Pokud je v konfiguračních souborech základ kódu, modul runtime kontroluje jenom toto umístění. Pokud tento test selže, modul runtime určuje, že požadavek na vytvoření vazby se nezdařilo a dojde k žádné další zjišťování.  
  
    3.  Sondy pro sestavení pomocí heuristické metody popsané v [testování části](#step4). Pokud sestavení není nalezen po zjišťování, modul runtime požádá o Instalační služby systému Windows k poskytování sestavení. To slouží jako funkce nainstalovat na vyžádání.  
  
        > [!NOTE]
        >  Neexistuje žádná verze kontrolují sestavení bez silných názvů ani nespouští kontrolu za modulu runtime v globální mezipaměti sestavení pro sestavení bez silných názvů.  
  
<a name="step1"></a>   
## <a name="step-1-examining-the-configuration-files"></a>Krok 1: Kontrola konfiguračních souborů  
 Chování vazby sestavení je možné nakonfigurovat na různých úrovních podle tři soubory XML:  
  
-   Konfigurační soubor aplikace.  
  
-   Soubor zásad vydavatele.  
  
-   Konfigurační soubor počítače.  
  
 Tyto soubory postupujte podle stejné syntaxe a poskytují informace, jako je přesměrování, umístění kódu, vazby a vazby režimy pro konkrétní sestavení. Každý konfigurační soubor může obsahovat [ \<assemblyBinding > element](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) , který přesměruje proces vytváření vazby. Podřízených elementů [ \<assemblyBinding > element](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) zahrnout [ \<dependentAssembly > element](../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md). Podřízené objekty daného [ \<dependentAssembly > element](../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md) zahrnout [ \<assemblyIdentity > element](/visualstudio/deployment/assemblyidentity-element-clickonce-deployment), [ \<bindingRedirect > Element](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)a [ \<codeBase > element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md).  
  
> [!NOTE]
>  Informace o konfiguraci najdete v souborech konfigurace na tři; Ne všechny prvky jsou platné v všechny konfigurační soubory. Například vazby režimu a privátní cesta informace lze pouze v konfiguračním souboru aplikace. Úplný seznam informace, které jsou obsaženy v jednotlivých souborech, naleznete v tématu [konfigurace aplikací pomocí konfiguračními soubory](../../../docs/framework/configure-apps/index.md).  
  
### <a name="application-configuration-file"></a>Konfigurační soubor aplikace  
 Modul common language runtime nejprve ověří konfigurační soubor aplikace pro informace, které přepíše informací o verzi uložených v manifestu volajícího sestavení. Konfigurační soubor aplikace je možné nasadit s aplikací, ale není potřeba pro spuštění aplikace. Obvykle je téměř okamžité načítání tohoto souboru, ale v situacích, kde základ cesty aplikace je na vzdáleném počítači, například ve scénáři založeného na webu Internet Explorer konfigurační soubor je nutné stáhnout.  
  
 Konfigurační soubor aplikace pro spustitelné soubory klienta, se nachází ve stejném adresáři jako spustitelný soubor aplikace a má stejný základní název jako spustitelný soubor s příponou .config. Například konfigurační soubor pro C:\Program Files\Myapp\Myapp.exe je C:\Program Files\Myapp\Myapp.exe.config. Ve scénáři založené na prohlížeči, musíte použít soubor HTML  **\<odkaz >** element explicitně odkazovat na konfigurační soubor.  
  
 Následující kód nabízí jednoduchý příklad konfiguračního souboru aplikace. V tomto příkladu přidá <xref:System.Diagnostics.TextWriterTraceListener> k <xref:System.Diagnostics.Debug.Listeners%2A> kolekci, aby záznam informace o ladění do souboru.  
  
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
 Za druhé modul runtime zkoumá soubor zásad vydavatele, pokud existuje. Soubory zásad vydavatele se distribuují komponenty vydavatelem jako oprava nebo aktualizace sdílené komponenty. Tyto soubory obsahují informace o kompatibilitě vydané vydavatele Sdílená komponenta, která přesměruje odkaz na sestavení na novou verzi. Na rozdíl od aplikace a konfigurační soubory soubory zásad vydavatele jsou součástí vlastní sestavení, musí být instalována v globální mezipaměti sestavení.  
  
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
  
 K vytvoření sestavení, můžete použít [Al.exe (Linker sestavení)](../../../docs/framework/tools/al-exe-assembly-linker.md) nástroj pomocí příkazu, jako je následující:  
  
```  
Al.exe /link:asm6.exe.config /out:policy.3.0.asm6.dll /keyfile: compatkey.dat /v:3.0.0.0  
```  
  
 `compatkey.dat` je soubor klíče se silným názvem. Tento příkaz vytvoří sestavení se silným názvem, který můžete umístit v globální mezipaměti sestavení.  
  
> [!NOTE]
>  Zásady vydavatele ovlivňuje všechny aplikace, které používají sdílené komponenty.  
  
 Konfigurační soubor zásad vydavatele přepíše informace o verzi, která pochází z aplikace (to znamená z manifestu sestavení nebo z konfiguračního souboru aplikace). Pokud není žádný příkaz k přesměrování verze určená v manifestu sestavení konfiguračního souboru aplikace, soubor zásad vydavatele přepsání verze určená v manifestu sestavení. Ale pokud je příkaz přesměrování konfiguračního souboru aplikace, zásady vydavatele přepíše tuto verzi než verze zadaná v manifestu.  
  
 Soubor zásad vydavatele se používá při aktualizaci sdílené komponenty a nová verze Sdílená komponenta by neexistoval, použije všemi aplikacemi pomocí této součásti. Nastavení v souboru zásad vydavatele přepsat nastavení konfiguračního souboru aplikace, pokud konfigurační soubor aplikace vynucuje Nouzový režim.  
  
#### <a name="safe-mode"></a>Nouzový režim  
 Soubory zásad vydavatele jsou obvykle nainstalován jako součást aktualizace service pack nebo program. Pokud je jakýkoli problém s upgradovaný sdílené komponenty, můžete ignorovat přepsání souboru zásad vydavatele pomocí nouzového režimu. Nouzový režim je určeno  **\<publisherPolicy použít = "Ano**&#124;**žádné" / >** element nachází pouze v konfiguračním souboru aplikace. Určuje, zda informace o konfiguraci zásad vydavatele by měl být odebrány proces vytváření vazby.  
  
 Nouzový režim můžete nastavit pro celou aplikaci nebo pro vybrané sestavení. To znamená vypněte tuto zásadu pro všechna sestavení, které aplikaci tvoří nebo ho zapnout pro některá sestavení, ale ne pro jiné. Chcete-li použít k sestavení, které tvoří aplikaci zásad vydavatele, nastavte  **\<použít publisherPolicy\=žádné / >** a zadejte sestavení, které chcete mít vliv na použití \< **dependentAssembly**> element. Chcete-li použít zásady vydavatele pro všechna sestavení, které aplikaci tvoří, nastavte  **\<použít publisherPolicy\=žádné / >** bez prvků závislého sestavení. Další informace o konfiguraci najdete v tématu [konfigurace aplikací pomocí konfiguračních souborů](../../../docs/framework/configure-apps/index.md).  
  
### <a name="machine-configuration-file"></a>Konfigurační soubor počítače  
 Třetí modul runtime zkoumá konfiguračního souboru počítače. Tento soubor s názvem souboru Machine.config, je umístěn v podadresáři konfigurace kořenového adresáře, kde je nainstalován modul runtime v místním počítači. Tento soubor umožňuje správci zadat omezení vazeb sestavení, která jsou vzhledem k tomuto počítači. Nastavení v konfiguračním souboru počítače přednost před všechny ostatní nastavení konfigurace. Nicméně to neznamená, že všechna nastavení konfigurace by měl být umístěny v tomto souboru. Verze Určuje soubor zásad, který správce je finální a nemůže být přepsána. Přepsání zadaná v souboru Machine.config ovlivňují všechny aplikace. Další informace o konfiguračních souborech najdete v tématu [konfigurace aplikací pomocí konfiguračních souborů](../../../docs/framework/configure-apps/index.md).  
  
<a name="step2"></a>   
## <a name="step-2-checking-for-previously-referenced-assemblies"></a>Krok 2: Kontrola dříve odkazovaných sestavení  
 Pokud požadovaná sestavení se požaduje také v předchozích volání, používá modul common language runtime sestavení, který je již načten. To může mít důsledky, při pojmenování sestavení, které tvoří aplikaci. Další informace o vytváření názvů sestavení naleznete v tématu [názvy sestavení](../../../docs/framework/app-domains/assembly-names.md).  
  
 Pokud předchozí žádost o sestavení se nezdařilo, odeslání dalších žádostí o sestavení se nepodařilo okamžitě bez pokusu o načtení sestavení. Od verze rozhraní .NET Framework verze 2.0, selhání vazby sestavení jsou uložené v mezipaměti, a informace uložené v mezipaměti se používá k určení, jestli se má pokus o načtení sestavení.  
  
> [!NOTE]
>  Pokud chcete vrátit k chování rozhraní .NET Framework verze 1.0 a 1.1, který do mezipaměti selhání vazby, zahrňte [ \<disablecachingbindingfailures – > Element](../../../docs/framework/configure-apps/file-schema/runtime/disablecachingbindingfailures-element.md) v konfiguračním souboru.  
  
<a name="step3"></a>   
## <a name="step-3-checking-the-global-assembly-cache"></a>Krok 3: Kontrola globální mezipaměti sestavení  
 Pro sestavení se silným názvem pokračuje proces vytváření vazby vyhledáváním v globální mezipaměti sestavení. Globální mezipaměti sestavení obsahuje sestavení, které lze použít více aplikacemi v počítači. Všechna sestavení v globální mezipaměti sestavení musí mít silné názvy.  
  
<a name="step4"></a>   
## <a name="step-4-locating-the-assembly-through-codebases-or-probing"></a>Krok 4: Vyhledání sestavení prostřednictvím základů kódu nebo zjišťování  
 Po verzi správné sestavení podle informací uvedených v odkazu na volajícího sestavení a v konfiguračních souborech a po jeho kontrole v globální mezipaměti sestavení (pouze pro sestavení se silným názvem), CLR modul runtime pokusí se najít sestavení. Proces vyhledávání sestavení zahrnuje následující kroky:  
  
1. Pokud [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) je nalezen element v konfiguračním souboru aplikace, modul runtime zkontroluje, zda zadané umístění. Pokud se najde shoda, toto sestavení se používá a bez testování dochází. Pokud sestavení není nalezen existuje, selže požadavek na vytvoření vazby.  
  
2. Modul runtime se pak sondy pro odkazované sestavení pomocí pravidel specifikovaných později v této části.  
  
> [!NOTE]
>  Pokud máte více verzí sestavení v adresáři a chcete odkazovat na konkrétní verzi sestavení, je nutné použít [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) elementu namísto `privatePath` atribut [ \<zjišťování >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) elementu. Pokud používáte [ \<zjišťování >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) elementu, modul runtime zastaví zjišťování poprvé vyhledá sestavení, která odpovídá názvu jednoduché sestavení odkazuje, ať už jde o správný shoda nebo ne. Pokud je správná shoda, použije se toto sestavení. Pokud není správná shoda, zjišťování zastaví a vazba se nezdaří.  
  
### <a name="locating-the-assembly-through-codebases"></a>Vyhledání sestavení prostřednictvím základů kódu  
 Základ kódu informace lze zadat pomocí [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) element v konfiguračním souboru. Tento základ kódu je vždy zaškrtnuto předtím, než se pokusí sběr dat pro odkazované sestavení modulu runtime. Pokud soubor zásad vydavatele obsahující přesměrování finální verze také obsahuje [ \<základu kódu >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) elementu, který [ \<základu kódu >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) element je ten, který se používá. Například, pokud Určuje konfigurační soubor aplikace [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) také určuje element a soubor zásad vydavatele, který přepisuje informace o aplikaci [ \< codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) elementu, [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) element v souboru zásad vydavatele se používá.  
  
 Pokud není nalezena žádná shoda v místě určeném [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) elementu vazby žádost selže a jsou přesměrováni žádné další kroky. Pokud modul runtime určuje, že sestavení by odpovídalo kritériím volajícího sestavení, použije se toto sestavení. Když soubor zadaný pomocí dané [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) elementu je načtena, modul runtime zkontroluje, abyste měli jistotu, že název, verzi, jazykovou verzi a veřejnému klíči odpovídat volající sestavení je odkazovat.  
  
> [!NOTE]
>  Odkazovaná sestavení mimo kořenový adresář aplikace musí mít silné názvy a musí být instalována v globální mezipaměti sestavení nebo zadat pomocí [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) elementu.  
  
### <a name="locating-the-assembly-through-probing"></a>Vyhledání sestavení prostřednictvím zjišťování  
 Pokud neexistuje žádné [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) prvku v konfiguračním souboru aplikace, modul runtime sondy pro sestavení s využitím čtyř kritéria:  
  
-   Základ cesty aplikace, což je kořenový adresář, ve kterém se aplikace zpracovává.  
  
-   Jazyková verze, která je atribut culture sestavení, na kterou se odkazuje.  
  
-   Název, který je název odkazovaného sestavení.  
  
-   `privatePath` Atribut [ \<zjišťování >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) prvku, který představuje uživatelem definovaný seznam podadresářů kořenový adresář. Toto umístění se dá nastavit v konfiguračním souboru aplikace a pomocí spravovaného kódu <xref:System.AppDomainSetup.PrivateBinPath?displayProperty=nameWithType> vlastnost pro doménu aplikace. Pokud zadaný ve spravovaném kódu, spravovaný kód `privatePath` je zjišťován nejprve, za nímž následuje cestě zadané v konfiguračním souboru aplikace.  
  
#### <a name="probing-the-application-base-and-culture-directories"></a>Zjišťování základ cesty aplikace a jazykové verze adresáře  
 Modul runtime vždy začíná zjišťování v základním vaší aplikace, který může být adresa URL nebo kořenového adresáře aplikace v počítači. Pokud má odkazované sestavení nebyl nalezen v základ cesty aplikace a je k dispozici žádné informace o jazykové verzi, modul runtime vyhledá všechny podadresáře, s názvem sestavení. Adresáře otestovaná patří:  
  
 [základ cesty aplikace] / [název sestavení] .dll  
  
 [základ cesty aplikace] / [název sestavení] / [název sestavení] .dll  
  
 Pokud informace o jazykové verzi je zadaný pro odkazované sestavení, vystavovány jsou pouze následující adresáře:  
  
 [základ cesty aplikace] / [culture] / [název sestavení] .dll  
  
 [základ cesty aplikace] / [culture] / [název sestavení] / [název sestavení] .dll  
  
#### <a name="probing-with-the-privatepath-attribute"></a>Testování s privatePath atribut  
 Kromě podadresáře jazykovou verzi a podadresářů pro odkazované sestavení s názvem, modul runtime také sondy adresáře určené pomocí `privatePath` atribut [ \<zjišťování >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) elementu. Adresáře určené pomocí `privatePath` atribut musí být podadresáře kořenového adresáře aplikace. Adresáře otestovaná se liší v závislosti na tom, zda informace o jazykové verzi je součástí žádosti o odkazovaném sestavení.  
  
 Modul runtime zastaví zjišťování prvním vyhledá sestavení, která odpovídá názvu jednoduché sestavení odkazuje, ať už jde o správný shoda nebo ne. Pokud je správná shoda, použije se toto sestavení. Pokud není správná shoda, zjišťování zastaví a vazba se nezdaří.  
  
 Pokud je zahrnuto jazykovou verzi, jsou otestovaná následující adresáře:  
  
 [základ cesty aplikace] / [cesta] / [culture] / [název sestavení] .dll  
  
 [základ cesty aplikace] / [cesta] / [culture] / [název sestavení] / [název sestavení] .dll  
  
 Pokud se informace o jazykové verzi neuvedete, jsou otestovaná následující adresáře:  
  
 [základ cesty aplikace] / [cesta] / [název sestavení] .dll  
  
 [základ cesty aplikace] / [cesta] / [název sestavení] / [název sestavení] .dll  
  
#### <a name="probing-examples"></a>Zjišťování příklady  
 Daný následující informace:  
  
-   Název odkazovaného sestavení: myAssembly  
  
-   Kořenový adresář aplikace: `http://www.code.microsoft.com`  
  
-   [\<zjišťování >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) určuje element v konfiguračním souboru: bin  
  
-   Jazyková verze: Německo  
  
 Modul runtime sondy následující adresy URL:  
  
 `http://www.code.microsoft.com/de/myAssembly.dll`
  
 `http://www.code.microsoft.com/de/myAssembly/myAssembly.dll`
  
 `http://www.code.microsoft.com/bin/de/myAssembly.dll`
  
 `http://www.code.microsoft.com/bin/de/myAssembly/myAssembly.dll`
  
##### <a name="multiple-assemblies-with-the-same-name"></a>Více sestavení se stejným názvem  
 Následující příklad ukazuje postup při konfiguraci několika sestavení se stejným názvem.  
  
```xml  
<dependentAssembly>  
   <assemblyIdentity name="Server" publicKeyToken="c0305c36380ba429" />   
   <codeBase version="1.0.0.0" href="v1/Server.dll" />  
   <codeBase version="2.0.0.0" href="v2/Server.dll" />  
</dependentAssembly>  
```  
  
#### <a name="other-locations-probed"></a>Jiné umístění otestovaná  
 Umístění sestavení můžete také určit pomocí aktuálního kontextu vazby. Této chybě nejčastěji dochází při <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metodu použít a ve scénářích vzájemné spolupráce COM. Pokud sestavení využívá <xref:System.Reflection.Assembly.LoadFrom%2A> metoda odkazovat na jiné sestavení volajícího sestavení umístění se považuje za nápovědu o tom, kde najít odkazované sestavení. Pokud se najde shoda, je načteno sestavení. Pokud není nalezena žádná shoda, modul runtime pokračuje s jeho sémantiku hledání a následně se dotazuje Instalační služby systému Windows k poskytování sestavení. Pokud žádné sestavení za předpokladu, který odpovídá požadavek na vytvoření vazby, je vyvolána výjimka. Tato výjimka je <xref:System.TypeLoadException> ve spravovaném kódu, pokud bylo odkazováno typ, nebo <xref:System.IO.FileNotFoundException> Pokud načítání sestavení nebyl nalezen.  
  
 Například pokud Assembly1 odkazuje Assembly2 a Assembly1 byl stažen z `http://www.code.microsoft.com/utils`, že umístění je považován za nápovědu o tom, kde najít Assembly2.dll. Modul runtime a testů pro sestavení v `http://www.code.microsoft.com/utils/Assembly2.dll` a `http://www.code.microsoft.com/utils/Assembly2/Assembly2.dll`. Pokud Assembly2 nebyl v některém z těchto míst, dotáže se modul runtime Instalační služby systému Windows.  
  
## <a name="see-also"></a>Viz také:

- [Doporučené postupy pro načtení sestavení](../../../docs/framework/deployment/best-practices-for-assembly-loading.md)
- [Nasazení](../../../docs/framework/deployment/index.md)
