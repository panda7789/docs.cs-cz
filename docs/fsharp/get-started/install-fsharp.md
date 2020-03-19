---
title: Instalace F#
description: Naučte se, jak nainstalovat F# různými způsoby.
ms.date: 12/20/2019
ms.openlocfilehash: 302e04f7cf3271516dff88d9d5f18f620b6ede80
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400244"
---
# <a name="install-f"></a>Instalace F\#

Můžete nainstalovat F# několika způsoby, v závislosti na vašem prostředí.

## <a name="install-f-with-visual-studio"></a>Instalace jazyka F# pomocí sady Visual Studio

1. Pokud stahujete [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) poprvé, nejprve nainstaluje Instalační program sady Visual Studio. Nainstalujte příslušnou edici sady Visual Studio od instalačního programu.

   Pokud už máte nainstalovaný Visual Studio, zvolte **Změnit** vedle edice, do které chcete přidat F#.

2. Na stránce Úlohy vyberte **úlohu vývoje ASP.NET a webu,** která zahrnuje podporu F# a .NET Core pro ASP.NET základní projekty.

3. Zvolte **Změnit** v pravém dolním rohu a nainstalujte vše, co jste vybrali.

   Potom můžete spustit Visual Studio s F# výběrem **Spustit** v Instalační službě sady Visual Studio.

## <a name="install-f-with-visual-studio-code"></a>Instalace jazyka F# s kódem sady Visual Studio

1. Ujistěte se, že máte [na](https://git-scm.com/download) vaší cestě nainstalovaný git. Zda je správně nainstalována, můžete `git --version` ji ověřit zadáním příkazového řádku a stisknutím **klávesy Enter**.

2. Nainstalujte [sadu](https://code.visualstudio.com) [.NET Core SDK](https://dotnet.microsoft.com/download) a kód sady Visual Studio .

3. Vyberte ikonu Rozšíření a vyhledejte "Ionide":

   Jediný modul plug-in potřebný pro podporu Jazyka F# v kódu sady Visual Studio je [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp). Můžete však také nainstalovat [Ionide-FAKE,](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) abyste získali [podporu FAKE](https://fake.build/) a [Ionide-Paket,](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) abyste získali podporu [Paketu.](https://fsprojects.github.io/Paket/) FAKE a Paket jsou další f# komunitní nástroje pro vytváření projektů a správu závislostí, resp.

## <a name="install-f-with-visual-studio-for-mac"></a>Instalace Jazyka F# pomocí Visual Studia pro Mac

F# je ve výchozím nastavení nainstalován v [sadě Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)bez ohledu na to, jakou konfiguraci zvolíte.

Po dokončení instalace zvolte **Spustit Visual Studio**. Visual Studio můžete otevřít taky ve Finderu v macOS.

## <a name="install-f-on-a-build-server"></a>Instalace jazyka F# na server sestavení

Pokud používáte rozhraní .NET Core nebo rozhraní .NET Framework prostřednictvím sady .NET SDK, stačí nainstalovat sadu .NET SDK na server sestavení. Má vše, co potřebujete.

Pokud používáte rozhraní .NET Framework a **nepoužíváte** sdk .NET SDK, budete muset nainstalovat [skladovou položku nástroje sady Visual Studio Build Tools](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) do systému Windows Server. V instalačním programu vyberte **nástroje pro sestavení instalačního programu .NET**a potom vyberte komponentu **kompilátoru F#** na pravé straně nabídky instalačního programu.
