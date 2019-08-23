---
title: 'Postupy: Vytváření služeb systému Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, creating
- templates, Windows Service
ms.assetid: 0f5e2cbb-d95d-477c-b2b5-4b990e6b86ff
author: ghogen
ms.openlocfilehash: 148d99713b6e6379893701b8f217a7d7546decd9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952543"
---
# <a name="how-to-create-windows-services"></a><span data-ttu-id="fbc2b-102">Postupy: Vytváření služeb systému Windows</span><span class="sxs-lookup"><span data-stu-id="fbc2b-102">How to: Create Windows Services</span></span>
<span data-ttu-id="fbc2b-103">Při vytváření služby můžete použít šablonu projektu sady Visual Studio s názvem **služba systému Windows**.</span><span class="sxs-lookup"><span data-stu-id="fbc2b-103">When you create a service, you can use a Visual Studio project template called **Windows Service**.</span></span> <span data-ttu-id="fbc2b-104">Tato šablona automaticky provede spoustu práce za vás odkazem na příslušné třídy a obory názvů, nastavením dědičnosti ze základní třídy pro služby a přepsáním několika metod, které pravděpodobně chcete přepsat.</span><span class="sxs-lookup"><span data-stu-id="fbc2b-104">This template automatically does much of the work for you by referencing the appropriate classes and namespaces, setting up the inheritance from the base class for services, and overriding several of the methods you're likely to want to override.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="fbc2b-105">Šablona projektu služby systému Windows není k dispozici v edici Express sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fbc2b-105">The Windows Services project template is not available in the Express edition of Visual Studio.</span></span>  
  
 <span data-ttu-id="fbc2b-106">Aby bylo možné vytvořit funkční službu, musíte:</span><span class="sxs-lookup"><span data-stu-id="fbc2b-106">At a minimum, to create a functional service you must:</span></span>  
  
- <span data-ttu-id="fbc2b-107"><xref:System.ServiceProcess.ServiceBase.ServiceName%2A> Nastavte vlastnost.</span><span class="sxs-lookup"><span data-stu-id="fbc2b-107">Set the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property.</span></span>  
  
- <span data-ttu-id="fbc2b-108">Vytvořte potřebné instalační programy pro aplikaci služby.</span><span class="sxs-lookup"><span data-stu-id="fbc2b-108">Create the necessary installers for your service application.</span></span>  
  
- <span data-ttu-id="fbc2b-109">Přepsat a zadat kód pro <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody a <xref:System.ServiceProcess.ServiceBase.OnStop%2A> pro přizpůsobení způsobů, kterými se vaše služba chová.</span><span class="sxs-lookup"><span data-stu-id="fbc2b-109">Override and specify code for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods to customize the ways in which your service behaves.</span></span>  
  
### <a name="to-create-a-windows-service-application"></a><span data-ttu-id="fbc2b-110">Vytvoření aplikace služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="fbc2b-110">To create a Windows Service application</span></span>  
  
1. <span data-ttu-id="fbc2b-111">Vytvořte projekt **služby systému Windows** .</span><span class="sxs-lookup"><span data-stu-id="fbc2b-111">Create a **Windows Service** project.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="fbc2b-112">Pokyny k zápisu služby bez použití šablony najdete v tématu [How to: Napište služby](../../../docs/framework/windows-services/how-to-write-services-programmatically.md)programově.</span><span class="sxs-lookup"><span data-stu-id="fbc2b-112">For instructions on writing a service without using the template, see [How to: Write Services Programmatically](../../../docs/framework/windows-services/how-to-write-services-programmatically.md).</span></span>  
  
2. <span data-ttu-id="fbc2b-113">V okně **vlastnosti** nastavte <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> vlastnost pro vaši službu.</span><span class="sxs-lookup"><span data-stu-id="fbc2b-113">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for your service.</span></span>  
  
     <span data-ttu-id="fbc2b-114">![Nastavte vlastnost ServiceName.](../../../docs/framework/windows-services/media/windowsservice-servicename.PNG "WindowsService_ServiceName")</span><span class="sxs-lookup"><span data-stu-id="fbc2b-114">![Set the ServiceName property.](../../../docs/framework/windows-services/media/windowsservice-servicename.PNG "WindowsService_ServiceName")</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="fbc2b-115">Hodnota <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> vlastnosti musí vždy odpovídat názvu zaznamenanému v instalačních třídách.</span><span class="sxs-lookup"><span data-stu-id="fbc2b-115">The value of the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property must always match the name recorded in the installer classes.</span></span> <span data-ttu-id="fbc2b-116">Změníte-li tuto vlastnost, je nutné aktualizovat <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> také vlastnost instalačních tříd.</span><span class="sxs-lookup"><span data-stu-id="fbc2b-116">If you change this property, you must update the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property of installer classes as well.</span></span>  
  
3. <span data-ttu-id="fbc2b-117">Nastavením libovolné z následujících vlastností určíte, jak bude služba fungovat.</span><span class="sxs-lookup"><span data-stu-id="fbc2b-117">Set any of the following properties to determine how your service will function.</span></span>  
  
    |<span data-ttu-id="fbc2b-118">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="fbc2b-118">Property</span></span>|<span data-ttu-id="fbc2b-119">Nastavení</span><span class="sxs-lookup"><span data-stu-id="fbc2b-119">Setting</span></span>|  
    |--------------|-------------|  
    |<xref:System.ServiceProcess.ServiceBase.CanStop%2A>|<span data-ttu-id="fbc2b-120">`True`pro indikaci, že služba bude přijímat žádosti o zastavení provozu; `false` zabránit zastavení služby.</span><span class="sxs-lookup"><span data-stu-id="fbc2b-120">`True` to indicate that the service will accept requests to stop running; `false` to prevent the service from being stopped.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanShutdown%2A>|<span data-ttu-id="fbc2b-121">`True`pro indikaci, že služba chce dostávat oznámení, když počítač, ve kterém se nachází, je vypnutý, a umožňuje tak <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> volání procedury.</span><span class="sxs-lookup"><span data-stu-id="fbc2b-121">`True` to indicate that the service wants to receive notification when the computer on which it lives shuts down, enabling it to call the <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> procedure.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A>|<span data-ttu-id="fbc2b-122">`True`pro indikaci, že služba bude přijímat požadavky na pozastavení nebo pokračování v běhu; `false` brání pozastavení a obnovení služby.</span><span class="sxs-lookup"><span data-stu-id="fbc2b-122">`True` to indicate that the service will accept requests to pause or to resume running; `false` to prevent the service from being paused and resumed.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanHandlePowerEvent%2A>|<span data-ttu-id="fbc2b-123">`True`pro indikaci, že služba může zpracovávat oznámení o změnách stavu napájení počítače. `false` brání službě v upozorňování na tyto změny.</span><span class="sxs-lookup"><span data-stu-id="fbc2b-123">`True` to indicate that the service can handle notification of changes to the computer's power status; `false` to prevent the service from being notified of these changes.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.AutoLog%2A>|<span data-ttu-id="fbc2b-124">`True`zápis informativních položek do protokolu událostí aplikace, když vaše služba provádí akci; `false` tuto funkci můžete zakázat.</span><span class="sxs-lookup"><span data-stu-id="fbc2b-124">`True` to write informational entries to the Application event log when your service performs an action; `false` to disable this functionality.</span></span> <span data-ttu-id="fbc2b-125">Další informace najdete v tématu [jak: Protokoluje informace o](../../../docs/framework/windows-services/how-to-log-information-about-services.md)službách.</span><span class="sxs-lookup"><span data-stu-id="fbc2b-125">For more information, see [How to: Log Information About Services](../../../docs/framework/windows-services/how-to-log-information-about-services.md).</span></span> <span data-ttu-id="fbc2b-126">**Poznámka:**  Ve výchozím nastavení <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> je nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="fbc2b-126">**Note:**  By default, <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> is set to `true`.</span></span>|  
  
    > [!NOTE]
    > <span data-ttu-id="fbc2b-127">Pokud <xref:System.ServiceProcess.ServiceBase.CanStop%2A> `false`nebo <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> jsou nastaveny na, **správce řízení služeb** zakáže odpovídající možnosti nabídky pro zastavení, pozastavení nebo pokračování služby.</span><span class="sxs-lookup"><span data-stu-id="fbc2b-127">When <xref:System.ServiceProcess.ServiceBase.CanStop%2A> or <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> are set to `false`, the **Service Control Manager** will disable the corresponding menu options to stop, pause, or continue the service.</span></span>  
  
4. <span data-ttu-id="fbc2b-128">Přihlaste se k editoru kódu a vyplňte požadované zpracování pro <xref:System.ServiceProcess.ServiceBase.OnStart%2A> postupy a. <xref:System.ServiceProcess.ServiceBase.OnStop%2A></span><span class="sxs-lookup"><span data-stu-id="fbc2b-128">Access the Code Editor and fill in the processing you want for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedures.</span></span>  
  
5. <span data-ttu-id="fbc2b-129">Přepište jakékoli jiné metody, pro které chcete definovat funkčnost.</span><span class="sxs-lookup"><span data-stu-id="fbc2b-129">Override any other methods for which you want to define functionality.</span></span>  
  
6. <span data-ttu-id="fbc2b-130">Přidejte nezbytné instalační programy pro aplikaci služby.</span><span class="sxs-lookup"><span data-stu-id="fbc2b-130">Add the necessary installers for your service application.</span></span> <span data-ttu-id="fbc2b-131">Další informace najdete v tématu [jak: Přidejte instalační programy do aplikace](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)služby.</span><span class="sxs-lookup"><span data-stu-id="fbc2b-131">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
7. <span data-ttu-id="fbc2b-132">Sestavte projekt výběrem možnosti **Sestavit řešení** v nabídce **sestavení** .</span><span class="sxs-lookup"><span data-stu-id="fbc2b-132">Build your project by selecting **Build Solution** from the **Build** menu.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="fbc2b-133">Netiskněte klávesu F5 pro spuštění projektu – projekt služby nemůžete tímto způsobem spustit.</span><span class="sxs-lookup"><span data-stu-id="fbc2b-133">Do not press F5 to run your project — you cannot run a service project in this way.</span></span>  
  
8. <span data-ttu-id="fbc2b-134">Nainstalujte službu.</span><span class="sxs-lookup"><span data-stu-id="fbc2b-134">Install the service.</span></span> <span data-ttu-id="fbc2b-135">Další informace najdete v tématu [jak: Nainstalujte a odinstalujte](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)služby.</span><span class="sxs-lookup"><span data-stu-id="fbc2b-135">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbc2b-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fbc2b-136">See also</span></span>

- [<span data-ttu-id="fbc2b-137">Úvod do aplikací služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="fbc2b-137">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [<span data-ttu-id="fbc2b-138">Postupy: Programové psaní služeb</span><span class="sxs-lookup"><span data-stu-id="fbc2b-138">How to: Write Services Programmatically</span></span>](../../../docs/framework/windows-services/how-to-write-services-programmatically.md)
- [<span data-ttu-id="fbc2b-139">Postupy: Přidání instalačních programů do aplikace služby</span><span class="sxs-lookup"><span data-stu-id="fbc2b-139">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="fbc2b-140">Postupy: Protokolovat informace o službách</span><span class="sxs-lookup"><span data-stu-id="fbc2b-140">How to: Log Information About Services</span></span>](../../../docs/framework/windows-services/how-to-log-information-about-services.md)
- [<span data-ttu-id="fbc2b-141">Postupy: Spustit služby</span><span class="sxs-lookup"><span data-stu-id="fbc2b-141">How to: Start Services</span></span>](../../../docs/framework/windows-services/how-to-start-services.md)
- [<span data-ttu-id="fbc2b-142">Postupy: Určení kontextu zabezpečení pro služby</span><span class="sxs-lookup"><span data-stu-id="fbc2b-142">How to: Specify the Security Context for Services</span></span>](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)
- [<span data-ttu-id="fbc2b-143">Postupy: Instalace a odinstalace služeb</span><span class="sxs-lookup"><span data-stu-id="fbc2b-143">How to: Install and Uninstall Services</span></span>](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)
- [<span data-ttu-id="fbc2b-144">Návod: Vytvoření aplikace služby systému Windows v Návrháři součástí</span><span class="sxs-lookup"><span data-stu-id="fbc2b-144">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
