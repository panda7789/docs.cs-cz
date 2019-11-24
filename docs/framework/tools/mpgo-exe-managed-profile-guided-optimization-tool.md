---
title: Mpgo.exe (Nástroj pro optimalizaci spravovaného kódu na základě profilu)
ms.date: 03/30/2017
helpviewer_keywords:
- Mpgo.exe
- training scenarios, generating profiles with
- Managed Profile Guided Optimization Tool
- Ngen.exe
- Ngen.exe, profilers and native images
ms.assetid: f6976502-a000-4fbe-aaf5-a7aab9ce4ec2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a5ab3040a246a135771c45b2639567db9ab510e3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447971"
---
# <a name="mpgoexe-managed-profile-guided-optimization-tool"></a>Mpgo.exe (Nástroj pro optimalizaci spravovaného kódu na základě profilu)

The Managed Profile Guided Optimization Tool (Mpgo.exe) is a command-line tool that uses common end-user scenarios to optimize the native image assemblies that are created by the [Native Image Generator (Ngen.exe)](ngen-exe-native-image-generator.md). Tento nástroj umožňuje spustit trénovací scénáře, které generují data profilu. The [Native Image Generator (Ngen.exe)](ngen-exe-native-image-generator.md) uses this data to optimize its generated native image application assemblies. Trénovací scénář je zkušební spuštění očekávaného použití aplikace. Nástroj Mpgo.exe je k dispozici v sadě Visual Studio Ultimate 2012 a vyšší. Starting with Visual Studio 2013, you can also use Mpgo.exe to optimize Windows 8.x Store apps.  
  
Profilováním řízená optimalizace zlepšuje dobu spuštění aplikace, využití paměti (velikost pracovní sady) a propustnost pomocí shromažďování dat z trénovacích scénářů a jejich použitím pro optimalizaci rozložení nativních bitových kopií.  
  
Při výkonových potížích s časem spuštění a velikostí pracovní sady pro sestavení jazyka IL doporučujeme nejdříve použít nástroj Ngen.exe k eliminaci nároků spojených s kompilací JIT a k usnadnění sdílení kódu. V případě potřeby dalšího zlepšení je k optimalizaci aplikace možné použít nástroj Mpgo.exe. Data o výkonu z neoptimalizované nativní bitové kopie sestavení je možné použít jako základ k vyhodnocení zlepšení výkonu. Použití nástroje Mpgo.exe může mít za následek rychlejší úplné spuštění a menší velikost pracovní sady. Nástroj Mpgo.exe přidá informace do sestavení jazyka IL, které nástroj Ngen.exe používá k vytvoření optimalizované nativní bitové kopie sestavení. For more information, see the entry [Improving Launch Performance for your Desktop Applications](https://devblogs.microsoft.com/dotnet/improving-launch-performance-for-your-desktop-applications/) in the .NET blog.  
  
Tento nástroj je automaticky nainstalován se sadou Visual Studio. To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7) with administrator credentials, and type the following at the command prompt. For more information, see [Command Prompts](developer-command-prompt-for-vs.md).  
  
Pro aplikace klasické pracovní plochy:  
  
```console  
mpgo –Scenario <command> [-Import <directory>] –AssemblyList <assembly1>  <assembly2> ... -OutDir <directory> [options]  
```  
  
For Windows 8.x Store apps:  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
mpgo –Scenario <packageName> -AppID <appId> -Timeout <seconds>  
```  
  
## <a name="parameters"></a>Parametry  
 Žádný argument nástroje Mpgo.exe nerozlišuje velká a malá písmena. Příkazy začínají pomlčkou.  
  
> [!NOTE]
> You can use either `–Scenario` or `–Import` as a required command, but not both. None of the required parameters are used if you specify the `–Reset` option.

|Povinný parametr|Popis|
|------------------------|-----------------|
|`-Scenario` \<*command*><br /><br /> —nebo—<br /><br /> `-Scenario` \<*packageName*><br /><br /> -nebo-<br /><br /> `-Import` \<*directory*>|For desktop apps, use `–Scenario` to specify the command to run the application you want to optimize, including any command-line arguments. Use three sets of double quotation marks around *command* if it specifies a path that includes spaces; for example: `mpgo.exe -scenario """C:\My App\myapp.exe""" -assemblylist """C:\My App\myapp.exe""" -outdir "C:\optimized files"`. Do not use double quotation marks; they will not work correctly if *command* includes spaces.<br /><br /> -nebo-<br /><br /> For Windows 8.x Store apps, use `–Scenario` to specify the package that you want to generate profile information for. Při zadání zobrazovaného názvu balíčku nebo názvu řady balíčků namísto kompletního názvu balíčku nástroj Mpgo.exe vybere balíček, který se shoduje se zadaným názvem, pokud existuje pouze jediná shoda. Pokud zadanému názvu odpovídá více balíčků, nástroj Mpgo.exe vyzve k výběru balíčku.<br /><br /> —nebo—<br /><br /> Use `-Import` to specify that optimization data from previously optimized assemblies should be used to optimize the assemblies in `-AssemblyList`. *directory* specifies the directory that contains the previously optimized files. The assemblies specified in `–AssemblyList` or `–AssemblyListFile` are the new versions of the assemblies to be optimized using the data from the imported files. Použití optimalizačních dat ze starších verzí sestavení umožňuje optimalizovat novější verze sestavení bez opětovného spuštění scénáře.  Nicméně, pokud importované a cílové sestavení obsahují výrazně odlišný kód, optimalizační data budou neúčinná. The assembly names specified in `–AssemblyList` or `–AssemblyListFile` must be present in the directory specified by `–Import`*directory*. Use three sets of double quotation marks around *directory* if it specifies a path that includes spaces.<br /><br /> You must specify either `–Scenario` or `–Import`, but not both parameters.|
|`-OutDir` \<*directory*>|Adresář, do kterého se umístí optimalizovaná sestavení. If an assembly already exists in the output directory folder, a new copy is created and an index number is appended to its name; for example: *assemblyname*-1.exe. Use double quotation marks around *directory* if it specifies a path that contains spaces.|
|`-AssemblyList` \<*assembly1 assembly2 ...* ><br /><br /> —nebo—<br /><br /> `-AssemblyListFile` \<*file*>|Seznam sestavení (včetně souborů .exe a .dll) oddělených mezerami, o kterých je třeba shromáždit profilovací informace. You can specify `C:\Dir\*.dll` or `*.dll` to select all the assemblies in the designated or current working directory. Další informace naleznete v části Poznámky.<br /><br /> —nebo—<br /><br /> Textový soubor obsahující seznam sestavení, o kterých je třeba shromáždit profilovací informace. Vždy je uvedeno jedno sestavení na řádku. Pokud název sestavení začíná pomlčkou (-), je třeba použít soubor seznamu sestavení nebo sestavení přejmenovat.|
|`-AppID` \<*appId*>|ID aplikace v zadaném balíčku. If you use the wildcard (\*), Mpgo.exe will try to enumerate the AppIDs in the package and will fall back to \<*package_family_name*>!App if it fails. Při zadání řetězce, který má předponu vykřičník (!), bude nástroj Mpgo.exe řetězit název řady balíčků s dodaným argumentem.|
|`-Timeout` \<*seconds*>|The amount of time to allow the Windows 8.x Store app to run before the app exits.|

|Volitelný parametr|Popis|
|------------------------|-----------------|
|`-64bit`|Upraví sestavení pro 64bitové systémy.  Tento parametr je nutné zadat pro 64bitová sestavení, i když sestavení samo sebe prohlašuje za 64bitové.|
|`-ExeConfig` \<*filename*>|Určuje konfigurační soubor, který scénář využívá k poskytování informací o verzi a zavaděči.|
|`-f`|Vynutí zahrnutí dat profilu do binárního sestavení, i pokud je podepsáno.  Pokud je sestavení podepsáno, je třeba jej znovu podepsat, jinak se načtení a spuštění sestavení nezdaří.|
|`-Reset`|Nastaví výchozí hodnoty prostředí pro ujištění, že přerušená relace profilování nemá žádný vliv na sestavení, a poté se ukončí. Prostředí je nastaveno na výchozí hodnoty standardně před relací a po relaci profilování.|
|`-Timeout` \<*time in seconds*>|Určuje dobu profilování v sekundách. Je třeba použít hodnotu, která je mírně vyšší než pozorované časy spuštění grafického uživatelského rozhraní (GUI) aplikace. Na konci časového limitu jsou zaznamenána data profilu, přestože aplikace nadále běží. Pokud tuto možnost nenastavíte, bude profilování pokračovat až do ukončení aplikace, kdy budou data zaznamenána.|
|`-LeaveNativeImages`|Určuje, že po spuštění scénáře by neměly být odebrány upravené nativní bitové kopie. Tato možnost se používá především u aplikace, která byla určena pro spuštěný scénář. Zabrání opětovnému vytvoření nativních bitových kopií pro následné spuštění nástroje Mpgo.exe. Při zadání této možnosti mohou být po dokončení běhu aplikace ve vyrovnávací paměti přítomny osamocené nativní bitové kopie. In this case, run Mpgo.exe with the same scenario and assembly list and use the `–RemoveNativeImages` parameter to remove these native images.|
|`-RemoveNativeImages`|Cleans up from a run where `–LeaveNativeImages` was specified. If you specify `-RemoveNativeImages`, Mpgo.exe ignores any arguments except `-64bit` and `–AssemblyList`, and exits after removing all instrumented native images.|

## <a name="remarks"></a>Poznámky
 You can use both `–AssemblyList` and `- AssemblyListFile` multiple times on the command line.

 Pokud při určování sestavení nezadáte úplný název cesty, nástroj Mpgo.exe hledá v aktuálním adresáři. Při zadání nesprávné cesty nástroj Mpgo.exe zobrazí chybovou zprávu, ale stále generuje data pro jiná sestavení. Při zadání sestavení, které není načteno během trénovacího scénáře, nejsou pro toto sestavení generována žádná trénovací data.

 Jestliže se sestavení ze seznamu nachází v globální mezipaměti sestavení (GAC), nebude aktualizováno pro zahrnutí informací o profilu.  Pro shromáždění informací o profilu je třeba sestavení odebrat z globální mezipaměti sestavení (GAC).

 Použití nástrojů Ngen.exe a Mpgo.exe je doporučeno pouze pro velké spravované aplikace, protože výhoda předkompilovaných nativních bitových kopií je obvykle vidět pouze v případě, že eliminuje významné množství kompilace JIT za běhu. Running Mpgo.exe on "Hello World" style applications that aren’t working-set intensive will not provide any benefits, and Mpgo.exe may even fail to gather profile data.

> [!NOTE]
> Nástroje Ngen.exe a Mpgo.exe nejsou vhodné pro aplikace ASP.NET a služby Windows Communication Foundation (WCF).  
  
## <a name="to-use-mpgoexe"></a>Použití nástroje Mpgo.exe  
  
1. Použijte počítač, který má nainstalovánu vaši aplikaci a sadu Visual Studio Ultimate 2012.  
  
2. Spusťte nástroj Mpgo.exe jako správce s nezbytnými parametry.  Ukázkové příkazy naleznete v další části.  
  
     The optimized intermediate language (IL) assemblies are created in the folder specified by the `–OutDir` parameter (in the examples, this is the `C:\Optimized` folder).  
  
3. Replace the IL assemblies you used for Ngen.exe  with the new IL assemblies that contain the profile information from the directory specified by `–OutDir`.  
  
4. Instalace aplikace (pomocí bitových kopií poskytnutých nástrojem Mpgo.exe) nainstaluje optimalizované nativní bitové kopie.  
  
## <a name="suggested-workflow"></a>Navrhovaný pracovní postup  
  
1. Create a set of optimized IL assemblies by using Mpgo.exe with the `–Scenario` parameter.  
  
2. Zaveďte optimalizovaná sestavení jazyka IL do správy zdrojového kódu.  
  
3. In the build process, call Mpgo.exe with the `–Import` parameter as a post-build step to generate optimized IL images to pass to Ngen.exe.  
  
 Tento proces zajišťuje, že všechna sestavení mají optimalizační data. Při častějším zavádění aktualizovaných optimalizovaných sestavení (kroky 1 a 2) bude výkon během celého vývoje produktu konzistentnější.  
  
## <a name="using-mpgoexe-from-visual-studio"></a>Použití nástroje Mpgo.exe ze sady Visual Studio  
 You can run Mpgo.exe from Visual Studio (see the article [How to: Specify Build Events (C#)](/visualstudio/ide/how-to-specify-build-events-csharp)) with the following restrictions:  
  
- Nelze použít cesty v uvozovkách ukončené lomítkem, protože makra sady Visual Studio ve výchozím nastavení také používají koncová lomítka. (For example, `–OutDir "C:\Output Folder\"` is invalid.) To work around this restriction, you can escape the trailing slash. (For example, use `-OutDir "$(OutDir)\"` instead.)  
  
- Ve výchozím nastavení není nástroj Mpgo.exe v cestě sestavení sady Visual Studio. Je nutné přidat cestu do sady Visual Studio nebo zadat úplnou cestu v příkazovém řádku nástroje Mpgo.exe. You can use either the `–Scenario` or the `–Import` parameter in the post-build event in Visual Studio. However, the typical process is to use `–Scenario` one time from a Developer Command Prompt for Visual Studio, and then use `–Import` to update the optimized assemblies after each build; for example:  `"C:\Program Files\Microsoft Visual Studio 11.0\Team Tools\Performance Tools\mpgo.exe" -import "$(OutDir)tmp" -assemblylist "$(TargetPath)" -outdir "$(OutDir)\"`.  
  
<a name="samples"></a>   
## <a name="examples"></a>Příklady  
 The following Mpgo.exe command from a Developer Command Prompt for Visual Studio optimizes a tax application:  
  
```console  
mpgo –scenario "C:\MyApp\MyTax.exe /params par" –AssemblyList Mytax.dll MyTaxUtil2011.dll –OutDir C:\Optimized –TimeOut 15  
```  
  
 Následující příkaz nástroje Mpgo.exe optimalizuje zvukovou aplikaci:  
  
```console  
mpgo –scenario "C:\MyApp\wav2wma.exe –input song1.wav –output song1.wma" –AssemblyList transcode.dll –OutDir C:\Optimized –TimeOut 15  
```  
  
 Následující příkaz nástroje Mpgo.exe používá data z dříve optimalizovaných sestavení pro optimalizaci novějších verzí sestavení:  
  
```console  
mpgo.exe -import "C:\Optimized" -assemblylist "C:\MyApp\MyTax.dll" "C:\MyApp\MyTaxUtil2011.dll" -outdir C:\ReOptimized  
```  
  
## <a name="see-also"></a>Viz také:

- [Ngen.exe (generátor nativních obrázků)](ngen-exe-native-image-generator.md)
- [Příkazové řádky](developer-command-prompt-for-vs.md)
- [Improving Launch Performance for your Desktop Applications](https://devblogs.microsoft.com/dotnet/improving-launch-performance-for-your-desktop-applications/)
- [An Overview of Performance Improvements in .NET 4.5](https://docs.microsoft.com/archive/msdn-magazine/2012/april/clr-an-overview-of-performance-improvements-in-net-4-5)
