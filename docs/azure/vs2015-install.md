---
title: Nástroje Azure pro Visual Studio 2015
description: Získejte nástroje pro zahájení používání knihoven Azure .NET ze sady Visual Studio 2015.
ms.date: 06/19/2020
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: 72229ce0c0276912ddc5658e34f4572a7948a4e6
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174904"
---
# <a name="azure-tools-for-visual-studio-2015"></a>Nástroje Azure pro Visual Studio 2015

Nejrychlejší a nejjednodušší způsob, jak nainstalovat **sadu Azure SDK pro Visual studio 2015** a **Service Fabric SDK a nástroje pro Visual Studio 2015** , používá [instalační program webové platformy](https://www.microsoft.com/web/downloads/platform.aspx). Instalace webové platformy Microsoft je bezplatný nástroj, který zjednodušuje stahování, instalaci a aktualizaci některých komponent webové platformy Microsoftu, včetně nástrojů Azure pro Visual Studio 2015. Tyto sady SDK je také možné stáhnout a nainstalovat jako jednotlivé komponenty ze [stránky Azure downloads](https://azure.microsoft.com/downloads/).

## <a name="using-the-web-platform-installer"></a>Použití instalačního programu webové platformy

1. Stáhněte a spusťte tento [zaváděcí program instalace webové platformy](https://www.microsoft.com/web/handlers/webpi.ashx?command=getinstallerredirect&appid=VWDOrVs2015AzurePack;MicrosoftAzure-ServiceFabric-VS2015).

2. Zaváděcí nástroj nainstaluje instalační program webové platformy (v případě potřeby) a automaticky vloží nejnovější verze **sady Azure SDK pro Visual studio 2015** a **Service Fabric sady SDK a nástrojů pro Visual Studio 2015** položky v seznamu *položky, které mají být nainstalovány* . Klikněte na **Install** (Nainstalovat).

    ![Instalační program webové platformy](media/vs2015-install/webpi.png)

3. Na další obrazovce klikněte na **Souhlasím**. Webová PI začne stahovat a instalovat součásti, které jste vybrali.

4. Po dokončení instalace se zobrazí potvrzovací obrazovka. Klikněte na **Finish** (Dokončit). Nyní můžete zavřít instalační program webové platformy.

## <a name="verifying-the-installation"></a>Ověření instalace

1. V aplikaci Visual Studio 2015 klikněte na nabídku **nástroje** a potom klikněte na možnost **rozšíření a aktualizace...**.

2. Zobrazený seznam bude obsahovat několik nástrojů Azure, například **Microsoft Azure App Service nástroje**, **Microsoft Azure Storage připojená služba**a **nástroje Service Fabric**.

    ![Rozšíření a aktualizace](media/vs2015-install/ext-tools.png)
