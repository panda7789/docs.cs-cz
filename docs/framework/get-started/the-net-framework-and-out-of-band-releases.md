---
title: Rozhraní .NET Framework a nesvázaná vydání
ms.date: 10/10/2018
ms.assetid: 721f10fa-3189-4124-a00d-56ddabd889b3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d968283bb2a39e2a366adc8713fa64fa1c87cd60
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50193978"
---
# <a name="the-net-framework-and-out-of-band-releases"></a>Rozhraní .NET Framework a nesvázaná vydání

Rozhraní .NET Framework se vyvíjí pro různé platformy, jako jsou Windows Phone a aplikace pro Windows Store a tradiční stolní počítače a webové aplikace a maximalizuje opětovnou využitelnost kódu. Kromě regulárních verzí rozhraní .NET Framework vydáváme nové funkce OOB (out of band) z důvodu zlepšení vývoje napříč platformami nebo představení nových funkcí. Toto téma popisuje budoucí směr rozhraní .NET Framework a jeho OOB verzí.

## <a name="advantages-of-oob-releases"></a>Výhody verzí OOB
 Dodávání nových komponent nebo aktualizací komponent OOB umožňuje společnosti Microsoft poskytovat častější aktualizace rozhraní .NET Framework. Kromě toho můžeme shromažďovat názory zákazníků a rychleji na ně reagovat.

 Použijete-li ve své aplikaci funkci OOB, nemusí uživatelé instalovat nejnovější verzi rozhraní .NET Framework pro spuštění aplikace, protože sestavení OOB se nasazují s vaším balíčkem aplikací.

## <a name="how-oob-packages-are-distributed"></a>Distribuce balíčků OOB
Verze OOB pro součásti jádra common language runtime (CLR) jsou poskytovány pomocí [NuGet](https://www.nuget.org/), což je Správce balíčků pro .NET. Technologie NuGet umožňuje procházet a přidávat knihovny do projektů rozhraní .NET Framework z Průzkumníku řešení v sadě Visual Studio. Správce balíčků NuGet je součástí všech edicí sady Visual Studio, počínaje verzí Visual Studio 2012. Chcete-li zobrazit, zda je nainstalována služba NuGet, vyhledejte **Správce balíčků NuGet** v sadě Visual Studio **nástroje** nabídky. Pokud není nainstalován:

1.  Na řádku nabídek sady Visual Studio, zvolte **nástroje**, **rozšíření a aktualizace** (v sadě Visual Studio 2010 zvolte **Správce rozšíření**).

     **Rozšíření a aktualizace** zobrazí se dialogové okno.

2.  Zvolte **Online**, **Správce balíčků NuGet**a klikněte na tlačítko **Stáhnout**.

3.  Po dokončení stahování restartujte aplikaci Visual Studio.

 Podrobné pokyny k instalaci naleznete v tématu [instalace balíčků NuGet](/nuget/install-nuget-client-tools) na webu NuGet Docs. Další informace o systému NuGet najdete v tématu [dokumentace pro NuGet](/nuget).

## <a name="using-a-nuget-oob-package"></a>Použití balíčku NuGet OOB
 Po instalaci balíčku NuGet můžete procházet a přidávat odkazy na balíčky NuGet pomocí Průzkumníka řešení v sadě Visual Studio:

1.  Otevřete místní nabídku pro váš projekt v sadě Visual Studio a klikněte na tlačítko **spravovat balíčky NuGet**. (Tato možnost je k dispozici také **projektu** nabídky.)

2.  V levém podokně vyberte **Online**.

3.  Pokud chcete použít předprodejní balíčky, v rozevíracím seznamu v prostředním podokně, vyberte **zahrnout předběžné verze** místo **pouze stabilní verze**.

4.  V pravém podokně můžete použít **hledání** políčka k vyhledání balíčku, které chcete použít. Některé balíčky společnosti Microsoft jsou označeny logem rozhraní Microsoft .NET Framework a všechny identifikují společnost Microsoft jako vydavatele.

 ![Správce balíčků NuGet](../../../docs/framework/get-started/media/clrnugetdialog.png "clrNugetDialog")

 Jak bylo zmíněno dříve, pokud nasadíte aplikaci, která používá balíček OOB, sestavení OOB bude dodáváno spolu s balíčkem aplikace.

## <a name="types-of-oob-releases"></a>Typy verzí OOB
 Balíček OOB obvykle má jednu nebo více předprodejních verzí a stabilní verzi. Licence, která doprovází zkušební verzi, obvykle neumožňuje přerozdělování, ale umožňuje vyzkoušet balíček a poskytnout zpětnou vazbu. Zpětná vazba je součástí všech aktualizací balíčku. Konečná vydaná verze je distribuována jako stabilní balíček NuGet a obsahuje licenci, která umožňuje tento balíček NuGet distribuovat s vaší aplikací. Stabilní balíčky jsou podporovány společností Microsoft. Společnost Microsoft poskytuje podporu technologie IntelliSense, jakož i jiné druhy dokumentace, jako jsou příspěvky blogu a odpovědi na fóru pro všechny balíčky. Navíc zdrojový kód může být k dispozici některé, ale ne všechny balíčky. Pro oznámení týkající se nové a aktualizované balíčky, můžete odebírat [blogu .NET Framework](https://blogs.msdn.com/b/dotnet/).

 Chcete-li vyhledat balíčky předprodejní a stabilní, zvolte **zahrnout předběžné verze** ve správci balíčků NuGet.

 Pokud chcete dostat stabilní balíček verzí, přihlášení k odběru [rozhraní .NET Framework kanálu](https://nuget.org/api/v2/curated-feeds/dotnetframework/Packages/).

## <a name="see-also"></a>Viz také

- [Začínáme](../../../docs/framework/get-started/index.md)