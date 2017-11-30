---
title: "Postupy: Vytváření služeb systému Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Service applications, creating
- templates, Windows Service
ms.assetid: 0f5e2cbb-d95d-477c-b2b5-4b990e6b86ff
caps.latest.revision: "18"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: c4d7f2f19c8d156f86513ac7138bccd59ae3b7fb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-windows-services"></a><span data-ttu-id="6a150-102">Postupy: Vytváření služeb systému Windows</span><span class="sxs-lookup"><span data-stu-id="6a150-102">How to: Create Windows Services</span></span>
<span data-ttu-id="6a150-103">Když vytváříte službu, můžete použít šabloně projektu sady Visual Studio s názvem **služba systému Windows**.</span><span class="sxs-lookup"><span data-stu-id="6a150-103">When you create a service, you can use a Visual Studio project template called **Windows Service**.</span></span> <span data-ttu-id="6a150-104">Tato šablona automaticky provede většinu práce vám tak, že odkazy na příslušné třídy a obory názvů, nastavení dědičnosti ze základní třídy pro služby, a přepsání několik metod budete pravděpodobně chcete přepsat.</span><span class="sxs-lookup"><span data-stu-id="6a150-104">This template automatically does much of the work for you by referencing the appropriate classes and namespaces, setting up the inheritance from the base class for services, and overriding several of the methods you're likely to want to override.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="6a150-105">Šablona projektu služby systému Windows není k dispozici v edici Express sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6a150-105">The Windows Services project template is not available in the Express edition of Visual Studio.</span></span>  
  
 <span data-ttu-id="6a150-106">Minimálně vytvoření funkčnosti služby, musíte:</span><span class="sxs-lookup"><span data-stu-id="6a150-106">At a minimum, to create a functional service you must:</span></span>  
  
-   <span data-ttu-id="6a150-107">Nastavte <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6a150-107">Set the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property.</span></span>  
  
-   <span data-ttu-id="6a150-108">Vytvořte potřebné instalační programy pro aplikaci služby.</span><span class="sxs-lookup"><span data-stu-id="6a150-108">Create the necessary installers for your service application.</span></span>  
  
-   <span data-ttu-id="6a150-109">Přepsat a zadat kód pro <xref:System.ServiceProcess.ServiceBase.OnStart%2A> a <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metody pro přizpůsobení způsobů, jak se chová služby.</span><span class="sxs-lookup"><span data-stu-id="6a150-109">Override and specify code for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods to customize the ways in which your service behaves.</span></span>  
  
### <a name="to-create-a-windows-service-application"></a><span data-ttu-id="6a150-110">Vytvoření aplikace služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="6a150-110">To create a Windows Service application</span></span>  
  
1.  <span data-ttu-id="6a150-111">Vytvoření **služba systému Windows** projektu.</span><span class="sxs-lookup"><span data-stu-id="6a150-111">Create a **Windows Service** project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6a150-112">Pokyny pro zápis služby bez použití šablony, v tématu [postupy: zápis služeb prostřednictvím kódu programu](../../../docs/framework/windows-services/how-to-write-services-programmatically.md).</span><span class="sxs-lookup"><span data-stu-id="6a150-112">For instructions on writing a service without using the template, see [How to: Write Services Programmatically](../../../docs/framework/windows-services/how-to-write-services-programmatically.md).</span></span>  
  
2.  <span data-ttu-id="6a150-113">V **vlastnosti** nastavte <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> vlastnost pro vaši službu.</span><span class="sxs-lookup"><span data-stu-id="6a150-113">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for your service.</span></span>  
  
     <span data-ttu-id="6a150-114">![Nastavte vlastnost ServiceName. ] (../../../docs/framework/windows-services/media/windowsservice-servicename.PNG "WindowsService_ServiceName")</span><span class="sxs-lookup"><span data-stu-id="6a150-114">![Set the ServiceName property.](../../../docs/framework/windows-services/media/windowsservice-servicename.PNG "WindowsService_ServiceName")</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6a150-115">Hodnota <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> vlastnost musí vždy odpovídat názvu zaznamenávají v třídách Instalační služby.</span><span class="sxs-lookup"><span data-stu-id="6a150-115">The value of the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property must always match the name recorded in the installer classes.</span></span> <span data-ttu-id="6a150-116">Pokud tuto vlastnost změníte, musíte aktualizovat <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> vlastnost také třídy Instalační služby.</span><span class="sxs-lookup"><span data-stu-id="6a150-116">If you change this property, you must update the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property of installer classes as well.</span></span>  
  
3.  <span data-ttu-id="6a150-117">Nastavte následující vlastnosti k určení, jak bude vaše služba fungovat.</span><span class="sxs-lookup"><span data-stu-id="6a150-117">Set any of the following properties to determine how your service will function.</span></span>  
  
    |<span data-ttu-id="6a150-118">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="6a150-118">Property</span></span>|<span data-ttu-id="6a150-119">Nastavení</span><span class="sxs-lookup"><span data-stu-id="6a150-119">Setting</span></span>|  
    |--------------|-------------|  
    |<xref:System.ServiceProcess.ServiceBase.CanStop%2A>|<span data-ttu-id="6a150-120">`True`k označení, že služba bude přijímat žádosti o zastaví; `false` zabránit zastavenou službu.</span><span class="sxs-lookup"><span data-stu-id="6a150-120">`True` to indicate that the service will accept requests to stop running; `false` to prevent the service from being stopped.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanShutdown%2A>|<span data-ttu-id="6a150-121">`True`k označení, že služba chce dostávat oznámení při vypnutí počítače, na kterém je umístěn mimo provoz, povolení k volání <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> postupu.</span><span class="sxs-lookup"><span data-stu-id="6a150-121">`True` to indicate that the service wants to receive notification when the computer on which it lives shuts down, enabling it to call the <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> procedure.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A>|<span data-ttu-id="6a150-122">`True`k označení, že služba bude přijímat požadavky pozastavit nebo obnovit systémem; `false` aby služby z je pozastavený a obnovený.</span><span class="sxs-lookup"><span data-stu-id="6a150-122">`True` to indicate that the service will accept requests to pause or to resume running; `false` to prevent the service from being paused and resumed.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanHandlePowerEvent%2A>|<span data-ttu-id="6a150-123">`True`k označení, že služba dokáže zpracovat oznámení změny stavu napájení počítače; `false` zabránit službu upozornění na tyto změny.</span><span class="sxs-lookup"><span data-stu-id="6a150-123">`True` to indicate that the service can handle notification of changes to the computer's power status; `false` to prevent the service from being notified of these changes.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.AutoLog%2A>|<span data-ttu-id="6a150-124">`True`k zápisu informační položky do protokolu událostí aplikace, když služby provádí akce; `false` zakázat tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="6a150-124">`True` to write informational entries to the Application event log when your service performs an action; `false` to disable this functionality.</span></span> <span data-ttu-id="6a150-125">Další informace najdete v tématu [postup: protokolu informace o služby](../../../docs/framework/windows-services/how-to-log-information-about-services.md).</span><span class="sxs-lookup"><span data-stu-id="6a150-125">For more information, see [How to: Log Information About Services](../../../docs/framework/windows-services/how-to-log-information-about-services.md).</span></span> <span data-ttu-id="6a150-126">**Poznámka:** ve výchozím nastavení, <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> je nastaven na `true`.</span><span class="sxs-lookup"><span data-stu-id="6a150-126">**Note:**  By default, <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> is set to `true`.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="6a150-127">Když <xref:System.ServiceProcess.ServiceBase.CanStop%2A> nebo <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> jsou nastaveny na `false`, **správce řízení služeb** vypne odpovídající možností v nabídce zastavit, pozastavit nebo službu dále používat.</span><span class="sxs-lookup"><span data-stu-id="6a150-127">When <xref:System.ServiceProcess.ServiceBase.CanStop%2A> or <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> are set to `false`, the **Service Control Manager** will disable the corresponding menu options to stop, pause, or continue the service.</span></span>  
  
4.  <span data-ttu-id="6a150-128">Přístup k editoru kódu a vyplňte chcete použít pro zpracování <xref:System.ServiceProcess.ServiceBase.OnStart%2A> a <xref:System.ServiceProcess.ServiceBase.OnStop%2A> postupy.</span><span class="sxs-lookup"><span data-stu-id="6a150-128">Access the Code Editor and fill in the processing you want for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedures.</span></span>  
  
5.  <span data-ttu-id="6a150-129">Přepište jiné metody, pro které chcete definovat funkce.</span><span class="sxs-lookup"><span data-stu-id="6a150-129">Override any other methods for which you want to define functionality.</span></span>  
  
6.  <span data-ttu-id="6a150-130">Přidejte nezbytné instalační programy pro aplikaci služby.</span><span class="sxs-lookup"><span data-stu-id="6a150-130">Add the necessary installers for your service application.</span></span> <span data-ttu-id="6a150-131">Další informace najdete v tématu [postupy: Přidání instalačních programů pro vaše aplikace služby](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="6a150-131">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
7.  <span data-ttu-id="6a150-132">Sestavení projektu výběrem **sestavit řešení** z **sestavení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="6a150-132">Build your project by selecting **Build Solution** from the **Build** menu.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6a150-133">Není stisknutím klávesy F5 spusťte projekt – služba projektu nelze spustit tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="6a150-133">Do not press F5 to run your project — you cannot run a service project in this way.</span></span>  
  
8.  <span data-ttu-id="6a150-134">Nainstalujte službu.</span><span class="sxs-lookup"><span data-stu-id="6a150-134">Install the service.</span></span> <span data-ttu-id="6a150-135">Další informace najdete v tématu [postupy: instalace a odinstalace služeb](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="6a150-135">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a150-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="6a150-136">See Also</span></span>  
 [<span data-ttu-id="6a150-137">Úvod do aplikace služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="6a150-137">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="6a150-138">Postupy: zápis služeb prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="6a150-138">How to: Write Services Programmatically</span></span>](../../../docs/framework/windows-services/how-to-write-services-programmatically.md)  
 [<span data-ttu-id="6a150-139">Postupy: Přidání instalačních programů do aplikace služby</span><span class="sxs-lookup"><span data-stu-id="6a150-139">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [<span data-ttu-id="6a150-140">Postupy: protokolování informací o službách</span><span class="sxs-lookup"><span data-stu-id="6a150-140">How to: Log Information About Services</span></span>](../../../docs/framework/windows-services/how-to-log-information-about-services.md)  
 [<span data-ttu-id="6a150-141">Postupy: spuštění služeb</span><span class="sxs-lookup"><span data-stu-id="6a150-141">How to: Start Services</span></span>](../../../docs/framework/windows-services/how-to-start-services.md)  
 [<span data-ttu-id="6a150-142">Postupy: určení kontextu zabezpečení pro služby</span><span class="sxs-lookup"><span data-stu-id="6a150-142">How to: Specify the Security Context for Services</span></span>](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)  
 [<span data-ttu-id="6a150-143">Postupy: instalace a odinstalace služeb</span><span class="sxs-lookup"><span data-stu-id="6a150-143">How to: Install and Uninstall Services</span></span>](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [<span data-ttu-id="6a150-144">Návod: Vytvoření aplikace služby systému Windows v Návrháři součástí</span><span class="sxs-lookup"><span data-stu-id="6a150-144">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
