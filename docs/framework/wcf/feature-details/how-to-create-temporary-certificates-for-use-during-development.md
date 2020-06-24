---
title: 'Postupy: Vytváření dočasných certifikátů pro použití během vývoje'
description: Naučte se používat rutinu PowerShellu k vytvoření dvou dočasných certifikátů X. 509 pro použití při vývoji zabezpečené služby nebo klienta služby WCF.
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], creating temporary certificates
- temporary certificates [WCF]
ms.assetid: bc5f6637-5513-4d27-99bb-51aad7741e4a
ms.openlocfilehash: 0a21548386639a9f6a8c8572e5d7928ffdb270d6
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247036"
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a><span data-ttu-id="4e98b-103">Postupy: Vytváření dočasných certifikátů pro použití během vývoje</span><span class="sxs-lookup"><span data-stu-id="4e98b-103">How to: Create Temporary Certificates for Use During Development</span></span>

<span data-ttu-id="4e98b-104">Při vývoji zabezpečené služby nebo klienta pomocí Windows Communication Foundation (WCF) je často nutné dodat certifikát X. 509, který se má použít jako přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="4e98b-104">When developing a secure service or client using Windows Communication Foundation (WCF), it is often necessary to supply an X.509 certificate to be used as a credential.</span></span> <span data-ttu-id="4e98b-105">Certifikát obvykle je součástí řetězce certifikátů s kořenovou autoritou, která se nachází v úložišti důvěryhodných kořenových certifikačních autorit počítače.</span><span class="sxs-lookup"><span data-stu-id="4e98b-105">The certificate typically is part of a chain of certificates with a root authority found in the Trusted Root Certification Authorities store of the computer.</span></span> <span data-ttu-id="4e98b-106">Řetěz certifikátů vám umožní určit rozsah sady certifikátů, ve kterých je kořenová autorita z vaší organizace nebo organizační jednotky.</span><span class="sxs-lookup"><span data-stu-id="4e98b-106">Having a certificate chain enables you to scope a set of certificates where typically the root authority is from your organization or business unit.</span></span> <span data-ttu-id="4e98b-107">Chcete-li tuto možnost emulovat v době vývoje, můžete vytvořit dva certifikáty, které splňují požadavky na zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4e98b-107">To emulate this at development time, you can create two certificates to satisfy the security requirements.</span></span> <span data-ttu-id="4e98b-108">První je certifikát podepsaný svým držitelem, který je umístěný v úložišti důvěryhodných kořenových certifikačních autorit, a druhý certifikát se vytvoří z prvního a uloží se do osobního úložiště umístění místního počítače nebo do osobního úložiště aktuálního umístění uživatele.</span><span class="sxs-lookup"><span data-stu-id="4e98b-108">The first is a self-signed certificate that is placed in the Trusted Root Certification Authorities store, and the second certificate is created from the first and is placed in either the Personal store of the Local Machine location, or the Personal store of the Current User location.</span></span> <span data-ttu-id="4e98b-109">Toto téma vás provede kroky k vytvoření těchto dvou certifikátů pomocí rutiny [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) prostředí PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4e98b-109">This topic walks through the steps to create these two certificates using the Powershell [New-SelfSignedCertificate)](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4e98b-110">Certifikáty, které generuje rutina New-SelfSignedCertificate, jsou k dispozici pouze pro účely testování.</span><span class="sxs-lookup"><span data-stu-id="4e98b-110">The certificates that the New-SelfSignedCertificate cmdlet generates are provided for testing purposes only.</span></span> <span data-ttu-id="4e98b-111">Při nasazování služby nebo klienta nezapomeňte použít příslušný certifikát poskytovaný certifikační autoritou.</span><span class="sxs-lookup"><span data-stu-id="4e98b-111">When deploying a service or client, be sure to use an appropriate certificate provided by a certification authority.</span></span> <span data-ttu-id="4e98b-112">Může to být buď certifikát serveru Windows Server ve vaší organizaci, nebo třetí strana.</span><span class="sxs-lookup"><span data-stu-id="4e98b-112">This could either be from a Windows Server certificate server in your organization or a third party.</span></span>
>
> <span data-ttu-id="4e98b-113">Ve výchozím nastavení vytvoří rutina [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) certifikáty, které jsou podepsané svým držitelem, a tyto certifikáty jsou nezabezpečené.</span><span class="sxs-lookup"><span data-stu-id="4e98b-113">By default, the [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet creates certificates that are self-signed and these certificates are insecure.</span></span> <span data-ttu-id="4e98b-114">Umístění certifikátů podepsaných svým držitelem do úložiště důvěryhodných kořenových certifikačních autorit vám umožní vytvořit vývojové prostředí, které lépe simuluje prostředí nasazení.</span><span class="sxs-lookup"><span data-stu-id="4e98b-114">Placing the self-signed certificates in the Trusted Root Certification Authorities store enables you to create a development environment that more closely simulates your deployment environment.</span></span>

 <span data-ttu-id="4e98b-115">Další informace o vytváření a používání certifikátů najdete v tématu [práce s certifikáty](working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="4e98b-115">For more information about creating and using certificates, see [Working with Certificates](working-with-certificates.md).</span></span> <span data-ttu-id="4e98b-116">Další informace o použití certifikátu jako přihlašovacích údajů najdete v tématu [zabezpečení služeb a klientů](securing-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="4e98b-116">For more information about using a certificate as a credential, see [Securing Services and Clients](securing-services-and-clients.md).</span></span> <span data-ttu-id="4e98b-117">Kurz týkající se používání technologie Microsoft Authenticode naleznete v tématu [přehledy technologie Authenticode a kurzy](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537360(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="4e98b-117">For a tutorial about using Microsoft Authenticode technology, see [Authenticode Overviews and Tutorials](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537360(v=vs.85)).</span></span>

## <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a><span data-ttu-id="4e98b-118">Vytvoření certifikátu kořenového úřadu podepsaného svým držitelem a export privátního klíče</span><span class="sxs-lookup"><span data-stu-id="4e98b-118">To create a self-signed root authority certificate and export the private key</span></span>

<span data-ttu-id="4e98b-119">Následující příkaz vytvoří certifikát podepsaný svým držitelem s názvem subjektu "RootCA" v aktuálním osobním úložišti uživatele.</span><span class="sxs-lookup"><span data-stu-id="4e98b-119">The following command creates a self-signed certificate with a subject name of "RootCA" in the Current User Personal store.</span></span>

```powershell
$rootcert = New-SelfSignedCertificate -CertStoreLocation Cert:\CurrentUser\My -DnsName "RootCA" -TextExtension @("2.5.29.19={text}CA=true") -KeyUsage CertSign,CrlSign,DigitalSignature
```

<span data-ttu-id="4e98b-120">Musíme vyexportovat certifikát do souboru PFX, aby se mohl importovat do, kde bude potřeba v pozdějším kroku.</span><span class="sxs-lookup"><span data-stu-id="4e98b-120">We need to export the certificate to a PFX file so that it can be imported to where it's needed in a later step.</span></span> <span data-ttu-id="4e98b-121">Při exportu certifikátu s privátním klíčem je nutné zadat heslo k ochraně.</span><span class="sxs-lookup"><span data-stu-id="4e98b-121">When exporting a certificate with the private key, a password is needed to protect it.</span></span> <span data-ttu-id="4e98b-122">Uložíme heslo do `SecureString` a pomocí rutiny [Export-vybíráte](/powershell/module/pkiclient/export-pfxcertificate) vyexportujete certifikát s přidruženým privátním klíčem do souboru PFX.</span><span class="sxs-lookup"><span data-stu-id="4e98b-122">We save the password in a `SecureString` and use the [Export-PfxCertificate](/powershell/module/pkiclient/export-pfxcertificate) cmdlet to export the certificate with the associated private key to a PFX file.</span></span> <span data-ttu-id="4e98b-123">Do souboru CRT také ukládáme jenom veřejný certifikát pomocí rutiny [Export-Certificate](/powershell/module/pkiclient/export-certificate) .</span><span class="sxs-lookup"><span data-stu-id="4e98b-123">We also save just the public certificate into a CRT file using the [Export-Certificate](/powershell/module/pkiclient/export-certificate) cmdlet.</span></span>

```powershell
[System.Security.SecureString]$rootcertPassword = ConvertTo-SecureString -String "password" -Force -AsPlainText
[String]$rootCertPath = Join-Path -Path 'cert:\CurrentUser\My\' -ChildPath "$($rootcert.Thumbprint)"
Export-PfxCertificate -Cert $rootCertPath -FilePath 'RootCA.pfx' -Password $rootcertPassword
Export-Certificate -Cert $rootCertPath -FilePath 'RootCA.crt'
```

## <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a><span data-ttu-id="4e98b-124">Vytvoření nového certifikátu podepsaného certifikátem kořenové autority</span><span class="sxs-lookup"><span data-stu-id="4e98b-124">To create a new certificate signed by a root authority certificate</span></span>

<span data-ttu-id="4e98b-125">Následující příkaz vytvoří certifikát podepsaný pomocí `RootCA` názvu subjektu "SignedByRootCA" pomocí privátního klíče vystavitele.</span><span class="sxs-lookup"><span data-stu-id="4e98b-125">The following command creates a certificate signed by the `RootCA` with a subject name of "SignedByRootCA" using the private key of the issuer.</span></span>

```powershell
$testCert = New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "SignedByRootCA" -KeyExportPolicy Exportable -KeyLength 2048 -KeyUsage DigitalSignature,KeyEncipherment -Signer $rootCert
```

<span data-ttu-id="4e98b-126">Podobně ukládáme podepsaný certifikát s privátním klíčem do souboru PFX a jenom veřejný klíč do souboru CRT.</span><span class="sxs-lookup"><span data-stu-id="4e98b-126">Similarly, we save the signed certificate with private key into a PFX file and just the public key into a CRT file.</span></span>

```powershell
[String]$testCertPath = Join-Path -Path 'cert:\LocalMachine\My\' -ChildPath "$($testCert.Thumbprint)"
Export-PfxCertificate -Cert $testCertPath -FilePath testcert.pfx -Password $rootcertPassword
Export-Certificate -Cert $testCertPath -FilePath testcert.crt
```

## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a><span data-ttu-id="4e98b-127">Instalace certifikátu v úložišti důvěryhodných kořenových certifikačních autorit</span><span class="sxs-lookup"><span data-stu-id="4e98b-127">Installing a Certificate in the Trusted Root Certification Authorities Store</span></span>

<span data-ttu-id="4e98b-128">Po vytvoření certifikátu podepsaného svým držitelem ho můžete nainstalovat v úložišti důvěryhodných kořenových certifikačních autorit.</span><span class="sxs-lookup"><span data-stu-id="4e98b-128">Once a self-signed certificate is created, you can install it in the Trusted Root Certification Authorities store.</span></span> <span data-ttu-id="4e98b-129">Všechny certifikáty, které jsou v tomto okamžiku podepsány certifikátem, jsou tímto počítačem důvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="4e98b-129">Any certificates that are signed with the certificate at this point are trusted by the computer.</span></span> <span data-ttu-id="4e98b-130">Z tohoto důvodu odstraňte certifikát z úložiště, jakmile ho už nebudete potřebovat.</span><span class="sxs-lookup"><span data-stu-id="4e98b-130">For this reason, delete the certificate from the store as soon as you no longer need it.</span></span> <span data-ttu-id="4e98b-131">Když odstraníte tento certifikát kořenové autority, všechny ostatní certifikáty, které s ním budou podepsané, se stanou neautorizovanými.</span><span class="sxs-lookup"><span data-stu-id="4e98b-131">When you delete this root authority certificate, all other certificates that signed with it become unauthorized.</span></span> <span data-ttu-id="4e98b-132">Certifikáty kořenové autority jsou jednoduše mechanismem, který může podle potřeby vymezena skupina certifikátů.</span><span class="sxs-lookup"><span data-stu-id="4e98b-132">Root authority certificates are simply a mechanism whereby a group of certificates can be scoped as necessary.</span></span> <span data-ttu-id="4e98b-133">Například v aplikacích typu peer-to-peer není obvykle nutné, aby byla kořenová autorita, protože jednoduše důvěřujete identitě jednotlivce podle jeho poskytnutého certifikátu.</span><span class="sxs-lookup"><span data-stu-id="4e98b-133">For example, in peer-to-peer applications, there is typically no need for a root authority because you simply trust the identity of an individual by its supplied certificate.</span></span>

### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a><span data-ttu-id="4e98b-134">Instalace certifikátu podepsaného svým držitelem do důvěryhodných kořenových certifikačních autorit</span><span class="sxs-lookup"><span data-stu-id="4e98b-134">To install a self-signed certificate in the Trusted Root Certification Authorities</span></span>

1. <span data-ttu-id="4e98b-135">Otevřete modul snap-in Certifikáty.</span><span class="sxs-lookup"><span data-stu-id="4e98b-135">Open the certificate snap-in.</span></span> <span data-ttu-id="4e98b-136">Další informace najdete v tématu [Postup: zobrazení certifikátů pomocí modulu snap-in konzoly MMC](how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="4e98b-136">For more information, see [How to: View Certificates with the MMC Snap-in](how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>

2. <span data-ttu-id="4e98b-137">Otevřete složku pro uložení certifikátu, buď **místního počítače** , nebo **aktuálního uživatele**.</span><span class="sxs-lookup"><span data-stu-id="4e98b-137">Open the folder to store the certificate, either the **Local Computer** or the **Current User**.</span></span>

3. <span data-ttu-id="4e98b-138">Otevřete složku **důvěryhodných kořenových certifikačních autorit** .</span><span class="sxs-lookup"><span data-stu-id="4e98b-138">Open the **Trusted Root Certification Authorities** folder.</span></span>

4. <span data-ttu-id="4e98b-139">Klikněte pravým tlačítkem na složku **certifikáty** , klikněte na **všechny úlohy**a pak klikněte na **importovat**.</span><span class="sxs-lookup"><span data-stu-id="4e98b-139">Right-click the **Certificates** folder and click **All Tasks**, then click **Import**.</span></span>

5. <span data-ttu-id="4e98b-140">Postupujte podle pokynů Průvodce na obrazovce a importujte soubor RootCA. pfx do úložiště.</span><span class="sxs-lookup"><span data-stu-id="4e98b-140">Follow the on-screen wizard instructions to import the RootCA.pfx into the store.</span></span>

## <a name="using-certificates-with-wcf"></a><span data-ttu-id="4e98b-141">Používání certifikátů pomocí WCF</span><span class="sxs-lookup"><span data-stu-id="4e98b-141">Using certificates With WCF</span></span>

<span data-ttu-id="4e98b-142">Po nastavení dočasných certifikátů je můžete použít k vývoji řešení WCF, která určují certifikáty jako typ pověření klienta.</span><span class="sxs-lookup"><span data-stu-id="4e98b-142">Once you have set up the temporary certificates, you can use them to develop WCF solutions that specify certificates as a client credential type.</span></span> <span data-ttu-id="4e98b-143">Například následující konfigurace XML určuje zabezpečení zprávy a certifikát jako typ přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="4e98b-143">For example, the following XML configuration specifies message security and a certificate as the client credential type.</span></span>

### <a name="to-specify-a-certificate-as-the-client-credential-type"></a><span data-ttu-id="4e98b-144">Určení certifikátu jako typ přihlašovacích údajů klienta</span><span class="sxs-lookup"><span data-stu-id="4e98b-144">To specify a certificate as the client credential type</span></span>

1. <span data-ttu-id="4e98b-145">V konfiguračním souboru pro službu použijte následující kód XML pro nastavení režimu zabezpečení na zpráva a typ přihlašovacích údajů klienta na certifikát.</span><span class="sxs-lookup"><span data-stu-id="4e98b-145">In the configuration file for a service, use the following XML to set the security mode to message, and the client credential type to certificate.</span></span>

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

2. <span data-ttu-id="4e98b-146">V konfiguračním souboru pro klienta použijte následující kód XML k určení toho, že se certifikát nachází v úložišti uživatele, a lze jej najít hledáním pole Subject pro hodnotu "CohoWinery".</span><span class="sxs-lookup"><span data-stu-id="4e98b-146">In the configuration file for a client, use the following XML to specify that the certificate is found in the user’s store, and can be found by searching the SubjectName field for the value "CohoWinery."</span></span>

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

<span data-ttu-id="4e98b-147">Další informace o použití certifikátů v technologii WCF najdete v tématu [práce s certifikáty](working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="4e98b-147">For more information about using certificates in WCF, see [Working with Certificates](working-with-certificates.md).</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="4e98b-148">zabezpečení v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4e98b-148">.NET Framework security</span></span>

<span data-ttu-id="4e98b-149">Nezapomeňte odstranit dočasné certifikáty kořenové autority z **důvěryhodných kořenových certifikačních autorit** a **osobní** složky tak, že kliknete pravým tlačítkem na certifikát a pak kliknete na **Odstranit**.</span><span class="sxs-lookup"><span data-stu-id="4e98b-149">Be sure to delete any temporary root authority certificates from the **Trusted Root Certification Authorities** and **Personal** folders by right-clicking the certificate, then clicking **Delete**.</span></span>

## <a name="see-also"></a><span data-ttu-id="4e98b-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="4e98b-150">See also</span></span>

- [<span data-ttu-id="4e98b-151">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="4e98b-151">Working with Certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="4e98b-152">Postupy: Zobrazení certifikátů pomocí modulu snap-in konzoly MMC</span><span class="sxs-lookup"><span data-stu-id="4e98b-152">How to: View Certificates with the MMC Snap-in</span></span>](how-to-view-certificates-with-the-mmc-snap-in.md)
- [<span data-ttu-id="4e98b-153">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="4e98b-153">Securing Services and Clients</span></span>](securing-services-and-clients.md)
