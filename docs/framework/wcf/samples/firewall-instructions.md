---
title: "Pokyny k bráně firewall"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7dc429f-65ac-4faf-974a-77d5fb977fe1
caps.latest.revision: "32"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0aac3a161b0482bad1a32f5223d2031402a632cc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="firewall-instructions"></a><span data-ttu-id="40003-102">Pokyny k bráně firewall</span><span class="sxs-lookup"><span data-stu-id="40003-102">Firewall Instructions</span></span>
<span data-ttu-id="40003-103">Musíte povolit několik portů nebo programů v bráně firewall tak, která [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ukázky, můžou fungovat.</span><span class="sxs-lookup"><span data-stu-id="40003-103">You must enable several ports or programs in the firewall so that the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] samples can function.</span></span> <span data-ttu-id="40003-104">Řadu ukázky komunikovat prostřednictvím portů v rozsahu 8000-8003 a portu 9000.</span><span class="sxs-lookup"><span data-stu-id="40003-104">Many of the samples communicate by using ports in the range 8000-8003, and port 9000.</span></span> <span data-ttu-id="40003-105">Brána firewall je ve výchozím nastavení zapnuta a brání přístupu k těmto portům.</span><span class="sxs-lookup"><span data-stu-id="40003-105">The firewall is turned on by default and prevents access to these ports.</span></span> <span data-ttu-id="40003-106">Pokud chcete povolit bránu firewall pro ukázky, proveďte jednu z následujících postupů, v závislosti na vašich požadavcích a zabezpečení prostředí:</span><span class="sxs-lookup"><span data-stu-id="40003-106">To enable the firewall for the samples, complete one of the following procedures, depending on your requirements and security environment:</span></span>  
  
-   <span data-ttu-id="40003-107">Možnost 1: Povolení interaktivní ukázky během spuštění.</span><span class="sxs-lookup"><span data-stu-id="40003-107">Option 1: Interactively enable samples while running.</span></span> <span data-ttu-id="40003-108">Neprovedete žádné změny záloh konfigurace brány firewall a pokračujte začít sestavovat a spouštět ukázky.</span><span class="sxs-lookup"><span data-stu-id="40003-108">Make no advance changes to your firewall configuration and proceed to start building and running the samples.</span></span> <span data-ttu-id="40003-109">Když se spustí ukázku, **výstraha zabezpečení Windows** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="40003-109">When a sample is run, a **Windows Security Alert** dialog box appears.</span></span> <span data-ttu-id="40003-110">Ukázkový program dotyčném lze přidat interaktivně odblokuje seznamu.</span><span class="sxs-lookup"><span data-stu-id="40003-110">The sample program in question can then be added interactively to an unblocked list.</span></span> <span data-ttu-id="40003-111">Pomocí tohoto postupu budete muset znovu spusťte vzorku.</span><span class="sxs-lookup"><span data-stu-id="40003-111">With this procedure, you may have to then restart the sample.</span></span>  
  
-   <span data-ttu-id="40003-112">Možnost 2: Povolení předem ukázkové aplikace.</span><span class="sxs-lookup"><span data-stu-id="40003-112">Option 2: Enable sample programs in advance.</span></span> <span data-ttu-id="40003-113">Spuštění **ovládacích panelů Windows Firewall** aplet a povolit ukázku programy plán ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="40003-113">Start the **Windows Firewall Control Panel** applet and enable the sample programs you plan to run.</span></span> <span data-ttu-id="40003-114">Programy musí nejprve vytvořit tak spustitelné soubory existují.</span><span class="sxs-lookup"><span data-stu-id="40003-114">You must build the programs first so the executable files exist.</span></span> <span data-ttu-id="40003-115">Podrobnější pokyny najdete v následujícím postupu.</span><span class="sxs-lookup"><span data-stu-id="40003-115">You can find more detailed instructions in the following procedure.</span></span>  
  
-   <span data-ttu-id="40003-116">Možnost 3: Povolení předem rozsah portů.</span><span class="sxs-lookup"><span data-stu-id="40003-116">Option 3: Enable a port range in advance.</span></span> <span data-ttu-id="40003-117">Spuštění **brány Windows Firewall** **ovládací panely** aplet a povolit porty 80 a 443, 8000 8003 a 9000, které jsou používány ukázky.</span><span class="sxs-lookup"><span data-stu-id="40003-117">Start the **Windows Firewall** **Control Panel** applet and enable ports 80, 443, 8000-8003 and 9000, which are used by the samples.</span></span> <span data-ttu-id="40003-118">Podrobnější pokyny najdete v následujícím postupu.</span><span class="sxs-lookup"><span data-stu-id="40003-118">You can find more detailed instructions in the following procedure.</span></span> <span data-ttu-id="40003-119">Tato možnost je méně bezpečné než jiné, protože umožňuje žádné program použít tyto porty, ne jenom ukázky.</span><span class="sxs-lookup"><span data-stu-id="40003-119">This option is less secure than the others because it allows any program to use these ports, not just the samples.</span></span>  
  
 <span data-ttu-id="40003-120">Pokud si nejste jistí, z kterého postupu se má použít, zvolte první možnost.</span><span class="sxs-lookup"><span data-stu-id="40003-120">If you are unsure of which procedure to use, choose the first option.</span></span> <span data-ttu-id="40003-121">Pokud používáte firewall od jiného dodavatele, musíte může provádět podobné změny.</span><span class="sxs-lookup"><span data-stu-id="40003-121">If you are running a firewall from another vendor, you might need to make similar changes.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="40003-122">Změna konfigurace brány firewall má vliv na zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="40003-122">Changing your firewall configuration affects your security.</span></span> <span data-ttu-id="40003-123">Doporučuje se záznamu změny, ujistěte se a po skončení práce s ukázky je odebrat.</span><span class="sxs-lookup"><span data-stu-id="40003-123">It is recommended that you record the changes you make and remove them when you are finished working with the samples.</span></span>  
  
### <a name="to-enable-samples-programs-in-advance"></a><span data-ttu-id="40003-124">Chcete-li povolit programy ukázky předem</span><span class="sxs-lookup"><span data-stu-id="40003-124">To enable samples programs in advance</span></span>  
  
1.  <span data-ttu-id="40003-125">Sestavte ukázku.</span><span class="sxs-lookup"><span data-stu-id="40003-125">Build the sample.</span></span>  
  
2.  <span data-ttu-id="40003-126">Klikněte na tlačítko **spustit**, klikněte na tlačítko **spustit**a typ `firewall.cpl`.</span><span class="sxs-lookup"><span data-stu-id="40003-126">Click **Start**, click **Run**, and type `firewall.cpl`.</span></span> <span data-ttu-id="40003-127">Tím se otevře **ovládacích panelů Windows Firewall** aplet.</span><span class="sxs-lookup"><span data-stu-id="40003-127">This opens the **Windows Firewall Control Panel** applet.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="40003-128">Musíte mít oprávnění ke změně nastavení brány Firewall ke spuštění ukázky, které potřebují ke komunikaci přes bránu Windows Firewall.</span><span class="sxs-lookup"><span data-stu-id="40003-128">You must have permission to change the Firewall settings to run samples that require the ability to communicate through the Windows Firewall.</span></span> <span data-ttu-id="40003-129">Pokud některá nastavení brány firewall nejsou k dispozici a je počítač připojen k doméně, správce systému může být tato nastavení řídí prostřednictvím zásad skupiny.</span><span class="sxs-lookup"><span data-stu-id="40003-129">If some firewall settings are unavailable and your computer is connected to a domain, your system administrator might be controlling these settings through Group Policy.</span></span>  
  
3.  <span data-ttu-id="40003-130">Proveďte jeden z následujících operační konkrétní kroků povolit program přes bránu Windows Firewall:</span><span class="sxs-lookup"><span data-stu-id="40003-130">Complete one of the following operating specific steps to allow a program through the Windows Firewall:</span></span>  
  
    -   <span data-ttu-id="40003-131">V systému Windows 7 nebo Windows Server 2008 r2, klikněte na tlačítko **povolit program nebo funkci průchod bránou Windows Firewall**.</span><span class="sxs-lookup"><span data-stu-id="40003-131">On Windows 7 or Windows Server 2008 r2, click **Allow a program or feature through Windows Firewall**.</span></span> <span data-ttu-id="40003-132">Klikněte na tlačítko **změnit nastavení**, povolit **jiný Program...** .</span><span class="sxs-lookup"><span data-stu-id="40003-132">Click **Change Settings**, Allow **Another Program…**.</span></span>  
  
    -   <span data-ttu-id="40003-133">Na [!INCLUDE[wv](../../../../includes/wv-md.md)] nebo [!INCLUDE[lserver](../../../../includes/lserver-md.md)], klikněte na tlačítko **programu přes bránu Windows Firewall povolit**.</span><span class="sxs-lookup"><span data-stu-id="40003-133">On [!INCLUDE[wv](../../../../includes/wv-md.md)] or [!INCLUDE[lserver](../../../../includes/lserver-md.md)], click **Allow a program through Windows Firewall**.</span></span>  
  
4.  <span data-ttu-id="40003-134">Na **výjimky** , klikněte na **přidat Program**.</span><span class="sxs-lookup"><span data-stu-id="40003-134">On the **Exceptions** tab, click **Add Program**.</span></span>  
  
5.  <span data-ttu-id="40003-135">Klikněte **Procházet** tlačítko a vyberte spustitelný soubor, ukázky, které chcete spustit.</span><span class="sxs-lookup"><span data-stu-id="40003-135">Click the **Browse** button and select the executable file of the sample you plan to run.</span></span>  
  
6.  <span data-ttu-id="40003-136">Opakujte kroky 4 a 5, dokud nepřidáte všechny ukázky, které plánujete spouštět spustitelné soubory.</span><span class="sxs-lookup"><span data-stu-id="40003-136">Repeat steps 4 and 5 until you have added the executable files of all the samples you plan to run.</span></span>  
  
7.  <span data-ttu-id="40003-137">Klikněte na tlačítko **OK** zavřete apletu brány firewall.</span><span class="sxs-lookup"><span data-stu-id="40003-137">Click **OK** to close the firewall applet.</span></span>  
  
### <a name="to-enable-a-port-range-in-advance"></a><span data-ttu-id="40003-138">Chcete-li povolit rozsah portů předem</span><span class="sxs-lookup"><span data-stu-id="40003-138">To enable a port range in advance</span></span>  
  
1.  <span data-ttu-id="40003-139">Klikněte na tlačítko **spustit**, klikněte na tlačítko **spustit**a typ `firewall.cpl`.</span><span class="sxs-lookup"><span data-stu-id="40003-139">Click **Start**, click **Run**, and type `firewall.cpl`.</span></span> <span data-ttu-id="40003-140">Tím se otevře **ovládacích panelů Windows Firewall** aplet.</span><span class="sxs-lookup"><span data-stu-id="40003-140">This opens the **Windows Firewall Control Panel** applet.</span></span>  
  
2.  <span data-ttu-id="40003-141">Windows 7 nebo Windows Server 2008 R2 postupujte podle těchto kroků.</span><span class="sxs-lookup"><span data-stu-id="40003-141">On Windows 7 or Windows Server 2008 R2, follow these steps.</span></span>  
  
    1.  <span data-ttu-id="40003-142">Klikněte na tlačítko **upřesňující nastavení** v levém sloupci okna brány Windows Firewall.</span><span class="sxs-lookup"><span data-stu-id="40003-142">Click **Advanced settings** in the left column of the Windows Firewall window.</span></span>  
  
    2.  <span data-ttu-id="40003-143">Klikněte na tlačítko **příchozí pravidla** v levém sloupci.</span><span class="sxs-lookup"><span data-stu-id="40003-143">Click **Inbound Rules** in the left column.</span></span>  
  
    3.  <span data-ttu-id="40003-144">Klikněte na tlačítko **nové pravidel** v pravém sloupci.</span><span class="sxs-lookup"><span data-stu-id="40003-144">Click **New Rules** in the right column.</span></span>  
  
    4.  <span data-ttu-id="40003-145">Vyberte **Port** a klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="40003-145">Select **Port** and click **next**.</span></span>  
  
    5.  <span data-ttu-id="40003-146">Vyberte **TCP** a zadejte `8000, 8001, 8002, 8003, 9000, 80, 443` v **určité místní porty** pole.</span><span class="sxs-lookup"><span data-stu-id="40003-146">Select **TCP** and enter `8000, 8001, 8002, 8003, 9000, 80, 443` in the **Specific local ports** field.</span></span>  
  
    6.  <span data-ttu-id="40003-147">Klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="40003-147">Click **Next**.</span></span>  
  
    7.  <span data-ttu-id="40003-148">Vyberte **povolit připojení**a klikněte na tlačítko **Další** .</span><span class="sxs-lookup"><span data-stu-id="40003-148">Select **Allow the connection**, and click **Next** .</span></span>  
  
    8.  <span data-ttu-id="40003-149">Vyberte **domény** a **privátní**a klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="40003-149">Select **Domain** and **Private**, and click **Next**.</span></span>  
  
    9. <span data-ttu-id="40003-150">Název tohoto pravidla `WCF-WF 4.0 Samples`a klikněte na tlačítko **Dokončit**.</span><span class="sxs-lookup"><span data-stu-id="40003-150">Name this rule `WCF-WF 4.0 Samples`, and click **Finish**.</span></span>  
  
    10. <span data-ttu-id="40003-151">Klikněte na tlačítko **odchozí pravidla** a opakujte kroky c h.</span><span class="sxs-lookup"><span data-stu-id="40003-151">Click **Outbound Rules** and repeat steps c to h.</span></span>  
  
3.  <span data-ttu-id="40003-152">Na [!INCLUDE[wv](../../../../includes/wv-md.md)] nebo [!INCLUDE[lserver](../../../../includes/lserver-md.md)], postupujte podle těchto kroků.</span><span class="sxs-lookup"><span data-stu-id="40003-152">On [!INCLUDE[wv](../../../../includes/wv-md.md)] or [!INCLUDE[lserver](../../../../includes/lserver-md.md)], follow these steps.</span></span>  
  
    1.  <span data-ttu-id="40003-153">Klikněte na tlačítko **programu přes bránu Windows Firewall povolit**.</span><span class="sxs-lookup"><span data-stu-id="40003-153">Click **Allow a program through Windows Firewall**.</span></span>  
  
    2.  <span data-ttu-id="40003-154">Na **výjimky** , klikněte na **přidat Port**.</span><span class="sxs-lookup"><span data-stu-id="40003-154">On the **Exceptions** tab, click **Add Port**.</span></span>  
  
    3.  <span data-ttu-id="40003-155">Zadejte název a 8000 jako číslo portu a vyberte **TCP** možnost.</span><span class="sxs-lookup"><span data-stu-id="40003-155">Enter a name, enter 8000 as the port number, and select the **TCP** option.</span></span>  
  
    4.  <span data-ttu-id="40003-156">Klikněte na tlačítko **změnit obor** tlačítko, vyberte **Moje sítě** pouze možnost (podsítě) a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="40003-156">Click the **Change Scope** button, select the **My Network** (subnet) only option, and click **OK**.</span></span>  
  
    5.  <span data-ttu-id="40003-157">Opakujte kroky b d pro porty 8001, 8002, 8003, 9000, 80 a 443.</span><span class="sxs-lookup"><span data-stu-id="40003-157">Repeat steps b to d for ports 8001, 8002, 8003, 9000, 80, and 443.</span></span>  
  
4.  <span data-ttu-id="40003-158">Klikněte na tlačítko **OK** zavřete apletu brány firewall.</span><span class="sxs-lookup"><span data-stu-id="40003-158">Click **OK** to close the firewall applet.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="40003-159">Po dokončení práce s ukázky, odeberte všechny výjimky brány firewall.</span><span class="sxs-lookup"><span data-stu-id="40003-159">Remove any firewall exceptions when you are finished working with the samples.</span></span> <span data-ttu-id="40003-160">Chcete-li to provést, otevřete **ovládacích panelů Windows Firewall** aplet a odeberte všechny programy nebo portu položky, které byly přidány jako předchozí postupy.</span><span class="sxs-lookup"><span data-stu-id="40003-160">To do so, open the **Windows Firewall Control Panel** applet and remove any programs or port entries that were added by the previous procedures.</span></span>
