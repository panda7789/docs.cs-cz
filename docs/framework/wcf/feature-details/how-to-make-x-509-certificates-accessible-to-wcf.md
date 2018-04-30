---
title: 'Postupy: Zpřístupnění certifikátů X.509 pro WCF'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- X.509 certificates [WCF]
- certificates [WCF], making X.509 certificates accessible to WCF
- X.509 certificates [WCF], making accessible to WCF
ms.assetid: a54e407c-c2b5-4319-a648-60e43413664b
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 77ee21074b6f1bb5a2f5bd4ee653100d3534075d
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="e2800-102">Postupy: Zpřístupnění certifikátů X.509 pro WCF</span><span class="sxs-lookup"><span data-stu-id="e2800-102">How to: Make X.509 Certificates Accessible to WCF</span></span>
<span data-ttu-id="e2800-103">Pro zpřístupnění certifikát X.509 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], kód aplikace musíte zadat název úložiště certifikátu a umístění.</span><span class="sxs-lookup"><span data-stu-id="e2800-103">To make an X.509 certificate accessible to [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], application code must specify the certificate store name and location.</span></span> <span data-ttu-id="e2800-104">V některých případech identita procesu, musí mít přístup k souboru, který obsahuje soukromý klíč spojenou s certifikátem X.509.</span><span class="sxs-lookup"><span data-stu-id="e2800-104">In certain circumstances, the process identity must have access to the file that contains the private key associated with the X.509 certificate.</span></span> <span data-ttu-id="e2800-105">Získat soukromý klíč přidružený k certifikátu X.509. certifikát v úložišti certifikátů, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] musí mít oprávnění k tomu.</span><span class="sxs-lookup"><span data-stu-id="e2800-105">To obtain the private key associated with an X.509 certificate in a certificate store, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] must have permission to do so.</span></span> <span data-ttu-id="e2800-106">Ve výchozím nastavení může pouze vlastník a systémový účet přístup k privátnímu klíči certifikátu.</span><span class="sxs-lookup"><span data-stu-id="e2800-106">By default, only the owner and the System account can access the private key of a certificate.</span></span>  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="e2800-107">Pro zpřístupnění certifikátů X.509 pro WCF</span><span class="sxs-lookup"><span data-stu-id="e2800-107">To make X.509 certificates accessible to WCF</span></span>  
  
1.  <span data-ttu-id="e2800-108">Zadejte účet, pod kterým [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] běží přístup pro čtení k souboru, který obsahuje soukromý klíč spojenou s certifikátem X.509.</span><span class="sxs-lookup"><span data-stu-id="e2800-108">Give the account under which [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is running read access to the file that contains the private key associated with the X.509 certificate.</span></span>  
  
    1.  <span data-ttu-id="e2800-109">Určit, zda [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vyžaduje přístup pro čtení k privátnímu klíči certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="e2800-109">Determine whether [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requires read access to the private key for the X.509 certificate.</span></span>  
  
         <span data-ttu-id="e2800-110">Následující tabulka uvádí, zda privátní klíč musí být k dispozici při použití certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="e2800-110">The following table details whether a private key must be available when using an X.509 certificate.</span></span>  
  
        |<span data-ttu-id="e2800-111">Použití certifikátu X.509</span><span class="sxs-lookup"><span data-stu-id="e2800-111">X.509 certificate use</span></span>|<span data-ttu-id="e2800-112">privátní klíč</span><span class="sxs-lookup"><span data-stu-id="e2800-112">Private key</span></span>|  
        |---------------------------|-----------------|  
        |<span data-ttu-id="e2800-113">Digitální podepisování odchozí zprávu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="e2800-113">Digitally signing an outbound SOAP message.</span></span>|<span data-ttu-id="e2800-114">Ano</span><span class="sxs-lookup"><span data-stu-id="e2800-114">Yes</span></span>|  
        |<span data-ttu-id="e2800-115">Ověření podpisu příchozí zprávy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="e2800-115">Verifying the signature of an inbound SOAP message.</span></span>|<span data-ttu-id="e2800-116">Ne</span><span class="sxs-lookup"><span data-stu-id="e2800-116">No</span></span>|  
        |<span data-ttu-id="e2800-117">Šifrování odchozí zprávu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="e2800-117">Encrypting an outbound SOAP message.</span></span>|<span data-ttu-id="e2800-118">Ne</span><span class="sxs-lookup"><span data-stu-id="e2800-118">No</span></span>|  
        |<span data-ttu-id="e2800-119">Dešifrování příchozí zprávu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="e2800-119">Decrypting an inbound SOAP message.</span></span>|<span data-ttu-id="e2800-120">Ano</span><span class="sxs-lookup"><span data-stu-id="e2800-120">Yes</span></span>|  
  
    2.  <span data-ttu-id="e2800-121">Určete umístění úložiště certifikátu a název, který certifikát je uložen.</span><span class="sxs-lookup"><span data-stu-id="e2800-121">Determine the certificate store location and name in which the certificate is stored.</span></span>  
  
         <span data-ttu-id="e2800-122">Úložiště certifikátů, ve kterém je uložený certifikát je zadána v kódu aplikace nebo v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="e2800-122">The certificate store in which the certificate is stored is specified either in application code or in configuration.</span></span> <span data-ttu-id="e2800-123">Například následující příklad určuje, že certifikát nachází v `CurrentUser` úložiště certifikátů s názvem `My`.</span><span class="sxs-lookup"><span data-stu-id="e2800-123">For example, the following example specifies that the certificate is located in the `CurrentUser` certificate store named `My`.</span></span>  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3.  <span data-ttu-id="e2800-124">Určení umístění privátní klíč pro certifikát v počítači pomocí [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) nástroj.</span><span class="sxs-lookup"><span data-stu-id="e2800-124">Determine where the private key for the certificate is located on the computer by using the [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool.</span></span>  
  
         <span data-ttu-id="e2800-125">[FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) nástroj vyžaduje název úložiště certifikátu, umístění úložiště certifikátu a něco, která jednoznačně identifikuje certifikát.</span><span class="sxs-lookup"><span data-stu-id="e2800-125">The [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool requires the certificate store name, certificate store location, and something that uniquely identifies the certificate.</span></span> <span data-ttu-id="e2800-126">Nástroj přijme název subjektu certifikátu nebo jeho kryptografický otisk jako jedinečný identifikátor.</span><span class="sxs-lookup"><span data-stu-id="e2800-126">The tool accepts either the certificate's subject name or its thumbprint as a unique identifier.</span></span> <span data-ttu-id="e2800-127">Další informace o tom, jak určit kryptografický otisk certifikátu najdete v tématu [postupy: načtení kryptografického otisku certifikátu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="e2800-127">For more information about how to determine the thumbprint for a certificate, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
         <span data-ttu-id="e2800-128">Následující příklad kódu používá [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) nástroj k určení umístění privátního klíče certifikátu v `My` Uložit `CurrentUser` s kryptografickým otiskem `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.</span><span class="sxs-lookup"><span data-stu-id="e2800-128">The following code example uses the [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool to determine the location of the private key for a certificate in the `My` store in `CurrentUser` with a thumbprint of `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.</span></span>  
  
        ```  
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4.  <span data-ttu-id="e2800-129">Určení účtu, který [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] je spuštěno.</span><span class="sxs-lookup"><span data-stu-id="e2800-129">Determine the account that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is running under.</span></span>  
  
         <span data-ttu-id="e2800-130">V následující tabulce jsou účet, pod kterým [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] běží v daném scénáři.</span><span class="sxs-lookup"><span data-stu-id="e2800-130">The following table details the account under which [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is running for a given scenario.</span></span>  
  
        |<span data-ttu-id="e2800-131">Scénář</span><span class="sxs-lookup"><span data-stu-id="e2800-131">Scenario</span></span>|<span data-ttu-id="e2800-132">Identitě procesu</span><span class="sxs-lookup"><span data-stu-id="e2800-132">Process identity</span></span>|  
        |--------------|----------------------|  
        |<span data-ttu-id="e2800-133">Klient (konzole nebo WinForms aplikace).</span><span class="sxs-lookup"><span data-stu-id="e2800-133">Client (console or WinForms application).</span></span>|<span data-ttu-id="e2800-134">Aktuálně přihlášeného uživatele.</span><span class="sxs-lookup"><span data-stu-id="e2800-134">Currently logged in user.</span></span>|  
        |<span data-ttu-id="e2800-135">Služba, která se hostuje sama.</span><span class="sxs-lookup"><span data-stu-id="e2800-135">Service that is self-hosted.</span></span>|<span data-ttu-id="e2800-136">Aktuálně přihlášeného uživatele.</span><span class="sxs-lookup"><span data-stu-id="e2800-136">Currently logged in user.</span></span>|  
        |<span data-ttu-id="e2800-137">Služby, který je hostován ve službě IIS 6.0 ([!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]) nebo IIS 7.0 ([!INCLUDE[wv](../../../../includes/wv-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="e2800-137">Service that is hosted in IIS 6.0 ([!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]) or IIS 7.0 ([!INCLUDE[wv](../../../../includes/wv-md.md)]).</span></span>|<span data-ttu-id="e2800-138">SÍŤOVÉ SLUŽBY</span><span class="sxs-lookup"><span data-stu-id="e2800-138">NETWORK SERVICE</span></span>|  
        |<span data-ttu-id="e2800-139">Službu, která je hostovaná v IIS 5.X ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="e2800-139">Service that is hosted in IIS 5.X ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]).</span></span>|<span data-ttu-id="e2800-140">Řízené `<processModel>` element v souboru Machine.config.</span><span class="sxs-lookup"><span data-stu-id="e2800-140">Controlled by the `<processModel>` element in the Machine.config file.</span></span> <span data-ttu-id="e2800-141">Je výchozího účtu ASPNET.</span><span class="sxs-lookup"><span data-stu-id="e2800-141">The default account is ASPNET.</span></span>|  
  
    5.  <span data-ttu-id="e2800-142">Udělte oprávnění ke čtení k souboru, který obsahuje soukromý klíč k účtu, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] je spuštěno, pomocí nástroje, jako je cacls.exe.</span><span class="sxs-lookup"><span data-stu-id="e2800-142">Grant read access to the file that contains the private key to the account that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is running under, using a tool such as cacls.exe.</span></span>  
  
         <span data-ttu-id="e2800-143">Následující kód například úpravy (/ E) seznamu řízení přístupu (ACL) pro zadaný soubor udělit (/ G) účet NETWORK SERVICE pro čtení (: R) přístup k souboru.</span><span class="sxs-lookup"><span data-stu-id="e2800-143">The following code example edits (/E) the access control list (ACL) for the specified file to grant (/G) the NETWORK SERVICE account read (:R) access to the file.</span></span>  
  
        ```  
        cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a><span data-ttu-id="e2800-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="e2800-144">See Also</span></span>  
 [<span data-ttu-id="e2800-145">FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="e2800-145">FindPrivateKey</span></span>](../../../../docs/framework/wcf/samples/findprivatekey.md)  
 [<span data-ttu-id="e2800-146">Postupy: Načtení kryptografického otisku certifikátu</span><span class="sxs-lookup"><span data-stu-id="e2800-146">How to: Retrieve the Thumbprint of a Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)  
 [<span data-ttu-id="e2800-147">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="e2800-147">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
