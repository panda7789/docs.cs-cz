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
# <a name="azure-tools-for-visual-studio-2015"></a><span data-ttu-id="40d83-103">Nástroje Azure pro Visual Studio 2015</span><span class="sxs-lookup"><span data-stu-id="40d83-103">Azure tools for Visual Studio 2015</span></span>

<span data-ttu-id="40d83-104">Nejrychlejší a nejjednodušší způsob, jak nainstalovat **sadu Azure SDK pro Visual studio 2015** a **Service Fabric SDK a nástroje pro Visual Studio 2015** , používá [instalační program webové platformy](https://www.microsoft.com/web/downloads/platform.aspx).</span><span class="sxs-lookup"><span data-stu-id="40d83-104">The quickest and easiest way to install the **Azure SDK for Visual Studio 2015** and **Service Fabric SDK and Tools for Visual Studio 2015** is using the [Web Platform Installer](https://www.microsoft.com/web/downloads/platform.aspx).</span></span> <span data-ttu-id="40d83-105">Instalace webové platformy Microsoft je bezplatný nástroj, který zjednodušuje stahování, instalaci a aktualizaci některých komponent webové platformy Microsoftu, včetně nástrojů Azure pro Visual Studio 2015.</span><span class="sxs-lookup"><span data-stu-id="40d83-105">The Microsoft Web Platform Installer is a free tool that streamlines downloading, installing, and updating some of the components of the Microsoft Web Platform, including Azure tools for Visual Studio 2015.</span></span> <span data-ttu-id="40d83-106">Tyto sady SDK je také možné stáhnout a nainstalovat jako jednotlivé komponenty ze [stránky Azure downloads](https://azure.microsoft.com/downloads/).</span><span class="sxs-lookup"><span data-stu-id="40d83-106">These SDKs can also be downloaded and installed as individual components from the [Azure Downloads page](https://azure.microsoft.com/downloads/).</span></span>

## <a name="using-the-web-platform-installer"></a><span data-ttu-id="40d83-107">Použití instalačního programu webové platformy</span><span class="sxs-lookup"><span data-stu-id="40d83-107">Using the Web Platform Installer</span></span>

1. <span data-ttu-id="40d83-108">Stáhněte a spusťte tento [zaváděcí program instalace webové platformy](https://www.microsoft.com/web/handlers/webpi.ashx?command=getinstallerredirect&appid=VWDOrVs2015AzurePack;MicrosoftAzure-ServiceFabric-VS2015).</span><span class="sxs-lookup"><span data-stu-id="40d83-108">Download and run this [Web Platform Installer bootstrapper](https://www.microsoft.com/web/handlers/webpi.ashx?command=getinstallerredirect&appid=VWDOrVs2015AzurePack;MicrosoftAzure-ServiceFabric-VS2015).</span></span>

2. <span data-ttu-id="40d83-109">Zaváděcí nástroj nainstaluje instalační program webové platformy (v případě potřeby) a automaticky vloží nejnovější verze **sady Azure SDK pro Visual studio 2015** a **Service Fabric sady SDK a nástrojů pro Visual Studio 2015** položky v seznamu *položky, které mají být nainstalovány* .</span><span class="sxs-lookup"><span data-stu-id="40d83-109">The bootstrapper will install Web Platform Installer (if needed) and automatically put the latest versions of the  **Azure SDK for Visual Studio 2015** and **Service Fabric SDK and Tools for Visual Studio 2015** items in your *Items to be installed* list.</span></span> <span data-ttu-id="40d83-110">Klikněte na **Install** (Nainstalovat).</span><span class="sxs-lookup"><span data-stu-id="40d83-110">Click **Install**.</span></span>

    ![Instalační program webové platformy](media/vs2015-install/webpi.png)

3. <span data-ttu-id="40d83-112">Na další obrazovce klikněte na **Souhlasím**.</span><span class="sxs-lookup"><span data-stu-id="40d83-112">On the next screen, click **I Accept**.</span></span> <span data-ttu-id="40d83-113">Webová PI začne stahovat a instalovat součásti, které jste vybrali.</span><span class="sxs-lookup"><span data-stu-id="40d83-113">Web PI will begin downloading and installing the components you selected.</span></span>

4. <span data-ttu-id="40d83-114">Po dokončení instalace se zobrazí potvrzovací obrazovka.</span><span class="sxs-lookup"><span data-stu-id="40d83-114">After the installation is finished, it will display a confirmation screen.</span></span> <span data-ttu-id="40d83-115">Klikněte na **Finish** (Dokončit).</span><span class="sxs-lookup"><span data-stu-id="40d83-115">Click **Finish**.</span></span> <span data-ttu-id="40d83-116">Nyní můžete zavřít instalační program webové platformy.</span><span class="sxs-lookup"><span data-stu-id="40d83-116">You can now close Web Platform Installer.</span></span>

## <a name="verifying-the-installation"></a><span data-ttu-id="40d83-117">Ověření instalace</span><span class="sxs-lookup"><span data-stu-id="40d83-117">Verifying the installation</span></span>

1. <span data-ttu-id="40d83-118">V aplikaci Visual Studio 2015 klikněte na nabídku **nástroje** a potom klikněte na možnost **rozšíření a aktualizace...**.</span><span class="sxs-lookup"><span data-stu-id="40d83-118">In Visual Studio 2015, click the **Tools** menu, and then click **Extensions and Updates...**.</span></span>

2. <span data-ttu-id="40d83-119">Zobrazený seznam bude obsahovat několik nástrojů Azure, například **Microsoft Azure App Service nástroje**, **Microsoft Azure Storage připojená služba**a **nástroje Service Fabric**.</span><span class="sxs-lookup"><span data-stu-id="40d83-119">The displayed list will contain several Azure tools, such as **Microsoft Azure App Service Tools**, **Microsoft Azure Storage Connected Service**, and **Service Fabric Tools**.</span></span>

    ![Rozšíření a aktualizace](media/vs2015-install/ext-tools.png)
