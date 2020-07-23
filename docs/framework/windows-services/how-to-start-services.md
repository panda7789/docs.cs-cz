---
title: 'Postupy: Spuštění služby'
description: Podívejte se na několik způsobů, jak spustit služby. Po instalaci služby je nutné ji spustit. Spouští se volání metody OnStart u třídy služby.
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, starting
- services, starting
ms.assetid: 9ea77955-2d96-4c3d-913c-14db7604cdad
author: ghogen
ms.openlocfilehash: 4a2f9b291e60b12b1465fbb6bbbd1604572359a7
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925719"
---
# <a name="how-to-start-services"></a><span data-ttu-id="46bc1-105">Postupy: Spuštění služby</span><span class="sxs-lookup"><span data-stu-id="46bc1-105">How to: Start Services</span></span>

<span data-ttu-id="46bc1-106">Po instalaci služby je nutné ji spustit.</span><span class="sxs-lookup"><span data-stu-id="46bc1-106">After a service is installed, it must be started.</span></span> <span data-ttu-id="46bc1-107">Spouští se volání <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody třídy služby.</span><span class="sxs-lookup"><span data-stu-id="46bc1-107">Starting calls the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method on the service class.</span></span> <span data-ttu-id="46bc1-108"><xref:System.ServiceProcess.ServiceBase.OnStart%2A>Metoda obvykle definuje užitečnou práci, kterou bude služba provádět.</span><span class="sxs-lookup"><span data-stu-id="46bc1-108">Usually, the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method defines the useful work the service will perform.</span></span> <span data-ttu-id="46bc1-109">Po spuštění služby zůstane aktivní, dokud není ručně pozastavená nebo zastavená.</span><span class="sxs-lookup"><span data-stu-id="46bc1-109">After a service starts, it remains active until it is manually paused or stopped.</span></span>

<span data-ttu-id="46bc1-110">Služby je možné nastavit tak, aby se spouštěly automaticky nebo ručně.</span><span class="sxs-lookup"><span data-stu-id="46bc1-110">Services can be set up to start automatically or manually.</span></span> <span data-ttu-id="46bc1-111">Služba, která se spustí automaticky, se spustí při restartování počítače, ve kterém je nainstalovaný, nebo nejdřív zapnutý.</span><span class="sxs-lookup"><span data-stu-id="46bc1-111">A service that starts automatically will be started when the computer on which it is installed is rebooted or first turned on.</span></span> <span data-ttu-id="46bc1-112">Uživatel musí spustit službu, která se spustí ručně.</span><span class="sxs-lookup"><span data-stu-id="46bc1-112">A user must start a service that starts manually.</span></span>

> [!NOTE]
> <span data-ttu-id="46bc1-113">Ve výchozím nastavení se služby vytvořené pomocí sady Visual Studio nastaví tak, aby se spouštěly ručně.</span><span class="sxs-lookup"><span data-stu-id="46bc1-113">By default, services created with Visual Studio are set to start manually.</span></span>

<span data-ttu-id="46bc1-114">Existuje několik způsobů, jak ručně spustit službu – od **Průzkumník serveru**, od **správce řízení služeb**nebo z kódu pomocí komponenty s názvem <xref:System.ServiceProcess.ServiceController> .</span><span class="sxs-lookup"><span data-stu-id="46bc1-114">There are several ways you can manually start a service — from **Server Explorer**, from the **Services Control Manager**, or from code using a component called the <xref:System.ServiceProcess.ServiceController>.</span></span>

<span data-ttu-id="46bc1-115">Nastavením <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> vlastnosti <xref:System.ServiceProcess.ServiceInstaller> třídy určíte, zda má být služba spuštěna ručně nebo automaticky.</span><span class="sxs-lookup"><span data-stu-id="46bc1-115">You set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property on the <xref:System.ServiceProcess.ServiceInstaller> class to determine whether a service should be started manually or automatically.</span></span>

### <a name="to-specify-how-a-service-should-start"></a><span data-ttu-id="46bc1-116">Určení způsobu spuštění služby</span><span class="sxs-lookup"><span data-stu-id="46bc1-116">To specify how a service should start</span></span>

1. <span data-ttu-id="46bc1-117">Po vytvoření služby přidejte pro ni potřebné instalační programy.</span><span class="sxs-lookup"><span data-stu-id="46bc1-117">After creating your service, add the necessary installers for it.</span></span> <span data-ttu-id="46bc1-118">Další informace najdete v tématu [Postup: Přidání instalačních programů do aplikace služby](how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="46bc1-118">For more information, see [How to: Add Installers to Your Service Application](how-to-add-installers-to-your-service-application.md).</span></span>

2. <span data-ttu-id="46bc1-119">V návrháři klikněte na instalační program služby pro službu, se kterou pracujete.</span><span class="sxs-lookup"><span data-stu-id="46bc1-119">In the designer, click the service installer for the service you are working with.</span></span>

3. <span data-ttu-id="46bc1-120">V okně **vlastnosti** nastavte <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> vlastnost na jednu z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="46bc1-120">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to one of the following:</span></span>

    |<span data-ttu-id="46bc1-121">Instalace služby</span><span class="sxs-lookup"><span data-stu-id="46bc1-121">To have your service install</span></span>|<span data-ttu-id="46bc1-122">Nastavit tuto hodnotu</span><span class="sxs-lookup"><span data-stu-id="46bc1-122">Set this value</span></span>|
    |----------------------------------|--------------------|
    |<span data-ttu-id="46bc1-123">Po restartování počítače</span><span class="sxs-lookup"><span data-stu-id="46bc1-123">When the computer is restarted</span></span>|<span data-ttu-id="46bc1-124">**Automaticky**</span><span class="sxs-lookup"><span data-stu-id="46bc1-124">**Automatic**</span></span>|
    |<span data-ttu-id="46bc1-125">Když akce explicitního uživatele spustí službu</span><span class="sxs-lookup"><span data-stu-id="46bc1-125">When an explicit user action starts the service</span></span>|<span data-ttu-id="46bc1-126">**Ruční**</span><span class="sxs-lookup"><span data-stu-id="46bc1-126">**Manual**</span></span>|

    > [!TIP]
    > <span data-ttu-id="46bc1-127">Pokud chcete zabránit tomu, aby se služba spustila vůbec, můžete vlastnost nastavit <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> na **zakázáno**.</span><span class="sxs-lookup"><span data-stu-id="46bc1-127">To prevent your service from being started at all, you can set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to **Disabled**.</span></span> <span data-ttu-id="46bc1-128">To můžete provést, pokud budete Server několikrát restartovat a chcete ušetřit čas tím, že znemožníte službám, které by normálně začaly začít.</span><span class="sxs-lookup"><span data-stu-id="46bc1-128">You might do this if you are going to reboot a server several times and want to save time by preventing the services that would normally start from starting up.</span></span>

    > [!NOTE]
    > <span data-ttu-id="46bc1-129">Tyto a další vlastnosti se dají po instalaci služby změnit.</span><span class="sxs-lookup"><span data-stu-id="46bc1-129">These and other properties can be changed after your service is installed.</span></span>

    <span data-ttu-id="46bc1-130">Existuje několik způsobů, jak můžete spustit službu, která má svůj <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> proces nastavený na **Ruční** – od **Průzkumník serveru**, od **správce řízení služeb systému Windows**nebo z kódu.</span><span class="sxs-lookup"><span data-stu-id="46bc1-130">There are several ways you can start a service that has its <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> process set to **Manual** — from **Server Explorer**, from the **Windows Services Control Manager**, or from code.</span></span> <span data-ttu-id="46bc1-131">Je důležité si uvědomit, že ne všechny tyto metody ve skutečnosti zahájí službu v kontextu **správce řízení služeb**; **Průzkumník serveru** a programové metody spuštění služby skutečně manipulují s řadičem.</span><span class="sxs-lookup"><span data-stu-id="46bc1-131">It is important to note that not all of these methods actually start the service in the context of the **Services Control Manager**; **Server Explorer** and programmatic methods of starting the service actually manipulate the controller.</span></span>

### <a name="to-manually-start-a-service-from-server-explorer"></a><span data-ttu-id="46bc1-132">Ruční spuštění služby z Průzkumník serveru</span><span class="sxs-lookup"><span data-stu-id="46bc1-132">To manually start a service from Server Explorer</span></span>

1. <span data-ttu-id="46bc1-133">V **Průzkumník serveru**přidejte server, který chcete, pokud již není uveden.</span><span class="sxs-lookup"><span data-stu-id="46bc1-133">In **Server Explorer**, add the server you want if it is not already listed.</span></span> <span data-ttu-id="46bc1-134">Další informace naleznete v tématu How to: Access and Initialize Průzkumník serveru-Database Explorer.</span><span class="sxs-lookup"><span data-stu-id="46bc1-134">For more information, see How to: Access and Initialize Server Explorer-Database Explorer.</span></span>

2. <span data-ttu-id="46bc1-135">Rozbalte uzel **služby** a vyhledejte službu, kterou chcete spustit.</span><span class="sxs-lookup"><span data-stu-id="46bc1-135">Expand the **Services** node, and then locate the service you want to start.</span></span>

3. <span data-ttu-id="46bc1-136">Klikněte pravým tlačítkem na název služby a pak klikněte na **Spustit**.</span><span class="sxs-lookup"><span data-stu-id="46bc1-136">Right-click the name of the service, and click **Start**.</span></span>

### <a name="to-manually-start-a-service-from-services-control-manager"></a><span data-ttu-id="46bc1-137">Ruční spuštění služby ze Správce řízení služeb</span><span class="sxs-lookup"><span data-stu-id="46bc1-137">To manually start a service from Services Control Manager</span></span>

1. <span data-ttu-id="46bc1-138">Pomocí jedné z následujících akcí otevřete **správce řízení služeb** :</span><span class="sxs-lookup"><span data-stu-id="46bc1-138">Open the **Services Control Manager** by doing one of the following:</span></span>

    - <span data-ttu-id="46bc1-139">V systému Windows XP a 2000 Professional klikněte pravým tlačítkem na položku **Tento počítač** na ploše a pak klikněte na možnost **Spravovat**.</span><span class="sxs-lookup"><span data-stu-id="46bc1-139">In Windows XP and 2000 Professional, right-click **My Computer** on the desktop, and then click **Manage**.</span></span> <span data-ttu-id="46bc1-140">V dialogovém okně, které se zobrazí, rozbalte uzel **služby a aplikace** .</span><span class="sxs-lookup"><span data-stu-id="46bc1-140">In the dialog box that appears, expand the **Services and Applications** node.</span></span>

      <span data-ttu-id="46bc1-141">\-ani</span><span class="sxs-lookup"><span data-stu-id="46bc1-141">\- or -</span></span>

    - <span data-ttu-id="46bc1-142">V systému Windows Server 2003 a Windows 2000 Server klikněte na **Start**, přejděte na **programy**, klikněte na **Nástroje pro správu**a potom klikněte na **služby**.</span><span class="sxs-lookup"><span data-stu-id="46bc1-142">In Windows Server 2003 and Windows 2000 Server, click **Start**, point to **Programs**, click **Administrative Tools**, and then click **Services**.</span></span>

      > [!NOTE]
      > <span data-ttu-id="46bc1-143">V systému Windows NT verze 4,0 můžete toto dialogové okno otevřít z **ovládacích panelů**.</span><span class="sxs-lookup"><span data-stu-id="46bc1-143">In Windows NT version 4.0, you can open this dialog box from **Control Panel**.</span></span>

    <span data-ttu-id="46bc1-144">Teď by se měla zobrazit vaše služba uvedená v části **služby** v okně.</span><span class="sxs-lookup"><span data-stu-id="46bc1-144">You should now see your service listed in the **Services** section of the window.</span></span>

2. <span data-ttu-id="46bc1-145">V seznamu vyberte svou službu, klikněte na ni pravým tlačítkem myši a pak klikněte na **Spustit**.</span><span class="sxs-lookup"><span data-stu-id="46bc1-145">Select your service in the list, right-click it, and then click **Start**.</span></span>

### <a name="to-manually-start-a-service-from-code"></a><span data-ttu-id="46bc1-146">Ruční spuštění služby z kódu</span><span class="sxs-lookup"><span data-stu-id="46bc1-146">To manually start a service from code</span></span>

1. <span data-ttu-id="46bc1-147">Vytvořte instanci <xref:System.ServiceProcess.ServiceController> třídy a nakonfigurujte ji pro interakci se službou, kterou chcete spravovat.</span><span class="sxs-lookup"><span data-stu-id="46bc1-147">Create an instance of the <xref:System.ServiceProcess.ServiceController> class, and configure it to interact with the service you want to administer.</span></span>

2. <span data-ttu-id="46bc1-148">Zavolejte <xref:System.ServiceProcess.ServiceController.Start%2A> metodu pro spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="46bc1-148">Call the <xref:System.ServiceProcess.ServiceController.Start%2A> method to start the service.</span></span>

## <a name="see-also"></a><span data-ttu-id="46bc1-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="46bc1-149">See also</span></span>

- [<span data-ttu-id="46bc1-150">Představení aplikací spouštěných jako služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="46bc1-150">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="46bc1-151">Postupy: Vytváření služeb systému Windows</span><span class="sxs-lookup"><span data-stu-id="46bc1-151">How to: Create Windows Services</span></span>](how-to-create-windows-services.md)
- [<span data-ttu-id="46bc1-152">Postupy: Přidání instalačních programů do aplikace služby</span><span class="sxs-lookup"><span data-stu-id="46bc1-152">How to: Add Installers to Your Service Application</span></span>](how-to-add-installers-to-your-service-application.md)
