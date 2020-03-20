---
title: Souběžné spouštění v .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution
ms.assetid: 649f1342-766b-49e6-a90d-5b019a751e11
ms.openlocfilehash: e965702943149d3ed34be39bb2923ad52dcf90ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181648"
---
# <a name="side-by-side-execution-in-the-net-framework"></a>Souběžné spouštění v .NET Framework

Souběžné spouštění je možnost spuštění několika verzí aplikace nebo komponenty v jednom počítači. V jednom počítači lze nainstalovat více verzí modulu CLR (Common Language Runtime) a několik verzí aplikací a komponent, které využívají verzi modulu runtime ve stejnou dobu.  
  
Následující obrázek znázorňuje několik aplikací, které používají dvě různé verze modulu runtime v jednom počítači. Aplikace A, B a C používají modul runtime verze 1.0, zatímco aplikace D používá modul runtime verze 1.1.  
  
![Souběžné provádění různých verzí runtime,](./media/side-by-side-execution/side-by-side-runtime-execution.gif)  
  
Rozhraní .NET Framework zahrnuje modul CLR (Common Language Runtime) a kolekci sestavení, která obsahují typy rozhraní API. Modul runtime a sestavení rozhraní .NET Framework jsou opatřeny samostatnými verzemi. Například verze 4.0 modulu runtime je ve skutečnosti verzí 4.0.319, zatímco verze 1.0 sestavení rozhraní .NET Framework je verzí 1.0.3300.0.  
  
Následující obrázek znázorňuje několik aplikací, které používají dvě různé verze komponenty na stejném počítači. Aplikace A a B používá verzi komponenty 1.0, zatímco aplikace C používá verzi 2.0 stejné komponenty.  
  
![Diagram, který ukazuje souběžné provádění součásti.](./media/side-by-side-execution/side-by-side-component-execution.gif)  
  
Souběžné spouštění dává větší kontrolu nad tím, s jakou verzí komponenty je aplikace propojena, a větší kontrolu nad tím, jakou verzi modulu runtime aplikace používá.  
  
## <a name="benefits-of-side-by-side-execution"></a>Výhody souběžného spouštění  

Před příchodem systému Windows XP a rozhraní .NET Framework docházelo ke konfliktům knihoven DLL, protože aplikace nebyla schopna rozlišovat mezi nekompatibilními verzemi stejného kódu. Informace o typu obsažené v knihovně DLL byly propojeny pouze s názvem souboru. Aplikace neměla žádnou možnost zjistit, zda typy obsažené v knihovně DLL jsou stejné jako ty, pomocí kterých byla aplikace sestavena. Ve výsledku mohla nová verze komponenty přepsat starší verzi a aplikace poškodit.  
  
Souběžné spouštění a rozhraní .NET Framework poskytují následující funkce, které pomáhají předcházet konfliktům knihoven DLL:  
  
- Sestavení se silným názvem.  
  
     Souběžné spouštění používá sestavení se silným názvem k vytvoření vazby informací o typu ke konkrétní verzi sestavení. Díky tomu aplikace nebo součást nevytvoří vazbu k neplatné verzi sestavení. Sestavení se silným názvem také umožňují, aby na stejném počítači existovalo více verzí souboru a aby je mohly využívat aplikace. Další informace naleznete [v tématu Sestavení se silným názvem](../../standard/assembly/strong-named.md).  
  
- Úložiště kódu podporující verze.  
  
     Rozhraní .NET Framework poskytuje úložiště kódu podporující verze v globální mezipaměti sestavení (GAC). Globální mezipaměť sestavení (GAC) je mezipaměť kódu pro celý počítač, která je k dispozici na všech počítačích s nainstalovaným rozhraním .NET Framework. Jsou v ní uložena sestavení na základě informací o verzi, jazykové verzi a vydavateli a podporuje více verzí komponent a aplikací. Další informace naleznete v [tématu Global Assembly Cache](../app-domains/gac.md).  
  
- Izolace.  
  
     Pomocí rozhraní .NET Framework lze vytvořit aplikace a komponenty, které jsou spouštěny v izolaci. Izolace je základní součástí souběžného spouštění. Zahrnuje znalost prostředků, které využíváte, a zkušenosti se sdílením prostředků napříč několika verzemi aplikace nebo komponenty. Izolace zahrnuje také ukládání souborů na základě verze. Další informace o izolaci naleznete [v tématu Pokyny pro vytváření komponent pro souběžné spuštění](guidelines-for-creating-components-for-side-by-side-execution.md).  
  
## <a name="version-compatibility"></a>Kompatibilita verzí  

Verze 1.0 a 1.1 rozhraní .NET Framework jsou navrženy tak, aby byly navzájem kompatibilní. Aplikaci sestavenou pomocí verze 1.0 rozhraní .NET Framework lze spustit ve verzi 1.1 a aplikaci sestavenou pomocí verze 1.1 rozhraní .NET Framework lze spustit ve verzi 1.0. Funkce rozhraní API, které byly přidány ve verzi 1.1 rozhraní .NET Framework, však nebudou fungovat v rozhraní .NET Framework verze 1.0. Aplikace vytvořené pro verzi 2.0 lze spouštět pouze ve verzi 2.0. Aplikace pro verzi 2.0 nelze spustit ve verzi 1.1 nebo starší.  
  
Verze rozhraní .NET Framework jsou považovány za celek, který sestává z modulu runtime a přidružených sestavení rozhraní .NET Framework (koncept se označuje jako sjednocení sestavení). Vazbu sestavení lze přesměrovat tak, aby zahrnovala další verze sestavení rozhraní .NET Framework. Přepsání výchozích vazeb sestavení však může být nebezpečné a je nutné je před nasazením pečlivě otestovat.  
  
## <a name="locating-runtime-version-information"></a>Vyhledání informací o verzi běhového prostředí  

Informace o tom, s jakou verzí za běhu byla aplikace nebo komponenta zkompilována a které verze runtime, které aplikace potřebuje ke spuštění, jsou uloženy ve dvou umístěních. Při kompilaci aplikace nebo součásti jsou informace o verzi modulu runtime použité ke kompilaci uloženy ve spravovaném spustitelném souboru. Informace o verzích runtime, které aplikace nebo komponenta vyžaduje, jsou uloženy v konfiguračním souboru aplikace.  
  
### <a name="runtime-version-information-in-the-managed-executable"></a>Informace o verzi modulu Runtime ve spravovaném spustitelném souboru  

Přenosná hlavička souboru spustitelného souboru (PE) každé spravované aplikace a součásti obsahuje informace o runtime verzi, se kterou byla vytvořena. Běžný jazyk runtime používá tyto informace k určení nejpravděpodobnější verze runtime aplikace potřebuje ke spuštění.  
  
### <a name="runtime-version-information-in-the-application-configuration-file"></a>Informace o verzi za běhu v konfiguračním souboru aplikace  

Kromě informací v hlavičce souboru PE lze aplikaci nasadit pomocí konfiguračního souboru aplikace, který poskytuje informace o verzi za běhu. Konfigurační soubor aplikace je soubor založený na xml, který je vytvořen vývojářem aplikace a který je dodáván s aplikací. [ \<Pokud](../configure-apps/file-schema/startup/requiredruntime-element.md) je v tomto souboru k dispozici, funkce requiredRuntime> Element [ \<spouštěcí>](../configure-apps/file-schema/startup/startup-element.md)určuje, které verze runtime a které verze komponenty aplikace podporuje. Tento soubor můžete také použít při testování k testování kompatibility aplikace s různými verzemi runtime.  
  
Nespravovaný kód, včetně aplikací modelu COM a COM+, může mít konfigurační soubory aplikací, které runtime používá pro interakci se spravovaným kódem. Konfigurační soubor aplikace ovlivňuje jakýkoli spravovaný kód, který aktivujete prostřednictvím serveru COM. Soubor může určit, které verze runtime podporuje, stejně jako sestavení přesměrování. Ve výchozím nastavení používají interopové aplikace com volající spravovaný kód nejnovější verzi runtime nainstalovanou v počítači.  
  
 Další informace o konfiguračních souborech aplikace naleznete v [tématu Konfigurace aplikací](../configure-apps/index.md).  
  
## <a name="determining-which-version-of-the-runtime-to-load"></a>Určení verze běhového prostředí, která má být načtena  

Běžný jazyk runtime používá následující informace k určení, která verze runtime načíst pro aplikaci:  
  
- Runtime verze, které jsou k dispozici.  
  
- Runtime verze, které podporuje aplikace.  
  
### <a name="supported-runtime-versions"></a>Podporované verze modulu Runtime  

Modul runtime používá konfigurační soubor aplikace a hlavičku přenosného spustitelného souboru (PE) k určení, kterou verzi modulu runtime aplikace podporuje. Pokud není k dispozici žádný konfigurační soubor aplikace, načte doba runtime verzi runtime zadanou v hlavičce souboru PE aplikace, pokud je tato verze k dispozici.  
  
Pokud je k dispozici konfigurační soubor aplikace, runtime určuje příslušnou verzi runtime k načtení na základě výsledků následujícího procesu:  
  
1. Modul runtime zkontroluje [ \<prvek supportedRuntime> Element](../configure-apps/file-schema/startup/supportedruntime-element.md) v konfiguračním souboru aplikace. Pokud jedna nebo více podporovaných verzí modulu runtime zadaných v ** \<podporovaném** prvku runtime>jsou k dispozici, modul runtime načte verzi modulu runtime určenou prvním ** \<podporovaným prvkem>modulrun.** Pokud tato verze není k dispozici, modul runtime zkontroluje další ** \<podporovaný modul Runtime>** elementa a pokusí se načíst zadanou verzi modulu runtime. Pokud tato verze modulu runtime není k dispozici, následné ** \<podporované Modul runtime>** prvky jsou zkontrolovány. Pokud není k dispozici žádná z podporovaných verzí modulu runtime, modul runtime nenačte verzi modulu runtime a zobrazí zprávu uživateli (viz krok 3).  
  
2. Modul runtime přečte záhlaví souboru PE spustitelného souboru aplikace. Pokud je k dispozici verze runtime určená hlavičkou souboru PE, načte se tato verze. Pokud zadaná verze runtime není k dispozici, hledá runtime verzi runtime určenou společností Microsoft jako kompatibilní s verzí runtime v hlavičce pe. Pokud tato verze nebyla nalezena, proces pokračuje krok 3.  
  
3. Modul runtime zobrazí zprávu oznamující, že verze modulu runtime podporovaná aplikací není k dispozici. Doba běhu není načtena.  
  
    > [!NOTE]
    > Zobrazení této zprávy můžete potlačit pomocí hodnoty NoGuiFromShim pod klíčem registru HKLM\Software\Microsoft\\. NETFramework nebo pomocí proměnné prostředí COMPLUS_NoGuiFromShim. Můžete například potlačit zprávu pro aplikace, které obvykle nekomunikují s uživatelem, například bezobslužné instalace nebo služby systému Windows. Při potlačení tohoto zobrazení zprávy zapíše zaběhu zprávu do protokolu událostí.  Nastavte hodnotu registru NoGuiFromShim na 1 potlačit tuto zprávu pro všechny aplikace v počítači. Alternativně nastavte proměnnou prostředí COMPLUS_NoGuiFromShim na 1 potlačit zprávu pro aplikace spuštěné v určitém kontextu uživatele.  
  
> [!NOTE]
> Po načtení verze runtime mohou přesměrování vazeb sestavení určit, že bude načtena jiná verze jednotlivého sestavení rozhraní .NET Framework. Tato přesměrování vazby ovlivní pouze konkrétní sestavení, které je přesměrováno.  
  
## <a name="partially-qualified-assembly-names-and-side-by-side-execution"></a>Částečně kvalifikované názvy sestavení a souběžné spouštění  

Vzhledem k tomu, že jsou potenciálním zdrojem souběžných problémů, částečně kvalifikované odkazy na sestavení lze použít pouze k vazbě na sestavení v adresáři aplikace. Vyhněte se částečně kvalifikované sestavení odkazy v kódu.  
  
Chcete-li zmírnit částečně kvalifikované odkazy na sestavení v kódu, můžete použít prvek [ \<qualifyAssembly>](../configure-apps/file-schema/runtime/qualifyassembly-element.md) v konfiguračním souboru aplikace k úplnému kvalifikaci částečně kvalifikovaných odkazů na sestavení, ke kterým dochází v kódu. Pomocí prvku ** \<qualifyAssembly>** určete pouze pole, která nebyla nastavena v částečném odkazu. Identita sestavení uvedená v atributu **fullName** musí obsahovat všechny informace potřebné k úplnému zařazení názvu sestavení: název sestavení, veřejný klíč, jazyková verze a verze.  
  
 Následující příklad ukazuje položku konfiguračního `myAssembly`souboru aplikace, aby bylo plně kvalifikováno sestavení s názvem .  
  
```xml  
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
<qualifyAssembly partialName="myAssembly"
fullName="myAssembly,  
      version=1.0.0.0,
publicKeyToken=...,
      culture=neutral"/>
</assemblyBinding>
```  
  
 Kdykoli odkazuje příkaz zatížení `myAssembly`sestavení , tato nastavení konfiguračního `myAssembly` souboru způsobí, že za běhu automaticky přeloží částečně kvalifikovaný odkaz na plně kvalifikovaný odkaz. Například Assembly.Load("myAssembly") se stane Assembly.Load("myAssembly, version=1.0.0.0, publicKeyToken=..., culture=neutral").  
  
> [!NOTE]
> Metodu **LoadWithPartialName** můžete použít k obejití omezení běžného časového režimu jazyka, které zakazuje načítání částečně odkazovaných sestavení z globální mezipaměti sestavení. Tato metoda by měla být použita pouze ve scénářích vzdálené komunikace, protože může snadno způsobit problémy při souběžném spuštění.  
  
## <a name="related-topics"></a>Související témata  
  
|Nadpis|Popis|  
|-----------|-----------------|  
|[Postupy: Povolení a zákaz automatického přesměrování vazby](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)|Popisuje způsob propojení aplikace s konkrétní verzí sestavení.|  
|[Konfigurace přesměrování vazby sestavení](configuring-assembly-binding-redirection.md)|Objasňuje způsob, jakým lze odkazy vazby přesměrovat na určitou verzi sestavení rozhraní .NET Framework.|  
|[Vnitroprocesové souběžné provádění](in-process-side-by-side-execution.md)|Popisuje způsob používání souběžného spouštění aktivace hostitele v jednom procesu, který je určen pro spouštění více verzí modulu CLR (Common Language Runtime) v rámci jednoho procesu.|  
|[Sestavení v .NET](../../standard/assembly/index.md)|Poskytuje koncepční přehled sestavení.|  
|[Aplikační domény](../app-domains/application-domains.md)|Poskytuje koncepční přehled domén aplikací.|  
  
## <a name="reference"></a>Referenční informace  

[\<podporovaný modul> Modul runtime](../configure-apps/file-schema/startup/supportedruntime-element.md)
