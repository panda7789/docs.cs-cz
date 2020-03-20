---
title: 'Postup: Zobrazení certifikátů pomocí modulu snap-in Konzoly MMC'
ms.date: 02/25/2019
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: 35048c24e838c513909fae8bedcba287001f5cef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184787"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a><span data-ttu-id="44159-102">Postup: Zobrazení certifikátů pomocí modulu snap-in Konzoly MMC</span><span class="sxs-lookup"><span data-stu-id="44159-102">How to: View certificates with the MMC snap-in</span></span>
<span data-ttu-id="44159-103">Při vytváření zabezpečeného klienta nebo služby můžete jako pověření použít [certifikát.](working-with-certificates.md)</span><span class="sxs-lookup"><span data-stu-id="44159-103">When you create a secure client or service, you can use a [certificate](working-with-certificates.md) as the credential.</span></span> <span data-ttu-id="44159-104">Běžným typem pověření je například certifikát X.509, <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> který vytvoříte pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="44159-104">For example, a common type of credential is the X.509 certificate, which you create with the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="44159-105">Existují tři různé typy úložišť certifikátů, které můžete prozkoumat pomocí konzoly MMC (MMC) v systémech Windows:</span><span class="sxs-lookup"><span data-stu-id="44159-105">There are three different types of certificate stores that you can examine with the Microsoft Management Console (MMC) on Windows systems:</span></span>

- <span data-ttu-id="44159-106">Místní počítač: Úložiště je místní pro zařízení a globální pro všechny uživatele v zařízení.</span><span class="sxs-lookup"><span data-stu-id="44159-106">Local computer: The store is local to the device and global to all users on the device.</span></span>

- <span data-ttu-id="44159-107">Aktuální uživatel: Úložiště je místní aktuální uživatelský účet v zařízení.</span><span class="sxs-lookup"><span data-stu-id="44159-107">Current user: The store is local to the current user account on the device.</span></span>

- <span data-ttu-id="44159-108">Účet služby: Úložiště je místní pro konkrétní službu v zařízení.</span><span class="sxs-lookup"><span data-stu-id="44159-108">Service account: The store is local to a particular service on the device.</span></span>

## <a name="view-certificates-in-the-mmc-snap-in"></a><span data-ttu-id="44159-109">Zobrazení certifikátů v modulu snap-in konzoly MMC</span><span class="sxs-lookup"><span data-stu-id="44159-109">View certificates in the MMC snap-in</span></span>

<span data-ttu-id="44159-110">Následující postup ukazuje, jak zkontrolovat obchody v místním zařízení najít odpovídající certifikát:</span><span class="sxs-lookup"><span data-stu-id="44159-110">The following procedure demonstrates how to examine the stores on your local device to find an appropriate certificate:</span></span>
  
1. <span data-ttu-id="44159-111">Z nabídky **Start** vyberte **Spustit** a zadejte *konzolu MMC*.</span><span class="sxs-lookup"><span data-stu-id="44159-111">Select **Run** from the **Start** menu, and then enter *mmc*.</span></span>

    <span data-ttu-id="44159-112">Zobrazí se konzola MMC.</span><span class="sxs-lookup"><span data-stu-id="44159-112">The MMC appears.</span></span>
  
2. <span data-ttu-id="44159-113">V nabídce **Soubor** vyberte **Přidat nebo odebrat přichycení**.</span><span class="sxs-lookup"><span data-stu-id="44159-113">From the **File** menu, select **Add/Remove Snap In**.</span></span>

    <span data-ttu-id="44159-114">Zobrazí se okno **Přidat nebo odebrat moduly snap-in.**</span><span class="sxs-lookup"><span data-stu-id="44159-114">The **Add or Remove Snap-ins** window appears.</span></span>
  
3. <span data-ttu-id="44159-115">V seznamu **Dostupné moduly snap-in** zvolte **Certifikáty**a pak vyberte **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="44159-115">From the **Available snap-ins** list, choose **Certificates**, then select **Add**.</span></span>  

    ![Přidání modulu snap-in certifikátu](./media/mmc-add-certificate-snap-in.png)
  
4. <span data-ttu-id="44159-117">V okně **modulu snap-in Certifikáty** vyberte **Účet počítače**a pak vyberte **Další**.</span><span class="sxs-lookup"><span data-stu-id="44159-117">In the **Certificates snap-in** window, select **Computer account**, and then select **Next**.</span></span>
  
    <span data-ttu-id="44159-118">Volitelně můžete vybrat **můj uživatelský účet** pro aktuální uživatelský účet nebo účet **služby** pro konkrétní službu.</span><span class="sxs-lookup"><span data-stu-id="44159-118">Optionally, you can select **My user account** for the current user or **Service account** for a particular service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="44159-119">Pokud nejste správcem zařízení, můžete spravovat certifikáty pouze pro svůj uživatelský účet.</span><span class="sxs-lookup"><span data-stu-id="44159-119">If you're not an administrator for your device, you can manage certificates only for your user account.</span></span>
  
5. <span data-ttu-id="44159-120">V okně **Vybrat počítač** ponechejte vybrat **místní počítač** a pak vyberte **Dokončit**.</span><span class="sxs-lookup"><span data-stu-id="44159-120">In the **Select Computer** window, leave **Local computer** selected, and then select **Finish**.</span></span>  
  
6. <span data-ttu-id="44159-121">V okně **Přidat nebo odebrat modul snap-in** vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="44159-121">In the **Add or Remove Snap-in** window, select **OK**.</span></span>  
  
    ![Přidání modulu snap-in certifikátu](./media/mmc-certificate-snap-in-selected.png)

7. <span data-ttu-id="44159-123">Volitelné: V nabídce **Soubor** vyberte **Uložit** nebo **Uložit jako,** chcete-li soubor konzoly MMC uložit pro pozdější použití.</span><span class="sxs-lookup"><span data-stu-id="44159-123">Optional: From the **File** menu, select **Save** or **Save As** to save the MMC console file for later use.</span></span>  

8. <span data-ttu-id="44159-124">Chcete-li zobrazit certifikáty v modulu snap-in konzoly MMC, vyberte v levém podokně **položku Kořenová konzola** a potom rozbalte **položku Certifikáty (místní počítač).**</span><span class="sxs-lookup"><span data-stu-id="44159-124">To view your certificates in the MMC snap-in, select **Console Root** in the left pane, then expand **Certificates (Local Computer)**.</span></span>

    <span data-ttu-id="44159-125">Zobrazí se seznam adresářů pro každý typ certifikátu.</span><span class="sxs-lookup"><span data-stu-id="44159-125">A list of directories for each type of certificate appears.</span></span> <span data-ttu-id="44159-126">V každém adresáři certifikátů můžete jeho certifikáty zobrazit, exportovat, importovat a odstranit.</span><span class="sxs-lookup"><span data-stu-id="44159-126">From each certificate directory, you can view, export, import, and delete its certificates.</span></span>

## <a name="view-certificates-with-the-certificate-manager-tool"></a><span data-ttu-id="44159-127">Zobrazení certifikátů pomocí nástroje Správce certifikátů</span><span class="sxs-lookup"><span data-stu-id="44159-127">View certificates with the Certificate Manager tool</span></span>

<span data-ttu-id="44159-128">Certifikáty můžete také zobrazit, exportovat, importovat a odstraňovat pomocí nástroje Správce certifikátů.</span><span class="sxs-lookup"><span data-stu-id="44159-128">You can also view, export, import, and delete certificates by using the Certificate Manager tool.</span></span>

### <a name="to-view-certificates-for-the-local-device"></a><span data-ttu-id="44159-129">Zobrazení certifikátů pro místní zařízení</span><span class="sxs-lookup"><span data-stu-id="44159-129">To view certificates for the local device</span></span>

1. <span data-ttu-id="44159-130">Z nabídky **Start** vyberte **Spustit** a zadejte *certlm.msc*.</span><span class="sxs-lookup"><span data-stu-id="44159-130">Select **Run** from the **Start** menu, and then enter *certlm.msc*.</span></span>

    <span data-ttu-id="44159-131">Zobrazí se nástroj Správce certifikátů pro místní zařízení.</span><span class="sxs-lookup"><span data-stu-id="44159-131">The Certificate Manager tool for the local device appears.</span></span>
  
2. <span data-ttu-id="44159-132">Chcete-li zobrazit certifikáty, rozbalte v levém podokně v části **Certifikáty – místní počítač** adresář pro typ certifikátu, který chcete zobrazit.</span><span class="sxs-lookup"><span data-stu-id="44159-132">To view your certificates, under **Certificates - Local Computer** in the left pane, expand the directory for the type of certificate you want to view.</span></span>

### <a name="to-view-certificates-for-the-current-user"></a><span data-ttu-id="44159-133">Zobrazení certifikátů pro aktuálního uživatele</span><span class="sxs-lookup"><span data-stu-id="44159-133">To view certificates for the current user</span></span>

1. <span data-ttu-id="44159-134">Z nabídky **Start** vyberte **Spustit** a zadejte *certmgr.msc*.</span><span class="sxs-lookup"><span data-stu-id="44159-134">Select **Run** from the **Start** menu, and then enter *certmgr.msc*.</span></span>

    <span data-ttu-id="44159-135">Zobrazí se nástroj Správce certifikátů pro aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="44159-135">The Certificate Manager tool for the current user appears.</span></span>
  
2. <span data-ttu-id="44159-136">Chcete-li zobrazit certifikáty, rozbalte v části **Certifikáty - Aktuální uživatel** v levém podokně adresář pro typ certifikátu, který chcete zobrazit.</span><span class="sxs-lookup"><span data-stu-id="44159-136">To view your certificates, under **Certificates - Current User** in the left pane, expand the directory for the type of certificate you want to view.</span></span>

## <a name="see-also"></a><span data-ttu-id="44159-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="44159-137">See also</span></span>

- [<span data-ttu-id="44159-138">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="44159-138">Working with certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="44159-139">Postup: Vytvoření dočasných certifikátů pro použití během vývoje</span><span class="sxs-lookup"><span data-stu-id="44159-139">How to: Create temporary certificates for use during development</span></span>](how-to-create-temporary-certificates-for-use-during-development.md)
- [<span data-ttu-id="44159-140">Postup: Načtení kryptografického otisku certifikátu</span><span class="sxs-lookup"><span data-stu-id="44159-140">How to: Retrieve the thumbprint of a certificate</span></span>](how-to-retrieve-the-thumbprint-of-a-certificate.md)
