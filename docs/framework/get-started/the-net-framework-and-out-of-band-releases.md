---
title: .NET Framework a vzdálené verze
description: Přečtěte si o .NET a neintegrovaných verzích. Nové funkce jsou vydány mimo pásmo (OOB), které zlepšují vývoj pro různé platformy nebo zavádějí nové funkce.
ms.date: 10/10/2018
ms.assetid: 721f10fa-3189-4124-a00d-56ddabd889b3
ms.openlocfilehash: 9653696f46279e0c23418f92030d64839cc20518
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618763"
---
# <a name="net-framework-and-out-of-band-releases"></a>Rozhraní .NET Framework a mimořádná vydání

.NET Framework se vyvinula tak, aby vyhovovala různým platformám, jako jsou aplikace UWP a tradiční desktopové a webové aplikace, a umožňuje maximalizovat opětovné použití kódu. Kromě pravidelných .NET Framework verzí jsou nové funkce vydány mimo pásmo (OOB), aby se zlepšil vývoj pro různé platformy, nebo aby se zavedly nové funkce.

## <a name="advantages-of-oob-releases"></a>Výhody verzí OOB

Doručení nových komponent nebo aktualizací do komponent mimo IP síť umožňuje společnosti Microsoft poskytovat častější aktualizace .NET Framework. Kromě toho můžeme shromažďovat názory zákazníků a rychleji na ně reagovat.

Použijete-li ve své aplikaci funkci OOB, nemusí uživatelé instalovat nejnovější verzi .NET Framework ke spuštění aplikace, protože sestavení OOB se nasazují s balíčkem aplikace.

## <a name="how-oob-packages-are-distributed"></a>Distribuce balíčků OOB

Verze OOB pro základní komponenty modulu CLR (Common Language Runtime) jsou dodávané prostřednictvím [NuGet](https://www.nuget.org/), což je správce balíčků pro .NET. NuGet umožňuje snadno procházet a přidávat knihovny do projektů .NET Framework v rámci sady Visual Studio. Správce balíčků NuGet je součástí všech edic sady Visual Studio počínaje sadou Visual Studio 2012. Vyhledejte **Správce balíčků NuGet** v nabídce **nástroje** v aplikaci Visual Studio. Pokud není nainstalovaný, postupujte podle pokynů k [instalaci NuGet](/nuget/install-nuget-client-tools). Další informace o NuGet najdete v dokumentaci k [NuGet](/nuget).

## <a name="use-a-nuget-oob-package"></a>Použití balíčku NuGet OOB

Pokud je nainstalován Správce balíčků NuGet, můžete procházet a přidávat odkazy na balíčky NuGet pomocí Průzkumník řešení v aplikaci Visual Studio:

1. Otevřete místní nabídku projektu v aplikaci Visual Studio a pak zvolte možnost **Spravovat balíčky NuGet**. (Tato možnost je k dispozici také z nabídky **projekt** .)

2. V levém podokně vyberte možnost **online**.

3. Pokud chcete použít předprodejní balíčky, v rozevíracím seznamu v prostředním podokně vyberte možnost **Zahrnout předprodejní verze** místo **pouze stabilní**.

4. V pravém podokně pomocí **vyhledávacího** pole vyhledejte balíček, který chcete použít. Některé balíčky společnosti Microsoft jsou označeny logem rozhraní Microsoft .NET Framework a všechny identifikují společnost Microsoft jako vydavatele.

![Správce balíčků NuGet.](./media/the-net-framework-and-out-of-band-releases/nuget-package-manager-dialog.png)

Jak bylo zmíněno dříve, pokud nasadíte aplikaci, která používá balíček OOB, sestavení OOB bude dodáváno spolu s balíčkem aplikace.

## <a name="types-of-oob-releases"></a>Typy verzí OOB

Balíček OOB obvykle má jednu nebo více předprodejních verzí a stabilní verzi. Licence, která doprovází předběžnou verzi, obvykle neumožňuje opětovnou distribuci, ale umožňuje vyzkoušet balíček a poskytnout zpětnou vazbu. Zpětná vazba je součástí všech aktualizací balíčku. Konečná vydaná verze je distribuována jako stabilní balíček NuGet a obsahuje licenci, která umožňuje tento balíček NuGet distribuovat s vaší aplikací. Microsoft podporuje stabilní balíčky. Společnost Microsoft poskytuje podporu technologie IntelliSense i další typy dokumentace, jako jsou příspěvky na blogu a odpovědi na fóru pro všechny balíčky. Kromě toho může být zdrojový kód k dispozici s některými, ale ne všemi balíčky. Pro oznámení týkající se nových a aktualizovaných balíčků se můžete přihlásit k odběru [blogu .NET Framework](https://devblogs.microsoft.com/dotnet/).

Pokud chcete najít jak předběžné verze, tak stabilní balíčky, vyberte **Zahrnout předprodejní verze** ve Správci balíčků NuGet.

## <a name="see-also"></a>Viz také:

- [Začínáme](index.md)
