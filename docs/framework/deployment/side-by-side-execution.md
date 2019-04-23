---
title: Souběžné spouštění v .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution
ms.assetid: 649f1342-766b-49e6-a90d-5b019a751e11
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ee17426e3ac8d5351490276a8c71cdfe996eb1a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59341072"
---
# <a name="side-by-side-execution-in-the-net-framework"></a>Souběžné spouštění v .NET Framework
Souběžné spouštění je možnost spuštění několika verzí aplikace nebo komponenty v jednom počítači. V jednom počítači lze nainstalovat více verzí modulu CLR (Common Language Runtime) a několik verzí aplikací a komponent, které využívají verzi modulu runtime ve stejnou dobu.  
  
 Následující obrázek znázorňuje několik aplikací, které používají dvě různé verze modulu runtime v jednom počítači. Aplikace A, B a C používají modul runtime verze 1.0, zatímco aplikace D používá modul runtime verze 1.1.  
  
 ![Vedle sebe provádění různých běhových verze](./media/side-by-side-execution/side-by-side-runtime-execution.gif)  
  
 Rozhraní .NET Framework zahrnuje modul CLR (Common Language Runtime) a kolekci sestavení, která obsahují typy rozhraní API. Modul runtime a sestavení rozhraní .NET Framework jsou opatřeny samostatnými verzemi. Například verze 4.0 modulu runtime je ve skutečnosti verzí 4.0.319, zatímco verze 1.0 sestavení rozhraní .NET Framework je verzí 1.0.3300.0.  
  
 Následující obrázek znázorňuje několik aplikací, které používají dvě různé verze komponenty na stejném počítači. Aplikace A a B používá verzi komponenty 1.0, zatímco aplikace C používá verzi 2.0 stejné komponenty.  
  
 ![Diagram, který zobrazuje vedle sebe spuštění součásti.](./media/side-by-side-execution/side-by-side-component-execution.gif)  
  
 Souběžné spouštění dává větší kontrolu nad tím, s jakou verzí komponenty je aplikace propojena, a větší kontrolu nad tím, jakou verzi modulu runtime aplikace používá.  
  
## <a name="benefits-of-side-by-side-execution"></a>Výhody souběžného spouštění  
 Před příchodem systému Windows XP a rozhraní .NET Framework docházelo ke konfliktům knihoven DLL, protože aplikace nebyla schopna rozlišovat mezi nekompatibilními verzemi stejného kódu. Informace o typu obsažené v knihovně DLL byly propojeny pouze s názvem souboru. Aplikace neměla žádnou možnost zjistit, zda typy obsažené v knihovně DLL jsou stejné jako ty, pomocí kterých byla aplikace sestavena. Ve výsledku mohla nová verze komponenty přepsat starší verzi a aplikace poškodit.  
  
 Souběžné spouštění a rozhraní .NET Framework poskytují následující funkce, které pomáhají předcházet konfliktům knihoven DLL:  
  
-   Sestavení se silným názvem.  
  
     Souběžné spouštění používá sestavení se silným názvem k vytvoření vazby informací o typu ke konkrétní verzi sestavení. Díky tomu aplikace nebo součást nevytvoří vazbu k neplatné verzi sestavení. Sestavení se silným názvem také umožňují, aby na stejném počítači existovalo více verzí souboru a aby je mohly využívat aplikace. Další informace najdete v tématu [sestavení se silným názvem](../../../docs/framework/app-domains/strong-named-assemblies.md).  
  
-   Úložiště kódu podporující verze.  
  
     Rozhraní .NET Framework poskytuje úložiště kódu podporující verze v globální mezipaměti sestavení (GAC). Globální mezipaměť sestavení (GAC) je mezipaměť kódu pro celý počítač, která je k dispozici na všech počítačích s nainstalovaným rozhraním .NET Framework. Jsou v ní uložena sestavení na základě informací o verzi, jazykové verzi a vydavateli a podporuje více verzí komponent a aplikací. Další informace najdete v tématu [Global Assembly Cache](../../../docs/framework/app-domains/gac.md).  
  
-   Izolace.  
  
     Pomocí rozhraní .NET Framework lze vytvořit aplikace a komponenty, které jsou spouštěny v izolaci. Izolace je základní součástí souběžného spouštění. Zahrnuje znalost prostředků, které využíváte, a zkušenosti se sdílením prostředků napříč několika verzemi aplikace nebo komponenty. Izolace zahrnuje také ukládání souborů na základě verze. Další informace o izolaci naleznete v tématu [pokyny pro vytváření komponent pro spuštění vedle sebe](../../../docs/framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).  
  
## <a name="version-compatibility"></a>Kompatibilita verzí  
 Verze 1.0 a 1.1 rozhraní .NET Framework jsou navrženy tak, aby byly navzájem kompatibilní. Aplikaci sestavenou pomocí verze 1.0 rozhraní .NET Framework lze spustit ve verzi 1.1 a aplikaci sestavenou pomocí verze 1.1 rozhraní .NET Framework lze spustit ve verzi 1.0. Funkce rozhraní API, které byly přidány ve verzi 1.1 rozhraní .NET Framework, však nebudou fungovat v rozhraní .NET Framework verze 1.0. Aplikace vytvořené pro verzi 2.0 lze spouštět pouze ve verzi 2.0. Aplikace pro verzi 2.0 nelze spustit ve verzi 1.1 nebo starší.  
  
 Verze rozhraní .NET Framework jsou považovány za celek, který sestává z modulu runtime a přidružených sestavení rozhraní .NET Framework (koncept se označuje jako sjednocení sestavení). Vazbu sestavení lze přesměrovat tak, aby zahrnovala další verze sestavení rozhraní .NET Framework. Přepsání výchozích vazeb sestavení však může být nebezpečné a je nutné je před nasazením pečlivě otestovat.  
  
## <a name="locating-runtime-version-information"></a>Vyhledání informací o verzi běhového prostředí  
 Informace o které modul runtime verze aplikace nebo komponenty byl kompilován s a které verze modulu runtime aplikace vyžaduje pro spuštění jsou uloženy ve dvou umístěních. Při kompilaci aplikace nebo komponenty, informace o verzi modulu runtime používá ke kompilaci je uložený v spravovaného spustitelný soubor. Informace o verze modulu runtime, které vyžaduje aplikace nebo komponenty je uložené v konfiguračním souboru aplikace.  
  
### <a name="runtime-version-information-in-the-managed-executable"></a>Informace o verzi modulu runtime v spravovaného spustitelný soubor  
 Přenosné spustitelné (PE) hlavičku souboru každé spravované aplikace a komponenty obsahuje informace o verzi modulu runtime, který byl sestaven s. Modul common language runtime používá tyto informace k určení pravděpodobně verze modulu runtime, které aplikace potřebuje ke spuštění.  
  
### <a name="runtime-version-information-in-the-application-configuration-file"></a>Informace o verzi modulu runtime v konfiguračním souboru aplikace  
 Spolu s informacemi v hlavičkách přenositelných Spustitelných souborů je možné aplikaci nasadit pomocí konfiguračního souboru aplikace, která poskytuje informace o verzi modulu runtime. Konfigurační soubor aplikace je soubor založený na formátu XML, který je vytvořil vývojář aplikace a, který je součástí aplikace. [ \<RequiredRuntime > Element](../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) z [ \<spuštění > části](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md), pokud je k dispozici v tomto souboru Určuje, jaké verze modulu runtime a verze nástroje součást aplikace podporuje. Tento soubor při testování můžete také použít pro testování kompatibility aplikace s různými verzemi modulu runtime.  
  
 Nespravovaný kód, jako jsou třeba aplikace modelu COM a modelu COM +, může mít konfigurační soubory aplikace, které modul runtime používá pro komunikaci se spravovaným kódem. Konfigurační soubor aplikace má vliv na spravovaný kód, který můžete aktivovat pomocí modelu COM. Soubor můžete určit, které podporuje verze modulu runtime, jakož i sestavení přesměruje. Ve výchozím nastavení spravované aplikace modelu COM interop volání do kódu použijte nejnovější verzi modulu runtime nainstalovaného v počítači.  
  
 Další informace o konfiguračních souborech aplikací naleznete v tématu [konfigurace aplikace](../../../docs/framework/configure-apps/index.md).  
  
## <a name="determining-which-version-of-the-runtime-to-load"></a>Určení verze běhového prostředí, která má být načtena  
 Modul common language runtime používá tyto informace k určení verze modulu runtime k načtení pro aplikaci:  
  
-   Verze modulu runtime, které jsou k dispozici.  
  
-   Verze modulu runtime, které podporuje aplikace.  
  
### <a name="supported-runtime-versions"></a>Podporované verze modulu Runtime  
 Modul runtime používá k určení, která verze modulu runtime aplikace podporuje konfiguračního souboru aplikace a přenosný spustitelný soubor záhlaví souboru (PE). Pokud se nachází konfigurační soubor aplikace, modul runtime načte modul runtime verze specifikovaná v hlavičkách přenositelných Spustitelných souborů aplikace, pokud tato verze je k dispozici.  
  
 Pokud se nachází konfigurační soubor aplikace, modul runtime určuje verzi odpovídající modul runtime k načtení závislosti na výsledcích následující proces:  
  
1. Modul runtime zkoumá [ \<supportedRuntime > Element](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) prvku v konfiguračním souboru aplikace. Pokud jeden nebo více následujících podporovaný modul runtime verze uvedené v  **\<supportedRuntime >** element jsou k dispozici, načte modul runtime verze modulu runtime, který je zadán prvním  **\< supportedRuntime >** elementu. Pokud tato verze není k dispozici, modul runtime zkoumá Další  **\<supportedRuntime >** elementu a pokusí se načíst modul runtime verze specifikovaná. Pokud tuto verzi modulu runtime není k dispozici, následné  **\<supportedRuntime >** jsou zkoumány elementy. Pokud nejsou k dispozici žádné podporované verze modulu runtime, modul runtime se nepodaří načíst verzi modulu runtime a zobrazí uživateli zprávu (viz krok 3).  
  
2. Modul runtime přečte hlavičkách přenositelných Spustitelných souborů spustitelného souboru aplikace. Pokud je k dispozici modul runtime verze zadaná v hlavičce souboru PE, načte modul runtime tuto verzi. Pokud zadaná verze modulu runtime není k dispozici, modul runtime vyhledává verze modulu runtime určí společnost Microsoft na kompatibilitu s modulem runtime verze v záhlaví PE. Pokud není nalezena tato verze, proces pokračuje ke kroku 3.  
  
3. Modul runtime se zobrazí zpráva s informacemi o tom, že verze modulu runtime podporováno v aplikaci není k dispozici. Modul runtime není načten.  
  
    > [!NOTE]
    >  Zobrazení této zprávy můžete potlačit pomocí hodnoty NoGuiFromShim v klíči registru HKLM\Software\Microsoft\\. NETFramework nebo COMPLUS_NoGuiFromShim proměnné prostředí. Například můžete potlačit zprávu pro aplikace, které obvykle nekomunikují s uživatelem, například bezobslužné instalace nebo služby Windows. Při zobrazení této zprávy je potlačena, modul runtime zapíše zprávu do protokolu událostí.  Nastavte hodnotu registru NoGuiFromShim na 1 pro potlačení této zprávy pro všechny aplikace v počítači. Můžete také nastavte proměnnou prostředí COMPLUS_NoGuiFromShim 1 k potlačení zprávy pro aplikace běžící v rámci určitého uživatele.  
  
> [!NOTE]
>  Po načtení verze modulu runtime přesměrování vazeb sestavení můžete určit, že být načtena jiná verze jednotlivých sestavení rozhraní .NET Framework. Tyto přesměrování vazby ovlivňují jenom konkrétní sestavení, který přesměruje.  
  
## <a name="partially-qualified-assembly-names-and-side-by-side-execution"></a>Částečně kvalifikované názvy sestavení a souběžné spouštění  
 Protože jde o potenciální příčinu problémů vedle sebe, částečně kvalifikované odkazy na sestavení lze použít pouze k vytvoření vazby na sestavení v adresáři aplikace. Vyhněte se částečně kvalifikovaných odkazů sestavení v kódu.  
  
 Ke zmírnění částečně kvalifikovaných odkazů sestavení v kódu, můžete použít [ \<qualifyassembly – >](../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md) prvku v konfiguračním souboru aplikace k plnému určení částečně kvalifikované odkazy na sestavení, ke kterým dochází v kódu. Použití  **\<qualifyassembly – >** element zadat pouze pole, které nebyly nastaveny v částečný odkaz. Identitu sestavení, které jsou uvedeny v **fullName** atribut musí obsahovat veškeré informace potřebné k plnému určení názvu sestavení: název sestavení, veřejný klíč, jazykovou verzi a verzi.  
  
 Následující příklad ukazuje položka souboru konfigurace aplikace k plnému určení sestavení nazvané `myAssembly`.  
  
```xml  
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">   
<qualifyAssembly partialName="myAssembly"   
fullName="myAssembly,  
      version=1.0.0.0,   
publicKeyToken=...,   
      culture=neutral"/>   
</assemblyBinding>   
```  
  
 Vždy, když sestavení načtení odkazů příkaz `myAssembly`, tato nastavení konfiguračního souboru způsobit, že modul runtime automaticky překládat částečně kvalifikované `myAssembly` odkaz na plně kvalifikovaný odkaz. Například Assembly.Load("myAssembly") stane Assembly.Load ("myAssembly, verze = 1.0.0.0, publicKeyToken =..., culture = neutral").  
  
> [!NOTE]
>  Můžete použít **loadwithpartialname –** metoda obejít common language runtime omezení, zakazuje částečně odkazovaná sestavení nejde načíst z globální mezipaměti sestavení. Tato metoda by měla sloužit pouze ve scénářích vzdálené komunikace může snadno způsobit problémy při provádění vedle sebe.  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Postupy: Povolení a zákaz automatického přesměrování vazby](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)|Popisuje způsob propojení aplikace s konkrétní verzí sestavení.|  
|[Konfigurace přesměrování vazby sestavení](../../../docs/framework/deployment/configuring-assembly-binding-redirection.md)|Objasňuje způsob, jakým lze odkazy vazby přesměrovat na určitou verzi sestavení rozhraní .NET Framework.|  
|[Vnitroprocesové souběžné provádění](../../../docs/framework/deployment/in-process-side-by-side-execution.md)|Popisuje způsob používání souběžného spouštění aktivace hostitele v jednom procesu, který je určen pro spouštění více verzí modulu CLR (Common Language Runtime) v rámci jednoho procesu.|  
|[Sestavení v modulu CLR (Common Language Runtime)](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)|Poskytuje koncepční přehled sestavení.|  
|[Aplikační domény](../../../docs/framework/app-domains/application-domains.md)|Poskytuje koncepční přehled domén aplikací.|  
  
## <a name="reference"></a>Odkaz  
 [\<supportedRuntime > – Element](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)
