---
title: "Postupy: Zobrazení certifikátů pomocí modulu snap-in konzoly MMC"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 582eaef518e10acb4c4c356226ce0be24d1b4c35
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a><span data-ttu-id="e9743-102">Postupy: Zobrazení certifikátů pomocí modulu snap-in konzoly MMC</span><span class="sxs-lookup"><span data-stu-id="e9743-102">How to: View Certificates with the MMC Snap-in</span></span>
<span data-ttu-id="e9743-103">Běžný typ přihlašovacích údajů je certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="e9743-103">A common type of credential is the X.509 certificate.</span></span> <span data-ttu-id="e9743-104">Při vytváření zabezpečené služby nebo klientů, můžete zadat, certifikát se dá použít jako pověření klienta služby nebo pomocí metody, jako <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="e9743-104">When creating secure services or clients, you can specify a certificate be used as the client or service credential by using methods such as the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method.</span></span> <span data-ttu-id="e9743-105">Metoda vyžaduje různé parametry, jako je například úložiště, kde je uložen certifikát a hodnotu mají použít při hledání pro certifikát.</span><span class="sxs-lookup"><span data-stu-id="e9743-105">The method requires various parameters, such as the store where the certificate is stored and a value to use when searching for the certificate.</span></span> <span data-ttu-id="e9743-106">Následující postup předvádí, jak prozkoumat úložiště na počítače, který chcete najít příslušný certifikát.</span><span class="sxs-lookup"><span data-stu-id="e9743-106">The following procedure demonstrates how to examine the stores on a computer to find an appropriate certificate.</span></span> <span data-ttu-id="e9743-107">Příklad hledání kryptografický otisk certifikátu, naleznete v části [postupy: načtení kryptografického otisku certifikátu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="e9743-107">For an example of finding the certificate thumbprint, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
### <a name="to-view-certificates-in-the-mmc-snap-in"></a><span data-ttu-id="e9743-108">K zobrazení certifikátů modulu snap-in konzoly MMC</span><span class="sxs-lookup"><span data-stu-id="e9743-108">To view certificates in the MMC snap-in</span></span>  
  
1.  <span data-ttu-id="e9743-109">Otevřete okno příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="e9743-109">Open a Command Prompt window.</span></span>  
  
2.  <span data-ttu-id="e9743-110">Typ `mmc` a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="e9743-110">Type `mmc` and press the ENTER key.</span></span> <span data-ttu-id="e9743-111">Všimněte si, že chcete-li zobrazit certifikáty v úložišti místního počítače, musí být v roli správce.</span><span class="sxs-lookup"><span data-stu-id="e9743-111">Note that to view certificates in the local machine store, you must be in the Administrator role.</span></span>  
  
3.  <span data-ttu-id="e9743-112">Na **soubor** nabídky, klikněte na tlačítko **přidat nebo odebrat modul snap-In**.</span><span class="sxs-lookup"><span data-stu-id="e9743-112">On the **File** menu, click **Add/Remove Snap In**.</span></span>  
  
4.  <span data-ttu-id="e9743-113">Klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="e9743-113">Click **Add**.</span></span>  
  
5.  <span data-ttu-id="e9743-114">V **přidat samostatný modul Snap-in** dialogové okno, vyberte **certifikáty**.</span><span class="sxs-lookup"><span data-stu-id="e9743-114">In the **Add Standalone Snap-in** dialog box, select **Certificates**.</span></span>  
  
6.  <span data-ttu-id="e9743-115">Klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="e9743-115">Click **Add**.</span></span>  
  
7.  <span data-ttu-id="e9743-116">V **modul snap-in Certifikáty** dialogové okno, vyberte **účet počítače** a klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="e9743-116">In the **Certificates snap-in** dialog box, select **Computer account** and click **Next**.</span></span> <span data-ttu-id="e9743-117">Volitelně můžete vybrat **Moje uživatelský účet** nebo **účet služby**.</span><span class="sxs-lookup"><span data-stu-id="e9743-117">Optionally, you can select **My User account** or **Service account**.</span></span> <span data-ttu-id="e9743-118">Pokud si nejste správcem počítače, můžete spravovat certifikáty jenom pro váš uživatelský účet.</span><span class="sxs-lookup"><span data-stu-id="e9743-118">If you are not an administrator of the computer, you can manage certificates only for your user account.</span></span>  
  
8.  <span data-ttu-id="e9743-119">V **vybrat počítač** dialogové okno, klikněte na tlačítko **Dokončit**.</span><span class="sxs-lookup"><span data-stu-id="e9743-119">In the **Select Computer** dialog box, click **Finish**.</span></span>  
  
9. <span data-ttu-id="e9743-120">V **přidat samostatný modul Snap-in** dialogové okno, klikněte na tlačítko **Zavřít**.</span><span class="sxs-lookup"><span data-stu-id="e9743-120">In the **Add Standalone Snap-in** dialog box, click **Close**.</span></span>  
  
10. <span data-ttu-id="e9743-121">Na **přidat nebo odebrat modul Snap-in** dialogové okno, klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="e9743-121">On the **Add/Remove Snap-in** dialog box, click **OK**.</span></span>  
  
11. <span data-ttu-id="e9743-122">V **kořenový adresář konzoly** okně klikněte na tlačítko **certifikáty (místní počítač)** zobrazíte certifikát uloží pro počítač.</span><span class="sxs-lookup"><span data-stu-id="e9743-122">In the **Console Root** window, click **Certificates (Local Computer)** to view the certificate stores for the computer.</span></span>  
  
12. <span data-ttu-id="e9743-123">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e9743-123">Optional.</span></span> <span data-ttu-id="e9743-124">Chcete-li zobrazit certifikáty pro váš účet, opakujte kroky 3 až 6.</span><span class="sxs-lookup"><span data-stu-id="e9743-124">To view certificates for your account, repeat steps 3 to 6.</span></span> <span data-ttu-id="e9743-125">V kroku 7, místo výběru **účet počítače**, klikněte na tlačítko **Moje uživatelský účet** a opakujte kroky 8 až 10.</span><span class="sxs-lookup"><span data-stu-id="e9743-125">In step 7, instead of selecting **Computer account**, click **My User account** and repeat steps 8 to 10.</span></span>  
  
13. <span data-ttu-id="e9743-126">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e9743-126">Optional.</span></span> <span data-ttu-id="e9743-127">Na **soubor** nabídky, klikněte na tlačítko **Uložit** nebo **uložit jako**.</span><span class="sxs-lookup"><span data-stu-id="e9743-127">On the **File** menu, click **Save** or **Save As**.</span></span> <span data-ttu-id="e9743-128">Uložte soubor konzoly pro pozdější použití.</span><span class="sxs-lookup"><span data-stu-id="e9743-128">Save the console file for later reuse.</span></span>  
  
## <a name="viewing-certificates-with-internet-explorer"></a><span data-ttu-id="e9743-129">Zobrazení certifikátů pomocí Internet Exploreru</span><span class="sxs-lookup"><span data-stu-id="e9743-129">Viewing Certificates with Internet Explorer</span></span>  
 <span data-ttu-id="e9743-130">Můžete také zobrazit, exportovat, importovat a odstranění certifikátů v aplikaci Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="e9743-130">You can also view, export, import, and delete certificates by using Internet Explorer.</span></span>  
  
#### <a name="to-view-certificates-with-internet-explorer"></a><span data-ttu-id="e9743-131">K zobrazení certifikátů pomocí Internet Exploreru</span><span class="sxs-lookup"><span data-stu-id="e9743-131">To view certificates with Internet Explorer</span></span>  
  
1.  <span data-ttu-id="e9743-132">V aplikaci Internet Explorer, klikněte na tlačítko **nástroje**, pak klikněte na tlačítko **Možnosti Internetu** zobrazíte **Možnosti Internetu** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="e9743-132">In Internet Explorer, click **Tools**, then click **Internet Options** to display the **Internet Options** dialog box.</span></span>  
  
2.  <span data-ttu-id="e9743-133">Klikněte **obsahu** kartě.</span><span class="sxs-lookup"><span data-stu-id="e9743-133">Click the **Content** tab.</span></span>  
  
3.  <span data-ttu-id="e9743-134">V části **certifikáty**, klikněte na tlačítko **certifikáty**.</span><span class="sxs-lookup"><span data-stu-id="e9743-134">Under **Certificates**, click **Certificates**.</span></span>  
  
4.  <span data-ttu-id="e9743-135">Chcete-li zobrazit podrobnosti o libovolný certifikát, vyberte certifikát a klikněte na tlačítko **zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="e9743-135">To view details of any certificate, select the certificate and click **View**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9743-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="e9743-136">See Also</span></span>  
 [<span data-ttu-id="e9743-137">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="e9743-137">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="e9743-138">Postupy: Vytváření dočasných certifikátů pro použití během vývoje</span><span class="sxs-lookup"><span data-stu-id="e9743-138">How to: Create Temporary Certificates for Use During Development</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)  
 [<span data-ttu-id="e9743-139">Postupy: Načtení kryptografického otisku certifikátu</span><span class="sxs-lookup"><span data-stu-id="e9743-139">How to: Retrieve the Thumbprint of a Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
