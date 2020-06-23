---
title: 'Postupy: zobrazení certifikátů pomocí modulu snap-in konzoly MMC'
description: Zabezpečený klient nebo služba WCF může použít certifikát jako přihlašovací údaje. Seznamte se s typy úložišť certifikátů, které můžete prozkoumávat pomocí modulu plug-in konzoly MMC.
ms.date: 02/25/2019
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: e63034e48ae836f67f89b454829f7196c94610cd
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246672"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a><span data-ttu-id="27fc9-104">Postupy: zobrazení certifikátů pomocí modulu snap-in konzoly MMC</span><span class="sxs-lookup"><span data-stu-id="27fc9-104">How to: View certificates with the MMC snap-in</span></span>
<span data-ttu-id="27fc9-105">Když vytváříte zabezpečeného klienta nebo službu, můžete jako přihlašovací údaje použít [certifikát](working-with-certificates.md) .</span><span class="sxs-lookup"><span data-stu-id="27fc9-105">When you create a secure client or service, you can use a [certificate](working-with-certificates.md) as the credential.</span></span> <span data-ttu-id="27fc9-106">Například běžným typem přihlašovacích údajů je certifikát X. 509, který vytvoříte pomocí <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="27fc9-106">For example, a common type of credential is the X.509 certificate, which you create with the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="27fc9-107">Existují tři různé typy úložišť certifikátů, které můžete prozkoumávat pomocí konzoly MMC (Microsoft Management Console) v systémech Windows:</span><span class="sxs-lookup"><span data-stu-id="27fc9-107">There are three different types of certificate stores that you can examine with the Microsoft Management Console (MMC) on Windows systems:</span></span>

- <span data-ttu-id="27fc9-108">Místní počítač: úložiště je místní pro zařízení a globální pro všechny uživatele v zařízení.</span><span class="sxs-lookup"><span data-stu-id="27fc9-108">Local computer: The store is local to the device and global to all users on the device.</span></span>

- <span data-ttu-id="27fc9-109">Aktuální uživatel: úložiště je místní k aktuálnímu uživatelskému účtu v zařízení.</span><span class="sxs-lookup"><span data-stu-id="27fc9-109">Current user: The store is local to the current user account on the device.</span></span>

- <span data-ttu-id="27fc9-110">Účet služby: úložiště je místní pro určitou službu na zařízení.</span><span class="sxs-lookup"><span data-stu-id="27fc9-110">Service account: The store is local to a particular service on the device.</span></span>

## <a name="view-certificates-in-the-mmc-snap-in"></a><span data-ttu-id="27fc9-111">Zobrazení certifikátů v modulu snap-in konzoly MMC</span><span class="sxs-lookup"><span data-stu-id="27fc9-111">View certificates in the MMC snap-in</span></span>

<span data-ttu-id="27fc9-112">Následující postup ukazuje, jak ověřit obchody na místním zařízení a najít odpovídající certifikát:</span><span class="sxs-lookup"><span data-stu-id="27fc9-112">The following procedure demonstrates how to examine the stores on your local device to find an appropriate certificate:</span></span>
  
1. <span data-ttu-id="27fc9-113">V nabídce **Start** vyberte **Run (spustit** ) a pak zadejte *MMC*.</span><span class="sxs-lookup"><span data-stu-id="27fc9-113">Select **Run** from the **Start** menu, and then enter *mmc*.</span></span>

    <span data-ttu-id="27fc9-114">Zobrazí se konzola MMC.</span><span class="sxs-lookup"><span data-stu-id="27fc9-114">The MMC appears.</span></span>
  
2. <span data-ttu-id="27fc9-115">V nabídce **soubor** vyberte **Přidat nebo odebrat modul snap in**.</span><span class="sxs-lookup"><span data-stu-id="27fc9-115">From the **File** menu, select **Add/Remove Snap In**.</span></span>

    <span data-ttu-id="27fc9-116">Zobrazí se okno **Přidat nebo odebrat moduly snap-in** .</span><span class="sxs-lookup"><span data-stu-id="27fc9-116">The **Add or Remove Snap-ins** window appears.</span></span>
  
3. <span data-ttu-id="27fc9-117">V seznamu **dostupné moduly snap-in** vyberte **certifikáty**a pak **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="27fc9-117">From the **Available snap-ins** list, choose **Certificates**, then select **Add**.</span></span>  

    ![Přidat modul snap-in certifikátů](./media/mmc-add-certificate-snap-in.png)
  
4. <span data-ttu-id="27fc9-119">V okně **modulu snap-in Certifikáty** vyberte možnost **účet počítače**a potom vyberte možnost **Další**.</span><span class="sxs-lookup"><span data-stu-id="27fc9-119">In the **Certificates snap-in** window, select **Computer account**, and then select **Next**.</span></span>
  
    <span data-ttu-id="27fc9-120">Volitelně můžete vybrat možnost **Můj uživatelský účet** pro aktuálního uživatele nebo **účet služby** pro konkrétní službu.</span><span class="sxs-lookup"><span data-stu-id="27fc9-120">Optionally, you can select **My user account** for the current user or **Service account** for a particular service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="27fc9-121">Pokud nejste správcem vašeho zařízení, můžete spravovat certifikáty jenom pro svůj uživatelský účet.</span><span class="sxs-lookup"><span data-stu-id="27fc9-121">If you're not an administrator for your device, you can manage certificates only for your user account.</span></span>
  
5. <span data-ttu-id="27fc9-122">V okně **Vybrat počítač** ponechte vybraný **místní počítač** a pak vyberte **Dokončit**.</span><span class="sxs-lookup"><span data-stu-id="27fc9-122">In the **Select Computer** window, leave **Local computer** selected, and then select **Finish**.</span></span>  
  
6. <span data-ttu-id="27fc9-123">V okně **Přidat nebo odebrat modul snap-in** vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="27fc9-123">In the **Add or Remove Snap-in** window, select **OK**.</span></span>  
  
    ![Přidat modul snap-in certifikátů](./media/mmc-certificate-snap-in-selected.png)

7. <span data-ttu-id="27fc9-125">Volitelné: v nabídce **soubor** vyberte **Uložit** nebo **Uložit jako** a uložte soubor konzoly MMC pro pozdější použití.</span><span class="sxs-lookup"><span data-stu-id="27fc9-125">Optional: From the **File** menu, select **Save** or **Save As** to save the MMC console file for later use.</span></span>  

8. <span data-ttu-id="27fc9-126">Chcete-li zobrazit certifikáty v modulu snap-in konzoly MMC, vyberte v levém podokně **kořenový adresář konzoly** a potom rozbalte položku **certifikáty (místní počítač)**.</span><span class="sxs-lookup"><span data-stu-id="27fc9-126">To view your certificates in the MMC snap-in, select **Console Root** in the left pane, then expand **Certificates (Local Computer)**.</span></span>

    <span data-ttu-id="27fc9-127">Zobrazí se seznam adresářů pro každý typ certifikátu.</span><span class="sxs-lookup"><span data-stu-id="27fc9-127">A list of directories for each type of certificate appears.</span></span> <span data-ttu-id="27fc9-128">Z každého adresáře certifikátu můžete zobrazit, exportovat, importovat a odstranit jeho certifikáty.</span><span class="sxs-lookup"><span data-stu-id="27fc9-128">From each certificate directory, you can view, export, import, and delete its certificates.</span></span>

## <a name="view-certificates-with-the-certificate-manager-tool"></a><span data-ttu-id="27fc9-129">Zobrazení certifikátů pomocí nástroje Správce certifikátů</span><span class="sxs-lookup"><span data-stu-id="27fc9-129">View certificates with the Certificate Manager tool</span></span>

<span data-ttu-id="27fc9-130">Pomocí nástroje Správce certifikátů můžete také zobrazit, exportovat, importovat a odstranit certifikáty.</span><span class="sxs-lookup"><span data-stu-id="27fc9-130">You can also view, export, import, and delete certificates by using the Certificate Manager tool.</span></span>

### <a name="to-view-certificates-for-the-local-device"></a><span data-ttu-id="27fc9-131">Zobrazení certifikátů pro místní zařízení</span><span class="sxs-lookup"><span data-stu-id="27fc9-131">To view certificates for the local device</span></span>

1. <span data-ttu-id="27fc9-132">V nabídce **Start** vyberte **Run (spustit** ) a pak zadejte *Certlm. msc*.</span><span class="sxs-lookup"><span data-stu-id="27fc9-132">Select **Run** from the **Start** menu, and then enter *certlm.msc*.</span></span>

    <span data-ttu-id="27fc9-133">Zobrazí se nástroj Správce certifikátů pro místní zařízení.</span><span class="sxs-lookup"><span data-stu-id="27fc9-133">The Certificate Manager tool for the local device appears.</span></span>
  
2. <span data-ttu-id="27fc9-134">Certifikáty zobrazíte tak, že v části **certifikáty – místní počítač** v levém podokně rozbalíte adresář pro typ certifikátu, který chcete zobrazit.</span><span class="sxs-lookup"><span data-stu-id="27fc9-134">To view your certificates, under **Certificates - Local Computer** in the left pane, expand the directory for the type of certificate you want to view.</span></span>

### <a name="to-view-certificates-for-the-current-user"></a><span data-ttu-id="27fc9-135">Zobrazení certifikátů pro aktuálního uživatele</span><span class="sxs-lookup"><span data-stu-id="27fc9-135">To view certificates for the current user</span></span>

1. <span data-ttu-id="27fc9-136">V nabídce **Start** vyberte **Run (spustit** ) a pak zadejte *certmgr. msc*.</span><span class="sxs-lookup"><span data-stu-id="27fc9-136">Select **Run** from the **Start** menu, and then enter *certmgr.msc*.</span></span>

    <span data-ttu-id="27fc9-137">Zobrazí se nástroj Správce certifikátů pro aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="27fc9-137">The Certificate Manager tool for the current user appears.</span></span>
  
2. <span data-ttu-id="27fc9-138">Chcete-li zobrazit certifikáty, v části **Certifikáty – aktuální uživatel** v levém podokně rozbalte adresář pro typ certifikátu, který chcete zobrazit.</span><span class="sxs-lookup"><span data-stu-id="27fc9-138">To view your certificates, under **Certificates - Current User** in the left pane, expand the directory for the type of certificate you want to view.</span></span>

## <a name="see-also"></a><span data-ttu-id="27fc9-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="27fc9-139">See also</span></span>

- [<span data-ttu-id="27fc9-140">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="27fc9-140">Working with certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="27fc9-141">Postupy: vytváření dočasných certifikátů pro použití během vývoje</span><span class="sxs-lookup"><span data-stu-id="27fc9-141">How to: Create temporary certificates for use during development</span></span>](how-to-create-temporary-certificates-for-use-during-development.md)
- [<span data-ttu-id="27fc9-142">Postupy: Načtení kryptografického otisku certifikátu</span><span class="sxs-lookup"><span data-stu-id="27fc9-142">How to: Retrieve the thumbprint of a certificate</span></span>](how-to-retrieve-the-thumbprint-of-a-certificate.md)
