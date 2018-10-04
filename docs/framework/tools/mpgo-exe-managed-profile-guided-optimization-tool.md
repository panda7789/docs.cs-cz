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
ms.openlocfilehash: c4fea49a3200ca58264eb7c1bc1ead0a8ddc5914
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48584195"
---
# <a name="mpgoexe-managed-profile-guided-optimization-tool"></a>Mpgo.exe (Nástroj pro optimalizaci spravovaného kódu na základě profilu)

Profilu nástroj Optimalizace řízený spravovanými (Mpgo.exe) je nástroj příkazového řádku, který se používá k optimalizaci sestavení nativních bitových kopií, které jsou vytvořeny pomocí běžných uživatelských scénářů [Native Image Generator (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md). Tento nástroj umožňuje spustit trénovací scénáře, které generují data profilu. [Native Image Generator (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) tato data používá k optimalizaci jeho generovaných nativních bitových kopií sestavení aplikace. Trénovací scénář je zkušební spuštění očekávaného použití aplikace. Nástroj Mpgo.exe je k dispozici v sadě Visual Studio Ultimate 2012 a vyšší. Od verze Visual Studio 2013, můžete také použít Mpgo.exe k optimalizaci [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace.  
  
Profilováním řízená optimalizace zlepšuje dobu spuštění aplikace, využití paměti (velikost pracovní sady) a propustnost pomocí shromažďování dat z trénovacích scénářů a jejich použitím pro optimalizaci rozložení nativních bitových kopií.  
  
Při výkonových potížích s časem spuštění a velikostí pracovní sady pro sestavení jazyka IL doporučujeme nejdříve použít nástroj Ngen.exe k eliminaci nároků spojených s kompilací JIT a k usnadnění sdílení kódu. V případě potřeby dalšího zlepšení je k optimalizaci aplikace možné použít nástroj Mpgo.exe. Data o výkonu z neoptimalizované nativní bitové kopie sestavení je možné použít jako základ k vyhodnocení zlepšení výkonu. Použití nástroje Mpgo.exe může mít za následek rychlejší úplné spuštění a menší velikost pracovní sady. Nástroj Mpgo.exe přidá informace do sestavení jazyka IL, které nástroj Ngen.exe používá k vytvoření optimalizované nativní bitové kopie sestavení. Další informace naleznete v příspěvku [zlepšení výkonu spouštění pro aplikace klasické pracovní plochy](https://go.microsoft.com/fwlink/p/?LinkId=248943) v blogu .NET.  
  
Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit tento nástroj, použijte příkazový řádek pro vývojáře (nebo příkazový řádek sady Visual Studio v systému Windows 7) s oprávněními správce a napište do něj následující text. Další informace najdete v tématu [příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
Pro aplikace klasické pracovní plochy:  
  
```  
mpgo –Scenario <command> [-Import <directory>] –AssemblyList <assembly1>  <assembly2> ... -OutDir <directory> [options]  
```  
  
Pro [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
mpgo –Scenario <packageName> -AppID <appId> -Timeout <seconds>  
```  
  
#### <a name="parameters"></a>Parametry  
 Žádný argument nástroje Mpgo.exe nerozlišuje velká a malá písmena. Příkazy začínají pomlčkou.  
  
> [!NOTE]
> Můžete použít buď `–Scenario` nebo `–Import` jako požadovaný příkaz, ale ne obojí. Žádný z požadovaných parametrů se použijí, pokud zadáte `–Reset` možnost.

|Povinný parametr|Popis|
|------------------------|-----------------|
|`-Scenario` \<*Příkaz*><br /><br /> —nebo—<br /><br /> `-Scenario` \<*Název balíčku*><br /><br /> -nebo-<br /><br /> `-Import` \<*Adresář*>|Pro aplikace klasické pracovní plochy, použijte `–Scenario` k určení příkazu ke spuštění aplikace chcete optimalizovat, včetně jakýchkoli argumentů příkazového řádku. Použití tří párů uvozovek kolem *příkaz* Pokud Určuje cestu, která obsahuje mezery; například: `mpgo.exe -scenario """C:\My App\myapp.exe""" -assemblylist """C:\My App\myapp.exe""" -outdir "C:\optimized files"`. Nepoužívejte dvojitých uvozovek. nebude-li správně fungovat *příkaz* obsahuje mezery.<br /><br /> -nebo-<br /><br /> Pro [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace, použijte `–Scenario` k určení balíčku, který chcete generovat informace o profilu. Při zadání zobrazovaného názvu balíčku nebo názvu řady balíčků namísto kompletního názvu balíčku nástroj Mpgo.exe vybere balíček, který se shoduje se zadaným názvem, pokud existuje pouze jediná shoda. Pokud zadanému názvu odpovídá více balíčků, nástroj Mpgo.exe vyzve k výběru balíčku.<br /><br /> —nebo—<br /><br /> Použití `-Import` k určení, že optimalizační data z dříve optimalizovaných sestavení by měla sloužit k optimalizaci sestavení v `-AssemblyList`. *adresář* Určuje adresář obsahující dříve optimalizované soubory. Sestavení zadaná v `–AssemblyList` nebo `–AssemblyListFile` jsou nové verze sestavení, která se mají optimalizovat pomocí dat z importovaných souborů. Použití optimalizačních dat ze starších verzí sestavení umožňuje optimalizovat novější verze sestavení bez opětovného spuštění scénáře.  Nicméně, pokud importované a cílové sestavení obsahují výrazně odlišný kód, optimalizační data budou neúčinná. Názvy sestavení zadané v `–AssemblyList` nebo `–AssemblyListFile` musí existovat v adresáři určeném argumentem `–Import` *directory*. Použití tří párů uvozovek kolem *directory* Pokud Určuje cestu, která obsahuje mezery.<br /><br /> Musíte zadat buď `–Scenario` nebo `–Import`, ale nikoliv oba parametry.|
|`-OutDir` \<*Adresář*>|Adresář, do kterého se umístí optimalizovaná sestavení. Pokud sestavení již existuje ve výstupní složce adresáře, se vytvoří nová kopie a jeho názvu; se připojí číslo indexu Příklad: *assemblyname*-1.exe. Použít uvozovky kolem *directory* Pokud Určuje cestu, která obsahuje mezery.|
|`-AssemblyList` \<*assembly1 assembly2...*><br /><br /> —nebo—<br /><br /> `-AssemblyListFile` \<*Soubor*>|Seznam sestavení (včetně souborů .exe a .dll) oddělených mezerami, o kterých je třeba shromáždit profilovací informace. Můžete zadat `C:\Dir\*.dll` nebo `*.dll` vybrat všechna sestavení v zadaném nebo aktuálním pracovním adresáři. Další informace naleznete v části Poznámky.<br /><br /> —nebo—<br /><br /> Textový soubor obsahující seznam sestavení, o kterých je třeba shromáždit profilovací informace. Vždy je uvedeno jedno sestavení na řádku. Pokud název sestavení začíná pomlčkou (-), je třeba použít soubor seznamu sestavení nebo sestavení přejmenovat.|
|`-AppID` \<*ID aplikace*>|ID aplikace v zadaném balíčku. Pokud používáte zástupný znak (\*), Mpgo.exe pokusí vytvořit výčet AppID v balíčku a použije místo toho \< *package_family_name*>! Aplikace, pokud se nezdaří. Při zadání řetězce, který má předponu vykřičník (!), bude nástroj Mpgo.exe řetězit název řady balíčků s dodaným argumentem.|
|`-Timeout` \<*sekundy*>|Množství času, aby [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace se spustí před jejím ukončením.|

|Volitelný parametr|Popis|
|------------------------|-----------------|
|`-64bit`|Upraví sestavení pro 64bitové systémy.  Tento parametr je nutné zadat pro 64bitová sestavení, i když sestavení samo sebe prohlašuje za 64bitové.|
|`-ExeConfig` \<*Název souboru*>|Určuje konfigurační soubor, který scénář využívá k poskytování informací o verzi a zavaděči.|
|`-f`|Vynutí zahrnutí dat profilu do binárního sestavení, i pokud je podepsáno.  Pokud je sestavení podepsáno, je třeba jej znovu podepsat, jinak se načtení a spuštění sestavení nezdaří.|
|`-Reset`|Nastaví výchozí hodnoty prostředí pro ujištění, že přerušená relace profilování nemá žádný vliv na sestavení, a poté se ukončí. Prostředí je nastaveno na výchozí hodnoty standardně před relací a po relaci profilování.|
|`-Timeout` \<*Doba v sekundách*>|Určuje dobu profilování v sekundách. Je třeba použít hodnotu, která je mírně vyšší než pozorované časy spuštění grafického uživatelského rozhraní (GUI) aplikace. Na konci časového limitu jsou zaznamenána data profilu, přestože aplikace nadále běží. Pokud tuto možnost nenastavíte, bude profilování pokračovat až do ukončení aplikace, kdy budou data zaznamenána.|
|`-LeaveNativeImages`|Určuje, že po spuštění scénáře by neměly být odebrány upravené nativní bitové kopie. Tato možnost se používá především u aplikace, která byla určena pro spuštěný scénář. Zabrání opětovnému vytvoření nativních bitových kopií pro následné spuštění nástroje Mpgo.exe. Při zadání této možnosti mohou být po dokončení běhu aplikace ve vyrovnávací paměti přítomny osamocené nativní bitové kopie. V takovém případě spusťte Mpgo.exe s stejným scénářem a seznamem sestavení a použít `–RemoveNativeImages` parametr pro odebrání těchto nativních bitových kopií.|
|`-RemoveNativeImages`|Vyčistí z spuštění kde `–LeaveNativeImages` byl zadán. Pokud zadáte `-RemoveNativeImages`, Mpgo.exe ignoruje všechny argumenty kromě `-64bit` a `–AssemblyList`a skončí po odstranění všech upravených nativních bitových kopií.|

## <a name="remarks"></a>Poznámky
 Je možné použít jak `–AssemblyList` a `- AssemblyListFile` více než jednou v příkazovém řádku.

 Pokud při určování sestavení nezadáte úplný název cesty, nástroj Mpgo.exe hledá v aktuálním adresáři. Při zadání nesprávné cesty nástroj Mpgo.exe zobrazí chybovou zprávu, ale stále generuje data pro jiná sestavení. Při zadání sestavení, které není načteno během trénovacího scénáře, nejsou pro toto sestavení generována žádná trénovací data.

 Jestliže se sestavení ze seznamu nachází v globální mezipaměti sestavení (GAC), nebude aktualizováno pro zahrnutí informací o profilu.  Pro shromáždění informací o profilu je třeba sestavení odebrat z globální mezipaměti sestavení (GAC).

 Použití nástrojů Ngen.exe a Mpgo.exe je doporučeno pouze pro velké spravované aplikace, protože výhoda předkompilovaných nativních bitových kopií je obvykle vidět pouze v případě, že eliminuje významné množství kompilace JIT za běhu. Spuštění Mpgo.exe na aplikacích stylu "Hello World", které nejsou náročné pracovní sady, nepřinese žádné výhody a Mpgo.exe dokonce nemusí shromažďovat data profilu.

> [!NOTE]
> Nástroje Ngen.exe a Mpgo.exe nejsou vhodné pro aplikace ASP.NET a služby Windows Communication Foundation (WCF).  
  
## <a name="to-use-mpgoexe"></a>Použití nástroje Mpgo.exe  
  
1.  Použijte počítač, který má nainstalovánu vaši aplikaci a sadu Visual Studio Ultimate 2012.  
  
2.  Spusťte nástroj Mpgo.exe jako správce s nezbytnými parametry.  Ukázkové příkazy naleznete v další části.  
  
     Sestavení optimalizované (IL intermediate language) se vytvoří ve složce určené parametrem `–OutDir` parametrů (v příkladech je to `C:\Optimized` složky).  
  
3.  Nahraďte sestavení jazyka IL, který jste použili pro Ngen.exe s novými sestaveními jazyka IL, které obsahují informace o profilu z adresáře zadaného parametrem `–OutDir`.  
  
4.  Instalace aplikace (pomocí bitových kopií poskytnutých nástrojem Mpgo.exe) nainstaluje optimalizované nativní bitové kopie.  
  
## <a name="suggested-workflow"></a>Navrhovaný pracovní postup  
  
1.  Vytvořte sadu optimalizovaných sestavení jazyka IL pomocí Mpgo.exe s `–Scenario` parametru.  
  
2.  Zaveďte optimalizovaná sestavení jazyka IL do správy zdrojového kódu.  
  
3.  V procesu sestavení zavolejte Mpgo.exe s `–Import` parametr jako krok po sestavení pro vygenerování optimalizovaných bitových kopií IL předat Ngen.exe.  
  
 Tento proces zajišťuje, že všechna sestavení mají optimalizační data. Při častějším zavádění aktualizovaných optimalizovaných sestavení (kroky 1 a 2) bude výkon během celého vývoje produktu konzistentnější.  
  
## <a name="using-mpgoexe-from-visual-studio"></a>Použití nástroje Mpgo.exe ze sady Visual Studio  
 Mpgo.exe lze spustit ze sady Visual Studio (přečtěte si článek [jak: Specify Build Events (C#)](https://msdn.microsoft.com/library/b4ce1ad9-5215-4b6f-b6a2-798b249aa335)) s následujícími omezeními:  
  
-   Nelze použít cesty v uvozovkách ukončené lomítkem, protože makra sady Visual Studio ve výchozím nastavení také používají koncová lomítka. (Například `–OutDir "C:\Output Folder\"` je neplatný.) Chcete-li toto omezení obejít, je možné koncové lomítko zapsat s řídicími znaky. (Například použít `-OutDir "$(OutDir)\"` místo.)  
  
-   Ve výchozím nastavení není nástroj Mpgo.exe v cestě sestavení sady Visual Studio. Je nutné přidat cestu do sady Visual Studio nebo zadat úplnou cestu v příkazovém řádku nástroje Mpgo.exe. Můžete použít buď `–Scenario` nebo `–Import` parametr v události po sestavení v sadě Visual Studio. Typickým procesem je však použít `–Scenario` jednou z příkazu pro vývojáře Visual Studio výzvu a pak pomocí `–Import` k aktualizaci optimalizovaných sestavení po každém sestavení; například: `"C:\Program Files\Microsoft Visual Studio 11.0\Team Tools\Performance Tools\mpgo.exe" -import "$(OutDir)tmp" -assemblylist "$(TargetPath)" -outdir "$(OutDir)\"`.  
  
<a name="samples"></a>   
## <a name="examples"></a>Příklady  
 Následující příkaz nástroje Mpgo.exe z příkazového řádku pro vývojáře v sadě Visual Studio optimalizuje daňovou aplikaci:  
  
```  
mpgo –scenario "C:\MyApp\MyTax.exe /params par" –AssemblyList Mytax.dll MyTaxUtil2011.dll –OutDir C:\Optimized –TimeOut 15  
```  
  
 Následující příkaz nástroje Mpgo.exe optimalizuje zvukovou aplikaci:  
  
```  
mpgo –scenario "C:\MyApp\wav2wma.exe –input song1.wav –output song1.wma" –AssemblyList transcode.dll –OutDir C:\Optimized –TimeOut 15  
```  
  
 Následující příkaz nástroje Mpgo.exe používá data z dříve optimalizovaných sestavení pro optimalizaci novějších verzí sestavení:  
  
```  
mpgo.exe -import "C:\Optimized" -assemblylist "C:\MyApp\MyTax.dll" "C:\MyApp\MyTaxUtil2011.dll" -outdir C:\ReOptimized  
```  
  
## <a name="see-also"></a>Viz také  
 [Ngen.exe (generátor nativních obrázků)](../../../docs/framework/tools/ngen-exe-native-image-generator.md)  
 [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)  
 [Zlepšení výkonu spouštění pro aplikace klasické pracovní plochy](https://go.microsoft.com/fwlink/p/?LinkId=248943)  
 [Přehled vylepšení výkonu v rozhraní .NET 4.5](https://go.microsoft.com/fwlink/p/?LinkId=249131)
