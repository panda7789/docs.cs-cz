---
title: "Postupy: načtení kryptografického otisku certifikátu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: certificates [WCF], retrieving thumbprint
ms.assetid: da3101aa-78cd-4c34-9652-d1f24777eeab
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 45f66a7003fe712ab482d5237762e2bafffc5a6e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-retrieve-the-thumbprint-of-a-certificate"></a><span data-ttu-id="c2e9c-102">Postupy: načtení kryptografického otisku certifikátu</span><span class="sxs-lookup"><span data-stu-id="c2e9c-102">How to: Retrieve the Thumbprint of a Certificate</span></span>
<span data-ttu-id="c2e9c-103">Při zápisu [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikaci, která používá certifikátu X.509. certifikát pro ověřování, je často nutné k určení deklarací identity v certifikátu nalezeny.</span><span class="sxs-lookup"><span data-stu-id="c2e9c-103">When writing a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] application that uses an X.509 certificate for authentication, it is often necessary to specify claims found in the certificate.</span></span> <span data-ttu-id="c2e9c-104">Například musíte zadat deklaraci identity kryptografický otisk při použití <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> výčet ve <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="c2e9c-104">For example, you must supply a thumbprint claim when using the <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> enumeration in the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method.</span></span> <span data-ttu-id="c2e9c-105">Hledání hodnota deklarace identity vyžaduje dva kroky.</span><span class="sxs-lookup"><span data-stu-id="c2e9c-105">Finding the claim value requires two steps.</span></span> <span data-ttu-id="c2e9c-106">První otevřete modul snap-in Certifikáty konzoly Microsoft Management Console (MMC).</span><span class="sxs-lookup"><span data-stu-id="c2e9c-106">First, open the Microsoft Management Console (MMC) snap-in for certificates.</span></span> <span data-ttu-id="c2e9c-107">(Viz [postupy: zobrazení certifikátů pomocí modulu Snap-in konzoly MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).) Druhý podle postupu popsaného tady, vyhledejte příslušný certifikát a zkopírujte jeho kryptografický otisk (nebo jiné hodnoty deklarace identity).</span><span class="sxs-lookup"><span data-stu-id="c2e9c-107">(See [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).) Second, as described here, find an appropriate certificate and copy its thumbprint (or other claim values).</span></span>  
  
 <span data-ttu-id="c2e9c-108">Pokud používáte certifikát pro ověřování služby, je důležité si uvědomit, hodnota **vystaveno pro** sloupce (první sloupec v konzole).</span><span class="sxs-lookup"><span data-stu-id="c2e9c-108">If you are using a certificate for service authentication, it is important to note the value of the **Issued To** column (the first column in the console).</span></span> <span data-ttu-id="c2e9c-109">Při použití Secure Sockets Layer (SSL), jako je zabezpečení přenosu, jedním z první kontroly provést k porovnání základní adresa identifikátoru URI (Uniform Resource) služby **vystaveno pro** hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c2e9c-109">When using Secure Sockets Layer (SSL) as a transport security, one of the first checks done is to compare the base address Uniform Resource Identifier (URI) of a service to the **Issued To** value.</span></span> <span data-ttu-id="c2e9c-110">Hodnoty musí odpovídat nebo se zastavit proces ověřování.</span><span class="sxs-lookup"><span data-stu-id="c2e9c-110">The values must match or the authentication process is halted.</span></span>  
  
 <span data-ttu-id="c2e9c-111">Můžete také použít nástroj Makecert.exe z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] SDK k vytvoření dočasného certifikátů pro použití pouze během vývoje.</span><span class="sxs-lookup"><span data-stu-id="c2e9c-111">You can also use the Makecert.exe tool from the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] SDK to create temporary certificates for use only during development.</span></span> <span data-ttu-id="c2e9c-112">Ve výchozím nastavení ale tento certifikát není vystavený certifikační autoritou a nelze jej použít pro produkční účely.</span><span class="sxs-lookup"><span data-stu-id="c2e9c-112">By default, however, such a certificate is not issued by a certification authority, and is unusable for production purposes.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="c2e9c-113">[Postupy: vytváření dočasných certifikátů pro použití při vývoji](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md).</span><span class="sxs-lookup"><span data-stu-id="c2e9c-113"> [How to: Create Temporary Certificates for Use During Development](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md).</span></span>  
  
### <a name="to-retrieve-a-certificates-thumbprint"></a><span data-ttu-id="c2e9c-114">Načíst kryptografický otisk certifikátu</span><span class="sxs-lookup"><span data-stu-id="c2e9c-114">To retrieve a certificate's thumbprint</span></span>  
  
1.  <span data-ttu-id="c2e9c-115">Otevřete modul snap-in Certifikáty konzoly Microsoft Management Console (MMC).</span><span class="sxs-lookup"><span data-stu-id="c2e9c-115">Open the Microsoft Management Console (MMC) snap-in for certificates.</span></span> <span data-ttu-id="c2e9c-116">(Viz [postupy: zobrazení certifikátů pomocí modulu Snap-in konzoly MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).)</span><span class="sxs-lookup"><span data-stu-id="c2e9c-116">(See [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).)</span></span>  
  
2.  <span data-ttu-id="c2e9c-117">V **kořenový adresář konzoly** okno je levé podokno, klikněte na tlačítko **certifikáty (místní počítač)**.</span><span class="sxs-lookup"><span data-stu-id="c2e9c-117">In the **Console Root** window's left pane, click **Certificates (Local Computer)**.</span></span>  
  
3.  <span data-ttu-id="c2e9c-118">Klikněte **osobní** rozbalte složku.</span><span class="sxs-lookup"><span data-stu-id="c2e9c-118">Click the **Personal** folder to expand it.</span></span>  
  
4.  <span data-ttu-id="c2e9c-119">Klikněte **certifikáty** rozbalte složku.</span><span class="sxs-lookup"><span data-stu-id="c2e9c-119">Click the **Certificates** folder to expand it.</span></span>  
  
5.  <span data-ttu-id="c2e9c-120">V seznamu certifikátů, pamatujte **určený pro účely** záhlaví.</span><span class="sxs-lookup"><span data-stu-id="c2e9c-120">In the list of certificates, note the **Intended Purposes** heading.</span></span> <span data-ttu-id="c2e9c-121">Najít certifikát, který obsahuje seznam **ověření klienta** jako zamýšlený účel.</span><span class="sxs-lookup"><span data-stu-id="c2e9c-121">Find a certificate that lists **Client Authentication** as an intended purpose.</span></span>  
  
6.  <span data-ttu-id="c2e9c-122">Dvakrát klikněte na certifikát.</span><span class="sxs-lookup"><span data-stu-id="c2e9c-122">Double-click the certificate.</span></span>  
  
7.  <span data-ttu-id="c2e9c-123">V **certifikát** dialogové okno, klikněte na tlačítko **podrobnosti** kartě.</span><span class="sxs-lookup"><span data-stu-id="c2e9c-123">In the **Certificate** dialog box, click the **Details** tab.</span></span>  
  
8.  <span data-ttu-id="c2e9c-124">Vyhledejte v seznamu polí a klikněte na tlačítko **kryptografický otisk**.</span><span class="sxs-lookup"><span data-stu-id="c2e9c-124">Scroll through the list of fields and click **Thumbprint**.</span></span>  
  
9. <span data-ttu-id="c2e9c-125">Zkopírujte hexadecimálních znaků z pole.</span><span class="sxs-lookup"><span data-stu-id="c2e9c-125">Copy the hexadecimal characters from the box.</span></span> <span data-ttu-id="c2e9c-126">Pokud se tímto kryptografickým otiskem používá v kódu `X509FindType`, odebrat mezery mezi hexadecimální číslice.</span><span class="sxs-lookup"><span data-stu-id="c2e9c-126">If this thumbprint is used in code for the `X509FindType`, remove the spaces between the hexadecimal numbers.</span></span> <span data-ttu-id="c2e9c-127">Například kryptografický otisk "a9 09 50 2d d8 2a e4 14 33 e6 f8 38 86 b0 0d 42 77 a3 2a 7b" musí být zadány ve tvaru "a909502dd82ae41433e6f83886b00d4277a32a7b" v kódu.</span><span class="sxs-lookup"><span data-stu-id="c2e9c-127">For example, the thumbprint "a9 09 50 2d d8 2a e4 14 33 e6 f8 38 86 b0 0d 42 77 a3 2a 7b" should be specified as "a909502dd82ae41433e6f83886b00d4277a32a7b" in code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2e9c-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="c2e9c-128">See Also</span></span>  
 <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>  
 [<span data-ttu-id="c2e9c-129">Postupy: Konfigurace portu certifikát protokolu SSL</span><span class="sxs-lookup"><span data-stu-id="c2e9c-129">How to: Configure a Port with an SSL Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 [<span data-ttu-id="c2e9c-130">Postupy: zobrazení certifikátů pomocí modulu Snap-in konzoly MMC</span><span class="sxs-lookup"><span data-stu-id="c2e9c-130">How to: View Certificates with the MMC Snap-in</span></span>](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)  
 [<span data-ttu-id="c2e9c-131">Postupy: vytváření dočasných certifikátů pro použití při vývoji</span><span class="sxs-lookup"><span data-stu-id="c2e9c-131">How to: Create Temporary Certificates for Use During Development</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
