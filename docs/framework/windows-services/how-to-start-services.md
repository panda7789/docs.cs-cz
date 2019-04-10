---
title: 'Postupy: Spuštění služby'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, starting
- services, starting
ms.assetid: 9ea77955-2d96-4c3d-913c-14db7604cdad
author: ghogen
ms.openlocfilehash: db66e8a264bc0381a2ff4689c4427047a158eb32
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59336834"
---
# <a name="how-to-start-services"></a><span data-ttu-id="ecdd9-102">Postupy: Spuštění služby</span><span class="sxs-lookup"><span data-stu-id="ecdd9-102">How to: Start Services</span></span>
<span data-ttu-id="ecdd9-103">Po dokončení instalace služby musí být spuštěna.</span><span class="sxs-lookup"><span data-stu-id="ecdd9-103">After a service is installed, it must be started.</span></span> <span data-ttu-id="ecdd9-104">Od volání <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodu na třídu služby.</span><span class="sxs-lookup"><span data-stu-id="ecdd9-104">Starting calls the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method on the service class.</span></span> <span data-ttu-id="ecdd9-105">Obvykle <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda definuje užitečnou práci, služba bude provádět.</span><span class="sxs-lookup"><span data-stu-id="ecdd9-105">Usually, the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method defines the useful work the service will perform.</span></span> <span data-ttu-id="ecdd9-106">Po spuštění služby, zůstane aktivní, dokud je ručně pozastavená nebo zastavená.</span><span class="sxs-lookup"><span data-stu-id="ecdd9-106">After a service starts, it remains active until it is manually paused or stopped.</span></span>  
  
 <span data-ttu-id="ecdd9-107">Služby můžete nastavit spustit automaticky nebo ručně.</span><span class="sxs-lookup"><span data-stu-id="ecdd9-107">Services can be set up to start automatically or manually.</span></span> <span data-ttu-id="ecdd9-108">Služba, která se spustí automaticky spustí se při restartování nebo počítače, na kterém je nainstalovaný se nejprve zapnuté.</span><span class="sxs-lookup"><span data-stu-id="ecdd9-108">A service that starts automatically will be started when the computer on which it is installed is rebooted or first turned on.</span></span> <span data-ttu-id="ecdd9-109">Uživatel musí spustit služba, která se spouští ručně.</span><span class="sxs-lookup"><span data-stu-id="ecdd9-109">A user must start a service that starts manually.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ecdd9-110">Ve výchozím nastavení služby vytvořené pomocí sady Visual Studio jsou nastaveny na Manuální spuštění.</span><span class="sxs-lookup"><span data-stu-id="ecdd9-110">By default, services created with Visual Studio are set to start manually.</span></span>  
  
 <span data-ttu-id="ecdd9-111">Službu můžete ručně spustit několika způsoby – z **Průzkumníka serveru**, z **správce řízení služeb**, nebo z kódu pomocí komponentu volána <xref:System.ServiceProcess.ServiceController>.</span><span class="sxs-lookup"><span data-stu-id="ecdd9-111">There are several ways you can manually start a service — from **Server Explorer**, from the **Services Control Manager**, or from code using a component called the <xref:System.ServiceProcess.ServiceController>.</span></span>  
  
 <span data-ttu-id="ecdd9-112">Můžete nastavit <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> vlastnost <xref:System.ServiceProcess.ServiceInstaller> třídu k určení, zda by měl službu spustit ručně nebo automaticky.</span><span class="sxs-lookup"><span data-stu-id="ecdd9-112">You set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property on the <xref:System.ServiceProcess.ServiceInstaller> class to determine whether a service should be started manually or automatically.</span></span>  
  
### <a name="to-specify-how-a-service-should-start"></a><span data-ttu-id="ecdd9-113">Chcete-li určit, jak by měl spustit službu</span><span class="sxs-lookup"><span data-stu-id="ecdd9-113">To specify how a service should start</span></span>  
  
1. <span data-ttu-id="ecdd9-114">Po vytvoření vaší služby, přidejte nezbytné instalační programy pro něj.</span><span class="sxs-lookup"><span data-stu-id="ecdd9-114">After creating your service, add the necessary installers for it.</span></span> <span data-ttu-id="ecdd9-115">Další informace najdete v tématu [jak: Přidání instalačních programů do aplikace služby](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="ecdd9-115">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
2. <span data-ttu-id="ecdd9-116">V Návrháři klikněte na instalační program služby pro službu, kterou pracujete.</span><span class="sxs-lookup"><span data-stu-id="ecdd9-116">In the designer, click the service installer for the service you are working with.</span></span>  
  
3. <span data-ttu-id="ecdd9-117">V **vlastnosti** okno, nastaveno <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> vlastnost na jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="ecdd9-117">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to one of the following:</span></span>  
  
    |<span data-ttu-id="ecdd9-118">Služba instalace</span><span class="sxs-lookup"><span data-stu-id="ecdd9-118">To have your service install</span></span>|<span data-ttu-id="ecdd9-119">Nastavte tuto hodnotu</span><span class="sxs-lookup"><span data-stu-id="ecdd9-119">Set this value</span></span>|  
    |----------------------------------|--------------------|  
    |<span data-ttu-id="ecdd9-120">Po restartování počítače</span><span class="sxs-lookup"><span data-stu-id="ecdd9-120">When the computer is restarted</span></span>|**<span data-ttu-id="ecdd9-121">Automatické</span><span class="sxs-lookup"><span data-stu-id="ecdd9-121">Automatic</span></span>**|  
    |<span data-ttu-id="ecdd9-122">Při spuštění akce explicitní uživatel služby</span><span class="sxs-lookup"><span data-stu-id="ecdd9-122">When an explicit user action starts the service</span></span>|**<span data-ttu-id="ecdd9-123">Ruční</span><span class="sxs-lookup"><span data-stu-id="ecdd9-123">Manual</span></span>**|  
  
    > [!TIP]
    >  <span data-ttu-id="ecdd9-124">Chcete-li zabránit spuštění vůbec vaši službu, můžete nastavit <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> vlastnost **zakázané**.</span><span class="sxs-lookup"><span data-stu-id="ecdd9-124">To prevent your service from being started at all, you can set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to **Disabled**.</span></span> <span data-ttu-id="ecdd9-125">To může provést, pokud se chystáte několikrát restartuje server a chcete ušetřit čas tím, že zabráníte služby, které by normálně spustit spuštění.</span><span class="sxs-lookup"><span data-stu-id="ecdd9-125">You might do this if you are going to reboot a server several times and want to save time by preventing the services that would normally start from starting up.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ecdd9-126">Po instalaci služby lze změnit tyto a další vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ecdd9-126">These and other properties can be changed after your service is installed.</span></span>  
  
     <span data-ttu-id="ecdd9-127">Existuje několik způsobů, jak můžete spustit službu, která má jeho <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> procesu nastavena na **ruční** – od **Průzkumníka serveru**, z **správce řízení služeb Windows**, nebo z kódu.</span><span class="sxs-lookup"><span data-stu-id="ecdd9-127">There are several ways you can start a service that has its <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> process set to **Manual** — from **Server Explorer**, from the **Windows Services Control Manager**, or from code.</span></span> <span data-ttu-id="ecdd9-128">Je důležité si uvědomit, že některé z těchto metod ve skutečnosti spustit službu v kontextu **správce řízení služeb**; **Průzkumníka serveru** a programové metody spouštění služby ve skutečnosti manipulaci s řadičem.</span><span class="sxs-lookup"><span data-stu-id="ecdd9-128">It is important to note that not all of these methods actually start the service in the context of the **Services Control Manager**; **Server Explorer** and programmatic methods of starting the service actually manipulate the controller.</span></span>  
  
### <a name="to-manually-start-a-service-from-server-explorer"></a><span data-ttu-id="ecdd9-129">Chcete-li službu spustit ručně z Průzkumníka serveru</span><span class="sxs-lookup"><span data-stu-id="ecdd9-129">To manually start a service from Server Explorer</span></span>  
  
1. <span data-ttu-id="ecdd9-130">V **Průzkumníka serveru**, přidání serveru, je-li dosud není uložen.</span><span class="sxs-lookup"><span data-stu-id="ecdd9-130">In **Server Explorer**, add the server you want if it is not already listed.</span></span> <span data-ttu-id="ecdd9-131">Další informace najdete v tématu Postupy: Přístup a inicializace Průzkumníka serveru Průzkumníka databáze.</span><span class="sxs-lookup"><span data-stu-id="ecdd9-131">For more information, see How to: Access and Initialize Server Explorer-Database Explorer.</span></span>  
  
2. <span data-ttu-id="ecdd9-132">Rozbalte **služby** uzel a pak vyhledejte service, které chcete spustit.</span><span class="sxs-lookup"><span data-stu-id="ecdd9-132">Expand the **Services** node, and then locate the service you want to start.</span></span>  
  
3. <span data-ttu-id="ecdd9-133">Klikněte pravým tlačítkem na název služby a klikněte na tlačítko **Start**.</span><span class="sxs-lookup"><span data-stu-id="ecdd9-133">Right-click the name of the service, and click **Start**.</span></span>  
  
### <a name="to-manually-start-a-service-from-services-control-manager"></a><span data-ttu-id="ecdd9-134">Ruční spuštění služby od správce řízení služeb</span><span class="sxs-lookup"><span data-stu-id="ecdd9-134">To manually start a service from Services Control Manager</span></span>  
  
1. <span data-ttu-id="ecdd9-135">Otevřít **správce řízení služeb** pomocí jedné z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="ecdd9-135">Open the **Services Control Manager** by doing one of the following:</span></span>  
  
    -   <span data-ttu-id="ecdd9-136">V systémech Windows XP a 2000 Professional, klikněte pravým tlačítkem na **tento počítač** na ploše a pak klikněte na tlačítko **spravovat**.</span><span class="sxs-lookup"><span data-stu-id="ecdd9-136">In Windows XP and 2000 Professional, right-click **My Computer** on the desktop, and then click **Manage**.</span></span> <span data-ttu-id="ecdd9-137">V dialogovém okně, které se zobrazí, rozbalte **služeb a aplikací** uzlu.</span><span class="sxs-lookup"><span data-stu-id="ecdd9-137">In the dialog box that appears, expand the **Services and Applications** node.</span></span>  
  
         <span data-ttu-id="ecdd9-138">\- nebo –</span><span class="sxs-lookup"><span data-stu-id="ecdd9-138">\- or -</span></span>  
  
    -   <span data-ttu-id="ecdd9-139">V systému Windows Server 2003 a Windows 2000 Server, klikněte na tlačítko **Start**, přejděte na **programy**, klikněte na tlačítko **nástroje pro správu**a potom klikněte na tlačítko **služby**.</span><span class="sxs-lookup"><span data-stu-id="ecdd9-139">In Windows Server 2003 and Windows 2000 Server, click **Start**, point to **Programs**, click **Administrative Tools**, and then click **Services**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="ecdd9-140">V systému Windows NT verze 4.0, můžete otevřít toto dialogové z **ovládací panely**.</span><span class="sxs-lookup"><span data-stu-id="ecdd9-140">In Windows NT version 4.0, you can open this dialog box from **Control Panel**.</span></span>  
  
     <span data-ttu-id="ecdd9-141">Teď byste měli vidět vaše služba uvedená v **služby** části okna.</span><span class="sxs-lookup"><span data-stu-id="ecdd9-141">You should now see your service listed in the **Services** section of the window.</span></span>  
  
2. <span data-ttu-id="ecdd9-142">Vyberte svoji službu v seznamu pravým tlačítkem myši a potom klikněte na tlačítko **Start**.</span><span class="sxs-lookup"><span data-stu-id="ecdd9-142">Select your service in the list, right-click it, and then click **Start**.</span></span>  
  
### <a name="to-manually-start-a-service-from-code"></a><span data-ttu-id="ecdd9-143">Chcete-li službu spustit ručně z kódu</span><span class="sxs-lookup"><span data-stu-id="ecdd9-143">To manually start a service from code</span></span>  
  
1. <span data-ttu-id="ecdd9-144">Vytvoření instance <xref:System.ServiceProcess.ServiceController> třídy a jeho konfigurace pro interakci se službou, kterou chcete spravovat.</span><span class="sxs-lookup"><span data-stu-id="ecdd9-144">Create an instance of the <xref:System.ServiceProcess.ServiceController> class, and configure it to interact with the service you want to administer.</span></span>  
  
2. <span data-ttu-id="ecdd9-145">Volání <xref:System.ServiceProcess.ServiceController.Start%2A> metoda ke spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="ecdd9-145">Call the <xref:System.ServiceProcess.ServiceController.Start%2A> method to start the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecdd9-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ecdd9-146">See also</span></span>

- [<span data-ttu-id="ecdd9-147">Představení aplikací spouštěných jako služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="ecdd9-147">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [<span data-ttu-id="ecdd9-148">Postupy: Vytváření služeb systému Windows</span><span class="sxs-lookup"><span data-stu-id="ecdd9-148">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)
- [<span data-ttu-id="ecdd9-149">Postupy: Přidání instalačních programů do aplikace služby</span><span class="sxs-lookup"><span data-stu-id="ecdd9-149">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
