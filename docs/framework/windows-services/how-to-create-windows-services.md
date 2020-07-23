---
title: 'Postupy: Vytváření služeb systému Windows'
description: K vytvoření služby použijte šablonu projektu služby systému Windows. Nastavte vlastnost ServiceName, vytvořte instalační programy a přepište metody OnStart a OnStart.
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, creating
- templates, Windows Service
ms.assetid: 0f5e2cbb-d95d-477c-b2b5-4b990e6b86ff
author: ghogen
ms.openlocfilehash: 6918225e39c15a52710fd0d56342aae869b42325
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925771"
---
# <a name="how-to-create-windows-services"></a><span data-ttu-id="fd6c3-104">Postupy: Vytváření služeb systému Windows</span><span class="sxs-lookup"><span data-stu-id="fd6c3-104">How to: Create Windows Services</span></span>
<span data-ttu-id="fd6c3-105">Při vytváření služby můžete použít šablonu projektu sady Visual Studio s názvem **služba systému Windows**.</span><span class="sxs-lookup"><span data-stu-id="fd6c3-105">When you create a service, you can use a Visual Studio project template called **Windows Service**.</span></span> <span data-ttu-id="fd6c3-106">Tato šablona automaticky provede spoustu práce za vás odkazem na příslušné třídy a obory názvů, nastavením dědičnosti ze základní třídy pro služby a přepsáním několika metod, které pravděpodobně chcete přepsat.</span><span class="sxs-lookup"><span data-stu-id="fd6c3-106">This template automatically does much of the work for you by referencing the appropriate classes and namespaces, setting up the inheritance from the base class for services, and overriding several of the methods you're likely to want to override.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="fd6c3-107">Šablona projektu služby systému Windows není k dispozici v edici Express sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fd6c3-107">The Windows Services project template is not available in the Express edition of Visual Studio.</span></span>  
  
 <span data-ttu-id="fd6c3-108">Aby bylo možné vytvořit funkční službu, musíte:</span><span class="sxs-lookup"><span data-stu-id="fd6c3-108">At a minimum, to create a functional service you must:</span></span>  
  
- <span data-ttu-id="fd6c3-109">Nastavte <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="fd6c3-109">Set the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property.</span></span>  
  
- <span data-ttu-id="fd6c3-110">Vytvořte potřebné instalační programy pro aplikaci služby.</span><span class="sxs-lookup"><span data-stu-id="fd6c3-110">Create the necessary installers for your service application.</span></span>  
  
- <span data-ttu-id="fd6c3-111">Přepsat a zadat kód pro <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody a <xref:System.ServiceProcess.ServiceBase.OnStop%2A> pro přizpůsobení způsobů, kterými se vaše služba chová.</span><span class="sxs-lookup"><span data-stu-id="fd6c3-111">Override and specify code for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods to customize the ways in which your service behaves.</span></span>  
  
### <a name="to-create-a-windows-service-application"></a><span data-ttu-id="fd6c3-112">Vytvoření aplikace služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="fd6c3-112">To create a Windows Service application</span></span>  
  
1. <span data-ttu-id="fd6c3-113">Vytvořte projekt **služby systému Windows** .</span><span class="sxs-lookup"><span data-stu-id="fd6c3-113">Create a **Windows Service** project.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="fd6c3-114">Pokyny k zápisu služby bez použití šablony naleznete v tématu [How to: Write Services Programs](how-to-write-services-programmatically.md).</span><span class="sxs-lookup"><span data-stu-id="fd6c3-114">For instructions on writing a service without using the template, see [How to: Write Services Programmatically](how-to-write-services-programmatically.md).</span></span>  
  
2. <span data-ttu-id="fd6c3-115">V okně **vlastnosti** nastavte <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> vlastnost pro vaši službu.</span><span class="sxs-lookup"><span data-stu-id="fd6c3-115">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for your service.</span></span>  
  
     <span data-ttu-id="fd6c3-116">![Nastavte vlastnost ServiceName.](./media/windowsservice-servicename.PNG "WindowsService_ServiceName")</span><span class="sxs-lookup"><span data-stu-id="fd6c3-116">![Set the ServiceName property.](./media/windowsservice-servicename.PNG "WindowsService_ServiceName")</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="fd6c3-117">Hodnota <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> vlastnosti musí vždy odpovídat názvu zaznamenanému v instalačních třídách.</span><span class="sxs-lookup"><span data-stu-id="fd6c3-117">The value of the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property must always match the name recorded in the installer classes.</span></span> <span data-ttu-id="fd6c3-118">Změníte-li tuto vlastnost, je nutné aktualizovat <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> také vlastnost instalačních tříd.</span><span class="sxs-lookup"><span data-stu-id="fd6c3-118">If you change this property, you must update the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property of installer classes as well.</span></span>  
  
3. <span data-ttu-id="fd6c3-119">Nastavením libovolné z následujících vlastností určíte, jak bude služba fungovat.</span><span class="sxs-lookup"><span data-stu-id="fd6c3-119">Set any of the following properties to determine how your service will function.</span></span>  
  
    |<span data-ttu-id="fd6c3-120">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="fd6c3-120">Property</span></span>|<span data-ttu-id="fd6c3-121">Nastavení</span><span class="sxs-lookup"><span data-stu-id="fd6c3-121">Setting</span></span>|  
    |--------------|-------------|  
    |<xref:System.ServiceProcess.ServiceBase.CanStop%2A>|<span data-ttu-id="fd6c3-122">`True`pro indikaci, že služba bude přijímat žádosti o zastavení provozu; `false`zabránit zastavení služby.</span><span class="sxs-lookup"><span data-stu-id="fd6c3-122">`True` to indicate that the service will accept requests to stop running; `false` to prevent the service from being stopped.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanShutdown%2A>|<span data-ttu-id="fd6c3-123">`True`pro indikaci, že služba chce dostávat oznámení, když počítač, ve kterém se nachází, je vypnutý, a umožňuje tak volání <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> procedury.</span><span class="sxs-lookup"><span data-stu-id="fd6c3-123">`True` to indicate that the service wants to receive notification when the computer on which it lives shuts down, enabling it to call the <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> procedure.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A>|<span data-ttu-id="fd6c3-124">`True`pro indikaci, že služba bude přijímat požadavky na pozastavení nebo pokračování v běhu; `false`brání pozastavení a obnovení služby.</span><span class="sxs-lookup"><span data-stu-id="fd6c3-124">`True` to indicate that the service will accept requests to pause or to resume running; `false` to prevent the service from being paused and resumed.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanHandlePowerEvent%2A>|<span data-ttu-id="fd6c3-125">`True`pro indikaci, že služba může zpracovávat oznámení o změnách stavu napájení počítače. `false`brání službě v upozorňování na tyto změny.</span><span class="sxs-lookup"><span data-stu-id="fd6c3-125">`True` to indicate that the service can handle notification of changes to the computer's power status; `false` to prevent the service from being notified of these changes.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.AutoLog%2A>|<span data-ttu-id="fd6c3-126">`True`zápis informativních položek do protokolu událostí aplikace, když vaše služba provádí akci; `false`tuto funkci můžete zakázat.</span><span class="sxs-lookup"><span data-stu-id="fd6c3-126">`True` to write informational entries to the Application event log when your service performs an action; `false` to disable this functionality.</span></span> <span data-ttu-id="fd6c3-127">Další informace najdete v tématu [Postup: protokolování informací o službách](how-to-log-information-about-services.md).</span><span class="sxs-lookup"><span data-stu-id="fd6c3-127">For more information, see [How to: Log Information About Services](how-to-log-information-about-services.md).</span></span> <span data-ttu-id="fd6c3-128">**Poznámka:**  Ve výchozím nastavení <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> je nastavena na `true` .</span><span class="sxs-lookup"><span data-stu-id="fd6c3-128">**Note:**  By default, <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> is set to `true`.</span></span>|  
  
    > [!NOTE]
    > <span data-ttu-id="fd6c3-129">Pokud <xref:System.ServiceProcess.ServiceBase.CanStop%2A> nebo <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> jsou nastaveny na `false` , **správce řízení služeb** zakáže odpovídající možnosti nabídky pro zastavení, pozastavení nebo pokračování služby.</span><span class="sxs-lookup"><span data-stu-id="fd6c3-129">When <xref:System.ServiceProcess.ServiceBase.CanStop%2A> or <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> are set to `false`, the **Service Control Manager** will disable the corresponding menu options to stop, pause, or continue the service.</span></span>  
  
4. <span data-ttu-id="fd6c3-130">Přihlaste se k editoru kódu a vyplňte požadované zpracování pro <xref:System.ServiceProcess.ServiceBase.OnStart%2A> postupy a <xref:System.ServiceProcess.ServiceBase.OnStop%2A> .</span><span class="sxs-lookup"><span data-stu-id="fd6c3-130">Access the Code Editor and fill in the processing you want for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedures.</span></span>  
  
5. <span data-ttu-id="fd6c3-131">Přepište jakékoli jiné metody, pro které chcete definovat funkčnost.</span><span class="sxs-lookup"><span data-stu-id="fd6c3-131">Override any other methods for which you want to define functionality.</span></span>  
  
6. <span data-ttu-id="fd6c3-132">Přidejte nezbytné instalační programy pro aplikaci služby.</span><span class="sxs-lookup"><span data-stu-id="fd6c3-132">Add the necessary installers for your service application.</span></span> <span data-ttu-id="fd6c3-133">Další informace najdete v tématu [Postup: Přidání instalačních programů do aplikace služby](how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="fd6c3-133">For more information, see [How to: Add Installers to Your Service Application](how-to-add-installers-to-your-service-application.md).</span></span>  
  
7. <span data-ttu-id="fd6c3-134">Sestavte projekt výběrem možnosti **Sestavit řešení** v nabídce **sestavení** .</span><span class="sxs-lookup"><span data-stu-id="fd6c3-134">Build your project by selecting **Build Solution** from the **Build** menu.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="fd6c3-135">Netiskněte klávesu F5 pro spuštění projektu – projekt služby nemůžete tímto způsobem spustit.</span><span class="sxs-lookup"><span data-stu-id="fd6c3-135">Do not press F5 to run your project — you cannot run a service project in this way.</span></span>  
  
8. <span data-ttu-id="fd6c3-136">Nainstalujte službu.</span><span class="sxs-lookup"><span data-stu-id="fd6c3-136">Install the service.</span></span> <span data-ttu-id="fd6c3-137">Další informace najdete v tématu [Postupy: instalace a odinstalace služeb](how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="fd6c3-137">For more information, see [How to: Install and Uninstall Services](how-to-install-and-uninstall-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd6c3-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="fd6c3-138">See also</span></span>

- [<span data-ttu-id="fd6c3-139">Představení aplikací spouštěných jako služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="fd6c3-139">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="fd6c3-140">Postupy: Zápis služeb prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="fd6c3-140">How to: Write Services Programmatically</span></span>](how-to-write-services-programmatically.md)
- [<span data-ttu-id="fd6c3-141">Postupy: Přidání instalačních programů do aplikace služby</span><span class="sxs-lookup"><span data-stu-id="fd6c3-141">How to: Add Installers to Your Service Application</span></span>](how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="fd6c3-142">Postupy: Zaznamenávání informací o službách</span><span class="sxs-lookup"><span data-stu-id="fd6c3-142">How to: Log Information About Services</span></span>](how-to-log-information-about-services.md)
- [<span data-ttu-id="fd6c3-143">Postupy: Spuštění služby</span><span class="sxs-lookup"><span data-stu-id="fd6c3-143">How to: Start Services</span></span>](how-to-start-services.md)
- [<span data-ttu-id="fd6c3-144">Postupy: Určení kontextu zabezpečení pro služby</span><span class="sxs-lookup"><span data-stu-id="fd6c3-144">How to: Specify the Security Context for Services</span></span>](how-to-specify-the-security-context-for-services.md)
- [<span data-ttu-id="fd6c3-145">Postupy: Instalace a odinstalace služeb</span><span class="sxs-lookup"><span data-stu-id="fd6c3-145">How to: Install and Uninstall Services</span></span>](how-to-install-and-uninstall-services.md)
- [<span data-ttu-id="fd6c3-146">Návod: Vytvoření aplikace služby systému Windows v návrháři součástí</span><span class="sxs-lookup"><span data-stu-id="fd6c3-146">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
