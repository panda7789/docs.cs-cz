---
title: "Jak běhové prostředí vyhledává sestavení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- app.config files, assembly locations
- deploying applications [.NET Framework], assembly locations
- application configuration files, locating assemblies
- .NET Framework application deployment, locating assemblies
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 772ac6f4-64d2-4cfb-92fd-58096dcd6c34
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 97a56a095c1b0c080cd3df329fce0085dd01af23
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-the-runtime-locates-assemblies"></a>Jak běhové prostředí vyhledává sestavení
Pokud chcete úspěšně nasadit aplikace rozhraní .NET Framework, musíte pochopit, jak modul common language runtime vyhledá a váže k sestavení, které tvoří vaši aplikaci. Ve výchozím modulu runtime pokusí vytvořit vazbu s přesnou verzi sestavení, která byla vytvořena s. Toto výchozí chování můžete přepsat pomocí souboru nastavení konfigurace.  
  
 Modul common language runtime provede několik kroků při pokusu o vyhledání sestavení a vyřešit odkaz na sestavení. V následujících částech je vysvětlení jednotlivých kroků. Termín zkušební fáze se často používá, když popisující, jak běhové prostředí vyhledává sestavení; odkazuje na sadu heuristiky používaná k nalezení sestavení na základě jeho název a jazykovou verzi.  
  
> [!NOTE]
>  Můžete zobrazit informace o vazbě v souboru protokolu pomocí [Prohlížeč protokolu vazby sestavení (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md), který je součástí [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].  
  
## <a name="initiating-the-bind"></a>Probíhá inicializace vazeb  
 Proces vyhledávání a vytvoření vazby na sestavení začíná, když modul runtime pokusí přeložit odkaz na jiné sestavení. Tento odkaz může být statické nebo dynamické. Statické odkazy kompilátoru záznamy v metadatech manifest sestavení v čas sestavení. Dynamické odkazy se vytvářejí za chodu v důsledku volání metody různé metody, jako například <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>.  
  
 Preferovaný způsob, jak odkazovat na sestavení, je použití úplné informace, včetně název sestavení, verzi, jazykovou verzi a tokenu veřejného klíče (pokud existuje). Modul runtime používá tyto informace k vyhledání sestavení, proveďte kroky popsané dál v této části. Modul runtime používá stejného procesu bez ohledu na to, jestli je odkaz pro statickou nebo dynamickou sestavení.  
  
 Dynamické odkaz na sestavení můžete provést také tím, že poskytuje volání metody s pouze částečný informace o sestavení, např. zadat jenom název sestavení. V takovém případě pouze v adresáři aplikace, je prohledána sestavení a žádná další kontrola proběhne. Vytvoříte částečné odkaz pomocí různých metod pro načtení sestavení, jako <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> nebo <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>.  
  
 Nakonec můžete provést pomocí jiné metody, jako dynamické odkaz <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> a obsahují jenom částečnou informace; potom kvalifikaci pomocí odkazu [ \<qualifyassembly – >](../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md) element v aplikaci konfigurační soubor. Tento element umožňuje poskytovat úplné referenční informace (název, verzi, jazykovou verzi a, pokud je k dispozici, token veřejného klíče) v konfiguračním souboru aplikace místo v kódu. Pokud byste chtěli plně kvalifikovaný odkaz na sestavení mimo adresář aplikace nebo pokud jste chtěli odkazování na sestavení v globální mezipaměti sestavení, ale chtěli pohodlí určení úplné odkaz v použijete tento postup konfigurační soubor místo v kódu.  
  
> [!NOTE]
>  Tento typ odkazu na částečné nepoužívejte s sestavení, které jsou sdíleny mezi více aplikacemi. Protože nastavení konfigurace se použijí na aplikaci a na sestavení, nebude vyžadovat sdílené sestavení pomocí tohoto typu odkaz na částečné každou aplikaci pomocí sdíleného sestavení tak, aby měl opravňující informace v konfiguračního souboru.  
  
 Modul runtime používá následující kroky k vyřešení odkaz na sestavení:  
  
1.  [Určuje verzi správné sestavení](#step1) tak, že prověří použít konfigurační soubory, včetně konfiguračního souboru aplikace, soubor zásad vydavatele a konfiguračním souboru počítače. Pokud se konfigurační soubor nachází ve vzdáleném počítači, modul runtime musí vyhledat a stáhnout konfigurační soubor aplikace nejdřív.  
  
2.  [Kontroluje, zda název sestavení bylo svázáno se před](#step2) a pokud ano, použije dříve načíst sestavení. Pokud předchozí žádost o načtení sestavení se nezdařilo, požadavek se nezdařilo okamžitě bez pokusu o načtení sestavení.  
  
    > [!NOTE]
    >  Ukládání do mezipaměti selhání vazby sestavení je v rozhraní .NET Framework verze 2.0 nová.  
  
3.  [Kontroluje globální mezipaměti sestavení](#step3). Pokud je nalezeny sestavení, modul runtime používá toto sestavení.  
  
4.  [Testy pro sestavení](#step4) pomocí následujících kroků:  
  
    1.  Pokud zásady Konfigurace a vydavatele neovlivní původní odkaz, a pokud vazby byla vytvořena pomocí <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metoda, běhové prostředí vyhledává pomocné parametry umístění.  
  
    2.  Pokud codebase najde v konfiguračních souborech, modulu runtime kontroluje pouze toto umístění. Pokud tento test nezdaří, běhové prostředí zjistí, že vazba požadavek se nezdařil a žádné jiné zjišťování dojde.  
  
    3.  Testy pro sestavení pomocí heuristické metody popsané v [zjišťování části](#step4). Pokud sestavení nebyl nalezen po zjišťování, požadavků modulu runtime Instalační služby systému Windows k poskytování sestavení. Jde o funkci instalace na vyžádání.  
  
        > [!NOTE]
        >  Verze vyhledává sestavení bez silné názvy neexistuje, ani nebude zkontrolujte soubor modulu runtime v globální mezipaměti sestavení pro sestavení bez silné názvy.  
  
<a name="step1"></a>   
## <a name="step-1-examining-the-configuration-files"></a>Krok 1: Zkoumání konfiguračních souborů  
 Chování vazby sestavení, můžete nakonfigurovat na různých úrovních, které jsou založené na tři soubory XML:  
  
-   Konfigurační soubor aplikace.  
  
-   Soubor zásad vydavatele.  
  
-   Konfigurační soubor počítače.  
  
 Tyto soubory použijte stejnou syntaxi a zadejte informace, jako je přesměrování, umístění kódu, vazby a vazba režimy pro konkrétní sestavení. Každý konfigurační soubor může obsahovat [ \<assemblybinding – > element](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) , přesměruje proces vytváření vazby. Podřízených elementů [ \<assemblybinding – > element](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) zahrnují [ \<dependentAssembly > element](../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md). Podřízené objekty daného [ \<dependentAssembly > element](../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md) zahrnují [ \<assemblyIdentity > element](/visualstudio/deployment/assemblyidentity-element-clickonce-deployment), [ \<bindingRedirect > Element](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)a [ \<codeBase > element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md).  
  
> [!NOTE]
>  Informace o konfiguraci naleznete v souborech tři konfigurace; Ne všechny prvky jsou platné v všechny konfigurační soubory. Například vazby režim a informace o cestě privátní lze pouze v konfiguračním souboru aplikace. Úplný seznam informace, které je součástí každého souboru, najdete v části [konfigurace aplikací pomocí konfiguračními soubory](../../../docs/framework/configure-apps/index.md).  
  
### <a name="application-configuration-file"></a>Konfigurační soubor aplikace  
 Modul common language runtime nejdřív zkontroluje informace, který přepíše informace o verzi, které jsou uložené v manifestu volajícího sestavení konfiguračního souboru aplikace. Konfigurační soubor aplikace můžete nasadit aplikace, ale není nutné pro spuštění aplikace. Obvykle je téměř okamžitě načtení tohoto souboru, ale v situacích, kde je základní aplikace ve vzdáleném počítači, jako v případě pomocí Internet Exploreru webové konfigurace musí být soubor stažen.  
  
 Pro spustitelné soubory klienta konfiguračního souboru aplikace se nachází ve stejném adresáři jako spustitelný soubor aplikace a má stejný název základní jako spustitelný soubor s příponou .config. Například C:\Program Files\Myapp\Myapp.exe v souboru konfigurace je C:\Program Files\Myapp\Myapp.exe.config. Ve scénáři založené na prohlížeči, musíte použít soubor HTML  **\<odkaz >** element tak, aby explicitně odkazoval konfiguračního souboru.  
  
 Následující kód poskytuje jednoduchý příklad konfiguračního souboru aplikace. Tento příklad přidá <xref:System.Diagnostics.TextWriterTraceListener> k <xref:System.Diagnostics.Debug.Listeners%2A> kolekci, aby záznam informace o ladění do souboru.  
  
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
 Druhý modul runtime zkoumá soubor zásad vydavatele, pokud existuje. Vydavatel – soubory zásad se distribuují součást vydavatelem jako oprava nebo aktualizace sdílená součást. Tyto soubory obsahují informace o kompatibilitě vystavený vydavatele sdílená součást, která přesměruje odkaz na sestavení na novou verzi. Na rozdíl od aplikace a konfigurační soubory soubory zásad vydavatele jsou součástí vlastní sestavení, které musí být nainstalována v globální mezipaměti sestavení.  
  
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
  
 Pokud chcete vytvořit sestavení, můžete použít [Al.exe (Linker sestavení)](../../../docs/framework/tools/al-exe-assembly-linker.md) nástroj pomocí příkazu, například následující:  
  
```  
Al.exe /link:asm6.exe.config /out:policy.3.0.asm6.dll /keyfile: compatkey.dat /v:3.0.0.0  
```  
  
 `compatkey.dat`je soubor klíče se silným názvem. Tento příkaz vytvoří sestavení se silným názvem, který můžete umístit v globální mezipaměti sestavení.  
  
> [!NOTE]
>  Zásada vydavatele ovlivňuje všechny aplikace, které používají sdílené součásti.  
  
 Konfigurační soubor zásad vydavatele přepsání informace o verzi, která pochází z aplikace (tedy z manifestu sestavení nebo z konfiguračního souboru aplikace). Pokud není žádný příkaz v konfiguračním souboru aplikace pro přesměrování verze zadaná v manifestu sestavení, přepíše soubor zásad vydavatele verze zadaná v manifestu sestavení. Ale pokud je přesměrování příkaz v konfiguračním souboru aplikace, vydavatele zásada přepíše této verze než verze zadaná v manifestu.  
  
 Soubor zásad vydavatele se používá při aktualizaci sdílené součásti a novou verzi sdílená součást by měl být zachyceny pomocí všech aplikací pomocí této součásti. Nastavení v souboru zásad vydavatele přednost před nastavením v konfiguračním souboru aplikace, pokud konfigurační soubor aplikace vynucuje nouzovém režimu.  
  
#### <a name="safe-mode"></a>Nouzový režim  
 Vydavatel – soubory zásad jsou obvykle explicitně nainstalován jako součást aktualizace service pack nebo program. Pokud je jakýkoli problém s upgradovaný sdílená součást, můžete ignorovat přepsání v souboru zásad vydavatele pomocí nouzového režimu. Nouzový režim je dáno  **\<publisherPolicy použít = "Ano**&#124; **Ne "/ >** elementu, nachází pouze v konfiguračním souboru aplikace. Určuje, zda informace o konfiguraci zásad vydavatele má být odebrána z proces vytváření vazby.  
  
 Nouzový režim lze nastavit pro celou aplikaci nebo pro vybrané sestavení. Můžete to znamená, vypněte tuto zásadu pro všechny sestavení, které tvoří aplikace nebo zapnout pro některá sestavení a jiné ne. Selektivně použít zásady vydavatele na sestavení, které tvoří aplikaci, nastavte  **\<publisherPolicy použít\=žádné / >** a zadejte sestavení, které chcete mít vliv na používání \< **dependentAssembly**> elementu. Chcete-li použít zásady vydavatele na všechny sestavení, které tvoří aplikace, nastavte  **\<publisherPolicy použít\=žádné / >** bez prvků závislého sestavení. Další informace o konfiguraci najdete v tématu [konfigurace aplikací pomocí konfiguračních souborů](../../../docs/framework/configure-apps/index.md).  
  
### <a name="machine-configuration-file"></a>Konfigurační soubor počítače  
 Třetí modul runtime zkoumá konfiguračním souboru počítače. Tento soubor s názvem souboru Machine.config, se nachází v místním počítači v podadresáři Config ke kořenovému adresáři, kde je nainstalován modul runtime. Tento soubor lze správci můžete určit omezení vazby sestavení, které jsou místní vzhledem k tomuto počítači. Nastavení v konfiguračním souboru počítače mají přednost před všechny ostatní nastavení konfigurace. však neznamená to, že všechna nastavení konfigurace měly být umístěny do tohoto souboru. Verze určený soubor zásad, který správce je posledním a nelze přepsat. Přepsání zadaná v souboru Machine.config ovlivňují všechny aplikace. Další informace o konfiguračních souborech najdete v tématu [konfigurace aplikací pomocí konfiguračních souborů](../../../docs/framework/configure-apps/index.md).  
  
<a name="step2"></a>   
## <a name="step-2-checking-for-previously-referenced-assemblies"></a>Krok 2: Kontrola dříve odkazovaných sestavení  
 Pokud požadovaný sestavení požaduje také v předchozích volání, používá modul common language runtime sestavení, které je již načten. Následky to může mít v názvu sestavení, které tvoří aplikaci. Další informace o pojmenování sestavení najdete v tématu [názvy sestavení](../../../docs/framework/app-domains/assembly-names.md).  
  
 Pokud předchozí žádost o assembly se nezdařil, odeslání dalších žádostí o sestavení došlo k selhání okamžitě bez pokusu o načtení sestavení. Od verze rozhraní .NET Framework verze 2.0, selhání vazby sestavení jsou do mezipaměti, a informace uložené v mezipaměti se používá k určení, jestli se má pokus o načtení sestavení.  
  
> [!NOTE]
>  Vrátit se do chování rozhraní .NET Framework verze 1.0 a 1.1, který do mezipaměti selhání vazby, zahrňte [ \<disablecachingbindingfailures – > Element](../../../docs/framework/configure-apps/file-schema/runtime/disablecachingbindingfailures-element.md) v konfiguračním souboru.  
  
<a name="step3"></a>   
## <a name="step-3-checking-the-global-assembly-cache"></a>Krok 3: Kontrola globální mezipaměti sestavení  
 Pro sestavení se silným názvem proces vytváření vazby pokračuje tak, že vyhledá v globální mezipaměti sestavení. Globální mezipaměti sestavení uchovává sestavení, které lze použít více aplikacemi v počítači. Všechna sestavení v globální mezipaměti sestavení musí mít silné názvy.  
  
<a name="step4"></a>   
## <a name="step-4-locating-the-assembly-through-codebases-or-probing"></a>Krok 4: Vyhledání sestavení prostřednictvím základů kódu nebo zjišťování  
 Po určil verze správné sestavení pomocí informací v odkaz volajícího sestavení a konfigurační soubory a poté, co byl zkontrolován v globální mezipaměti sestavení (pouze pro sestavení se silným názvem), běžné jazyk modul runtime, pokusí se najít sestavení. Proces vyhledávání sestavení zahrnuje následující kroky:  
  
1.  Pokud [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) nebyl nalezen v konfiguračním souboru aplikace, modulu runtime kontroluje v zadaném umístění. Pokud je nalezena shoda, se používá toto sestavení a žádné zjišťování dojde. Pokud nejsou nalezena sestavení, žádost vazba se nezdaří.  
  
2.  Modul runtime pak sondy pro odkazované sestavení pomocí pravidel zadat později v této části.  
  
> [!NOTE]
>  Pokud máte více verzí sestavení v adresáři a chcete odkazovat na konkrétní verzi tohoto sestavení, je nutné použít [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) element místo `privatePath` atribut [ \<zjišťování >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) element. Pokud použijete [ \<zjišťování >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) element, modul runtime zastaví zjišťování poprvé najde sestavení, které odpovídá názvu jednoduché sestavení odkazováno, zda je správný shody, nebo ne. Pokud je správná shoda, použije se toto sestavení. Pokud není správný shodu, zjišťování zastaví a vazba se nezdaří.  
  
### <a name="locating-the-assembly-through-codebases"></a>Vyhledání sestavení pomocí základy kódu  
 CODEBASE informace lze zadat pomocí [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) element v konfiguračním souboru. Tento kód je vždy zaškrtnuto před modulu runtime pokusí testu pro odkazované sestavení. Pokud soubor zásad vydavatele obsahující přesměrování finální verzi také obsahuje [ \<základu kódu >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) element, který [ \<základu kódu >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) element je ten, který se používá. Například, pokud určuje konfiguračním souboru aplikace [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) také určuje element a soubor zásad vydavatele, který je přepsání informace o aplikaci [ \< codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) elementu, [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) element v souboru vydavatele zásad se používá.  
  
 Pokud není nalezena žádná shoda v umístění, které [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) elementu vazby požadavek selže a jsou přesměrováni žádné další kroky. Pokud modul runtime určuje, že sestavení odpovídá kritériím volajícího sestavení, použije toto sestavení. Když soubor určeného v dané [ \<základu kódu >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) elementu je načtena, modul runtime zkontroluje, abyste měli jistotu, že název, verzi, jazykovou verzi a veřejný klíč odpovídat volajícího sestavení je odkaz.  
  
> [!NOTE]
>  Odkazovaná sestavení mimo kořenový adresář aplikace musí mít silné názvy a buď musí být nainstalována v globální mezipaměti sestavení nebo zadán pomocí [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) element.  
  
### <a name="locating-the-assembly-through-probing"></a>Vyhledání sestavení pomocí zjišťování  
 Pokud není žádná [ \<základu kódu >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) element v konfiguračním souboru aplikace, modulu runtime sondy pro sestavení pomocí čtyř kritéria:  
  
-   Základ cesty aplikace, která je kořenový adresář, kde se spouští aplikace.  
  
-   Jazyková verze, která je atribut jazykovou verzi sestavení se na ně odkazovat.  
  
-   Název, který je název odkazované sestavení.  
  
-   `privatePath` Atribut [ \<zjišťování >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) element, který je uživatelem definované seznam podadresářů kořenový adresář. Toto umístění může být zadán v konfiguračním souboru aplikace a spravovaného kódu pomocí <xref:System.AppDomain.AppendPrivatePath%2A> vlastnost pro doménu aplikace. Pokud zadaný ve spravovaném kódu, spravovaného kódu `privatePath` je zjištěný první, a cesty zadané v konfiguračním souboru aplikace.  
  
#### <a name="probing-the-application-base-and-culture-directories"></a>Zkušební fáze základ cesty aplikace a adresáře jazykovou verzi  
 Modul runtime vždy začne zkušební fáze v základní aplikace, což může být adresa URL nebo kořenový adresář aplikace do počítače. Pokud odkazované sestavení nebyl nalezen v základní aplikace a je k dispozici žádné informace o jazykové verzi, modul runtime prohledá všechny podadresáře s název sestavení. Zahrnout adresáře, zjištěný:  
  
 [základ cesty aplikace] / [název sestavení] .dll  
  
 [základ cesty aplikace] / [název sestavení] / [název sestavení] .dll  
  
 Pokud se informace o jazykové verzi je zadán pro odkazované sestavení, jsou zjištěný pouze následující adresáře:  
  
 [základ cesty aplikace] / [culture] / [název sestavení] .dll  
  
 [základ cesty aplikace] / [culture] / [název sestavení] / [název sestavení] .dll  
  
#### <a name="probing-with-the-privatepath-attribute"></a>Zkušební fáze s privatePath atribut  
 Kromě podadresáře jazykovou verzi a podadresáře pro odkazované sestavení s názvem modulu runtime také sondy adresáře určené pomocí `privatePath` atribut [ \<zjišťování >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) element. Adresáře zadán pomocí `privatePath` atribut musí být podadresáře kořenového adresáře aplikace. Adresáře zjištěný lišit v závislosti na tom, zda informace o jazykové verzi je součástí požadavku odkazované sestavení.  
  
 Modul runtime zastaví zjišťování poprvé, které nalezne sestavení, které odpovídá názvu jednoduché sestavení odkazováno, zda je správný shody, nebo ne. Pokud je správná shoda, použije se toto sestavení. Pokud není správný shodu, zjišťování zastaví a vazba se nezdaří.  
  
 Pokud je zahrnuto jazykovou verzi, jsou zjištěný následující adresáře:  
  
 [základ cesty aplikace] nebo [cesta] / [culture] / [název sestavení] .dll  
  
 [základ cesty aplikace] nebo [cesta] / [culture] / [název sestavení] / [název sestavení] .dll  
  
 Pokud není součástí informací o jazykové verzi, jsou zjištěný následující adresáře:  
  
 [základ cesty aplikace] nebo [cesta] / [název sestavení] .dll  
  
 [základ cesty aplikace] nebo [cesta] / [název sestavení] / [název sestavení] .dll  
  
#### <a name="probing-examples"></a>Zkušební fáze příklady  
 Zadané následující informace:  
  
-   Název odkazovaného sestavení: myAssembly  
  
-   Kořenový adresář aplikace: http://www.code.microsoft.com  
  
-   [\<Zkušební fáze >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) určuje element v konfiguračním souboru: Koš  
  
-   Jazyková verze: de  
  
 Modul runtime sondy následující adresy URL:  
  
 http://www.Code.microsoft.com/de/myAssembly.dll  
  
 http://www.Code.microsoft.com/de/myAssembly/myAssembly.dll  
  
 http://www.Code.microsoft.com/bin/de/myAssembly.dll  
  
 http://www.Code.microsoft.com/bin/de/myAssembly/myAssembly.dll  
  
##### <a name="multiple-assemblies-with-the-same-name"></a>Více sestavení se stejným názvem  
 Následující příklad ukazuje, jak nakonfigurovat více sestavení se stejným názvem.  
  
```xml  
<dependentAssembly>  
   <assemblyIdentity name="Server" publicKeyToken="c0305c36380ba429" />   
      <codeBase version="1.0.0.0" href="v1/Server.dll"/>  
      <codeBase version="2.0.0.0" href="v2/Server.dll"/>  
</dependentAssembly>  
```  
  
#### <a name="other-locations-probed"></a>Jiných umístění zjištěný  
 Umístění sestavení můžete také zjistit pomocí aktuálního kontextu vazby. Této chybě nejčastěji dochází při <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metoda se používá a ve scénářích zprostředkovatele komunikace s objekty COM. Pokud používá sestavení <xref:System.Reflection.Assembly.LoadFrom%2A> metodu pro referenční sestavení, umístění volajícího sestavení se považuje za nápovědu o tom, kde najít odkazované sestavení. Pokud je nalezena shoda, je načteno tohoto sestavení. Pokud není nalezena žádná shoda, modul runtime pokračuje v jeho sémantiku hledání a následně se dotazuje Instalační služby systému Windows k poskytování sestavení. Pokud žádné sestavení zadaný odpovídající vazby požadavek, je vyvolána výjimka. Tato výjimka je <xref:System.TypeLoadException> ve spravovaném kódu, pokud bylo odkazováno typ, nebo <xref:System.IO.FileNotFoundException> Pokud načítá sestavení nebyl nalezen.  
  
 Například pokud Assembly1 odkazuje Assembly2 a Assembly1 byl stažen z http://www.code.microsoft.com/utils, toto umístění se považuje za nápovědu o tom, kde najít Assembly2.dll. Modul runtime pak hledá sestavení v http://www.code.microsoft.com/utils/Assembly2.dll a http://www.code.microsoft.com/utils/Assembly2/Assembly2.dll. Pokud Assembly2 nebyl nalezen v žádném z těchto umístění, dotáže se modul runtime Instalační služby systému Windows.  
  
## <a name="see-also"></a>Viz také  
 [Doporučené postupy pro načtení sestavení](../../../docs/framework/deployment/best-practices-for-assembly-loading.md)  
 [Nasazení](../../../docs/framework/deployment/index.md)
