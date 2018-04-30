---
title: 'Postupy: vytváření dočasných certifikátů pro použití při vývoji'
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
- certificates [WCF], creating temporary certificates
- temporary certificates [WCF]
ms.assetid: bc5f6637-5513-4d27-99bb-51aad7741e4a
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f5a096fd6e052fc744af5cee1ab0d322e1daafe6
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a><span data-ttu-id="62981-102">Postupy: vytváření dočasných certifikátů pro použití při vývoji</span><span class="sxs-lookup"><span data-stu-id="62981-102">How to: Create Temporary Certificates for Use During Development</span></span>
<span data-ttu-id="62981-103">Při vývoji zabezpečení služby nebo klienta s použitím [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], je často potřeba zadat certifikát X.509, který se má použít jako pověření.</span><span class="sxs-lookup"><span data-stu-id="62981-103">When developing a secure service or client using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], it is often necessary to supply an X.509 certificate to be used as a credential.</span></span> <span data-ttu-id="62981-104">Certifikát je obvykle součástí řetěz certifikátů s kořenovou autoritou nalezen v úložišti Důvěryhodné kořenové certifikační autority počítače.</span><span class="sxs-lookup"><span data-stu-id="62981-104">The certificate typically is part of a chain of certificates with a root authority found in the Trusted Root Certification Authorities store of the computer.</span></span> <span data-ttu-id="62981-105">S řetěz certifikátů umožňuje určit obor sadu certifikáty, které obvykle kořenovou autoritou je z vaší organizace nebo organizační jednotka.</span><span class="sxs-lookup"><span data-stu-id="62981-105">Having a certificate chain enables you to scope a set of certificates where typically the root authority is from your organization or business unit.</span></span> <span data-ttu-id="62981-106">To emulovat v době vývoje, můžete vytvořit dva certifikáty splňovat požadavky na zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="62981-106">To emulate this at development time, you can create two certificates to satisfy the security requirements.</span></span> <span data-ttu-id="62981-107">První je certifikát podepsaný svým držitelem, který je umístěn v úložišti důvěryhodných kořenových certifikačních autorit a druhý certifikát je vytvořený z první a je umístěn v osobním úložišti umístění místního počítače nebo osobním úložišti Aktuální umístění uživatele.</span><span class="sxs-lookup"><span data-stu-id="62981-107">The first is a self-signed certificate that is placed in the Trusted Root Certification Authorities store, and the second certificate is created from the first and is placed in either the Personal store of the Local Machine location, or the Personal store of the Current User location.</span></span> <span data-ttu-id="62981-108">Toto téma vás provede kroky k vytvoření těchto dvou certifikátů pomocí [nástroje vytvoření certifikátu (MakeCert.exe)](http://go.microsoft.com/fwlink/?LinkId=248185), poskytnutá [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] SDK.</span><span class="sxs-lookup"><span data-stu-id="62981-108">This topic walks through the steps to create these two certificates using the [Certificate Creation Tool (MakeCert.exe)](http://go.microsoft.com/fwlink/?LinkId=248185), which is provided by the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] SDK.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="62981-109">Certifikáty, které generuje nástroj pro vytváření certifikační jsou k dispozici jenom pro účely testování.</span><span class="sxs-lookup"><span data-stu-id="62981-109">The certificates the Certification Creation tool generates are provided for testing purposes only.</span></span> <span data-ttu-id="62981-110">Pokud nasazujete službu nebo klienta, je nutné používat příslušný certifikát od certifikační autority.</span><span class="sxs-lookup"><span data-stu-id="62981-110">When deploying a service or client, be sure to use an appropriate certificate provided by a certification authority.</span></span> <span data-ttu-id="62981-111">To může být buď z [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] certifikátů serveru ve vaší organizaci nebo třetí strany.</span><span class="sxs-lookup"><span data-stu-id="62981-111">This could either be from a [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] certificate server in your organization or a third party.</span></span>  
>   
>  <span data-ttu-id="62981-112">Ve výchozím nastavení [Makecert.exe (nástroj pro vytvoření certifikátu)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d) vytvoří certifikáty, jejichž kořenové autority se označuje jako "kořenový agentura **."**</span><span class="sxs-lookup"><span data-stu-id="62981-112">By default, the [Makecert.exe (Certificate Creation Tool)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d) creates certificates whose root authority is called "Root Agency **."**</span></span> <span data-ttu-id="62981-113">Protože agentura"kořenový" není v úložišti důvěryhodných kořenových certifikačních autorit, díky tyto certifikáty nezabezpečené.</span><span class="sxs-lookup"><span data-stu-id="62981-113">Because the "Root Agency" is not in the Trusted Root Certification Authorities store, this makes these certificates insecure.</span></span> <span data-ttu-id="62981-114">Vytvořit certifikát podepsaný svým držitelem, který je umístěn v důvěryhodných kořenových certifikačních autorit úložiště můžete vytvořit prostředí pro vývoj, která simuluje přesněji prostředí pro nasazení.</span><span class="sxs-lookup"><span data-stu-id="62981-114">Creating a self-signed certificate that is placed in the Trusted Root Certification Authorities store enables you to create a development environment that more closely simulates your deployment environment.</span></span>  
  
 <span data-ttu-id="62981-115">Další informace o vytváření a používání certifikátů najdete v tématu [práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="62981-115">For more information about creating and using certificates, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span> <span data-ttu-id="62981-116">Další informace o používání certifikátu jako pověření najdete v tématu [zabezpečení služeb a klientů](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="62981-116">For more information about using a certificate as a credential, see [Securing Services and Clients](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).</span></span> <span data-ttu-id="62981-117">Podívejte se kurz o pomocí technologie Microsoft Authenticode [Authenticode přehledy a kurzy](http://go.microsoft.com/fwlink/?LinkId=88919).</span><span class="sxs-lookup"><span data-stu-id="62981-117">For a tutorial about using Microsoft Authenticode technology, see [Authenticode Overviews and Tutorials](http://go.microsoft.com/fwlink/?LinkId=88919).</span></span>  
  
### <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a><span data-ttu-id="62981-118">Chcete-li vytvořit certifikát podepsaný svým držitelem kořenové autority a exportovat soukromý klíč</span><span class="sxs-lookup"><span data-stu-id="62981-118">To create a self-signed root authority certificate and export the private key</span></span>  
  
1.  <span data-ttu-id="62981-119">Pomocí nástroje MakeCert.exe s následující přepínače:</span><span class="sxs-lookup"><span data-stu-id="62981-119">Use the MakeCert.exe tool with the following switches:</span></span>  
  
    1.  <span data-ttu-id="62981-120">`-n` `subjectName`.</span><span class="sxs-lookup"><span data-stu-id="62981-120">`-n` `subjectName`.</span></span> <span data-ttu-id="62981-121">Určuje název předmětu.</span><span class="sxs-lookup"><span data-stu-id="62981-121">Specifies the subject name.</span></span> <span data-ttu-id="62981-122">Konvence je jako předpona názvu subjektu s "CN =" pro "Běžný název".</span><span class="sxs-lookup"><span data-stu-id="62981-122">The convention is to prefix the subject name with "CN = " for "Common Name".</span></span>  
  
    2.  <span data-ttu-id="62981-123">`-r`.</span><span class="sxs-lookup"><span data-stu-id="62981-123">`-r`.</span></span> <span data-ttu-id="62981-124">Určuje, že bude certifikát podepsaný svým držitelem.</span><span class="sxs-lookup"><span data-stu-id="62981-124">Specifies that the certificate will be self-signed.</span></span>  
  
    3.  <span data-ttu-id="62981-125">`-sv` `privateKeyFile`.</span><span class="sxs-lookup"><span data-stu-id="62981-125">`-sv` `privateKeyFile`.</span></span> <span data-ttu-id="62981-126">Určuje soubor, který obsahuje kontejner soukromého klíče.</span><span class="sxs-lookup"><span data-stu-id="62981-126">Specifies the file that contains the private key container.</span></span>  
  
     <span data-ttu-id="62981-127">Například následující příkaz vytvoří certifikát podepsaný svým držitelem s názvem subjektu "CN = TempCA."</span><span class="sxs-lookup"><span data-stu-id="62981-127">For example, the following command creates a self-signed certificate with a subject name of "CN=TempCA."</span></span>  
  
    ```  
    makecert -n "CN=TempCA" -r -sv TempCA.pvk TempCA.cer  
    ```  
  
     <span data-ttu-id="62981-128">Zobrazí se výzva k zadání hesla k ochraně soukromého klíče.</span><span class="sxs-lookup"><span data-stu-id="62981-128">You will be prompted to provide a password to protect the private key.</span></span> <span data-ttu-id="62981-129">Heslo je vyžadováno, při vytváření certifikát podepsaný tento kořenový certifikát.</span><span class="sxs-lookup"><span data-stu-id="62981-129">This password is required when creating a certificate signed by this root certificate.</span></span>  
  
### <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a><span data-ttu-id="62981-130">Chcete-li vytvořit nový certifikát podepsaný službou kořenového certifikátu autority</span><span class="sxs-lookup"><span data-stu-id="62981-130">To create a new certificate signed by a root authority certificate</span></span>  
  
1.  <span data-ttu-id="62981-131">Pomocí nástroje MakeCert.exe s následující přepínače:</span><span class="sxs-lookup"><span data-stu-id="62981-131">Use the MakeCert.exe tool with the following switches:</span></span>  
  
    1.  <span data-ttu-id="62981-132">`-sk` `subjectKey`.</span><span class="sxs-lookup"><span data-stu-id="62981-132">`-sk` `subjectKey`.</span></span> <span data-ttu-id="62981-133">Umístění kontejneru klíčů daného subjektu, který obsahuje soukromý klíč.</span><span class="sxs-lookup"><span data-stu-id="62981-133">The location of the subject's key container that holds the private key.</span></span> <span data-ttu-id="62981-134">Pokud kontejner klíčů neexistuje, je vytvořen jeden.</span><span class="sxs-lookup"><span data-stu-id="62981-134">If a key container does not exist, one is created.</span></span> <span data-ttu-id="62981-135">Pokud žádná z možností -sk nebo - sv se používá, se ve výchozím nastavení vytvoří kontejner klíčů názvem JoeSoft.</span><span class="sxs-lookup"><span data-stu-id="62981-135">If neither of the -sk or -sv options is used, a key container called JoeSoft is created by default.</span></span>  
  
    2.  <span data-ttu-id="62981-136">`-n` `subjectName`.</span><span class="sxs-lookup"><span data-stu-id="62981-136">`-n` `subjectName`.</span></span> <span data-ttu-id="62981-137">Určuje název předmětu.</span><span class="sxs-lookup"><span data-stu-id="62981-137">Specifies the subject name.</span></span> <span data-ttu-id="62981-138">Konvence je jako předpona názvu subjektu s "CN =" pro "Běžný název".</span><span class="sxs-lookup"><span data-stu-id="62981-138">The convention is to prefix the subject name with "CN = " for "Common Name".</span></span>  
  
    3.  <span data-ttu-id="62981-139">`-iv` `issuerKeyFile`.</span><span class="sxs-lookup"><span data-stu-id="62981-139">`-iv` `issuerKeyFile`.</span></span> <span data-ttu-id="62981-140">Určuje soubor privátního klíče vystavitele.</span><span class="sxs-lookup"><span data-stu-id="62981-140">Specifies the issuer's private key file.</span></span>  
  
    4.  <span data-ttu-id="62981-141">`-ic` `issuerCertFile`.</span><span class="sxs-lookup"><span data-stu-id="62981-141">`-ic` `issuerCertFile`.</span></span> <span data-ttu-id="62981-142">Určuje umístění vystavitele certifikátu.</span><span class="sxs-lookup"><span data-stu-id="62981-142">Specifies the location of the issuer's certificate.</span></span>  
  
     <span data-ttu-id="62981-143">Například následující příkaz vytvoří certifikát podepsaný službou `TempCA` kořenové autority s názvem subjektu `"CN=SignedByCA"` pomocí soukromého klíče vystavitele.</span><span class="sxs-lookup"><span data-stu-id="62981-143">For example, the following command creates a certificate signed by the `TempCA` root authority certificate with a subject name of `"CN=SignedByCA"` using the private key of the issuer.</span></span>  
  
    ```  
    makecert -sk SignedByCA -iv TempCA.pvk -n "CN=SignedByCA" -ic TempCA.cer SignedByCA.cer -sr currentuser -ss My  
    ```  
  
## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a><span data-ttu-id="62981-144">Instalace certifikátu do důvěryhodného úložiště kořenové certifikační autority</span><span class="sxs-lookup"><span data-stu-id="62981-144">Installing a Certificate in the Trusted Root Certification Authorities Store</span></span>  
 <span data-ttu-id="62981-145">Jakmile se vytvoří certifikát podepsaný svým držitelem, můžete ji nainstalovat v úložišti důvěryhodných kořenových certifikačních autorit.</span><span class="sxs-lookup"><span data-stu-id="62981-145">Once a self-signed certificate is created, you can install it in the Trusted Root Certification Authorities store.</span></span> <span data-ttu-id="62981-146">Všechny certifikáty, které jsou podepsané certifikátem v tomto okamžiku jsou důvěryhodné počítače.</span><span class="sxs-lookup"><span data-stu-id="62981-146">Any certificates that are signed with the certificate at this point are trusted by the computer.</span></span> <span data-ttu-id="62981-147">Z tohoto důvodu odstraňte certifikát z úložiště, jakmile ji už nepotřebujete.</span><span class="sxs-lookup"><span data-stu-id="62981-147">For this reason, delete the certificate from the store as soon as you no longer need it.</span></span> <span data-ttu-id="62981-148">Při odstranění tohoto kořenového certifikátu autority, stane neoprávněným všechny další certifikáty, které s ním podepsané.</span><span class="sxs-lookup"><span data-stu-id="62981-148">When you delete this root authority certificate, all other certificates that signed with it become unauthorized.</span></span> <span data-ttu-id="62981-149">Certifikáty kořenové autority se jednoduše mechanismus které může být skupinu certifikáty vymezena podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="62981-149">Root authority certificates are simply a mechanism whereby a group of certificates can be scoped as necessary.</span></span> <span data-ttu-id="62981-150">Například v aplikacích peer-to-peer, je obvykle není nutné mít kořenovou autoritou vzhledem k tomu, že důvěřujete identitě osoby, jednoduše podle jeho poskytnutý certifikát.</span><span class="sxs-lookup"><span data-stu-id="62981-150">For example, in peer-to-peer applications, there is typically no need for a root authority because you simply trust the identity of an individual by its supplied certificate.</span></span>  
  
#### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a><span data-ttu-id="62981-151">Chcete-li nainstalovat certifikát podepsaný svým držitelem v důvěryhodné kořenové certifikační autority</span><span class="sxs-lookup"><span data-stu-id="62981-151">To install a self-signed certificate in the Trusted Root Certification Authorities</span></span>  
  
1.  <span data-ttu-id="62981-152">Otevřete modul snap-in certifikátů.</span><span class="sxs-lookup"><span data-stu-id="62981-152">Open the certificate snap-in.</span></span> <span data-ttu-id="62981-153">Další informace najdete v tématu [postupy: zobrazení certifikátů pomocí modulu Snap-in konzoly MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="62981-153">For more information, see [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>  
  
2.  <span data-ttu-id="62981-154">Otevřete složku, která se má certifikát uložit buď **místního počítače** nebo **aktuální uživatel**.</span><span class="sxs-lookup"><span data-stu-id="62981-154">Open the folder to store the certificate, either the **Local Computer** or the **Current User**.</span></span>  
  
3.  <span data-ttu-id="62981-155">Otevřete **důvěryhodné kořenové certifikační autority** složky.</span><span class="sxs-lookup"><span data-stu-id="62981-155">Open the **Trusted Root Certification Authorities** folder.</span></span>  
  
4.  <span data-ttu-id="62981-156">Klikněte pravým tlačítkem myši **certifikáty** složky a klikněte na tlačítko **všechny úlohy**, pak klikněte na tlačítko **Import**.</span><span class="sxs-lookup"><span data-stu-id="62981-156">Right-click the **Certificates** folder and click **All Tasks**, then click **Import**.</span></span>  
  
5.  <span data-ttu-id="62981-157">Na obrazovce průvodce podle pokynů k importu TempCa.cer do úložiště.</span><span class="sxs-lookup"><span data-stu-id="62981-157">Follow the on-screen wizard instructions to import the TempCa.cer into the store.</span></span>  
  
## <a name="using-certificates-with-wcf"></a><span data-ttu-id="62981-158">Použití certifikátů s WCF</span><span class="sxs-lookup"><span data-stu-id="62981-158">Using Certificates With WCF</span></span>  
 <span data-ttu-id="62981-159">Jakmile jste nastavili dočasné certifikáty, můžete je používat pro vývoj řešení WCF, které určují certifikáty jako typ pověření klienta.</span><span class="sxs-lookup"><span data-stu-id="62981-159">Once you have set up the temporary certificates, you can use them to develop WCF solutions that specify certificates as a client credential type.</span></span> <span data-ttu-id="62981-160">Například následující konfigurační soubor XML určuje zabezpečení zpráv a certifikátu jako typ pověření klienta.</span><span class="sxs-lookup"><span data-stu-id="62981-160">For example, the following XML configuration specifies message security and a certificate as the client credential type.</span></span>  
  
#### <a name="to-specify-a-certificate-as-the-client-credential-type"></a><span data-ttu-id="62981-161">K určení certifikátu jako typ pověření klienta</span><span class="sxs-lookup"><span data-stu-id="62981-161">To specify a certificate as the client credential type</span></span>  
  
-   <span data-ttu-id="62981-162">V konfiguračním souboru pro službu použijte následující kód XML nastavení režimu zabezpečení na zprávu a typ pověření klienta k certifikátu.</span><span class="sxs-lookup"><span data-stu-id="62981-162">In the configuration file for a service, use the following XML to set the security mode to message, and the client credential type to certificate.</span></span>  
  
    ```xml  
    <bindings>       
      <wsHttpBinding>  
        <binding name="CertificateForClient">  
          <security>  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    ```  
  
 <span data-ttu-id="62981-163">V konfiguračním souboru pro klienta použijte následující kód XML k určení, že je certifikát nalezen v úložišti uživatele a můžete najít tak, že SubjectName pole pro tuto hodnotu "CohoWinery."</span><span class="sxs-lookup"><span data-stu-id="62981-163">In the configuration file for a client, use the following XML to specify that the certificate is found in the user’s store, and can be found by searching the SubjectName field for the value "CohoWinery."</span></span>  
  
```xml  
<behaviors>  
  <endpointBehaviors>  
    <behavior name="CertForClient">  
      <clientCredentials>  
        <clientCertificate findValue="CohoWinery" x509FindType="FindBySubjectName" />  
       </clientCredentials>  
     </behavior>  
   </endpointBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="62981-164">Další informace o používání certifikátů ve službě WCF najdete v tématu [práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="62981-164">For more information about using certificates in WCF, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="62981-165">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="62981-165">.NET Framework Security</span></span>  
 <span data-ttu-id="62981-166">Nezapomeňte odstranit všechny dočasné kořenových certifikátů úřadu z **důvěryhodné kořenové certifikační autority** a **osobní** složky tak, že kliknete pravým tlačítkem na certifikát, pak kliknutím na tlačítko  **Odstranit**.</span><span class="sxs-lookup"><span data-stu-id="62981-166">Be sure to delete any temporary root authority certificates from the **Trusted Root Certification Authorities** and **Personal** folders by right-clicking the certificate, then clicking **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62981-167">Viz také</span><span class="sxs-lookup"><span data-stu-id="62981-167">See Also</span></span>  
 [<span data-ttu-id="62981-168">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="62981-168">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="62981-169">Postupy: Zobrazení certifikátů pomocí modulu snap-in konzoly MMC</span><span class="sxs-lookup"><span data-stu-id="62981-169">How to: View Certificates with the MMC Snap-in</span></span>](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)  
 [<span data-ttu-id="62981-170">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="62981-170">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
