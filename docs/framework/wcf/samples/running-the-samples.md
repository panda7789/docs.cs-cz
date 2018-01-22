---
title: "Spouštění ukázek Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: db8a83da-95c1-4a21-a9d2-48caeb6398ea
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 603a6dce17d527a3f14e408da19006509514df52
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="running-the-windows-communication-foundation-samples"></a><span data-ttu-id="5938b-102">Spouštění ukázek Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="5938b-102">Running the Windows Communication Foundation Samples</span></span>
<span data-ttu-id="5938b-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Ukázky můžete spustit v jednom počítači nebo počítači konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="5938b-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] samples can be run in a single-machine or cross-machine configuration.</span></span> <span data-ttu-id="5938b-104">Zadaný, ukázky jsou připravené ke spuštění na jednom počítači.</span><span class="sxs-lookup"><span data-stu-id="5938b-104">As supplied, the samples are ready for running on a single machine.</span></span> <span data-ttu-id="5938b-105">V konfiguraci mezi počítači je potřeba upravit nastavení tohoto příkladu konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="5938b-105">In a cross-machine configuration, it is necessary to modify a sample's configuration file settings.</span></span> <span data-ttu-id="5938b-106">Následující postupy popisují, jak spustit ukázku ve stejném počítači a počítači konfigurace.</span><span class="sxs-lookup"><span data-stu-id="5938b-106">The following procedures explain how to run a sample in same-machine and cross-machine configurations.</span></span> <span data-ttu-id="5938b-107">Všimněte si, že jsou rozdíly v kroků pro služby hostované v Internetové informační služby (IIS) a vlastním hostováním ukázky.</span><span class="sxs-lookup"><span data-stu-id="5938b-107">Note that there are variations in the steps for services hosted in Internet Information Services (IIS) and the self-hosted samples.</span></span> <span data-ttu-id="5938b-108">Většina ukázky jsou hostované ve službě IIS; Zobrazit informace o ukázkový soubor readme k určení, jak je hostovaná.</span><span class="sxs-lookup"><span data-stu-id="5938b-108">Most samples are hosted in IIS; see the sample readme information to determine how it is hosted.</span></span>  
  
 <span data-ttu-id="5938b-109">Na [!INCLUDE[wv](../../../../includes/wv-md.md)], ukázky, které nejsou hostované ve službě IIS vyžaduje zvýšená oprávnění k registraci naslouchací proces s ovladače Http.sys.</span><span class="sxs-lookup"><span data-stu-id="5938b-109">On [!INCLUDE[wv](../../../../includes/wv-md.md)], samples that are not hosted in IIS require elevated privileges to register a listener with Http.sys.</span></span> <span data-ttu-id="5938b-110">Použijte aplikaci Httpcfg.exe registrace naslouchání adresy služby u účtu, který služba běží pod nebo spusťte službu z příkazového řádku s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="5938b-110">Use Httpcfg.exe to register the service's listening addresses with the account the service is running under, or launch the service from a command prompt running with administrator privileges.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5938b-111">Před sestavení nebo s některým z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ukázky, ujistěte se, kterou jste udělali [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5938b-111">Before building or running any of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] samples, be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="5938b-112">Ke spuštění ukázky na stejném počítači</span><span class="sxs-lookup"><span data-stu-id="5938b-112">To run the sample on the same machine</span></span>  
  
1.  <span data-ttu-id="5938b-113">Pokud služba je hostitelem služby IIS, ujistěte se, že mají přístup ke službě pomocí prohlížeče tak, že zadáte tuto adresu: http://localhost/servicemodelsamples/service.svc.</span><span class="sxs-lookup"><span data-stu-id="5938b-113">If the service is hosted by IIS, ensure that you can access the service using a browser by entering the following address: http://localhost/servicemodelsamples/service.svc.</span></span> <span data-ttu-id="5938b-114">Potvrzovací stránku má být zobrazena v odpovědi.</span><span class="sxs-lookup"><span data-stu-id="5938b-114">A confirmation page should be displayed in response.</span></span> <span data-ttu-id="5938b-115">Pokud se nezobrazí stránka potvrzení, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="5938b-115">If the confirmation page is not displayed, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
2.  <span data-ttu-id="5938b-116">Pokud je samoobslužně hostovaná služba, spusťte Service.exe z \service\bin získáte složky pro konkrétní jazyk.</span><span class="sxs-lookup"><span data-stu-id="5938b-116">If the service is self-hosted, run Service.exe from \service\bin, from under the language-specific folder.</span></span> <span data-ttu-id="5938b-117">Aktivita služby se zobrazí v okně konzoly služby.</span><span class="sxs-lookup"><span data-stu-id="5938b-117">Service activity is displayed on the service console window.</span></span>  
  
3.  <span data-ttu-id="5938b-118">Spusťte Client.exe z \client\bin\\, získáte složky pro konkrétní jazyk.</span><span class="sxs-lookup"><span data-stu-id="5938b-118">Run Client.exe from \client\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="5938b-119">Činnost klienta se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="5938b-119">Client activity is displayed on the client console window.</span></span>  
  
4.  <span data-ttu-id="5938b-120">Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="5938b-120">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="5938b-121">Ke spuštění ukázky mezi počítači</span><span class="sxs-lookup"><span data-stu-id="5938b-121">To run the sample across machines</span></span>  
  
1.  <span data-ttu-id="5938b-122">Pokud je služba hostovaná ve službě IIS:</span><span class="sxs-lookup"><span data-stu-id="5938b-122">If the service is hosted in IIS:</span></span>  
  
    1.  <span data-ttu-id="5938b-123">Na počítači služby vytvořte virtuální adresář s názvem ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="5938b-123">On the service machine, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="5938b-124">Dávkový soubor součástí Setupvroot.bat [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) slouží k vytvoření adresáře disk a virtuální adresář.</span><span class="sxs-lookup"><span data-stu-id="5938b-124">The batch file Setupvroot.bat included with [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) can be used to create the disk directory and virtual directory.</span></span>  
  
    2.  <span data-ttu-id="5938b-125">Zkopírujte soubory programu služby z %SystemDrive%\Inetpub\wwwroot\servicemodelsamples do ServiceModelSamples virtuálního adresáře na počítači služby.</span><span class="sxs-lookup"><span data-stu-id="5938b-125">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service machine.</span></span> <span data-ttu-id="5938b-126">Ujistěte se, jestli jste zahrnuli soubory v adresáři \bin.</span><span class="sxs-lookup"><span data-stu-id="5938b-126">Ensure that you include the files in the \bin directory.</span></span>  
  
    3.  <span data-ttu-id="5938b-127">Test službě můžete dostat z klientského počítače pomocí prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="5938b-127">Test that you can access the service from the client machine using a browser.</span></span>  
  
     <span data-ttu-id="5938b-128">Pokud služba se hostuje sama:</span><span class="sxs-lookup"><span data-stu-id="5938b-128">If the service is self-hosted:</span></span>  
  
    1.  <span data-ttu-id="5938b-129">Na počítači služby vytvořte adresář k uložení souborů služby.</span><span class="sxs-lookup"><span data-stu-id="5938b-129">On the service machine, create a directory to hold the service files.</span></span>  
  
    2.  <span data-ttu-id="5938b-130">Zkopírujte soubory programu služby ve složce \service\bin\ ve složce pro specifický jazyk k počítači služby.</span><span class="sxs-lookup"><span data-stu-id="5938b-130">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service machine.</span></span>  
  
    3.  <span data-ttu-id="5938b-131">V konfiguračním souboru služby změňte hodnotu adresu definice koncového bodu tak, aby odpovídala nové adresy vaší služby.</span><span class="sxs-lookup"><span data-stu-id="5938b-131">In the service configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="5938b-132">Nahraďte všechny odkazy na "localhost" plně kvalifikovaný název domény v adrese.</span><span class="sxs-lookup"><span data-stu-id="5938b-132">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
    4.  <span data-ttu-id="5938b-133">Service.exe spusťte z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="5938b-133">Launch Service.exe from a command prompt.</span></span>  
  
2.  <span data-ttu-id="5938b-134">Zkopírujte soubory programu klienta ve složce \client\bin\ ve složce jazyka na klientský počítač.</span><span class="sxs-lookup"><span data-stu-id="5938b-134">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machine.</span></span>  
  
3.  <span data-ttu-id="5938b-135">Nastavte adresu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="5938b-135">Set the endpoint address.</span></span>  
  
    1.  <span data-ttu-id="5938b-136">Pokud služba není spuštěna pod účtem domény, otevřete konfigurační soubor klienta a změňte hodnotu adresu definice koncového bodu tak, aby odpovídala nové adresy vaší služby.</span><span class="sxs-lookup"><span data-stu-id="5938b-136">If the service is not running under a domain account, open the client configuration file and change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="5938b-137">Nahraďte všechny odkazy na "localhost" plně kvalifikovaný název domény v adrese.</span><span class="sxs-lookup"><span data-stu-id="5938b-137">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
    2.  <span data-ttu-id="5938b-138">Pokud služba běží pod účtem domény, znovu vygenerujte konfigurace klienta spuštěním Svcutil.exe proti službu.</span><span class="sxs-lookup"><span data-stu-id="5938b-138">If the service is running under a domain account, regenerate the client configuration by running Svcutil.exe against the service.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="5938b-139">spuštění Svcutil.exe, najdete v části [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5938b-139"> running Svcutil.exe, see [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span> <span data-ttu-id="5938b-140">Použijte vygenerovaný soubor místo konfiguračního souboru ve vzorku.</span><span class="sxs-lookup"><span data-stu-id="5938b-140">Use the generated file instead of the configuration file in the sample.</span></span> <span data-ttu-id="5938b-141">Vygenerovaný konfigurační soubor obsahuje informace o dalších identity a obsahuje všechna nastavení, které jsou potřebné pro připojení ke koncovému bodu služby, i když jsou výchozí nastavení.</span><span class="sxs-lookup"><span data-stu-id="5938b-141">The generated configuration file has additional identity information, and contains all settings necessary to connect to the service endpoint even though they are the default settings.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="5938b-142">informace o identitě, najdete v části [identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md), a [ \<identity >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md).</span><span class="sxs-lookup"><span data-stu-id="5938b-142"> identity information, see [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md), and [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md).</span></span>  
  
4.  <span data-ttu-id="5938b-143">V klientském počítači spusťte z příkazového řádku Client.exe.</span><span class="sxs-lookup"><span data-stu-id="5938b-143">On the client machine, launch Client.exe from a command prompt.</span></span>  
  
### <a name="to-debug-a-service"></a><span data-ttu-id="5938b-144">K ladění služby</span><span class="sxs-lookup"><span data-stu-id="5938b-144">To debug a service</span></span>  
  
1.  <span data-ttu-id="5938b-145">Sestavení řešení (klient a service) pomocí **sestavení** nabídky nebo CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="5938b-145">Build the solution (both client and service) using the **Build** menu or CTRL+SHIFT+B.</span></span>  
  
2.  <span data-ttu-id="5938b-146">Pokud je služba hostovaná ve službě IIS:</span><span class="sxs-lookup"><span data-stu-id="5938b-146">If the service is hosted in IIS:</span></span>  
  
    1.  <span data-ttu-id="5938b-147">Aktivujte službu pomocí prohlížeče zadáním adresy http://localhost/servicemodelsamples/service.svc.</span><span class="sxs-lookup"><span data-stu-id="5938b-147">Activate the service using a browser by entering the address http://localhost/servicemodelsamples/service.svc.</span></span>  
  
    2.  <span data-ttu-id="5938b-148">V řešení, vyberte **ladění** nabídky a **připojit k procesu** položku nabídky.</span><span class="sxs-lookup"><span data-stu-id="5938b-148">In the solution, choose the **Debug** menu and the **Attach to Process** menu item.</span></span>  
  
    3.  <span data-ttu-id="5938b-149">Vyberte **Zobrazit procesy od všech uživatelů** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="5938b-149">Select the **Show processes from all users** check box.</span></span>  
  
    4.  <span data-ttu-id="5938b-150">Vyberte hostitele pracovní proces W3wp.exe k ladění (vyberte ASPNet_wp.exe v systému Windows XP).</span><span class="sxs-lookup"><span data-stu-id="5938b-150">Select the host worker process W3wp.exe to debug (select ASPNet_wp.exe on Windows XP).</span></span>  
  
3.  <span data-ttu-id="5938b-151">Teď můžete nastavit zarážky v kódu služby a povolit zarážky na výjimky.</span><span class="sxs-lookup"><span data-stu-id="5938b-151">You can now set breakpoints in the service code and enable breakpoints on exceptions.</span></span>  
  
4.  <span data-ttu-id="5938b-152">Klikněte pravým tlačítkem na položku projektu klienta a zvolte **ladění**, **spustit novou instanci**.</span><span class="sxs-lookup"><span data-stu-id="5938b-152">Right-click the client project item and choose **Debug**, **Start new instance**.</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="5938b-153">Vyčistěte po vzorku</span><span class="sxs-lookup"><span data-stu-id="5938b-153">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="5938b-154">Pokud je služba hostovaná ve službě IIS pro účely zabezpečení, odeberte definici virtuální adresář a oprávnění udělená v průběhu instalace, když skončíte s ukázky.</span><span class="sxs-lookup"><span data-stu-id="5938b-154">If the service is hosted in IIS for security purposes, remove the virtual directory definition and permissions granted in the setup steps when you are finished with the samples.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5938b-155">Viz také</span><span class="sxs-lookup"><span data-stu-id="5938b-155">See Also</span></span>  
 [<span data-ttu-id="5938b-156">Ukázky vytváření Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="5938b-156">Building the Windows Communication Foundation Samples</span></span>](../../../../docs/framework/wcf/samples/building-the-samples.md)  
 [<span data-ttu-id="5938b-157">Spuštění ukázky v pracovní skupině a v počítačích</span><span class="sxs-lookup"><span data-stu-id="5938b-157">Running the Samples in a Workgroup and Across Machines</span></span>](http://msdn.microsoft.com/library/a451a525-e7ce-452d-9da9-620221260113)  
 [<span data-ttu-id="5938b-158">Tipy pro odstraňování potíží</span><span class="sxs-lookup"><span data-stu-id="5938b-158">Troubleshooting Tips</span></span>](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b)
