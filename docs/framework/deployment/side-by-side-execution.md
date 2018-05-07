---
title: Souběžné spouštění v .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution
ms.assetid: 649f1342-766b-49e6-a90d-5b019a751e11
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea7a26a5b8ce0f30893e9ca66873ad61f82ff8df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="side-by-side-execution-in-the-net-framework"></a>Souběžné spouštění v .NET Framework
Souběžné spouštění je možnost spuštění několika verzí aplikace nebo komponenty v jednom počítači. V jednom počítači lze nainstalovat více verzí modulu CLR (Common Language Runtime) a několik verzí aplikací a komponent, které využívají verzi modulu runtime ve stejnou dobu.  
  
 Následující obrázek znázorňuje několik aplikací, které používají dvě různé verze modulu runtime v jednom počítači. Aplikace A, B a C používají modul runtime verze 1.0, zatímco aplikace D používá modul runtime verze 1.1.  
  
 ![Straně&#45;podle&#45;straně](../../../docs/framework/deployment/media/simplesbs.gif "simplesbs")  
Souběžné spouštění dvou verzí modulu runtime  
  
 Rozhraní .NET Framework zahrnuje modul CLR (Common Language Runtime) a kolekci sestavení, která obsahují typy rozhraní API. Modul runtime a sestavení rozhraní .NET Framework jsou opatřeny samostatnými verzemi. Například verze 4.0 modulu runtime je ve skutečnosti verzí 4.0.319, zatímco verze 1.0 sestavení rozhraní .NET Framework je verzí 1.0.3300.0.  
  
 Následující obrázek znázorňuje několik aplikací, které používají dvě různé verze komponenty na stejném počítači. Aplikace A a B používá verzi komponenty 1.0, zatímco aplikace C používá verzi 2.0 stejné komponenty.  
  
 ![Straně&#45;podle&#45;straně](../../../docs/framework/deployment/media/compsbs.gif "compsbs")  
Souběžné spouštění dvou verzí komponenty  
  
 Souběžné spouštění dává větší kontrolu nad tím, s jakou verzí komponenty je aplikace propojena, a větší kontrolu nad tím, jakou verzi modulu runtime aplikace používá.  
  
## <a name="benefits-of-side-by-side-execution"></a>Výhody souběžného spouštění  
 Před příchodem systému Windows XP a rozhraní .NET Framework docházelo ke konfliktům knihoven DLL, protože aplikace nebyla schopna rozlišovat mezi nekompatibilními verzemi stejného kódu. Informace o typu obsažené v knihovně DLL byly propojeny pouze s názvem souboru. Aplikace neměla žádnou možnost zjistit, zda typy obsažené v knihovně DLL jsou stejné jako ty, pomocí kterých byla aplikace sestavena. Ve výsledku mohla nová verze komponenty přepsat starší verzi a aplikace poškodit.  
  
 Souběžné spouštění a rozhraní .NET Framework poskytují následující funkce, které pomáhají předcházet konfliktům knihoven DLL:  
  
-   Sestavení se silným názvem.  
  
     Souběžné spouštění používá sestavení se silným názvem k vytvoření vazby informací o typu ke konkrétní verzi sestavení. Díky tomu aplikace nebo součást nevytvoří vazbu k neplatné verzi sestavení. Sestavení se silným názvem také umožňují, aby na stejném počítači existovalo více verzí souboru a aby je mohly využívat aplikace. Další informace najdete v tématu [sestavení se silným názvem](../../../docs/framework/app-domains/strong-named-assemblies.md).  
  
-   Úložiště kódu podporující verze.  
  
     Rozhraní .NET Framework poskytuje úložiště kódu podporující verze v globální mezipaměti sestavení (GAC). Globální mezipaměť sestavení (GAC) je mezipaměť kódu pro celý počítač, která je k dispozici na všech počítačích s nainstalovaným rozhraním .NET Framework. Jsou v ní uložena sestavení na základě informací o verzi, jazykové verzi a vydavateli a podporuje více verzí komponent a aplikací. Další informace najdete v tématu [globální mezipaměti sestavení](../../../docs/framework/app-domains/gac.md).  
  
-   Izolace.  
  
     Pomocí rozhraní .NET Framework lze vytvořit aplikace a komponenty, které jsou spouštěny v izolaci. Izolace je základní součástí souběžného spouštění. Zahrnuje znalost prostředků, které využíváte, a zkušenosti se sdílením prostředků napříč několika verzemi aplikace nebo komponenty. Izolace zahrnuje také ukládání souborů na základě verze. Další informace o izolaci najdete v tématu [pokyny pro vytváření komponent pro spuštění vedle sebe](../../../docs/framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).  
  
## <a name="version-compatibility"></a>Kompatibilita verzí  
 Verze 1.0 a 1.1 rozhraní .NET Framework jsou navrženy tak, aby byly navzájem kompatibilní. Aplikaci sestavenou pomocí verze 1.0 rozhraní .NET Framework lze spustit ve verzi 1.1 a aplikaci sestavenou pomocí verze 1.1 rozhraní .NET Framework lze spustit ve verzi 1.0. Funkce rozhraní API, které byly přidány ve verzi 1.1 rozhraní .NET Framework, však nebudou fungovat v rozhraní .NET Framework verze 1.0. Aplikace vytvořené pro verzi 2.0 lze spouštět pouze ve verzi 2.0. Aplikace pro verzi 2.0 nelze spustit ve verzi 1.1 nebo starší.  
  
 Verze rozhraní .NET Framework jsou považovány za celek, který sestává z modulu runtime a přidružených sestavení rozhraní .NET Framework (koncept se označuje jako sjednocení sestavení). Vazbu sestavení lze přesměrovat tak, aby zahrnovala další verze sestavení rozhraní .NET Framework. Přepsání výchozích vazeb sestavení však může být nebezpečné a je nutné je před nasazením pečlivě otestovat.  
  
## <a name="locating-runtime-version-information"></a>Vyhledání informací o verzi běhového prostředí  
 Informace, na které runtime verze aplikace nebo součásti bylo kompilováno s a jaké verze modulu runtime aplikace vyžaduje ke spuštění jsou uloženy ve dvou umístěních. Při kompilaci aplikace nebo součásti, informace o verzi modulu runtime používá ke kompilaci je uloženo v spravované spustitelný soubor. Informace o požadovaných aplikací nebo součástí modulu runtime verze je uložené v konfiguračním souboru aplikace.  
  
### <a name="runtime-version-information-in-the-managed-executable"></a>Informace o verzi modulu runtime v spravované spustitelný soubor  
 Přenosné záhlaví spustitelného souboru (PE) souboru každé spravované aplikace a součásti obsahuje informace o verzi modulu runtime, který byl sestaven s. Modul CLR používá tyto informace k určení nejpravděpodobnější verzi modulu runtime, které aplikace potřebuje ke spuštění.  
  
### <a name="runtime-version-information-in-the-application-configuration-file"></a>Informace o verzi modulu runtime v konfiguračním souboru aplikace  
 Kromě informací v záhlaví souboru PE lze nasadit aplikace s konfigurační soubor aplikace, která poskytuje informace o verzi modulu runtime. Konfigurační soubor aplikace je soubor na základě XML vytvořený vývojářem aplikace a který je součástí aplikace. [ \<RequiredRuntime > Element](../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) z [ \<spuštění > části](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md), pokud je k dispozici v tomto souboru Určuje, jaké verze modulu runtime a jaké verze součást aplikace podporuje. Tento soubor testování můžete použít také k testování kompatibility aplikace s různými verzemi modulu runtime.  
  
 Nespravovaný kód, včetně aplikace modelu COM a modelu COM +, může mít konfigurační soubory aplikace, které používá modul runtime pro interakci se spravovaným kódem. Konfigurační soubor aplikace ovlivňuje spravovaný kód, který je aktivovat pomocí modelu COM. Soubor můžete určit, které podporuje verze modulu runtime, jakož i sestavení přesměruje. Ve výchozím nastavení spravované aplikace spolupráce COM volání do kódu používat nejnovější verzi modulu runtime v počítači nainstalována.  
  
 Další informace o konfigurační soubory aplikace najdete v tématu [konfigurace aplikace](../../../docs/framework/configure-apps/index.md).  
  
## <a name="determining-which-version-of-the-runtime-to-load"></a>Určení verze běhového prostředí, která má být načtena  
 Modul common language runtime používá k určení načíst pro aplikaci, kterou verzi modulu runtime následující informace:  
  
-   Verze runtime, které jsou k dispozici.  
  
-   Verze runtime, které podporuje aplikace.  
  
### <a name="supported-runtime-versions"></a>Podporované Runtime verze  
 Modul runtime používá k určení, kterou verzi modulu runtime aplikace podporuje konfigurační soubor aplikace a přenosné hlavičky spustitelného souboru (PE). Pokud se nachází žádný konfigurační soubor aplikace, načte modul runtime runtime verze zadaná v záhlaví souboru PE aplikace, pokud tato verze je k dispozici.  
  
 Pokud se konfigurační soubor aplikace, modul runtime určuje verze odpovídající runtime k načtení podle výsledky následující proces:  
  
1.  Modul runtime zkoumá [ \<supportedRuntime > Element](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) element v konfiguračním souboru aplikace. Pokud jeden nebo více podporované runtime verze zadané v  **\<supportedRuntime >** element jsou k dispozici, načte modul runtime verze runtime – určení prvním  **\< supportedRuntime >** element. Pokud tato verze není k dispozici, modul runtime zkoumá Další  **\<supportedRuntime >** element a pokusí se načíst verze runtime – určení. Pokud tato verze modulu runtime není k dispozici, následných  **\<supportedRuntime >** se zkontrolují elementy. Pokud žádná z podporovaných runtime verzí jsou k dispozici, modul runtime nepodaří načíst verzi modulu runtime a zobrazí zprávu pro uživatele (viz krok 3).  
  
2.  Modul runtime přečte soubor záhlaví PE spustitelný soubor aplikace. Pokud je k dispozici modul runtime verze zadaná v hlavičce souboru PE, načte modul runtime této verze. Pokud verze runtime – určení není k dispozici, modul runtime prohledá pro verzi modulu runtime aplikací Microsoft za kompatibilní s verzí runtime v záhlaví PE. Pokud není nalezen této verze, proces pokračuje ke kroku 3.  
  
3.  Modul runtime zobrazí zprávu s oznámením, že verze runtime podporováno v aplikaci je k dispozici. Modul runtime není načtená.  
  
    > [!NOTE]
    >  Zobrazení této zprávy můžete potlačit pomocí hodnoty NoGuiFromShim v klíči registru HKLM\Software\Microsoft\\. NETFramework nebo pomocí proměnné prostředí COMPLUS_NoGuiFromShim. Můžete například potlačení zprávy s pro aplikace, které nejsou obvykle interakci s uživatelem, jako je bezobslužná instalace nebo služby systému Windows. Pokud je toto zobrazení zpráv potlačeno, modul runtime zapíše zprávu do protokolu událostí.  Nastavte hodnotu registru NoGuiFromShim na 1 pro potlačení této zprávy pro všechny aplikace v počítači. Alternativně nastavte proměnnou prostředí COMPLUS_NoGuiFromShim 1 k potlačení zprávy s pro aplikace spuštěné v kontextu určitého uživatele.  
  
> [!NOTE]
>  Po načtení verzi modulu runtime, můžete zadat sestavení – přesměrování vazby načíst jinou verzi jednotlivých sestavení rozhraní .NET Framework. Tyto přesměrování vazby vliv pouze konkrétní sestavení, které přesměrována.  
  
## <a name="partially-qualified-assembly-names-and-side-by-side-execution"></a>Částečně kvalifikované názvy sestavení a souběžné spouštění  
 Protože jsou zdroji potenciální problémy vedle sebe, odkazy na sestavení částečně kvalifikovaný slouží pouze k vytvoření vazby sestavení v adresáři aplikace. Nepoužívejte odkazy na sestavení částečně kvalifikovaný v kódu.  
  
 Pro zmírnění odkazy na sestavení částečně kvalifikovaný v kódu, můžete použít [ \<qualifyassembly – >](../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md) element v konfiguračním souboru aplikace k plnému určení částečně kvalifikované odkazy na sestavení, ke kterým došlo v kódu. Použití  **\<qualifyassembly – >** element zadat pouze pole, které nebyly nastaveny v odkaz na částečné. Uvedené v identity sestavení **fullName** atribut musí obsahovat veškeré informace potřebné k plnému určení název sestavení: název sestavení, veřejný klíč, jazykové verze a verze.  
  
 Následující příklad ukazuje soubor položku konfigurace aplikace k plnému určení sestavení nazvané `myAssembly`.  
  
```xml  
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">   
<qualifyAssembly partialName="myAssembly"   
fullName="myAssembly,  
      version=1.0.0.0,   
publicKeyToken=...,   
      culture=neutral"/>   
</assemblyBinding>   
```  
  
 Vždy, když načtení sestavení odkazů příkaz `myAssembly`, tato nastavení konfigurace souboru způsobit modulu runtime automaticky převede částečně kvalifikovaný `myAssembly` odkaz na plně kvalifikovaný odkaz. Například Assembly.Load("myAssembly") bude Assembly.Load ("myAssembly, verze = 1.0.0.0, publicKeyToken =..., culture = neutral").  
  
> [!NOTE]
>  Můžete použít **loadwithpartialname –** metoda obejít běžné omezení runtime jazyka, které zakazuje částečně odkazovaná sestavení z načítá z globální mezipaměti sestavení. Tato metoda by měla použít jenom v situacích, vzdálenou komunikaci, jako je snadno může způsobit problémy při provádění vedle sebe.  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Postupy: Povolení a zákaz automatického přesměrování vazby](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)|Popisuje způsob propojení aplikace s konkrétní verzí sestavení.|  
|[Konfigurace přesměrování vazby sestavení](../../../docs/framework/deployment/configuring-assembly-binding-redirection.md)|Objasňuje způsob, jakým lze odkazy vazby přesměrovat na určitou verzi sestavení rozhraní .NET Framework.|  
|[Vnitroprocesové souběžné provádění](../../../docs/framework/deployment/in-process-side-by-side-execution.md)|Popisuje způsob používání souběžného spouštění aktivace hostitele v jednom procesu, který je určen pro spouštění více verzí modulu CLR (Common Language Runtime) v rámci jednoho procesu.|  
|[Sestavení v modulu CLR (Common Language Runtime)](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)|Poskytuje koncepční přehled sestavení.|  
|[Aplikační domény](../../../docs/framework/app-domains/application-domains.md)|Poskytuje koncepční přehled domén aplikací.|  
  
## <a name="reference"></a>Odkaz  
 [\<supportedRuntime > elementu](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)
