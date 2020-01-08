---
title: Instalace F#
description: Naučte se instalovat F# různými různými způsoby.
ms.date: 12/20/2019
ms.openlocfilehash: 302e04f7cf3271516dff88d9d5f18f620b6ede80
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346568"
---
# <a name="install-f"></a>Nainstalovat F\#

V závislosti na F# vašem prostředí můžete instalovat různými způsoby.

## <a name="install-f-with-visual-studio"></a>Instalace F# se sadou Visual Studio

1. Pokud stahujete [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) poprvé, nejprve se nainstaluje instalační program pro Visual Studio. Z instalačního programu nainstalujte odpovídající edici sady Visual Studio.

   Pokud již máte nainstalováno Visual Studio, klikněte na tlačítko **Upravit** vedle edice, kterou chcete přidat F# do nástroje.

2. Na stránce úlohy vyberte úlohu **vývoje ASP.NET a webu** , která zahrnuje F# a podporu .NET Core pro ASP.NET Core projekty.

3. V pravém dolním rohu vyberte **Upravit** a nainstalujte všechno, co jste vybrali.

   Pak můžete otevřít Visual Studio s F# výběrem možnosti **Spustit** v instalační program pro Visual Studio.

## <a name="install-f-with-visual-studio-code"></a>Instalace F# pomocí Visual Studio Code

1. Ujistěte se, že máte nainstalovaný [Git](https://git-scm.com/download) a máte k dispozici na vaší cestě. Můžete ověřit, zda je správně nainstalován, zadáním `git --version` na příkazovém řádku a stisknutím klávesy **ENTER**.

2. Nainstalujte [.NET Core SDK](https://dotnet.microsoft.com/download) a [Visual Studio Code](https://code.visualstudio.com).

3. Vyberte ikonu rozšíření a vyhledejte "Ionide":

   Jediným modulem plug- F# in vyžadovaným pro podporu v Visual Studio Code je [Ionide-FSharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp). Můžete ale také nainstalovat [Ionide-falešné](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) , abyste získali [falešnou](https://fake.build/) podporu a [Ionide-paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) pro získání podpory [paket](https://fsprojects.github.io/Paket/) . NAPODOBENINy a paket jsou F# další komunitní nástroje pro vytváření projektů a správu závislostí v uvedeném pořadí.

## <a name="install-f-with-visual-studio-for-mac"></a>Instalace F# pomocí Visual Studio pro Mac

F#je ve výchozím nastavení nainstalován v [Visual Studio pro Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)bez ohledu na to, jakou konfiguraci zvolíte.

Po dokončení instalace vyberte **Spustit Visual Studio**. Můžete také otevřít Visual Studio prostřednictvím hledání na macOS.

## <a name="install-f-on-a-build-server"></a>Instalace F# na server sestavení

Pokud používáte .NET Core nebo .NET Framework přes sadu .NET SDK, stačí pouze nainstalovat sadu .NET SDK na server sestavení. Obsahuje všechno, co potřebujete.

Pokud používáte .NET Framework a **nepoužíváte** sadu .NET SDK, bude nutné nainstalovat [Visual Studio Build Tools SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) do Windows serveru. V instalačním programu vyberte možnost **Nástroje pro vytváření desktopových prostředí .NET**a pak na pravé straně nabídky instalačního programu vyberte komponentu  **F# kompilátoru** .
