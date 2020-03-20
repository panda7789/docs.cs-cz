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
ms.openlocfilehash: 0052475697dae2c3ad891db18d300b5ec08a7e62
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180352"
---
# <a name="mpgoexe-managed-profile-guided-optimization-tool"></a>Mpgo.exe (Nástroj pro optimalizaci spravovaného kódu na základě profilu)

Nástroj pro optimalizaci spravovaných profilů (Mpgo.exe) je nástroj příkazového řádku, který používá běžné scénáře koncových uživatelů k optimalizaci nativních obrazových sestavení vytvořených [generátorem nativních bitových obrázků (Ngen.exe).](ngen-exe-native-image-generator.md) Tento nástroj umožňuje spustit trénovací scénáře, které generují data profilu. Generátor [nativních bitových obrázků (Ngen.exe)](ngen-exe-native-image-generator.md) používá tato data k optimalizaci sestavení generovaných nativních aplikací bitové kopie. Trénovací scénář je zkušební spuštění očekávaného použití aplikace. Nástroj Mpgo.exe je k dispozici v sadě Visual Studio Ultimate 2012 a vyšší. Počínaje Visual Studio 2013, můžete také použít Mpgo.exe k optimalizaci aplikací pro Windows 8.x Store.  
  
Profilováním řízená optimalizace zlepšuje dobu spuštění aplikace, využití paměti (velikost pracovní sady) a propustnost pomocí shromažďování dat z trénovacích scénářů a jejich použitím pro optimalizaci rozložení nativních bitových kopií.  
  
Při výkonových potížích s časem spuštění a velikostí pracovní sady pro sestavení jazyka IL doporučujeme nejdříve použít nástroj Ngen.exe k eliminaci nároků spojených s kompilací JIT a k usnadnění sdílení kódu. V případě potřeby dalšího zlepšení je k optimalizaci aplikace možné použít nástroj Mpgo.exe. Data o výkonu z neoptimalizované nativní bitové kopie sestavení je možné použít jako základ k vyhodnocení zlepšení výkonu. Použití nástroje Mpgo.exe může mít za následek rychlejší úplné spuštění a menší velikost pracovní sady. Nástroj Mpgo.exe přidá informace do sestavení jazyka IL, které nástroj Ngen.exe používá k vytvoření optimalizované nativní bitové kopie sestavení. Další informace naleznete v položce [Zlepšení výkonu spuštění aplikací klasické pracovní plochy](https://devblogs.microsoft.com/dotnet/improving-launch-performance-for-your-desktop-applications/) v blogu .NET.  
  
Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li nástroj spustit, použijte příkazový řádek pro vývojáře pro sadu Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7) s pověřeními správce a na příkazovém řádku zadejte následující příkaz. Další informace naleznete v [příkazových koncích](developer-command-prompt-for-vs.md).  
  
Pro aplikace klasické pracovní plochy:  
  
```console  
mpgo –Scenario <command> [-Import <directory>] –AssemblyList <assembly1>  <assembly2> ... -OutDir <directory> [options]  
```  
  
Pro aplikace pro Windows 8.x Store:  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
mpgo –Scenario <packageName> -AppID <appId> -Timeout <seconds>  
```  
  
## <a name="parameters"></a>Parametry  
 Žádný argument nástroje Mpgo.exe nerozlišuje velká a malá písmena. Příkazy začínají pomlčkou.  
  
> [!NOTE]
> Můžete použít `–Scenario` buď `–Import` nebo jako požadovaný příkaz, ale ne obojí. Pokud zadáte `–Reset` možnost, nepoužije se žádný z požadovaných parametrů.

|Povinný parametr|Popis|
|------------------------|-----------------|
|`-Scenario`\< *příkaz*><br /><br /> —nebo—<br /><br /> `-Scenario`\< *packageName*><br /><br /> -nebo-<br /><br /> `-Import`\< *adresář*>|U aplikací klasické `–Scenario` pracovní plochy použijte k určení příkazu pro spuštění aplikace, kterou chcete optimalizovat, včetně všech argumentů příkazového řádku. Použijte tři sady dvojitých uvozovek kolem *příkazu,* pokud určuje cestu, která obsahuje mezery; například: `mpgo.exe -scenario """C:\My App\myapp.exe""" -assemblylist """C:\My App\myapp.exe""" -outdir "C:\optimized files"`. Nepoužívejte dvojité uvozovky; nebudou pracovat správně, pokud *příkaz* obsahuje mezery.<br /><br /> -nebo-<br /><br /> Pro aplikace pro Windows 8.x Store použijte `–Scenario` k určení balíčku, pro který chcete generovat informace o profilu. Při zadání zobrazovaného názvu balíčku nebo názvu řady balíčků namísto kompletního názvu balíčku nástroj Mpgo.exe vybere balíček, který se shoduje se zadaným názvem, pokud existuje pouze jediná shoda. Pokud zadanému názvu odpovídá více balíčků, nástroj Mpgo.exe vyzve k výběru balíčku.<br /><br /> —nebo—<br /><br /> Slouží `-Import` k určení, že data optimalizace z dříve optimalizovaných `-AssemblyList`sestavení by měla být použita k optimalizaci sestavení v . *adresář* určuje adresář, který obsahuje dříve optimalizované soubory. Sestavení zadaná `–AssemblyList` `–AssemblyListFile` v nebo jsou nové verze sestavení, které mají být optimalizovány pomocí dat z importovaných souborů. Použití optimalizačních dat ze starších verzí sestavení umožňuje optimalizovat novější verze sestavení bez opětovného spuštění scénáře.  Nicméně, pokud importované a cílové sestavení obsahují výrazně odlišný kód, optimalizační data budou neúčinná. Názvy sestavení `–AssemblyList` zadané `–AssemblyListFile` v adresáři nebo `–Import`v adresáři určeném *adresářem*musí být přítomny. Použijte tři sady dvojitých uvozovek kolem *adresáře,* pokud určuje cestu, která obsahuje mezery.<br /><br /> Je nutné `–Scenario` zadat `–Import`buď nebo , ale ne oba parametry.|
|`-OutDir`\< *adresář*>|Adresář, do kterého se umístí optimalizovaná sestavení. Pokud sestavení již existuje ve složce výstupního adresáře, vytvoří se nová kopie a k jeho názvu se připojí číslo indexu. například: *název_assembly*-1.exe. Pokud určuje cestu, která obsahuje mezery, použijte kolem *adresáře* dvojité uvozovky.|
|`-AssemblyList`\< *assembly1 assembly2 ...*><br /><br /> —nebo—<br /><br /> `-AssemblyListFile`\< *soubor*>|Seznam sestavení (včetně souborů .exe a .dll) oddělených mezerami, o kterých je třeba shromáždit profilovací informace. Můžete určit `C:\Dir\*.dll` `*.dll` nebo vybrat všechna sestavení v určeném nebo aktuálním pracovním adresáři. Další informace naleznete v části Poznámky.<br /><br /> —nebo—<br /><br /> Textový soubor obsahující seznam sestavení, o kterých je třeba shromáždit profilovací informace. Vždy je uvedeno jedno sestavení na řádku. Pokud název sestavení začíná pomlčkou (-), je třeba použít soubor seznamu sestavení nebo sestavení přejmenovat.|
|`-AppID`\< *appId*>|ID aplikace v zadaném balíčku. Pokud použijete zástupný\*znak ( ), Mpgo.exe se pokusí vytvořit výčet AppID \<v balíčku a bude klesat zpět na *package_family_name*>! Aplikace, pokud se nezdaří. Při zadání řetězce, který má předponu vykřičník (!), bude nástroj Mpgo.exe řetězit název řady balíčků s dodaným argumentem.|
|`-Timeout`\< *sekundy*>|Doba, po kterou se aplikace pro Windows 8.x Store spustí před ukončením aplikace.|

|Volitelný parametr|Popis|
|------------------------|-----------------|
|`-64bit`|Upraví sestavení pro 64bitové systémy.  Tento parametr je nutné zadat pro 64bitová sestavení, i když sestavení samo sebe prohlašuje za 64bitové.|
|`-ExeConfig`\< *název souboru*>|Určuje konfigurační soubor, který scénář využívá k poskytování informací o verzi a zavaděči.|
|`-f`|Vynutí zahrnutí dat profilu do binárního sestavení, i pokud je podepsáno.  Pokud je sestavení podepsáno, je třeba jej znovu podepsat, jinak se načtení a spuštění sestavení nezdaří.|
|`-Reset`|Nastaví výchozí hodnoty prostředí pro ujištění, že přerušená relace profilování nemá žádný vliv na sestavení, a poté se ukončí. Prostředí je nastaveno na výchozí hodnoty standardně před relací a po relaci profilování.|
|`-Timeout`\< *čas v sekundách*>|Určuje dobu profilování v sekundách. Je třeba použít hodnotu, která je mírně vyšší než pozorované časy spuštění grafického uživatelského rozhraní (GUI) aplikace. Na konci časového limitu jsou zaznamenána data profilu, přestože aplikace nadále běží. Pokud tuto možnost nenastavíte, bude profilování pokračovat až do ukončení aplikace, kdy budou data zaznamenána.|
|`-LeaveNativeImages`|Určuje, že po spuštění scénáře by neměly být odebrány upravené nativní bitové kopie. Tato možnost se používá především u aplikace, která byla určena pro spuštěný scénář. Zabrání opětovnému vytvoření nativních bitových kopií pro následné spuštění nástroje Mpgo.exe. Při zadání této možnosti mohou být po dokončení běhu aplikace ve vyrovnávací paměti přítomny osamocené nativní bitové kopie. V takovém případě spusťte mpgo.exe se stejným `–RemoveNativeImages` scénářem a seznamem sestavení a použijte parametr k odebrání těchto nativních bitových kopií.|
|`-RemoveNativeImages`|Vyčistí z běhu, `–LeaveNativeImages` kde byl zadán. Pokud zadáte `-RemoveNativeImages`, Program Mpgo.exe ignoruje `-64bit` `–AssemblyList`všechny argumenty s výjimkou a a ukončí po odebrání všech instrumentovaných nativních obrazů.|

## <a name="remarks"></a>Poznámky
 Na příkazovém řádku můžete použít obojí `–AssemblyList` i `- AssemblyListFile` vícekrát.

 Pokud při určování sestavení nezadáte úplný název cesty, nástroj Mpgo.exe hledá v aktuálním adresáři. Při zadání nesprávné cesty nástroj Mpgo.exe zobrazí chybovou zprávu, ale stále generuje data pro jiná sestavení. Při zadání sestavení, které není načteno během trénovacího scénáře, nejsou pro toto sestavení generována žádná trénovací data.

 Jestliže se sestavení ze seznamu nachází v globální mezipaměti sestavení (GAC), nebude aktualizováno pro zahrnutí informací o profilu.  Pro shromáždění informací o profilu je třeba sestavení odebrat z globální mezipaměti sestavení (GAC).

 Použití nástrojů Ngen.exe a Mpgo.exe je doporučeno pouze pro velké spravované aplikace, protože výhoda předkompilovaných nativních bitových kopií je obvykle vidět pouze v případě, že eliminuje významné množství kompilace JIT za běhu. Spuštění programu Mpgo.exe v aplikacích stylu "Hello World", které nejsou náročné na pracovní sadu, neposkytne žádné výhody a mpgo.exe může dokonce selhat při shromažďování dat profilu.

> [!NOTE]
> Nástroje Ngen.exe a Mpgo.exe nejsou vhodné pro aplikace ASP.NET a služby Windows Communication Foundation (WCF).  
  
## <a name="to-use-mpgoexe"></a>Použití nástroje Mpgo.exe  
  
1. Použijte počítač, který má nainstalovánu vaši aplikaci a sadu Visual Studio Ultimate 2012.  
  
2. Spusťte nástroj Mpgo.exe jako správce s nezbytnými parametry.  Ukázkové příkazy naleznete v další části.  
  
     Sestavení optimalizovaného zprostředkujícího jazyka (IL) jsou `–OutDir` vytvořena ve složce určené `C:\Optimized` parametrem (v příkladech se jedná o složku).  
  
3. Nahraďte sestavení IL použitá pro soubor Ngen.exe novými sestaveními IL, `–OutDir`která obsahují informace o profilu z adresáře určeného aplikací .  
  
4. Instalace aplikace (pomocí bitových kopií poskytnutých nástrojem Mpgo.exe) nainstaluje optimalizované nativní bitové kopie.  
  
## <a name="suggested-workflow"></a>Navrhovaný pracovní postup  
  
1. Vytvořte sadu optimalizovaných sestav IL pomocí parametru `–Scenario` Mpgo.exe.  
  
2. Zaveďte optimalizovaná sestavení jazyka IL do správy zdrojového kódu.  
  
3. V procesu sestavení volejte Mpgo.exe s `–Import` parametrem jako krok po sestavení pro generování optimalizovaných il bitových kopií pro předání ngen.exe.  
  
 Tento proces zajišťuje, že všechna sestavení mají optimalizační data. Při častějším zavádění aktualizovaných optimalizovaných sestavení (kroky 1 a 2) bude výkon během celého vývoje produktu konzistentnější.  
  
## <a name="using-mpgoexe-from-visual-studio"></a>Použití nástroje Mpgo.exe ze sady Visual Studio  
 Mpgo.exe můžete spustit z Visual Studia (viz článek [Jak: Zadejte události sestavení (C#)](/visualstudio/ide/how-to-specify-build-events-csharp)s následujícími omezeními:  
  
- Nelze použít cesty v uvozovkách ukončené lomítkem, protože makra sady Visual Studio ve výchozím nastavení také používají koncová lomítka. (Například `–OutDir "C:\Output Folder\"` je neplatný.) Chcete-li toto omezení obejít, můžete uniknout koncovému lomítku. (Místo toho `-OutDir "$(OutDir)\"` použijte například.)  
  
- Ve výchozím nastavení není nástroj Mpgo.exe v cestě sestavení sady Visual Studio. Je nutné přidat cestu do sady Visual Studio nebo zadat úplnou cestu v příkazovém řádku nástroje Mpgo.exe. Můžete použít `–Scenario` buď nebo `–Import` parametr v post-build události v sadě Visual Studio. Typickým procesem je `–Scenario` však použít jednou z příkazového řádku `–Import` pro vývojáře pro Visual Studio a potom použít k aktualizaci optimalizovaných sestavení po každém sestavení; například: `"C:\Program Files\Microsoft Visual Studio 11.0\Team Tools\Performance Tools\mpgo.exe" -import "$(OutDir)tmp" -assemblylist "$(TargetPath)" -outdir "$(OutDir)\"`.  
  
<a name="samples"></a>
## <a name="examples"></a>Příklady  
 Následující příkaz Mpgo.exe z příkazového řádku pro vývojáře pro Visual Studio optimalizuje daňovou aplikaci:  
  
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
  
## <a name="see-also"></a>Viz také

- [Ngen.exe (generátor nativních obrázků)](ngen-exe-native-image-generator.md)
- [Příkazové řádky](developer-command-prompt-for-vs.md)
- [Zlepšení výkonu spuštění pro desktopové aplikace](https://devblogs.microsoft.com/dotnet/improving-launch-performance-for-your-desktop-applications/)
- [Přehled vylepšení výkonu v rozhraní .NET 4.5](https://docs.microsoft.com/archive/msdn-magazine/2012/april/clr-an-overview-of-performance-improvements-in-net-4-5)
