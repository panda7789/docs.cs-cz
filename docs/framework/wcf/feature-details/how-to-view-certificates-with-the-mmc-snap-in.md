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
ms.openlocfilehash: 5981e68ebe2870870fff5e92e87d7582ac2c42b5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a><span data-ttu-id="71a6b-102">Postupy: Zobrazení certifikátů pomocí modulu snap-in konzoly MMC</span><span class="sxs-lookup"><span data-stu-id="71a6b-102">How to: View Certificates with the MMC Snap-in</span></span>
<span data-ttu-id="71a6b-103">Běžný typ přihlašovacích údajů je certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="71a6b-103">A common type of credential is the X.509 certificate.</span></span> <span data-ttu-id="71a6b-104">Při vytváření zabezpečené služby nebo klientů, můžete zadat, certifikát se dá použít jako pověření klienta služby nebo pomocí metody, jako <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="71a6b-104">When creating secure services or clients, you can specify a certificate be used as the client or service credential by using methods such as the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method.</span></span> <span data-ttu-id="71a6b-105">Metoda vyžaduje různé parametry, jako je například úložiště, kde je uložen certifikát a hodnotu mají použít při hledání pro certifikát.</span><span class="sxs-lookup"><span data-stu-id="71a6b-105">The method requires various parameters, such as the store where the certificate is stored and a value to use when searching for the certificate.</span></span> <span data-ttu-id="71a6b-106">Následující postup předvádí, jak prozkoumat úložiště na počítače, který chcete najít příslušný certifikát.</span><span class="sxs-lookup"><span data-stu-id="71a6b-106">The following procedure demonstrates how to examine the stores on a computer to find an appropriate certificate.</span></span> <span data-ttu-id="71a6b-107">Příklad hledání kryptografický otisk certifikátu, naleznete v části [postupy: načtení kryptografického otisku certifikátu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="71a6b-107">For an example of finding the certificate thumbprint, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
### <a name="to-view-certificates-in-the-mmc-snap-in"></a><span data-ttu-id="71a6b-108">K zobrazení certifikátů modulu snap-in konzoly MMC</span><span class="sxs-lookup"><span data-stu-id="71a6b-108">To view certificates in the MMC snap-in</span></span>  
  
1.  <span data-ttu-id="71a6b-109">Otevřete okno příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="71a6b-109">Open a Command Prompt window.</span></span>  
  
2.  <span data-ttu-id="71a6b-110">Typ `mmc` a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="71a6b-110">Type `mmc` and press the ENTER key.</span></span> <span data-ttu-id="71a6b-111">Všimněte si, že chcete-li zobrazit certifikáty v úložišti místního počítače, musí být v roli správce.</span><span class="sxs-lookup"><span data-stu-id="71a6b-111">Note that to view certificates in the local machine store, you must be in the Administrator role.</span></span>  
  
3.  <span data-ttu-id="71a6b-112">Na **soubor** nabídky, klikněte na tlačítko **přidat nebo odebrat modul snap-In**.</span><span class="sxs-lookup"><span data-stu-id="71a6b-112">On the **File** menu, click **Add/Remove Snap In**.</span></span>  
  
4.  <span data-ttu-id="71a6b-113">Klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="71a6b-113">Click **Add**.</span></span>  
  
5.  <span data-ttu-id="71a6b-114">V **přidat samostatný modul Snap-in** dialogové okno, vyberte **certifikáty**.</span><span class="sxs-lookup"><span data-stu-id="71a6b-114">In the **Add Standalone Snap-in** dialog box, select **Certificates**.</span></span>  
  
6.  <span data-ttu-id="71a6b-115">Klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="71a6b-115">Click **Add**.</span></span>  
  
7.  <span data-ttu-id="71a6b-116">V **modul snap-in Certifikáty** dialogové okno, vyberte **účet počítače** a klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="71a6b-116">In the **Certificates snap-in** dialog box, select **Computer account** and click **Next**.</span></span> <span data-ttu-id="71a6b-117">Volitelně můžete vybrat **Moje uživatelský účet** nebo **účet služby**.</span><span class="sxs-lookup"><span data-stu-id="71a6b-117">Optionally, you can select **My User account** or **Service account**.</span></span> <span data-ttu-id="71a6b-118">Pokud si nejste správcem počítače, můžete spravovat certifikáty jenom pro váš uživatelský účet.</span><span class="sxs-lookup"><span data-stu-id="71a6b-118">If you are not an administrator of the computer, you can manage certificates only for your user account.</span></span>  
  
8.  <span data-ttu-id="71a6b-119">V **vybrat počítač** dialogové okno, klikněte na tlačítko **Dokončit**.</span><span class="sxs-lookup"><span data-stu-id="71a6b-119">In the **Select Computer** dialog box, click **Finish**.</span></span>  
  
9. <span data-ttu-id="71a6b-120">V **přidat samostatný modul Snap-in** dialogové okno, klikněte na tlačítko **Zavřít**.</span><span class="sxs-lookup"><span data-stu-id="71a6b-120">In the **Add Standalone Snap-in** dialog box, click **Close**.</span></span>  
  
10. <span data-ttu-id="71a6b-121">Na **přidat nebo odebrat modul Snap-in** dialogové okno, klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="71a6b-121">On the **Add/Remove Snap-in** dialog box, click **OK**.</span></span>  
  
11. <span data-ttu-id="71a6b-122">V **kořenový adresář konzoly** okně klikněte na tlačítko **certifikáty (místní počítač)** zobrazíte certifikát uloží pro počítač.</span><span class="sxs-lookup"><span data-stu-id="71a6b-122">In the **Console Root** window, click **Certificates (Local Computer)** to view the certificate stores for the computer.</span></span>  
  
12. <span data-ttu-id="71a6b-123">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="71a6b-123">Optional.</span></span> <span data-ttu-id="71a6b-124">Chcete-li zobrazit certifikáty pro váš účet, opakujte kroky 3 až 6.</span><span class="sxs-lookup"><span data-stu-id="71a6b-124">To view certificates for your account, repeat steps 3 to 6.</span></span> <span data-ttu-id="71a6b-125">V kroku 7, místo výběru **účet počítače**, klikněte na tlačítko **Moje uživatelský účet** a opakujte kroky 8 až 10.</span><span class="sxs-lookup"><span data-stu-id="71a6b-125">In step 7, instead of selecting **Computer account**, click **My User account** and repeat steps 8 to 10.</span></span>  
  
13. <span data-ttu-id="71a6b-126">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="71a6b-126">Optional.</span></span> <span data-ttu-id="71a6b-127">Na **soubor** nabídky, klikněte na tlačítko **Uložit** nebo **uložit jako**.</span><span class="sxs-lookup"><span data-stu-id="71a6b-127">On the **File** menu, click **Save** or **Save As**.</span></span> <span data-ttu-id="71a6b-128">Uložte soubor konzoly pro pozdější použití.</span><span class="sxs-lookup"><span data-stu-id="71a6b-128">Save the console file for later reuse.</span></span>  
  
## <a name="viewing-certificates-with-internet-explorer"></a><span data-ttu-id="71a6b-129">Zobrazení certifikátů pomocí Internet Exploreru</span><span class="sxs-lookup"><span data-stu-id="71a6b-129">Viewing Certificates with Internet Explorer</span></span>  
 <span data-ttu-id="71a6b-130">Můžete také zobrazit, exportovat, importovat a odstranění certifikátů v aplikaci Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="71a6b-130">You can also view, export, import, and delete certificates by using Internet Explorer.</span></span>  
  
#### <a name="to-view-certificates-with-internet-explorer"></a><span data-ttu-id="71a6b-131">K zobrazení certifikátů pomocí Internet Exploreru</span><span class="sxs-lookup"><span data-stu-id="71a6b-131">To view certificates with Internet Explorer</span></span>  
  
1.  <span data-ttu-id="71a6b-132">V aplikaci Internet Explorer, klikněte na tlačítko **nástroje**, pak klikněte na tlačítko **Možnosti Internetu** zobrazíte **Možnosti Internetu** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="71a6b-132">In Internet Explorer, click **Tools**, then click **Internet Options** to display the **Internet Options** dialog box.</span></span>  
  
2.  <span data-ttu-id="71a6b-133">Klikněte **obsahu** kartě.</span><span class="sxs-lookup"><span data-stu-id="71a6b-133">Click the **Content** tab.</span></span>  
  
3.  <span data-ttu-id="71a6b-134">V části **certifikáty**, klikněte na tlačítko **certifikáty**.</span><span class="sxs-lookup"><span data-stu-id="71a6b-134">Under **Certificates**, click **Certificates**.</span></span>  
  
4.  <span data-ttu-id="71a6b-135">Chcete-li zobrazit podrobnosti o libovolný certifikát, vyberte certifikát a klikněte na tlačítko **zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="71a6b-135">To view details of any certificate, select the certificate and click **View**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71a6b-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="71a6b-136">See Also</span></span>  
 [<span data-ttu-id="71a6b-137">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="71a6b-137">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="71a6b-138">Postupy: vytváření dočasných certifikátů pro použití při vývoji</span><span class="sxs-lookup"><span data-stu-id="71a6b-138">How to: Create Temporary Certificates for Use During Development</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)  
 [<span data-ttu-id="71a6b-139">Postupy: načtení kryptografického otisku certifikátu</span><span class="sxs-lookup"><span data-stu-id="71a6b-139">How to: Retrieve the Thumbprint of a Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
