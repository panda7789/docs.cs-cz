---
title: Nástroje pro vývojáře na platformě Azure .NET
description: Získejte nástroje pro zahájení používání knihoven Azure .NET z prostředí Windows, Linux a Mac.
ms.date: 06/19/2020
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: fa645b152f15550b25a3542ba0cdbb43799536b9
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174907"
---
# <a name="azure-tools-for-developing-with-net"></a>Nástroje Azure pro vývoj s využitím .NET

## <a name="sdk-downloads"></a>Soubory sady SDK ke stažení

Knihovny Azure pro .NET jsou implementované jako [balíčky NuGet](https://www.nuget.org/packages?q=windowsazureofficial). Podívejte se na [referenční informace k rozhraní API](/dotnet/api/overview/azure/?view=azure-dotnet) pro referenční dokumentaci organizované službou Azure.

## <a name="development-tools"></a>Vývojářské nástroje

Visual Studio obsahuje nástroje pro řadu předdefinovaných služeb Azure. Některé služby Azure mají k dispozici další nástroje nebo emulátory, například [Průzkumník služby Azure Storage](https://azure.microsoft.com/features/storage-explorer/). V případě potřeby si přečtěte dokumentaci ke službě Azure pro všechny další nástroje.

Níže vyberte preferované vývojové prostředí.

## <a name="visual-studio-on-windows"></a>[Visual Studio ve Windows](#tab/vs)

Visual Studio verze 2017 a novější má integrovanou podporu pro vývoj pro Azure. Níže uvedené kroky popisují povolení podpory vývoje Azure v aplikaci Visual Studio.

V případě sady Visual Studio 2015 a starších verzí <a href="vs2015-install.md">postupujte podle těchto pokynů</a>.

### <a name="step-1-download-visual-studio-2019"></a>Krok 1: stažení sady Visual Studio 2019

Pokud již máte nainstalováno Visual Studio 2019, můžete tento krok přeskočit.

> [!div class="nextstepaction"]
> [Stáhněte si Visual Studio 2019](https://www.visualstudio.com/downloads/)

### <a name="step-2-install-the-two-azure-workloads"></a>Krok 2: instalace dvou úloh Azure

V instalačním programu sady Visual Studio nainstalujte Visual Studio (nebo upravte existující instalaci). Ujistěte se, že jsou vybrané úlohy vývoje a *ASP.NET a* vývoj pro web *Azure* .

### <a name="step-3-develop-with-net-on-azure"></a>Krok 3: vývoj s využitím .NET v Azure

Začněte [nasazením první ASP.NET Core webové aplikace v Azure App Service](/azure/app-service-web/app-service-web-get-started-dotnet).

## <a name="visual-studio-code-cross-platform"></a>[Visual Studio Code (pro různé platformy)](#tab/vscode)

Visual Studio Code má všechno, co potřebujete pro vývoj pro Azure na různých platformách.

### <a name="step-1-download-the-net-core-sdk"></a>Krok 1: stažení .NET Core SDK

Sada SDK a nástroje příkazového řádku pro aplikace .NET Core

> [!div class="nextstepaction"]
> [Stáhnout .NET Core SDK](https://dotnet.microsoft.com/download)

### <a name="step-2-visual-studio-code"></a>Krok 2: Visual Studio Code

Upravit a ladit aplikace .NET Core v jakémkoli operačním systému: Windows, Mac a Linux.

> [!div class="nextstepaction"]
> [Stáhnout Visual Studio Code](https://code.visualstudio.com)

### <a name="step-3-azure-tools-extension"></a>Krok 3: rozšíření nástrojů Azure

Nainstalujte rozšíření Azure Tools v Visual Studio Code.

> [!div class="nextstepaction"]
> [Nainstalovat rozšíření nástrojů Azure](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-node-azure-pack)

### <a name="step-4-develop-with-net-on-azure"></a>Krok 4: vývoj s využitím .NET v Azure

Začněte [nasazením první ASP.NET Core webové aplikace v Azure App Service v systému Linux](/azure/app-service/containers/quickstart-dotnetcore).

---
