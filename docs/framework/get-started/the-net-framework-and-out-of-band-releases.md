---
title: Rozhraní .NET Framework a nesvázaná vydání
ms.date: 03/30/2017
ms.assetid: 721f10fa-3189-4124-a00d-56ddabd889b3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6c0ea6590a53748c9ed85a6d13f67b260ce23af5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="the-net-framework-and-out-of-band-releases"></a>Rozhraní .NET Framework a nesvázaná vydání
Rozhraní .NET Framework se vyvíjí pro různé platformy, jako jsou Windows Phone a aplikace pro Windows Store a tradiční stolní počítače a webové aplikace a maximalizuje opětovnou využitelnost kódu. Kromě regulárních verzí rozhraní .NET Framework vydáváme nové funkce OOB (out of band) z důvodu zlepšení vývoje napříč platformami nebo představení nových funkcí. Toto téma popisuje budoucí směr rozhraní .NET Framework a jeho OOB verzí.  
  
## <a name="advantages-of-oob-releases"></a>Výhody verzí OOB  
 Dodávání nových komponent nebo aktualizací komponent OOB umožňuje společnosti Microsoft poskytovat častější aktualizace rozhraní .NET Framework. Kromě toho můžeme shromažďovat názory zákazníků a rychleji na ně reagovat.  
  
 Použijete-li ve své aplikaci funkci OOB, nemusí uživatelé instalovat nejnovější verzi rozhraní .NET Framework pro spuštění aplikace, protože sestavení OOB se nasazují s vaším balíčkem aplikací.  
  
## <a name="how-oob-packages-are-distributed"></a>Distribuce balíčků OOB  
Vydání OOB pro základní common language runtime (CLR) součásti se doručují prostřednictvím [NuGet](https://www.nuget.org/), což je Správce balíčků pro rozhraní .NET. Technologie NuGet umožňuje procházet a přidávat knihovny do projektů rozhraní .NET Framework z Průzkumníku řešení v sadě Visual Studio. Správce balíčků NuGet je součástí všech edicí sady Visual Studio, počínaje verzí Visual Studio 2012. Chcete-li zjistit, zda je nainstalován NuGet, vyhledejte **Správce balíčků knihoven** v sadě Visual Studio **nástroje** nabídky. Pokud není nainstalován:  
  
1.  Na panelu nabídek Visual Studio zvolte **nástroje**, **rozšíření a aktualizace** (v sadě Visual Studio 2010, zvolte **Správce rozšíření**).  
  
     **Rozšíření a aktualizace** otevře se dialogové okno.  
  
2.  Zvolte **Online**, **Správce balíčků NuGet**a potom zvolte **Stáhnout**.  
  
3.  Po dokončení stahování restartujte aplikaci Visual Studio.  
  
 Podrobné pokyny k instalaci naleznete v části [instalace NuGet](http://docs.nuget.org/docs/start-here/installing-nuget) na webu NuGet dokumentace. Další informace o systému NuGet najdete v tématu [NuGet dokumentaci](http://docs.nuget.org/).  
  
## <a name="using-a-nuget-oob-package"></a>Použití balíčku NuGet OOB  
 Po instalaci balíčku NuGet můžete procházet a přidávat odkazy na balíčky NuGet pomocí Průzkumníka řešení v sadě Visual Studio:  
  
1.  Otevřete místní nabídky pro váš projekt v sadě Visual Studio a zvolte **spravovat balíčky NuGet**. (Tato možnost je dostupná také prostřednictvím **projektu** nabídky.)  
  
2.  V levém podokně vyberte **Online**.  
  
3.  Pokud chcete použít předběžné verze balíčků, v rozevíracím seznamu v prostředním podokně, vyberte **zahrnout předběžné verze** místo **pouze stabilní**.  
  
4.  V pravém podokně, použijte **vyhledávání** pole a vyhledejte balíček, který chcete použít. Některé balíčky společnosti Microsoft jsou označeny logem rozhraní Microsoft .NET Framework a všechny identifikují společnost Microsoft jako vydavatele.  
  
 ![Správce balíčků NuGet](../../../docs/framework/get-started/media/clrnugetdialog.png "clrNugetDialog")  
  
 Jak bylo zmíněno dříve, pokud nasadíte aplikaci, která používá balíček OOB, sestavení OOB bude dodáváno spolu s balíčkem aplikace.  
  
## <a name="types-of-oob-releases"></a>Typy verzí OOB  
 Balíček OOB obvykle má jednu nebo více předprodejních verzí a stabilní verzi. Licence, které doprovází předběžné verze obvykle neumožňuje opětovné distribuci, ale můžete vyzkoušet na balíček a poskytnout zpětnou vazbu. Zpětná vazba je součástí všech aktualizací balíčku. Konečná vydaná verze je distribuována jako stabilní balíček NuGet a obsahuje licenci, která umožňuje tento balíček NuGet distribuovat s vaší aplikací. Microsoft podporuje stabilní balíčky. Společnost Microsoft poskytuje podporu technologie IntelliSense, jakož i jiné typy dokumentace například příspěvcích na blogu a fórum odpovědi pro všechny balíčky. Zdrojový kód kromě toho může být k dispozici s některé, ale ne všechny balíčky. Pro oznámení o nových a aktualizovaných balíčků, můžete odebírat [na blogu .NET Framework](http://blogs.msdn.com/b/dotnet/).  
  
 Chcete-li najít předprodejní a stabilní balíčky, zvolte **zahrnout předprodejní** Správce balíčků NuGet.  
  
 Pokud chcete být informováni o stabilní balíčku verze, přihlášení k odběru [rozhraní .NET Framework kanálu](https://nuget.org/api/v2/curated-feeds/dotnetframework/Packages/).  
  
## <a name="see-also"></a>Viz také  
 [Začínáme](../../../docs/framework/get-started/index.md)
