---
title: 'Postupy: vytváření dočasných certifikátů pro použití během vývoje.'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], creating temporary certificates
- temporary certificates [WCF]
ms.assetid: bc5f6637-5513-4d27-99bb-51aad7741e4a
ms.openlocfilehash: d3b051c7ea152606721388ea35b6f508eada1c5d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43524362"
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a><span data-ttu-id="84366-102">Postupy: vytváření dočasných certifikátů pro použití během vývoje.</span><span class="sxs-lookup"><span data-stu-id="84366-102">How to: Create Temporary Certificates for Use During Development</span></span>
<span data-ttu-id="84366-103">Při vývoji zabezpečenou službu nebo klienta s použitím Windows Communication Foundation (WCF), je často nutné zadat certifikát X.509, které se použijí jako přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="84366-103">When developing a secure service or client using Windows Communication Foundation (WCF), it is often necessary to supply an X.509 certificate to be used as a credential.</span></span> <span data-ttu-id="84366-104">Certifikát je obvykle součástí řetěz certifikátů s kořenovou autoritou nalezen v úložišti důvěryhodných kořenových certifikačních autorit počítače.</span><span class="sxs-lookup"><span data-stu-id="84366-104">The certificate typically is part of a chain of certificates with a root authority found in the Trusted Root Certification Authorities store of the computer.</span></span> <span data-ttu-id="84366-105">S řetěz certifikátů umožňuje určit obor sady certifikátů, kdy obvykle kořenová autorita je z vaší organizace nebo organizační jednotka.</span><span class="sxs-lookup"><span data-stu-id="84366-105">Having a certificate chain enables you to scope a set of certificates where typically the root authority is from your organization or business unit.</span></span> <span data-ttu-id="84366-106">Pro emulaci to při vývoji, vytvoříte dva certifikáty splňovat požadavky na zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="84366-106">To emulate this at development time, you can create two certificates to satisfy the security requirements.</span></span> <span data-ttu-id="84366-107">První je certifikát podepsaný svým držitelem, který je umístěn v úložišti Důvěryhodné kořenové certifikační autority, a druhý certifikát je vytvořený z první a je umístěn v osobním úložišti umístění místního počítače nebo osobním úložišti Aktuální umístění uživatele.</span><span class="sxs-lookup"><span data-stu-id="84366-107">The first is a self-signed certificate that is placed in the Trusted Root Certification Authorities store, and the second certificate is created from the first and is placed in either the Personal store of the Local Machine location, or the Personal store of the Current User location.</span></span> <span data-ttu-id="84366-108">Toto téma vás provede kroky k vytvoření těchto dvou certifikáty pomocí [Certificate Creation Tool (MakeCert.exe)](https://go.microsoft.com/fwlink/?LinkId=248185), která poskytuje [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] SDK.</span><span class="sxs-lookup"><span data-stu-id="84366-108">This topic walks through the steps to create these two certificates using the [Certificate Creation Tool (MakeCert.exe)](https://go.microsoft.com/fwlink/?LinkId=248185), which is provided by the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] SDK.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="84366-109">Certifikáty, které generuje nástroj pro vytváření certifikační jsou k dispozici pouze pro účely testování.</span><span class="sxs-lookup"><span data-stu-id="84366-109">The certificates the Certification Creation tool generates are provided for testing purposes only.</span></span> <span data-ttu-id="84366-110">Při nasazování služby ani klienta, nezapomeňte použít příslušný certifikát k dispozici certifikační autoritou.</span><span class="sxs-lookup"><span data-stu-id="84366-110">When deploying a service or client, be sure to use an appropriate certificate provided by a certification authority.</span></span> <span data-ttu-id="84366-111">To může být buď z [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] certifikátů serveru ve vaší organizaci nebo třetí strana.</span><span class="sxs-lookup"><span data-stu-id="84366-111">This could either be from a [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] certificate server in your organization or a third party.</span></span>  
>   
>  <span data-ttu-id="84366-112">Ve výchozím nastavení [Makecert.exe (Certificate Creation Tool)](https://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d) vytvoří certifikáty, jejichž kořenovou autoritou se nazývá "kořenový agentura **."**</span><span class="sxs-lookup"><span data-stu-id="84366-112">By default, the [Makecert.exe (Certificate Creation Tool)](https://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d) creates certificates whose root authority is called "Root Agency **."**</span></span> <span data-ttu-id="84366-113">Protože agentura"Root" není v úložišti důvěryhodných kořenových certifikačních autorit, díky tomu tyto certifikáty nezabezpečené.</span><span class="sxs-lookup"><span data-stu-id="84366-113">Because the "Root Agency" is not in the Trusted Root Certification Authorities store, this makes these certificates insecure.</span></span> <span data-ttu-id="84366-114">Vytváří se certifikát podepsaný svým držitelem, který je umístěn v kořenové certifikační autority úložiště vám umožní vytvořit prostředí pro vývoj, která lépe napodobuje prostředí pro nasazení.</span><span class="sxs-lookup"><span data-stu-id="84366-114">Creating a self-signed certificate that is placed in the Trusted Root Certification Authorities store enables you to create a development environment that more closely simulates your deployment environment.</span></span>  
  
 <span data-ttu-id="84366-115">Další informace o vytváření a používání certifikátů najdete v tématu [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="84366-115">For more information about creating and using certificates, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span> <span data-ttu-id="84366-116">Další informace o používání certifikátu jako přihlašovací údaje, najdete v části [zabezpečení služeb a klientů](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="84366-116">For more information about using a certificate as a credential, see [Securing Services and Clients](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).</span></span> <span data-ttu-id="84366-117">Kurz o pomocí technologie Authenticode Microsoftu, najdete v tématu [Authenticode přehledy a kurzy](https://go.microsoft.com/fwlink/?LinkId=88919).</span><span class="sxs-lookup"><span data-stu-id="84366-117">For a tutorial about using Microsoft Authenticode technology, see [Authenticode Overviews and Tutorials](https://go.microsoft.com/fwlink/?LinkId=88919).</span></span>  
  
### <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a><span data-ttu-id="84366-118">Vytvořit certifikát podepsaný svým držitelem kořenové autority a exportovat privátní klíč</span><span class="sxs-lookup"><span data-stu-id="84366-118">To create a self-signed root authority certificate and export the private key</span></span>  
  
1.  <span data-ttu-id="84366-119">Pomocí nástroje MakeCert.exe následující přepínače:</span><span class="sxs-lookup"><span data-stu-id="84366-119">Use the MakeCert.exe tool with the following switches:</span></span>  
  
    1.  <span data-ttu-id="84366-120">`-n` `subjectName`.</span><span class="sxs-lookup"><span data-stu-id="84366-120">`-n` `subjectName`.</span></span> <span data-ttu-id="84366-121">Určuje název předmětu.</span><span class="sxs-lookup"><span data-stu-id="84366-121">Specifies the subject name.</span></span> <span data-ttu-id="84366-122">V rámci konvence se jako předpona názvu subjektu s "CN =" pro "Běžný název".</span><span class="sxs-lookup"><span data-stu-id="84366-122">The convention is to prefix the subject name with "CN = " for "Common Name".</span></span>  
  
    2.  <span data-ttu-id="84366-123">`-r`.</span><span class="sxs-lookup"><span data-stu-id="84366-123">`-r`.</span></span> <span data-ttu-id="84366-124">Určuje, zda certifikát podepsaný svým držitelem.</span><span class="sxs-lookup"><span data-stu-id="84366-124">Specifies that the certificate will be self-signed.</span></span>  
  
    3.  <span data-ttu-id="84366-125">`-sv` `privateKeyFile`.</span><span class="sxs-lookup"><span data-stu-id="84366-125">`-sv` `privateKeyFile`.</span></span> <span data-ttu-id="84366-126">Určuje soubor, který obsahuje kontejner soukromého klíče.</span><span class="sxs-lookup"><span data-stu-id="84366-126">Specifies the file that contains the private key container.</span></span>  
  
     <span data-ttu-id="84366-127">Například následující příkaz vytvoří certifikát podepsaný svým držitelem se název předmětu "CN = TempCA."</span><span class="sxs-lookup"><span data-stu-id="84366-127">For example, the following command creates a self-signed certificate with a subject name of "CN=TempCA."</span></span>  
  
    ```  
    makecert -n "CN=TempCA" -r -sv TempCA.pvk TempCA.cer  
    ```  
  
     <span data-ttu-id="84366-128">Zobrazí se výzva k zadání hesla k ochraně soukromého klíče.</span><span class="sxs-lookup"><span data-stu-id="84366-128">You will be prompted to provide a password to protect the private key.</span></span> <span data-ttu-id="84366-129">Toto heslo se vyžaduje při vytvoření certifikátu podepsány tento kořenový certifikát.</span><span class="sxs-lookup"><span data-stu-id="84366-129">This password is required when creating a certificate signed by this root certificate.</span></span>  
  
### <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a><span data-ttu-id="84366-130">Chcete-li vytvořit nový certifikát podepsaný certifikátem kořenového certifikátu autority</span><span class="sxs-lookup"><span data-stu-id="84366-130">To create a new certificate signed by a root authority certificate</span></span>  
  
1.  <span data-ttu-id="84366-131">Pomocí nástroje MakeCert.exe následující přepínače:</span><span class="sxs-lookup"><span data-stu-id="84366-131">Use the MakeCert.exe tool with the following switches:</span></span>  
  
    1.  <span data-ttu-id="84366-132">`-sk` `subjectKey`.</span><span class="sxs-lookup"><span data-stu-id="84366-132">`-sk` `subjectKey`.</span></span> <span data-ttu-id="84366-133">Umístění kontejneru klíče předmětu, který obsahuje privátní klíč.</span><span class="sxs-lookup"><span data-stu-id="84366-133">The location of the subject's key container that holds the private key.</span></span> <span data-ttu-id="84366-134">Pokud kontejner klíčů neexistuje, vytvoří se.</span><span class="sxs-lookup"><span data-stu-id="84366-134">If a key container does not exist, one is created.</span></span> <span data-ttu-id="84366-135">Pokud žádná z možností – sk nebo - sv se používá, se standardně vytvoří kontejner klíče se nazývá JoeSoft.</span><span class="sxs-lookup"><span data-stu-id="84366-135">If neither of the -sk or -sv options is used, a key container called JoeSoft is created by default.</span></span>  
  
    2.  <span data-ttu-id="84366-136">`-n` `subjectName`.</span><span class="sxs-lookup"><span data-stu-id="84366-136">`-n` `subjectName`.</span></span> <span data-ttu-id="84366-137">Určuje název předmětu.</span><span class="sxs-lookup"><span data-stu-id="84366-137">Specifies the subject name.</span></span> <span data-ttu-id="84366-138">V rámci konvence se jako předpona názvu subjektu s "CN =" pro "Běžný název".</span><span class="sxs-lookup"><span data-stu-id="84366-138">The convention is to prefix the subject name with "CN = " for "Common Name".</span></span>  
  
    3.  <span data-ttu-id="84366-139">`-iv` `issuerKeyFile`.</span><span class="sxs-lookup"><span data-stu-id="84366-139">`-iv` `issuerKeyFile`.</span></span> <span data-ttu-id="84366-140">Určuje soubor privátního klíče vystavitele.</span><span class="sxs-lookup"><span data-stu-id="84366-140">Specifies the issuer's private key file.</span></span>  
  
    4.  <span data-ttu-id="84366-141">`-ic` `issuerCertFile`.</span><span class="sxs-lookup"><span data-stu-id="84366-141">`-ic` `issuerCertFile`.</span></span> <span data-ttu-id="84366-142">Určuje umístění certifikátu vystavitele.</span><span class="sxs-lookup"><span data-stu-id="84366-142">Specifies the location of the issuer's certificate.</span></span>  
  
     <span data-ttu-id="84366-143">Například následující příkaz vytvoří certifikát podepsaný službou `TempCA` kořenový certifikát autority s názvem subjektu `"CN=SignedByCA"` pomocí soukromého klíče vydavatele.</span><span class="sxs-lookup"><span data-stu-id="84366-143">For example, the following command creates a certificate signed by the `TempCA` root authority certificate with a subject name of `"CN=SignedByCA"` using the private key of the issuer.</span></span>  
  
    ```  
    makecert -sk SignedByCA -iv TempCA.pvk -n "CN=SignedByCA" -ic TempCA.cer SignedByCA.cer -sr currentuser -ss My  
    ```  
  
## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a><span data-ttu-id="84366-144">Instalace certifikátu v důvěryhodné Store autority certifikační kořenové</span><span class="sxs-lookup"><span data-stu-id="84366-144">Installing a Certificate in the Trusted Root Certification Authorities Store</span></span>  
 <span data-ttu-id="84366-145">Jakmile se vytvoří certifikát podepsaný svým držitelem, můžete nainstalovat v úložišti Důvěryhodné kořenové certifikační autority.</span><span class="sxs-lookup"><span data-stu-id="84366-145">Once a self-signed certificate is created, you can install it in the Trusted Root Certification Authorities store.</span></span> <span data-ttu-id="84366-146">Všechny certifikáty, které jsou podepsány pomocí certifikátu v tomto okamžiku jsou důvěryhodné počítače.</span><span class="sxs-lookup"><span data-stu-id="84366-146">Any certificates that are signed with the certificate at this point are trusted by the computer.</span></span> <span data-ttu-id="84366-147">Z tohoto důvodu se odstraní certifikát z úložiště, jakmile ho už nepotřebují.</span><span class="sxs-lookup"><span data-stu-id="84366-147">For this reason, delete the certificate from the store as soon as you no longer need it.</span></span> <span data-ttu-id="84366-148">Při odstranění tento kořenový certifikát autority stane neoprávněné všechny certifikáty, které s ním podepsané.</span><span class="sxs-lookup"><span data-stu-id="84366-148">When you delete this root authority certificate, all other certificates that signed with it become unauthorized.</span></span> <span data-ttu-id="84366-149">Kořenových certifikátů úřadu slouží jednoduše jako mechanismus, kterým skupinu certifikátů můžete zařadit do oboru podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="84366-149">Root authority certificates are simply a mechanism whereby a group of certificates can be scoped as necessary.</span></span> <span data-ttu-id="84366-150">Třeba aplikace peer-to-peer, není obvykle nutné pro kořenovou autoritou vzhledem k tomu, že důvěřujete identity individuální uživatel jednoduše podle jeho zadaný certifikát.</span><span class="sxs-lookup"><span data-stu-id="84366-150">For example, in peer-to-peer applications, there is typically no need for a root authority because you simply trust the identity of an individual by its supplied certificate.</span></span>  
  
#### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a><span data-ttu-id="84366-151">Chcete-li nainstalovat certifikát podepsaný svým držitelem v důvěryhodných kořenových certifikačních autorit</span><span class="sxs-lookup"><span data-stu-id="84366-151">To install a self-signed certificate in the Trusted Root Certification Authorities</span></span>  
  
1.  <span data-ttu-id="84366-152">Otevřete modul snap-in certifikátu.</span><span class="sxs-lookup"><span data-stu-id="84366-152">Open the certificate snap-in.</span></span> <span data-ttu-id="84366-153">Další informace najdete v tématu [postupy: zobrazení certifikátů pomocí modulu Snap-in konzoly MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="84366-153">For more information, see [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>  
  
2.  <span data-ttu-id="84366-154">Otevřete složku, která se má certifikát uložit buď **místního počítače** nebo **aktuálního uživatele**.</span><span class="sxs-lookup"><span data-stu-id="84366-154">Open the folder to store the certificate, either the **Local Computer** or the **Current User**.</span></span>  
  
3.  <span data-ttu-id="84366-155">Otevřít **důvěryhodných kořenových certifikačních autorit** složky.</span><span class="sxs-lookup"><span data-stu-id="84366-155">Open the **Trusted Root Certification Authorities** folder.</span></span>  
  
4.  <span data-ttu-id="84366-156">Klikněte pravým tlačítkem na **certifikáty** složky a klikněte na tlačítko **všechny úkoly**, pak klikněte na tlačítko **Import**.</span><span class="sxs-lookup"><span data-stu-id="84366-156">Right-click the **Certificates** folder and click **All Tasks**, then click **Import**.</span></span>  
  
5.  <span data-ttu-id="84366-157">Na obrazovce průvodce podle pokynů TempCa.cer naimportujte do úložiště.</span><span class="sxs-lookup"><span data-stu-id="84366-157">Follow the on-screen wizard instructions to import the TempCa.cer into the store.</span></span>  
  
## <a name="using-certificates-with-wcf"></a><span data-ttu-id="84366-158">Použití certifikátů s použitím technologie WCF</span><span class="sxs-lookup"><span data-stu-id="84366-158">Using Certificates With WCF</span></span>  
 <span data-ttu-id="84366-159">Po nastavení dočasných certifikátů můžete je použít pro vývoj řešení pro WCF, které určují certifikáty jako typ pověření klienta.</span><span class="sxs-lookup"><span data-stu-id="84366-159">Once you have set up the temporary certificates, you can use them to develop WCF solutions that specify certificates as a client credential type.</span></span> <span data-ttu-id="84366-160">Například následující XML konfigurace určuje zabezpečení zpráv a certifikát jako typ pověření klienta.</span><span class="sxs-lookup"><span data-stu-id="84366-160">For example, the following XML configuration specifies message security and a certificate as the client credential type.</span></span>  
  
#### <a name="to-specify-a-certificate-as-the-client-credential-type"></a><span data-ttu-id="84366-161">Chcete-li určit certifikát jako typ pověření klienta</span><span class="sxs-lookup"><span data-stu-id="84366-161">To specify a certificate as the client credential type</span></span>  
  
-   <span data-ttu-id="84366-162">V konfiguračním souboru pro službu použijte následující kód XML pro nastavení režimu zabezpečení zpráv a typu pověření klienta k certifikátu.</span><span class="sxs-lookup"><span data-stu-id="84366-162">In the configuration file for a service, use the following XML to set the security mode to message, and the client credential type to certificate.</span></span>  
  
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
  
 <span data-ttu-id="84366-163">V konfiguračním souboru pro klienta použijte následující kód XML k určení, že certifikát je nalezena v úložišti uživatele a najdete tak, že pole SubjectName pro hodnotu "CohoWinery."</span><span class="sxs-lookup"><span data-stu-id="84366-163">In the configuration file for a client, use the following XML to specify that the certificate is found in the user’s store, and can be found by searching the SubjectName field for the value "CohoWinery."</span></span>  
  
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
  
 <span data-ttu-id="84366-164">Další informace o používání certifikátů ve službě WCF najdete v tématu [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="84366-164">For more information about using certificates in WCF, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="84366-165">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="84366-165">.NET Framework Security</span></span>  
 <span data-ttu-id="84366-166">Nezapomeňte odstranit všechny dočasné kořenových certifikátů úřadu z **důvěryhodných kořenových certifikačních autorit** a **osobní** složek tak, že kliknete pravým tlačítkem certifikát, pak kliknutím na  **Odstranit**.</span><span class="sxs-lookup"><span data-stu-id="84366-166">Be sure to delete any temporary root authority certificates from the **Trusted Root Certification Authorities** and **Personal** folders by right-clicking the certificate, then clicking **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84366-167">Viz také</span><span class="sxs-lookup"><span data-stu-id="84366-167">See Also</span></span>  
 [<span data-ttu-id="84366-168">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="84366-168">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="84366-169">Postupy: Zobrazení certifikátů pomocí modulu snap-in konzoly MMC</span><span class="sxs-lookup"><span data-stu-id="84366-169">How to: View Certificates with the MMC Snap-in</span></span>](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)  
 [<span data-ttu-id="84366-170">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="84366-170">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
