---
title: Nástroje Azure pro Visual Studio 2015
description: Získejte nástroje, které vám pomohou začít používat knihovny Azure .NET z Visual Studia 2015.
ms.date: 10/19/2017
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: a29709d56f2debe04d49ee4eafdc27acd4ca480f
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2020
ms.locfileid: "82071925"
---
# <a name="azure-tools-for-visual-studio-2015"></a><span data-ttu-id="62de0-103">Nástroje Azure pro Visual Studio 2015</span><span class="sxs-lookup"><span data-stu-id="62de0-103">Azure tools for Visual Studio 2015</span></span>

<span data-ttu-id="62de0-104">Nejrychlejší a nejjednodušší způsob instalace **sady Azure SDK pro Visual Studio 2015** a **Service Fabric SDK a Nástroje pro Visual Studio 2015** používá [Instalační službu webové platformy](https://www.microsoft.com/web/downloads/platform.aspx).</span><span class="sxs-lookup"><span data-stu-id="62de0-104">The quickest and easiest way to install the **Azure SDK for Visual Studio 2015** and **Service Fabric SDK and Tools for Visual Studio 2015** is using the [Web Platform Installer](https://www.microsoft.com/web/downloads/platform.aspx).</span></span> <span data-ttu-id="62de0-105">Instalační služba webové platformy Microsoft je bezplatný nástroj, který zjednodušuje stahování, instalaci a aktualizaci některých součástí webové platformy Microsoft, včetně nástrojů Azure pro Visual Studio 2015.</span><span class="sxs-lookup"><span data-stu-id="62de0-105">The Microsoft Web Platform Installer is a free tool that streamlines downloading, installing, and updating some of the components of the Microsoft Web Platform, including Azure tools for Visual Studio 2015.</span></span> <span data-ttu-id="62de0-106">Tyto sady SDK lze také stáhnout a nainstalovat jako jednotlivé součásti ze [stránky Stahování Azure](https://azure.microsoft.com/downloads/).</span><span class="sxs-lookup"><span data-stu-id="62de0-106">These SDKs can also be downloaded and installed as individual components from the [Azure Downloads page](https://azure.microsoft.com/downloads/).</span></span>

## <a name="using-the-web-platform-installer"></a><span data-ttu-id="62de0-107">Použití Instalační služby webové platformy</span><span class="sxs-lookup"><span data-stu-id="62de0-107">Using the Web Platform Installer</span></span>

1. <span data-ttu-id="62de0-108">Stáhněte a spusťte tento [zaváděcí nástroj Instalační služby webové platformy](https://www.microsoft.com/web/handlers/webpi.ashx?command=getinstallerredirect&appid=VWDOrVs2015AzurePack;MicrosoftAzure-ServiceFabric-VS2015).</span><span class="sxs-lookup"><span data-stu-id="62de0-108">Download and run this [Web Platform Installer bootstrapper](https://www.microsoft.com/web/handlers/webpi.ashx?command=getinstallerredirect&appid=VWDOrVs2015AzurePack;MicrosoftAzure-ServiceFabric-VS2015).</span></span>

2. <span data-ttu-id="62de0-109">Zaváděcí nástroj nainstaluje Instalační program webové platformy (v případě potřeby) a automaticky vloží nejnovější verze **sady Azure SDK pro Visual Studio 2015** a service **fabric SDK a nástroje pro Visual Studio 2015** položky do seznamu *položky položky, které mají být nainstalovány.*</span><span class="sxs-lookup"><span data-stu-id="62de0-109">The bootstrapper will install Web Platform Installer (if needed) and automatically put the latest versions of the  **Azure SDK for Visual Studio 2015** and **Service Fabric SDK and Tools for Visual Studio 2015** items in your *Items to be installed* list.</span></span> <span data-ttu-id="62de0-110">Klepněte na tlačítko **Instalovat**.</span><span class="sxs-lookup"><span data-stu-id="62de0-110">Click **Install**.</span></span>

    ![Instalační program webové platformy](../media/sdk/vs2015-install/webpi.png)

3. <span data-ttu-id="62de0-112">Na další obrazovce klikněte na **Souhlasím**.</span><span class="sxs-lookup"><span data-stu-id="62de0-112">On the next screen, click **I Accept**.</span></span> <span data-ttu-id="62de0-113">Web PI začne stahovat a instalovat vybrané součásti.</span><span class="sxs-lookup"><span data-stu-id="62de0-113">Web PI will begin downloading and installing the components you selected.</span></span>

4. <span data-ttu-id="62de0-114">Po dokončení instalace se zobrazí potvrzovací obrazovka.</span><span class="sxs-lookup"><span data-stu-id="62de0-114">After the installation is finished, it will display a confirmation screen.</span></span> <span data-ttu-id="62de0-115">Klikněte na **Finish** (Dokončit).</span><span class="sxs-lookup"><span data-stu-id="62de0-115">Click **Finish**.</span></span> <span data-ttu-id="62de0-116">Instalační program webové platformy nyní můžete zavřít.</span><span class="sxs-lookup"><span data-stu-id="62de0-116">You can now close Web Platform Installer.</span></span>

## <a name="verifying-the-installation"></a><span data-ttu-id="62de0-117">Ověření instalace</span><span class="sxs-lookup"><span data-stu-id="62de0-117">Verifying the installation</span></span>

1. <span data-ttu-id="62de0-118">V sadě Visual Studio 2015 klikněte na nabídku **Nástroje** a potom klikněte na **Rozšíření a aktualizace...**.</span><span class="sxs-lookup"><span data-stu-id="62de0-118">In Visual Studio 2015, click the **Tools** menu, and then click **Extensions and Updates...**.</span></span>

2. <span data-ttu-id="62de0-119">Zobrazený seznam bude obsahovat několik nástrojů Azure, jako jsou **nástroje služby Microsoft Azure App Service Tools**, Microsoft Azure Storage Connected **Service**a Service **Fabric Tools**.</span><span class="sxs-lookup"><span data-stu-id="62de0-119">The displayed list will contain several Azure tools, such as **Microsoft Azure App Service Tools**, **Microsoft Azure Storage Connected Service**, and **Service Fabric Tools**.</span></span>

    ![Rozšíření a aktualizace](../media/sdk/vs2015-install/ext-tools.png)
