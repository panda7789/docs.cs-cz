---
title: Mpgo.exe (Nástroj pro optimalizaci spravovaného kódu na základě profilu)
description: Použijte Mpgo.exe Nástroj pro optimalizaci spravovaného profilu. Pomocí tohoto nástroje Optimalizujte nativní sestavení imagí vytvořená generátorem nativních imagí (Ngen.exe).
ms.date: 03/30/2017
helpviewer_keywords:
- Mpgo.exe
- training scenarios, generating profiles with
- Managed Profile Guided Optimization Tool
- Ngen.exe
- Ngen.exe, profilers and native images
ms.assetid: f6976502-a000-4fbe-aaf5-a7aab9ce4ec2
ms.openlocfilehash: 18a379447e1d5ba97090eca299c59cc161c7be71
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517279"
---
# <a name="mpgoexe-managed-profile-guided-optimization-tool"></a>Mpgo.exe (Nástroj pro optimalizaci spravovaného kódu na základě profilu)

Nástroj pro optimalizaci spravovaného profilu (Mpgo.exe) je nástroj příkazového řádku, který používá běžné scénáře koncových uživatelů k optimalizaci sestavení nativní bitové kopie, která jsou vytvořena pomocí [generátoru nativních imagí (Ngen.exe)](ngen-exe-native-image-generator.md). Tento nástroj umožňuje spustit trénovací scénáře, které generují data profilu. [Generátor nativních bitových kopií (Ngen.exe)](ngen-exe-native-image-generator.md) používá tato data k optimalizaci vygenerovaných sestavení nativní bitové kopie aplikace. Trénovací scénář je zkušební spuštění očekávaného použití aplikace. Nástroj Mpgo.exe je k dispozici v sadě Visual Studio Ultimate 2012 a vyšší. Počínaje Visual Studio 2013 můžete k optimalizaci aplikací ze Storu Windows 8. x použít taky Mpgo.exe.  
  
Profilováním řízená optimalizace zlepšuje dobu spuštění aplikace, využití paměti (velikost pracovní sady) a propustnost pomocí shromažďování dat z trénovacích scénářů a jejich použitím pro optimalizaci rozložení nativních bitových kopií.  
  
Při výkonových potížích s časem spuštění a velikostí pracovní sady pro sestavení jazyka IL doporučujeme nejdříve použít nástroj Ngen.exe k eliminaci nároků spojených s kompilací JIT a k usnadnění sdílení kódu. V případě potřeby dalšího zlepšení je k optimalizaci aplikace možné použít nástroj Mpgo.exe. Data o výkonu z neoptimalizované nativní bitové kopie sestavení je možné použít jako základ k vyhodnocení zlepšení výkonu. Použití nástroje Mpgo.exe může mít za následek rychlejší úplné spuštění a menší velikost pracovní sady. Nástroj Mpgo.exe přidá informace do sestavení jazyka IL, které nástroj Ngen.exe používá k vytvoření optimalizované nativní bitové kopie sestavení. Další informace najdete v tématu [vylepšení výkonu spouštění pro desktopové aplikace](https://devblogs.microsoft.com/dotnet/improving-launch-performance-for-your-desktop-applications/) na blogu .NET.  
  
Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7) s přihlašovacími údaji správce a zadejte do příkazového řádku následující příkaz. Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md).  
  
Pro aplikace klasické pracovní plochy:  
  
```console  
mpgo –Scenario <command> [-Import <directory>] –AssemblyList <assembly1>  <assembly2> ... -OutDir <directory> [options]  
```  
  
Pro aplikace Windows 8. x ze Storu:  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
mpgo –Scenario <packageName> -AppID <appId> -Timeout <seconds>  
```  
  
## <a name="parameters"></a>Parametry  
 Žádný argument nástroje Mpgo.exe nerozlišuje velká a malá písmena. Příkazy začínají pomlčkou.  
  
> [!NOTE]
> Můžete použít buď `–Scenario` nebo `–Import` jako vyžadovaný příkaz, ale ne obojí. Pokud zadáte možnost, žádný z požadovaných parametrů se nepoužije `–Reset` .

|Povinný parametr|Description|
|------------------------|-----------------|
|`-Scenario` \<*command*><br /><br /> —nebo—<br /><br /> `-Scenario` \<*packageName*><br /><br /> -nebo-<br /><br /> `-Import` \<*directory*>|U aplikací klasické pracovní plochy použijte `–Scenario` k zadání příkazu pro spuštění aplikace, kterou chcete optimalizovat, včetně všech argumentů příkazového řádku. Použít tři sady dvojitých uvozovek kolem *příkazu* , pokud Určuje cestu, která obsahuje mezery. například: `mpgo.exe -scenario """C:\My App\myapp.exe""" -assemblylist """C:\My App\myapp.exe""" -outdir "C:\optimized files"` . Nepoužívejte dvojité uvozovky. nebudou fungovat správně, pokud *příkaz* obsahuje mezery.<br /><br /> -nebo-<br /><br /> Pro aplikace Windows 8. x pro Store použijte `–Scenario` k určení balíčku, pro který chcete vygenerovat informace o profilu. Při zadání zobrazovaného názvu balíčku nebo názvu řady balíčků namísto kompletního názvu balíčku nástroj Mpgo.exe vybere balíček, který se shoduje se zadaným názvem, pokud existuje pouze jediná shoda. Pokud zadanému názvu odpovídá více balíčků, nástroj Mpgo.exe vyzve k výběru balíčku.<br /><br /> —nebo—<br /><br /> Použijte `-Import` k určení, že se data optimalizace z dříve optimalizovaných sestavení mají použít k optimalizaci sestavení v `-AssemblyList` . *adresář* Určuje adresář, který obsahuje dříve optimalizované soubory. Sestavení zadaná v `–AssemblyList` nebo `–AssemblyListFile` jsou nové verze sestavení, které mají být optimalizovány pomocí dat z importovaných souborů. Použití optimalizačních dat ze starších verzí sestavení umožňuje optimalizovat novější verze sestavení bez opětovného spuštění scénáře.  Nicméně, pokud importované a cílové sestavení obsahují výrazně odlišný kód, optimalizační data budou neúčinná. Názvy sestavení zadané v `–AssemblyList` nebo `–AssemblyListFile` musí být přítomny v adresáři určeném `–Import` *adresářem*. Kolem *adresáře* použijte tři sady dvojitých uvozovek, pokud Určuje cestu, která obsahuje mezery.<br /><br /> Je nutné zadat buď `–Scenario` `–Import` parametry nebo, ale ne oba parametry.|
|`-OutDir` \<*directory*>|Adresář, do kterého se umístí optimalizovaná sestavení. Pokud sestavení již existuje ve složce výstupní adresář, vytvoří se nová kopie a k názvu se připojí číslo indexu; Příklad: *assemblyname*-1.exe. Použijte dvojité uvozovky kolem *adresáře* , pokud Určuje cestu, která obsahuje mezery.|
|`-AssemblyList` \<*assembly1 assembly2 ...*><br /><br /> —nebo—<br /><br /> `-AssemblyListFile` \<*file*>|Seznam sestavení (včetně souborů .exe a .dll) oddělených mezerami, o kterých je třeba shromáždit profilovací informace. Můžete zadat `C:\Dir\*.dll` nebo `*.dll` Vybrat všechna sestavení v určeném nebo aktuálním pracovním adresáři. Další informace naleznete v části Poznámky.<br /><br /> —nebo—<br /><br /> Textový soubor obsahující seznam sestavení, o kterých je třeba shromáždit profilovací informace. Vždy je uvedeno jedno sestavení na řádku. Pokud název sestavení začíná pomlčkou (-), je třeba použít soubor seznamu sestavení nebo sestavení přejmenovat.|
|`-AppID` \<*appId*>|ID aplikace v zadaném balíčku. Použijete-li zástupný znak ( \* ), Mpgo.exe se pokusí vytvořit výčet AppID v balíčku a přejde zpět na \<*package_family_name*> ! Aplikace, pokud se nezdařila Při zadání řetězce, který má předponu vykřičník (!), bude nástroj Mpgo.exe řetězit název řady balíčků s dodaným argumentem.|
|`-Timeout` \<*seconds*>|Doba, po kterou se má spustit aplikace Windows 8. x Store před ukončením aplikace.|

|Volitelný parametr|Description|
|------------------------|-----------------|
|`-64bit`|Upraví sestavení pro 64bitové systémy.  Tento parametr je nutné zadat pro 64bitová sestavení, i když sestavení samo sebe prohlašuje za 64bitové.|
|`-ExeConfig` \<*filename*>|Určuje konfigurační soubor, který scénář využívá k poskytování informací o verzi a zavaděči.|
|`-f`|Vynutí zahrnutí dat profilu do binárního sestavení, i pokud je podepsáno.  Pokud je sestavení podepsáno, je třeba jej znovu podepsat, jinak se načtení a spuštění sestavení nezdaří.|
|`-Reset`|Nastaví výchozí hodnoty prostředí pro ujištění, že přerušená relace profilování nemá žádný vliv na sestavení, a poté se ukončí. Prostředí je nastaveno na výchozí hodnoty standardně před relací a po relaci profilování.|
|`-Timeout` \<*time in seconds*>|Určuje dobu profilování v sekundách. Je třeba použít hodnotu, která je mírně vyšší než pozorované časy spuštění grafického uživatelského rozhraní (GUI) aplikace. Na konci časového limitu jsou zaznamenána data profilu, přestože aplikace nadále běží. Pokud tuto možnost nenastavíte, bude profilování pokračovat až do ukončení aplikace, kdy budou data zaznamenána.|
|`-LeaveNativeImages`|Určuje, že po spuštění scénáře by neměly být odebrány upravené nativní bitové kopie. Tato možnost se používá především u aplikace, která byla určena pro spuštěný scénář. Zabrání opětovnému vytvoření nativních bitových kopií pro následné spuštění nástroje Mpgo.exe. Při zadání této možnosti mohou být po dokončení běhu aplikace ve vyrovnávací paměti přítomny osamocené nativní bitové kopie. V takovém případě spusťte Mpgo.exe se stejným scénářem a seznamem sestavení a použijte `–RemoveNativeImages` parametr k odebrání těchto nativních imagí.|
|`-RemoveNativeImages`|Vyčistí v `–LeaveNativeImages` zadaném běhu. Pokud zadáte `-RemoveNativeImages` , Mpgo.exe ignoruje všechny argumenty s výjimkou `-64bit` a a `–AssemblyList` ukončí se po odebrání všech instrumentované nativní bitové kopie.|

## <a name="remarks"></a>Poznámky
 `–AssemblyList`Na příkazovém řádku můžete použít obojí a víckrát `- AssemblyListFile` .

 Pokud při určování sestavení nezadáte úplný název cesty, nástroj Mpgo.exe hledá v aktuálním adresáři. Při zadání nesprávné cesty nástroj Mpgo.exe zobrazí chybovou zprávu, ale stále generuje data pro jiná sestavení. Při zadání sestavení, které není načteno během trénovacího scénáře, nejsou pro toto sestavení generována žádná trénovací data.

 Jestliže se sestavení ze seznamu nachází v globální mezipaměti sestavení (GAC), nebude aktualizováno pro zahrnutí informací o profilu.  Pro shromáždění informací o profilu je třeba sestavení odebrat z globální mezipaměti sestavení (GAC).

 Použití nástrojů Ngen.exe a Mpgo.exe je doporučeno pouze pro velké spravované aplikace, protože výhoda předkompilovaných nativních bitových kopií je obvykle vidět pouze v případě, že eliminuje významné množství kompilace JIT za běhu. Spouštění Mpgo.exe v aplikacích stylu "Hello World", které nefungují s náročnou sadou, neposkytuje žádné výhody a Mpgo.exe může dokonce neúspěšné shromáždění dat profilu.

> [!NOTE]
> Nástroje Ngen.exe a Mpgo.exe nejsou vhodné pro aplikace ASP.NET a služby Windows Communication Foundation (WCF).  
  
## <a name="to-use-mpgoexe"></a>Použití nástroje Mpgo.exe  
  
1. Použijte počítač, který má nainstalovánu vaši aplikaci a sadu Visual Studio Ultimate 2012.  
  
2. Spusťte nástroj Mpgo.exe jako správce s nezbytnými parametry.  Ukázkové příkazy naleznete v další části.  
  
     Sestavení optimalizovaného zprostředkujícího jazyka (IL) jsou vytvořena ve složce určené `–OutDir` parametrem (v těchto příkladech je to `C:\Optimized` Složka).  
  
3. Nahraďte sestavení IL použitá pro Ngen.exe novými sestaveními IL, která obsahují informace o profilu z adresáře zadaného parametrem `–OutDir` .  
  
4. Instalace aplikace (pomocí bitových kopií poskytnutých nástrojem Mpgo.exe) nainstaluje optimalizované nativní bitové kopie.  
  
## <a name="suggested-workflow"></a>Navrhovaný pracovní postup  
  
1. Vytvořte sadu optimalizovaných sestavení IL pomocí Mpgo.exe s `–Scenario` parametrem.  
  
2. Zaveďte optimalizovaná sestavení jazyka IL do správy zdrojového kódu.  
  
3. V procesu sestavení zavolejte Mpgo.exe s `–Import` parametrem jako krok po sestavení, čímž vygenerujete optimalizované image Il pro předání Ngen.exe.  
  
 Tento proces zajišťuje, že všechna sestavení mají optimalizační data. Při častějším zavádění aktualizovaných optimalizovaných sestavení (kroky 1 a 2) bude výkon během celého vývoje produktu konzistentnější.  
  
## <a name="using-mpgoexe-from-visual-studio"></a>Použití nástroje Mpgo.exe ze sady Visual Studio  
 Můžete spustit Mpgo.exe ze sady Visual Studio (viz článek [Postupy: určení událostí sestavení (C#)](/visualstudio/ide/how-to-specify-build-events-csharp)) s následujícími omezeními:  
  
- Nelze použít cesty v uvozovkách ukončené lomítkem, protože makra sady Visual Studio ve výchozím nastavení také používají koncová lomítka. (Například `–OutDir "C:\Output Folder\"` je neplatný.) Pokud chcete toto omezení obejít, můžete koncové lomítko. (Například `-OutDir "$(OutDir)\"` místo toho použijte.)  
  
- Ve výchozím nastavení není nástroj Mpgo.exe v cestě sestavení sady Visual Studio. Je nutné přidat cestu do sady Visual Studio nebo zadat úplnou cestu v příkazovém řádku nástroje Mpgo.exe. Můžete použít buď parametr, `–Scenario` nebo `–Import` v události po sestavení v aplikaci Visual Studio. Typický proces je však `–Scenario` jednorázově použit z Developer Command Prompt pro Visual Studio a potom použít `–Import` k aktualizaci optimalizovaných sestavení po každém sestavení, například: `"C:\Program Files\Microsoft Visual Studio 11.0\Team Tools\Performance Tools\mpgo.exe" -import "$(OutDir)tmp" -assemblylist "$(TargetPath)" -outdir "$(OutDir)\"` .  
  
<a name="samples"></a>
## <a name="examples"></a>Příklady  
 Následující Mpgo.exe příkaz z Developer Command Prompt pro Visual Studio optimalizuje daňovou aplikaci:  
  
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

- [Ngen.exe (generátor nativních imagí)](ngen-exe-native-image-generator.md)
- [Výzvy příkazového řádku](developer-command-prompt-for-vs.md)
- [Zlepšení výkonu spouštění pro aplikace klasické pracovní plochy](https://devblogs.microsoft.com/dotnet/improving-launch-performance-for-your-desktop-applications/)
- [Přehled vylepšení výkonu v .NET 4,5](https://docs.microsoft.com/archive/msdn-magazine/2012/april/clr-an-overview-of-performance-improvements-in-net-4-5)
