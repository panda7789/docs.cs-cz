---
title: 'Postupy: Zobrazení certifikátů pomocí modulu snap-in konzoly MMC'
ms.date: 02/25/2019
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: 6ec86ffca9ae84a9c3276a3dd6de676919dcd2e0
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/01/2019
ms.locfileid: "57200283"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a><span data-ttu-id="110c6-102">Postupy: Zobrazení certifikátů pomocí modulu snap-in konzoly MMC</span><span class="sxs-lookup"><span data-stu-id="110c6-102">How to: View certificates with the MMC snap-in</span></span>
<span data-ttu-id="110c6-103">Při vytváření zabezpečeného klienta nebo služby, můžete použít [certifikát](working-with-certificates.md) jako přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="110c6-103">When you create a secure client or service, you can use a [certificate](working-with-certificates.md) as the credential.</span></span> <span data-ttu-id="110c6-104">Například běžný typ přihlašovacích údajů je certifikát X.509, který vytvoříte pomocí <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="110c6-104">For example, a common type of credential is the X.509 certificate, which you create with the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> method.</span></span> 

<span data-ttu-id="110c6-105">Existují tři různé typy úložišť certifikátů, které můžete zkontrolovat pomocí Microsoft Management Console (MMC) v systémech Windows:</span><span class="sxs-lookup"><span data-stu-id="110c6-105">There are three different types of certificate stores that you can examine with the Microsoft Management Console (MMC) on Windows systems:</span></span>

- <span data-ttu-id="110c6-106">Místní počítač: Úložiště je místní pro zařízení a globální pro všechny uživatele v zařízení.</span><span class="sxs-lookup"><span data-stu-id="110c6-106">Local computer: The store is local to the device and global to all users on the device.</span></span>

- <span data-ttu-id="110c6-107">Aktuální uživatel: Úložiště je místní pro aktuální uživatelský účet v zařízení.</span><span class="sxs-lookup"><span data-stu-id="110c6-107">Current user: The store is local to the current user account on the device.</span></span>

- <span data-ttu-id="110c6-108">Účet služby: Úložiště je místní pro konkrétní službu na zařízení.</span><span class="sxs-lookup"><span data-stu-id="110c6-108">Service account: The store is local to a particular service on the device.</span></span>

  
## <a name="view-certificates-in-the-mmc-snap-in"></a><span data-ttu-id="110c6-109">Zobrazit certifikáty modulu snap-in konzoly MMC</span><span class="sxs-lookup"><span data-stu-id="110c6-109">View certificates in the MMC snap-in</span></span> 

<span data-ttu-id="110c6-110">Následující postup ukazuje, jak prozkoumat úložišť na vaše místní zařízení najít odpovídající certifikát:</span><span class="sxs-lookup"><span data-stu-id="110c6-110">The following procedure demonstrates how to examine the stores on your local device to find an appropriate certificate:</span></span> 
  
1. <span data-ttu-id="110c6-111">Vyberte **spustit** z **Start** nabídky a pak zadejte *konzoly mmc*.</span><span class="sxs-lookup"><span data-stu-id="110c6-111">Select **Run** from the **Start** menu, and then enter *mmc*.</span></span> 

    <span data-ttu-id="110c6-112">Otevře se konzole MMC.</span><span class="sxs-lookup"><span data-stu-id="110c6-112">The MMC appears.</span></span> 
  
2. <span data-ttu-id="110c6-113">Z **souboru** nabídce vyberte možnost **přidat nebo odebrat modul snap-In**.</span><span class="sxs-lookup"><span data-stu-id="110c6-113">From the **File** menu, select **Add/Remove Snap In**.</span></span> 
    
    <span data-ttu-id="110c6-114">**Přidat nebo odebrat moduly Snap in** zobrazí se okno.</span><span class="sxs-lookup"><span data-stu-id="110c6-114">The **Add or Remove Snap-ins** window appears.</span></span>
  
3. <span data-ttu-id="110c6-115">Z **modul snap in k dispozici** klikněte na položku **certifikáty**a pak vyberte **přidat**.</span><span class="sxs-lookup"><span data-stu-id="110c6-115">From the **Available snap-ins** list, choose **Certificates**, then select **Add**.</span></span>  

    ![Přidat modul snap-in certifikátů](./media/mmc-add-certificate-snap-in.png)
  
4. <span data-ttu-id="110c6-117">V **modul snap-in Certifikáty** okně **účet počítače**a pak vyberte **Další**.</span><span class="sxs-lookup"><span data-stu-id="110c6-117">In the **Certificates snap-in** window, select **Computer account**, and then select **Next**.</span></span> 
  
    <span data-ttu-id="110c6-118">Volitelně můžete vybrat **Můj uživatelský účet** pro aktuálního uživatele nebo **účet služby** pro konkrétní službu.</span><span class="sxs-lookup"><span data-stu-id="110c6-118">Optionally, you can select **My user account** for the current user or **Service account** for a particular service.</span></span> 

    > [!NOTE]
    > <span data-ttu-id="110c6-119">Pokud si nejste správce pro vaše zařízení, můžete spravovat certifikáty jenom pro váš uživatelský účet.</span><span class="sxs-lookup"><span data-stu-id="110c6-119">If you're not an administrator for your device, you can manage certificates only for your user account.</span></span>
  
5. <span data-ttu-id="110c6-120">V **vybrat počítač** okně, ponechejte tuto položku **místního počítače** vybrali a pak vyberte **Dokončit**.</span><span class="sxs-lookup"><span data-stu-id="110c6-120">In the **Select Computer** window, leave **Local computer** selected, and then select **Finish**.</span></span>  
  
6. <span data-ttu-id="110c6-121">V **přidat nebo odebrat modul Snap-in** okně **OK**.</span><span class="sxs-lookup"><span data-stu-id="110c6-121">In the **Add or Remove Snap-in** window, select **OK**.</span></span>  
  
    ![Přidat modul snap-in certifikátů](./media/mmc-certificate-snap-in-selected.png)

7. <span data-ttu-id="110c6-123">Volitelné: Z **souboru** nabídce vyberte možnost **Uložit** nebo **uložit jako** uložit soubor konzoly MMC pro pozdější použití.</span><span class="sxs-lookup"><span data-stu-id="110c6-123">Optional: From the **File** menu, select **Save** or **Save As** to save the MMC console file for later use.</span></span>  

8. <span data-ttu-id="110c6-124">Chcete-li zobrazit vaše certifikáty modulu snap-in konzoly MMC, vyberte **kořenový adresář konzoly** v levém podokně, potom rozbalte **certifikáty (místní počítač)**.</span><span class="sxs-lookup"><span data-stu-id="110c6-124">To view your certificates in the MMC snap-in, select **Console Root** in the left pane, then expand **Certificates (Local Computer)**.</span></span>

    <span data-ttu-id="110c6-125">Zobrazí se seznam adresářů pro každý typ certifikátu.</span><span class="sxs-lookup"><span data-stu-id="110c6-125">A list of directories for each type of certificate appears.</span></span> <span data-ttu-id="110c6-126">Každý certifikát adresáře můžete zobrazit, export, import a odstranit certifikáty pro jeho.</span><span class="sxs-lookup"><span data-stu-id="110c6-126">From each certificate directory, you can view, export, import, and delete its certificates.</span></span>
  

## <a name="view-certificates-with-the-certificate-manager-tool"></a><span data-ttu-id="110c6-127">Zobrazení certifikátů pomocí nástroje Správce certifikátů</span><span class="sxs-lookup"><span data-stu-id="110c6-127">View certificates with the Certificate Manager tool</span></span>

<span data-ttu-id="110c6-128">Můžete také zobrazit, export, import a odstranit certifikáty pomocí nástroje Správce certifikátů.</span><span class="sxs-lookup"><span data-stu-id="110c6-128">You can also view, export, import, and delete certificates by using the Certificate Manager tool.</span></span>

### <a name="to-view-certificates-for-the-local-device"></a><span data-ttu-id="110c6-129">Chcete-li zobrazit certifikáty pro místní zařízení</span><span class="sxs-lookup"><span data-stu-id="110c6-129">To view certificates for the local device</span></span>

1. <span data-ttu-id="110c6-130">Vyberte **spustit** z **Start** nabídky a pak zadejte *certlm.msc*.</span><span class="sxs-lookup"><span data-stu-id="110c6-130">Select **Run** from the **Start** menu, and then enter *certlm.msc*.</span></span> 

    <span data-ttu-id="110c6-131">Zobrazí se nástroj Správce certifikátů pro místní zařízení.</span><span class="sxs-lookup"><span data-stu-id="110c6-131">The Certificate Manager tool for the local device appears.</span></span> 
  
2. <span data-ttu-id="110c6-132">Chcete-li zobrazit certifikáty, v části **certifikáty - místní počítač** v levém podokně rozbalte adresář pro typ certifikátu, kterou chcete zobrazit.</span><span class="sxs-lookup"><span data-stu-id="110c6-132">To view your certificates, under **Certificates - Local Computer** in the left pane, expand the directory for the type of certificate you want to view.</span></span>

### <a name="to-view-certificates-for-the-current-user"></a><span data-ttu-id="110c6-133">Chcete-li zobrazit certifikáty pro aktuálního uživatele</span><span class="sxs-lookup"><span data-stu-id="110c6-133">To view certificates for the current user</span></span>

1. <span data-ttu-id="110c6-134">Vyberte **spustit** z **Start** nabídky a pak zadejte *certmgr.msc*.</span><span class="sxs-lookup"><span data-stu-id="110c6-134">Select **Run** from the **Start** menu, and then enter *certmgr.msc*.</span></span> 

    <span data-ttu-id="110c6-135">Zobrazí se nástroj Certificate Manager pro aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="110c6-135">The Certificate Manager tool for the current user appears.</span></span> 
  
2. <span data-ttu-id="110c6-136">Chcete-li zobrazit certifikáty, v části **certifikáty – aktuální uživatel** v levém podokně rozbalte adresář pro typ certifikátu, kterou chcete zobrazit.</span><span class="sxs-lookup"><span data-stu-id="110c6-136">To view your certificates, under **Certificates - Current User** in the left pane, expand the directory for the type of certificate you want to view.</span></span>

  
## <a name="see-also"></a><span data-ttu-id="110c6-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="110c6-137">See also</span></span>
- [<span data-ttu-id="110c6-138">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="110c6-138">Working with certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="110c6-139">Postupy: Vytváření dočasných certifikátů pro použití během vývoje.</span><span class="sxs-lookup"><span data-stu-id="110c6-139">How to: Create temporary certificates for use during development</span></span>](how-to-create-temporary-certificates-for-use-during-development.md)
- [<span data-ttu-id="110c6-140">Postupy: Načtení kryptografického otisku certifikátu</span><span class="sxs-lookup"><span data-stu-id="110c6-140">How to: Retrieve the thumbprint of a certificate</span></span>](how-to-retrieve-the-thumbprint-of-a-certificate.md)
