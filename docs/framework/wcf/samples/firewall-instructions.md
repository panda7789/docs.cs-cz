---
title: Pokyny k bráně firewall
ms.date: 03/30/2017
ms.assetid: a7dc429f-65ac-4faf-974a-77d5fb977fe1
ms.openlocfilehash: 5e557963c415cf39c4f25b4854c9863652201146
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961406"
---
# <a name="firewall-instructions"></a><span data-ttu-id="87bc3-102">Pokyny k bráně firewall</span><span class="sxs-lookup"><span data-stu-id="87bc3-102">Firewall Instructions</span></span>
<span data-ttu-id="87bc3-103">Musíte povolit několik portů nebo programů v bráně firewall, aby mohli ukázky Windows Communication Foundation (WCF) fungovat.</span><span class="sxs-lookup"><span data-stu-id="87bc3-103">You must enable several ports or programs in the firewall so that the Windows Communication Foundation (WCF) samples can function.</span></span> <span data-ttu-id="87bc3-104">Řada ukázek komunikuje pomocí portů v rozsahu 8000-8003 a portu 9000.</span><span class="sxs-lookup"><span data-stu-id="87bc3-104">Many of the samples communicate by using ports in the range 8000-8003, and port 9000.</span></span> <span data-ttu-id="87bc3-105">Brána firewall je ve výchozím nastavení zapnutá a brání přístupu k těmto portům.</span><span class="sxs-lookup"><span data-stu-id="87bc3-105">The firewall is turned on by default and prevents access to these ports.</span></span> <span data-ttu-id="87bc3-106">Pokud chcete bránu firewall povolit pro ukázky, proveďte v závislosti na vašich požadavcích a prostředí zabezpečení jeden z následujících postupů:</span><span class="sxs-lookup"><span data-stu-id="87bc3-106">To enable the firewall for the samples, complete one of the following procedures, depending on your requirements and security environment:</span></span>  
  
- <span data-ttu-id="87bc3-107">Možnost 1: Interaktivní povolení vzorků při spuštění.</span><span class="sxs-lookup"><span data-stu-id="87bc3-107">Option 1: Interactively enable samples while running.</span></span> <span data-ttu-id="87bc3-108">Neprovádějte žádné změny konfigurace brány firewall a pokračujte v sestavování a spouštění ukázek.</span><span class="sxs-lookup"><span data-stu-id="87bc3-108">Make no advance changes to your firewall configuration and proceed to start building and running the samples.</span></span> <span data-ttu-id="87bc3-109">Při spuštění ukázky se zobrazí dialogové okno **Výstraha zabezpečení systému Windows** .</span><span class="sxs-lookup"><span data-stu-id="87bc3-109">When a sample is run, a **Windows Security Alert** dialog box appears.</span></span> <span data-ttu-id="87bc3-110">Daný vzorový program lze následně přidat interaktivně do odblokovaného seznamu.</span><span class="sxs-lookup"><span data-stu-id="87bc3-110">The sample program in question can then be added interactively to an unblocked list.</span></span> <span data-ttu-id="87bc3-111">Pomocí tohoto postupu bude pravděpodobně nutné znovu spustit ukázku.</span><span class="sxs-lookup"><span data-stu-id="87bc3-111">With this procedure, you may have to then restart the sample.</span></span>  
  
- <span data-ttu-id="87bc3-112">Možnost 2: Povolit ukázkové programy předem</span><span class="sxs-lookup"><span data-stu-id="87bc3-112">Option 2: Enable sample programs in advance.</span></span> <span data-ttu-id="87bc3-113">Spusťte aplet **ovládacího panelu brány Windows Firewall** a povolte ukázkové programy, které chcete spustit.</span><span class="sxs-lookup"><span data-stu-id="87bc3-113">Start the **Windows Firewall Control Panel** applet and enable the sample programs you plan to run.</span></span> <span data-ttu-id="87bc3-114">Nejprve musíte vytvořit programy, aby existovaly spustitelné soubory.</span><span class="sxs-lookup"><span data-stu-id="87bc3-114">You must build the programs first so the executable files exist.</span></span> <span data-ttu-id="87bc3-115">Podrobnější pokyny najdete v následujícím postupu.</span><span class="sxs-lookup"><span data-stu-id="87bc3-115">You can find more detailed instructions in the following procedure.</span></span>  
  
- <span data-ttu-id="87bc3-116">Možnost 3: Zapněte rozsah portů předem.</span><span class="sxs-lookup"><span data-stu-id="87bc3-116">Option 3: Enable a port range in advance.</span></span> <span data-ttu-id="87bc3-117">Spusťte aplet **ovládacího panelu** **brány Windows Firewall** a povolte porty 80, 443, 8000-8003 a 9000, které jsou používány ukázkami.</span><span class="sxs-lookup"><span data-stu-id="87bc3-117">Start the **Windows Firewall** **Control Panel** applet and enable ports 80, 443, 8000-8003 and 9000, which are used by the samples.</span></span> <span data-ttu-id="87bc3-118">Podrobnější pokyny najdete v následujícím postupu.</span><span class="sxs-lookup"><span data-stu-id="87bc3-118">You can find more detailed instructions in the following procedure.</span></span> <span data-ttu-id="87bc3-119">Tato možnost je méně bezpečná než ostatní, protože umožňuje jakýmkoli programům používat tyto porty, nikoli jenom ukázky.</span><span class="sxs-lookup"><span data-stu-id="87bc3-119">This option is less secure than the others because it allows any program to use these ports, not just the samples.</span></span>  
  
 <span data-ttu-id="87bc3-120">Pokud si nejste jistí, který postup chcete použít, vyberte první možnost.</span><span class="sxs-lookup"><span data-stu-id="87bc3-120">If you are unsure of which procedure to use, choose the first option.</span></span> <span data-ttu-id="87bc3-121">Pokud používáte bránu firewall od jiného dodavatele, možná budete muset udělat podobné změny.</span><span class="sxs-lookup"><span data-stu-id="87bc3-121">If you are running a firewall from another vendor, you might need to make similar changes.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="87bc3-122">Změna konfigurace brány firewall má vliv na vaše zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="87bc3-122">Changing your firewall configuration affects your security.</span></span> <span data-ttu-id="87bc3-123">Doporučujeme, abyste záznamy, které jste provedli, zaznamenali a odebrali je po dokončení práce s ukázkami.</span><span class="sxs-lookup"><span data-stu-id="87bc3-123">It is recommended that you record the changes you make and remove them when you are finished working with the samples.</span></span>  
  
### <a name="to-enable-samples-programs-in-advance"></a><span data-ttu-id="87bc3-124">Postup při zapnutí ukázek programů předem</span><span class="sxs-lookup"><span data-stu-id="87bc3-124">To enable samples programs in advance</span></span>  
  
1. <span data-ttu-id="87bc3-125">Sestavte ukázku.</span><span class="sxs-lookup"><span data-stu-id="87bc3-125">Build the sample.</span></span>  
  
2. <span data-ttu-id="87bc3-126">Klikněte na **Start**, klikněte na **Spustit**a `firewall.cpl`zadejte.</span><span class="sxs-lookup"><span data-stu-id="87bc3-126">Click **Start**, click **Run**, and type `firewall.cpl`.</span></span> <span data-ttu-id="87bc3-127">Tím se otevře aplet **ovládacího panelu brány Windows Firewall** .</span><span class="sxs-lookup"><span data-stu-id="87bc3-127">This opens the **Windows Firewall Control Panel** applet.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="87bc3-128">Abyste mohli spouštět ukázky, které vyžadují komunikaci přes bránu Windows Firewall, musíte mít oprávnění ke změně nastavení brány firewall.</span><span class="sxs-lookup"><span data-stu-id="87bc3-128">You must have permission to change the Firewall settings to run samples that require the ability to communicate through the Windows Firewall.</span></span> <span data-ttu-id="87bc3-129">Pokud některá nastavení brány firewall nejsou k dispozici a počítač je připojen k doméně, může správce systému řídit tato nastavení prostřednictvím Zásady skupiny.</span><span class="sxs-lookup"><span data-stu-id="87bc3-129">If some firewall settings are unavailable and your computer is connected to a domain, your system administrator might be controlling these settings through Group Policy.</span></span>  
  
3. <span data-ttu-id="87bc3-130">Provedením jednoho z následujících postupů pro povolení programu v bráně Windows Firewall:</span><span class="sxs-lookup"><span data-stu-id="87bc3-130">Complete one of the following operating specific steps to allow a program through the Windows Firewall:</span></span>  
  
    - <span data-ttu-id="87bc3-131">V systému Windows 7 nebo Windows Server 2008 R2 klikněte na možnost **Povolení programu nebo funkce přes bránu Windows Firewall**.</span><span class="sxs-lookup"><span data-stu-id="87bc3-131">On Windows 7 or Windows Server 2008 r2, click **Allow a program or feature through Windows Firewall**.</span></span> <span data-ttu-id="87bc3-132">Klikněte na **změnit nastavení**, připustit **jiný program...** .</span><span class="sxs-lookup"><span data-stu-id="87bc3-132">Click **Change Settings**, Allow **Another Program…**.</span></span>  
  
    - <span data-ttu-id="87bc3-133">V [!INCLUDE[wv](../../../../includes/wv-md.md)] nebo[!INCLUDE[lserver](../../../../includes/lserver-md.md)]klikněte na možnost **Zapnout program přes bránu Windows Firewall**.</span><span class="sxs-lookup"><span data-stu-id="87bc3-133">On [!INCLUDE[wv](../../../../includes/wv-md.md)] or [!INCLUDE[lserver](../../../../includes/lserver-md.md)], click **Allow a program through Windows Firewall**.</span></span>  
  
4. <span data-ttu-id="87bc3-134">Na kartě **výjimky** klikněte na **Přidat program**.</span><span class="sxs-lookup"><span data-stu-id="87bc3-134">On the **Exceptions** tab, click **Add Program**.</span></span>  
  
5. <span data-ttu-id="87bc3-135">Klikněte na tlačítko **Procházet** a vyberte spustitelný soubor ukázkového plánu, který chcete spustit.</span><span class="sxs-lookup"><span data-stu-id="87bc3-135">Click the **Browse** button and select the executable file of the sample you plan to run.</span></span>  
  
6. <span data-ttu-id="87bc3-136">Opakujte kroky 4 a 5, dokud nepřidáte spustitelné soubory všech ukázek, které máte v plánu spouštět.</span><span class="sxs-lookup"><span data-stu-id="87bc3-136">Repeat steps 4 and 5 until you have added the executable files of all the samples you plan to run.</span></span>  
  
7. <span data-ttu-id="87bc3-137">Kliknutím na tlačítko **OK** zavřete aplet brány firewall.</span><span class="sxs-lookup"><span data-stu-id="87bc3-137">Click **OK** to close the firewall applet.</span></span>  
  
### <a name="to-enable-a-port-range-in-advance"></a><span data-ttu-id="87bc3-138">Postup při povolení rozsahu portů předem</span><span class="sxs-lookup"><span data-stu-id="87bc3-138">To enable a port range in advance</span></span>  
  
1. <span data-ttu-id="87bc3-139">Klikněte na **Start**, klikněte na **Spustit**a `firewall.cpl`zadejte.</span><span class="sxs-lookup"><span data-stu-id="87bc3-139">Click **Start**, click **Run**, and type `firewall.cpl`.</span></span> <span data-ttu-id="87bc3-140">Tím se otevře aplet **ovládacího panelu brány Windows Firewall** .</span><span class="sxs-lookup"><span data-stu-id="87bc3-140">This opens the **Windows Firewall Control Panel** applet.</span></span>  
  
2. <span data-ttu-id="87bc3-141">V systému Windows 7 nebo Windows Server 2008 R2 postupujte podle těchto kroků.</span><span class="sxs-lookup"><span data-stu-id="87bc3-141">On Windows 7 or Windows Server 2008 R2, follow these steps.</span></span>  
  
    1. <span data-ttu-id="87bc3-142">V levém sloupci okna brány Windows Firewall klikněte na **Upřesnit nastavení** .</span><span class="sxs-lookup"><span data-stu-id="87bc3-142">Click **Advanced settings** in the left column of the Windows Firewall window.</span></span>  
  
    2. <span data-ttu-id="87bc3-143">V levém sloupci klikněte na **příchozí pravidla** .</span><span class="sxs-lookup"><span data-stu-id="87bc3-143">Click **Inbound Rules** in the left column.</span></span>  
  
    3. <span data-ttu-id="87bc3-144">Klikněte na **Nová pravidla** v pravém sloupci.</span><span class="sxs-lookup"><span data-stu-id="87bc3-144">Click **New Rules** in the right column.</span></span>  
  
    4. <span data-ttu-id="87bc3-145">Vyberte **port** a klikněte na **Další**.</span><span class="sxs-lookup"><span data-stu-id="87bc3-145">Select **Port** and click **next**.</span></span>  
  
    5. <span data-ttu-id="87bc3-146">Vyberte **TCP** a zadejte `8000, 8001, 8002, 8003, 9000, 80, 443` do pole **konkrétní místní porty** .</span><span class="sxs-lookup"><span data-stu-id="87bc3-146">Select **TCP** and enter `8000, 8001, 8002, 8003, 9000, 80, 443` in the **Specific local ports** field.</span></span>  
  
    6. <span data-ttu-id="87bc3-147">Klikněte na **Další**.</span><span class="sxs-lookup"><span data-stu-id="87bc3-147">Click **Next**.</span></span>  
  
    7. <span data-ttu-id="87bc3-148">Vyberte možnost **Povolení připojení**a klikněte na tlačítko **Další** .</span><span class="sxs-lookup"><span data-stu-id="87bc3-148">Select **Allow the connection**, and click **Next** .</span></span>  
  
    8. <span data-ttu-id="87bc3-149">Vyberte **doména** a **privátní**a klikněte na **Další**.</span><span class="sxs-lookup"><span data-stu-id="87bc3-149">Select **Domain** and **Private**, and click **Next**.</span></span>  
  
    9. <span data-ttu-id="87bc3-150">Pojmenujte `WCF-WF 4.0 Samples`toto pravidlo a klikněte na **Dokončit**.</span><span class="sxs-lookup"><span data-stu-id="87bc3-150">Name this rule `WCF-WF 4.0 Samples`, and click **Finish**.</span></span>  
  
    10. <span data-ttu-id="87bc3-151">Klikněte na **odchozí pravidla** a opakujte kroky c až h.</span><span class="sxs-lookup"><span data-stu-id="87bc3-151">Click **Outbound Rules** and repeat steps c to h.</span></span>  
  
3. <span data-ttu-id="87bc3-152">V [!INCLUDE[wv](../../../../includes/wv-md.md)] systému [!INCLUDE[lserver](../../../../includes/lserver-md.md)]nebo použijte následující postup.</span><span class="sxs-lookup"><span data-stu-id="87bc3-152">On [!INCLUDE[wv](../../../../includes/wv-md.md)] or [!INCLUDE[lserver](../../../../includes/lserver-md.md)], follow these steps.</span></span>  
  
    1. <span data-ttu-id="87bc3-153">Klikněte na možnost **Povolení programu přes bránu Windows Firewall**.</span><span class="sxs-lookup"><span data-stu-id="87bc3-153">Click **Allow a program through Windows Firewall**.</span></span>  
  
    2. <span data-ttu-id="87bc3-154">Na kartě **výjimky** klikněte na **Přidat port**.</span><span class="sxs-lookup"><span data-stu-id="87bc3-154">On the **Exceptions** tab, click **Add Port**.</span></span>  
  
    3. <span data-ttu-id="87bc3-155">Zadejte název, jako číslo portu zadejte 8000 a vyberte možnost **TCP** .</span><span class="sxs-lookup"><span data-stu-id="87bc3-155">Enter a name, enter 8000 as the port number, and select the **TCP** option.</span></span>  
  
    4. <span data-ttu-id="87bc3-156">Klikněte na tlačítko **změnit obor** , vyberte možnost pouze **Moje síť** (podsíť) a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="87bc3-156">Click the **Change Scope** button, select the **My Network** (subnet) only option, and click **OK**.</span></span>  
  
    5. <span data-ttu-id="87bc3-157">Opakujte kroky b až d pro porty 8001, 8002, 8003, 9000, 80 a 443.</span><span class="sxs-lookup"><span data-stu-id="87bc3-157">Repeat steps b to d for ports 8001, 8002, 8003, 9000, 80, and 443.</span></span>  
  
4. <span data-ttu-id="87bc3-158">Kliknutím na tlačítko **OK** zavřete aplet brány firewall.</span><span class="sxs-lookup"><span data-stu-id="87bc3-158">Click **OK** to close the firewall applet.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="87bc3-159">Po dokončení práce s ukázkami odeberte všechny výjimky brány firewall.</span><span class="sxs-lookup"><span data-stu-id="87bc3-159">Remove any firewall exceptions when you are finished working with the samples.</span></span> <span data-ttu-id="87bc3-160">Provedete to tak, že otevřete aplet **ovládacího panelu brány Windows Firewall** a odeberete všechny programy nebo položky portů, které byly přidány předchozími postupy.</span><span class="sxs-lookup"><span data-stu-id="87bc3-160">To do so, open the **Windows Firewall Control Panel** applet and remove any programs or port entries that were added by the previous procedures.</span></span>
