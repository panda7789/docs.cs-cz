---
title: "Postupy: Spuštění služeb"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Service applications, starting
- services, starting
ms.assetid: 9ea77955-2d96-4c3d-913c-14db7604cdad
caps.latest.revision: "16"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 8352edaa9386adc1fbf3057c6e98f5a9cf9ce4a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-start-services"></a><span data-ttu-id="77087-102">Postupy: Spuštění služeb</span><span class="sxs-lookup"><span data-stu-id="77087-102">How to: Start Services</span></span>
<span data-ttu-id="77087-103">Po instalaci služby musí být spuštěna.</span><span class="sxs-lookup"><span data-stu-id="77087-103">After a service is installed, it must be started.</span></span> <span data-ttu-id="77087-104">Počáteční počet volání <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodu v třídě služby.</span><span class="sxs-lookup"><span data-stu-id="77087-104">Starting calls the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method on the service class.</span></span> <span data-ttu-id="77087-105">Obvykle <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda definuje užitečné pracovní službu provede.</span><span class="sxs-lookup"><span data-stu-id="77087-105">Usually, the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method defines the useful work the service will perform.</span></span> <span data-ttu-id="77087-106">Po spuštění služby, zůstane aktivní, dokud je ručně pozastavená nebo zastavená.</span><span class="sxs-lookup"><span data-stu-id="77087-106">After a service starts, it remains active until it is manually paused or stopped.</span></span>  
  
 <span data-ttu-id="77087-107">Služby můžete nastavit spustit automaticky nebo ručně.</span><span class="sxs-lookup"><span data-stu-id="77087-107">Services can be set up to start automatically or manually.</span></span> <span data-ttu-id="77087-108">Služba, která spouští se automaticky spustila, když je počítač, ve kterém je nainstalován restartoval nebo nejprve zapnutý.</span><span class="sxs-lookup"><span data-stu-id="77087-108">A service that starts automatically will be started when the computer on which it is installed is rebooted or first turned on.</span></span> <span data-ttu-id="77087-109">Uživatel musí spustit službu, která spustí ručně.</span><span class="sxs-lookup"><span data-stu-id="77087-109">A user must start a service that starts manually.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="77087-110">Ve výchozím nastavení vytvoří služby s [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] jsou nastavená na ruční spouštění.</span><span class="sxs-lookup"><span data-stu-id="77087-110">By default, services created with [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] are set to start manually.</span></span>  
  
 <span data-ttu-id="77087-111">Existuje několik způsobů, můžete ručně spustit službu – z **Průzkumníka serveru**, z **správci řízení služeb**, nebo pomocí součásti volat z kódu <xref:System.ServiceProcess.ServiceController>.</span><span class="sxs-lookup"><span data-stu-id="77087-111">There are several ways you can manually start a service — from **Server Explorer**, from the **Services Control Manager**, or from code using a component called the <xref:System.ServiceProcess.ServiceController>.</span></span>  
  
 <span data-ttu-id="77087-112">Můžete nastavit <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> vlastnost <xref:System.ServiceProcess.ServiceInstaller> třídu k určení, zda by měl službu spustit ručně nebo automaticky.</span><span class="sxs-lookup"><span data-stu-id="77087-112">You set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property on the <xref:System.ServiceProcess.ServiceInstaller> class to determine whether a service should be started manually or automatically.</span></span>  
  
### <a name="to-specify-how-a-service-should-start"></a><span data-ttu-id="77087-113">K určení toho, jak služba by se měl spustit</span><span class="sxs-lookup"><span data-stu-id="77087-113">To specify how a service should start</span></span>  
  
1.  <span data-ttu-id="77087-114">Po vytvoření služby, přidejte potřebné instalační programy pro ni.</span><span class="sxs-lookup"><span data-stu-id="77087-114">After creating your service, add the necessary installers for it.</span></span> <span data-ttu-id="77087-115">Další informace najdete v tématu [postupy: Přidání instalačních programů pro vaše aplikace služby](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="77087-115">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
2.  <span data-ttu-id="77087-116">V Návrháři klikněte na instalační program služby pro službu, kterou pracujete.</span><span class="sxs-lookup"><span data-stu-id="77087-116">In the designer, click the service installer for the service you are working with.</span></span>  
  
3.  <span data-ttu-id="77087-117">V **vlastnosti** nastavte <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> vlastnost na jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="77087-117">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to one of the following:</span></span>  
  
    |<span data-ttu-id="77087-118">Služba instalace</span><span class="sxs-lookup"><span data-stu-id="77087-118">To have your service install</span></span>|<span data-ttu-id="77087-119">Nastavení této hodnoty</span><span class="sxs-lookup"><span data-stu-id="77087-119">Set this value</span></span>|  
    |----------------------------------|--------------------|  
    |<span data-ttu-id="77087-120">Při restartování počítače</span><span class="sxs-lookup"><span data-stu-id="77087-120">When the computer is restarted</span></span>|<span data-ttu-id="77087-121">**Automatické**</span><span class="sxs-lookup"><span data-stu-id="77087-121">**Automatic**</span></span>|  
    |<span data-ttu-id="77087-122">Když akce explicitní uživatel spustí službu</span><span class="sxs-lookup"><span data-stu-id="77087-122">When an explicit user action starts the service</span></span>|<span data-ttu-id="77087-123">**Ruční**</span><span class="sxs-lookup"><span data-stu-id="77087-123">**Manual**</span></span>|  
  
    > [!TIP]
    >  <span data-ttu-id="77087-124">Chcete-li zabránit spuštění vůbec služby, můžete nastavit <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> vlastnost **zakázané**.</span><span class="sxs-lookup"><span data-stu-id="77087-124">To prevent your service from being started at all, you can set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to **Disabled**.</span></span> <span data-ttu-id="77087-125">To třeba udělat, pokud se chystáte restartovat server několikrát a chcete ušetřit čas tím, že služby, které by normálně spustit spuštění.</span><span class="sxs-lookup"><span data-stu-id="77087-125">You might do this if you are going to reboot a server several times and want to save time by preventing the services that would normally start from starting up.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="77087-126">Tyto a další vlastnosti můžete změnit po instalaci služby.</span><span class="sxs-lookup"><span data-stu-id="77087-126">These and other properties can be changed after your service is installed.</span></span>  
  
     <span data-ttu-id="77087-127">Existuje několik způsobů, můžete spustit službu, která má jeho <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> proces nastaven na **ruční** – z **Průzkumníka serveru**, z **správci řízení služeb systému Windows**, nebo z kódu.</span><span class="sxs-lookup"><span data-stu-id="77087-127">There are several ways you can start a service that has its <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> process set to **Manual** — from **Server Explorer**, from the **Windows Services Control Manager**, or from code.</span></span> <span data-ttu-id="77087-128">Je důležité si uvědomit, ne všechny tyto metody ve skutečnosti spusťte službu v kontextu **správci řízení služeb**; **Průzkumníka serveru** a programové metody spouštění služby ve skutečnosti manipulaci kontroleru.</span><span class="sxs-lookup"><span data-stu-id="77087-128">It is important to note that not all of these methods actually start the service in the context of the **Services Control Manager**; **Server Explorer** and programmatic methods of starting the service actually manipulate the controller.</span></span>  
  
### <a name="to-manually-start-a-service-from-server-explorer"></a><span data-ttu-id="77087-129">Chcete-li službu spustit ručně z Průzkumníka serveru</span><span class="sxs-lookup"><span data-stu-id="77087-129">To manually start a service from Server Explorer</span></span>  
  
1.  <span data-ttu-id="77087-130">V **Průzkumníka serveru**, přidejte server, je-li již není uveden.</span><span class="sxs-lookup"><span data-stu-id="77087-130">In **Server Explorer**, add the server you want if it is not already listed.</span></span> <span data-ttu-id="77087-131">Další informace najdete v tématu Postupy: přístup a inicializaci Průzkumníka databáze Průzkumníka serveru.</span><span class="sxs-lookup"><span data-stu-id="77087-131">For more information, see How to: Access and Initialize Server Explorer-Database Explorer.</span></span>  
  
2.  <span data-ttu-id="77087-132">Rozbalte **služby** uzel a vyhledejte službu, kterou chcete spustit.</span><span class="sxs-lookup"><span data-stu-id="77087-132">Expand the **Services** node, and then locate the service you want to start.</span></span>  
  
3.  <span data-ttu-id="77087-133">Klikněte pravým tlačítkem na název služby a klikněte na tlačítko **spustit**.</span><span class="sxs-lookup"><span data-stu-id="77087-133">Right-click the name of the service, and click **Start**.</span></span>  
  
### <a name="to-manually-start-a-service-from-services-control-manager"></a><span data-ttu-id="77087-134">Ručně spustit službu ze Správce řízení služeb</span><span class="sxs-lookup"><span data-stu-id="77087-134">To manually start a service from Services Control Manager</span></span>  
  
1.  <span data-ttu-id="77087-135">Otevřete **správci řízení služeb** jedním z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="77087-135">Open the **Services Control Manager** by doing one of the following:</span></span>  
  
    -   <span data-ttu-id="77087-136">V systému Windows XP a 2000 Professional, klikněte pravým tlačítkem na **Můj počítač** na ploše a pak klikněte na tlačítko **spravovat**.</span><span class="sxs-lookup"><span data-stu-id="77087-136">In Windows XP and 2000 Professional, right-click **My Computer** on the desktop, and then click **Manage**.</span></span> <span data-ttu-id="77087-137">V dialogovém okně, které se zobrazí, rozbalte **služeb a aplikací** uzlu.</span><span class="sxs-lookup"><span data-stu-id="77087-137">In the dialog box that appears, expand the **Services and Applications** node.</span></span>  
  
         <span data-ttu-id="77087-138">\-nebo –</span><span class="sxs-lookup"><span data-stu-id="77087-138">\- or -</span></span>  
  
    -   <span data-ttu-id="77087-139">V systému Windows Server 2003 a Windows 2000 Server, klikněte na **spustit**, přejděte na příkaz **programy**, klikněte na tlačítko **nástroje pro správu**a pak klikněte na tlačítko **služby**.</span><span class="sxs-lookup"><span data-stu-id="77087-139">In Windows Server 2003 and Windows 2000 Server, click **Start**, point to **Programs**, click **Administrative Tools**, and then click **Services**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="77087-140">V systému Windows NT verze 4.0, můžete otevřít dialogové okno z **ovládací panely**.</span><span class="sxs-lookup"><span data-stu-id="77087-140">In Windows NT version 4.0, you can open this dialog box from **Control Panel**.</span></span>  
  
     <span data-ttu-id="77087-141">Teď byste měli vidět služby uvedené v **služby** části okna.</span><span class="sxs-lookup"><span data-stu-id="77087-141">You should now see your service listed in the **Services** section of the window.</span></span>  
  
2.  <span data-ttu-id="77087-142">V seznamu vyberte služby, klikněte pravým tlačítkem ji a pak klikněte na tlačítko **spustit**.</span><span class="sxs-lookup"><span data-stu-id="77087-142">Select your service in the list, right-click it, and then click **Start**.</span></span>  
  
### <a name="to-manually-start-a-service-from-code"></a><span data-ttu-id="77087-143">Chcete-li službu spustit ručně z kódu</span><span class="sxs-lookup"><span data-stu-id="77087-143">To manually start a service from code</span></span>  
  
1.  <span data-ttu-id="77087-144">Vytvoření instance <xref:System.ServiceProcess.ServiceController> třídy a nakonfigurovat ji pro interakci s službou, které chcete spravovat.</span><span class="sxs-lookup"><span data-stu-id="77087-144">Create an instance of the <xref:System.ServiceProcess.ServiceController> class, and configure it to interact with the service you want to administer.</span></span>  
  
2.  <span data-ttu-id="77087-145">Volání <xref:System.ServiceProcess.ServiceController.Start%2A> metoda spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="77087-145">Call the <xref:System.ServiceProcess.ServiceController.Start%2A> method to start the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77087-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="77087-146">See Also</span></span>  
 [<span data-ttu-id="77087-147">Úvod do aplikací služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="77087-147">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="77087-148">Postupy: Vytváření služeb systému Windows</span><span class="sxs-lookup"><span data-stu-id="77087-148">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [<span data-ttu-id="77087-149">Postupy: Přidání instalačních programů do aplikace služby</span><span class="sxs-lookup"><span data-stu-id="77087-149">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
