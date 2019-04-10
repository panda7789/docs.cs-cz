---
title: Pokyny pro instalaci virtuálního adresáře
ms.date: 03/30/2017
ms.assetid: 3c62cab5-81a4-48b6-ac8c-9ce33a85a157
ms.openlocfilehash: 7999a040dc14d75a34b75f320982dd3118eae670
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225583"
---
# <a name="virtual-directory-setup-instructions"></a><span data-ttu-id="77627-102">Pokyny pro instalaci virtuálního adresáře</span><span class="sxs-lookup"><span data-stu-id="77627-102">Virtual Directory Setup Instructions</span></span>
<span data-ttu-id="77627-103">Ukázky Windows Communication Foundation (WCF) jsou určené ke sdílení běžné virtuální adresář s názvem servicemodelsamples, která je namapována na složku %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="77627-103">The Windows Communication Foundation (WCF) samples are intended to share a common virtual directory named servicemodelsamples that is mapped to the %SystemDrive%\inetpub\wwwroot\servicemodelsamples folder.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="77627-104">Jednotka % SystemDrive % je obvykle C: a D:, v závislosti na umístění disku instalaci Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="77627-104">%SystemDrive% is usually C: or D:, depending on the drive location where Internet Information Services (IIS) is installed.</span></span>  
  
 <span data-ttu-id="77627-105">Můžete spouštět Setupvroot.bat a Cleanupvroot.bat soubory z [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) vytvořit virtuální adresář.</span><span class="sxs-lookup"><span data-stu-id="77627-105">You can run the Setupvroot.bat and Cleanupvroot.bat files from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) to create the virtual directory.</span></span> <span data-ttu-id="77627-106">Pokud chcete ručně vytvořit virtuální adresář, použijte následující postupy.</span><span class="sxs-lookup"><span data-stu-id="77627-106">If you prefer to create the virtual directory manually, use the following procedures.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="77627-107">Procedury</span><span class="sxs-lookup"><span data-stu-id="77627-107">Procedures</span></span>  
  
#### <a name="to-create-a-virtual-directory-in-iis-70-or-75"></a><span data-ttu-id="77627-108">Chcete-li vytvořit virtuální adresář ve službě IIS 7.0 nebo 7.5</span><span class="sxs-lookup"><span data-stu-id="77627-108">To create a virtual directory in IIS 7.0 or 7.5</span></span>  
  
1.  <span data-ttu-id="77627-109">Z **Start** nabídky, klikněte na tlačítko **spustit**, zadejte **inetmgr** otevřete modul snap-in konzoly MMC Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="77627-109">From the **Start** menu, click **Run**, then type **inetmgr** to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2.  <span data-ttu-id="77627-110">V levém podokně rozbalte uzel s názvem počítače a potom rozbalte **lokality** uzlu.</span><span class="sxs-lookup"><span data-stu-id="77627-110">In the left pane, expand the node with the computer's name, and then expand the **Sites** node.</span></span>  
  
3.  <span data-ttu-id="77627-111">Klikněte pravým tlačítkem na **výchozí webový server**a pak vyberte **přidat aplikaci** otevřít **okna Přidat aplikaci**.</span><span class="sxs-lookup"><span data-stu-id="77627-111">Right-click **Default Web Site**, and then select **Add Application** to open the **Add Application window**.</span></span>  
  
4.  <span data-ttu-id="77627-112">V okně zadejte `servicemodelsamples` jako alias pro virtuální adresář, který vytváříte.</span><span class="sxs-lookup"><span data-stu-id="77627-112">In the window, type `servicemodelsamples` as the alias for the virtual directory that you are creating.</span></span>  
  
5.  <span data-ttu-id="77627-113">Vytvořit následující složku: %SystemDrive%\inetpub\wwwroot\servicemodelsamples</span><span class="sxs-lookup"><span data-stu-id="77627-113">Create the following directory: %SystemDrive%\inetpub\wwwroot\servicemodelsamples</span></span>  
  
6.  <span data-ttu-id="77627-114">Nastavte na % SystemDrive%\inetpub\wwwroot\servicemodelsamples fyzickou cestu.</span><span class="sxs-lookup"><span data-stu-id="77627-114">Set the physical path to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  <span data-ttu-id="77627-115">Většina Ukázky WCF zkopírujte do tohoto umístění při vytváření služby spustitelné soubory.</span><span class="sxs-lookup"><span data-stu-id="77627-115">Most of the WCF samples copy service executable files to this location when built.</span></span>  
  
7.  <span data-ttu-id="77627-116">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="77627-116">Click **OK**.</span></span> <span data-ttu-id="77627-117">Webová aplikace je vytvořený pro ukázky WCF.</span><span class="sxs-lookup"><span data-stu-id="77627-117">The Web application is now created for the WCF samples.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="77627-118">Tato úloha musí pouze jednou provést, protože všechny ukázky WCF používají stejné servicemodelsamples webové aplikace.</span><span class="sxs-lookup"><span data-stu-id="77627-118">This task must be performed only once, because all of the WCF samples use the same servicemodelsamples Web application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="77627-119">Pro účely této dokumentace termín `virtual directory` je synonymní s `Web application`.</span><span class="sxs-lookup"><span data-stu-id="77627-119">For the purpose of this documentation, the term `virtual directory` is synonymous with `Web application`.</span></span>  
  
     <span data-ttu-id="77627-120">Kromě vytvoření virtuálního adresáře, musíte také nastavit jeho vlastnosti umožňující spuštění služeb WCF.</span><span class="sxs-lookup"><span data-stu-id="77627-120">In addition to creating the virtual directory, you must also set its properties to enable WCF services to run.</span></span> <span data-ttu-id="77627-121">Podrobnosti najdete níže.</span><span class="sxs-lookup"><span data-stu-id="77627-121">See below for details.</span></span>  
  
#### <a name="to-create-a-virtual-directory-in-iis-51-or-60"></a><span data-ttu-id="77627-122">Chcete-li vytvořit virtuální adresář v IIS 5.1 a 6.0</span><span class="sxs-lookup"><span data-stu-id="77627-122">To create a virtual directory in IIS 5.1 or 6.0</span></span>  
  
1.  <span data-ttu-id="77627-123">Otevřete okno příkazového řádku a zadejte `start inetmgr` otevřete modul snap-in konzoly MMC Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="77627-123">Open a command prompt window and type `start inetmgr` to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2.  <span data-ttu-id="77627-124">V levém podokně rozbalte uzel s názvem počítače a potom rozbalte **weby** uzlu.</span><span class="sxs-lookup"><span data-stu-id="77627-124">In the left pane, expand the node with the computer's name, and then expand the **Web Sites** node.</span></span>  
  
3.  <span data-ttu-id="77627-125">Klikněte pravým tlačítkem na **výchozí webový server** a vyberte **nový, virtuální adresář** otevřete Průvodce vytvořením virtuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="77627-125">Right-click **Default Web Site** and select **New, Virtual Directory** to open the Virtual Directory Creation wizard.</span></span>  
  
4.  <span data-ttu-id="77627-126">V průvodci zadejte `servicemodelsamples` jako alias pro virtuální adresář, který vytváříte.</span><span class="sxs-lookup"><span data-stu-id="77627-126">In the wizard, type `servicemodelsamples` as the alias for the virtual directory that you are creating.</span></span>  
  
5.  <span data-ttu-id="77627-127">Nastavení cesty k % SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="77627-127">Set the path to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span> <span data-ttu-id="77627-128">Většina Ukázky WCF zkopírujte do tohoto umístění při vytváření služby spustitelné soubory.</span><span class="sxs-lookup"><span data-stu-id="77627-128">Most of the WCF samples copy service executable files to this location when built.</span></span>  
  
6.  <span data-ttu-id="77627-129">Klikněte na **Další**.</span><span class="sxs-lookup"><span data-stu-id="77627-129">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="77627-130">Ve výchozím nastavení jsou vybrány následující políčka:</span><span class="sxs-lookup"><span data-stu-id="77627-130">By default, the following check boxes are selected:</span></span>  
  
    -   **<span data-ttu-id="77627-131">Číst</span><span class="sxs-lookup"><span data-stu-id="77627-131">Read</span></span>**  
  
    -   **<span data-ttu-id="77627-132">Spouštění skriptů (například ASP)</span><span class="sxs-lookup"><span data-stu-id="77627-132">Run scripts (such as ASP)</span></span>**  
  
8.  <span data-ttu-id="77627-133">Klikněte na tlačítko **Další**a potom klikněte na tlačítko **Dokončit** kroky průvodce dokončete.</span><span class="sxs-lookup"><span data-stu-id="77627-133">Click **Next**, and then click **Finish** to complete the wizard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="77627-134">Tato úloha musí pouze jednou provést, protože všechny ukázky WCF používají servicemodelsamples virtuální adresář.</span><span class="sxs-lookup"><span data-stu-id="77627-134">This task must be performed only once because all of the WCF samples use the same servicemodelsamples virtual directory.</span></span>  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-70-or-75"></a><span data-ttu-id="77627-135">Chcete-li nastavit vlastnosti další virtuální adresáře ve službě IIS 7.0 nebo 7.5</span><span class="sxs-lookup"><span data-stu-id="77627-135">To set additional virtual directory properties in IIS 7.0 or 7.5</span></span>  
  
1.  <span data-ttu-id="77627-136">Klikněte na uzel servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="77627-136">Click the servicemodelsamples node.</span></span> <span data-ttu-id="77627-137">V dolní části okna jsou uvedeny dvě zobrazení.</span><span class="sxs-lookup"><span data-stu-id="77627-137">Along the bottom of the window, two views are listed.</span></span> <span data-ttu-id="77627-138">Vyberte **zobrazení funkcí** Pokud ještě není vybraná.</span><span class="sxs-lookup"><span data-stu-id="77627-138">Select **Features View** if it isn’t already selected.</span></span>  
  
2.  <span data-ttu-id="77627-139">Dvakrát klikněte na položku **procházení adresářů**.</span><span class="sxs-lookup"><span data-stu-id="77627-139">Double-click the entry for **Directory Browsing**.</span></span>  
  
3.  <span data-ttu-id="77627-140">V podokně Akce, vyberte **povolit** možnost.</span><span class="sxs-lookup"><span data-stu-id="77627-140">In the Actions pane, select the **Enable** option.</span></span> <span data-ttu-id="77627-141">Umožňuje získat přístup k adresáři adresáře pomocí aplikace Internet Explorer, který pomáhá při ladění služby.</span><span class="sxs-lookup"><span data-stu-id="77627-141">This enables you to access the directory of the directory by using Internet Explorer, which helps when debugging a service.</span></span>  
  
 <span data-ttu-id="77627-142">Nakonec musíte nastavit vlastnosti zabezpečení servicemodelsamples složky, aby mohla být přístup i jiní.</span><span class="sxs-lookup"><span data-stu-id="77627-142">Finally, you must set the security properties of the servicemodelsamples folder to allow it to be accessed by others.</span></span> <span data-ttu-id="77627-143">Podrobnosti najdete níže.</span><span class="sxs-lookup"><span data-stu-id="77627-143">See below for details.</span></span>  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-51-or-60"></a><span data-ttu-id="77627-144">Chcete-li nastavit vlastnosti další virtuální adresář IIS 5.1 a 6.0</span><span class="sxs-lookup"><span data-stu-id="77627-144">To set additional virtual directory properties in IIS 5.1 or 6.0</span></span>  
  
1.  <span data-ttu-id="77627-145">Klikněte pravým tlačítkem na uzel servicemodelsamples a potom klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="77627-145">Right-click the servicemodelsamples node and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="77627-146">Ve výchozím nastavení jsou vybrány následující políčka:</span><span class="sxs-lookup"><span data-stu-id="77627-146">By default, the following check boxes are selected:</span></span>  
  
    -   **<span data-ttu-id="77627-147">Číst</span><span class="sxs-lookup"><span data-stu-id="77627-147">Read</span></span>**  
  
    -   **<span data-ttu-id="77627-148">Navštíví protokolu</span><span class="sxs-lookup"><span data-stu-id="77627-148">Log visits</span></span>**  
  
    -   **<span data-ttu-id="77627-149">Xovat tento prostředek</span><span class="sxs-lookup"><span data-stu-id="77627-149">Index this resource</span></span>**  
  
3.  <span data-ttu-id="77627-150">Vyberte **procházení adresářů** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="77627-150">Select the **Directory browsing** check box.</span></span> <span data-ttu-id="77627-151">Umožňuje získat přístup k adresáři adresáře pomocí aplikace Internet Explorer, který pomáhá při ladění služby.</span><span class="sxs-lookup"><span data-stu-id="77627-151">This enables you to access the directory of the directory by using Internet Explorer, which helps when debugging a service.</span></span>  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-70-or-75"></a><span data-ttu-id="77627-152">Chcete-li nastavit vlastnosti zabezpečení složky ve službě IIS 7.0 nebo 7.5</span><span class="sxs-lookup"><span data-stu-id="77627-152">To set security properties of the folder in IIS 7.0 or 7.5</span></span>  
  
1.  <span data-ttu-id="77627-153">Přejděte na % SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="77627-153">Navigate to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  
  
2.  <span data-ttu-id="77627-154">Klikněte pravým tlačítkem na složku servicemodelsamples a klikněte na tlačítko **sdílenou složku** nebo **sdílenou složku s**.</span><span class="sxs-lookup"><span data-stu-id="77627-154">Right-click the servicemodelsamples folder and click **Share** or **Share With**.</span></span>  
  
3.  <span data-ttu-id="77627-155">Klikněte na šipku dolů nalevo od **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="77627-155">Click the down arrow to the left of the **Add** button.</span></span>  
  
4.  <span data-ttu-id="77627-156">Vyberte **najít** položka.</span><span class="sxs-lookup"><span data-stu-id="77627-156">Select the **Find** entry.</span></span> <span data-ttu-id="77627-157">**Vybrat uživatele nebo skupiny** otevře se okno.</span><span class="sxs-lookup"><span data-stu-id="77627-157">The **Select Users or Groups** window opens.</span></span>  
  
5.  <span data-ttu-id="77627-158">Klikněte na tlačítko **Advanced**.</span><span class="sxs-lookup"><span data-stu-id="77627-158">Click **Advanced**.</span></span>  
  
6.  <span data-ttu-id="77627-159">Klikněte na tlačítko **umístění**.</span><span class="sxs-lookup"><span data-stu-id="77627-159">Click **Locations**.</span></span> <span data-ttu-id="77627-160">**Umístění** okna je teď otevřené.</span><span class="sxs-lookup"><span data-stu-id="77627-160">The **Locations** window is now open.</span></span>  
  
7.  <span data-ttu-id="77627-161">Vyberte položku pro počítač používá.</span><span class="sxs-lookup"><span data-stu-id="77627-161">Select the entry for the computer being used.</span></span> <span data-ttu-id="77627-162">Je důležité vybrat místním počítači a ne položka pro všechny domény nebo sítě, které jsou uvedeny.</span><span class="sxs-lookup"><span data-stu-id="77627-162">It is important to select the local computer and not an entry for any domains or networks that are listed.</span></span> <span data-ttu-id="77627-163">Jakmile vyberete počítač, klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="77627-163">After you have selected the computer, click **OK**.</span></span>  
  
8.  <span data-ttu-id="77627-164">Klikněte na tlačítko **najít**.</span><span class="sxs-lookup"><span data-stu-id="77627-164">Click **Find Now**.</span></span> <span data-ttu-id="77627-165">Tím vyplníte výsledky hledání s objekty přidružené k místnímu počítači.</span><span class="sxs-lookup"><span data-stu-id="77627-165">This populates the search results with objects associated with the local computer.</span></span>  
  
9. <span data-ttu-id="77627-166">Najít **IIS_IUSRS** položku **název (relativní rozlišující název)** sloupec.</span><span class="sxs-lookup"><span data-stu-id="77627-166">Find the **IIS_IUSRS** entry in the **Name (Relative Distinguished Name)** column.</span></span> <span data-ttu-id="77627-167">Vyberte tuto položku a klikněte na tlačítko **OK** hledání zavřete okno výsledků.</span><span class="sxs-lookup"><span data-stu-id="77627-167">Select that entry and click **OK** to close the search results window.</span></span>  
  
10. <span data-ttu-id="77627-168">Klikněte na tlačítko **OK** zavřete **vybrat uživatele nebo skupiny** okna.</span><span class="sxs-lookup"><span data-stu-id="77627-168">Click **OK** to close the **Select Users or Groups** window.</span></span>  
  
11. <span data-ttu-id="77627-169">Klikněte na tlačítko **sdílené složky** a zachová tak změny.</span><span class="sxs-lookup"><span data-stu-id="77627-169">Click **Share** to persist the changes.</span></span>  
  
12. <span data-ttu-id="77627-170">Po povolení sdílení změn se dokončí, klikněte na tlačítko **provádí** zavřete **sdílení souborů** okna.</span><span class="sxs-lookup"><span data-stu-id="77627-170">After the changes to enable sharing are complete, click **Done** to close the **File Sharing** window.</span></span>  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-51-or-60"></a><span data-ttu-id="77627-171">Chcete-li nastavit vlastnosti zabezpečení složky v IIS 5.1 a 6.0</span><span class="sxs-lookup"><span data-stu-id="77627-171">To set security properties of the folder in IIS 5.1 or 6.0</span></span>  
  
1.  <span data-ttu-id="77627-172">Přejděte na % SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="77627-172">Navigate to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  
  
2.  <span data-ttu-id="77627-173">Klikněte pravým tlačítkem myši **servicemodelsamples** složku a pak klikněte na tlačítko **sdílení a zabezpečení.**</span><span class="sxs-lookup"><span data-stu-id="77627-173">Right-click the **servicemodelsamples** folder and then click **Sharing and Security.**</span></span>  
  
3.  <span data-ttu-id="77627-174">Klikněte na tlačítko **zabezpečení** kartu.</span><span class="sxs-lookup"><span data-stu-id="77627-174">Click the **Security** tab.</span></span>  
  
4.  <span data-ttu-id="77627-175">Pokud používáte IIS 6.0 v **skupiny nebo jméno uživatele** zaškrtněte políčko, zda **účet Guest Internet** je uvedena.</span><span class="sxs-lookup"><span data-stu-id="77627-175">If you are using IIS 6.0, in the **Group or user names** box, check whether **Internet Guest Account** is listed.</span></span>  
  
     <span data-ttu-id="77627-176">Pokud není uvedená:</span><span class="sxs-lookup"><span data-stu-id="77627-176">If it is not listed:</span></span>  
  
    1.  <span data-ttu-id="77627-177">Klikněte na tlačítko **Start** a potom klikněte na tlačítko **ovládací panely**.</span><span class="sxs-lookup"><span data-stu-id="77627-177">Click **Start** and then click **Control Panel**.</span></span>  
  
    2.  <span data-ttu-id="77627-178">Pokud se nezobrazí **uživatelské účty** ikonu, klikněte na tlačítko **přepnout na zobrazení kategorií**.</span><span class="sxs-lookup"><span data-stu-id="77627-178">If you do not see the **User Accounts** icon, click **Switch to Category View**.</span></span>  
  
    3.  <span data-ttu-id="77627-179">Klikněte na tlačítko **uživatelské účty** ikonu.</span><span class="sxs-lookup"><span data-stu-id="77627-179">Click the **User Accounts** icon.</span></span>  
  
    4.  <span data-ttu-id="77627-180">V části "nebo vyberte ikonu ovládacího prvku panelu," klikněte na tlačítko **uživatelské účty**.</span><span class="sxs-lookup"><span data-stu-id="77627-180">Under "or pick a Control Panel icon," click **User Accounts**.</span></span>  
  
    5.  <span data-ttu-id="77627-181">V **uživatelské účty** dialogové okno, klikněte na tlačítko **Upřesnit** kartu.</span><span class="sxs-lookup"><span data-stu-id="77627-181">In the **User Accounts** dialog box, click the **Advanced** tab.</span></span>  
  
    6.  <span data-ttu-id="77627-182">Klikněte na tlačítko **Advanced**.</span><span class="sxs-lookup"><span data-stu-id="77627-182">Click **Advanced**.</span></span>  
  
    7.  <span data-ttu-id="77627-183">V **místní uživatelé a skupiny** dialogové okno, rozbalte kliknutím **uživatelé** složky.</span><span class="sxs-lookup"><span data-stu-id="77627-183">In the **Local Users and Groups** dialog box, click to expand the **Users** folder.</span></span>  
  
    8.  <span data-ttu-id="77627-184">V pravém podokně klikněte dvakrát na **účet Guest Internet**.</span><span class="sxs-lookup"><span data-stu-id="77627-184">In the right pane, double-click **Internet Guest Account**.</span></span>  
  
    9. <span data-ttu-id="77627-185">V **vlastnosti** dialogové okno, zkopírujte název použit jako účet guest Internet.</span><span class="sxs-lookup"><span data-stu-id="77627-185">In the **Properties** dialog box, copy the name used as the Internet guest account.</span></span> <span data-ttu-id="77627-186">Ve výchozím nastavení název začíná řetězcem "USR_", za nímž následuje název počítače.</span><span class="sxs-lookup"><span data-stu-id="77627-186">By default, the name begins with "USR_" followed by the name of the computer.</span></span>  
  
    10. <span data-ttu-id="77627-187">Zavřít **vlastnosti** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="77627-187">Close the **Properties** dialog box.</span></span>  
  
    11. <span data-ttu-id="77627-188">Zavřít **místní uživatelé a skupiny** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="77627-188">Close the **Local Users and Groups** dialog box.</span></span>  
  
    12. <span data-ttu-id="77627-189">Zavřít **uživatelské účty** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="77627-189">Close the **User Accounts** dialog box.</span></span>  
  
    13. <span data-ttu-id="77627-190">Zavřete druhou **uživatelské účty** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="77627-190">Close the other **User Accounts** dialog box.</span></span>  
  
    14. <span data-ttu-id="77627-191">V **servicemodelsamples vlastnosti** dialogovém okně **zabezpečení** klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="77627-191">In the **servicemodelsamples Properties** dialog box, on the **Security** tab, click **Add**.</span></span>  
  
    15. <span data-ttu-id="77627-192">Zadejte název počítače, za nímž následuje zpětné lomítko a poté vložte název účtu uživatele Internet, například myMachineName\\InternetGuestAccountName %</span><span class="sxs-lookup"><span data-stu-id="77627-192">Type the name of the computer followed by a backslash, then paste the name of the Internet user account, for example, myMachineName\\%InternetGuestAccountName%</span></span>  
  
    16. <span data-ttu-id="77627-193">Klikněte na tlačítko **Kontrola názvů** aby se ověřilo přidání.</span><span class="sxs-lookup"><span data-stu-id="77627-193">Click **Check Names** to verify the addition.</span></span> <span data-ttu-id="77627-194">Pokud je platný, je název velkými písmeny a podtržené.</span><span class="sxs-lookup"><span data-stu-id="77627-194">If it is valid, the name is in all capital letters and is underlined.</span></span>  
  
5.  <span data-ttu-id="77627-195">Pro službu IIS 6.0, zkontrolujte také, že síťová služba je uveden v **skupiny nebo jméno uživatele** pole.</span><span class="sxs-lookup"><span data-stu-id="77627-195">For IIS 6.0, also check that NETWORK SERVICE is listed in the **Group or user names** box.</span></span>  
  
     <span data-ttu-id="77627-196">Pokud není uvedená síť služby:</span><span class="sxs-lookup"><span data-stu-id="77627-196">If NETWORK SERVICE is not listed:</span></span>  
  
    1.  <span data-ttu-id="77627-197">Klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="77627-197">Click **Add**.</span></span>  
  
    2.  <span data-ttu-id="77627-198">V **vybrat uživatele nebo skupiny** dialogové okno, zadejte název počítače, a potom je zpětným lomítkem.</span><span class="sxs-lookup"><span data-stu-id="77627-198">In the **Select Users or Groups** dialog box, type the name of the computer followed by a backslash.</span></span>  
  
    3.  <span data-ttu-id="77627-199">Typ **služby** za zpětným lomítkem (bez mezer).</span><span class="sxs-lookup"><span data-stu-id="77627-199">Type **service** after the backslash (no space).</span></span>  
  
    4.  <span data-ttu-id="77627-200">Klikněte na tlačítko **zkontrolovat názvy**.</span><span class="sxs-lookup"><span data-stu-id="77627-200">Click **Check names**.</span></span>  
  
    5.  <span data-ttu-id="77627-201">Pokud je nalezeno více jmen, vyberte **síťová služba** a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="77627-201">If multiple names are found, select **NETWORK SERVICE** and click **OK**.</span></span>  
  
    6.  <span data-ttu-id="77627-202">Klikněte na tlačítko **OK** zavřete **vybrat uživatele nebo skupiny** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="77627-202">Click **OK** to close the **Select Users or Groups** dialog box.</span></span>  
  
6.  <span data-ttu-id="77627-203">Pokud používáte Windows XP SP2 se služba IIS 5.1, zkontrolujte, že jsou v uvedené Internet účet Guest a ASPNET **skupiny nebo jméno uživatele** pole.</span><span class="sxs-lookup"><span data-stu-id="77627-203">If you are using Windows XP SP2 with IIS 5.1, check that both Internet Guest Account and ASPNET are listed in the **Group or user names** box.</span></span>  
  
     <span data-ttu-id="77627-204">Všimněte si, že uživatel ASPNET může být členem předdefinované **uživatelé** skupiny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="77627-204">Note that the ASPNET user may be a member of the built-in **Users** security group.</span></span> <span data-ttu-id="77627-205">Pokud ano, pak v případě **uživatelé** skupina je uvedena v dialogovém okně, není potřeba ho přidat jako samostatné položky do seznamu povolených uživatelů.</span><span class="sxs-lookup"><span data-stu-id="77627-205">If so, then if the **Users** group is listed in the dialog box, you do not need to add it as a separate item to the list of permitted users.</span></span>  
  
     <span data-ttu-id="77627-206">Chcete-li zkontrolovat, jestli ASPNET je součástí **uživatelé** skupiny zabezpečení:</span><span class="sxs-lookup"><span data-stu-id="77627-206">To check if ASPNET is part of the **Users** security group:</span></span>  
  
    1.  <span data-ttu-id="77627-207">Na **Start** nabídky, klikněte na tlačítko **ovládací panely**.</span><span class="sxs-lookup"><span data-stu-id="77627-207">On the **Start** menu, click **Control Panel**.</span></span>  
  
    2.  <span data-ttu-id="77627-208">Klikněte na tlačítko **uživatelské účty** ikonu.</span><span class="sxs-lookup"><span data-stu-id="77627-208">Click the **User Accounts** icon.</span></span>  
  
    3.  <span data-ttu-id="77627-209">V **skupiny** sloupce, zkontrolujte, že hodnota **ASPNET** "uživatelů."</span><span class="sxs-lookup"><span data-stu-id="77627-209">In the **Group** column, check that the value for **ASPNET** is "Users."</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77627-210">Viz také:</span><span class="sxs-lookup"><span data-stu-id="77627-210">See also</span></span>

- [<span data-ttu-id="77627-211">Pokyny k hostování služby IIS</span><span class="sxs-lookup"><span data-stu-id="77627-211">Internet Information Service Hosting Instructions</span></span>](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)
