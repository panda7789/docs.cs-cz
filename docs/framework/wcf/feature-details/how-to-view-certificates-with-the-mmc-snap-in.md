---
title: 'Postupy: Zobrazení certifikátů pomocí modulu snap-in konzoly MMC'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: 72fd6a1be2f33e1bfeb08fd43f3436627ee842e5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521579"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a><span data-ttu-id="79c7e-102">Postupy: Zobrazení certifikátů pomocí modulu snap-in konzoly MMC</span><span class="sxs-lookup"><span data-stu-id="79c7e-102">How to: View Certificates with the MMC Snap-in</span></span>
<span data-ttu-id="79c7e-103">Společný typ přihlašovacích údajů je certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="79c7e-103">A common type of credential is the X.509 certificate.</span></span> <span data-ttu-id="79c7e-104">Při vytváření zabezpečených služeb a klientů, můžete určit certifikát použít jako pověření klienta nebo služby pomocí metody, jako <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="79c7e-104">When creating secure services or clients, you can specify a certificate be used as the client or service credential by using methods such as the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method.</span></span> <span data-ttu-id="79c7e-105">Metoda vyžaduje různé parametry, jako jsou úložiště, kde je certifikát uložený a hodnoty pro použití při hledání certifikátu.</span><span class="sxs-lookup"><span data-stu-id="79c7e-105">The method requires various parameters, such as the store where the certificate is stored and a value to use when searching for the certificate.</span></span> <span data-ttu-id="79c7e-106">Následující postup ukazuje, jak prozkoumat úložišti v počítači se najít odpovídající certifikát.</span><span class="sxs-lookup"><span data-stu-id="79c7e-106">The following procedure demonstrates how to examine the stores on a computer to find an appropriate certificate.</span></span> <span data-ttu-id="79c7e-107">Příklad toho, jak najít kryptografický otisk certifikátu, naleznete v tématu [jak: Načtení kryptografického otisku certifikátu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="79c7e-107">For an example of finding the certificate thumbprint, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
### <a name="to-view-certificates-in-the-mmc-snap-in"></a><span data-ttu-id="79c7e-108">Chcete-li zobrazit certifikáty modulu snap-in konzoly MMC</span><span class="sxs-lookup"><span data-stu-id="79c7e-108">To view certificates in the MMC snap-in</span></span>  
  
1.  <span data-ttu-id="79c7e-109">Otevřete okno příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="79c7e-109">Open a Command Prompt window.</span></span>  
  
2.  <span data-ttu-id="79c7e-110">Typ `mmc` a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="79c7e-110">Type `mmc` and press the ENTER key.</span></span> <span data-ttu-id="79c7e-111">Všimněte si, že chcete zobrazit certifikáty v úložišti místního počítače, musí být v roli správce.</span><span class="sxs-lookup"><span data-stu-id="79c7e-111">Note that to view certificates in the local machine store, you must be in the Administrator role.</span></span>  
  
3.  <span data-ttu-id="79c7e-112">Na **souboru** nabídky, klikněte na tlačítko **přidat nebo odebrat modul snap-In**.</span><span class="sxs-lookup"><span data-stu-id="79c7e-112">On the **File** menu, click **Add/Remove Snap In**.</span></span>  
  
4.  <span data-ttu-id="79c7e-113">Klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="79c7e-113">Click **Add**.</span></span>  
  
5.  <span data-ttu-id="79c7e-114">V **přidat samostatný modul Snap-in** dialogu **certifikáty**.</span><span class="sxs-lookup"><span data-stu-id="79c7e-114">In the **Add Standalone Snap-in** dialog box, select **Certificates**.</span></span>  
  
6.  <span data-ttu-id="79c7e-115">Klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="79c7e-115">Click **Add**.</span></span>  
  
7.  <span data-ttu-id="79c7e-116">V **modul snap-in Certifikáty** dialogu **účet počítače** a klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="79c7e-116">In the **Certificates snap-in** dialog box, select **Computer account** and click **Next**.</span></span> <span data-ttu-id="79c7e-117">Volitelně můžete vybrat **tento uživatelský účet** nebo **účet služby**.</span><span class="sxs-lookup"><span data-stu-id="79c7e-117">Optionally, you can select **My User account** or **Service account**.</span></span> <span data-ttu-id="79c7e-118">Pokud nejste správcem tohoto počítače, můžete spravovat certifikáty jenom pro váš uživatelský účet.</span><span class="sxs-lookup"><span data-stu-id="79c7e-118">If you are not an administrator of the computer, you can manage certificates only for your user account.</span></span>  
  
8.  <span data-ttu-id="79c7e-119">V **vybrat počítač** dialogové okno, klikněte na tlačítko **Dokončit**.</span><span class="sxs-lookup"><span data-stu-id="79c7e-119">In the **Select Computer** dialog box, click **Finish**.</span></span>  
  
9. <span data-ttu-id="79c7e-120">V **přidat samostatný modul Snap-in** dialogové okno, klikněte na tlačítko **Zavřít**.</span><span class="sxs-lookup"><span data-stu-id="79c7e-120">In the **Add Standalone Snap-in** dialog box, click **Close**.</span></span>  
  
10. <span data-ttu-id="79c7e-121">Na **Přidat/odebrat modul Snap-in** dialogové okno, klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="79c7e-121">On the **Add/Remove Snap-in** dialog box, click **OK**.</span></span>  
  
11. <span data-ttu-id="79c7e-122">V **kořenový adresář konzoly** okna, klikněte na tlačítko **certifikáty (místní počítač)** zobrazíte certifikát uloží pro počítač.</span><span class="sxs-lookup"><span data-stu-id="79c7e-122">In the **Console Root** window, click **Certificates (Local Computer)** to view the certificate stores for the computer.</span></span>  
  
12. <span data-ttu-id="79c7e-123">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="79c7e-123">Optional.</span></span> <span data-ttu-id="79c7e-124">Pokud chcete zobrazit certifikáty pro váš účet, opakujte kroky 3 až 6.</span><span class="sxs-lookup"><span data-stu-id="79c7e-124">To view certificates for your account, repeat steps 3 to 6.</span></span> <span data-ttu-id="79c7e-125">V kroku 7, místo výběru **účet počítače**, klikněte na tlačítko **tento uživatelský účet** a opakujte kroky 8 až 10.</span><span class="sxs-lookup"><span data-stu-id="79c7e-125">In step 7, instead of selecting **Computer account**, click **My User account** and repeat steps 8 to 10.</span></span>  
  
13. <span data-ttu-id="79c7e-126">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="79c7e-126">Optional.</span></span> <span data-ttu-id="79c7e-127">Na **souboru** nabídky, klikněte na tlačítko **Uložit** nebo **uložit jako**.</span><span class="sxs-lookup"><span data-stu-id="79c7e-127">On the **File** menu, click **Save** or **Save As**.</span></span> <span data-ttu-id="79c7e-128">Uložte soubor konzoly pro pozdější použití.</span><span class="sxs-lookup"><span data-stu-id="79c7e-128">Save the console file for later reuse.</span></span>  
  
## <a name="viewing-certificates-with-internet-explorer"></a><span data-ttu-id="79c7e-129">Zobrazení certifikátů pomocí Internet Exploreru</span><span class="sxs-lookup"><span data-stu-id="79c7e-129">Viewing Certificates with Internet Explorer</span></span>  
 <span data-ttu-id="79c7e-130">Můžete také zobrazit, export, import a odstranit certifikáty pomocí aplikace Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="79c7e-130">You can also view, export, import, and delete certificates by using Internet Explorer.</span></span>  
  
#### <a name="to-view-certificates-with-internet-explorer"></a><span data-ttu-id="79c7e-131">K zobrazení certifikátů pomocí Internet Exploreru</span><span class="sxs-lookup"><span data-stu-id="79c7e-131">To view certificates with Internet Explorer</span></span>  
  
1.  <span data-ttu-id="79c7e-132">V aplikaci Internet Explorer, klikněte na tlačítko **nástroje**, pak klikněte na tlačítko **Možnosti Internetu** zobrazíte **Možnosti Internetu** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="79c7e-132">In Internet Explorer, click **Tools**, then click **Internet Options** to display the **Internet Options** dialog box.</span></span>  
  
2.  <span data-ttu-id="79c7e-133">Klikněte na tlačítko **obsahu** kartu.</span><span class="sxs-lookup"><span data-stu-id="79c7e-133">Click the **Content** tab.</span></span>  
  
3.  <span data-ttu-id="79c7e-134">V části **certifikáty**, klikněte na tlačítko **certifikáty**.</span><span class="sxs-lookup"><span data-stu-id="79c7e-134">Under **Certificates**, click **Certificates**.</span></span>  
  
4.  <span data-ttu-id="79c7e-135">Chcete-li zobrazit podrobnosti o některý z certifikátů, vyberte certifikát a klikněte na tlačítko **zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="79c7e-135">To view details of any certificate, select the certificate and click **View**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79c7e-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="79c7e-136">See also</span></span>
- [<span data-ttu-id="79c7e-137">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="79c7e-137">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="79c7e-138">Postupy: Vytváření dočasných certifikátů pro použití během vývoje.</span><span class="sxs-lookup"><span data-stu-id="79c7e-138">How to: Create Temporary Certificates for Use During Development</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
- [<span data-ttu-id="79c7e-139">Postupy: Načtení kryptografického otisku certifikátu</span><span class="sxs-lookup"><span data-stu-id="79c7e-139">How to: Retrieve the Thumbprint of a Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
