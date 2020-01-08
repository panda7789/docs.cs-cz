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
ms.openlocfilehash: 7f24966f06730e62ea7a8967c3930f05ca78f50e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347085"
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="12b01-102">Postupy: Zpřístupnění certifikátů X.509 pro WCF</span><span class="sxs-lookup"><span data-stu-id="12b01-102">How to: Make X.509 Certificates Accessible to WCF</span></span>
<span data-ttu-id="12b01-103">Aby byl certifikát X. 509 přístupný Windows Communication Foundation (WCF), kód aplikace musí určovat název a umístění úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="12b01-103">To make an X.509 certificate accessible to Windows Communication Foundation (WCF), application code must specify the certificate store name and location.</span></span> <span data-ttu-id="12b01-104">V určitých případech musí mít identita procesu přístup k souboru, který obsahuje privátní klíč přidružený k certifikátu X. 509.</span><span class="sxs-lookup"><span data-stu-id="12b01-104">In certain circumstances, the process identity must have access to the file that contains the private key associated with the X.509 certificate.</span></span> <span data-ttu-id="12b01-105">K získání privátního klíče přidruženého k certifikátu X. 509 v úložišti certifikátů musí mít WCF oprávnění k tomu.</span><span class="sxs-lookup"><span data-stu-id="12b01-105">To obtain the private key associated with an X.509 certificate in a certificate store, WCF must have permission to do so.</span></span> <span data-ttu-id="12b01-106">Ve výchozím nastavení má přístup k privátnímu klíči certifikátu pouze vlastník a systémový účet.</span><span class="sxs-lookup"><span data-stu-id="12b01-106">By default, only the owner and the System account can access the private key of a certificate.</span></span>  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="12b01-107">Zpřístupnění certifikátů X. 509 pro WCF</span><span class="sxs-lookup"><span data-stu-id="12b01-107">To make X.509 certificates accessible to WCF</span></span>  
  
1. <span data-ttu-id="12b01-108">Udělte účtu, pod kterým má WCF spuštěný přístup pro čtení k souboru, který obsahuje privátní klíč přidružený k certifikátu X. 509.</span><span class="sxs-lookup"><span data-stu-id="12b01-108">Give the account under which WCF is running read access to the file that contains the private key associated with the X.509 certificate.</span></span>  
  
    1. <span data-ttu-id="12b01-109">Určete, zda WCF vyžaduje přístup pro čtení k privátnímu klíči pro certifikát X. 509.</span><span class="sxs-lookup"><span data-stu-id="12b01-109">Determine whether WCF requires read access to the private key for the X.509 certificate.</span></span>  
  
         <span data-ttu-id="12b01-110">Následující tabulka popisuje, jestli musí být při použití certifikátu X. 509 k dispozici privátní klíč.</span><span class="sxs-lookup"><span data-stu-id="12b01-110">The following table details whether a private key must be available when using an X.509 certificate.</span></span>  
  
        |<span data-ttu-id="12b01-111">Použití certifikátu X. 509</span><span class="sxs-lookup"><span data-stu-id="12b01-111">X.509 certificate use</span></span>|<span data-ttu-id="12b01-112">Privátní klíč</span><span class="sxs-lookup"><span data-stu-id="12b01-112">Private key</span></span>|  
        |---------------------------|-----------------|  
        |<span data-ttu-id="12b01-113">Digitální podepisování odchozí zprávy SOAP.</span><span class="sxs-lookup"><span data-stu-id="12b01-113">Digitally signing an outbound SOAP message.</span></span>|<span data-ttu-id="12b01-114">Ano</span><span class="sxs-lookup"><span data-stu-id="12b01-114">Yes</span></span>|  
        |<span data-ttu-id="12b01-115">Ověřuje se podpis příchozí zprávy SOAP.</span><span class="sxs-lookup"><span data-stu-id="12b01-115">Verifying the signature of an inbound SOAP message.</span></span>|<span data-ttu-id="12b01-116">Ne</span><span class="sxs-lookup"><span data-stu-id="12b01-116">No</span></span>|  
        |<span data-ttu-id="12b01-117">Šifrování odchozí zprávy SOAP.</span><span class="sxs-lookup"><span data-stu-id="12b01-117">Encrypting an outbound SOAP message.</span></span>|<span data-ttu-id="12b01-118">Ne</span><span class="sxs-lookup"><span data-stu-id="12b01-118">No</span></span>|  
        |<span data-ttu-id="12b01-119">Probíhá dešifrování příchozí zprávy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="12b01-119">Decrypting an inbound SOAP message.</span></span>|<span data-ttu-id="12b01-120">Ano</span><span class="sxs-lookup"><span data-stu-id="12b01-120">Yes</span></span>|  
  
    2. <span data-ttu-id="12b01-121">Určete umístění a název úložiště certifikátů, ve kterém je certifikát uložený.</span><span class="sxs-lookup"><span data-stu-id="12b01-121">Determine the certificate store location and name in which the certificate is stored.</span></span>  
  
         <span data-ttu-id="12b01-122">Úložiště certifikátů, ve kterém je certifikát uložený, je zadané buď v kódu aplikace, nebo v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="12b01-122">The certificate store in which the certificate is stored is specified either in application code or in configuration.</span></span> <span data-ttu-id="12b01-123">Například následující příklad určuje, že certifikát je umístěn v úložišti certifikátů `CurrentUser` s názvem `My`.</span><span class="sxs-lookup"><span data-stu-id="12b01-123">For example, the following example specifies that the certificate is located in the `CurrentUser` certificate store named `My`.</span></span>  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3. <span data-ttu-id="12b01-124">Pomocí nástroje [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) určete, kde se privátní klíč pro certifikát nachází v počítači.</span><span class="sxs-lookup"><span data-stu-id="12b01-124">Determine where the private key for the certificate is located on the computer by using the [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool.</span></span>  
  
         <span data-ttu-id="12b01-125">Nástroj [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) vyžaduje název úložiště certifikátů, umístění úložiště certifikátů a něco, co certifikát jedinečně identifikuje.</span><span class="sxs-lookup"><span data-stu-id="12b01-125">The [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool requires the certificate store name, certificate store location, and something that uniquely identifies the certificate.</span></span> <span data-ttu-id="12b01-126">Nástroj přijme buď název předmětu certifikátu, nebo jeho kryptografický otisk jako jedinečný identifikátor.</span><span class="sxs-lookup"><span data-stu-id="12b01-126">The tool accepts either the certificate's subject name or its thumbprint as a unique identifier.</span></span> <span data-ttu-id="12b01-127">Další informace o tom, jak určit kryptografický otisk pro certifikát, naleznete v tématu [How to: Načtení kryptografického otisku certifikátu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="12b01-127">For more information about how to determine the thumbprint for a certificate, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
         <span data-ttu-id="12b01-128">Následující příklad kódu používá nástroj [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) k určení umístění privátního klíče pro certifikát v `My` storu v `CurrentUser` s kryptografickým otiskem `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.</span><span class="sxs-lookup"><span data-stu-id="12b01-128">The following code example uses the [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool to determine the location of the private key for a certificate in the `My` store in `CurrentUser` with a thumbprint of `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.</span></span>  
  
        ```console
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4. <span data-ttu-id="12b01-129">Určete účet, pod kterým je WCF spuštěno.</span><span class="sxs-lookup"><span data-stu-id="12b01-129">Determine the account that WCF is running under.</span></span>  
  
         <span data-ttu-id="12b01-130">Následující tabulka podrobně popisuje účet, pod kterým je WCF spuštěno pro daný scénář.</span><span class="sxs-lookup"><span data-stu-id="12b01-130">The following table details the account under which WCF is running for a given scenario.</span></span>  
  
        |<span data-ttu-id="12b01-131">Scénář</span><span class="sxs-lookup"><span data-stu-id="12b01-131">Scenario</span></span>|<span data-ttu-id="12b01-132">Identita procesu</span><span class="sxs-lookup"><span data-stu-id="12b01-132">Process identity</span></span>|  
        |--------------|----------------------|  
        |<span data-ttu-id="12b01-133">Klient (aplikace konzoly nebo WinForms).</span><span class="sxs-lookup"><span data-stu-id="12b01-133">Client (console or WinForms application).</span></span>|<span data-ttu-id="12b01-134">Aktuálně přihlášený uživatel.</span><span class="sxs-lookup"><span data-stu-id="12b01-134">Currently logged in user.</span></span>|  
        |<span data-ttu-id="12b01-135">Služba, která je samostatně hostována.</span><span class="sxs-lookup"><span data-stu-id="12b01-135">Service that is self-hosted.</span></span>|<span data-ttu-id="12b01-136">Aktuálně přihlášený uživatel.</span><span class="sxs-lookup"><span data-stu-id="12b01-136">Currently logged in user.</span></span>|  
        |<span data-ttu-id="12b01-137">Služba, která je hostována ve službě IIS 6,0 (Windows Server 2003) nebo IIS 7,0 (Windows Vista).</span><span class="sxs-lookup"><span data-stu-id="12b01-137">Service that is hosted in IIS 6.0 (Windows Server 2003) or IIS 7.0 (Windows Vista).</span></span>|<span data-ttu-id="12b01-138">SÍŤOVÁ SLUŽBA</span><span class="sxs-lookup"><span data-stu-id="12b01-138">NETWORK SERVICE</span></span>|  
        |<span data-ttu-id="12b01-139">Služba, která je hostována ve službě IIS 5. X ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="12b01-139">Service that is hosted in IIS 5.X ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]).</span></span>|<span data-ttu-id="12b01-140">Ovládáno `<processModel>` prvkem v souboru Machine. config.</span><span class="sxs-lookup"><span data-stu-id="12b01-140">Controlled by the `<processModel>` element in the Machine.config file.</span></span> <span data-ttu-id="12b01-141">Výchozí účet je ASPNET.</span><span class="sxs-lookup"><span data-stu-id="12b01-141">The default account is ASPNET.</span></span>|  
  
    5. <span data-ttu-id="12b01-142">Udělte oprávnění ke čtení souboru, který obsahuje privátní klíč, k účtu, pod kterým běží WCF, pomocí nástroje, jako je Icacls. exe.</span><span class="sxs-lookup"><span data-stu-id="12b01-142">Grant read access to the file that contains the private key to the account that WCF is running under, using a tool such as icacls.exe.</span></span>  
  
         <span data-ttu-id="12b01-143">Následující příklad kódu upraví volitelný seznam řízení přístupu (DACL) pro zadaný soubor a udělí účtu síťové služby čtení (: R) přístup k souboru.</span><span class="sxs-lookup"><span data-stu-id="12b01-143">The following code example edits the discretionary access control list (DACL) for the specified file to grant the NETWORK SERVICE account read (:R) access to the file.</span></span>  
  
        ```console 
        icacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /grant "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a><span data-ttu-id="12b01-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="12b01-144">See also</span></span>

- [<span data-ttu-id="12b01-145">FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="12b01-145">FindPrivateKey</span></span>](../../../../docs/framework/wcf/samples/findprivatekey.md)
- [<span data-ttu-id="12b01-146">Postupy: Načtení kryptografického otisku certifikátu</span><span class="sxs-lookup"><span data-stu-id="12b01-146">How to: Retrieve the Thumbprint of a Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
- [<span data-ttu-id="12b01-147">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="12b01-147">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
