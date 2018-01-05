---
title: "Fuslogvw.exe (prohlížeč protokolu vazby sestavení)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- failed assembly binds
- Fuslogvw.exe
- displaying failed assembly bind details
- assemblies [.NET Framework], failed assembly binds
- locating assemblies
- Assembly Binding Log Viewer
ms.assetid: e32fa443-0778-4cc3-bf36-5c8ea297d296
caps.latest.revision: "35"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 170e9ca4ed2b9ad17ec9120321612c37da32e453
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="fuslogvwexe-assembly-binding-log-viewer"></a>Fuslogvw.exe (prohlížeč protokolu vazby sestavení)
Nástroj Assembly Binding Log Viewer zobrazuje podrobnosti o vazbách sestavení. Tyto informace vám pomohou diagnostikovat, proč rozhraní .NET Framework nemůže najít sestavení v době běhu. Tyto chyby jsou obvykle výsledkem nasazení sestavení na nesprávné místo, neplatné nativní bitové kopie nebo neshody čísel verzí nebo jazykových verzí. Modul common language runtime se nezdařilo najít sestavení obvykle objeví jako <xref:System.TypeLoadException> ve vaší aplikaci.  
  
> [!IMPORTANT]
>  Nástroj fuslogvw.exe je nutné spustit s oprávněními správce.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit tento nástroj, použijte příkazový řádek pro vývojáře (nebo příkazový řádek sady Visual Studio v systému Windows 7) s oprávněními správce. Další informace najdete v tématu [příkazového řádku](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
```  
fuslogvw  
```  
  
 Prohlížeč zobrazí záznam pro každou nezdařenou vazbu sestavení. Pro každou chybu prohlížeč vypíše aplikaci, která iniciovala tuto vazbu, sestavení, kterého se vazba týká, včetně názvu, verze, jazykové verze, veřejného klíče a data a času chyby.  
  
### <a name="to-change-the-log-location-view"></a>Změna umístění zobrazení protokolu  
  
1.  Vyberte **výchozí** tlačítko Možnosti zobrazíte selhání vazby pro všechny typy aplikací. Položky protokolu jsou ve výchozím nastavení uloženy na disku do mezipaměti rozhraní wininet v adresářích jednotlivých uživatelů.  
  
2.  Vyberte **vlastní** tlačítko zobrazíte selhání vazby v vlastní adresář, který zadáte. Je nutné zadat vlastní umístění, kam chcete ukládat protokoly nastavením umístění vlastní protokolu v modulu runtime **nastavení protokolu** dialogovém okně můžete platný název adresáře. Tento adresář by měl být prázdný a měl by obsahovat pouze soubory, které generuje modul runtime. Pokud obsahuje spustitelný soubor, který generuje chybu do protokolu, tato chyba nebude protokolována, protože se nástroj pokusí vytvořit adresář se stejným názvem jako tento spustitelný soubor. Kromě toho se nezdaří pokus o spuštění spustitelného souboru z umístění protokolu.  
  
    > [!NOTE]
    >  Výchozí umístění vazby je vhodnější než vlastní umístění vazby. Modul runtime ukládá výchozí umístění vazby do mezipaměti rozhraní wininet, a proto vazbu automaticky odstraní. Pokud určíte vlastní umístění vazby, zodpovídáte za její odstranění.  
  
### <a name="to-view-details-about-a-specific-failure"></a>Zobrazení podrobností o konkrétní chybě  
  
1.  V prohlížeči vyberte název aplikace požadovaného záznamu.  
  
2.  Klikněte **zobrazit protokol** tlačítko. Záznam lze vybrat také dvojitým kliknutím.  
  
     Nástroj zobrazí následující podrobnosti o vybrané chybě vazby:  
  
    -   Konkrétní důvod selhání vazby, například „soubor nebyl nalezen“ nebo „neshoda verzí“.  
  
    -   Informace o aplikaci, která iniciovala tuto vazbu, včetně jejího názvu, kořenového adresáře aplikace (AppBase) a popisu soukromé cesty hledání, pokud existuje.  
  
    -   Identitu sestavení, které tento nástroj hledá.  
  
    -   Popis všech zásad aplikace, vydavatele nebo správce, které byly použity.  
  
    -   Zda je sestavení byl nalezen v [globální mezipaměť sestavení](../../../docs/framework/app-domains/gac.md).  
  
    -   Seznam všech zjišťovaných adres URL.  
  
 Následující ukázka položky protokolu zobrazuje detailní informace o selhání vazby sestavení.  
  
```  
*** Assembly Binder Log Entry  (3/5/2007 @ 12:54:20 PM) ***  
  
The operation failed.  
Bind result: hr = 0x80070002. The system cannot find the file specified.  
  
Assembly manager loaded from:  C:\WINNT\Microsoft.NET\Framework\v2.0.50727\fusion.dll  
Running under executable  C:\Program Files\Microsoft.NET\FrameworkSDK\Samples\Tutorials\resourcesandlocalization\graphic\cs\graphicfailtest.exe  
--- A detailed error log follows.   
  
=== Pre-bind state information ===  
LOG: DisplayName = graphicfailtest.resources, Version=0.0.0.0, Culture=en-US, PublicKeyToken=null  
 (Fully-specified)  
LOG: Appbase = C:\Program Files\Microsoft.NET\FrameworkSDK\Samples\Tutorials\resourcesandlocalization\graphic\cs\  
LOG: Initial PrivatePath = NULL  
LOG: Dynamic Base = NULL  
LOG: Cache Base = NULL  
LOG: AppName = NULL  
Calling assembly : graphicfailtest, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
===  
  
LOG: Processing DEVPATH.  
LOG: DEVPATH is not set. Falling through to regular bind.  
LOG: Policy not being applied to reference at this time (private, custom, partial, or location-based assembly bind).  
LOG: Post-policy reference: graphicfailtest.resources, Version=0.0.0.0, Culture=en-US, PublicKeyToken=null  
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources.DLL.  
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources/graphicfailtest.resources.DLL.  
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources.EXE.  
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources/graphicfailtest.resources.EXE.  
LOG: All probing URLs attempted and failed.  
```  
  
### <a name="to-delete-a-single-entry-from-the-log"></a>Odstranění jednoho záznamu z protokolu  
  
1.  Vyberte záznam v prohlížeči.  
  
2.  Klikněte **odstranit položku** tlačítko.  
  
### <a name="to-delete-all-entries-from-the-log"></a>Odstranění všech záznamů z protokolu  
  
-   Klikněte **odstranit všechny** tlačítko.  
  
### <a name="to-refresh-the-user-interface"></a>Obnovení uživatelského rozhraní  
  
-   Klikněte **aktualizovat** tlačítko. Prohlížeč automaticky nerozpozná nové položky protokolu, pokud je spuštěn. Je nutné použít **aktualizovat** tlačítko zobrazit.  
  
### <a name="to-change-the-log-settings"></a>Změna nastavení protokolu  
  
-   Klikněte **nastavení** tlačítko Otevřít **nastavení protokolu** dialogové okno.  
  
### <a name="to-view-the-about-dialog"></a>Zobrazení dialogového okna O programu  
  
-   Klikněte **o** tlačítko.  
  
## <a name="binding-logs-for-native-images"></a>Protokoly vazeb nativních bitových kopií  
 Ve výchozím nastavení nástroj Fuslogvw.exe zaznamenává normální požadavky vazby sestavení. Alternativně můžete protokolu vazby sestavení pro nativní bitové kopie, které byly vytvořené pomocí [Ngen.exe (Generátor nativních obrázků)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
#### <a name="to-log-assembly-binds-for-native-images"></a>Protokolování vazeb sestavení nativních bitových kopií  
  
-   V **kategorií protokolu** skupiny, vyberte **nativní bitové kopie** tlačítko.  
  
 Následující protokol zobrazuje chybu způsobenou neexistující závislostí při vytvoření nativní bitové kopie pro aplikaci. Pokud se tyto závislosti v době běhu liší od závislostí při spuštění nástroje Ngen.exe, vazba na nativní bitovou kopii není povolena.  
  
```  
*** Assembly Binder Log Entry  (12/8/2006 @ 5:22:07 PM) ***  
  
The operation failed.  
Bind result: hr = 0x80070002. The system cannot find the file specified.  
  
Assembly manager loaded from:  E:\Windows\Microsoft.NET\Framework64\v2.0.50727\mscorwks.dll  
Running under executable  E:\test\App.exe  
--- A detailed error log follows.   
  
LOG: Start binding of native image App, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
LOG: IL assembly loaded from E:\test\App.exe.  
LOG: Start validating native image App, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
LOG: Start validating all the dependencies.  
LOG: [Level 1]Start validating native image dependency mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089.  
LOG: Dependency evaluation succeeded.  
LOG: [Level 1]Start validating IL dependency b, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
WRN: Dependency assembly was not found at ngen time, but is found at binding time. Disallow using this native image.  
WRN: No matching native image found.  
LOG: Bind to native image assembly did not succeed. Use IL image.  
```  
  
 Následující protokol zobrazuje selhání vazby nativní bitové kopie, ke kterému došlo, protože nastavení zabezpečení počítače při spuštění aplikace se liší od nastavení zabezpečení v době, kdy byla tato nativní bitová kopie vytvořena.  
  
```  
*** Assembly Binder Log Entry  (12/8/2006 @ 5:29:09 PM) ***  
  
The operation failed.  
Bind result: hr = 0x80004005. Unspecified error  
  
Assembly manager loaded from:  E:\Windows\Microsoft.NET\Framework64\v2.0.50727\mscorwks.dll  
Running under executable  E:\test\Application101622.exe  
--- A detailed error log follows.   
  
LOG: Start binding of native image Application101622, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
LOG: IL assembly loaded from E:\test\Application101622.exe.  
LOG: Start validating native image Application101622, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
LOG: Start validating all the dependencies.  
LOG: [Level 1]Start validating native image dependency mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089.  
LOG: Dependency evaluation succeeded.  
LOG: [Level 1]Start validating IL dependency Dependency101622, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
LOG: Dependency evaluation succeeded.  
LOG: Validation of dependencies succeeded.  
LOG: Start loading all the dependencies into load context.  
LOG: Loading of dependencies succeeded.  
LOG: Bind to native image succeeded.  
Native image has correct version information.  
Attempting to use native image E:\Windows\assembly\NativeImages_v2.0.50727_64\Application101622\1ac7fadabec4f72575d807501e9fdc72\Application101622.ni.exe.  
Rejecting native image because it failed the security check. The assembly's permissions must have changed since the time it was ngenned, or it is running with a different security context.  
Discarding native image.  
```  
  
## <a name="the-log-settings-dialog"></a>Dialogové okno nastavení protokolu  
 Můžete použít **nastavení protokolu** dialogovém okně můžete provádět následující akce.  
  
#### <a name="to-disable-logging"></a>Zákaz protokolování  
  
-   Vyberte **protokolu zakázáno** tlačítko.  Tato možnost je ve výchozím stavu zvolena.  
  
#### <a name="to-log-assembly-binds-in-exceptions"></a>Protokolování vazby sestavení ve výjimkách  
  
-   Vyberte **přihlásit text výjimky** tlačítko. Pouze nejméně podrobné informace protokolu jsou zaznamenány v textu výjimky. Chcete-li zobrazit úplné informace, použijte některé z dalších nastavení.  
  
     Prohlédněte si důležitou poznámku týkající se sestavení, která jsou načtena jako doménově neutrální.  
  
#### <a name="to-log-assembly-bind-failures"></a>Protokolování selhání vazby sestavení  
  
-   Vyberte **selhání vazby protokolu na disk** tlačítko.  
  
     Prohlédněte si důležitou poznámku týkající se sestavení, která jsou načtena jako doménově neutrální.  
  
#### <a name="to-log-all-assembly-binds"></a>Protokolování všech vazeb sestavení  
  
-   Vyberte **protokolu všechny vazby na disk** tlačítko.  
  
     Prohlédněte si důležitou poznámku týkající se sestavení, která jsou načtena jako doménově neutrální.  
  
> [!IMPORTANT]
>  Když je načteno sestavení jako doména neutrální, například nastavením <xref:System.AppDomainSetup.LoaderOptimization%2A> vlastnost <xref:System.LoaderOptimization.MultiDomain?displayProperty=nameWithType> nebo <xref:System.LoaderOptimization.MultiDomainHost?displayProperty=nameWithType>, zapnout protokolování může nastat únik paměti v některých případech. K tomu může dojít, pokud je položka protokolu vytvořena při načtení doménově neutrálního modulu do domény aplikace a později, když je doména aplikace uvolněna. Položka protokolu nemusí být uvolněna až do ukončení procesu. Některé ladicí programy automaticky zapínají protokolování.  
  
#### <a name="to-enable-a-custom-log-path"></a>Povolení vlastní cesty protokolu  
  
1.  Vyberte **povolit vlastní protokol cesta** tlačítko.  
  
2.  Zadejte cestu do **cesta protokolu vlastní** textové pole.  
  
> [!NOTE]
>  [Prohlížeč protokolu vazby sestavení (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) používá mezipaměť Internet Explorer (IE) k uložení protokol vazby. Kvůli příležitostně poškození v mezipaměti IE [Prohlížeč protokolu vazby sestavení (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) může někdy přestane zobrazovat text nové protokoly vazby v okně zobrazení. V důsledku tohoto poškození infrastruktura vazeb rozhraní .NET (Fusion) nemůže do protokolu vazeb zapisovat nebo číst. (Při použití vlastní cesty protokolu k tomuto problému nedochází.)  Chcete-li opravit toto poškození a umožnit zobrazení protokolů vazeb, vymažte mezipaměť aplikace Internet Explorer (IE) odstraněním dočasných souborů internetu v dialogovém okně Možnosti Internetu.  
>   
>  Pokud vaše nespravované aplikace je hostitelem modul common language runtime implementací `IHostAssemblyManager` a `IHostAssemblyStore` rozhraní, položky protokolu nemůže být uložen do mezipaměti wininet.  Chcete-li zobrazit položky protokolu pro vlastní hostitele implementující tato rozhraní, je nutné zadat alternativní cestu k protokolu.  
  
#### <a name="to-enable-logging-for-apps-running-in-the-windows-app-container"></a>Povolení protokolování pro aplikace spuštěné v kontejneru pro aplikace systému Windows  
  
1.  Povolte vlastní cestu protokolu, jak je popsáno v předchozí proceduře. Ve výchozím nastavení mají aplikace spuštěné v kontejneru pro aplikace systému Windows omezený přístup na pevný disk. Zadaný adresář bude mít přístup pro čtení a zápis pro všechny aplikace v kontejneru aplikace.  
  
2.  Vyberte **dokonalé protokolování** zaškrtávací políčko.  
  
    > [!NOTE]
    >  Toto pole je povoleno pouze v systému Windows 8 nebo novějším.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.TypeLoadException>  
 [Nástroje](../../../docs/framework/tools/index.md)  
 [Globální mezipaměť sestavení](../../../docs/framework/app-domains/gac.md)  
 [Jak běhové prostředí vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
