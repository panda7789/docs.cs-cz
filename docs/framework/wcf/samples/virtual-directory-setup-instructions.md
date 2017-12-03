---
title: "Pokyny pro instalaci virtuálního adresáře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c62cab5-81a4-48b6-ac8c-9ce33a85a157
caps.latest.revision: "36"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 72487c4a6720f80119beb837fbb3b5ea25ac3b93
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="virtual-directory-setup-instructions"></a><span data-ttu-id="49896-102">Pokyny pro instalaci virtuálního adresáře</span><span class="sxs-lookup"><span data-stu-id="49896-102">Virtual Directory Setup Instructions</span></span>
<span data-ttu-id="49896-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Ukázky jsou určeny k sdílejí společný virtuální adresář s názvem servicemodelsamples, který je namapovaný na %SystemDrive%\inetpub\wwwroot\servicemodelsamples složky.</span><span class="sxs-lookup"><span data-stu-id="49896-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] samples are intended to share a common virtual directory named servicemodelsamples that is mapped to the %SystemDrive%\inetpub\wwwroot\servicemodelsamples folder.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="49896-104">% SystemDrive % je obvykle C: nebo D:, v závislosti na umístění jednotky, kde je nainstalován Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="49896-104">%SystemDrive% is usually C: or D:, depending on the drive location where Internet Information Services (IIS) is installed.</span></span>  
  
 <span data-ttu-id="49896-105">Můžete spouštět soubory Setupvroot.bat a Cleanupvroot.bat z [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) se vytvořit virtuální adresář.</span><span class="sxs-lookup"><span data-stu-id="49896-105">You can run the Setupvroot.bat and Cleanupvroot.bat files from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) to create the virtual directory.</span></span> <span data-ttu-id="49896-106">Pokud ale chcete ručně vytvořit virtuální adresář, použijte následující postupy.</span><span class="sxs-lookup"><span data-stu-id="49896-106">If you prefer to create the virtual directory manually, use the following procedures.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="49896-107">Procedury</span><span class="sxs-lookup"><span data-stu-id="49896-107">Procedures</span></span>  
  
#### <a name="to-create-a-virtual-directory-in-iis-70-or-75"></a><span data-ttu-id="49896-108">Chcete-li vytvořit virtuální adresář ve službě IIS 7.0 nebo 7.5</span><span class="sxs-lookup"><span data-stu-id="49896-108">To create a virtual directory in IIS 7.0 or 7.5</span></span>  
  
1.  <span data-ttu-id="49896-109">Z **spustit** nabídky, klikněte na tlačítko **spustit**, pak zadejte **inetmgr** otevřete modul snap-in konzoly MMC Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="49896-109">From the **Start** menu, click **Run**, then type **inetmgr** to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2.  <span data-ttu-id="49896-110">V levém podokně rozbalte uzel s názvem počítače a pak rozbalte **lokality** uzlu.</span><span class="sxs-lookup"><span data-stu-id="49896-110">In the left pane, expand the node with the computer's name, and then expand the **Sites** node.</span></span>  
  
3.  <span data-ttu-id="49896-111">Klikněte pravým tlačítkem na **Default Web Site**a potom vyberte **přidat aplikaci** otevřete **okna Přidat aplikaci**.</span><span class="sxs-lookup"><span data-stu-id="49896-111">Right-click **Default Web Site**, and then select **Add Application** to open the **Add Application window**.</span></span>  
  
4.  <span data-ttu-id="49896-112">V okně zadejte `servicemodelsamples` jako alias pro virtuální adresář, který vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="49896-112">In the window, type `servicemodelsamples` as the alias for the virtual directory that you are creating.</span></span>  
  
5.  <span data-ttu-id="49896-113">Vytvořte na následující adresář: %SystemDrive%\inetpub\wwwroot\servicemodelsamples</span><span class="sxs-lookup"><span data-stu-id="49896-113">Create the following directory: %SystemDrive%\inetpub\wwwroot\servicemodelsamples</span></span>  
  
6.  <span data-ttu-id="49896-114">Nastavte na % SystemDrive%\inetpub\wwwroot\servicemodelsamples fyzickou cestu.</span><span class="sxs-lookup"><span data-stu-id="49896-114">Set the physical path to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  <span data-ttu-id="49896-115">Většina Ukázky WCF zkopírujte služby spustitelné soubory do tohoto umístění při sestavení.</span><span class="sxs-lookup"><span data-stu-id="49896-115">Most of the WCF samples copy service executable files to this location when built.</span></span>  
  
7.  <span data-ttu-id="49896-116">Click **OK**.</span><span class="sxs-lookup"><span data-stu-id="49896-116">Click **OK**.</span></span> <span data-ttu-id="49896-117">Webová aplikace je nyní vytvořen pro ukázky WCF.</span><span class="sxs-lookup"><span data-stu-id="49896-117">The Web application is now created for the WCF samples.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="49896-118">Tato úloha musí provést pouze jednou, protože všechny [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ukázky použijte stejné servicemodelsamples webové aplikace.</span><span class="sxs-lookup"><span data-stu-id="49896-118">This task must be performed only once, because all of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] samples use the same servicemodelsamples Web application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="49896-119">Pro účely této dokumentace termín `virtual directory` je totožná s `Web application`.</span><span class="sxs-lookup"><span data-stu-id="49896-119">For the purpose of this documentation, the term `virtual directory` is synonymous with `Web application`.</span></span>  
  
     <span data-ttu-id="49896-120">Kromě vytvoření virtuálního adresáře, musíte taky nastavit její vlastnosti, aby povolit [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] spuštění služeb.</span><span class="sxs-lookup"><span data-stu-id="49896-120">In addition to creating the virtual directory, you must also set its properties to enable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services to run.</span></span> <span data-ttu-id="49896-121">Níže naleznete podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="49896-121">See below for details.</span></span>  
  
#### <a name="to-create-a-virtual-directory-in-iis-51-or-60"></a><span data-ttu-id="49896-122">Chcete-li vytvořit virtuální adresář v IIS 5.1 nebo 6.0</span><span class="sxs-lookup"><span data-stu-id="49896-122">To create a virtual directory in IIS 5.1 or 6.0</span></span>  
  
1.  <span data-ttu-id="49896-123">Otevřete okno příkazového řádku a zadejte `start inetmgr` otevřete modul snap-in konzoly MMC Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="49896-123">Open a command prompt window and type `start inetmgr` to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2.  <span data-ttu-id="49896-124">V levém podokně rozbalte uzel s názvem počítače a pak rozbalte **weby** uzlu.</span><span class="sxs-lookup"><span data-stu-id="49896-124">In the left pane, expand the node with the computer's name, and then expand the **Web Sites** node.</span></span>  
  
3.  <span data-ttu-id="49896-125">Klikněte pravým tlačítkem na **Default Web Site** a vyberte **nový, virtuální adresář** otevřete Průvodce vytvořením virtuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="49896-125">Right-click **Default Web Site** and select **New, Virtual Directory** to open the Virtual Directory Creation wizard.</span></span>  
  
4.  <span data-ttu-id="49896-126">V průvodci zadejte `servicemodelsamples` jako alias pro virtuální adresář, který vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="49896-126">In the wizard, type `servicemodelsamples` as the alias for the virtual directory that you are creating.</span></span>  
  
5.  <span data-ttu-id="49896-127">Nastavte cestu k % SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="49896-127">Set the path to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span> <span data-ttu-id="49896-128">Většina [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ukázky zkopírujte služby spustitelné soubory do tohoto umístění při sestavení.</span><span class="sxs-lookup"><span data-stu-id="49896-128">Most of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] samples copy service executable files to this location when built.</span></span>  
  
6.  <span data-ttu-id="49896-129">Klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="49896-129">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="49896-130">Ve výchozím nastavení jsou vybrány následující zaškrtávací políčka:</span><span class="sxs-lookup"><span data-stu-id="49896-130">By default, the following check boxes are selected:</span></span>  
  
    -   <span data-ttu-id="49896-131">**Pro čtení**</span><span class="sxs-lookup"><span data-stu-id="49896-131">**Read**</span></span>  
  
    -   <span data-ttu-id="49896-132">**Spouštění skriptů (například ASP)**</span><span class="sxs-lookup"><span data-stu-id="49896-132">**Run scripts (such as ASP)**</span></span>  
  
8.  <span data-ttu-id="49896-133">Klikněte na tlačítko **Další**a potom klikněte na **Dokončit** dokončete průvodce.</span><span class="sxs-lookup"><span data-stu-id="49896-133">Click **Next**, and then click **Finish** to complete the wizard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="49896-134">Tato úloha musí provést pouze jednou, protože všechny [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ukázky používat stejné servicemodelsamples virtuální adresář.</span><span class="sxs-lookup"><span data-stu-id="49896-134">This task must be performed only once because all of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] samples use the same servicemodelsamples virtual directory.</span></span>  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-70-or-75"></a><span data-ttu-id="49896-135">Chcete-li nastavit další virtuální adresář vlastnosti ve službě IIS 7.0 nebo 7.5</span><span class="sxs-lookup"><span data-stu-id="49896-135">To set additional virtual directory properties in IIS 7.0 or 7.5</span></span>  
  
1.  <span data-ttu-id="49896-136">Klikněte na uzel servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="49896-136">Click the servicemodelsamples node.</span></span> <span data-ttu-id="49896-137">Ve spodní části okna jsou uvedeny dvě zobrazení.</span><span class="sxs-lookup"><span data-stu-id="49896-137">Along the bottom of the window, two views are listed.</span></span> <span data-ttu-id="49896-138">Vyberte **zobrazení funkcí** Pokud již není vybrána.</span><span class="sxs-lookup"><span data-stu-id="49896-138">Select **Features View** if it isn’t already selected.</span></span>  
  
2.  <span data-ttu-id="49896-139">Dvakrát klikněte na položku **procházení adresářů**.</span><span class="sxs-lookup"><span data-stu-id="49896-139">Double-click the entry for **Directory Browsing**.</span></span>  
  
3.  <span data-ttu-id="49896-140">V podokně Akce vyberte **povolit** možnost.</span><span class="sxs-lookup"><span data-stu-id="49896-140">In the Actions pane, select the **Enable** option.</span></span> <span data-ttu-id="49896-141">To umožňuje přístup k adresáři adresáře v aplikaci Internet Explorer, která pomáhá při ladění služby.</span><span class="sxs-lookup"><span data-stu-id="49896-141">This enables you to access the directory of the directory by using Internet Explorer, which helps when debugging a service.</span></span>  
  
 <span data-ttu-id="49896-142">Nakonec musíte nastavit vlastnosti zabezpečení servicemodelsamples složky, aby mělo přístup ostatní uživatelé.</span><span class="sxs-lookup"><span data-stu-id="49896-142">Finally, you must set the security properties of the servicemodelsamples folder to allow it to be accessed by others.</span></span> <span data-ttu-id="49896-143">Níže naleznete podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="49896-143">See below for details.</span></span>  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-51-or-60"></a><span data-ttu-id="49896-144">Chcete-li nastavit vlastnosti další virtuální adresář v IIS 5.1 a 6.0</span><span class="sxs-lookup"><span data-stu-id="49896-144">To set additional virtual directory properties in IIS 5.1 or 6.0</span></span>  
  
1.  <span data-ttu-id="49896-145">Klikněte pravým tlačítkem na uzel servicemodelsamples a pak klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="49896-145">Right-click the servicemodelsamples node and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="49896-146">Ve výchozím nastavení jsou vybrány následující zaškrtávací políčka:</span><span class="sxs-lookup"><span data-stu-id="49896-146">By default, the following check boxes are selected:</span></span>  
  
    -   <span data-ttu-id="49896-147">**Pro čtení**</span><span class="sxs-lookup"><span data-stu-id="49896-147">**Read**</span></span>  
  
    -   <span data-ttu-id="49896-148">**Navštíví protokolu**</span><span class="sxs-lookup"><span data-stu-id="49896-148">**Log visits**</span></span>  
  
    -   <span data-ttu-id="49896-149">**Index tento prostředek**</span><span class="sxs-lookup"><span data-stu-id="49896-149">**Index this resource**</span></span>  
  
3.  <span data-ttu-id="49896-150">Vyberte **procházení adresářů** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="49896-150">Select the **Directory browsing** check box.</span></span> <span data-ttu-id="49896-151">To umožňuje přístup k adresáři adresáře v aplikaci Internet Explorer, která pomáhá při ladění služby.</span><span class="sxs-lookup"><span data-stu-id="49896-151">This enables you to access the directory of the directory by using Internet Explorer, which helps when debugging a service.</span></span>  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-70-or-75"></a><span data-ttu-id="49896-152">Chcete-li nastavit vlastnosti zabezpečení složky ve službě IIS 7.0 nebo 7.5</span><span class="sxs-lookup"><span data-stu-id="49896-152">To set security properties of the folder in IIS 7.0 or 7.5</span></span>  
  
1.  <span data-ttu-id="49896-153">Přejděte na % SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="49896-153">Navigate to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  
  
2.  <span data-ttu-id="49896-154">Klikněte pravým tlačítkem na složku servicemodelsamples a klikněte na tlačítko **sdílené složky** nebo **sdílenou složku s**.</span><span class="sxs-lookup"><span data-stu-id="49896-154">Right-click the servicemodelsamples folder and click **Share** or **Share With**.</span></span>  
  
3.  <span data-ttu-id="49896-155">Klikněte na šipku nalevo od **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="49896-155">Click the down arrow to the left of the **Add** button.</span></span>  
  
4.  <span data-ttu-id="49896-156">Vyberte **najít** položku.</span><span class="sxs-lookup"><span data-stu-id="49896-156">Select the **Find** entry.</span></span> <span data-ttu-id="49896-157">**Vybrat uživatele nebo skupiny** otevře se okno.</span><span class="sxs-lookup"><span data-stu-id="49896-157">The **Select Users or Groups** window opens.</span></span>  
  
5.  <span data-ttu-id="49896-158">Klikněte na tlačítko **rozšířené**.</span><span class="sxs-lookup"><span data-stu-id="49896-158">Click **Advanced**.</span></span>  
  
6.  <span data-ttu-id="49896-159">Klikněte na tlačítko **umístění**.</span><span class="sxs-lookup"><span data-stu-id="49896-159">Click **Locations**.</span></span> <span data-ttu-id="49896-160">**Umístění** je nyní otevřené okno.</span><span class="sxs-lookup"><span data-stu-id="49896-160">The **Locations** window is now open.</span></span>  
  
7.  <span data-ttu-id="49896-161">Vyberte položku pro počítač používá.</span><span class="sxs-lookup"><span data-stu-id="49896-161">Select the entry for the computer being used.</span></span> <span data-ttu-id="49896-162">Je důležité vybrat místní počítač a ne položka pro všechny domény nebo sítě, které jsou uvedeny.</span><span class="sxs-lookup"><span data-stu-id="49896-162">It is important to select the local computer and not an entry for any domains or networks that are listed.</span></span> <span data-ttu-id="49896-163">Po výběru počítače, klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="49896-163">After you have selected the computer, click **OK**.</span></span>  
  
8.  <span data-ttu-id="49896-164">Klikněte na tlačítko **najít**.</span><span class="sxs-lookup"><span data-stu-id="49896-164">Click **Find Now**.</span></span> <span data-ttu-id="49896-165">Tím vyplníte výsledků hledání s objekty přidružené k místním počítači.</span><span class="sxs-lookup"><span data-stu-id="49896-165">This populates the search results with objects associated with the local computer.</span></span>  
  
9. <span data-ttu-id="49896-166">Najít **IIS_IUSRS** položku **název (relativní rozlišující název)** sloupce.</span><span class="sxs-lookup"><span data-stu-id="49896-166">Find the **IIS_IUSRS** entry in the **Name (Relative Distinguished Name)** column.</span></span> <span data-ttu-id="49896-167">Vyberte tuto položku a klikněte na **OK** hledání zavřete okno výsledků.</span><span class="sxs-lookup"><span data-stu-id="49896-167">Select that entry and click **OK** to close the search results window.</span></span>  
  
10. <span data-ttu-id="49896-168">Klikněte na tlačítko **OK** zavřete **vybrat uživatele nebo skupiny** okno.</span><span class="sxs-lookup"><span data-stu-id="49896-168">Click **OK** to close the **Select Users or Groups** window.</span></span>  
  
11. <span data-ttu-id="49896-169">Klikněte na tlačítko **sdílenou složku** a zachová tak změny.</span><span class="sxs-lookup"><span data-stu-id="49896-169">Click **Share** to persist the changes.</span></span>  
  
12. <span data-ttu-id="49896-170">Po dokončení se změny povolit sdílení, klikněte na tlačítko **provádí** zavřete **sdílení souborů** okno.</span><span class="sxs-lookup"><span data-stu-id="49896-170">After the changes to enable sharing are complete, click **Done** to close the **File Sharing** window.</span></span>  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-51-or-60"></a><span data-ttu-id="49896-171">Nastavit vlastnosti zabezpečení složky v IIS 5.1 nebo 6.0</span><span class="sxs-lookup"><span data-stu-id="49896-171">To set security properties of the folder in IIS 5.1 or 6.0</span></span>  
  
1.  <span data-ttu-id="49896-172">Přejděte na % SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="49896-172">Navigate to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  
  
2.  <span data-ttu-id="49896-173">Klikněte pravým tlačítkem myši **servicemodelsamples** složku a pak klikněte na tlačítko **sdílení a zabezpečení.**</span><span class="sxs-lookup"><span data-stu-id="49896-173">Right-click the **servicemodelsamples** folder and then click **Sharing and Security.**</span></span>  
  
3.  <span data-ttu-id="49896-174">Klikněte **zabezpečení** kartě.</span><span class="sxs-lookup"><span data-stu-id="49896-174">Click the **Security** tab.</span></span>  
  
4.  <span data-ttu-id="49896-175">Pokud používáte služby IIS 6.0, **skupiny nebo jméno uživatele** zaškrtněte políčko zda **účtu Guest Internet** je uveden.</span><span class="sxs-lookup"><span data-stu-id="49896-175">If you are using IIS 6.0, in the **Group or user names** box, check whether **Internet Guest Account** is listed.</span></span>  
  
     <span data-ttu-id="49896-176">Pokud v seznamu není:</span><span class="sxs-lookup"><span data-stu-id="49896-176">If it is not listed:</span></span>  
  
    1.  <span data-ttu-id="49896-177">Klikněte na tlačítko **spustit** a pak klikněte na **ovládací panely**.</span><span class="sxs-lookup"><span data-stu-id="49896-177">Click **Start** and then click **Control Panel**.</span></span>  
  
    2.  <span data-ttu-id="49896-178">Pokud se nezobrazí **uživatelské účty** ikonu, klikněte na tlačítko **přepnout na zobrazení kategorií**.</span><span class="sxs-lookup"><span data-stu-id="49896-178">If you do not see the **User Accounts** icon, click **Switch to Category View**.</span></span>  
  
    3.  <span data-ttu-id="49896-179">Klikněte **uživatelské účty** ikonu.</span><span class="sxs-lookup"><span data-stu-id="49896-179">Click the **User Accounts** icon.</span></span>  
  
    4.  <span data-ttu-id="49896-180">V části "nebo vyberte ikonu Ovládací panely," klikněte na tlačítko **uživatelské účty**.</span><span class="sxs-lookup"><span data-stu-id="49896-180">Under "or pick a Control Panel icon," click **User Accounts**.</span></span>  
  
    5.  <span data-ttu-id="49896-181">V **uživatelské účty** dialogové okno, klikněte **Upřesnit** kartě.</span><span class="sxs-lookup"><span data-stu-id="49896-181">In the **User Accounts** dialog box, click the **Advanced** tab.</span></span>  
  
    6.  <span data-ttu-id="49896-182">Klikněte na tlačítko **rozšířené**.</span><span class="sxs-lookup"><span data-stu-id="49896-182">Click **Advanced**.</span></span>  
  
    7.  <span data-ttu-id="49896-183">V **místní uživatelé a skupiny** dialogové okno, rozbalte kliknutím **uživatelé** složky.</span><span class="sxs-lookup"><span data-stu-id="49896-183">In the **Local Users and Groups** dialog box, click to expand the **Users** folder.</span></span>  
  
    8.  <span data-ttu-id="49896-184">V pravém podokně klikněte dvakrát na **účtu Guest Internet**.</span><span class="sxs-lookup"><span data-stu-id="49896-184">In the right pane, double-click **Internet Guest Account**.</span></span>  
  
    9. <span data-ttu-id="49896-185">V **vlastnosti** dialogové okno, kopie tento název používá jako účet guest Internetu.</span><span class="sxs-lookup"><span data-stu-id="49896-185">In the **Properties** dialog box, copy the name used as the Internet guest account.</span></span> <span data-ttu-id="49896-186">Ve výchozím nastavení název začíná řetězcem "USR_" a název počítače.</span><span class="sxs-lookup"><span data-stu-id="49896-186">By default, the name begins with "USR_" followed by the name of the computer.</span></span>  
  
    10. <span data-ttu-id="49896-187">Zavřít **vlastnosti** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="49896-187">Close the **Properties** dialog box.</span></span>  
  
    11. <span data-ttu-id="49896-188">Zavřít **místní uživatelé a skupiny** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="49896-188">Close the **Local Users and Groups** dialog box.</span></span>  
  
    12. <span data-ttu-id="49896-189">Zavřít **uživatelské účty** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="49896-189">Close the **User Accounts** dialog box.</span></span>  
  
    13. <span data-ttu-id="49896-190">Zavřete dalších **uživatelské účty** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="49896-190">Close the other **User Accounts** dialog box.</span></span>  
  
    14. <span data-ttu-id="49896-191">V **servicemodelsamples vlastnosti** v dialogovém **zabezpečení** , klikněte na **přidat**.</span><span class="sxs-lookup"><span data-stu-id="49896-191">In the **servicemodelsamples Properties** dialog box, on the **Security** tab, click **Add**.</span></span>  
  
    15. <span data-ttu-id="49896-192">Zadejte název počítače, za nímž následuje zpětné lomítko, pak vložit název účtu uživatele Internetu, například myMachineName\\InternetGuestAccountName %</span><span class="sxs-lookup"><span data-stu-id="49896-192">Type the name of the computer followed by a backslash, then paste the name of the Internet user account, for example, myMachineName\\%InternetGuestAccountName%</span></span>  
  
    16. <span data-ttu-id="49896-193">Klikněte na tlačítko **Kontrola názvů** ověření přidání.</span><span class="sxs-lookup"><span data-stu-id="49896-193">Click **Check Names** to verify the addition.</span></span> <span data-ttu-id="49896-194">Pokud je platný, název je v velkými písmeny a jsou podtržené.</span><span class="sxs-lookup"><span data-stu-id="49896-194">If it is valid, the name is in all capital letters and is underlined.</span></span>  
  
5.  <span data-ttu-id="49896-195">Pro služby IIS 6.0, také zkontrolujte, jestli síťové služby je uvedený v **skupiny nebo jméno uživatele** pole.</span><span class="sxs-lookup"><span data-stu-id="49896-195">For IIS 6.0, also check that NETWORK SERVICE is listed in the **Group or user names** box.</span></span>  
  
     <span data-ttu-id="49896-196">Pokud není uvedené síťové služby:</span><span class="sxs-lookup"><span data-stu-id="49896-196">If NETWORK SERVICE is not listed:</span></span>  
  
    1.  <span data-ttu-id="49896-197">Klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="49896-197">Click **Add**.</span></span>  
  
    2.  <span data-ttu-id="49896-198">V **vybrat uživatele nebo skupiny** dialogové okno, zadejte název počítače, následuje zpětné lomítko.</span><span class="sxs-lookup"><span data-stu-id="49896-198">In the **Select Users or Groups** dialog box, type the name of the computer followed by a backslash.</span></span>  
  
    3.  <span data-ttu-id="49896-199">Typ **služby** po zpětné lomítko (bez mezery).</span><span class="sxs-lookup"><span data-stu-id="49896-199">Type **service** after the backslash (no space).</span></span>  
  
    4.  <span data-ttu-id="49896-200">Klikněte na tlačítko **Zkontrolujte názvy**.</span><span class="sxs-lookup"><span data-stu-id="49896-200">Click **Check names**.</span></span>  
  
    5.  <span data-ttu-id="49896-201">Pokud je nalezeno více jmen, vyberte **síťové služby** a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="49896-201">If multiple names are found, select **NETWORK SERVICE** and click **OK**.</span></span>  
  
    6.  <span data-ttu-id="49896-202">Klikněte na tlačítko **OK** zavřete **vybrat uživatele nebo skupiny** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="49896-202">Click **OK** to close the **Select Users or Groups** dialog box.</span></span>  
  
6.  <span data-ttu-id="49896-203">Pokud používáte systém Windows XP SP2 se služba IIS 5.1, zkontrolujte, jestli jsou v uvedený účet Guest Internet a ASPNET **skupiny nebo jméno uživatele** pole.</span><span class="sxs-lookup"><span data-stu-id="49896-203">If you are using Windows XP SP2 with IIS 5.1, check that both Internet Guest Account and ASPNET are listed in the **Group or user names** box.</span></span>  
  
     <span data-ttu-id="49896-204">Upozorňujeme, že uživatel ASPNET může být člen předdefinované **uživatelé** skupiny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="49896-204">Note that the ASPNET user may be a member of the built-in **Users** security group.</span></span> <span data-ttu-id="49896-205">Pokud ano, pak pokud **uživatelé** skupina je uvedena v dialogovém okně, není potřeba ji přidat jako samostatný položky do seznamu povolených uživatelů.</span><span class="sxs-lookup"><span data-stu-id="49896-205">If so, then if the **Users** group is listed in the dialog box, you do not need to add it as a separate item to the list of permitted users.</span></span>  
  
     <span data-ttu-id="49896-206">Zkontrolujte, zda ASPNET je součástí **uživatelé** skupiny zabezpečení:</span><span class="sxs-lookup"><span data-stu-id="49896-206">To check if ASPNET is part of the **Users** security group:</span></span>  
  
    1.  <span data-ttu-id="49896-207">Na **spustit** nabídky, klikněte na tlačítko **ovládací panely**.</span><span class="sxs-lookup"><span data-stu-id="49896-207">On the **Start** menu, click **Control Panel**.</span></span>  
  
    2.  <span data-ttu-id="49896-208">Klikněte **uživatelské účty** ikonu.</span><span class="sxs-lookup"><span data-stu-id="49896-208">Click the **User Accounts** icon.</span></span>  
  
    3.  <span data-ttu-id="49896-209">V **skupiny** sloupce, zkontrolujte, zda hodnota **ASPNET** je "Uživatelé."</span><span class="sxs-lookup"><span data-stu-id="49896-209">In the **Group** column, check that the value for **ASPNET** is "Users."</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49896-210">Viz také</span><span class="sxs-lookup"><span data-stu-id="49896-210">See Also</span></span>  
 [<span data-ttu-id="49896-211">Internetové informace o pokyny k hostování služby</span><span class="sxs-lookup"><span data-stu-id="49896-211">Internet Information Service Hosting Instructions</span></span>](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)
