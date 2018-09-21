---
title: 'Postupy: vytváření dočasných certifikátů pro použití během vývoje.'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], creating temporary certificates
- temporary certificates [WCF]
ms.assetid: bc5f6637-5513-4d27-99bb-51aad7741e4a
ms.openlocfilehash: 2d0301b040d0fd9865eaf5c3f96fe320ccfd8488
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46485308"
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a><span data-ttu-id="fca48-102">Postupy: vytváření dočasných certifikátů pro použití během vývoje.</span><span class="sxs-lookup"><span data-stu-id="fca48-102">How to: Create Temporary Certificates for Use During Development</span></span>

<span data-ttu-id="fca48-103">Při vývoji zabezpečenou službu nebo klienta s použitím Windows Communication Foundation (WCF), je často nutné zadat certifikát X.509, které se použijí jako přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="fca48-103">When developing a secure service or client using Windows Communication Foundation (WCF), it is often necessary to supply an X.509 certificate to be used as a credential.</span></span> <span data-ttu-id="fca48-104">Certifikát je obvykle součástí řetěz certifikátů s kořenovou autoritou nalezen v úložišti důvěryhodných kořenových certifikačních autorit počítače.</span><span class="sxs-lookup"><span data-stu-id="fca48-104">The certificate typically is part of a chain of certificates with a root authority found in the Trusted Root Certification Authorities store of the computer.</span></span> <span data-ttu-id="fca48-105">S řetěz certifikátů umožňuje určit obor sady certifikátů, kdy obvykle kořenová autorita je z vaší organizace nebo organizační jednotka.</span><span class="sxs-lookup"><span data-stu-id="fca48-105">Having a certificate chain enables you to scope a set of certificates where typically the root authority is from your organization or business unit.</span></span> <span data-ttu-id="fca48-106">Pro emulaci to při vývoji, vytvoříte dva certifikáty splňovat požadavky na zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="fca48-106">To emulate this at development time, you can create two certificates to satisfy the security requirements.</span></span> <span data-ttu-id="fca48-107">První je certifikát podepsaný svým držitelem, který je umístěn v úložišti Důvěryhodné kořenové certifikační autority, a druhý certifikát je vytvořený z první a je umístěn v osobním úložišti umístění místního počítače nebo osobním úložišti Aktuální umístění uživatele.</span><span class="sxs-lookup"><span data-stu-id="fca48-107">The first is a self-signed certificate that is placed in the Trusted Root Certification Authorities store, and the second certificate is created from the first and is placed in either the Personal store of the Local Machine location, or the Personal store of the Current User location.</span></span> <span data-ttu-id="fca48-108">Toto téma vás provede kroky k vytvoření těchto dvou certifikátů pomocí Powershellu [New-SelfSignedCertificate)](/powershell/module/pkiclient/new-selfsignedcertificate) rutiny.</span><span class="sxs-lookup"><span data-stu-id="fca48-108">This topic walks through the steps to create these two certificates using the Powershell [New-SelfSignedCertificate)](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fca48-109">Certifikáty, které rutina New-SelfSignedCertificate generuje jsou k dispozici pouze pro účely testování.</span><span class="sxs-lookup"><span data-stu-id="fca48-109">The certificates that the New-SelfSignedCertificate cmdlet generates are provided for testing purposes only.</span></span> <span data-ttu-id="fca48-110">Při nasazování služby ani klienta, nezapomeňte použít příslušný certifikát k dispozici certifikační autoritou.</span><span class="sxs-lookup"><span data-stu-id="fca48-110">When deploying a service or client, be sure to use an appropriate certificate provided by a certification authority.</span></span> <span data-ttu-id="fca48-111">To může být z certifikačního serveru Windows Server ve vaší organizaci nebo třetí strana.</span><span class="sxs-lookup"><span data-stu-id="fca48-111">This could either be from a Windows Server certificate server in your organization or a third party.</span></span>
>
> <span data-ttu-id="fca48-112">Ve výchozím nastavení [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) rutina vytvoří certifikáty, které jsou podepsané svým držitelem a tyto certifikáty jsou nezabezpečené.</span><span class="sxs-lookup"><span data-stu-id="fca48-112">By default, the [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet creates certificates that are self-signed and these certificates are insecure.</span></span> <span data-ttu-id="fca48-113">Umístění certifikáty podepsané svým držitelem v důvěryhodných kořenových certifikačních autorit úložiště vám umožní vytvářet prostředí pro vývoj, která lépe napodobuje prostředí pro nasazení.</span><span class="sxs-lookup"><span data-stu-id="fca48-113">Placing the self-signed certificates in the Trusted Root Certification Authorities store enables you to create a development environment that more closely simulates your deployment environment.</span></span>

 <span data-ttu-id="fca48-114">Další informace o vytváření a používání certifikátů najdete v tématu [Working with Certificates](working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="fca48-114">For more information about creating and using certificates, see [Working with Certificates](working-with-certificates.md).</span></span> <span data-ttu-id="fca48-115">Další informace o používání certifikátu jako přihlašovací údaje, najdete v části [zabezpečení služeb a klientů](securing-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="fca48-115">For more information about using a certificate as a credential, see [Securing Services and Clients](securing-services-and-clients.md).</span></span> <span data-ttu-id="fca48-116">Kurz o pomocí technologie Authenticode Microsoftu, najdete v tématu [Authenticode přehledy a kurzy](https://go.microsoft.com/fwlink/?LinkId=88919).</span><span class="sxs-lookup"><span data-stu-id="fca48-116">For a tutorial about using Microsoft Authenticode technology, see [Authenticode Overviews and Tutorials](https://go.microsoft.com/fwlink/?LinkId=88919).</span></span>

## <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a><span data-ttu-id="fca48-117">Vytvořit certifikát podepsaný svým držitelem kořenové autority a exportovat privátní klíč</span><span class="sxs-lookup"><span data-stu-id="fca48-117">To create a self-signed root authority certificate and export the private key</span></span>

<span data-ttu-id="fca48-118">Následující příkaz vytvoří certifikát podepsaný svým držitelem se název předmětu "RootCA" v úložišti osobní aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="fca48-118">The following command creates a self-signed certificate with a subject name of "RootCA" in the Current User Personal store.</span></span>

```powershell
PS $rootCert = New-SelfSignedCertificate -CertStoreLocation cert:\CurrentUser\My -DnsName "RootCA" -TextExtension @("1.3.6.1.4.1.311.21.10={text}1.3.6.1.5.5.7.3.1,1.3.6.1.5.5.7.3.2")
```

<span data-ttu-id="fca48-119">Musíme exportujte certifikát do souboru PFX, takže může být importován do kde budete ho potřebovat v pozdějším kroku.</span><span class="sxs-lookup"><span data-stu-id="fca48-119">We need to export the certificate to a PFX file so that it can be imported to where it's needed in a later step.</span></span> <span data-ttu-id="fca48-120">Při exportu certifikátu s privátním klíčem, aby je chránil se vyžaduje heslo.</span><span class="sxs-lookup"><span data-stu-id="fca48-120">When exporting a certificate with the private key, a password is needed to protect it.</span></span> <span data-ttu-id="fca48-121">Doporučujeme uložit heslo v `SecureString` a použít [Export-PfxCertificate](/powershell/module/pkiclient/export-pfxcertificate) rutiny pro export certifikátu s přidruženým privátním klíčem do souboru PFX.</span><span class="sxs-lookup"><span data-stu-id="fca48-121">We save the password in a `SecureString` and use the [Export-PfxCertificate](/powershell/module/pkiclient/export-pfxcertificate) cmdlet to export the certificate with the associated private key to a PFX file.</span></span> <span data-ttu-id="fca48-122">Veřejný certifikát do souboru CRT pomocí uložíme také [Export certifikátu](/powershell/module/pkiclient/export-certificate) rutiny.</span><span class="sxs-lookup"><span data-stu-id="fca48-122">We also save just the public certificate into a CRT file using the [Export-Certificate](/powershell/module/pkiclient/export-certificate) cmdlet.</span></span>

```powershell
PS [System.Security.SecureString]$rootcertPassword = ConvertTo-SecureString -String "password" -Force -AsPlainText
PS [String]$rootCertPath = Join-Path -Path 'cert:\CurrentUser\My\' -ChildPath "$($rootcert.Thumbprint)"
PS Export-PfxCertificate -Cert $rootCertPath -FilePath 'RootCA.pfx' -Password $rootcertPassword
PS Export-Certificate -Cert $rootCertPath -FilePath 'RootCA.crt'
```

## <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a><span data-ttu-id="fca48-123">Chcete-li vytvořit nový certifikát podepsaný certifikátem kořenového certifikátu autority</span><span class="sxs-lookup"><span data-stu-id="fca48-123">To create a new certificate signed by a root authority certificate</span></span>

<span data-ttu-id="fca48-124">Následující příkaz vytvoří certifikát podepsaný službou `RootCA` s názvem subjektu "SignedByRootCA" pomocí soukromého klíče vydavatele.</span><span class="sxs-lookup"><span data-stu-id="fca48-124">The following command creates a certificate signed by the `RootCA` with a subject name of "SignedByRootCA" using the private key of the issuer.</span></span>

```powershell
PS $testCert = New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "SignedByRootCA" -KeyExportPolicy Exportable -KeyLength 2048 -KeyUsage DigitalSignature,KeyEncipherment -Signer $rootCert
```

<span data-ttu-id="fca48-125">Podobně uložíme podepsaném certifikátu s privátním klíčem do souboru PFX a pouze veřejný klíč do souboru CRT.</span><span class="sxs-lookup"><span data-stu-id="fca48-125">Similarly, we save the signed certificate with private key into a PFX file and just the public key into a CRT file.</span></span>

```powershell
PS [String]$testCertPath = Join-Path -Path 'cert:\LocalMachine\My\' -ChildPath "$($testCert.Thumbprint)"
PS Export-PfxCertificate -Cert $testCertPath -FilePath testcert.pfx -Password $rootcertPassword
PS Export-Certificate -Cert $testCertPath -FilePath testcert.crt
```

## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a><span data-ttu-id="fca48-126">Instalace certifikátu v důvěryhodné Store autority certifikační kořenové</span><span class="sxs-lookup"><span data-stu-id="fca48-126">Installing a Certificate in the Trusted Root Certification Authorities Store</span></span>

<span data-ttu-id="fca48-127">Jakmile se vytvoří certifikát podepsaný svým držitelem, můžete nainstalovat v úložišti Důvěryhodné kořenové certifikační autority.</span><span class="sxs-lookup"><span data-stu-id="fca48-127">Once a self-signed certificate is created, you can install it in the Trusted Root Certification Authorities store.</span></span> <span data-ttu-id="fca48-128">Všechny certifikáty, které jsou podepsány pomocí certifikátu v tomto okamžiku jsou důvěryhodné počítače.</span><span class="sxs-lookup"><span data-stu-id="fca48-128">Any certificates that are signed with the certificate at this point are trusted by the computer.</span></span> <span data-ttu-id="fca48-129">Z tohoto důvodu se odstraní certifikát z úložiště, jakmile ho už nepotřebují.</span><span class="sxs-lookup"><span data-stu-id="fca48-129">For this reason, delete the certificate from the store as soon as you no longer need it.</span></span> <span data-ttu-id="fca48-130">Při odstranění tento kořenový certifikát autority stane neoprávněné všechny certifikáty, které s ním podepsané.</span><span class="sxs-lookup"><span data-stu-id="fca48-130">When you delete this root authority certificate, all other certificates that signed with it become unauthorized.</span></span> <span data-ttu-id="fca48-131">Kořenových certifikátů úřadu slouží jednoduše jako mechanismus, kterým skupinu certifikátů můžete zařadit do oboru podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="fca48-131">Root authority certificates are simply a mechanism whereby a group of certificates can be scoped as necessary.</span></span> <span data-ttu-id="fca48-132">Třeba aplikace peer-to-peer, není obvykle nutné pro kořenovou autoritou vzhledem k tomu, že důvěřujete identity individuální uživatel jednoduše podle jeho zadaný certifikát.</span><span class="sxs-lookup"><span data-stu-id="fca48-132">For example, in peer-to-peer applications, there is typically no need for a root authority because you simply trust the identity of an individual by its supplied certificate.</span></span>

### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a><span data-ttu-id="fca48-133">Chcete-li nainstalovat certifikát podepsaný svým držitelem v důvěryhodných kořenových certifikačních autorit</span><span class="sxs-lookup"><span data-stu-id="fca48-133">To install a self-signed certificate in the Trusted Root Certification Authorities</span></span>

1. <span data-ttu-id="fca48-134">Otevřete modul snap-in certifikátu.</span><span class="sxs-lookup"><span data-stu-id="fca48-134">Open the certificate snap-in.</span></span> <span data-ttu-id="fca48-135">Další informace najdete v tématu [postupy: zobrazení certifikátů pomocí modulu Snap-in konzoly MMC](how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="fca48-135">For more information, see [How to: View Certificates with the MMC Snap-in](how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>

2. <span data-ttu-id="fca48-136">Otevřete složku, která se má certifikát uložit buď **místního počítače** nebo **aktuálního uživatele**.</span><span class="sxs-lookup"><span data-stu-id="fca48-136">Open the folder to store the certificate, either the **Local Computer** or the **Current User**.</span></span>

3. <span data-ttu-id="fca48-137">Otevřít **důvěryhodných kořenových certifikačních autorit** složky.</span><span class="sxs-lookup"><span data-stu-id="fca48-137">Open the **Trusted Root Certification Authorities** folder.</span></span>

4. <span data-ttu-id="fca48-138">Klikněte pravým tlačítkem na **certifikáty** složky a klikněte na tlačítko **všechny úkoly**, pak klikněte na tlačítko **Import**.</span><span class="sxs-lookup"><span data-stu-id="fca48-138">Right-click the **Certificates** folder and click **All Tasks**, then click **Import**.</span></span>

5. <span data-ttu-id="fca48-139">Na obrazovce průvodce podle pokynů TempCa.cer naimportujte do úložiště.</span><span class="sxs-lookup"><span data-stu-id="fca48-139">Follow the on-screen wizard instructions to import the TempCa.cer into the store.</span></span>

## <a name="using-certificates-with-wcf"></a><span data-ttu-id="fca48-140">Použití certifikátů s WCF</span><span class="sxs-lookup"><span data-stu-id="fca48-140">Using certificates With WCF</span></span>

<span data-ttu-id="fca48-141">Po nastavení dočasných certifikátů můžete je použít pro vývoj řešení pro WCF, které určují certifikáty jako typ pověření klienta.</span><span class="sxs-lookup"><span data-stu-id="fca48-141">Once you have set up the temporary certificates, you can use them to develop WCF solutions that specify certificates as a client credential type.</span></span> <span data-ttu-id="fca48-142">Například následující XML konfigurace určuje zabezpečení zpráv a certifikát jako typ pověření klienta.</span><span class="sxs-lookup"><span data-stu-id="fca48-142">For example, the following XML configuration specifies message security and a certificate as the client credential type.</span></span>

### <a name="to-specify-a-certificate-as-the-client-credential-type"></a><span data-ttu-id="fca48-143">Chcete-li určit certifikát jako typ pověření klienta</span><span class="sxs-lookup"><span data-stu-id="fca48-143">To specify a certificate as the client credential type</span></span>

- <span data-ttu-id="fca48-144">V konfiguračním souboru pro službu použijte následující kód XML pro nastavení režimu zabezpečení zpráv a typu pověření klienta k certifikátu.</span><span class="sxs-lookup"><span data-stu-id="fca48-144">In the configuration file for a service, use the following XML to set the security mode to message, and the client credential type to certificate.</span></span>

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

<span data-ttu-id="fca48-145">V konfiguračním souboru pro klienta použijte následující kód XML k určení, že certifikát je nalezena v úložišti uživatele a najdete tak, že pole SubjectName pro hodnotu "CohoWinery."</span><span class="sxs-lookup"><span data-stu-id="fca48-145">In the configuration file for a client, use the following XML to specify that the certificate is found in the user’s store, and can be found by searching the SubjectName field for the value "CohoWinery."</span></span>

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

<span data-ttu-id="fca48-146">Další informace o používání certifikátů ve službě WCF najdete v tématu [Working with Certificates](working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="fca48-146">For more information about using certificates in WCF, see [Working with Certificates](working-with-certificates.md).</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="fca48-147">zabezpečení v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fca48-147">.NET Framework security</span></span>

<span data-ttu-id="fca48-148">Nezapomeňte odstranit všechny dočasné kořenových certifikátů úřadu z **důvěryhodných kořenových certifikačních autorit** a **osobní** složek tak, že kliknete pravým tlačítkem certifikát, pak kliknutím na  **Odstranit**.</span><span class="sxs-lookup"><span data-stu-id="fca48-148">Be sure to delete any temporary root authority certificates from the **Trusted Root Certification Authorities** and **Personal** folders by right-clicking the certificate, then clicking **Delete**.</span></span>

## <a name="see-also"></a><span data-ttu-id="fca48-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fca48-149">See also</span></span>

- [<span data-ttu-id="fca48-150">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="fca48-150">Working with Certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="fca48-151">Postupy: Zobrazení certifikátů pomocí modulu snap-in konzoly MMC</span><span class="sxs-lookup"><span data-stu-id="fca48-151">How to: View Certificates with the MMC Snap-in</span></span>](how-to-view-certificates-with-the-mmc-snap-in.md)
- [<span data-ttu-id="fca48-152">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="fca48-152">Securing Services and Clients</span></span>](securing-services-and-clients.md)