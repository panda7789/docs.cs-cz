---
title: 'Postupy: Zadání řetězu certifikátů certifikační autority používaného k ověřování podpisů (WCF)'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- certificates [WCF], specifying the certificate authority certificate chain
- certificates [WCF], verifying signatures
ms.assetid: 7c719355-aa41-4567-80d0-5115a8cf73fd
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 29637ea7f0a1e533a6735ebfa6f428fe20039e48
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-specify-the-certificate-authority-certificate-chain-used-to-verify-signatures-wcf"></a><span data-ttu-id="8e711-102">Postupy: Zadání řetězu certifikátů certifikační autority používaného k ověřování podpisů (WCF)</span><span class="sxs-lookup"><span data-stu-id="8e711-102">How to: Specify the Certificate Authority Certificate Chain Used to Verify Signatures (WCF)</span></span>
<span data-ttu-id="8e711-103">Když [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] obdrží zprávu protokolu SOAP podepsána pomocí certifikátu X.509, ve výchozím nastavení ověřuje, že certifikát X.509 byl vydán důvěryhodnou certifikační autoritou.</span><span class="sxs-lookup"><span data-stu-id="8e711-103">When [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] receives a SOAP message signed using an X.509 certificate, by default it verifies that the X.509 certificate was issued by a trusted certification authority.</span></span> <span data-ttu-id="8e711-104">K tomu je potřeba vyhledávání v úložišti certifikátů a určení, pokud pro tento certifikační autorita je klasifikován jako důvěryhodný certifikát.</span><span class="sxs-lookup"><span data-stu-id="8e711-104">This is done by looking in a certificate store and determining if the certificate for that certification authority has been designated as trusted.</span></span> <span data-ttu-id="8e711-105">Aby [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] za účelem určení, musí být nainstalován řetězu certifikátů certifikační autority v úložišti certifikátů správné.</span><span class="sxs-lookup"><span data-stu-id="8e711-105">In order for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to make this determination, the certification authority certificate chain must be installed in the correct certificate store.</span></span>  
  
### <a name="to-install-a-certification-authority-certificate-chain"></a><span data-ttu-id="8e711-106">Chcete-li nainstalovat řetěz certifikátů certifikační autority</span><span class="sxs-lookup"><span data-stu-id="8e711-106">To install a certification authority certificate chain</span></span>  
  
-   <span data-ttu-id="8e711-107">Pro každý certifikační autoritu, kterou chce příjemce zprávu protokolu SOAP důvěřovat vystavené certifikáty X.509, který ukládání instalace řetězu certifikátů certifikační autority do certifikátu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] je nakonfigurován k načtení certifikátů X.509 z.</span><span class="sxs-lookup"><span data-stu-id="8e711-107">For each certification authority that a SOAP message recipient intends to trust X.509 certificates issued from, install the certification authority certificate chain into the certificate store that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is configured to retrieve X.509 certificates from.</span></span>  
  
     <span data-ttu-id="8e711-108">Například pokud příjemce zprávu protokolu SOAP v úmyslu důvěřovat certifikátů X.509 vystavených společností Microsoft, řetězu certifikátů certifikační autority pro Microsoft musí být nainstalován v certifikátu uložit, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nastavena tak, aby Hledat certifikáty X.509 z.</span><span class="sxs-lookup"><span data-stu-id="8e711-108">For instance, if a SOAP message recipient intends to trust X.509 certificates issued by Microsoft, the certification authority certificate chain for Microsoft must be installed in the certificate store that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is set up to look for X.509 certificates from.</span></span> <span data-ttu-id="8e711-109">Úložiště certifikátů, ve kterém [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vypadá pro certifikáty X.509 lze zadat v kódu nebo konfigurace.</span><span class="sxs-lookup"><span data-stu-id="8e711-109">The certificate store in which [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] looks for X.509 certificates can be specified in code or configuration.</span></span> <span data-ttu-id="8e711-110">Například můžete zadat v kódu pomocí <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metoda nebo v konfiguraci několika způsoby, včetně [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) .</span><span class="sxs-lookup"><span data-stu-id="8e711-110">For example, this can be specified in code using the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method or in configuration a few ways, including the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) .</span></span>  
  
     <span data-ttu-id="8e711-111">Protože systém Windows je dodáván s sadu výchozí řetězů certifikátů pro důvěryhodné certifikační autority, nemusí být potřeba instalovat řetěz certifikátů pro všechny certifikačních autorit.</span><span class="sxs-lookup"><span data-stu-id="8e711-111">Because Windows ships with a set of default certificate chains for trusted certificate authorities, it may not be necessary to install the certificate chain for all certificate authorities.</span></span>  
  
    1.  <span data-ttu-id="8e711-112">Exportujte řetězu certifikátů certifikační autority.</span><span class="sxs-lookup"><span data-stu-id="8e711-112">Export the certification authority certificate chain.</span></span>  
  
         <span data-ttu-id="8e711-113">Přesně způsob provedení závisí na certifikační autoritě.</span><span class="sxs-lookup"><span data-stu-id="8e711-113">Exactly how this is done depends on the certification authority.</span></span> <span data-ttu-id="8e711-114">Pokud certifikační autorita běží certifikační služby společnosti Microsoft, vyberte **stáhnout certifikát certifikační Autority, řetěz certifikátů nebo seznam CRL**a potom zvolte **stáhnout certifikát certifikační Autority**.</span><span class="sxs-lookup"><span data-stu-id="8e711-114">If the certification authority is running Microsoft Certificate Services, select **Download a CA certificate, certificate chain, or CRL**, and then choose **Download CA certificate**.</span></span>  
  
    2.  <span data-ttu-id="8e711-115">Importujte řetězu certifikátů certifikační autority.</span><span class="sxs-lookup"><span data-stu-id="8e711-115">Import the certification authority certificate chain.</span></span>  
  
         <span data-ttu-id="8e711-116">V Microsoft Management Console (MMC), otevřete modul snap-in Certifikáty.</span><span class="sxs-lookup"><span data-stu-id="8e711-116">In the Microsoft Management Console (MMC), open the Certificates snap-in.</span></span> <span data-ttu-id="8e711-117">Pro certifikát úložiště, který [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] je nakonfigurován k načtení certifikátů X.509 z vyberte **důvěryhodné kořenové** **certifikačních autorit**složky.</span><span class="sxs-lookup"><span data-stu-id="8e711-117">For the certificate store that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is configured to retrieve X.509 certificates from, select the **Trusted Root** **Certification Authorities**folder.</span></span> <span data-ttu-id="8e711-118">V části **důvěryhodné kořenové certifikační autority** složku, klikněte pravým tlačítkem myši **certifikáty**složku, přejděte na příkaz **všechny úlohy**a potom klikněte na **importu** .</span><span class="sxs-lookup"><span data-stu-id="8e711-118">Under the **Trusted Root Certification Authorities** folder, right-click the **Certificates**folder, point to **All Tasks**, and then click **Import**.</span></span> <span data-ttu-id="8e711-119">Zadejte soubor exportovali v kroku.</span><span class="sxs-lookup"><span data-stu-id="8e711-119">Provide the file exported in step a.</span></span>  
  
         <span data-ttu-id="8e711-120">Další informace o pomocí modulu snap-in Certifikáty konzoly MMC najdete v tématu [postupy: zobrazení certifikátů pomocí modulu Snap-in konzoly MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="8e711-120">For more information about using the Certificates snap-in with MMC, see [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e711-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="8e711-121">See Also</span></span>  
 [<span data-ttu-id="8e711-122">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="8e711-122">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
