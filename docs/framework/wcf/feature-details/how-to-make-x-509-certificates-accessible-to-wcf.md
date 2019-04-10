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
ms.openlocfilehash: 85f572f021f1613e0a2bb70cc090f58d2833182e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59219912"
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="4b1bb-102">Postupy: Zpřístupnění certifikátů X.509 pro WCF</span><span class="sxs-lookup"><span data-stu-id="4b1bb-102">How to: Make X.509 Certificates Accessible to WCF</span></span>
<span data-ttu-id="4b1bb-103">Zpřístupnit certifikát X.509 do služby Windows Communication Foundation (WCF), musí kód aplikace zadejte název úložiště certifikátu a umístění.</span><span class="sxs-lookup"><span data-stu-id="4b1bb-103">To make an X.509 certificate accessible to Windows Communication Foundation (WCF), application code must specify the certificate store name and location.</span></span> <span data-ttu-id="4b1bb-104">V některých případech se identita procesu, musí mít přístup k souboru, který obsahuje privátní klíč spojený s certifikátem X.509.</span><span class="sxs-lookup"><span data-stu-id="4b1bb-104">In certain circumstances, the process identity must have access to the file that contains the private key associated with the X.509 certificate.</span></span> <span data-ttu-id="4b1bb-105">K získání soukromého klíče přidružené k certifikátu v úložišti certifikátů X.509, WCF, musí mít oprávnění k tomuto.</span><span class="sxs-lookup"><span data-stu-id="4b1bb-105">To obtain the private key associated with an X.509 certificate in a certificate store, WCF must have permission to do so.</span></span> <span data-ttu-id="4b1bb-106">Ve výchozím nastavení můžete přístup pouze vlastník a účet System privátní klíč certifikátu.</span><span class="sxs-lookup"><span data-stu-id="4b1bb-106">By default, only the owner and the System account can access the private key of a certificate.</span></span>  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="4b1bb-107">Pro zpřístupnění certifikátů X.509 pro WCF</span><span class="sxs-lookup"><span data-stu-id="4b1bb-107">To make X.509 certificates accessible to WCF</span></span>  
  
1.  <span data-ttu-id="4b1bb-108">Zadejte účet, pod které WCF je spuštěna oprávnění ke čtení souboru, který obsahuje privátní klíč spojený s certifikátem X.509.</span><span class="sxs-lookup"><span data-stu-id="4b1bb-108">Give the account under which WCF is running read access to the file that contains the private key associated with the X.509 certificate.</span></span>  
  
    1.  <span data-ttu-id="4b1bb-109">Zjistěte, zda WCF vyžaduje přístup pro čtení k privátnímu klíči certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="4b1bb-109">Determine whether WCF requires read access to the private key for the X.509 certificate.</span></span>  
  
         <span data-ttu-id="4b1bb-110">Následující tabulka uvádí, zda privátní klíč musí být k dispozici při použití certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="4b1bb-110">The following table details whether a private key must be available when using an X.509 certificate.</span></span>  
  
        |<span data-ttu-id="4b1bb-111">Použití certifikátu X.509</span><span class="sxs-lookup"><span data-stu-id="4b1bb-111">X.509 certificate use</span></span>|<span data-ttu-id="4b1bb-112">privátní klíč</span><span class="sxs-lookup"><span data-stu-id="4b1bb-112">Private key</span></span>|  
        |---------------------------|-----------------|  
        |<span data-ttu-id="4b1bb-113">Digitální podepisování odchozí zprávu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="4b1bb-113">Digitally signing an outbound SOAP message.</span></span>|<span data-ttu-id="4b1bb-114">Ano</span><span class="sxs-lookup"><span data-stu-id="4b1bb-114">Yes</span></span>|  
        |<span data-ttu-id="4b1bb-115">Ověření podpisu příchozí zprávy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="4b1bb-115">Verifying the signature of an inbound SOAP message.</span></span>|<span data-ttu-id="4b1bb-116">Ne</span><span class="sxs-lookup"><span data-stu-id="4b1bb-116">No</span></span>|  
        |<span data-ttu-id="4b1bb-117">Šifrování odchozí zprávu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="4b1bb-117">Encrypting an outbound SOAP message.</span></span>|<span data-ttu-id="4b1bb-118">Ne</span><span class="sxs-lookup"><span data-stu-id="4b1bb-118">No</span></span>|  
        |<span data-ttu-id="4b1bb-119">Dešifrování příchozí zprávy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="4b1bb-119">Decrypting an inbound SOAP message.</span></span>|<span data-ttu-id="4b1bb-120">Ano</span><span class="sxs-lookup"><span data-stu-id="4b1bb-120">Yes</span></span>|  
  
    2.  <span data-ttu-id="4b1bb-121">Určete umístění úložiště certifikátů a název, který certifikát je uložen.</span><span class="sxs-lookup"><span data-stu-id="4b1bb-121">Determine the certificate store location and name in which the certificate is stored.</span></span>  
  
         <span data-ttu-id="4b1bb-122">Úložiště certifikátů, ve kterém certifikát je uložen je zadat v kódu aplikace nebo v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="4b1bb-122">The certificate store in which the certificate is stored is specified either in application code or in configuration.</span></span> <span data-ttu-id="4b1bb-123">Například následující příklad určuje, že certifikát je umístěn v `CurrentUser` úložiště certifikátů s názvem `My`.</span><span class="sxs-lookup"><span data-stu-id="4b1bb-123">For example, the following example specifies that the certificate is located in the `CurrentUser` certificate store named `My`.</span></span>  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3.  <span data-ttu-id="4b1bb-124">Určení, kde je umístěn privátní klíč pro certifikát v počítači pomocí [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) nástroj.</span><span class="sxs-lookup"><span data-stu-id="4b1bb-124">Determine where the private key for the certificate is located on the computer by using the [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool.</span></span>  
  
         <span data-ttu-id="4b1bb-125">[FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) nástroj vyžaduje název úložiště certifikátu, umístění úložiště certifikátů a něco, který jednoznačně identifikuje tento certifikát.</span><span class="sxs-lookup"><span data-stu-id="4b1bb-125">The [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool requires the certificate store name, certificate store location, and something that uniquely identifies the certificate.</span></span> <span data-ttu-id="4b1bb-126">Nástroj přijímá jako jedinečný identifikátor názvu subjektu certifikátu nebo jeho kryptografický otisk.</span><span class="sxs-lookup"><span data-stu-id="4b1bb-126">The tool accepts either the certificate's subject name or its thumbprint as a unique identifier.</span></span> <span data-ttu-id="4b1bb-127">Další informace o tom, jak určit kryptografický otisk certifikátu, naleznete v tématu [jak: Načtení kryptografického otisku certifikátu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="4b1bb-127">For more information about how to determine the thumbprint for a certificate, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
         <span data-ttu-id="4b1bb-128">Následující příklad kódu používá [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) nástroje k určení umístění privátního klíče pro certifikát v `My` ukládat v `CurrentUser` pomocí kryptografického otisku `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.</span><span class="sxs-lookup"><span data-stu-id="4b1bb-128">The following code example uses the [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool to determine the location of the private key for a certificate in the `My` store in `CurrentUser` with a thumbprint of `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.</span></span>  
  
        ```  
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4.  <span data-ttu-id="4b1bb-129">Určete účet, ve které běží WCF.</span><span class="sxs-lookup"><span data-stu-id="4b1bb-129">Determine the account that WCF is running under.</span></span>  
  
         <span data-ttu-id="4b1bb-130">Následující tabulka obsahuje podrobnosti o účtu, pod kterým běží WCF v daném scénáři.</span><span class="sxs-lookup"><span data-stu-id="4b1bb-130">The following table details the account under which WCF is running for a given scenario.</span></span>  
  
        |<span data-ttu-id="4b1bb-131">Scénář</span><span class="sxs-lookup"><span data-stu-id="4b1bb-131">Scenario</span></span>|<span data-ttu-id="4b1bb-132">Identita procesu</span><span class="sxs-lookup"><span data-stu-id="4b1bb-132">Process identity</span></span>|  
        |--------------|----------------------|  
        |<span data-ttu-id="4b1bb-133">Klient (konzole nebo aplikace WinForms).</span><span class="sxs-lookup"><span data-stu-id="4b1bb-133">Client (console or WinForms application).</span></span>|<span data-ttu-id="4b1bb-134">Aktuálně přihlášeného uživatele.</span><span class="sxs-lookup"><span data-stu-id="4b1bb-134">Currently logged in user.</span></span>|  
        |<span data-ttu-id="4b1bb-135">Služba, která je v místním prostředí.</span><span class="sxs-lookup"><span data-stu-id="4b1bb-135">Service that is self-hosted.</span></span>|<span data-ttu-id="4b1bb-136">Aktuálně přihlášeného uživatele.</span><span class="sxs-lookup"><span data-stu-id="4b1bb-136">Currently logged in user.</span></span>|  
        |<span data-ttu-id="4b1bb-137">Služba, která je hostovaná ve službě IIS 6.0 ([!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]) nebo službu IIS 7.0 ([!INCLUDE[wv](../../../../includes/wv-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="4b1bb-137">Service that is hosted in IIS 6.0 ([!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]) or IIS 7.0 ([!INCLUDE[wv](../../../../includes/wv-md.md)]).</span></span>|<span data-ttu-id="4b1bb-138">SÍŤOVÉ SLUŽBY</span><span class="sxs-lookup"><span data-stu-id="4b1bb-138">NETWORK SERVICE</span></span>|  
        |<span data-ttu-id="4b1bb-139">Službu, která je hostovaná v IIS 5.X ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="4b1bb-139">Service that is hosted in IIS 5.X ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]).</span></span>|<span data-ttu-id="4b1bb-140">Řídí `<processModel>` element v souboru Machine.config.</span><span class="sxs-lookup"><span data-stu-id="4b1bb-140">Controlled by the `<processModel>` element in the Machine.config file.</span></span> <span data-ttu-id="4b1bb-141">Je výchozího účtu ASPNET.</span><span class="sxs-lookup"><span data-stu-id="4b1bb-141">The default account is ASPNET.</span></span>|  
  
    5.  <span data-ttu-id="4b1bb-142">Udělte oprávnění ke čtení souboru, který obsahuje privátní klíč k účtu, ve které WCF běží, pomocí nástroje, jako je například icacls.exe.</span><span class="sxs-lookup"><span data-stu-id="4b1bb-142">Grant read access to the file that contains the private key to the account that WCF is running under, using a tool such as icacls.exe.</span></span>  
  
         <span data-ttu-id="4b1bb-143">Následující příklad kódu upraví seznam řízení přístupu (DACL) pro zadaný soubor udělit čtení účtu síťové služby (: R) přístup k souboru.</span><span class="sxs-lookup"><span data-stu-id="4b1bb-143">The following code example edits the discretionary access control list (DACL) for the specified file to grant the NETWORK SERVICE account read (:R) access to the file.</span></span>  
  
        ```  
        icacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /grant "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a><span data-ttu-id="4b1bb-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4b1bb-144">See also</span></span>

- [<span data-ttu-id="4b1bb-145">FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="4b1bb-145">FindPrivateKey</span></span>](../../../../docs/framework/wcf/samples/findprivatekey.md)
- [<span data-ttu-id="4b1bb-146">Postupy: Načtení kryptografického otisku certifikátu</span><span class="sxs-lookup"><span data-stu-id="4b1bb-146">How to: Retrieve the Thumbprint of a Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
- [<span data-ttu-id="4b1bb-147">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="4b1bb-147">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
