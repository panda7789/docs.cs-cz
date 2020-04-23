---
title: 'Postupy: Spuštění služeb'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, starting
- services, starting
ms.assetid: 9ea77955-2d96-4c3d-913c-14db7604cdad
author: ghogen
ms.openlocfilehash: 75fd3aba88bdffbe536ad5dab14996913d0a9d22
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053575"
---
# <a name="how-to-start-services"></a><span data-ttu-id="28b07-102">Postupy: Spuštění služeb</span><span class="sxs-lookup"><span data-stu-id="28b07-102">How to: Start Services</span></span>

<span data-ttu-id="28b07-103">Po instalaci služby je nutné ji spustit.</span><span class="sxs-lookup"><span data-stu-id="28b07-103">After a service is installed, it must be started.</span></span> <span data-ttu-id="28b07-104">Spouští se <xref:System.ServiceProcess.ServiceBase.OnStart%2A> volání metody třídy služby.</span><span class="sxs-lookup"><span data-stu-id="28b07-104">Starting calls the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method on the service class.</span></span> <span data-ttu-id="28b07-105"><xref:System.ServiceProcess.ServiceBase.OnStart%2A> Metoda obvykle definuje užitečnou práci, kterou bude služba provádět.</span><span class="sxs-lookup"><span data-stu-id="28b07-105">Usually, the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method defines the useful work the service will perform.</span></span> <span data-ttu-id="28b07-106">Po spuštění služby zůstane aktivní, dokud není ručně pozastavená nebo zastavená.</span><span class="sxs-lookup"><span data-stu-id="28b07-106">After a service starts, it remains active until it is manually paused or stopped.</span></span>

<span data-ttu-id="28b07-107">Služby je možné nastavit tak, aby se spouštěly automaticky nebo ručně.</span><span class="sxs-lookup"><span data-stu-id="28b07-107">Services can be set up to start automatically or manually.</span></span> <span data-ttu-id="28b07-108">Služba, která se spustí automaticky, se spustí při restartování počítače, ve kterém je nainstalovaný, nebo nejdřív zapnutý.</span><span class="sxs-lookup"><span data-stu-id="28b07-108">A service that starts automatically will be started when the computer on which it is installed is rebooted or first turned on.</span></span> <span data-ttu-id="28b07-109">Uživatel musí spustit službu, která se spustí ručně.</span><span class="sxs-lookup"><span data-stu-id="28b07-109">A user must start a service that starts manually.</span></span>

> [!NOTE]
> <span data-ttu-id="28b07-110">Ve výchozím nastavení se služby vytvořené pomocí sady Visual Studio nastaví tak, aby se spouštěly ručně.</span><span class="sxs-lookup"><span data-stu-id="28b07-110">By default, services created with Visual Studio are set to start manually.</span></span>

<span data-ttu-id="28b07-111">Existuje několik způsobů, jak ručně spustit službu – od **Průzkumník serveru**, od **správce řízení služeb**nebo z kódu pomocí komponenty s názvem <xref:System.ServiceProcess.ServiceController>.</span><span class="sxs-lookup"><span data-stu-id="28b07-111">There are several ways you can manually start a service — from **Server Explorer**, from the **Services Control Manager**, or from code using a component called the <xref:System.ServiceProcess.ServiceController>.</span></span>

<span data-ttu-id="28b07-112">Nastavením <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> vlastnosti <xref:System.ServiceProcess.ServiceInstaller> třídy určíte, zda má být služba spuštěna ručně nebo automaticky.</span><span class="sxs-lookup"><span data-stu-id="28b07-112">You set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property on the <xref:System.ServiceProcess.ServiceInstaller> class to determine whether a service should be started manually or automatically.</span></span>

### <a name="to-specify-how-a-service-should-start"></a><span data-ttu-id="28b07-113">Určení způsobu spuštění služby</span><span class="sxs-lookup"><span data-stu-id="28b07-113">To specify how a service should start</span></span>

1. <span data-ttu-id="28b07-114">Po vytvoření služby přidejte pro ni potřebné instalační programy.</span><span class="sxs-lookup"><span data-stu-id="28b07-114">After creating your service, add the necessary installers for it.</span></span> <span data-ttu-id="28b07-115">Další informace najdete v tématu [Postup: Přidání instalačních programů do aplikace služby](how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="28b07-115">For more information, see [How to: Add Installers to Your Service Application](how-to-add-installers-to-your-service-application.md).</span></span>

2. <span data-ttu-id="28b07-116">V návrháři klikněte na instalační program služby pro službu, se kterou pracujete.</span><span class="sxs-lookup"><span data-stu-id="28b07-116">In the designer, click the service installer for the service you are working with.</span></span>

3. <span data-ttu-id="28b07-117">V okně **vlastnosti** nastavte <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> vlastnost na jednu z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="28b07-117">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to one of the following:</span></span>

    |<span data-ttu-id="28b07-118">Instalace služby</span><span class="sxs-lookup"><span data-stu-id="28b07-118">To have your service install</span></span>|<span data-ttu-id="28b07-119">Nastavit tuto hodnotu</span><span class="sxs-lookup"><span data-stu-id="28b07-119">Set this value</span></span>|
    |----------------------------------|--------------------|
    |<span data-ttu-id="28b07-120">Po restartování počítače</span><span class="sxs-lookup"><span data-stu-id="28b07-120">When the computer is restarted</span></span>|<span data-ttu-id="28b07-121">**Automaticky**</span><span class="sxs-lookup"><span data-stu-id="28b07-121">**Automatic**</span></span>|
    |<span data-ttu-id="28b07-122">Když akce explicitního uživatele spustí službu</span><span class="sxs-lookup"><span data-stu-id="28b07-122">When an explicit user action starts the service</span></span>|<span data-ttu-id="28b07-123">**Ruční**</span><span class="sxs-lookup"><span data-stu-id="28b07-123">**Manual**</span></span>|

    > [!TIP]
    > <span data-ttu-id="28b07-124">Pokud chcete zabránit tomu, aby se služba spustila vůbec, můžete <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> vlastnost nastavit na **zakázáno**.</span><span class="sxs-lookup"><span data-stu-id="28b07-124">To prevent your service from being started at all, you can set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to **Disabled**.</span></span> <span data-ttu-id="28b07-125">To můžete provést, pokud budete Server několikrát restartovat a chcete ušetřit čas tím, že znemožníte službám, které by normálně začaly začít.</span><span class="sxs-lookup"><span data-stu-id="28b07-125">You might do this if you are going to reboot a server several times and want to save time by preventing the services that would normally start from starting up.</span></span>

    > [!NOTE]
    > <span data-ttu-id="28b07-126">Tyto a další vlastnosti se dají po instalaci služby změnit.</span><span class="sxs-lookup"><span data-stu-id="28b07-126">These and other properties can be changed after your service is installed.</span></span>

    <span data-ttu-id="28b07-127">Existuje několik způsobů, jak můžete spustit službu, která má svůj <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> proces nastavený na **ruční** – od **Průzkumník serveru**, od **správce řízení služeb systému Windows**nebo z kódu.</span><span class="sxs-lookup"><span data-stu-id="28b07-127">There are several ways you can start a service that has its <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> process set to **Manual** — from **Server Explorer**, from the **Windows Services Control Manager**, or from code.</span></span> <span data-ttu-id="28b07-128">Je důležité si uvědomit, že ne všechny tyto metody ve skutečnosti zahájí službu v kontextu **správce řízení služeb**; **Průzkumník serveru** a programové metody spuštění služby skutečně manipulují s řadičem.</span><span class="sxs-lookup"><span data-stu-id="28b07-128">It is important to note that not all of these methods actually start the service in the context of the **Services Control Manager**; **Server Explorer** and programmatic methods of starting the service actually manipulate the controller.</span></span>

### <a name="to-manually-start-a-service-from-server-explorer"></a><span data-ttu-id="28b07-129">Ruční spuštění služby z Průzkumník serveru</span><span class="sxs-lookup"><span data-stu-id="28b07-129">To manually start a service from Server Explorer</span></span>

1. <span data-ttu-id="28b07-130">V **Průzkumník serveru**přidejte server, který chcete, pokud již není uveden.</span><span class="sxs-lookup"><span data-stu-id="28b07-130">In **Server Explorer**, add the server you want if it is not already listed.</span></span> <span data-ttu-id="28b07-131">Další informace naleznete v tématu How to: Access and Initialize Průzkumník serveru-Database Explorer.</span><span class="sxs-lookup"><span data-stu-id="28b07-131">For more information, see How to: Access and Initialize Server Explorer-Database Explorer.</span></span>

2. <span data-ttu-id="28b07-132">Rozbalte uzel **služby** a vyhledejte službu, kterou chcete spustit.</span><span class="sxs-lookup"><span data-stu-id="28b07-132">Expand the **Services** node, and then locate the service you want to start.</span></span>

3. <span data-ttu-id="28b07-133">Klikněte pravým tlačítkem na název služby a pak klikněte na **Spustit**.</span><span class="sxs-lookup"><span data-stu-id="28b07-133">Right-click the name of the service, and click **Start**.</span></span>

### <a name="to-manually-start-a-service-from-services-control-manager"></a><span data-ttu-id="28b07-134">Ruční spuštění služby ze Správce řízení služeb</span><span class="sxs-lookup"><span data-stu-id="28b07-134">To manually start a service from Services Control Manager</span></span>

1. <span data-ttu-id="28b07-135">Pomocí jedné z následujících akcí otevřete **správce řízení služeb** :</span><span class="sxs-lookup"><span data-stu-id="28b07-135">Open the **Services Control Manager** by doing one of the following:</span></span>

    - <span data-ttu-id="28b07-136">V systému Windows XP a 2000 Professional klikněte pravým tlačítkem na položku **Tento počítač** na ploše a pak klikněte na možnost **Spravovat**.</span><span class="sxs-lookup"><span data-stu-id="28b07-136">In Windows XP and 2000 Professional, right-click **My Computer** on the desktop, and then click **Manage**.</span></span> <span data-ttu-id="28b07-137">V dialogovém okně, které se zobrazí, rozbalte uzel **služby a aplikace** .</span><span class="sxs-lookup"><span data-stu-id="28b07-137">In the dialog box that appears, expand the **Services and Applications** node.</span></span>

      <span data-ttu-id="28b07-138">\-ani</span><span class="sxs-lookup"><span data-stu-id="28b07-138">\- or -</span></span>

    - <span data-ttu-id="28b07-139">V systému Windows Server 2003 a Windows 2000 Server klikněte na **Start**, přejděte na **programy**, klikněte na **Nástroje pro správu**a potom klikněte na **služby**.</span><span class="sxs-lookup"><span data-stu-id="28b07-139">In Windows Server 2003 and Windows 2000 Server, click **Start**, point to **Programs**, click **Administrative Tools**, and then click **Services**.</span></span>

      > [!NOTE]
      > <span data-ttu-id="28b07-140">V systému Windows NT verze 4,0 můžete toto dialogové okno otevřít z **ovládacích panelů**.</span><span class="sxs-lookup"><span data-stu-id="28b07-140">In Windows NT version 4.0, you can open this dialog box from **Control Panel**.</span></span>

    <span data-ttu-id="28b07-141">Teď by se měla zobrazit vaše služba uvedená v části **služby** v okně.</span><span class="sxs-lookup"><span data-stu-id="28b07-141">You should now see your service listed in the **Services** section of the window.</span></span>

2. <span data-ttu-id="28b07-142">V seznamu vyberte svou službu, klikněte na ni pravým tlačítkem myši a pak klikněte na **Spustit**.</span><span class="sxs-lookup"><span data-stu-id="28b07-142">Select your service in the list, right-click it, and then click **Start**.</span></span>

### <a name="to-manually-start-a-service-from-code"></a><span data-ttu-id="28b07-143">Ruční spuštění služby z kódu</span><span class="sxs-lookup"><span data-stu-id="28b07-143">To manually start a service from code</span></span>

1. <span data-ttu-id="28b07-144">Vytvořte instanci <xref:System.ServiceProcess.ServiceController> třídy a nakonfigurujte ji pro interakci se službou, kterou chcete spravovat.</span><span class="sxs-lookup"><span data-stu-id="28b07-144">Create an instance of the <xref:System.ServiceProcess.ServiceController> class, and configure it to interact with the service you want to administer.</span></span>

2. <span data-ttu-id="28b07-145">Zavolejte <xref:System.ServiceProcess.ServiceController.Start%2A> metodu pro spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="28b07-145">Call the <xref:System.ServiceProcess.ServiceController.Start%2A> method to start the service.</span></span>

## <a name="see-also"></a><span data-ttu-id="28b07-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="28b07-146">See also</span></span>

- [<span data-ttu-id="28b07-147">Úvod do aplikací služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="28b07-147">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="28b07-148">Postupy: Vytváření služeb systému Windows</span><span class="sxs-lookup"><span data-stu-id="28b07-148">How to: Create Windows Services</span></span>](how-to-create-windows-services.md)
- [<span data-ttu-id="28b07-149">Postupy: Přidání instalačních programů do aplikace služby</span><span class="sxs-lookup"><span data-stu-id="28b07-149">How to: Add Installers to Your Service Application</span></span>](how-to-add-installers-to-your-service-application.md)
