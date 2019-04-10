---
title: Pokyny k bráně firewall
ms.date: 03/30/2017
ms.assetid: a7dc429f-65ac-4faf-974a-77d5fb977fe1
ms.openlocfilehash: f1b576b4e413fa3bae70ef1eb8f8ed768e28e309
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295156"
---
# <a name="firewall-instructions"></a><span data-ttu-id="2a93f-102">Pokyny k bráně firewall</span><span class="sxs-lookup"><span data-stu-id="2a93f-102">Firewall Instructions</span></span>
<span data-ttu-id="2a93f-103">Je nutné povolit několik portů a programů v bráně firewall tak, aby ukázky Windows Communication Foundation (WCF), můžou fungovat.</span><span class="sxs-lookup"><span data-stu-id="2a93f-103">You must enable several ports or programs in the firewall so that the Windows Communication Foundation (WCF) samples can function.</span></span> <span data-ttu-id="2a93f-104">Mnoho vzorků komunikaci prostřednictvím portů v rozsahu 8000-8003 a portu 9000.</span><span class="sxs-lookup"><span data-stu-id="2a93f-104">Many of the samples communicate by using ports in the range 8000-8003, and port 9000.</span></span> <span data-ttu-id="2a93f-105">Brána firewall je ve výchozím nastavení zapnutá a brání v přístupu k těmto portům.</span><span class="sxs-lookup"><span data-stu-id="2a93f-105">The firewall is turned on by default and prevents access to these ports.</span></span> <span data-ttu-id="2a93f-106">Pokud chcete povolit bránu firewall pro ukázky, proveďte jednu z následujících postupů, v závislosti na vašich požadavcích a zabezpečení prostředí:</span><span class="sxs-lookup"><span data-stu-id="2a93f-106">To enable the firewall for the samples, complete one of the following procedures, depending on your requirements and security environment:</span></span>  
  
-   <span data-ttu-id="2a93f-107">Option 1: Povolte interaktivní ukázky při spuštění.</span><span class="sxs-lookup"><span data-stu-id="2a93f-107">Option 1: Interactively enable samples while running.</span></span> <span data-ttu-id="2a93f-108">Neprovádějte žádné změny zálohy konfigurace brány firewall a pokračujte začít sestavovat a spouštět ukázky.</span><span class="sxs-lookup"><span data-stu-id="2a93f-108">Make no advance changes to your firewall configuration and proceed to start building and running the samples.</span></span> <span data-ttu-id="2a93f-109">Při spuštění ukázky **výstraha zabezpečení Windows** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="2a93f-109">When a sample is run, a **Windows Security Alert** dialog box appears.</span></span> <span data-ttu-id="2a93f-110">Ukázkový program dotyčný je potom možné přidat interaktivně odblokované seznamu.</span><span class="sxs-lookup"><span data-stu-id="2a93f-110">The sample program in question can then be added interactively to an unblocked list.</span></span> <span data-ttu-id="2a93f-111">V tomto návodu budete muset znovu spusťte ukázku.</span><span class="sxs-lookup"><span data-stu-id="2a93f-111">With this procedure, you may have to then restart the sample.</span></span>  
  
-   <span data-ttu-id="2a93f-112">Option 2: Povolte ukázkové programy předem.</span><span class="sxs-lookup"><span data-stu-id="2a93f-112">Option 2: Enable sample programs in advance.</span></span> <span data-ttu-id="2a93f-113">Spustit **ovládacích panelů Windows Firewall** aplet a povolte ukázka programy plánu pro spuštění.</span><span class="sxs-lookup"><span data-stu-id="2a93f-113">Start the **Windows Firewall Control Panel** applet and enable the sample programs you plan to run.</span></span> <span data-ttu-id="2a93f-114">Programy musí nejprve sestavení, spustitelné soubory existují.</span><span class="sxs-lookup"><span data-stu-id="2a93f-114">You must build the programs first so the executable files exist.</span></span> <span data-ttu-id="2a93f-115">Podrobné pokyny najdete v následujícím postupu.</span><span class="sxs-lookup"><span data-stu-id="2a93f-115">You can find more detailed instructions in the following procedure.</span></span>  
  
-   <span data-ttu-id="2a93f-116">Možnost 3: Povolte rozsah portů předem.</span><span class="sxs-lookup"><span data-stu-id="2a93f-116">Option 3: Enable a port range in advance.</span></span> <span data-ttu-id="2a93f-117">Spustit **brány Windows Firewall** **ovládací panely** aplet a povolte porty 80, 443, 8000 8003 a 9000, které se používají ve vzorcích.</span><span class="sxs-lookup"><span data-stu-id="2a93f-117">Start the **Windows Firewall** **Control Panel** applet and enable ports 80, 443, 8000-8003 and 9000, which are used by the samples.</span></span> <span data-ttu-id="2a93f-118">Podrobné pokyny najdete v následujícím postupu.</span><span class="sxs-lookup"><span data-stu-id="2a93f-118">You can find more detailed instructions in the following procedure.</span></span> <span data-ttu-id="2a93f-119">Tato možnost je méně bezpečné než ostatní, protože umožňuje libovolné aplikaci pro používání těchto portů, nejen ukázky.</span><span class="sxs-lookup"><span data-stu-id="2a93f-119">This option is less secure than the others because it allows any program to use these ports, not just the samples.</span></span>  
  
 <span data-ttu-id="2a93f-120">Pokud si nejste jisti, který postup máte použít, zvolte první možnost.</span><span class="sxs-lookup"><span data-stu-id="2a93f-120">If you are unsure of which procedure to use, choose the first option.</span></span> <span data-ttu-id="2a93f-121">Pokud používáte firewall od jiného dodavatele, může být nutné provést změny podobné změny.</span><span class="sxs-lookup"><span data-stu-id="2a93f-121">If you are running a firewall from another vendor, you might need to make similar changes.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2a93f-122">Když změníte konfiguraci brány firewall má vliv na zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="2a93f-122">Changing your firewall configuration affects your security.</span></span> <span data-ttu-id="2a93f-123">Doporučujeme záznamu změny Ujistěte se a odstranit je při dokončení práce s ukázkami.</span><span class="sxs-lookup"><span data-stu-id="2a93f-123">It is recommended that you record the changes you make and remove them when you are finished working with the samples.</span></span>  
  
### <a name="to-enable-samples-programs-in-advance"></a><span data-ttu-id="2a93f-124">Chcete-li povolit ukázkové programy předem</span><span class="sxs-lookup"><span data-stu-id="2a93f-124">To enable samples programs in advance</span></span>  
  
1. <span data-ttu-id="2a93f-125">Sestavte ukázku.</span><span class="sxs-lookup"><span data-stu-id="2a93f-125">Build the sample.</span></span>  
  
2. <span data-ttu-id="2a93f-126">Klikněte na tlačítko **Start**, klikněte na tlačítko **spustit**a typ `firewall.cpl`.</span><span class="sxs-lookup"><span data-stu-id="2a93f-126">Click **Start**, click **Run**, and type `firewall.cpl`.</span></span> <span data-ttu-id="2a93f-127">Tím se otevře **ovládacích panelů Windows Firewall** aplet.</span><span class="sxs-lookup"><span data-stu-id="2a93f-127">This opens the **Windows Firewall Control Panel** applet.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2a93f-128">Musíte mít oprávnění ke změně nastavení brány Firewall pro spuštění ukázky, které potřebují komunikovat přes bránu Windows Firewall.</span><span class="sxs-lookup"><span data-stu-id="2a93f-128">You must have permission to change the Firewall settings to run samples that require the ability to communicate through the Windows Firewall.</span></span> <span data-ttu-id="2a93f-129">Pokud některé nastavení brány firewall nejsou k dispozici a je počítač připojen k doméně, může správce systému řízení těchto nastavení prostřednictvím zásad skupiny.</span><span class="sxs-lookup"><span data-stu-id="2a93f-129">If some firewall settings are unavailable and your computer is connected to a domain, your system administrator might be controlling these settings through Group Policy.</span></span>  
  
3. <span data-ttu-id="2a93f-130">Proveďte jeden z následujících provozních konkrétní kroky pro povolit programu přes bránu Windows Firewall:</span><span class="sxs-lookup"><span data-stu-id="2a93f-130">Complete one of the following operating specific steps to allow a program through the Windows Firewall:</span></span>  
  
    -   <span data-ttu-id="2a93f-131">Na Windows 7 nebo Windows Server 2008 r2, klikněte na tlačítko **povolit program nebo funkci průchod bránou Windows Firewall**.</span><span class="sxs-lookup"><span data-stu-id="2a93f-131">On Windows 7 or Windows Server 2008 r2, click **Allow a program or feature through Windows Firewall**.</span></span> <span data-ttu-id="2a93f-132">Klikněte na tlačítko **změnit nastavení**, povolit **jiný Program...** .</span><span class="sxs-lookup"><span data-stu-id="2a93f-132">Click **Change Settings**, Allow **Another Program…**.</span></span>  
  
    -   <span data-ttu-id="2a93f-133">Na [!INCLUDE[wv](../../../../includes/wv-md.md)] nebo [!INCLUDE[lserver](../../../../includes/lserver-md.md)], klikněte na tlačítko **programu přes bránu Windows Firewall povolit**.</span><span class="sxs-lookup"><span data-stu-id="2a93f-133">On [!INCLUDE[wv](../../../../includes/wv-md.md)] or [!INCLUDE[lserver](../../../../includes/lserver-md.md)], click **Allow a program through Windows Firewall**.</span></span>  
  
4. <span data-ttu-id="2a93f-134">Na **výjimky** klikněte na tlačítko **přidat Program**.</span><span class="sxs-lookup"><span data-stu-id="2a93f-134">On the **Exceptions** tab, click **Add Program**.</span></span>  
  
5. <span data-ttu-id="2a93f-135">Klikněte na tlačítko **Procházet** tlačítko a vyberte spustitelný soubor, ukázky, které plánujete spouštět.</span><span class="sxs-lookup"><span data-stu-id="2a93f-135">Click the **Browse** button and select the executable file of the sample you plan to run.</span></span>  
  
6. <span data-ttu-id="2a93f-136">Opakujte kroky 4 a 5, dokud nepřidáte spustitelné soubory všechny ukázky, které chcete spustit.</span><span class="sxs-lookup"><span data-stu-id="2a93f-136">Repeat steps 4 and 5 until you have added the executable files of all the samples you plan to run.</span></span>  
  
7. <span data-ttu-id="2a93f-137">Klikněte na tlačítko **OK** zavřete aplet brány firewall.</span><span class="sxs-lookup"><span data-stu-id="2a93f-137">Click **OK** to close the firewall applet.</span></span>  
  
### <a name="to-enable-a-port-range-in-advance"></a><span data-ttu-id="2a93f-138">Povolit rozsah portů předem</span><span class="sxs-lookup"><span data-stu-id="2a93f-138">To enable a port range in advance</span></span>  
  
1. <span data-ttu-id="2a93f-139">Klikněte na tlačítko **Start**, klikněte na tlačítko **spustit**a typ `firewall.cpl`.</span><span class="sxs-lookup"><span data-stu-id="2a93f-139">Click **Start**, click **Run**, and type `firewall.cpl`.</span></span> <span data-ttu-id="2a93f-140">Tím se otevře **ovládacích panelů Windows Firewall** aplet.</span><span class="sxs-lookup"><span data-stu-id="2a93f-140">This opens the **Windows Firewall Control Panel** applet.</span></span>  
  
2. <span data-ttu-id="2a93f-141">Na Windows 7 nebo Windows Server 2008 R2 postupujte podle těchto kroků.</span><span class="sxs-lookup"><span data-stu-id="2a93f-141">On Windows 7 or Windows Server 2008 R2, follow these steps.</span></span>  
  
    1.  <span data-ttu-id="2a93f-142">Klikněte na tlačítko **upřesňující nastavení** v levém sloupci okna brána Windows Firewall.</span><span class="sxs-lookup"><span data-stu-id="2a93f-142">Click **Advanced settings** in the left column of the Windows Firewall window.</span></span>  
  
    2.  <span data-ttu-id="2a93f-143">Klikněte na tlačítko **příchozí pravidla** v levém sloupci.</span><span class="sxs-lookup"><span data-stu-id="2a93f-143">Click **Inbound Rules** in the left column.</span></span>  
  
    3.  <span data-ttu-id="2a93f-144">Klikněte na tlačítko **nová pravidla** v pravém sloupci.</span><span class="sxs-lookup"><span data-stu-id="2a93f-144">Click **New Rules** in the right column.</span></span>  
  
    4.  <span data-ttu-id="2a93f-145">Vyberte **Port** a klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="2a93f-145">Select **Port** and click **next**.</span></span>  
  
    5.  <span data-ttu-id="2a93f-146">Vyberte **TCP** a zadejte `8000, 8001, 8002, 8003, 9000, 80, 443` v **určité místní porty** pole.</span><span class="sxs-lookup"><span data-stu-id="2a93f-146">Select **TCP** and enter `8000, 8001, 8002, 8003, 9000, 80, 443` in the **Specific local ports** field.</span></span>  
  
    6.  <span data-ttu-id="2a93f-147">Klikněte na **Další**.</span><span class="sxs-lookup"><span data-stu-id="2a93f-147">Click **Next**.</span></span>  
  
    7.  <span data-ttu-id="2a93f-148">Vyberte **povolit připojení**a klikněte na tlačítko **Další** .</span><span class="sxs-lookup"><span data-stu-id="2a93f-148">Select **Allow the connection**, and click **Next** .</span></span>  
  
    8.  <span data-ttu-id="2a93f-149">Vyberte **domény** a **privátní**a klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="2a93f-149">Select **Domain** and **Private**, and click **Next**.</span></span>  
  
    9. <span data-ttu-id="2a93f-150">Název tohoto pravidla `WCF-WF 4.0 Samples`a klikněte na tlačítko **Dokončit**.</span><span class="sxs-lookup"><span data-stu-id="2a93f-150">Name this rule `WCF-WF 4.0 Samples`, and click **Finish**.</span></span>  
  
    10. <span data-ttu-id="2a93f-151">Klikněte na tlačítko **odchozí pravidla** a opakujte kroky c h.</span><span class="sxs-lookup"><span data-stu-id="2a93f-151">Click **Outbound Rules** and repeat steps c to h.</span></span>  
  
3. <span data-ttu-id="2a93f-152">Na [!INCLUDE[wv](../../../../includes/wv-md.md)] nebo [!INCLUDE[lserver](../../../../includes/lserver-md.md)], postupujte podle těchto kroků.</span><span class="sxs-lookup"><span data-stu-id="2a93f-152">On [!INCLUDE[wv](../../../../includes/wv-md.md)] or [!INCLUDE[lserver](../../../../includes/lserver-md.md)], follow these steps.</span></span>  
  
    1.  <span data-ttu-id="2a93f-153">Klikněte na tlačítko **programu přes bránu Windows Firewall povolit**.</span><span class="sxs-lookup"><span data-stu-id="2a93f-153">Click **Allow a program through Windows Firewall**.</span></span>  
  
    2.  <span data-ttu-id="2a93f-154">Na **výjimky** klikněte na tlačítko **přidat Port**.</span><span class="sxs-lookup"><span data-stu-id="2a93f-154">On the **Exceptions** tab, click **Add Port**.</span></span>  
  
    3.  <span data-ttu-id="2a93f-155">Zadejte název, zadejte jako číslo portu 8000 a vyberte **TCP** možnost.</span><span class="sxs-lookup"><span data-stu-id="2a93f-155">Enter a name, enter 8000 as the port number, and select the **TCP** option.</span></span>  
  
    4.  <span data-ttu-id="2a93f-156">Klikněte na tlačítko **změnit obor** tlačítka, vyberte **Moje sítě** jedinou možností (podsítě) a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="2a93f-156">Click the **Change Scope** button, select the **My Network** (subnet) only option, and click **OK**.</span></span>  
  
    5.  <span data-ttu-id="2a93f-157">Opakujte kroky b až d pro porty 8001, 8002 8003, 9000, 80 a 443.</span><span class="sxs-lookup"><span data-stu-id="2a93f-157">Repeat steps b to d for ports 8001, 8002, 8003, 9000, 80, and 443.</span></span>  
  
4. <span data-ttu-id="2a93f-158">Klikněte na tlačítko **OK** zavřete aplet brány firewall.</span><span class="sxs-lookup"><span data-stu-id="2a93f-158">Click **OK** to close the firewall applet.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a93f-159">Po dokončení práce s ukázkami, odeberte všechny výjimky brány firewall.</span><span class="sxs-lookup"><span data-stu-id="2a93f-159">Remove any firewall exceptions when you are finished working with the samples.</span></span> <span data-ttu-id="2a93f-160">Chcete-li to provést, otevřete **ovládacích panelů Windows Firewall** aplet a odebrání všech programů nebo port položky, které byly přidány podle předchozích kroků.</span><span class="sxs-lookup"><span data-stu-id="2a93f-160">To do so, open the **Windows Firewall Control Panel** applet and remove any programs or port entries that were added by the previous procedures.</span></span>
