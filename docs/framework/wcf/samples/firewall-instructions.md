---
title: Pokyny k bráně firewall
description: Přečtěte si, jak povolit porty nebo programy v bráně firewall pro ukázky WCF. V závislosti na vašich požadavcích a prostředí zabezpečení použijte jeden z těchto postupů.
ms.date: 03/30/2017
ms.assetid: a7dc429f-65ac-4faf-974a-77d5fb977fe1
ms.openlocfilehash: de55d067960b8f2096c129f6feaf037219e06a96
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246138"
---
# <a name="firewall-instructions"></a><span data-ttu-id="4c79a-104">Pokyny pro bránu firewall</span><span class="sxs-lookup"><span data-stu-id="4c79a-104">Firewall instructions</span></span>

<span data-ttu-id="4c79a-105">Musíte povolit několik portů nebo programů v bráně firewall, aby mohli ukázky Windows Communication Foundation (WCF) fungovat.</span><span class="sxs-lookup"><span data-stu-id="4c79a-105">You must enable several ports or programs in the firewall so that the Windows Communication Foundation (WCF) samples can function.</span></span> <span data-ttu-id="4c79a-106">Řada ukázek komunikuje pomocí portů v rozsahu 8000-8003 a portu 9000.</span><span class="sxs-lookup"><span data-stu-id="4c79a-106">Many of the samples communicate by using ports in the range 8000-8003, and port 9000.</span></span> <span data-ttu-id="4c79a-107">Brána firewall je ve výchozím nastavení zapnutá a brání přístupu k těmto portům.</span><span class="sxs-lookup"><span data-stu-id="4c79a-107">The firewall is turned on by default and prevents access to these ports.</span></span> <span data-ttu-id="4c79a-108">Pokud chcete bránu firewall povolit pro ukázky, proveďte v závislosti na vašich požadavcích a prostředí zabezpečení jeden z následujících postupů:</span><span class="sxs-lookup"><span data-stu-id="4c79a-108">To enable the firewall for the samples, complete one of the following procedures, depending on your requirements and security environment:</span></span>

- <span data-ttu-id="4c79a-109">Možnost 1: interaktivní povolení vzorků při spuštění.</span><span class="sxs-lookup"><span data-stu-id="4c79a-109">Option 1: Interactively enable samples while running.</span></span> <span data-ttu-id="4c79a-110">Neprovádějte žádné změny konfigurace brány firewall a pokračujte v sestavování a spouštění ukázek.</span><span class="sxs-lookup"><span data-stu-id="4c79a-110">Make no advance changes to your firewall configuration and proceed to start building and running the samples.</span></span> <span data-ttu-id="4c79a-111">Při spuštění ukázky se zobrazí dialogové okno **Výstraha zabezpečení systému Windows** .</span><span class="sxs-lookup"><span data-stu-id="4c79a-111">When a sample is run, a **Windows Security Alert** dialog box appears.</span></span> <span data-ttu-id="4c79a-112">Daný vzorový program lze následně přidat interaktivně do odblokovaného seznamu.</span><span class="sxs-lookup"><span data-stu-id="4c79a-112">The sample program in question can then be added interactively to an unblocked list.</span></span> <span data-ttu-id="4c79a-113">Pomocí tohoto postupu bude pravděpodobně nutné znovu spustit ukázku.</span><span class="sxs-lookup"><span data-stu-id="4c79a-113">With this procedure, you may have to then restart the sample.</span></span>

- <span data-ttu-id="4c79a-114">Možnost 2: povolení předem ukázkových programů.</span><span class="sxs-lookup"><span data-stu-id="4c79a-114">Option 2: Enable sample programs in advance.</span></span> <span data-ttu-id="4c79a-115">Spusťte aplet **ovládacího panelu brány Windows Firewall** a povolte ukázkové programy, které chcete spustit.</span><span class="sxs-lookup"><span data-stu-id="4c79a-115">Start the **Windows Firewall Control Panel** applet and enable the sample programs you plan to run.</span></span> <span data-ttu-id="4c79a-116">Nejprve musíte vytvořit programy, aby existovaly spustitelné soubory.</span><span class="sxs-lookup"><span data-stu-id="4c79a-116">You must build the programs first so the executable files exist.</span></span> <span data-ttu-id="4c79a-117">Podrobnější pokyny najdete v následujícím postupu.</span><span class="sxs-lookup"><span data-stu-id="4c79a-117">You can find more detailed instructions in the following procedure.</span></span>

- <span data-ttu-id="4c79a-118">Možnost 3: Zapněte si rozsah portů předem.</span><span class="sxs-lookup"><span data-stu-id="4c79a-118">Option 3: Enable a port range in advance.</span></span> <span data-ttu-id="4c79a-119">Spusťte aplet **ovládacího panelu brány Windows Firewall** a povolte porty 80, 443, 8000-8003 a 9000, které jsou používány ukázkami.</span><span class="sxs-lookup"><span data-stu-id="4c79a-119">Start the **Windows Firewall Control Panel** applet and enable ports 80, 443, 8000-8003 and 9000, which are used by the samples.</span></span> <span data-ttu-id="4c79a-120">Podrobnější pokyny najdete v následujícím postupu.</span><span class="sxs-lookup"><span data-stu-id="4c79a-120">You can find more detailed instructions in the following procedure.</span></span> <span data-ttu-id="4c79a-121">Tato možnost je méně bezpečná než ostatní, protože umožňuje jakýmkoli programům používat tyto porty, nikoli jenom ukázky.</span><span class="sxs-lookup"><span data-stu-id="4c79a-121">This option is less secure than the others because it allows any program to use these ports, not just the samples.</span></span>

<span data-ttu-id="4c79a-122">Pokud si nejste jistí, který postup chcete použít, vyberte první možnost.</span><span class="sxs-lookup"><span data-stu-id="4c79a-122">If you are unsure of which procedure to use, choose the first option.</span></span> <span data-ttu-id="4c79a-123">Pokud používáte bránu firewall od jiného dodavatele, možná budete muset udělat podobné změny.</span><span class="sxs-lookup"><span data-stu-id="4c79a-123">If you are running a firewall from another vendor, you might need to make similar changes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4c79a-124">Změna konfigurace brány firewall má vliv na vaše zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4c79a-124">Changing your firewall configuration affects your security.</span></span> <span data-ttu-id="4c79a-125">Doporučujeme, abyste záznamy, které jste provedli, zaznamenali a odebrali je po dokončení práce s ukázkami.</span><span class="sxs-lookup"><span data-stu-id="4c79a-125">It is recommended that you record the changes you make and remove them when you are finished working with the samples.</span></span>

## <a name="enable-samples-programs-in-advance"></a><span data-ttu-id="4c79a-126">Povolit ukázkové programy předem</span><span class="sxs-lookup"><span data-stu-id="4c79a-126">Enable samples programs in advance</span></span>

1. <span data-ttu-id="4c79a-127">Sestavte ukázku.</span><span class="sxs-lookup"><span data-stu-id="4c79a-127">Build the sample.</span></span>

2. <span data-ttu-id="4c79a-128">Vyberte **Spustit**  >  **běh**a zadejte `firewall.cpl` .</span><span class="sxs-lookup"><span data-stu-id="4c79a-128">Choose **Start** > **Run**, and enter `firewall.cpl`.</span></span> <span data-ttu-id="4c79a-129">Tím se otevře aplet **ovládacího panelu brány Windows Firewall** .</span><span class="sxs-lookup"><span data-stu-id="4c79a-129">This opens the **Windows Firewall Control Panel** applet.</span></span>

    > [!NOTE]
    > <span data-ttu-id="4c79a-130">Abyste mohli spouštět ukázky, které vyžadují komunikaci přes bránu Windows Firewall, musíte mít oprávnění ke změně nastavení brány firewall.</span><span class="sxs-lookup"><span data-stu-id="4c79a-130">You must have permission to change the Firewall settings to run samples that require the ability to communicate through the Windows Firewall.</span></span> <span data-ttu-id="4c79a-131">Pokud některá nastavení brány firewall nejsou k dispozici a počítač je připojen k doméně, může správce systému řídit tato nastavení prostřednictvím Zásady skupiny.</span><span class="sxs-lookup"><span data-stu-id="4c79a-131">If some firewall settings are unavailable and your computer is connected to a domain, your system administrator might be controlling these settings through Group Policy.</span></span>

3. <span data-ttu-id="4c79a-132">Proveďte jeden z následujících kroků pro konkrétní operační systém, aby bylo možné program přes bránu Windows Firewall:</span><span class="sxs-lookup"><span data-stu-id="4c79a-132">Complete one of the following operating-specific steps to allow a program through the Windows Firewall:</span></span>

    - <span data-ttu-id="4c79a-133">V systému Windows 7 nebo Windows Server 2008 R2 klikněte na možnost **Povolení programu nebo funkce přes bránu Windows Firewall**.</span><span class="sxs-lookup"><span data-stu-id="4c79a-133">On Windows 7 or Windows Server 2008 R2, click **Allow a program or feature through Windows Firewall**.</span></span> <span data-ttu-id="4c79a-134">Klikněte na **změnit nastavení**  >  .**umožní vám jiný program**.</span><span class="sxs-lookup"><span data-stu-id="4c79a-134">Click **Change Settings** > **Allow Another Program**.</span></span>

    - <span data-ttu-id="4c79a-135">V systému Windows Vista nebo Windows Server 2008 klikněte na možnost **Povolení programu přes bránu Windows Firewall**.</span><span class="sxs-lookup"><span data-stu-id="4c79a-135">On Windows Vista or Windows Server 2008, click **Allow a program through Windows Firewall**.</span></span>

4. <span data-ttu-id="4c79a-136">Na kartě **výjimky** klikněte na **Přidat program**.</span><span class="sxs-lookup"><span data-stu-id="4c79a-136">On the **Exceptions** tab, click **Add Program**.</span></span>

5. <span data-ttu-id="4c79a-137">Klikněte na tlačítko **Procházet** a vyberte spustitelný soubor ukázkového plánu, který chcete spustit.</span><span class="sxs-lookup"><span data-stu-id="4c79a-137">Click the **Browse** button and select the executable file of the sample you plan to run.</span></span>

6. <span data-ttu-id="4c79a-138">Opakujte kroky 4 a 5, dokud nepřidáte spustitelné soubory všech ukázek, které máte v plánu spouštět.</span><span class="sxs-lookup"><span data-stu-id="4c79a-138">Repeat steps 4 and 5 until you have added the executable files of all the samples you plan to run.</span></span>

7. <span data-ttu-id="4c79a-139">Kliknutím na tlačítko **OK** zavřete aplet brány firewall.</span><span class="sxs-lookup"><span data-stu-id="4c79a-139">Click **OK** to close the firewall applet.</span></span>

## <a name="enable-a-port-range-in-advance"></a><span data-ttu-id="4c79a-140">Povolit rozsah portů předem</span><span class="sxs-lookup"><span data-stu-id="4c79a-140">Enable a port range in advance</span></span>

1. <span data-ttu-id="4c79a-141">Vyberte **Spustit**  >  **běh**a zadejte `firewall.cpl` .</span><span class="sxs-lookup"><span data-stu-id="4c79a-141">Choose **Start** > **Run**, and enter `firewall.cpl`.</span></span> <span data-ttu-id="4c79a-142">Tím se otevře aplet **ovládacího panelu brány Windows Firewall** .</span><span class="sxs-lookup"><span data-stu-id="4c79a-142">This opens the **Windows Firewall Control Panel** applet.</span></span>

2. <span data-ttu-id="4c79a-143">V systému Windows 7 nebo Windows Server 2008 R2 postupujte podle těchto kroků.</span><span class="sxs-lookup"><span data-stu-id="4c79a-143">On Windows 7 or Windows Server 2008 R2, follow these steps.</span></span>

    1. <span data-ttu-id="4c79a-144">V levém sloupci okna brány Windows Firewall klikněte na **Upřesnit nastavení** .</span><span class="sxs-lookup"><span data-stu-id="4c79a-144">Click **Advanced settings** in the left column of the Windows Firewall window.</span></span>

    2. <span data-ttu-id="4c79a-145">V levém sloupci klikněte na **příchozí pravidla** .</span><span class="sxs-lookup"><span data-stu-id="4c79a-145">Click **Inbound Rules** in the left column.</span></span>

    3. <span data-ttu-id="4c79a-146">Klikněte na **Nová pravidla** v pravém sloupci.</span><span class="sxs-lookup"><span data-stu-id="4c79a-146">Click **New Rules** in the right column.</span></span>

    4. <span data-ttu-id="4c79a-147">Vyberte **port** a klikněte na **Další**.</span><span class="sxs-lookup"><span data-stu-id="4c79a-147">Select **Port** and click **next**.</span></span>

    5. <span data-ttu-id="4c79a-148">Vyberte **TCP** a zadejte `8000, 8001, 8002, 8003, 9000, 80, 443` do pole **konkrétní místní porty** .</span><span class="sxs-lookup"><span data-stu-id="4c79a-148">Select **TCP** and enter `8000, 8001, 8002, 8003, 9000, 80, 443` in the **Specific local ports** field.</span></span>

    6. <span data-ttu-id="4c79a-149">Klikněte na **Další**.</span><span class="sxs-lookup"><span data-stu-id="4c79a-149">Click **Next**.</span></span>

    7. <span data-ttu-id="4c79a-150">Vyberte možnost **Povolení připojení**a klikněte na tlačítko **Další** .</span><span class="sxs-lookup"><span data-stu-id="4c79a-150">Select **Allow the connection**, and click **Next** .</span></span>

    8. <span data-ttu-id="4c79a-151">Vyberte **doména** a **privátní**a klikněte na **Další**.</span><span class="sxs-lookup"><span data-stu-id="4c79a-151">Select **Domain** and **Private**, and click **Next**.</span></span>

    9. <span data-ttu-id="4c79a-152">Pojmenujte toto pravidlo `WCF-WF 4.0 Samples` a klikněte na **Dokončit**.</span><span class="sxs-lookup"><span data-stu-id="4c79a-152">Name this rule `WCF-WF 4.0 Samples`, and click **Finish**.</span></span>

    10. <span data-ttu-id="4c79a-153">Klikněte na **odchozí pravidla** a opakujte kroky c až h.</span><span class="sxs-lookup"><span data-stu-id="4c79a-153">Click **Outbound Rules** and repeat steps c to h.</span></span>

3. <span data-ttu-id="4c79a-154">V systému Windows Vista nebo Windows Server 2008 postupujte podle těchto kroků.</span><span class="sxs-lookup"><span data-stu-id="4c79a-154">On Windows Vista or Windows Server 2008, follow these steps.</span></span>

    1. <span data-ttu-id="4c79a-155">Klikněte na možnost **Povolení programu přes bránu Windows Firewall**.</span><span class="sxs-lookup"><span data-stu-id="4c79a-155">Click **Allow a program through Windows Firewall**.</span></span>

    2. <span data-ttu-id="4c79a-156">Na kartě **výjimky** klikněte na **Přidat port**.</span><span class="sxs-lookup"><span data-stu-id="4c79a-156">On the **Exceptions** tab, click **Add Port**.</span></span>

    3. <span data-ttu-id="4c79a-157">Zadejte název, jako číslo portu zadejte 8000 a vyberte možnost **TCP** .</span><span class="sxs-lookup"><span data-stu-id="4c79a-157">Enter a name, enter 8000 as the port number, and select the **TCP** option.</span></span>

    4. <span data-ttu-id="4c79a-158">Klikněte na tlačítko **změnit obor** , vyberte možnost pouze **Moje síť** (podsíť) a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="4c79a-158">Click the **Change Scope** button, select the **My Network** (subnet) only option, and click **OK**.</span></span>

    5. <span data-ttu-id="4c79a-159">Opakujte kroky b až d pro porty 8001, 8002, 8003, 9000, 80 a 443.</span><span class="sxs-lookup"><span data-stu-id="4c79a-159">Repeat steps b to d for ports 8001, 8002, 8003, 9000, 80, and 443.</span></span>

4. <span data-ttu-id="4c79a-160">Kliknutím na tlačítko **OK** zavřete aplet brány firewall.</span><span class="sxs-lookup"><span data-stu-id="4c79a-160">Click **OK** to close the firewall applet.</span></span>

> [!NOTE]
> <span data-ttu-id="4c79a-161">Po dokončení práce s ukázkami odeberte všechny výjimky brány firewall.</span><span class="sxs-lookup"><span data-stu-id="4c79a-161">Remove any firewall exceptions when you are finished working with the samples.</span></span> <span data-ttu-id="4c79a-162">Provedete to tak, že otevřete aplet **ovládacího panelu brány Windows Firewall** a odeberete všechny programy nebo položky portů, které byly přidány předchozími postupy.</span><span class="sxs-lookup"><span data-stu-id="4c79a-162">To do so, open the **Windows Firewall Control Panel** applet and remove any programs or port entries that were added by the previous procedures.</span></span>
