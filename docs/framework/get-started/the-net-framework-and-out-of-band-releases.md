---
title: Rozhraní .NET Framework a nepásmová vydání
ms.date: 10/10/2018
ms.assetid: 721f10fa-3189-4124-a00d-56ddabd889b3
ms.openlocfilehash: 058bc1a5180060d3c3c6ba4ead1f074a14336b53
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181567"
---
# <a name="net-framework-and-out-of-band-releases"></a>Rozhraní .NET Framework a nepásmová vydání

Rozhraní .NET Framework se vyvinulo tak, aby vyhovovalo různým platformám, jako jsou aplikace UPW a tradiční desktopové a webové aplikace, a maximalizovalo opakované použití kódu. Kromě běžných verzí rozhraní .NET Framework jsou nové funkce vydávány mimo pásmo (OOB) pro zlepšení vývoje napříč platformami nebo zavedení nových funkcí.

## <a name="advantages-of-oob-releases"></a>Výhody verzí OOB

Odesílání nových součástí nebo aktualizace součástí mimo pásmo umožňuje společnosti Microsoft poskytovat častější aktualizace rozhraní .NET Framework. Kromě toho můžeme shromažďovat názory zákazníků a rychleji na ně reagovat.

Když používáte funkci OOB ve vaší aplikaci, vaši uživatelé nemusí instalovat nejnovější verzi rozhraní .NET Framework ke spuštění aplikace, protože sestavení OOB nasadit s balíčkem aplikace.

## <a name="how-oob-packages-are-distributed"></a>Distribuce balíčků OOB

Verze OOB pro základní komponenty CLR (COMMON Language Runtime) jsou dodávány prostřednictvím [NuGet](https://www.nuget.org/), což je správce balíčků pro rozhraní .NET. NuGet umožňuje procházet a přidávat knihovny do vašich projektů rozhraní .NET Framework snadno z visual studia. NuGet Package Manager je součástí všech edicí sady Visual Studio počínaje Visual Studio 2012. Vyhledejte **Správce balíčků NuGet** v nabídce **Nástroje** v sadě Visual Studio. Pokud není nainstalován, postupujte podle pokynů na [instalaci NuGet](/nuget/install-nuget-client-tools). Další informace o NuGet, naleznete [v části Dokumenty NuGet](/nuget).

## <a name="use-a-nuget-oob-package"></a>Použití balíčku NuGet OOB

Pokud je nainstalován Správce balíčků NuGet, můžete procházet a přidávat odkazy na balíčky NuGet pomocí Průzkumníka řešení v sadě Visual Studio:

1. Otevřete místní nabídku projektu v sadě Visual Studio a pak zvolte **Spravovat balíčky NuGet**. (Tato možnost je k dispozici také v nabídce **Projekt.)**

2. V levém podokně zvolte **Online**.

3. Pokud chcete použít předběžné balíčky, v rozevíracím seznamu v prostředním podokně zvolte **Zahrnout předběžnou verzi** místo **Stable Only**.

4. V pravém podokně **Search** vyhledejte balíček, který chcete použít, pomocí vyhledávacího pole. Některé balíčky společnosti Microsoft jsou označeny logem rozhraní Microsoft .NET Framework a všechny identifikují společnost Microsoft jako vydavatele.

![Správce balíčků Nuget.](./media/the-net-framework-and-out-of-band-releases/nuget-package-manager-dialog.png)

Jak bylo zmíněno dříve, pokud nasadíte aplikaci, která používá balíček OOB, sestavení OOB bude dodáváno spolu s balíčkem aplikace.

## <a name="types-of-oob-releases"></a>Typy verzí OOB

Balíček OOB obvykle má jednu nebo více předprodejních verzí a stabilní verzi. Licence, která doprovází předběžnou verzi, obvykle neumožňuje redistribuci, ale umožňuje vyzkoušet balíček a poskytnout zpětnou vazbu. Zpětná vazba je součástí všech aktualizací balíčku. Konečná vydaná verze je distribuována jako stabilní balíček NuGet a obsahuje licenci, která umožňuje tento balíček NuGet distribuovat s vaší aplikací. Stabilní balíčky jsou podporovány společností Microsoft. Společnost Microsoft poskytuje podporu Technologie IntelliSense a další typy dokumentace, jako jsou příspěvky na blogu a odpovědi na fórum pro všechny balíčky. Kromě toho zdrojový kód může být k dispozici s některými, ale ne všechny balíčky. V případě oznámení týkajících se nových a aktualizovaných balíčků se můžete přihlásit k odběru [blogu .NET Framework .](https://devblogs.microsoft.com/dotnet/)

Chcete-li najít předběžné verze a stabilní balíčky, zvolte **Zahrnout předběžné vydání** ve Správci balíčků NuGet.

## <a name="see-also"></a>Viz také

- [Začínáme](index.md)
