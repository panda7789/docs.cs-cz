---
title: Instalace F#
description: Přečtěte si, F# jak nainstalovat na základě vašeho prostředí.
ms.date: 09/05/2019
ms.openlocfilehash: 592a4c7763266cee68809fca84f9604d7e96b8f1
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204877"
---
# <a name="install-f"></a>Nainstalovat F\#

V závislosti na F# vašem prostředí můžete instalovat různými způsoby.

## <a name="install-f-with-visual-studio"></a>Instalace F# se sadou Visual Studio

Pokud stahujete [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) poprvé, nainstaluje se nejprve instalační program sady Visual Studio. Z instalačního programu nainstalujte příslušnou SKU sady Visual Studio. Pokud již máte nainstalováno, klikněte na tlačítko **Upravit**.

Zobrazí se další seznam úloh. Vyberte **ASP.NET a vývoj pro web** , které F# budou instalovat podporu a podporu .net Core pro projekty ASP.NET Core.

Potom v pravé dolní části klikněte na **Upravit** .  Tím se nainstaluje všechno, co jste vybrali. Pak můžete otevřít Visual Studio 2017 s F# podporou jazyka kliknutím na **Spustit**.

## <a name="install-f-with-visual-studio-code"></a>Instalace F# pomocí Visual Studio Code

Nejdřív ověřte, že máte [nainstalovaný Git](https://git-scm.com/download) a máte k dispozici na vaší cestě. Můžete ověřit, zda je správně nainstalován, zadáním `git --version` na příkazovém řádku a stisknutím klávesy **ENTER**.

Dále nainstalujte [.NET Core SDK](https://dotnet.microsoft.com/download).

Pak budete potřebovat [Visual Studio Code](https://code.visualstudio.com) nainstalovat.

Potom klikněte na ikonu rozšíření a vyhledejte "Ionide":

Jediným modulem plug- F# in vyžadovaným pro podporu v Visual Studio Code je [Ionide-FSharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp). Můžete ale také nainstalovat [Ionide-falešné](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) , abyste získali [falešnou](https://fake.build/) podporu a [Ionide-paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) pro získání podpory [paket](https://fsprojects.github.io/Paket/) . NAPODOBENINy a paket jsou F# další komunitní nástroje pro vytváření projektů a správu závislostí v uvedeném pořadí.

## <a name="install-f-with-visual-studio-for-mac"></a>Instalace F# pomocí Visual Studio pro Mac

F#je ve výchozím nastavení nainstalován v [Visual Studio pro Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)bez ohledu na to, jakou konfiguraci zvolíte.

Po dokončení instalace klikněte na spustit Visual Studio. Můžete ho také spustit pomocí hledání na macOS.

## <a name="install-f-on-a-build-server"></a>Instalace F# na server sestavení

Pokud používáte .NET Core nebo .NET Framework přes sadu .NET SDK, stačí pouze nainstalovat sadu .NET SDK na server sestavení. Obsahuje všechno, co potřebujete.

Pokud **používáte .NET Framework a nepoužíváte** sadu .NET SDK, bude nutné nainstalovat [Visual Studio Build Tools SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) do Windows serveru. V instalačním programu vyberte možnost **Nástroje pro vytváření desktopových prostředí .NET** a pak na pravé straně nabídky instalačního programu vyberte komponentu  **F# kompilátoru** .
