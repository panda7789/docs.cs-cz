---
title: Pokyny k hostování služby IIS
ms.date: 03/30/2017
ms.assetid: 959a21c8-9d9d-4757-b255-4e57793ae9d6
ms.openlocfilehash: 226b47bfd90dc4cffb0a364a804016043cc25d02
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929113"
---
# <a name="internet-information-service-hosting-instructions"></a><span data-ttu-id="c9d49-102">Pokyny k hostování služby IIS</span><span class="sxs-lookup"><span data-stu-id="c9d49-102">Internet Information Service Hosting Instructions</span></span>
<span data-ttu-id="c9d49-103">Chcete-li spustit ukázky, které jsou hostovány službou Internetová informační služba (IIS), je nutné zajistit, aby služba IIS byla správně nainstalována a spuštěna.</span><span class="sxs-lookup"><span data-stu-id="c9d49-103">To run the samples that are hosted by Internet Information Services (IIS), you must make sure that IIS is properly installed and is running.</span></span>  
  
### <a name="to-install-iis-version-75-on-windows-server-2008-r2"></a><span data-ttu-id="c9d49-104">Instalace IIS verze 7,5 v systému Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="c9d49-104">To install IIS version 7.5 on Windows Server 2008 R2</span></span>  
  
1. <span data-ttu-id="c9d49-105">Z **Správce serveru**vyberte **role.**</span><span class="sxs-lookup"><span data-stu-id="c9d49-105">From **Server Manager**, select **Roles.**</span></span> <span data-ttu-id="c9d49-106">V části **Souhrn rolí**klikněte na **Přidat role**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-106">Under **Roles Summary**, click **Add Roles**.</span></span>  
  
2. <span data-ttu-id="c9d49-107">Kliknutím na tlačítko **Další** zobrazíte dialogové okno **Vybrat role serveru** .</span><span class="sxs-lookup"><span data-stu-id="c9d49-107">Click **Next** to display the **Select Server Roles** dialog.</span></span>  
  
3. <span data-ttu-id="c9d49-108">V seznamu **role** vyberte **aplikační server** a pak dvakrát klikněte na tlačítko **Další** , aby se zobrazil dialog **Vybrat služby rolí** pro roli aplikačního serveru.</span><span class="sxs-lookup"><span data-stu-id="c9d49-108">Select **Application Server** from the **Roles** list, and then click **Next** twice to display the **Select Role Services** dialog for the Application Server role.</span></span>  
  
4. <span data-ttu-id="c9d49-109">Zaškrtněte políčko **webový server (IIS)** .</span><span class="sxs-lookup"><span data-stu-id="c9d49-109">Select the **Web Server (IIS)** check box.</span></span> <span data-ttu-id="c9d49-110">Pokud se zobrazí výzva k instalaci dalších služeb rolí a funkcí, klikněte na **Přidat požadované funkce**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-110">If you are prompted to install additional role services and features, click **Add Required Features**.</span></span> <span data-ttu-id="c9d49-111">Dvojím kliknutím na tlačítko **Další** zobrazíte dialogové okno **Vybrat služby rolí** pro roli webového serveru (IIS).</span><span class="sxs-lookup"><span data-stu-id="c9d49-111">Click **Next** twice to display the **Select Role Services** dialog for the Web Server (IIS) role.</span></span>  
  
5. <span data-ttu-id="c9d49-112">Rozbalte položku **Nástroje pro správu**a poté rozbalte možnost **Kompatibilita správy služby IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-112">Expand **Management Tools**, and then expand **IIS 6 Management Compatibility**.</span></span> <span data-ttu-id="c9d49-113">Vyberte **Nástroje pro skriptování služby IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-113">Select **IIS 6 Scripting Tools**.</span></span> <span data-ttu-id="c9d49-114">Pokud se zobrazí výzva k instalaci dalších služeb rolí a funkcí, klikněte na **Přidat požadované služby rolí**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-114">If you are prompted to install additional role services and features, click **Add Required Role Services**.</span></span> <span data-ttu-id="c9d49-115">Klikněte na **Další**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-115">Click **Next**.</span></span>  
  
6. <span data-ttu-id="c9d49-116">Pokud je souhrn výběrů správný, klikněte na **nainstalovat**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-116">If the summary of selections is correct, click **Install**.</span></span>  
  
7. <span data-ttu-id="c9d49-117">Po dokončení instalace klikněte na **Zavřít**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-117">When installation completes, click **Close**.</span></span>  
  
### <a name="to-install-iis-version-75-on-windows-7"></a><span data-ttu-id="c9d49-118">Instalace IIS verze 7,5 ve Windows 7</span><span class="sxs-lookup"><span data-stu-id="c9d49-118">To install IIS version 7.5 on Windows 7</span></span>  
  
1. <span data-ttu-id="c9d49-119">Klikněte na tlačítko **Start**a poté na příkaz **Ovládací panely**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-119">Click **Start**, and then click **Control Panel**.</span></span>  
  
2. <span data-ttu-id="c9d49-120">Otevřete skupinu **programy** .</span><span class="sxs-lookup"><span data-stu-id="c9d49-120">Open the **Programs** group.</span></span>  
  
3. <span data-ttu-id="c9d49-121">V části **programy a funkce**klikněte na **zapnout nebo vypnout funkce systému Windows**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-121">Under **Programs and Features**, click **Turn Windows Features on or off**.</span></span>  
  
4. <span data-ttu-id="c9d49-122">Zobrazí se dialogové okno **řízení uživatelských účtů** .</span><span class="sxs-lookup"><span data-stu-id="c9d49-122">The **User Account Control** dialog is displayed.</span></span> <span data-ttu-id="c9d49-123">Klikněte na **Pokračovat**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-123">Click **Continue**.</span></span>  
  
5. <span data-ttu-id="c9d49-124">Zobrazí se dialogové okno **funkce systému Windows** .</span><span class="sxs-lookup"><span data-stu-id="c9d49-124">The **Windows Features** dialog is displayed.</span></span> <span data-ttu-id="c9d49-125">Rozbalte položku s označením **Internetová informační služba**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-125">Expand the item labeled **Internet Information Services**.</span></span>  
  
6. <span data-ttu-id="c9d49-126">Rozbalte položku označené **webové služby**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-126">Expand the item labeled **World Wide Web Services**.</span></span>  
  
7. <span data-ttu-id="c9d49-127">Rozbalte položku **funkce pro vývoj aplikací**s popisky.</span><span class="sxs-lookup"><span data-stu-id="c9d49-127">Expand the item labeled **Application Development Features**.</span></span>  
  
8. <span data-ttu-id="c9d49-128">Ujistěte se, že jsou vybrané následující položky:</span><span class="sxs-lookup"><span data-stu-id="c9d49-128">Make sure the following items are selected:</span></span>  
  
    1. <span data-ttu-id="c9d49-129">**Rozšiřitelnost rozhraní .NET**</span><span class="sxs-lookup"><span data-stu-id="c9d49-129">**.NET Extensibility**</span></span>  
  
    2. <span data-ttu-id="c9d49-130">**ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="c9d49-130">**ASP.NET**</span></span>  
  
    3. <span data-ttu-id="c9d49-131">**Rozšíření ISAPI**</span><span class="sxs-lookup"><span data-stu-id="c9d49-131">**ISAPI Extensions**</span></span>  
  
    4. <span data-ttu-id="c9d49-132">**Filtry ISAPI**</span><span class="sxs-lookup"><span data-stu-id="c9d49-132">**ISAPI Filters**</span></span>  
  
9. <span data-ttu-id="c9d49-133">V části položka označená jako **webové služby**rozbalte možnost **běžné funkce protokolu HTTP**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-133">Under the item labeled **World Wide Web Services**, expand **Common Http Features**.</span></span>  
  
10. <span data-ttu-id="c9d49-134">Ujistěte se, že je vybraný **statický obsah** .</span><span class="sxs-lookup"><span data-stu-id="c9d49-134">Make sure **Static Content** is selected.</span></span>  
  
11. <span data-ttu-id="c9d49-135">Pod položkou označený **World World Web Services**rozbalte **zabezpečení**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-135">Under the item labeled **World Wide Web Services**, expand **Security**.</span></span>  
  
12. <span data-ttu-id="c9d49-136">Ujistěte se, že je vybráno **ověřování systému Windows** .</span><span class="sxs-lookup"><span data-stu-id="c9d49-136">Make sure that **Windows Authentication** is selected.</span></span>  
  
13. <span data-ttu-id="c9d49-137">V adresáři **Internetová informační služba** rozbalte položku nástroje s popisem **webové správy**a pak vyberte možnost **Konzola pro správu služby IIS**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-137">Under the **Internet Information Services** directory, expand the item labeled **Web Management Tools**, and then select **IIS Management Console**.</span></span>  
  
14. <span data-ttu-id="c9d49-138">Rozbalte položku označená **Kompatibilita správy služby IIS 6**a pak vyberte **Nástroje pro skriptování služby IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-138">Expand the item labeled **IIS 6 Management Compatibility**, and then select **IIS 6 Scripting Tools**.</span></span>  
  
15. <span data-ttu-id="c9d49-139">V adresáři **Internetová informační služba** rozbalte položku s názvem **Microsoft .NET Framework 3.5.1**a pak vyberte **Windows Communication Foundation aktivace protokolem HTTP**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-139">Under the **Internet Information Services** directory, expand the item labeled **Microsoft .NET Framework 3.5.1**, and then select **Windows Communication Foundation Http Activation**.</span></span>  
  
16. <span data-ttu-id="c9d49-140">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-140">Click **OK**.</span></span>  
  
### <a name="to-install-iis-version-70-on-windows-server-2008"></a><span data-ttu-id="c9d49-141">Instalace IIS verze 7,0 v systému Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="c9d49-141">To install IIS version 7.0 on Windows Server 2008</span></span>  
  
1. <span data-ttu-id="c9d49-142">Z **Správce serveru**vyberte **role**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-142">From **Server Manager**, select **Roles**.</span></span> <span data-ttu-id="c9d49-143">V části **Souhrn rolí**klikněte na **Přidat role**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-143">Under **Roles Summary**, click **Add Roles**.</span></span>  
  
2. <span data-ttu-id="c9d49-144">Kliknutím na tlačítko **Další** zobrazíte dialogové okno **Vybrat role serveru** .</span><span class="sxs-lookup"><span data-stu-id="c9d49-144">Click **Next** to display the **Select Server Roles** dialog.</span></span>  
  
3. <span data-ttu-id="c9d49-145">V seznamu **role** vyberte **aplikační server** a pak dvakrát klikněte na tlačítko **Další** , aby se zobrazil dialog **Vybrat služby rolí** pro roli aplikačního serveru.</span><span class="sxs-lookup"><span data-stu-id="c9d49-145">Select **Application Server** from the **Roles** list, and then click **Next** twice to display the **Select Role Services** dialog for the Application Server role.</span></span>  
  
4. <span data-ttu-id="c9d49-146">Vyberte zaškrtávací políčko **webový server (IIS)** .</span><span class="sxs-lookup"><span data-stu-id="c9d49-146">Select **Web Server (IIS)** check box.</span></span> <span data-ttu-id="c9d49-147">Pokud se zobrazí výzva k instalaci dalších služeb rolí a funkcí, klikněte na **Přidat požadované funkce**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-147">If you are prompted to install additional role services and features, click **Add Required Features**.</span></span> <span data-ttu-id="c9d49-148">Dvojím kliknutím na tlačítko **Další** zobrazíte dialogové okno **Vybrat služby rolí** pro roli webového serveru (IIS).</span><span class="sxs-lookup"><span data-stu-id="c9d49-148">Click **Next** twice to display the **Select Role Services** dialog for the Web Server (IIS) role.</span></span>  
  
5. <span data-ttu-id="c9d49-149">Rozbalte položku **Nástroje pro správu**a poté rozbalte možnost **Kompatibilita správy služby IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-149">Expand **Management Tools**, and then expand **IIS 6 Management Compatibility**.</span></span> <span data-ttu-id="c9d49-150">Vyberte **Nástroje pro skriptování služby IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-150">Select **IIS 6 Scripting Tools**.</span></span> <span data-ttu-id="c9d49-151">Pokud se zobrazí výzva k instalaci dalších služeb rolí a funkcí, klikněte na **Přidat požadované služby rolí**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-151">If you are prompted to install additional role services and features, click **Add Required Role Services**.</span></span> <span data-ttu-id="c9d49-152">Klikněte na **Další**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-152">Click **Next**.</span></span>  
  
6. <span data-ttu-id="c9d49-153">Pokud je souhrn výběrů správný, klikněte na **nainstalovat**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-153">If the summary of selections is correct, click **Install**.</span></span>  
  
7. <span data-ttu-id="c9d49-154">Po dokončení instalace klikněte na **Zavřít**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-154">When installation completes, click **Close**.</span></span>  
  
### <a name="to-install-iis-version-70-on-windows-vista"></a><span data-ttu-id="c9d49-155">Instalace IIS verze 7,0 v systému Windows Vista</span><span class="sxs-lookup"><span data-stu-id="c9d49-155">To install IIS version 7.0 on Windows Vista</span></span>  
  
1. <span data-ttu-id="c9d49-156">Klikněte na tlačítko Start a poté na příkaz Ovládací panely.</span><span class="sxs-lookup"><span data-stu-id="c9d49-156">Click Start, and then click Control Panel.</span></span>  
  
2. <span data-ttu-id="c9d49-157">Vyberte skupinu **programy** .</span><span class="sxs-lookup"><span data-stu-id="c9d49-157">Select the **Programs** group.</span></span>  
  
3. <span data-ttu-id="c9d49-158">V části **programy a funkce**klikněte na **zapnout nebo vypnout funkce systému Windows**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-158">Under **Programs and Features**, click **Turn Windows Features on or off**.</span></span>  
  
4. <span data-ttu-id="c9d49-159">Zobrazí se dialogové okno **řízení uživatelských účtů** .</span><span class="sxs-lookup"><span data-stu-id="c9d49-159">The **User Account Control** dialog is displayed.</span></span> <span data-ttu-id="c9d49-160">Klikněte na **Pokračovat**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-160">Click **Continue**.</span></span>  
  
5. <span data-ttu-id="c9d49-161">Zobrazí se dialogové okno **funkce systému Windows** .</span><span class="sxs-lookup"><span data-stu-id="c9d49-161">The **Windows Features** dialog is displayed.</span></span> <span data-ttu-id="c9d49-162">Rozbalte položku s označením **Internetová informační služba**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-162">Expand the item labeled **Internet Information Services**.</span></span>  
  
6. <span data-ttu-id="c9d49-163">Rozbalte položku označené **webové služby**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-163">Expand the item labeled **World Wide Web Services**.</span></span>  
  
7. <span data-ttu-id="c9d49-164">Rozbalte položku **funkce pro vývoj aplikací**s popisky.</span><span class="sxs-lookup"><span data-stu-id="c9d49-164">Expand the item labeled **Application Development Features**.</span></span>  
  
8. <span data-ttu-id="c9d49-165">Ujistěte se, že jsou vybrané následující položky:</span><span class="sxs-lookup"><span data-stu-id="c9d49-165">Make sure the following items are selected:</span></span>  
  
    1. <span data-ttu-id="c9d49-166">**Rozšiřitelnost rozhraní .NET**</span><span class="sxs-lookup"><span data-stu-id="c9d49-166">**.NET Extensibility**</span></span>  
  
    2. <span data-ttu-id="c9d49-167">**ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="c9d49-167">**ASP.NET**</span></span>  
  
    3. <span data-ttu-id="c9d49-168">**Rozšíření ISAPI**</span><span class="sxs-lookup"><span data-stu-id="c9d49-168">**ISAPI Extensions**</span></span>  
  
    4. <span data-ttu-id="c9d49-169">**Filtry ISAPI**</span><span class="sxs-lookup"><span data-stu-id="c9d49-169">**ISAPI Filters**</span></span>  
  
9. <span data-ttu-id="c9d49-170">Rozbalte položku označené **Nástroje webové správy**a pak vyberte možnost **Konzola pro správu služby IIS**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-170">Expand the item labeled **Web Management Tools**, and then select **IIS Management Console**.</span></span>  
  
10. <span data-ttu-id="c9d49-171">V části položka označená jako **webové služby**rozbalte možnost **běžné funkce protokolu HTTP**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-171">Under the item labeled **World Wide Web Services**, expand **Common Http Features**.</span></span>  
  
11. <span data-ttu-id="c9d49-172">Ujistěte se, že je vybraný **statický obsah** .</span><span class="sxs-lookup"><span data-stu-id="c9d49-172">Make sure **Static Content** is selected.</span></span>  
  
12. <span data-ttu-id="c9d49-173">Pod položkou označený **World World Web Services**rozbalte **zabezpečení**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-173">Under the item labeled **World Wide Web Services**, expand **Security**.</span></span>  
  
13. <span data-ttu-id="c9d49-174">Ujistěte se, že je vybráno **ověřování systému Windows** .</span><span class="sxs-lookup"><span data-stu-id="c9d49-174">Make sure **Windows Authentication** is selected.</span></span>  
  
14. <span data-ttu-id="c9d49-175">Rozbalte položku označená **Kompatibilita správy služby IIS 6**a pak vyberte **Nástroje pro skriptování služby IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-175">Expand the item labeled **IIS 6 Management Compatibility**, and then select **IIS 6 Scripting Tools**.</span></span>  
  
15. <span data-ttu-id="c9d49-176">Rozbalte položku s označením **Microsoft .NET Framework 3,0**a potom vyberte **Windows Communication Foundation aktivace protokolem HTTP**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-176">Expand the item labeled **Microsoft .NET Framework 3.0**, and then select **Windows Communication Foundation Http Activation**.</span></span>  
  
16. <span data-ttu-id="c9d49-177">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-177">Click **OK**.</span></span>  
  
### <a name="to-install-iis-version-60-on-windows-server-2003"></a><span data-ttu-id="c9d49-178">Instalace IIS verze 6,0 v systému Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="c9d49-178">To install IIS version 6.0 on Windows Server 2003</span></span>  
  
1. <span data-ttu-id="c9d49-179">V nabídce **spravovat server**klikněte na **Přidat nebo odebrat roli**a pak klikněte na **Další**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-179">From **Manage Your Server**, click **Add or remove a role**, and then click **Next**.</span></span>  
  
2. <span data-ttu-id="c9d49-180">V seznamu **role serveru** vyberte **aplikační server (IIS, ASP.NET)** a pak klikněte na **Další**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-180">Select **Application server (IIS, ASP.NET)** from the **Server Role** list, and then click **Next**.</span></span>  
  
3. <span data-ttu-id="c9d49-181">Zaškrtněte políčko **povolit ASP.NET** a potom klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-181">Select **Enable ASP.NET** check box, and then click **Next**.</span></span>  
  
4. <span data-ttu-id="c9d49-182">Je-li Souhrn výběrů správný, klikněte na tlačítko Další.</span><span class="sxs-lookup"><span data-stu-id="c9d49-182">If the summary of selections is correct, click Next.</span></span>  
  
### <a name="to-install-iis-version-51-on-windows-xp-with-service-pack-2-and-service-pack-3-installed"></a><span data-ttu-id="c9d49-183">Instalace IIS verze 5,1 v systému Windows XP s nainstalovanou aktualizací Service Pack 2 a Service Pack 3</span><span class="sxs-lookup"><span data-stu-id="c9d49-183">To install IIS version 5.1 on Windows XP with Service Pack 2 and Service Pack 3 installed</span></span>  
  
1. <span data-ttu-id="c9d49-184">V Ovládacích panelech klikněte na **Přidat nebo odebrat programy**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-184">In Control Panel, click **Add or Remove Programs**.</span></span>  
  
2. <span data-ttu-id="c9d49-185">V dialogovém okně **Přidat nebo odebrat programy** klikněte na tlačítko **Přidat nebo odebrat součásti systému Windows**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-185">In the **Add or Remove Programs** dialog box, click **Add/Remove Windows Components**.</span></span>  
  
3. <span data-ttu-id="c9d49-186">V **Průvodci součástmi systému Windows**zaškrtněte políčko **Internetová informační služba (IIS)** a poté klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-186">In the **Windows Components Wizard**, select the **Internet Information Services (IIS)** check box, and then click **Next**.</span></span>  
  
4. <span data-ttu-id="c9d49-187">Pokud se zobrazí dialogové okno **potřebné soubory** , vložte instalační disk operačního systému, vyhledejte složku i386 a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-187">If the **Files Needed** dialog box is displayed, insert your operating system installation disc, browse to the i386 folder, and then click **OK**.</span></span>  
  
5. <span data-ttu-id="c9d49-188">Po dokončení instalace klikněte na **Dokončit**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-188">When installation completes, click **Finish**.</span></span>  
  
6. <span data-ttu-id="c9d49-189">Zavřete dialogové okno **Přidat nebo odebrat programy** a pak zavřete **Ovládací panely**.</span><span class="sxs-lookup"><span data-stu-id="c9d49-189">Close the **Add or Remove Programs** dialog box, and then close **Control Panel**.</span></span>  
  
### <a name="to-verify-the-installation-of-iis-and-aspnet"></a><span data-ttu-id="c9d49-190">Ověření instalace služby IIS a ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c9d49-190">To verify the installation of IIS and ASP.NET</span></span>  
  
1. <span data-ttu-id="c9d49-191">Uložte soubor HTML, který najdete na konci tohoto tématu, do kořenového adresáře \InetPub\wwwroot a pojmenujte ho default. aspx.</span><span class="sxs-lookup"><span data-stu-id="c9d49-191">Save the HTML file found at the end of this topic in the root \InetPub\wwwroot directory and name it Default.aspx.</span></span>  
  
2. <span data-ttu-id="c9d49-192">Otevřete okno prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="c9d49-192">Open a browser window.</span></span>  
  
3. <span data-ttu-id="c9d49-193">Do `http://localhost/Default.aspx` pole Adresa zadejte a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="c9d49-193">Type `http://localhost/Default.aspx` in the address box, and then press ENTER.</span></span>  
  
4. <span data-ttu-id="c9d49-194">Měla by se zobrazit webová stránka s textem Hello World.</span><span class="sxs-lookup"><span data-stu-id="c9d49-194">A Web page with the text "Hello World" should appear.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c9d49-195">Pokaždé, když instalujete novou verzi .NET Framework, je nutné znovu zaregistrovat modul Aspnet_isapi jako rozšíření webové služby pro službu IIS.</span><span class="sxs-lookup"><span data-stu-id="c9d49-195">Each time you install a new version of the .NET Framework, you must re-register aspnet_isapi as a Web service extension for IIS.</span></span> <span data-ttu-id="c9d49-196">Provedete to tak, `aspnet_regiis –I –enable` že vydáte příkaz.</span><span class="sxs-lookup"><span data-stu-id="c9d49-196">To do so, issue the `aspnet_regiis –I –enable` command.</span></span>  
  
## <a name="sample-code"></a><span data-ttu-id="c9d49-197">Vzorový kód</span><span class="sxs-lookup"><span data-stu-id="c9d49-197">Sample Code</span></span>  
  
```xml  
<html>  
   <body>  
       <form >  
           <h3> Hello World  
           </h3>  
       </form>  
   </body>  
</html>  
```
