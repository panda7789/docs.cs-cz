---
title: 'Postupy: Zpřístupnění certifikátů X.509 pro WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- X.509 certificates [WCF]
- certificates [WCF], making X.509 certificates accessible to WCF
- X.509 certificates [WCF], making accessible to WCF
ms.assetid: a54e407c-c2b5-4319-a648-60e43413664b
ms.openlocfilehash: 14f2242ab55795c74fa169382fef846bc0e60ace
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184899"
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="26d35-102">Postupy: Zpřístupnění certifikátů X.509 pro WCF</span><span class="sxs-lookup"><span data-stu-id="26d35-102">How to: Make X.509 Certificates Accessible to WCF</span></span>
<span data-ttu-id="26d35-103">Chcete-li zpřístupnit certifikát X.509 systému Windows Communication Foundation (WCF), musí kód aplikace určit název a umístění úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="26d35-103">To make an X.509 certificate accessible to Windows Communication Foundation (WCF), application code must specify the certificate store name and location.</span></span> <span data-ttu-id="26d35-104">Za určitých okolností musí mít identita procesu přístup k souboru, který obsahuje soukromý klíč přidružený k certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="26d35-104">In certain circumstances, the process identity must have access to the file that contains the private key associated with the X.509 certificate.</span></span> <span data-ttu-id="26d35-105">Chcete-li získat soukromý klíč přidružený k certifikátu X.509 v úložišti certifikátů, wcf musí mít oprávnění k tomu.</span><span class="sxs-lookup"><span data-stu-id="26d35-105">To obtain the private key associated with an X.509 certificate in a certificate store, WCF must have permission to do so.</span></span> <span data-ttu-id="26d35-106">Ve výchozím nastavení může k soukromému klíči certifikátu přistupovat pouze vlastník a systémový účet.</span><span class="sxs-lookup"><span data-stu-id="26d35-106">By default, only the owner and the System account can access the private key of a certificate.</span></span>  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="26d35-107">Zpřístupnění certifikátů X.509 wcf</span><span class="sxs-lookup"><span data-stu-id="26d35-107">To make X.509 certificates accessible to WCF</span></span>  
  
1. <span data-ttu-id="26d35-108">Podejte účet, pod kterým WCF je spuštěn přístup pro čtení do souboru, který obsahuje soukromý klíč přidružený k certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="26d35-108">Give the account under which WCF is running read access to the file that contains the private key associated with the X.509 certificate.</span></span>  
  
    1. <span data-ttu-id="26d35-109">Zjistěte, zda WCF vyžaduje přístup pro čtení k soukromému klíči pro certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="26d35-109">Determine whether WCF requires read access to the private key for the X.509 certificate.</span></span>  
  
         <span data-ttu-id="26d35-110">V následující tabulce je podrobně uveden, zda musí být soukromý klíč k dispozici při použití certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="26d35-110">The following table details whether a private key must be available when using an X.509 certificate.</span></span>  
  
        |<span data-ttu-id="26d35-111">Použití certifikátu X.509</span><span class="sxs-lookup"><span data-stu-id="26d35-111">X.509 certificate use</span></span>|<span data-ttu-id="26d35-112">Privátní klíč</span><span class="sxs-lookup"><span data-stu-id="26d35-112">Private key</span></span>|  
        |---------------------------|-----------------|  
        |<span data-ttu-id="26d35-113">Digitální podepisování odchozí zprávy SOAP.</span><span class="sxs-lookup"><span data-stu-id="26d35-113">Digitally signing an outbound SOAP message.</span></span>|<span data-ttu-id="26d35-114">Ano</span><span class="sxs-lookup"><span data-stu-id="26d35-114">Yes</span></span>|  
        |<span data-ttu-id="26d35-115">Ověření podpisu příchozí zprávy SOAP.</span><span class="sxs-lookup"><span data-stu-id="26d35-115">Verifying the signature of an inbound SOAP message.</span></span>|<span data-ttu-id="26d35-116">Ne</span><span class="sxs-lookup"><span data-stu-id="26d35-116">No</span></span>|  
        |<span data-ttu-id="26d35-117">Šifrování odchozí zprávy SOAP.</span><span class="sxs-lookup"><span data-stu-id="26d35-117">Encrypting an outbound SOAP message.</span></span>|<span data-ttu-id="26d35-118">Ne</span><span class="sxs-lookup"><span data-stu-id="26d35-118">No</span></span>|  
        |<span data-ttu-id="26d35-119">Dešifrování příchozí zprávy SOAP.</span><span class="sxs-lookup"><span data-stu-id="26d35-119">Decrypting an inbound SOAP message.</span></span>|<span data-ttu-id="26d35-120">Ano</span><span class="sxs-lookup"><span data-stu-id="26d35-120">Yes</span></span>|  
  
    2. <span data-ttu-id="26d35-121">Určete umístění úložiště certifikátů a název, ve kterém je certifikát uložen.</span><span class="sxs-lookup"><span data-stu-id="26d35-121">Determine the certificate store location and name in which the certificate is stored.</span></span>  
  
         <span data-ttu-id="26d35-122">Úložiště certifikátů, ve kterém je certifikát uložen, je určeno v kódu aplikace nebo v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="26d35-122">The certificate store in which the certificate is stored is specified either in application code or in configuration.</span></span> <span data-ttu-id="26d35-123">Například následující příklad určuje, že certifikát je `CurrentUser` umístěn `My`v úložišti certifikátů s názvem .</span><span class="sxs-lookup"><span data-stu-id="26d35-123">For example, the following example specifies that the certificate is located in the `CurrentUser` certificate store named `My`.</span></span>  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3. <span data-ttu-id="26d35-124">Zjistěte, kde je soukromý klíč certifikátu umístěn v počítači pomocí nástroje [NajítprivateKey.](../../../../docs/framework/wcf/samples/findprivatekey.md)</span><span class="sxs-lookup"><span data-stu-id="26d35-124">Determine where the private key for the certificate is located on the computer by using the [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool.</span></span>  
  
         <span data-ttu-id="26d35-125">Nástroj [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) vyžaduje název úložiště certifikátů, umístění úložiště certifikátů a něco, co jednoznačně identifikuje certifikát.</span><span class="sxs-lookup"><span data-stu-id="26d35-125">The [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool requires the certificate store name, certificate store location, and something that uniquely identifies the certificate.</span></span> <span data-ttu-id="26d35-126">Nástroj přijímá název předmětu certifikátu nebo jeho kryptografický otisk jako jedinečný identifikátor.</span><span class="sxs-lookup"><span data-stu-id="26d35-126">The tool accepts either the certificate's subject name or its thumbprint as a unique identifier.</span></span> <span data-ttu-id="26d35-127">Další informace o tom, jak určit kryptografický otisk certifikátu, naleznete v tématu [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="26d35-127">For more information about how to determine the thumbprint for a certificate, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
         <span data-ttu-id="26d35-128">Následující příklad kódu používá nástroj [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) k určení umístění soukromého `My` klíče `CurrentUser` pro certifikát v `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`úložišti v úložišti pomocí kryptografického otisku .</span><span class="sxs-lookup"><span data-stu-id="26d35-128">The following code example uses the [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool to determine the location of the private key for a certificate in the `My` store in `CurrentUser` with a thumbprint of `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.</span></span>  
  
        ```console
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4. <span data-ttu-id="26d35-129">Určete účet, pod kterým je wcf spuštěn.</span><span class="sxs-lookup"><span data-stu-id="26d35-129">Determine the account that WCF is running under.</span></span>  
  
         <span data-ttu-id="26d35-130">V následující tabulce je podrobně uveden účet, pod kterým wcf běží pro daný scénář.</span><span class="sxs-lookup"><span data-stu-id="26d35-130">The following table details the account under which WCF is running for a given scenario.</span></span>  
  
        |<span data-ttu-id="26d35-131">Scénář</span><span class="sxs-lookup"><span data-stu-id="26d35-131">Scenario</span></span>|<span data-ttu-id="26d35-132">Identita procesu</span><span class="sxs-lookup"><span data-stu-id="26d35-132">Process identity</span></span>|  
        |--------------|----------------------|  
        |<span data-ttu-id="26d35-133">Klient (konzola nebo aplikace WinForms).</span><span class="sxs-lookup"><span data-stu-id="26d35-133">Client (console or WinForms application).</span></span>|<span data-ttu-id="26d35-134">Aktuálně přihlášený uživatel.</span><span class="sxs-lookup"><span data-stu-id="26d35-134">Currently logged in user.</span></span>|  
        |<span data-ttu-id="26d35-135">Služba, která je hostována samostatně.</span><span class="sxs-lookup"><span data-stu-id="26d35-135">Service that is self-hosted.</span></span>|<span data-ttu-id="26d35-136">Aktuálně přihlášený uživatel.</span><span class="sxs-lookup"><span data-stu-id="26d35-136">Currently logged in user.</span></span>|  
        |<span data-ttu-id="26d35-137">Služba hostovaná ve službě IIS 6.0 (Windows Server 2003) nebo IIS 7.0 (Windows Vista).</span><span class="sxs-lookup"><span data-stu-id="26d35-137">Service that is hosted in IIS 6.0 (Windows Server 2003) or IIS 7.0 (Windows Vista).</span></span>|<span data-ttu-id="26d35-138">SÍŤOVÁ SLUŽBA</span><span class="sxs-lookup"><span data-stu-id="26d35-138">NETWORK SERVICE</span></span>|  
        |<span data-ttu-id="26d35-139">Služba hostovaná ve službě IIS 5.X (Windows XP).</span><span class="sxs-lookup"><span data-stu-id="26d35-139">Service that is hosted in IIS 5.X (Windows XP).</span></span>|<span data-ttu-id="26d35-140">Řízeno `<processModel>` prvkem v souboru Machine.config.</span><span class="sxs-lookup"><span data-stu-id="26d35-140">Controlled by the `<processModel>` element in the Machine.config file.</span></span> <span data-ttu-id="26d35-141">Výchozí účet je ASPNET.</span><span class="sxs-lookup"><span data-stu-id="26d35-141">The default account is ASPNET.</span></span>|  
  
    5. <span data-ttu-id="26d35-142">Udělit přístup pro čtení do souboru, který obsahuje soukromý klíč k účtu, který WCF je spuštěna pod pomocí nástroje, jako je například icacls.exe.</span><span class="sxs-lookup"><span data-stu-id="26d35-142">Grant read access to the file that contains the private key to the account that WCF is running under, using a tool such as icacls.exe.</span></span>  
  
         <span data-ttu-id="26d35-143">Následující příklad kódu upevrdne volitelný seznam řízení přístupu (DACL) pro zadaný soubor, aby účet SÍŤOVÉ SLUŽBY získal přístup k souboru.The following code example uetily the discretionary access control list (DACL) for the specified file to grant the NETWORK SERVICE account read (:R) access to the file.</span><span class="sxs-lookup"><span data-stu-id="26d35-143">The following code example edits the discretionary access control list (DACL) for the specified file to grant the NETWORK SERVICE account read (:R) access to the file.</span></span>  
  
        ```console
        icacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /grant "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a><span data-ttu-id="26d35-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="26d35-144">See also</span></span>

- [<span data-ttu-id="26d35-145">FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="26d35-145">FindPrivateKey</span></span>](../../../../docs/framework/wcf/samples/findprivatekey.md)
- [<span data-ttu-id="26d35-146">Postupy: Načtení kryptografického otisku certifikátu</span><span class="sxs-lookup"><span data-stu-id="26d35-146">How to: Retrieve the Thumbprint of a Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
- [<span data-ttu-id="26d35-147">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="26d35-147">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
