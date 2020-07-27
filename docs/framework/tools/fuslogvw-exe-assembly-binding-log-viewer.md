---
title: Fuslogvw.exe (prohlížeč protokolu vazby sestavení)
description: Použijte Fuslogvw.exe, prohlížeč protokolů vazby sestavení. Tento prohlížeč zobrazuje podrobnosti vazby sestavení, které pomáhají diagnostikovat, proč rozhraní .NET nemůže najít sestavení v době běhu.
ms.date: 03/30/2017
helpviewer_keywords:
- failed assembly binds
- Fuslogvw.exe
- displaying failed assembly bind details
- assemblies [.NET Framework], failed assembly binds
- locating assemblies
- Assembly Binding Log Viewer
ms.assetid: e32fa443-0778-4cc3-bf36-5c8ea297d296
ms.openlocfilehash: 949f9cf98d5eb4e100be9837be120038f085cc40
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167120"
---
# <a name="fuslogvwexe-assembly-binding-log-viewer"></a>Fuslogvw.exe (prohlížeč protokolu vazby sestavení)

Nástroj Assembly Binding Log Viewer zobrazuje podrobnosti o vazbách sestavení. Tyto informace vám pomohou diagnostikovat, proč rozhraní .NET Framework nemůže najít sestavení v době běhu. Tyto chyby jsou obvykle výsledkem nasazení sestavení na nesprávné místo, neplatné nativní bitové kopie nebo neshody čísel verzí nebo jazykových verzí. Modul CLR (Common Language Runtime) při hledání sestavení obvykle zobrazuje <xref:System.TypeLoadException> ve vaší aplikaci.

> [!IMPORTANT]
> Nástroj fuslogvw.exe je nutné spustit s oprávněními správce.

Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7) s přihlašovacími údaji správce. Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md).

V příkazovém řádku zadejte následující:

```console
fuslogvw
```

Prohlížeč zobrazí záznam pro každou nezdařenou vazbu sestavení. Pro každou chybu prohlížeč vypíše aplikaci, která iniciovala tuto vazbu, sestavení, kterého se vazba týká, včetně názvu, verze, jazykové verze, veřejného klíče a data a času chyby.

### <a name="to-change-the-log-location-view"></a>Změna umístění zobrazení protokolu

1. Chcete-li zobrazit selhání vazeb pro všechny typy aplikací, vyberte přepínač **výchozí** . Položky protokolu jsou ve výchozím nastavení uloženy na disku do mezipaměti rozhraní wininet v adresářích jednotlivých uživatelů.

2. Pokud chcete zobrazit chyby vazeb ve vlastním adresáři, který určíte, vyberte **vlastní** přepínač. Je nutné zadat vlastní umístění, kam má modul runtime ukládat protokoly, nastavením umístění vlastního protokolu v dialogovém okně **nastavení protokolu** na platný název adresáře. Tento adresář by měl být prázdný a měl by obsahovat pouze soubory, které generuje modul runtime. Pokud obsahuje spustitelný soubor, který generuje chybu do protokolu, tato chyba nebude protokolována, protože se nástroj pokusí vytvořit adresář se stejným názvem jako tento spustitelný soubor. Kromě toho se nezdaří pokus o spuštění spustitelného souboru z umístění protokolu.

    > [!NOTE]
    > Výchozí umístění vazby je vhodnější než vlastní umístění vazby. Modul runtime ukládá výchozí umístění vazby v mezipaměti WinInet a proto ho automaticky vyčistí. Pokud zadáte vlastní umístění vazby, zodpovídáte za jeho vyčištění.

### <a name="to-view-details-about-a-specific-failure"></a>Zobrazení podrobností o konkrétní chybě

1. V prohlížeči vyberte název aplikace požadovaného záznamu.

2. Klikněte na tlačítko **Zobrazit protokol** . Záznam lze vybrat také dvojitým kliknutím.

    Nástroj zobrazí následující podrobnosti o vybrané chybě vazby:

    - Konkrétní důvod selhání vazby, například „soubor nebyl nalezen“ nebo „neshoda verzí“.

    - Informace o aplikaci, která iniciovala tuto vazbu, včetně jejího názvu, kořenového adresáře aplikace (AppBase) a popisu soukromé cesty hledání, pokud existuje.

    - Identitu sestavení, které tento nástroj hledá.

    - Popis všech zásad aplikace, vydavatele nebo správce, které byly použity.

    - Zda bylo sestavení nalezeno v [globální mezipaměti sestavení (GAC](../app-domains/gac.md)).

    - Seznam všech zjišťovaných adres URL.

Následující ukázka položky protokolu zobrazuje detailní informace o selhání vazby sestavení.

```output
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

1. Vyberte záznam v prohlížeči.

2. Klikněte na tlačítko **Odstranit položku** .

### <a name="to-delete-all-entries-from-the-log"></a>Odstranění všech záznamů z protokolu

- Klikněte na tlačítko **Odstranit vše** .

### <a name="to-refresh-the-user-interface"></a>Obnovení uživatelského rozhraní

- Klikněte na tlačítko **aktualizovat** . Prohlížeč automaticky nerozpozná nové položky protokolu, pokud je spuštěn. K jejich zobrazení musíte použít tlačítko **aktualizovat** .

### <a name="to-change-the-log-settings"></a>Změna nastavení protokolu

- Kliknutím na tlačítko **Nastavení** otevřete dialogové okno **nastavení protokolu** .

### <a name="to-view-the-about-dialog"></a>Zobrazení dialogového okna O programu

- Klikněte na tlačítko **o produktu** .

## <a name="binding-logs-for-native-images"></a>Protokoly vazeb nativních bitových kopií

Ve výchozím nastavení nástroj Fuslogvw.exe zaznamenává normální požadavky vazby sestavení. Alternativně můžete protokolovat vazby sestavení pro nativní bitové kopie, které byly vytvořeny pomocí [Ngen.exe (generátor nativních imagí)](ngen-exe-native-image-generator.md).

#### <a name="to-log-assembly-binds-for-native-images"></a>Protokolování vazeb sestavení nativních bitových kopií

- Ve skupině **Kategorie protokolů** vyberte přepínač **nativní bitové kopie** .

Následující protokol zobrazuje chybu způsobenou neexistující závislostí při vytvoření nativní bitové kopie pro aplikaci. Pokud se tyto závislosti v době běhu liší od závislostí při spuštění nástroje Ngen.exe, vazba na nativní bitovou kopii není povolena.

```output
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

```output
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

Pomocí dialogového okna **nastavení protokolu** můžete provést následující akce.

#### <a name="to-disable-logging"></a>Zákaz protokolování

- Vyberte přepínač **protokol zakázán** .  Tato možnost je ve výchozím stavu zvolena.

#### <a name="to-log-assembly-binds-in-exceptions"></a>Protokolování vazby sestavení ve výjimkách

- Vyberte přepínač **Protokolovat text výjimky** . Pouze nejméně podrobné informace protokolu jsou zaznamenány v textu výjimky. Chcete-li zobrazit úplné informace, použijte některé z dalších nastavení.

  Prohlédněte si důležitou poznámku týkající se sestavení, která jsou načtena jako doménově neutrální.

#### <a name="to-log-assembly-bind-failures"></a>Protokolování selhání vazby sestavení

- Vyberte přepínač **Protokolovat chyby vazby na disk** .

  Prohlédněte si důležitou poznámku týkající se sestavení, která jsou načtena jako doménově neutrální.

#### <a name="to-log-all-assembly-binds"></a>Protokolování všech vazeb sestavení

- Vyberte přepínač **Protokolovat všechny vazby na disk** .

  Prohlédněte si důležitou poznámku týkající se sestavení, která jsou načtena jako doménově neutrální.

> [!IMPORTANT]
> Když je sestavení načteno jako doménově neutrální, například nastavením <xref:System.AppDomainSetup.LoaderOptimization%2A> vlastnosti na <xref:System.LoaderOptimization.MultiDomain?displayProperty=nameWithType> nebo <xref:System.LoaderOptimization.MultiDomainHost?displayProperty=nameWithType> , zapnutí protokolování může v některých případech způsobit nevracení paměti. K tomu může dojít, pokud je položka protokolu vytvořena při načtení doménově neutrálního modulu do domény aplikace a později, když je doména aplikace uvolněna. Položka protokolu nemusí být uvolněna až do ukončení procesu. Některé ladicí programy automaticky zapínají protokolování.

#### <a name="to-enable-a-custom-log-path"></a>Povolení vlastní cesty protokolu

1. Vyberte přepínač **Povolit vlastní cestu protokolu** .

2. Zadejte cestu do textového pole **vlastní cesta protokolu** .

> [!NOTE]
> [Prohlížeč protokolů vazby sestavení (Fuslogvw.exe)](fuslogvw-exe-assembly-binding-log-viewer.md) používá mezipaměť aplikace Internet Explorer (IE) k uložení protokolu vazby. V důsledku příležitostného poškození mezipaměti IE může [Prohlížeč protokolu vazeb sestavení (Fuslogvw.exe)](fuslogvw-exe-assembly-binding-log-viewer.md) někdy zastavit zobrazování nových protokolů vazby v okně zobrazení. V důsledku tohoto poškození infrastruktura vazeb rozhraní .NET (Fusion) nemůže do protokolu vazeb zapisovat nebo číst. (K tomuto problému nedochází, pokud použijete vlastní cestu protokolu.)  Chcete-li opravit poškození a dovolit, aby fúze znovu zobrazovala protokoly vazby, vymažte mezipaměť IE odstraněním dočasných internetových souborů z dialogového okna Internet možnosti Internetu.
>
> Pokud vaše nespravovaná aplikace je hostitelem modulu CLR (Common Language Runtime) implementací `IHostAssemblyManager` `IHostAssemblyStore` rozhraní a, položky protokolu nelze ukládat do mezipaměti WinInet.  Chcete-li zobrazit položky protokolu pro vlastní hostitele implementující tato rozhraní, je nutné zadat alternativní cestu k protokolu.

#### <a name="to-enable-logging-for-apps-running-in-the-windows-app-container"></a>Povolení protokolování pro aplikace spuštěné v kontejneru pro aplikace systému Windows

1. Povolte vlastní cestu protokolu, jak je popsáno v předchozí proceduře. Ve výchozím nastavení mají aplikace spuštěné v kontejneru pro aplikace systému Windows omezený přístup na pevný disk. Zadaný adresář bude mít přístup pro čtení a zápis pro všechny aplikace v kontejneru aplikace.

2. Zaškrtněte políčko **Povolit moderní protokolování** .

    > [!NOTE]
    > Toto pole je povoleno pouze v systému Windows 8 nebo novějším.

## <a name="see-also"></a>Viz také

- <xref:System.TypeLoadException>
- [Nástroje](index.md)
- [Globální mezipaměť sestavení](../app-domains/gac.md)
- [Jak běhové prostředí vyhledává sestavení](../deployment/how-the-runtime-locates-assemblies.md)
- [Výzvy příkazového řádku](developer-command-prompt-for-vs.md)
