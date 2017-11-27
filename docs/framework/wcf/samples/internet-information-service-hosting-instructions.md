---
title: "Pokyny k hostování služby IIS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 959a21c8-9d9d-4757-b255-4e57793ae9d6
caps.latest.revision: "30"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3c815ffe88918502f7d040bdeb1ff1b201cec832
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="internet-information-service-hosting-instructions"></a><span data-ttu-id="25958-102">Pokyny k hostování služby IIS</span><span class="sxs-lookup"><span data-stu-id="25958-102">Internet Information Service Hosting Instructions</span></span>
<span data-ttu-id="25958-103">Ke spuštění ukázky, které jsou hostované pomocí Internetové informační služby (IIS), musí se ujistěte, že služba IIS je správně nainstalován a běží.</span><span class="sxs-lookup"><span data-stu-id="25958-103">To run the samples that are hosted by Internet Information Services (IIS), you must make sure that IIS is properly installed and is running.</span></span>  
  
### <a name="to-install-iis-version-75-on-windows-server-2008-r2"></a><span data-ttu-id="25958-104">Instalace služby IIS verze 7.5 na Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="25958-104">To install IIS version 7.5 on Windows Server 2008 R2</span></span>  
  
1.  <span data-ttu-id="25958-105">Z **správce serveru**, vyberte **role.**</span><span class="sxs-lookup"><span data-stu-id="25958-105">From **Server Manager**, select **Roles.**</span></span> <span data-ttu-id="25958-106">V části **Souhrn rolí**, klikněte na tlačítko **přidat role**.</span><span class="sxs-lookup"><span data-stu-id="25958-106">Under **Roles Summary**, click **Add Roles**.</span></span>  
  
2.  <span data-ttu-id="25958-107">Klikněte na tlačítko **Další** zobrazíte **vybrat role serveru** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="25958-107">Click **Next** to display the **Select Server Roles** dialog.</span></span>  
  
3.  <span data-ttu-id="25958-108">Vyberte **aplikační Server** z **role** seznamu a pak klikněte na tlačítko **Další** dvakrát zobrazíte **vybrat služby rolí** dialogové okno pro Role aplikačního serveru.</span><span class="sxs-lookup"><span data-stu-id="25958-108">Select **Application Server** from the **Roles** list, and then click **Next** twice to display the **Select Role Services** dialog for the Application Server role.</span></span>  
  
4.  <span data-ttu-id="25958-109">Vyberte **webového serveru (IIS)** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="25958-109">Select the **Web Server (IIS)** check box.</span></span> <span data-ttu-id="25958-110">Pokud se zobrazí výzva k instalaci další služby rolí a funkcí, klikněte na tlačítko **přidat požadované funkce**.</span><span class="sxs-lookup"><span data-stu-id="25958-110">If you are prompted to install additional role services and features, click **Add Required Features**.</span></span> <span data-ttu-id="25958-111">Klikněte na tlačítko **Další** dvakrát zobrazíte **vybrat služby rolí** dialogové okno pro roli webového serveru (IIS).</span><span class="sxs-lookup"><span data-stu-id="25958-111">Click **Next** twice to display the **Select Role Services** dialog for the Web Server (IIS) role.</span></span>  
  
5.  <span data-ttu-id="25958-112">Rozbalte položku **nástroje pro správu**a potom rozbalte **IIS 6 Management Compatibility**.</span><span class="sxs-lookup"><span data-stu-id="25958-112">Expand **Management Tools**, and then expand **IIS 6 Management Compatibility**.</span></span> <span data-ttu-id="25958-113">Vyberte **IIS nástroje pro skriptování 6**.</span><span class="sxs-lookup"><span data-stu-id="25958-113">Select **IIS 6 Scripting Tools**.</span></span> <span data-ttu-id="25958-114">Pokud se zobrazí výzva k instalaci další služby rolí a funkcí, klikněte na tlačítko **přidat požadované služby rolí**.</span><span class="sxs-lookup"><span data-stu-id="25958-114">If you are prompted to install additional role services and features, click **Add Required Role Services**.</span></span> <span data-ttu-id="25958-115">Klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="25958-115">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="25958-116">Pokud souhrn výběr správné, klikněte na tlačítko **nainstalovat**.</span><span class="sxs-lookup"><span data-stu-id="25958-116">If the summary of selections is correct, click **Install**.</span></span>  
  
7.  <span data-ttu-id="25958-117">Po dokončení instalace, klikněte na tlačítko **Zavřít**.</span><span class="sxs-lookup"><span data-stu-id="25958-117">When installation completes, click **Close**.</span></span>  
  
### <a name="to-install-iis-version-75-on-windows-7"></a><span data-ttu-id="25958-118">Instalace služby IIS verze 7.5 na systému Windows 7</span><span class="sxs-lookup"><span data-stu-id="25958-118">To install IIS version 7.5 on Windows 7</span></span>  
  
1.  <span data-ttu-id="25958-119">Klikněte na tlačítko **spustit**a potom klikněte na **ovládací panely**.</span><span class="sxs-lookup"><span data-stu-id="25958-119">Click **Start**, and then click **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="25958-120">Otevřete **programy** skupiny.</span><span class="sxs-lookup"><span data-stu-id="25958-120">Open the **Programs** group.</span></span>  
  
3.  <span data-ttu-id="25958-121">V části **programy a funkce**, klikněte na tlačítko **zapnout nebo vypnout funkce systému Windows**.</span><span class="sxs-lookup"><span data-stu-id="25958-121">Under **Programs and Features**, click **Turn Windows Features on or off**.</span></span>  
  
4.  <span data-ttu-id="25958-122">**Řízení uživatelských účtů** se zobrazí dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="25958-122">The **User Account Control** dialog is displayed.</span></span> <span data-ttu-id="25958-123">Klikněte na tlačítko **pokračovat**.</span><span class="sxs-lookup"><span data-stu-id="25958-123">Click **Continue**.</span></span>  
  
5.  <span data-ttu-id="25958-124">**Funkce systému Windows** se zobrazí dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="25958-124">The **Windows Features** dialog is displayed.</span></span> <span data-ttu-id="25958-125">Rozbalte položky s popiskem **Internetová informační služba**.</span><span class="sxs-lookup"><span data-stu-id="25958-125">Expand the item labeled **Internet Information Services**.</span></span>  
  
6.  <span data-ttu-id="25958-126">Rozbalte položky s popiskem **webové služby**.</span><span class="sxs-lookup"><span data-stu-id="25958-126">Expand the item labeled **World Wide Web Services**.</span></span>  
  
7.  <span data-ttu-id="25958-127">Rozbalte položky s popiskem **funkce pro vývoj aplikací**.</span><span class="sxs-lookup"><span data-stu-id="25958-127">Expand the item labeled **Application Development Features**.</span></span>  
  
8.  <span data-ttu-id="25958-128">Zkontrolujte, zda že jsou vybrány následující položky:</span><span class="sxs-lookup"><span data-stu-id="25958-128">Make sure the following items are selected:</span></span>  
  
    1.  <span data-ttu-id="25958-129">**Rozšiřitelnost rozhraní .NET**</span><span class="sxs-lookup"><span data-stu-id="25958-129">**.NET Extensibility**</span></span>  
  
    2.  <span data-ttu-id="25958-130">**TECHNOLOGIE ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="25958-130">**ASP.NET**</span></span>  
  
    3.  <span data-ttu-id="25958-131">**Rozšíření ISAPI**</span><span class="sxs-lookup"><span data-stu-id="25958-131">**ISAPI Extensions**</span></span>  
  
    4.  <span data-ttu-id="25958-132">**Filtry ISAPI**</span><span class="sxs-lookup"><span data-stu-id="25958-132">**ISAPI Filters**</span></span>  
  
9. <span data-ttu-id="25958-133">V části položka s názvem bez přípony **webové služby**, rozbalte položku **společné funkce protokolu Http**.</span><span class="sxs-lookup"><span data-stu-id="25958-133">Under the item labeled **World Wide Web Services**, expand **Common Http Features**.</span></span>  
  
10. <span data-ttu-id="25958-134">Zajistěte, aby **statický obsah** je vybrána.</span><span class="sxs-lookup"><span data-stu-id="25958-134">Make sure **Static Content** is selected.</span></span>  
  
11. <span data-ttu-id="25958-135">V části položka s názvem bez přípony **webové služby**, rozbalte položku **zabezpečení**.</span><span class="sxs-lookup"><span data-stu-id="25958-135">Under the item labeled **World Wide Web Services**, expand **Security**.</span></span>  
  
12. <span data-ttu-id="25958-136">Ujistěte se, že **ověřování systému Windows** je vybrána.</span><span class="sxs-lookup"><span data-stu-id="25958-136">Make sure that **Windows Authentication** is selected.</span></span>  
  
13. <span data-ttu-id="25958-137">V části **Internetová informační služba** adresáře, rozbalte položku s popiskem **nástroje webové správy**a potom vyberte **konzoly pro správu služby IIS**.</span><span class="sxs-lookup"><span data-stu-id="25958-137">Under the **Internet Information Services** directory, expand the item labeled **Web Management Tools**, and then select **IIS Management Console**.</span></span>  
  
14. <span data-ttu-id="25958-138">Rozbalte položky s popiskem **IIS 6 Management Compatibility**a potom vyberte **nástroje pro skriptování na služby IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="25958-138">Expand the item labeled **IIS 6 Management Compatibility**, and then select **IIS 6 Scripting Tools**.</span></span>  
  
15. <span data-ttu-id="25958-139">V části **Internetová informační služba** adresáře, rozbalte položku s popiskem **rozhraní Microsoft .NET Framework 3.5.1**a potom vyberte **aktivace Windows Communication Foundation Http**.</span><span class="sxs-lookup"><span data-stu-id="25958-139">Under the **Internet Information Services** directory, expand the item labeled **Microsoft .NET Framework 3.5.1**, and then select **Windows Communication Foundation Http Activation**.</span></span>  
  
16. <span data-ttu-id="25958-140">Click **OK**.</span><span class="sxs-lookup"><span data-stu-id="25958-140">Click **OK**.</span></span>  
  
### <a name="to-install-iis-version-70-on-windows-server-2008"></a><span data-ttu-id="25958-141">Chcete-li nainstalovat službu IIS 7.0 v systému Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="25958-141">To install IIS version 7.0 on Windows Server 2008</span></span>  
  
1.  <span data-ttu-id="25958-142">Z **správce serveru**, vyberte **role**.</span><span class="sxs-lookup"><span data-stu-id="25958-142">From **Server Manager**, select **Roles**.</span></span> <span data-ttu-id="25958-143">V části **Souhrn rolí**, klikněte na tlačítko **přidat role**.</span><span class="sxs-lookup"><span data-stu-id="25958-143">Under **Roles Summary**, click **Add Roles**.</span></span>  
  
2.  <span data-ttu-id="25958-144">Klikněte na tlačítko **Další** zobrazíte **vybrat role serveru** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="25958-144">Click **Next** to display the **Select Server Roles** dialog.</span></span>  
  
3.  <span data-ttu-id="25958-145">Vyberte **aplikační Server** z **role** seznamu a pak klikněte na tlačítko **Další** dvakrát zobrazíte **vybrat služby rolí** dialogové okno pro Role aplikačního serveru.</span><span class="sxs-lookup"><span data-stu-id="25958-145">Select **Application Server** from the **Roles** list, and then click **Next** twice to display the **Select Role Services** dialog for the Application Server role.</span></span>  
  
4.  <span data-ttu-id="25958-146">Vyberte **webového serveru (IIS)** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="25958-146">Select **Web Server (IIS)** check box.</span></span> <span data-ttu-id="25958-147">Pokud se zobrazí výzva k instalaci další služby rolí a funkcí, klikněte na tlačítko **přidat požadované funkce**.</span><span class="sxs-lookup"><span data-stu-id="25958-147">If you are prompted to install additional role services and features, click **Add Required Features**.</span></span> <span data-ttu-id="25958-148">Klikněte na tlačítko **Další** dvakrát zobrazíte **vybrat služby rolí** dialogové okno pro roli webového serveru (IIS).</span><span class="sxs-lookup"><span data-stu-id="25958-148">Click **Next** twice to display the **Select Role Services** dialog for the Web Server (IIS) role.</span></span>  
  
5.  <span data-ttu-id="25958-149">Rozbalte položku **nástroje pro správu**a potom rozbalte **IIS 6 Management Compatibility**.</span><span class="sxs-lookup"><span data-stu-id="25958-149">Expand **Management Tools**, and then expand **IIS 6 Management Compatibility**.</span></span> <span data-ttu-id="25958-150">Vyberte **IIS nástroje pro skriptování 6**.</span><span class="sxs-lookup"><span data-stu-id="25958-150">Select **IIS 6 Scripting Tools**.</span></span> <span data-ttu-id="25958-151">Pokud se zobrazí výzva k instalaci další služby rolí a funkcí, klikněte na tlačítko **přidat požadované služby rolí**.</span><span class="sxs-lookup"><span data-stu-id="25958-151">If you are prompted to install additional role services and features, click **Add Required Role Services**.</span></span> <span data-ttu-id="25958-152">Klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="25958-152">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="25958-153">Pokud souhrn výběr správné, klikněte na tlačítko **nainstalovat**.</span><span class="sxs-lookup"><span data-stu-id="25958-153">If the summary of selections is correct, click **Install**.</span></span>  
  
7.  <span data-ttu-id="25958-154">Po dokončení instalace, klikněte na tlačítko **Zavřít**.</span><span class="sxs-lookup"><span data-stu-id="25958-154">When installation completes, click **Close**.</span></span>  
  
### <a name="to-install-iis-version-70-on-windows-vista"></a><span data-ttu-id="25958-155">Chcete-li nainstalovat službu IIS 7.0 v systému Windows Vista</span><span class="sxs-lookup"><span data-stu-id="25958-155">To install IIS version 7.0 on Windows Vista</span></span>  
  
1.  <span data-ttu-id="25958-156">Klikněte na tlačítko Start a pak klikněte na ovládacích panelech.</span><span class="sxs-lookup"><span data-stu-id="25958-156">Click Start, and then click Control Panel.</span></span>  
  
2.  <span data-ttu-id="25958-157">Vyberte **programy** skupiny.</span><span class="sxs-lookup"><span data-stu-id="25958-157">Select the **Programs** group.</span></span>  
  
3.  <span data-ttu-id="25958-158">V části **programy a funkce**, klikněte na tlačítko **zapnout nebo vypnout funkce systému Windows**.</span><span class="sxs-lookup"><span data-stu-id="25958-158">Under **Programs and Features**, click **Turn Windows Features on or off**.</span></span>  
  
4.  <span data-ttu-id="25958-159">**Řízení uživatelských účtů** se zobrazí dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="25958-159">The **User Account Control** dialog is displayed.</span></span> <span data-ttu-id="25958-160">Klikněte na tlačítko **pokračovat**.</span><span class="sxs-lookup"><span data-stu-id="25958-160">Click **Continue**.</span></span>  
  
5.  <span data-ttu-id="25958-161">**Funkce systému Windows** se zobrazí dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="25958-161">The **Windows Features** dialog is displayed.</span></span> <span data-ttu-id="25958-162">Rozbalte položky s popiskem **Internetová informační služba**.</span><span class="sxs-lookup"><span data-stu-id="25958-162">Expand the item labeled **Internet Information Services**.</span></span>  
  
6.  <span data-ttu-id="25958-163">Rozbalte položky s popiskem **webové služby**.</span><span class="sxs-lookup"><span data-stu-id="25958-163">Expand the item labeled **World Wide Web Services**.</span></span>  
  
7.  <span data-ttu-id="25958-164">Rozbalte položky s popiskem **funkce pro vývoj aplikací**.</span><span class="sxs-lookup"><span data-stu-id="25958-164">Expand the item labeled **Application Development Features**.</span></span>  
  
8.  <span data-ttu-id="25958-165">Zkontrolujte, zda že jsou vybrány následující položky:</span><span class="sxs-lookup"><span data-stu-id="25958-165">Make sure the following items are selected:</span></span>  
  
    1.  <span data-ttu-id="25958-166">**Rozšiřitelnost rozhraní .NET**</span><span class="sxs-lookup"><span data-stu-id="25958-166">**.NET Extensibility**</span></span>  
  
    2.  <span data-ttu-id="25958-167">**TECHNOLOGIE ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="25958-167">**ASP.NET**</span></span>  
  
    3.  <span data-ttu-id="25958-168">**Rozšíření ISAPI**</span><span class="sxs-lookup"><span data-stu-id="25958-168">**ISAPI Extensions**</span></span>  
  
    4.  <span data-ttu-id="25958-169">**Filtry ISAPI**</span><span class="sxs-lookup"><span data-stu-id="25958-169">**ISAPI Filters**</span></span>  
  
9. <span data-ttu-id="25958-170">Rozbalte položky s popiskem **nástroje webové správy**a potom vyberte **konzoly pro správu služby IIS**.</span><span class="sxs-lookup"><span data-stu-id="25958-170">Expand the item labeled **Web Management Tools**, and then select **IIS Management Console**.</span></span>  
  
10. <span data-ttu-id="25958-171">V části položka s názvem bez přípony **webové služby**, rozbalte položku **společné funkce protokolu Http**.</span><span class="sxs-lookup"><span data-stu-id="25958-171">Under the item labeled **World Wide Web Services**, expand **Common Http Features**.</span></span>  
  
11. <span data-ttu-id="25958-172">Zajistěte, aby **statický obsah** je vybrána.</span><span class="sxs-lookup"><span data-stu-id="25958-172">Make sure **Static Content** is selected.</span></span>  
  
12. <span data-ttu-id="25958-173">V části položka s názvem bez přípony **webové služby**, rozbalte položku **zabezpečení**.</span><span class="sxs-lookup"><span data-stu-id="25958-173">Under the item labeled **World Wide Web Services**, expand **Security**.</span></span>  
  
13. <span data-ttu-id="25958-174">Zajistěte, aby **ověřování systému Windows** je vybrána.</span><span class="sxs-lookup"><span data-stu-id="25958-174">Make sure **Windows Authentication** is selected.</span></span>  
  
14. <span data-ttu-id="25958-175">Rozbalte položky s popiskem **IIS 6 Management Compatibility**a potom vyberte **nástroje pro skriptování na služby IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="25958-175">Expand the item labeled **IIS 6 Management Compatibility**, and then select **IIS 6 Scripting Tools**.</span></span>  
  
15. <span data-ttu-id="25958-176">Rozbalte položky s popiskem **rozhraní Microsoft .NET Framework 3.0**a potom vyberte **aktivace Windows Communication Foundation Http**.</span><span class="sxs-lookup"><span data-stu-id="25958-176">Expand the item labeled **Microsoft .NET Framework 3.0**, and then select **Windows Communication Foundation Http Activation**.</span></span>  
  
16. <span data-ttu-id="25958-177">Klikněte na tlačítko**OK**.</span><span class="sxs-lookup"><span data-stu-id="25958-177">Click**OK**.</span></span>  
  
### <a name="to-install-iis-version-60-on-windows-server-2003"></a><span data-ttu-id="25958-178">Instalace služby IIS verze 6.0 na Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="25958-178">To install IIS version 6.0 on Windows Server 2003</span></span>  
  
1.  <span data-ttu-id="25958-179">Z **Správa serveru**, klikněte na tlačítko **přidat nebo odebrat roli**a potom klikněte na **Další**.</span><span class="sxs-lookup"><span data-stu-id="25958-179">From **Manage Your Server**, click **Add or remove a role**, and then click **Next**.</span></span>  
  
2.  <span data-ttu-id="25958-180">Vyberte **aplikační server (IIS, ASP.NET)** z **Role serveru** seznamu a pak klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="25958-180">Select **Application server (IIS, ASP.NET)** from the **Server Role** list, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="25958-181">Vyberte **povolit technologii ASP.NET** zaškrtněte políčko a potom klikněte na **Další**.</span><span class="sxs-lookup"><span data-stu-id="25958-181">Select **Enable ASP.NET** check box, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="25958-182">Pokud souhrn výběr správné, klikněte na tlačítko Další.</span><span class="sxs-lookup"><span data-stu-id="25958-182">If the summary of selections is correct, click Next.</span></span>  
  
### <a name="to-install-iis-version-51-on-windows-xp-with-service-pack-2-and-service-pack-3-installed"></a><span data-ttu-id="25958-183">Chcete-li nainstalovat službu IIS verze 5.1 v systému Windows XP s aktualizací Service Pack 2 a aktualizací Service Pack 3 nainstalovány</span><span class="sxs-lookup"><span data-stu-id="25958-183">To install IIS version 5.1 on Windows XP with Service Pack 2 and Service Pack 3 installed</span></span>  
  
1.  <span data-ttu-id="25958-184">V Ovládacích panelech klikněte na tlačítko **přidat nebo odebrat programy**.</span><span class="sxs-lookup"><span data-stu-id="25958-184">In Control Panel, click **Add or Remove Programs**.</span></span>  
  
2.  <span data-ttu-id="25958-185">V **přidat nebo odebrat programy** dialogové okno, klikněte na tlačítko **přidat nebo odebrat součásti systému Windows**.</span><span class="sxs-lookup"><span data-stu-id="25958-185">In the **Add or Remove Programs** dialog box, click **Add/Remove Windows Components**.</span></span>  
  
3.  <span data-ttu-id="25958-186">V **Průvodce součástmi systému Windows**, vyberte **Internetové informační služby (IIS)** zaškrtněte políčko a potom klikněte na **Další**.</span><span class="sxs-lookup"><span data-stu-id="25958-186">In the **Windows Components Wizard**, select the **Internet Information Services (IIS)** check box, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="25958-187">Pokud **soubory potřebné** se zobrazí dialogové okno, vložte disk instalace operačního systému, přejděte do složky i386 a pak klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="25958-187">If the **Files Needed** dialog box is displayed, insert your operating system installation disc, browse to the i386 folder, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="25958-188">Po dokončení instalace, klikněte na tlačítko **Dokončit**.</span><span class="sxs-lookup"><span data-stu-id="25958-188">When installation completes, click **Finish**.</span></span>  
  
6.  <span data-ttu-id="25958-189">Zavřete **přidat nebo odebrat programy** dialogové okno a potom zavřete **ovládací panely**.</span><span class="sxs-lookup"><span data-stu-id="25958-189">Close the **Add or Remove Programs** dialog box, and then close **Control Panel**.</span></span>  
  
### <a name="to-verify-the-installation-of-iis-and-aspnet"></a><span data-ttu-id="25958-190">Ověření instalace služby IIS a ASP.NET</span><span class="sxs-lookup"><span data-stu-id="25958-190">To verify the installation of IIS and ASP.NET</span></span>  
  
1.  <span data-ttu-id="25958-191">Uložte soubor HTML nalezen na konci tohoto tématu v kořenovém adresáři \InetPub\wwwroot s názvem Default.aspx.</span><span class="sxs-lookup"><span data-stu-id="25958-191">Save the HTML file found at the end of this topic in the root \InetPub\wwwroot directory and name it Default.aspx.</span></span>  
  
2.  <span data-ttu-id="25958-192">Otevřete okno prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="25958-192">Open a browser window.</span></span>  
  
3.  <span data-ttu-id="25958-193">Typ `http://localhost/Default.aspx` do pole Adresa a potom stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="25958-193">Type `http://localhost/Default.aspx` in the address box, and then press ENTER.</span></span>  
  
4.  <span data-ttu-id="25958-194">Webové stránky s textem "Hello World" by se zobrazit.</span><span class="sxs-lookup"><span data-stu-id="25958-194">A Web page with the text "Hello World" should appear.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="25958-195">Pokaždé, když instalujete novou verzi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], je nutné znovu zaregistrovat aspnet_isapi jako rozšíření webové služby pro službu IIS.</span><span class="sxs-lookup"><span data-stu-id="25958-195">Each time you install a new version of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], you must re-register aspnet_isapi as a Web service extension for IIS.</span></span> <span data-ttu-id="25958-196">Uděláte to tak, vydání `aspnet_regiis –I –enable` příkaz.</span><span class="sxs-lookup"><span data-stu-id="25958-196">To do so, issue the `aspnet_regiis –I –enable` command.</span></span>  
  
## <a name="sample-code"></a><span data-ttu-id="25958-197">Ukázkový kód</span><span class="sxs-lookup"><span data-stu-id="25958-197">Sample Code</span></span>  
  
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
