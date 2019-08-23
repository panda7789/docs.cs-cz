---
title: Pokyny pro instalaci virtuálního adresáře
ms.date: 03/30/2017
ms.assetid: 3c62cab5-81a4-48b6-ac8c-9ce33a85a157
ms.openlocfilehash: f755fadf6bef2bdd58fd31f3460a143b8f52eddf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966731"
---
# <a name="virtual-directory-setup-instructions"></a><span data-ttu-id="56e94-102">Pokyny pro instalaci virtuálního adresáře</span><span class="sxs-lookup"><span data-stu-id="56e94-102">Virtual Directory Setup Instructions</span></span>
<span data-ttu-id="56e94-103">Ukázky Windows Communication Foundation (WCF) mají za cíl sdílet společný virtuální adresář s názvem ServiceModelSamples, který je namapován na složku%SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="56e94-103">The Windows Communication Foundation (WCF) samples are intended to share a common virtual directory named servicemodelsamples that is mapped to the %SystemDrive%\inetpub\wwwroot\servicemodelsamples folder.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="56e94-104">Jednotka% SystemDrive% je obvykle C: nebo D:, v závislosti na umístění jednotky, kde je nainstalovaná Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="56e94-104">%SystemDrive% is usually C: or D:, depending on the drive location where Internet Information Services (IIS) is installed.</span></span>  
  
 <span data-ttu-id="56e94-105">Můžete spustit soubory Setupvroot. bat a cleanupvroot. bat z [procesu jednorázového nastavení pro Windows Communication Foundation Samples pro](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) vytvoření virtuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="56e94-105">You can run the Setupvroot.bat and Cleanupvroot.bat files from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) to create the virtual directory.</span></span> <span data-ttu-id="56e94-106">Pokud budete chtít vytvořit virtuální adresář ručně, použijte následující postupy.</span><span class="sxs-lookup"><span data-stu-id="56e94-106">If you prefer to create the virtual directory manually, use the following procedures.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="56e94-107">Procedury</span><span class="sxs-lookup"><span data-stu-id="56e94-107">Procedures</span></span>  
  
#### <a name="to-create-a-virtual-directory-in-iis-70-or-75"></a><span data-ttu-id="56e94-108">Vytvoření virtuálního adresáře ve službě IIS 7,0 nebo 7,5</span><span class="sxs-lookup"><span data-stu-id="56e94-108">To create a virtual directory in IIS 7.0 or 7.5</span></span>  
  
1. <span data-ttu-id="56e94-109">V nabídce **Start** klikněte na tlačítko **Spustit**a zadejte příkaz **inetmgr** . tím otevřete modul snap-in konzoly MMC Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="56e94-109">From the **Start** menu, click **Run**, then type **inetmgr** to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2. <span data-ttu-id="56e94-110">V levém podokně rozbalte uzel s názvem počítače a potom rozbalte uzel **lokality** .</span><span class="sxs-lookup"><span data-stu-id="56e94-110">In the left pane, expand the node with the computer's name, and then expand the **Sites** node.</span></span>  
  
3. <span data-ttu-id="56e94-111">Klikněte pravým tlačítkem na **výchozí web**a pak vyberte **Přidat aplikaci** . otevře se **okno Přidat aplikaci**.</span><span class="sxs-lookup"><span data-stu-id="56e94-111">Right-click **Default Web Site**, and then select **Add Application** to open the **Add Application window**.</span></span>  
  
4. <span data-ttu-id="56e94-112">V okně zadejte `servicemodelsamples` alias pro virtuální adresář, který vytváříte.</span><span class="sxs-lookup"><span data-stu-id="56e94-112">In the window, type `servicemodelsamples` as the alias for the virtual directory that you are creating.</span></span>  
  
5. <span data-ttu-id="56e94-113">Vytvořte následující adresář:%SystemDrive%\inetpub\wwwroot\servicemodelsamples</span><span class="sxs-lookup"><span data-stu-id="56e94-113">Create the following directory: %SystemDrive%\inetpub\wwwroot\servicemodelsamples</span></span>  
  
6. <span data-ttu-id="56e94-114">Nastavte fyzickou cestu na%SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="56e94-114">Set the physical path to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  <span data-ttu-id="56e94-115">Většina ukázek WCF při sestavení zkopíruje spustitelné soubory služby do tohoto umístění.</span><span class="sxs-lookup"><span data-stu-id="56e94-115">Most of the WCF samples copy service executable files to this location when built.</span></span>  
  
7. <span data-ttu-id="56e94-116">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="56e94-116">Click **OK**.</span></span> <span data-ttu-id="56e94-117">Webová aplikace je nyní vytvořena pro ukázky WCF.</span><span class="sxs-lookup"><span data-stu-id="56e94-117">The Web application is now created for the WCF samples.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="56e94-118">Tato úloha musí být prováděna pouze jednou, protože všechny ukázky služby WCF používají stejnou webovou aplikaci ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="56e94-118">This task must be performed only once, because all of the WCF samples use the same servicemodelsamples Web application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="56e94-119">Pro účely této dokumentace je termínem `virtual directory` synonymum. `Web application`</span><span class="sxs-lookup"><span data-stu-id="56e94-119">For the purpose of this documentation, the term `virtual directory` is synonymous with `Web application`.</span></span>  
  
     <span data-ttu-id="56e94-120">Kromě vytváření virtuálního adresáře musíte také nastavit jeho vlastnosti, aby bylo možné spouštět služby WCF.</span><span class="sxs-lookup"><span data-stu-id="56e94-120">In addition to creating the virtual directory, you must also set its properties to enable WCF services to run.</span></span> <span data-ttu-id="56e94-121">Podrobnosti najdete níže.</span><span class="sxs-lookup"><span data-stu-id="56e94-121">See below for details.</span></span>  
  
#### <a name="to-create-a-virtual-directory-in-iis-51-or-60"></a><span data-ttu-id="56e94-122">Vytvoření virtuálního adresáře ve službě IIS 5,1 nebo 6,0</span><span class="sxs-lookup"><span data-stu-id="56e94-122">To create a virtual directory in IIS 5.1 or 6.0</span></span>  
  
1. <span data-ttu-id="56e94-123">Otevřete okno příkazového řádku a zadejte `start inetmgr` a otevřete modul snap-in konzoly MMC Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="56e94-123">Open a command prompt window and type `start inetmgr` to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2. <span data-ttu-id="56e94-124">V levém podokně rozbalte uzel s názvem počítače a potom rozbalte uzel **weby** .</span><span class="sxs-lookup"><span data-stu-id="56e94-124">In the left pane, expand the node with the computer's name, and then expand the **Web Sites** node.</span></span>  
  
3. <span data-ttu-id="56e94-125">Klikněte pravým tlačítkem na **výchozí web** a vyberte **Nový, virtuální adresář** . otevře se Průvodce vytvořením virtuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="56e94-125">Right-click **Default Web Site** and select **New, Virtual Directory** to open the Virtual Directory Creation wizard.</span></span>  
  
4. <span data-ttu-id="56e94-126">V průvodci zadejte `servicemodelsamples` alias pro virtuální adresář, který vytváříte.</span><span class="sxs-lookup"><span data-stu-id="56e94-126">In the wizard, type `servicemodelsamples` as the alias for the virtual directory that you are creating.</span></span>  
  
5. <span data-ttu-id="56e94-127">Nastavte cestu na%SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="56e94-127">Set the path to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span> <span data-ttu-id="56e94-128">Většina ukázek WCF při sestavení zkopíruje spustitelné soubory služby do tohoto umístění.</span><span class="sxs-lookup"><span data-stu-id="56e94-128">Most of the WCF samples copy service executable files to this location when built.</span></span>  
  
6. <span data-ttu-id="56e94-129">Klikněte na **Další**.</span><span class="sxs-lookup"><span data-stu-id="56e94-129">Click **Next**.</span></span>  
  
7. <span data-ttu-id="56e94-130">Ve výchozím nastavení jsou zaškrtnuta následující zaškrtávací políčka:</span><span class="sxs-lookup"><span data-stu-id="56e94-130">By default, the following check boxes are selected:</span></span>  
  
    - <span data-ttu-id="56e94-131">**Read**</span><span class="sxs-lookup"><span data-stu-id="56e94-131">**Read**</span></span>  
  
    - <span data-ttu-id="56e94-132">**Spouštění skriptů (například ASP)**</span><span class="sxs-lookup"><span data-stu-id="56e94-132">**Run scripts (such as ASP)**</span></span>  
  
8. <span data-ttu-id="56e94-133">Klikněte na tlačítko **Další**a dokončete průvodce kliknutím na tlačítko **Dokončit** .</span><span class="sxs-lookup"><span data-stu-id="56e94-133">Click **Next**, and then click **Finish** to complete the wizard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="56e94-134">Tato úloha se musí provést jenom jednou, protože všechny ukázky WCF používají stejný virtuální adresář ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="56e94-134">This task must be performed only once because all of the WCF samples use the same servicemodelsamples virtual directory.</span></span>  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-70-or-75"></a><span data-ttu-id="56e94-135">Nastavení dalších vlastností virtuálního adresáře ve službě IIS 7,0 nebo 7,5</span><span class="sxs-lookup"><span data-stu-id="56e94-135">To set additional virtual directory properties in IIS 7.0 or 7.5</span></span>  
  
1. <span data-ttu-id="56e94-136">Klikněte na uzel ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="56e94-136">Click the servicemodelsamples node.</span></span> <span data-ttu-id="56e94-137">Podél dolního okraje okna jsou uvedena dvě zobrazení.</span><span class="sxs-lookup"><span data-stu-id="56e94-137">Along the bottom of the window, two views are listed.</span></span> <span data-ttu-id="56e94-138">Vyberte **zobrazení funkcí** , pokud ještě není vybrané.</span><span class="sxs-lookup"><span data-stu-id="56e94-138">Select **Features View** if it isn’t already selected.</span></span>  
  
2. <span data-ttu-id="56e94-139">Dvakrát klikněte na položku pro **procházení adresářů**.</span><span class="sxs-lookup"><span data-stu-id="56e94-139">Double-click the entry for **Directory Browsing**.</span></span>  
  
3. <span data-ttu-id="56e94-140">V podokně Akce vyberte možnost **Povolit** .</span><span class="sxs-lookup"><span data-stu-id="56e94-140">In the Actions pane, select the **Enable** option.</span></span> <span data-ttu-id="56e94-141">To umožňuje přístup k adresáři adresáře pomocí aplikace Internet Explorer, která pomáhá při ladění služby.</span><span class="sxs-lookup"><span data-stu-id="56e94-141">This enables you to access the directory of the directory by using Internet Explorer, which helps when debugging a service.</span></span>  
  
 <span data-ttu-id="56e94-142">Nakonec musíte nastavit vlastnosti zabezpečení pro složku ServiceModelSamples, aby k ní měli přístup jiní uživatelé.</span><span class="sxs-lookup"><span data-stu-id="56e94-142">Finally, you must set the security properties of the servicemodelsamples folder to allow it to be accessed by others.</span></span> <span data-ttu-id="56e94-143">Podrobnosti najdete níže.</span><span class="sxs-lookup"><span data-stu-id="56e94-143">See below for details.</span></span>  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-51-or-60"></a><span data-ttu-id="56e94-144">Nastavení dalších vlastností virtuálního adresáře ve službě IIS 5,1 nebo 6,0</span><span class="sxs-lookup"><span data-stu-id="56e94-144">To set additional virtual directory properties in IIS 5.1 or 6.0</span></span>  
  
1. <span data-ttu-id="56e94-145">Klikněte pravým tlačítkem na uzel ServiceModelSamples a pak klikněte na **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="56e94-145">Right-click the servicemodelsamples node and then click **Properties**.</span></span>  
  
2. <span data-ttu-id="56e94-146">Ve výchozím nastavení jsou zaškrtnuta následující zaškrtávací políčka:</span><span class="sxs-lookup"><span data-stu-id="56e94-146">By default, the following check boxes are selected:</span></span>  
  
    - <span data-ttu-id="56e94-147">**Read**</span><span class="sxs-lookup"><span data-stu-id="56e94-147">**Read**</span></span>  
  
    - <span data-ttu-id="56e94-148">**Protokolovat návštěvy**</span><span class="sxs-lookup"><span data-stu-id="56e94-148">**Log visits**</span></span>  
  
    - <span data-ttu-id="56e94-149">**Index tohoto prostředku**</span><span class="sxs-lookup"><span data-stu-id="56e94-149">**Index this resource**</span></span>  
  
3. <span data-ttu-id="56e94-150">Zaškrtněte políčko **procházení adresářů** .</span><span class="sxs-lookup"><span data-stu-id="56e94-150">Select the **Directory browsing** check box.</span></span> <span data-ttu-id="56e94-151">To umožňuje přístup k adresáři adresáře pomocí aplikace Internet Explorer, která pomáhá při ladění služby.</span><span class="sxs-lookup"><span data-stu-id="56e94-151">This enables you to access the directory of the directory by using Internet Explorer, which helps when debugging a service.</span></span>  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-70-or-75"></a><span data-ttu-id="56e94-152">Nastavení vlastností zabezpečení složky ve službě IIS 7,0 nebo 7,5</span><span class="sxs-lookup"><span data-stu-id="56e94-152">To set security properties of the folder in IIS 7.0 or 7.5</span></span>  
  
1. <span data-ttu-id="56e94-153">Přejít na%SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="56e94-153">Navigate to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  
  
2. <span data-ttu-id="56e94-154">Klikněte pravým tlačítkem na složku ServiceModelSamples a pak klikněte na **sdílet** nebo **sdílet s**.</span><span class="sxs-lookup"><span data-stu-id="56e94-154">Right-click the servicemodelsamples folder and click **Share** or **Share With**.</span></span>  
  
3. <span data-ttu-id="56e94-155">Klikněte na šipku dolů nalevo od tlačítka **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="56e94-155">Click the down arrow to the left of the **Add** button.</span></span>  
  
4. <span data-ttu-id="56e94-156">Vyberte položku **Najít** .</span><span class="sxs-lookup"><span data-stu-id="56e94-156">Select the **Find** entry.</span></span> <span data-ttu-id="56e94-157">Otevře se okno **Vybrat uživatele nebo skupiny** .</span><span class="sxs-lookup"><span data-stu-id="56e94-157">The **Select Users or Groups** window opens.</span></span>  
  
5. <span data-ttu-id="56e94-158">Klikněte na tlačítko **Advanced**.</span><span class="sxs-lookup"><span data-stu-id="56e94-158">Click **Advanced**.</span></span>  
  
6. <span data-ttu-id="56e94-159">Klikněte na **umístění**.</span><span class="sxs-lookup"><span data-stu-id="56e94-159">Click **Locations**.</span></span> <span data-ttu-id="56e94-160">Okno **umístění** je nyní otevřeno.</span><span class="sxs-lookup"><span data-stu-id="56e94-160">The **Locations** window is now open.</span></span>  
  
7. <span data-ttu-id="56e94-161">Vyberte položku pro používaný počítač.</span><span class="sxs-lookup"><span data-stu-id="56e94-161">Select the entry for the computer being used.</span></span> <span data-ttu-id="56e94-162">Je důležité vybrat místní počítač a nikoli položku pro žádné domény nebo sítě, které jsou uvedeny v seznamu.</span><span class="sxs-lookup"><span data-stu-id="56e94-162">It is important to select the local computer and not an entry for any domains or networks that are listed.</span></span> <span data-ttu-id="56e94-163">Po výběru počítače klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="56e94-163">After you have selected the computer, click **OK**.</span></span>  
  
8. <span data-ttu-id="56e94-164">Klikněte na **Najít**.</span><span class="sxs-lookup"><span data-stu-id="56e94-164">Click **Find Now**.</span></span> <span data-ttu-id="56e94-165">Tím se výsledky hledání naplní objekty, které jsou přidružené k místnímu počítači.</span><span class="sxs-lookup"><span data-stu-id="56e94-165">This populates the search results with objects associated with the local computer.</span></span>  
  
9. <span data-ttu-id="56e94-166">Najděte položku **IIS_IUSRS** ve sloupci **název (relativní rozlišující název)** .</span><span class="sxs-lookup"><span data-stu-id="56e94-166">Find the **IIS_IUSRS** entry in the **Name (Relative Distinguished Name)** column.</span></span> <span data-ttu-id="56e94-167">Vyberte tuto položku a kliknutím na tlačítko **OK** zavřete okno výsledků hledání.</span><span class="sxs-lookup"><span data-stu-id="56e94-167">Select that entry and click **OK** to close the search results window.</span></span>  
  
10. <span data-ttu-id="56e94-168">Kliknutím na tlačítko **OK** zavřete okno **Vybrat uživatele nebo skupiny** .</span><span class="sxs-lookup"><span data-stu-id="56e94-168">Click **OK** to close the **Select Users or Groups** window.</span></span>  
  
11. <span data-ttu-id="56e94-169">Kliknutím na **sdílet** zachovejte změny.</span><span class="sxs-lookup"><span data-stu-id="56e94-169">Click **Share** to persist the changes.</span></span>  
  
12. <span data-ttu-id="56e94-170">Po dokončení změn pro povolení sdílení klikněte na Hotovo a zavřete okno **sdílení souborů** .</span><span class="sxs-lookup"><span data-stu-id="56e94-170">After the changes to enable sharing are complete, click **Done** to close the **File Sharing** window.</span></span>  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-51-or-60"></a><span data-ttu-id="56e94-171">Nastavení vlastností zabezpečení složky ve službě IIS 5,1 nebo 6,0</span><span class="sxs-lookup"><span data-stu-id="56e94-171">To set security properties of the folder in IIS 5.1 or 6.0</span></span>  
  
1. <span data-ttu-id="56e94-172">Přejít na%SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="56e94-172">Navigate to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  
  
2. <span data-ttu-id="56e94-173">Klikněte pravým tlačítkem na složku **ServiceModelSamples** a pak klikněte na **sdílení a zabezpečení.**</span><span class="sxs-lookup"><span data-stu-id="56e94-173">Right-click the **servicemodelsamples** folder and then click **Sharing and Security.**</span></span>  
  
3. <span data-ttu-id="56e94-174">Klikněte na kartu **zabezpečení** .</span><span class="sxs-lookup"><span data-stu-id="56e94-174">Click the **Security** tab.</span></span>  
  
4. <span data-ttu-id="56e94-175">Pokud používáte službu IIS 6,0, v poli **název skupiny nebo jméno uživatele** ověřte, zda je uveden **účet internetového účtu Guest** .</span><span class="sxs-lookup"><span data-stu-id="56e94-175">If you are using IIS 6.0, in the **Group or user names** box, check whether **Internet Guest Account** is listed.</span></span>  
  
     <span data-ttu-id="56e94-176">Pokud není uveden:</span><span class="sxs-lookup"><span data-stu-id="56e94-176">If it is not listed:</span></span>  
  
    1. <span data-ttu-id="56e94-177">Klikněte na tlačítko **Start** a poté na příkaz **Ovládací panely**.</span><span class="sxs-lookup"><span data-stu-id="56e94-177">Click **Start** and then click **Control Panel**.</span></span>  
  
    2. <span data-ttu-id="56e94-178">Pokud se nezobrazí ikona **uživatelské účty** , klikněte na **Přepnout do zobrazení kategorií**.</span><span class="sxs-lookup"><span data-stu-id="56e94-178">If you do not see the **User Accounts** icon, click **Switch to Category View**.</span></span>  
  
    3. <span data-ttu-id="56e94-179">Klikněte na ikonu **uživatelské účty** .</span><span class="sxs-lookup"><span data-stu-id="56e94-179">Click the **User Accounts** icon.</span></span>  
  
    4. <span data-ttu-id="56e94-180">V části nebo vyberte ikonu ovládacího panelu, klikněte na **uživatelské účty**.</span><span class="sxs-lookup"><span data-stu-id="56e94-180">Under "or pick a Control Panel icon," click **User Accounts**.</span></span>  
  
    5. <span data-ttu-id="56e94-181">V dialogovém okně **uživatelské účty** klikněte na kartu **Upřesnit** .</span><span class="sxs-lookup"><span data-stu-id="56e94-181">In the **User Accounts** dialog box, click the **Advanced** tab.</span></span>  
  
    6. <span data-ttu-id="56e94-182">Klikněte na tlačítko **Advanced**.</span><span class="sxs-lookup"><span data-stu-id="56e94-182">Click **Advanced**.</span></span>  
  
    7. <span data-ttu-id="56e94-183">V dialogovém okně **místní uživatelé a skupiny** rozbalte složku **Uživatelé** kliknutím.</span><span class="sxs-lookup"><span data-stu-id="56e94-183">In the **Local Users and Groups** dialog box, click to expand the **Users** folder.</span></span>  
  
    8. <span data-ttu-id="56e94-184">V pravém podokně dvakrát klikněte na možnost **účet internetového účtu Guest**.</span><span class="sxs-lookup"><span data-stu-id="56e94-184">In the right pane, double-click **Internet Guest Account**.</span></span>  
  
    9. <span data-ttu-id="56e94-185">V dialogovém okně **vlastnosti** zkopírujte název používaný jako internetový účet hosta.</span><span class="sxs-lookup"><span data-stu-id="56e94-185">In the **Properties** dialog box, copy the name used as the Internet guest account.</span></span> <span data-ttu-id="56e94-186">Ve výchozím nastavení začíná název "USR_" následovaný názvem počítače.</span><span class="sxs-lookup"><span data-stu-id="56e94-186">By default, the name begins with "USR_" followed by the name of the computer.</span></span>  
  
    10. <span data-ttu-id="56e94-187">Zavřete dialogové okno **vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="56e94-187">Close the **Properties** dialog box.</span></span>  
  
    11. <span data-ttu-id="56e94-188">Zavřete dialogové okno **místní uživatelé a skupiny** .</span><span class="sxs-lookup"><span data-stu-id="56e94-188">Close the **Local Users and Groups** dialog box.</span></span>  
  
    12. <span data-ttu-id="56e94-189">Zavřete dialogové okno **uživatelské účty** .</span><span class="sxs-lookup"><span data-stu-id="56e94-189">Close the **User Accounts** dialog box.</span></span>  
  
    13. <span data-ttu-id="56e94-190">Zavřete dialogové okno ostatní **uživatelské účty** .</span><span class="sxs-lookup"><span data-stu-id="56e94-190">Close the other **User Accounts** dialog box.</span></span>  
  
    14. <span data-ttu-id="56e94-191">V dialogovém okně **vlastnosti ServiceModelSamples** na kartě **zabezpečení** klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="56e94-191">In the **servicemodelsamples Properties** dialog box, on the **Security** tab, click **Add**.</span></span>  
  
    15. <span data-ttu-id="56e94-192">Zadejte název počítače následovaný zpětným lomítkem a pak vložte název internetového uživatelského účtu, například myMachineName\\% InternetGuestAccountName%.</span><span class="sxs-lookup"><span data-stu-id="56e94-192">Type the name of the computer followed by a backslash, then paste the name of the Internet user account, for example, myMachineName\\%InternetGuestAccountName%</span></span>  
  
    16. <span data-ttu-id="56e94-193">Kliknutím na **Kontrola názvů** ověřte přidání.</span><span class="sxs-lookup"><span data-stu-id="56e94-193">Click **Check Names** to verify the addition.</span></span> <span data-ttu-id="56e94-194">Pokud je platný, jméno je velkými písmeny a je podtržené.</span><span class="sxs-lookup"><span data-stu-id="56e94-194">If it is valid, the name is in all capital letters and is underlined.</span></span>  
  
5. <span data-ttu-id="56e94-195">V případě služby IIS 6,0 zaškrtněte políčko síťová služba je uvedena v poli **název skupiny nebo jméno uživatele** .</span><span class="sxs-lookup"><span data-stu-id="56e94-195">For IIS 6.0, also check that NETWORK SERVICE is listed in the **Group or user names** box.</span></span>  
  
     <span data-ttu-id="56e94-196">Pokud síťová služba není uvedená:</span><span class="sxs-lookup"><span data-stu-id="56e94-196">If NETWORK SERVICE is not listed:</span></span>  
  
    1. <span data-ttu-id="56e94-197">Klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="56e94-197">Click **Add**.</span></span>  
  
    2. <span data-ttu-id="56e94-198">V dialogovém okně **Vybrat uživatele nebo skupiny** zadejte název počítače následovaný zpětným lomítkem.</span><span class="sxs-lookup"><span data-stu-id="56e94-198">In the **Select Users or Groups** dialog box, type the name of the computer followed by a backslash.</span></span>  
  
    3. <span data-ttu-id="56e94-199">Zadejte **službu** za zpětným lomítkem (bez mezer).</span><span class="sxs-lookup"><span data-stu-id="56e94-199">Type **service** after the backslash (no space).</span></span>  
  
    4. <span data-ttu-id="56e94-200">Klikněte na tlačítko **kontrolovat jména**.</span><span class="sxs-lookup"><span data-stu-id="56e94-200">Click **Check names**.</span></span>  
  
    5. <span data-ttu-id="56e94-201">Pokud je nalezeno více názvů, vyberte **Síťová služba** a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="56e94-201">If multiple names are found, select **NETWORK SERVICE** and click **OK**.</span></span>  
  
    6. <span data-ttu-id="56e94-202">Kliknutím na tlačítko **OK** zavřete dialogové okno **Vybrat uživatele nebo skupiny** .</span><span class="sxs-lookup"><span data-stu-id="56e94-202">Click **OK** to close the **Select Users or Groups** dialog box.</span></span>  
  
6. <span data-ttu-id="56e94-203">Pokud používáte systém Windows XP SP2 se službou IIS 5,1, zaškrtněte políčko v poli **název skupiny nebo jméno uživatele** .</span><span class="sxs-lookup"><span data-stu-id="56e94-203">If you are using Windows XP SP2 with IIS 5.1, check that both Internet Guest Account and ASPNET are listed in the **Group or user names** box.</span></span>  
  
     <span data-ttu-id="56e94-204">Všimněte si, že uživatel ASPNET může být členem předdefinované skupiny zabezpečení **Uživatelé** .</span><span class="sxs-lookup"><span data-stu-id="56e94-204">Note that the ASPNET user may be a member of the built-in **Users** security group.</span></span> <span data-ttu-id="56e94-205">Pokud ano, pak pokud je skupina **uživatelů** uvedena v dialogovém okně, není nutné ji přidat jako samostatnou položku do seznamu povolených uživatelů.</span><span class="sxs-lookup"><span data-stu-id="56e94-205">If so, then if the **Users** group is listed in the dialog box, you do not need to add it as a separate item to the list of permitted users.</span></span>  
  
     <span data-ttu-id="56e94-206">Chcete-li zjistit, zda je ASPNET součástí skupiny zabezpečení **Uživatelé** :</span><span class="sxs-lookup"><span data-stu-id="56e94-206">To check if ASPNET is part of the **Users** security group:</span></span>  
  
    1. <span data-ttu-id="56e94-207">V nabídce **Start** klikněte na příkaz **Ovládací panely**.</span><span class="sxs-lookup"><span data-stu-id="56e94-207">On the **Start** menu, click **Control Panel**.</span></span>  
  
    2. <span data-ttu-id="56e94-208">Klikněte na ikonu **uživatelské účty** .</span><span class="sxs-lookup"><span data-stu-id="56e94-208">Click the **User Accounts** icon.</span></span>  
  
    3. <span data-ttu-id="56e94-209">Ve sloupci **Skupina** ověřte, že hodnota pro **ASPNET** je "Users".</span><span class="sxs-lookup"><span data-stu-id="56e94-209">In the **Group** column, check that the value for **ASPNET** is "Users."</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56e94-210">Viz také:</span><span class="sxs-lookup"><span data-stu-id="56e94-210">See also</span></span>

- [<span data-ttu-id="56e94-211">Pokyny k hostování Internetové informační služby</span><span class="sxs-lookup"><span data-stu-id="56e94-211">Internet Information Service Hosting Instructions</span></span>](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)
