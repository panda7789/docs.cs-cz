---
title: Nástroje Azure pro Visual Studio 2015
description: Získejte nástroje pro zahájení používání knihoven Azure .NET ze sady Visual Studio 2015.
ms.date: 10/19/2017
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: a29709d56f2debe04d49ee4eafdc27acd4ca480f
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2020
ms.locfileid: "82071925"
---
# <a name="azure-tools-for-visual-studio-2015"></a>Nástroje Azure pro Visual Studio 2015

Nejrychlejší a nejjednodušší způsob, jak nainstalovat **sadu Azure SDK pro Visual studio 2015** a **Service Fabric SDK a nástroje pro Visual Studio 2015** , používá [instalační program webové platformy](https://www.microsoft.com/web/downloads/platform.aspx). Instalace webové platformy Microsoft je bezplatný nástroj, který zjednodušuje stahování, instalaci a aktualizaci některých komponent webové platformy Microsoftu, včetně nástrojů Azure pro Visual Studio 2015. Tyto sady SDK je také možné stáhnout a nainstalovat jako jednotlivé komponenty ze [stránky Azure downloads](https://azure.microsoft.com/downloads/).

## <a name="using-the-web-platform-installer"></a>Použití instalačního programu webové platformy

1. Stáhněte a spusťte tento [zaváděcí program instalace webové platformy](https://www.microsoft.com/web/handlers/webpi.ashx?command=getinstallerredirect&appid=VWDOrVs2015AzurePack;MicrosoftAzure-ServiceFabric-VS2015).

2. Zaváděcí nástroj nainstaluje instalační program webové platformy (v případě potřeby) a automaticky vloží nejnovější verze **sady Azure SDK pro Visual studio 2015** a **Service Fabric sady SDK a nástrojů pro Visual Studio 2015** položky v seznamu *položky, které mají být nainstalovány* . Klikněte na **nainstalovat**.

    ![Instalační program webové platformy](../media/sdk/vs2015-install/webpi.png)

3. Na další obrazovce klikněte na **Souhlasím**. Webová PI začne stahovat a instalovat součásti, které jste vybrali.

4. Po dokončení instalace se zobrazí potvrzovací obrazovka. Klikněte na **Finish** (Dokončit). Nyní můžete zavřít instalační program webové platformy.

## <a name="verifying-the-installation"></a>Ověření instalace

1. V aplikaci Visual Studio 2015 klikněte na nabídku **nástroje** a potom klikněte na možnost **rozšíření a aktualizace...**.

2. Zobrazený seznam bude obsahovat několik nástrojů Azure, například **Microsoft Azure App Service nástroje**, **Microsoft Azure Storage připojená služba**a **nástroje Service Fabric**.

    ![Rozšíření a aktualizace](../media/sdk/vs2015-install/ext-tools.png)
