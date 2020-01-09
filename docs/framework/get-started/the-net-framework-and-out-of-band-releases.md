---
title: Rozhraní .NET Framework a nesvázaná vydání
ms.date: 10/10/2018
ms.assetid: 721f10fa-3189-4124-a00d-56ddabd889b3
ms.openlocfilehash: a2dcd011548df857a1399c5bbdfe6ed33927672e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716406"
---
# <a name="the-net-framework-and-out-of-band-releases"></a>Rozhraní .NET Framework a nesvázaná vydání

Rozhraní .NET Framework se vyvíjí pro různé platformy, jako jsou Windows Phone a aplikace pro Windows Store a tradiční stolní počítače a webové aplikace a maximalizuje opětovnou využitelnost kódu. Kromě regulárních verzí rozhraní .NET Framework vydáváme nové funkce OOB (out of band) z důvodu zlepšení vývoje napříč platformami nebo představení nových funkcí. Toto téma popisuje budoucí směr rozhraní .NET Framework a jeho OOB verzí.

## <a name="advantages-of-oob-releases"></a>Výhody verzí OOB
 Dodávání nových komponent nebo aktualizací komponent OOB umožňuje společnosti Microsoft poskytovat častější aktualizace rozhraní .NET Framework. Kromě toho můžeme shromažďovat názory zákazníků a rychleji na ně reagovat.

 Použijete-li ve své aplikaci funkci OOB, nemusí uživatelé instalovat nejnovější verzi rozhraní .NET Framework pro spuštění aplikace, protože sestavení OOB se nasazují s vaším balíčkem aplikací.

## <a name="how-oob-packages-are-distributed"></a>Distribuce balíčků OOB
Verze OOB pro základní komponenty modulu CLR (Common Language Runtime) jsou dodávány prostřednictvím [NuGet](https://www.nuget.org/), což je správce balíčků pro .NET. Technologie NuGet umožňuje procházet a přidávat knihovny do projektů rozhraní .NET Framework z Průzkumníku řešení v sadě Visual Studio. Správce balíčků NuGet je součástí všech edicí sady Visual Studio, počínaje verzí Visual Studio 2012. Chcete-li zjistit, zda je nainstalována sada NuGet, vyhledejte v nabídce **nástroje** sady Visual Studio **Správce balíčků NuGet** . Pokud není nainstalován:

1. Na řádku nabídek sady Visual Studio vyberte **nástroje**, **rozšíření a aktualizace** (v aplikaci Visual Studio 2010 vyberte **Správce rozšíření**).

     Otevře se dialogové okno **rozšíření a aktualizace** .

2. Zvolte **online**, **Správce balíčků NuGet**a pak zvolte **Stáhnout**.

3. Po dokončení stahování restartujte aplikaci Visual Studio.

 Podrobné pokyny k instalaci najdete v tématu [instalace nugetu](/nuget/install-nuget-client-tools) na webu NuGet docs. Další informace o NuGet najdete v [dokumentaci k NuGet](/nuget).

## <a name="using-a-nuget-oob-package"></a>Použití balíčku NuGet OOB
 Po instalaci balíčku NuGet můžete procházet a přidávat odkazy na balíčky NuGet pomocí Průzkumníka řešení v sadě Visual Studio:

1. Otevřete místní nabídku projektu v aplikaci Visual Studio a pak zvolte možnost **Spravovat balíčky NuGet**. (Tato možnost je k dispozici také z nabídky **projekt** .)

2. V levém podokně vyberte možnost **online**.

3. Pokud chcete použít předprodejní balíčky, v rozevíracím seznamu v prostředním podokně vyberte možnost **Zahrnout předprodejní verze** místo **pouze stabilní**.

4. V pravém podokně pomocí **vyhledávacího** pole vyhledejte balíček, který chcete použít. Některé balíčky společnosti Microsoft jsou označeny logem rozhraní Microsoft .NET Framework a všechny identifikují společnost Microsoft jako vydavatele.

 ![Snímek obrazovky, který zobrazuje správce balíčků NuGet.](./media/the-net-framework-and-out-of-band-releases/nuget-package-manager-dialog.png)

 Jak bylo zmíněno dříve, pokud nasadíte aplikaci, která používá balíček OOB, sestavení OOB bude dodáváno spolu s balíčkem aplikace.

## <a name="types-of-oob-releases"></a>Typy verzí OOB
 Balíček OOB obvykle má jednu nebo více předprodejních verzí a stabilní verzi. Licence, která doprovází předběžnou verzi, obvykle neumožňuje opětovnou distribuci, ale umožňuje vyzkoušet balíček a poskytnout zpětnou vazbu. Zpětná vazba je součástí všech aktualizací balíčku. Konečná vydaná verze je distribuována jako stabilní balíček NuGet a obsahuje licenci, která umožňuje tento balíček NuGet distribuovat s vaší aplikací. Microsoft podporuje stabilní balíčky. Společnost Microsoft poskytuje podporu technologie IntelliSense i další typy dokumentace, jako jsou příspěvky na blogu a odpovědi na fóru pro všechny balíčky. Kromě toho může být zdrojový kód k dispozici s některými, ale ne všemi balíčky. Pro oznámení týkající se nových a aktualizovaných balíčků se můžete přihlásit k odběru [blogu .NET Framework](https://devblogs.microsoft.com/dotnet/).

 Pokud chcete najít jak předběžné verze, tak stabilní balíčky, vyberte **Zahrnout předprodejní verze** ve Správci balíčků NuGet.

## <a name="see-also"></a>Viz také:

- [Začínáme](index.md)
