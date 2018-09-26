---
title: 'Postupy: Vytváření služeb systému Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, creating
- templates, Windows Service
ms.assetid: 0f5e2cbb-d95d-477c-b2b5-4b990e6b86ff
author: ghogen
ms.openlocfilehash: 7a529a94edf3a4cf71150c04994d82b8f21eb996
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47204635"
---
# <a name="how-to-create-windows-services"></a><span data-ttu-id="99d20-102">Postupy: Vytváření služeb systému Windows</span><span class="sxs-lookup"><span data-stu-id="99d20-102">How to: Create Windows Services</span></span>
<span data-ttu-id="99d20-103">Při vytváření služby můžete použít šablonu projektu sady Visual Studio volá **Windows Service**.</span><span class="sxs-lookup"><span data-stu-id="99d20-103">When you create a service, you can use a Visual Studio project template called **Windows Service**.</span></span> <span data-ttu-id="99d20-104">Tato šablona automaticky provádí velkou část práce za vás odkazováním na příslušné třídy a obory názvů, nastavením dědičnosti ze základní třídy pro služby, a přepisováním několika metod, které budete pravděpodobně chtít přepsat.</span><span class="sxs-lookup"><span data-stu-id="99d20-104">This template automatically does much of the work for you by referencing the appropriate classes and namespaces, setting up the inheritance from the base class for services, and overriding several of the methods you're likely to want to override.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="99d20-105">Šablona projektu služby Windows není k dispozici v edici Express sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="99d20-105">The Windows Services project template is not available in the Express edition of Visual Studio.</span></span>  
  
 <span data-ttu-id="99d20-106">Minimálně pro vytvoření funkční služby je potřeba:</span><span class="sxs-lookup"><span data-stu-id="99d20-106">At a minimum, to create a functional service you must:</span></span>  
  
-   <span data-ttu-id="99d20-107">Nastavte <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="99d20-107">Set the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property.</span></span>  
  
-   <span data-ttu-id="99d20-108">Vytvořte nezbytné instalační programy pro aplikaci služby.</span><span class="sxs-lookup"><span data-stu-id="99d20-108">Create the necessary installers for your service application.</span></span>  
  
-   <span data-ttu-id="99d20-109">A zadejte kód pro <xref:System.ServiceProcess.ServiceBase.OnStart%2A> a <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metody, chcete-li přizpůsobit způsoby, jak se chová vaší služby.</span><span class="sxs-lookup"><span data-stu-id="99d20-109">Override and specify code for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods to customize the ways in which your service behaves.</span></span>  
  
### <a name="to-create-a-windows-service-application"></a><span data-ttu-id="99d20-110">Vytvoření aplikace služby Windows</span><span class="sxs-lookup"><span data-stu-id="99d20-110">To create a Windows Service application</span></span>  
  
1.  <span data-ttu-id="99d20-111">Vytvoření **Windows Service** projektu.</span><span class="sxs-lookup"><span data-stu-id="99d20-111">Create a **Windows Service** project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="99d20-112">Pokyny pro zápis služby bez použití šablony najdete v tématu [postupy: zápis služeb prostřednictvím kódu programu](../../../docs/framework/windows-services/how-to-write-services-programmatically.md).</span><span class="sxs-lookup"><span data-stu-id="99d20-112">For instructions on writing a service without using the template, see [How to: Write Services Programmatically](../../../docs/framework/windows-services/how-to-write-services-programmatically.md).</span></span>  
  
2.  <span data-ttu-id="99d20-113">V **vlastnosti** okno, nastaveno <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> vlastnost pro vaši službu.</span><span class="sxs-lookup"><span data-stu-id="99d20-113">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for your service.</span></span>  
  
     <span data-ttu-id="99d20-114">![Nastavte vlastnost ServiceName. ](../../../docs/framework/windows-services/media/windowsservice-servicename.PNG "WindowsService_ServiceName")</span><span class="sxs-lookup"><span data-stu-id="99d20-114">![Set the ServiceName property.](../../../docs/framework/windows-services/media/windowsservice-servicename.PNG "WindowsService_ServiceName")</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="99d20-115">Hodnota <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> vlastnosti musí vždy odpovídat názvu v instalačních třídách.</span><span class="sxs-lookup"><span data-stu-id="99d20-115">The value of the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property must always match the name recorded in the installer classes.</span></span> <span data-ttu-id="99d20-116">Pokud tuto vlastnost změníte, je nutné aktualizovat <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> vlastnost také instalačních tříd.</span><span class="sxs-lookup"><span data-stu-id="99d20-116">If you change this property, you must update the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property of installer classes as well.</span></span>  
  
3.  <span data-ttu-id="99d20-117">Nastavte libovolné z následujících vlastností určíte, jak služba funguje.</span><span class="sxs-lookup"><span data-stu-id="99d20-117">Set any of the following properties to determine how your service will function.</span></span>  
  
    |<span data-ttu-id="99d20-118">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="99d20-118">Property</span></span>|<span data-ttu-id="99d20-119">Nastavení</span><span class="sxs-lookup"><span data-stu-id="99d20-119">Setting</span></span>|  
    |--------------|-------------|  
    |<xref:System.ServiceProcess.ServiceBase.CanStop%2A>|<span data-ttu-id="99d20-120">`True` Chcete-li určit, že služba bude přijímat žádosti o zastavení činnosti; `false` zabránit zastavení služby.</span><span class="sxs-lookup"><span data-stu-id="99d20-120">`True` to indicate that the service will accept requests to stop running; `false` to prevent the service from being stopped.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanShutdown%2A>|<span data-ttu-id="99d20-121">`True` k označení, že služba chce obdržet oznámení, při vypnutí počítače, ve kterém žije, aby mohla volat <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> postup.</span><span class="sxs-lookup"><span data-stu-id="99d20-121">`True` to indicate that the service wants to receive notification when the computer on which it lives shuts down, enabling it to call the <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> procedure.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A>|<span data-ttu-id="99d20-122">`True` Chcete-li určit, že služba bude přijímat žádosti o pozastavení nebo obnovení činnosti; `false` zabránit službě pozastavit a obnovit.</span><span class="sxs-lookup"><span data-stu-id="99d20-122">`True` to indicate that the service will accept requests to pause or to resume running; `false` to prevent the service from being paused and resumed.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanHandlePowerEvent%2A>|<span data-ttu-id="99d20-123">`True` k označení, že služba může zpracovat oznámení změny stavu napájení počítače; `false` zabránit službě dostávat oznámení těchto změn.</span><span class="sxs-lookup"><span data-stu-id="99d20-123">`True` to indicate that the service can handle notification of changes to the computer's power status; `false` to prevent the service from being notified of these changes.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.AutoLog%2A>|<span data-ttu-id="99d20-124">`True` pro zápis informačních položek do protokolu událostí aplikace, když služba provede akci; `false` zakázat tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="99d20-124">`True` to write informational entries to the Application event log when your service performs an action; `false` to disable this functionality.</span></span> <span data-ttu-id="99d20-125">Další informace najdete v tématu [jak: protokolu informace o služby](../../../docs/framework/windows-services/how-to-log-information-about-services.md).</span><span class="sxs-lookup"><span data-stu-id="99d20-125">For more information, see [How to: Log Information About Services](../../../docs/framework/windows-services/how-to-log-information-about-services.md).</span></span> <span data-ttu-id="99d20-126">**Poznámka:** ve výchozím nastavení, <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> je nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="99d20-126">**Note:**  By default, <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> is set to `true`.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="99d20-127">Když <xref:System.ServiceProcess.ServiceBase.CanStop%2A> nebo <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> jsou nastaveny na `false`, **správce řízení služeb** zakáže odpovídající možnosti nabídky zastavit, pozastavit nebo pokračovat ve službě.</span><span class="sxs-lookup"><span data-stu-id="99d20-127">When <xref:System.ServiceProcess.ServiceBase.CanStop%2A> or <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> are set to `false`, the **Service Control Manager** will disable the corresponding menu options to stop, pause, or continue the service.</span></span>  
  
4.  <span data-ttu-id="99d20-128">Přístup k editoru kódu a vyplňte zpracování, které požadujete pro <xref:System.ServiceProcess.ServiceBase.OnStart%2A> a <xref:System.ServiceProcess.ServiceBase.OnStop%2A> postupy.</span><span class="sxs-lookup"><span data-stu-id="99d20-128">Access the Code Editor and fill in the processing you want for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedures.</span></span>  
  
5.  <span data-ttu-id="99d20-129">Přepište všechny jiné metody, pro které chcete definovat funkci.</span><span class="sxs-lookup"><span data-stu-id="99d20-129">Override any other methods for which you want to define functionality.</span></span>  
  
6.  <span data-ttu-id="99d20-130">Přidejte nezbytné instalační programy pro aplikaci služby.</span><span class="sxs-lookup"><span data-stu-id="99d20-130">Add the necessary installers for your service application.</span></span> <span data-ttu-id="99d20-131">Další informace najdete v tématu [postupy: Přidání instalačních programů do aplikace služby](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="99d20-131">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
7.  <span data-ttu-id="99d20-132">Sestavte projekt výběrem **sestavit řešení** z **sestavení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="99d20-132">Build your project by selecting **Build Solution** from the **Build** menu.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="99d20-133">Nepoužívejte klávesu F5 ke spuštění projektu – tímto způsobem nelze spustit projekt služby.</span><span class="sxs-lookup"><span data-stu-id="99d20-133">Do not press F5 to run your project — you cannot run a service project in this way.</span></span>  
  
8.  <span data-ttu-id="99d20-134">Nainstalujte službu.</span><span class="sxs-lookup"><span data-stu-id="99d20-134">Install the service.</span></span> <span data-ttu-id="99d20-135">Další informace najdete v tématu [postupy: instalace a odinstalace služeb](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="99d20-135">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99d20-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="99d20-136">See Also</span></span>  
 [<span data-ttu-id="99d20-137">Úvod do aplikací služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="99d20-137">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="99d20-138">Postupy: Zápis služeb prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="99d20-138">How to: Write Services Programmatically</span></span>](../../../docs/framework/windows-services/how-to-write-services-programmatically.md)  
 [<span data-ttu-id="99d20-139">Postupy: Přidání instalačních programů do aplikace služby</span><span class="sxs-lookup"><span data-stu-id="99d20-139">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [<span data-ttu-id="99d20-140">Postupy: Protokolování informací o službách</span><span class="sxs-lookup"><span data-stu-id="99d20-140">How to: Log Information About Services</span></span>](../../../docs/framework/windows-services/how-to-log-information-about-services.md)  
 [<span data-ttu-id="99d20-141">Postupy: Spuštění služeb</span><span class="sxs-lookup"><span data-stu-id="99d20-141">How to: Start Services</span></span>](../../../docs/framework/windows-services/how-to-start-services.md)  
 [<span data-ttu-id="99d20-142">Postupy: Určení kontextu zabezpečení pro služby</span><span class="sxs-lookup"><span data-stu-id="99d20-142">How to: Specify the Security Context for Services</span></span>](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)  
 [<span data-ttu-id="99d20-143">Postupy: Instalace a odinstalace služeb</span><span class="sxs-lookup"><span data-stu-id="99d20-143">How to: Install and Uninstall Services</span></span>](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [<span data-ttu-id="99d20-144">Návod: Vytvoření aplikace služby systému Windows v návrháři součástí</span><span class="sxs-lookup"><span data-stu-id="99d20-144">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
