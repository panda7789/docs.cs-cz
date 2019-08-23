---
title: Souběžné spouštění v .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution
ms.assetid: 649f1342-766b-49e6-a90d-5b019a751e11
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 47f211256b4820e3fb25339de2fe4db962171056
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911012"
---
# <a name="side-by-side-execution-in-the-net-framework"></a>Souběžné spouštění v .NET Framework
Souběžné spouštění je možnost spuštění několika verzí aplikace nebo komponenty v jednom počítači. V jednom počítači lze nainstalovat více verzí modulu CLR (Common Language Runtime) a několik verzí aplikací a komponent, které využívají verzi modulu runtime ve stejnou dobu.  
  
 Následující obrázek znázorňuje několik aplikací, které používají dvě různé verze modulu runtime v jednom počítači. Aplikace A, B a C používají modul runtime verze 1.0, zatímco aplikace D používá modul runtime verze 1.1.  
  
 ![Souběžné spouštění různých verzí modulu runtime,](./media/side-by-side-execution/side-by-side-runtime-execution.gif)  
  
 Rozhraní .NET Framework zahrnuje modul CLR (Common Language Runtime) a kolekci sestavení, která obsahují typy rozhraní API. Modul runtime a sestavení rozhraní .NET Framework jsou opatřeny samostatnými verzemi. Například verze 4.0 modulu runtime je ve skutečnosti verzí 4.0.319, zatímco verze 1.0 sestavení rozhraní .NET Framework je verzí 1.0.3300.0.  
  
 Následující obrázek znázorňuje několik aplikací, které používají dvě různé verze komponenty na stejném počítači. Aplikace A a B používá verzi komponenty 1.0, zatímco aplikace C používá verzi 2.0 stejné komponenty.  
  
 ![Diagram, který znázorňuje souběžné spouštění součásti.](./media/side-by-side-execution/side-by-side-component-execution.gif)  
  
 Souběžné spouštění dává větší kontrolu nad tím, s jakou verzí komponenty je aplikace propojena, a větší kontrolu nad tím, jakou verzi modulu runtime aplikace používá.  
  
## <a name="benefits-of-side-by-side-execution"></a>Výhody souběžného spouštění  
 Před příchodem systému Windows XP a rozhraní .NET Framework docházelo ke konfliktům knihoven DLL, protože aplikace nebyla schopna rozlišovat mezi nekompatibilními verzemi stejného kódu. Informace o typu obsažené v knihovně DLL byly propojeny pouze s názvem souboru. Aplikace neměla žádnou možnost zjistit, zda typy obsažené v knihovně DLL jsou stejné jako ty, pomocí kterých byla aplikace sestavena. Ve výsledku mohla nová verze komponenty přepsat starší verzi a aplikace poškodit.  
  
 Souběžné spouštění a rozhraní .NET Framework poskytují následující funkce, které pomáhají předcházet konfliktům knihoven DLL:  
  
- Sestavení se silným názvem.  
  
     Souběžné spouštění používá sestavení se silným názvem k vytvoření vazby informací o typu ke konkrétní verzi sestavení. Díky tomu aplikace nebo součást nevytvoří vazbu k neplatné verzi sestavení. Sestavení se silným názvem také umožňují, aby na stejném počítači existovalo více verzí souboru a aby je mohly využívat aplikace. Další informace naleznete v tématu [sestavení se silným názvem](../../../docs/framework/app-domains/strong-named-assemblies.md).  
  
- Úložiště kódu podporující verze.  
  
     Rozhraní .NET Framework poskytuje úložiště kódu podporující verze v globální mezipaměti sestavení (GAC). Globální mezipaměť sestavení (GAC) je mezipaměť kódu pro celý počítač, která je k dispozici na všech počítačích s nainstalovaným rozhraním .NET Framework. Jsou v ní uložena sestavení na základě informací o verzi, jazykové verzi a vydavateli a podporuje více verzí komponent a aplikací. Další informace naleznete v tématu [globální mezipaměť sestavení (GAC](../../../docs/framework/app-domains/gac.md)).  
  
- Izolace.  
  
     Pomocí rozhraní .NET Framework lze vytvořit aplikace a komponenty, které jsou spouštěny v izolaci. Izolace je základní součástí souběžného spouštění. Zahrnuje znalost prostředků, které využíváte, a zkušenosti se sdílením prostředků napříč několika verzemi aplikace nebo komponenty. Izolace zahrnuje také ukládání souborů na základě verze. Další informace o izolaci najdete v tématu [pokyny pro vytváření komponent pro souběžné spouštění](../../../docs/framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).  
  
## <a name="version-compatibility"></a>Kompatibilita verzí  
 Verze 1.0 a 1.1 rozhraní .NET Framework jsou navrženy tak, aby byly navzájem kompatibilní. Aplikaci sestavenou pomocí verze 1.0 rozhraní .NET Framework lze spustit ve verzi 1.1 a aplikaci sestavenou pomocí verze 1.1 rozhraní .NET Framework lze spustit ve verzi 1.0. Funkce rozhraní API, které byly přidány ve verzi 1.1 rozhraní .NET Framework, však nebudou fungovat v rozhraní .NET Framework verze 1.0. Aplikace vytvořené pro verzi 2.0 lze spouštět pouze ve verzi 2.0. Aplikace pro verzi 2.0 nelze spustit ve verzi 1.1 nebo starší.  
  
 Verze rozhraní .NET Framework jsou považovány za celek, který sestává z modulu runtime a přidružených sestavení rozhraní .NET Framework (koncept se označuje jako sjednocení sestavení). Vazbu sestavení lze přesměrovat tak, aby zahrnovala další verze sestavení rozhraní .NET Framework. Přepsání výchozích vazeb sestavení však může být nebezpečné a je nutné je před nasazením pečlivě otestovat.  
  
## <a name="locating-runtime-version-information"></a>Vyhledání informací o verzi běhového prostředí  
 Informace o tom, které verze modulu runtime aplikace nebo komponenty byly kompilovány s a které verze modulu runtime aplikace vyžaduje ke spuštění, jsou uloženy ve dvou umístěních. Když je zkompilována aplikace nebo komponenta, informace o verzi modulu runtime použité ke kompilaci jsou uloženy ve spravovaném spustitelném souboru. Informace o běhových verzích, které aplikace nebo komponenta vyžaduje, jsou uložené v konfiguračním souboru aplikace.  
  
### <a name="runtime-version-information-in-the-managed-executable"></a>Informace o verzi modulu runtime ve spravovaném spustitelném souboru  
 Hlavička přenositelného spustitelného souboru (PE) každé spravované aplikace a komponenty obsahuje informace o verzi modulu runtime, pomocí které byla vytvořena. Modul CLR (Common Language Runtime) používá tyto informace k určení nejpravděpodobnější verze modulu runtime, kterou aplikace potřebuje spustit.  
  
### <a name="runtime-version-information-in-the-application-configuration-file"></a>Informace o verzi modulu runtime v konfiguračním souboru aplikace  
 Kromě informací v hlavičce souboru PE může být aplikace nasazena pomocí konfiguračního souboru aplikace, který poskytuje informace o verzi modulu runtime. Konfigurační soubor aplikace je soubor založený na jazyce XML, který je vytvořen vývojářem aplikace a který je dodáván s aplikací. [Element requiredRuntime > oddílu startup >, pokud se nachází v tomto souboru, určuje, které verze modulu runtime a které verze komponenty aplikace podporuje. \<](../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) [ \<](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) Tento soubor můžete také použít při testování k otestování kompatibility aplikace s různými verzemi modulu runtime.  
  
 Nespravovaný kód, včetně aplikací COM a COM+, může mít konfigurační soubory aplikace, které modul runtime používá pro interakci se spravovaným kódem. Konfigurační soubor aplikace má vliv na veškerý spravovaný kód, který aktivujete pomocí modelu COM. Soubor může určovat, které verze modulu runtime podporuje, i přesměrování sestavení. Ve výchozím nastavení používají spolupracující aplikace COM volání spravovaného kódu nejnovější verzi modulu runtime, který je v počítači nainstalován.  
  
 Další informace o konfiguračních souborech aplikace najdete v tématu [Konfigurace aplikací](../../../docs/framework/configure-apps/index.md).  
  
## <a name="determining-which-version-of-the-runtime-to-load"></a>Určení verze běhového prostředí, která má být načtena  
 Modul CLR (Common Language Runtime) používá následující informace k určení verze modulu runtime, který se má načíst pro aplikaci:  
  
- Verze modulu runtime, které jsou k dispozici.  
  
- Verze modulu runtime, které aplikace podporuje.  
  
### <a name="supported-runtime-versions"></a>Podporované verze modulu runtime  
 Modul runtime používá konfigurační soubor aplikace a hlavičku přenositelného spustitelného souboru (PE) k určení verze modulu runtime, který aplikace podporuje. Pokud není přítomen konfigurační soubor aplikace, modul runtime načte verzi modulu runtime určenou v hlavičce souboru PE aplikace, pokud je tato verze k dispozici.  
  
 Pokud je přítomen konfigurační soubor aplikace, modul runtime určí vhodnou verzi modulu runtime, která se má načíst na základě výsledků následujícího procesu:  
  
1. Modul runtime prověřuje [ \<element supportedRuntime > elementu](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) v konfiguračním souboru aplikace. Pokud je přítomna jedna nebo více podporovaných verzí modulu runtime, které jsou zadány v  **\<prvku supportedRuntime >** , modul runtime načte verzi modulu runtime určenou prvním  **\<prvkem supportedRuntime >** . Pokud tato verze není k dispozici, modul runtime prověřuje další  **\<prvek > supportedRuntime** a pokusí se načíst zadanou verzi modulu runtime. Pokud tato verze modulu runtime není k dispozici, jsou zkontrolovány další  **\<> supportedRuntime** prvky. Pokud není k dispozici žádná z podporovaných verzí modulu runtime, modul runtime nedokáže načíst verzi modulu runtime a zobrazí uživateli zprávu (viz krok 3).  
  
2. Modul runtime čte hlavičku souboru PE spustitelného souboru aplikace. Je-li verze modulu runtime určená hlavičkou souboru PE k dispozici, modul runtime tuto verzi načte. Pokud zadaná verze modulu runtime není k dispozici, modul runtime vyhledá verzi modulu runtime určenou společností Microsoft, aby byla kompatibilní s verzí modulu runtime v hlavičce PE. Pokud se tato verze nenajde, proces pokračuje krokem 3.  
  
3. Modul runtime zobrazí zprávu s oznámením, že verze modulu runtime podporovaná aplikací není k dispozici. Modul runtime není zaveden.  
  
    > [!NOTE]
    > Zobrazení této zprávy můžete potlačit pomocí hodnoty NoGuiFromShim v klíči registru HKLM\Software\Microsoft\\. NETFramework nebo pomocí proměnné prostředí COMPLUS_NoGuiFromShim. Můžete například potlačit zprávu pro aplikace, které obvykle nepracují s uživatelem, například bezobslužné instalace nebo služby systému Windows. Když se toto zobrazení této zprávy potlačí, modul runtime zapíše zprávu do protokolu událostí.  Nastavte hodnotu registru NoGuiFromShim na 1 pro potlačení této zprávy pro všechny aplikace v počítači. Alternativně nastavte proměnnou prostředí COMPLUS_NoGuiFromShim na hodnotu 1, chcete-li potlačit zprávu pro aplikace spuštěné v konkrétním uživatelském kontextu.  
  
> [!NOTE]
> Po načtení verze modulu runtime může přesměrování vazby sestavení určit, že je načtena jiná verze samostatného sestavení .NET Framework. Tyto přesměrování vazby ovlivňují pouze konkrétní sestavení, které je přesměrováno.  
  
## <a name="partially-qualified-assembly-names-and-side-by-side-execution"></a>Částečně kvalifikované názvy sestavení a souběžné spouštění  
 Vzhledem k tomu, že se jedná o potenciální zdroj souběžných problémů, lze použít částečně kvalifikované odkazy na sestavení pouze k vytvoření vazby k sestavením v adresáři aplikace. Vyhněte se částečně kvalifikovaným odkazům na sestavení ve vašem kódu.  
  
 Chcete-li zmírnit částečně kvalifikované odkazy na sestavení v kódu, můžete použít [ \<prvek qualifyAssembly >](../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md) v konfiguračním souboru aplikace pro úplné určení částečně kvalifikovaných odkazů na sestavení, které se vyskytují v kódu. Pomocí elementu qualifyAssembly > můžete určit pouze pole, která nebyla nastavena v částečném odkazu.  **\<** Identita sestavení uvedená v atributu **FullName** musí obsahovat všechny informace potřebné k plnému kvalifikovanému názvu sestavení: název sestavení, veřejný klíč, jazyková verze a verze.  
  
 Následující příklad ukazuje položku konfiguračního souboru aplikace pro úplné zařazení sestavení s názvem `myAssembly`.  
  
```xml  
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">   
<qualifyAssembly partialName="myAssembly"   
fullName="myAssembly,  
      version=1.0.0.0,   
publicKeyToken=...,   
      culture=neutral"/>   
</assemblyBinding>   
```  
  
 Při každém odkazu `myAssembly`na příkaz načtení sestavení způsobí tato nastavení konfiguračního souboru, aby modul runtime automaticky přeložil částečně `myAssembly` kvalifikovaný odkaz na plně kvalifikovaný odkaz. Například Assembly. Load ("myAssembly") se bude jednat o Assembly. Load ("myAssembly, Version = 1.0.0.0, publicKeyToken =..., Culture = neutral").  
  
> [!NOTE]
> Pomocí metody **LoadWithPartialName** můžete obejít omezení modulu CLR (Common Language Runtime), které zabrání načtení částečně odkazovaných sestavení z globální mezipaměti sestavení (GAC). Tato metoda by se měla používat jenom ve scénářích vzdálené komunikace, protože může snadno způsobovat problémy při souběžném spouštění.  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Postupy: Povolení a zákaz automatického přesměrování vazby](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)|Popisuje způsob propojení aplikace s konkrétní verzí sestavení.|  
|[Konfigurace přesměrování vazby sestavení](../../../docs/framework/deployment/configuring-assembly-binding-redirection.md)|Objasňuje způsob, jakým lze odkazy vazby přesměrovat na určitou verzi sestavení rozhraní .NET Framework.|  
|[Vnitroprocesové souběžné provádění](../../../docs/framework/deployment/in-process-side-by-side-execution.md)|Popisuje způsob používání souběžného spouštění aktivace hostitele v jednom procesu, který je určen pro spouštění více verzí modulu CLR (Common Language Runtime) v rámci jednoho procesu.|  
|[Sestavení v modulu CLR (Common Language Runtime)](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)|Poskytuje koncepční přehled sestavení.|  
|[Aplikační domény](../../../docs/framework/app-domains/application-domains.md)|Poskytuje koncepční přehled domén aplikací.|  
  
## <a name="reference"></a>Reference  
 [\<supportedRuntime – element >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)
