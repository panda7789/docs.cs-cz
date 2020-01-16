---
title: 'Postupy: vytváření dočasných certifikátů pro použití během vývoje'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], creating temporary certificates
- temporary certificates [WCF]
ms.assetid: bc5f6637-5513-4d27-99bb-51aad7741e4a
ms.openlocfilehash: 9e01ccb29ad017a2657ab08b54d7f01ef4564481
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964540"
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a><span data-ttu-id="b6ef8-102">Postupy: vytváření dočasných certifikátů pro použití během vývoje</span><span class="sxs-lookup"><span data-stu-id="b6ef8-102">How to: Create Temporary Certificates for Use During Development</span></span>

<span data-ttu-id="b6ef8-103">Při vývoji zabezpečené služby nebo klienta pomocí Windows Communication Foundation (WCF) je často nutné dodat certifikát X. 509, který se má použít jako přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="b6ef8-103">When developing a secure service or client using Windows Communication Foundation (WCF), it is often necessary to supply an X.509 certificate to be used as a credential.</span></span> <span data-ttu-id="b6ef8-104">Certifikát obvykle je součástí řetězce certifikátů s kořenovou autoritou, která se nachází v úložišti důvěryhodných kořenových certifikačních autorit počítače.</span><span class="sxs-lookup"><span data-stu-id="b6ef8-104">The certificate typically is part of a chain of certificates with a root authority found in the Trusted Root Certification Authorities store of the computer.</span></span> <span data-ttu-id="b6ef8-105">Řetěz certifikátů vám umožní určit rozsah sady certifikátů, ve kterých je kořenová autorita z vaší organizace nebo organizační jednotky.</span><span class="sxs-lookup"><span data-stu-id="b6ef8-105">Having a certificate chain enables you to scope a set of certificates where typically the root authority is from your organization or business unit.</span></span> <span data-ttu-id="b6ef8-106">Chcete-li tuto možnost emulovat v době vývoje, můžete vytvořit dva certifikáty, které splňují požadavky na zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="b6ef8-106">To emulate this at development time, you can create two certificates to satisfy the security requirements.</span></span> <span data-ttu-id="b6ef8-107">První je certifikát podepsaný svým držitelem, který je umístěn v úložišti důvěryhodných kořenových certifikačních autorit a druhý certifikát je vytvořen z prvního a je umístěn v osobním úložišti umístění místního počítače nebo osobního úložiště Aktuální umístění uživatele.</span><span class="sxs-lookup"><span data-stu-id="b6ef8-107">The first is a self-signed certificate that is placed in the Trusted Root Certification Authorities store, and the second certificate is created from the first and is placed in either the Personal store of the Local Machine location, or the Personal store of the Current User location.</span></span> <span data-ttu-id="b6ef8-108">Toto téma vás provede kroky k vytvoření těchto dvou certifikátů pomocí rutiny [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) prostředí PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b6ef8-108">This topic walks through the steps to create these two certificates using the Powershell [New-SelfSignedCertificate)](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b6ef8-109">Certifikáty, které generuje rutina New-SelfSignedCertificate, jsou k dispozici pouze pro účely testování.</span><span class="sxs-lookup"><span data-stu-id="b6ef8-109">The certificates that the New-SelfSignedCertificate cmdlet generates are provided for testing purposes only.</span></span> <span data-ttu-id="b6ef8-110">Při nasazování služby nebo klienta nezapomeňte použít příslušný certifikát poskytovaný certifikační autoritou.</span><span class="sxs-lookup"><span data-stu-id="b6ef8-110">When deploying a service or client, be sure to use an appropriate certificate provided by a certification authority.</span></span> <span data-ttu-id="b6ef8-111">Může to být buď certifikát serveru Windows Server ve vaší organizaci, nebo třetí strana.</span><span class="sxs-lookup"><span data-stu-id="b6ef8-111">This could either be from a Windows Server certificate server in your organization or a third party.</span></span>
>
> <span data-ttu-id="b6ef8-112">Ve výchozím nastavení vytvoří rutina [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) certifikáty, které jsou podepsané svým držitelem, a tyto certifikáty jsou nezabezpečené.</span><span class="sxs-lookup"><span data-stu-id="b6ef8-112">By default, the [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet creates certificates that are self-signed and these certificates are insecure.</span></span> <span data-ttu-id="b6ef8-113">Umístění certifikátů podepsaných svým držitelem do úložiště důvěryhodných kořenových certifikačních autorit vám umožní vytvořit vývojové prostředí, které lépe simuluje prostředí nasazení.</span><span class="sxs-lookup"><span data-stu-id="b6ef8-113">Placing the self-signed certificates in the Trusted Root Certification Authorities store enables you to create a development environment that more closely simulates your deployment environment.</span></span>

 <span data-ttu-id="b6ef8-114">Další informace o vytváření a používání certifikátů najdete v tématu [práce s certifikáty](working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="b6ef8-114">For more information about creating and using certificates, see [Working with Certificates](working-with-certificates.md).</span></span> <span data-ttu-id="b6ef8-115">Další informace o použití certifikátu jako přihlašovacích údajů najdete v tématu [zabezpečení služeb a klientů](securing-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="b6ef8-115">For more information about using a certificate as a credential, see [Securing Services and Clients](securing-services-and-clients.md).</span></span> <span data-ttu-id="b6ef8-116">Kurz týkající se používání technologie Microsoft Authenticode naleznete v tématu [přehledy technologie Authenticode a kurzy](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537360(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="b6ef8-116">For a tutorial about using Microsoft Authenticode technology, see [Authenticode Overviews and Tutorials](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537360(v=vs.85)).</span></span>

## <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a><span data-ttu-id="b6ef8-117">Vytvoření certifikátu kořenového úřadu podepsaného svým držitelem a export privátního klíče</span><span class="sxs-lookup"><span data-stu-id="b6ef8-117">To create a self-signed root authority certificate and export the private key</span></span>

<span data-ttu-id="b6ef8-118">Následující příkaz vytvoří certifikát podepsaný svým držitelem s názvem subjektu "RootCA" v aktuálním osobním úložišti uživatele.</span><span class="sxs-lookup"><span data-stu-id="b6ef8-118">The following command creates a self-signed certificate with a subject name of "RootCA" in the Current User Personal store.</span></span>

```powershell
$rootcert = New-SelfSignedCertificate -CertStoreLocation Cert:\CurrentUser\My -DnsName "RootCA" -TextExtension @("2.5.29.19={text}CA=true") -KeyUsage CertSign,CrlSign,DigitalSignature
```

<span data-ttu-id="b6ef8-119">Musíme vyexportovat certifikát do souboru PFX, aby se mohl importovat do, kde bude potřeba v pozdějším kroku.</span><span class="sxs-lookup"><span data-stu-id="b6ef8-119">We need to export the certificate to a PFX file so that it can be imported to where it's needed in a later step.</span></span> <span data-ttu-id="b6ef8-120">Při exportu certifikátu s privátním klíčem je nutné zadat heslo k ochraně.</span><span class="sxs-lookup"><span data-stu-id="b6ef8-120">When exporting a certificate with the private key, a password is needed to protect it.</span></span> <span data-ttu-id="b6ef8-121">Heslo ukládáme do `SecureString` a pomocí rutiny [Export-vybíráte](/powershell/module/pkiclient/export-pfxcertificate) vyexportujete certifikát s přidruženým privátním klíčem do souboru PFX.</span><span class="sxs-lookup"><span data-stu-id="b6ef8-121">We save the password in a `SecureString` and use the [Export-PfxCertificate](/powershell/module/pkiclient/export-pfxcertificate) cmdlet to export the certificate with the associated private key to a PFX file.</span></span> <span data-ttu-id="b6ef8-122">Do souboru CRT také ukládáme jenom veřejný certifikát pomocí rutiny [Export-Certificate](/powershell/module/pkiclient/export-certificate) .</span><span class="sxs-lookup"><span data-stu-id="b6ef8-122">We also save just the public certificate into a CRT file using the [Export-Certificate](/powershell/module/pkiclient/export-certificate) cmdlet.</span></span>

```powershell
[System.Security.SecureString]$rootcertPassword = ConvertTo-SecureString -String "password" -Force -AsPlainText
[String]$rootCertPath = Join-Path -Path 'cert:\CurrentUser\My\' -ChildPath "$($rootcert.Thumbprint)"
Export-PfxCertificate -Cert $rootCertPath -FilePath 'RootCA.pfx' -Password $rootcertPassword
Export-Certificate -Cert $rootCertPath -FilePath 'RootCA.crt'
```

## <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a><span data-ttu-id="b6ef8-123">Vytvoření nového certifikátu podepsaného certifikátem kořenové autority</span><span class="sxs-lookup"><span data-stu-id="b6ef8-123">To create a new certificate signed by a root authority certificate</span></span>

<span data-ttu-id="b6ef8-124">Následující příkaz vytvoří certifikát podepsaný `RootCA`em s názvem subjektu "SignedByRootCA", který používá privátní klíč vystavitele.</span><span class="sxs-lookup"><span data-stu-id="b6ef8-124">The following command creates a certificate signed by the `RootCA` with a subject name of "SignedByRootCA" using the private key of the issuer.</span></span>

```powershell
$testCert = New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "SignedByRootCA" -KeyExportPolicy Exportable -KeyLength 2048 -KeyUsage DigitalSignature,KeyEncipherment -Signer $rootCert
```

<span data-ttu-id="b6ef8-125">Podobně ukládáme podepsaný certifikát s privátním klíčem do souboru PFX a jenom veřejný klíč do souboru CRT.</span><span class="sxs-lookup"><span data-stu-id="b6ef8-125">Similarly, we save the signed certificate with private key into a PFX file and just the public key into a CRT file.</span></span>

```powershell
[String]$testCertPath = Join-Path -Path 'cert:\LocalMachine\My\' -ChildPath "$($testCert.Thumbprint)"
Export-PfxCertificate -Cert $testCertPath -FilePath testcert.pfx -Password $rootcertPassword
Export-Certificate -Cert $testCertPath -FilePath testcert.crt
```

## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a><span data-ttu-id="b6ef8-126">Instalace certifikátu v úložišti důvěryhodných kořenových certifikačních autorit</span><span class="sxs-lookup"><span data-stu-id="b6ef8-126">Installing a Certificate in the Trusted Root Certification Authorities Store</span></span>

<span data-ttu-id="b6ef8-127">Po vytvoření certifikátu podepsaného svým držitelem ho můžete nainstalovat v úložišti důvěryhodných kořenových certifikačních autorit.</span><span class="sxs-lookup"><span data-stu-id="b6ef8-127">Once a self-signed certificate is created, you can install it in the Trusted Root Certification Authorities store.</span></span> <span data-ttu-id="b6ef8-128">Všechny certifikáty, které jsou v tomto okamžiku podepsány certifikátem, jsou tímto počítačem důvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="b6ef8-128">Any certificates that are signed with the certificate at this point are trusted by the computer.</span></span> <span data-ttu-id="b6ef8-129">Z tohoto důvodu odstraňte certifikát z úložiště, jakmile ho už nebudete potřebovat.</span><span class="sxs-lookup"><span data-stu-id="b6ef8-129">For this reason, delete the certificate from the store as soon as you no longer need it.</span></span> <span data-ttu-id="b6ef8-130">Když odstraníte tento certifikát kořenové autority, všechny ostatní certifikáty, které s ním budou podepsané, se stanou neautorizovanými.</span><span class="sxs-lookup"><span data-stu-id="b6ef8-130">When you delete this root authority certificate, all other certificates that signed with it become unauthorized.</span></span> <span data-ttu-id="b6ef8-131">Certifikáty kořenové autority jsou jednoduše mechanismem, který může podle potřeby vymezena skupina certifikátů.</span><span class="sxs-lookup"><span data-stu-id="b6ef8-131">Root authority certificates are simply a mechanism whereby a group of certificates can be scoped as necessary.</span></span> <span data-ttu-id="b6ef8-132">Například v aplikacích typu peer-to-peer není obvykle nutné, aby byla kořenová autorita, protože jednoduše důvěřujete identitě jednotlivce podle jeho poskytnutého certifikátu.</span><span class="sxs-lookup"><span data-stu-id="b6ef8-132">For example, in peer-to-peer applications, there is typically no need for a root authority because you simply trust the identity of an individual by its supplied certificate.</span></span>

### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a><span data-ttu-id="b6ef8-133">Instalace certifikátu podepsaného svým držitelem do důvěryhodných kořenových certifikačních autorit</span><span class="sxs-lookup"><span data-stu-id="b6ef8-133">To install a self-signed certificate in the Trusted Root Certification Authorities</span></span>

1. <span data-ttu-id="b6ef8-134">Otevřete modul snap-in Certifikáty.</span><span class="sxs-lookup"><span data-stu-id="b6ef8-134">Open the certificate snap-in.</span></span> <span data-ttu-id="b6ef8-135">Další informace najdete v tématu [Postup: zobrazení certifikátů pomocí modulu snap-in konzoly MMC](how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="b6ef8-135">For more information, see [How to: View Certificates with the MMC Snap-in](how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>

2. <span data-ttu-id="b6ef8-136">Otevřete složku pro uložení certifikátu, buď **místního počítače** , nebo **aktuálního uživatele**.</span><span class="sxs-lookup"><span data-stu-id="b6ef8-136">Open the folder to store the certificate, either the **Local Computer** or the **Current User**.</span></span>

3. <span data-ttu-id="b6ef8-137">Otevřete složku **důvěryhodných kořenových certifikačních autorit** .</span><span class="sxs-lookup"><span data-stu-id="b6ef8-137">Open the **Trusted Root Certification Authorities** folder.</span></span>

4. <span data-ttu-id="b6ef8-138">Klikněte pravým tlačítkem na složku **certifikáty** , klikněte na **všechny úlohy**a pak klikněte na **importovat**.</span><span class="sxs-lookup"><span data-stu-id="b6ef8-138">Right-click the **Certificates** folder and click **All Tasks**, then click **Import**.</span></span>

5. <span data-ttu-id="b6ef8-139">Postupujte podle pokynů Průvodce na obrazovce a importujte soubor RootCA. pfx do úložiště.</span><span class="sxs-lookup"><span data-stu-id="b6ef8-139">Follow the on-screen wizard instructions to import the RootCA.pfx into the store.</span></span>

## <a name="using-certificates-with-wcf"></a><span data-ttu-id="b6ef8-140">Používání certifikátů pomocí WCF</span><span class="sxs-lookup"><span data-stu-id="b6ef8-140">Using certificates With WCF</span></span>

<span data-ttu-id="b6ef8-141">Po nastavení dočasných certifikátů je můžete použít k vývoji řešení WCF, která určují certifikáty jako typ pověření klienta.</span><span class="sxs-lookup"><span data-stu-id="b6ef8-141">Once you have set up the temporary certificates, you can use them to develop WCF solutions that specify certificates as a client credential type.</span></span> <span data-ttu-id="b6ef8-142">Například následující konfigurace XML určuje zabezpečení zprávy a certifikát jako typ přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="b6ef8-142">For example, the following XML configuration specifies message security and a certificate as the client credential type.</span></span>

### <a name="to-specify-a-certificate-as-the-client-credential-type"></a><span data-ttu-id="b6ef8-143">Určení certifikátu jako typ přihlašovacích údajů klienta</span><span class="sxs-lookup"><span data-stu-id="b6ef8-143">To specify a certificate as the client credential type</span></span>

1. <span data-ttu-id="b6ef8-144">V konfiguračním souboru pro službu použijte následující kód XML pro nastavení režimu zabezpečení na zpráva a typ přihlašovacích údajů klienta na certifikát.</span><span class="sxs-lookup"><span data-stu-id="b6ef8-144">In the configuration file for a service, use the following XML to set the security mode to message, and the client credential type to certificate.</span></span>

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

2. <span data-ttu-id="b6ef8-145">V konfiguračním souboru pro klienta použijte následující kód XML k určení toho, že se certifikát nachází v úložišti uživatele, a lze jej najít hledáním pole Subject pro hodnotu "CohoWinery".</span><span class="sxs-lookup"><span data-stu-id="b6ef8-145">In the configuration file for a client, use the following XML to specify that the certificate is found in the user’s store, and can be found by searching the SubjectName field for the value "CohoWinery."</span></span>

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

<span data-ttu-id="b6ef8-146">Další informace o použití certifikátů v technologii WCF najdete v tématu [práce s certifikáty](working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="b6ef8-146">For more information about using certificates in WCF, see [Working with Certificates](working-with-certificates.md).</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="b6ef8-147">zabezpečení v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b6ef8-147">.NET Framework security</span></span>

<span data-ttu-id="b6ef8-148">Nezapomeňte odstranit dočasné certifikáty kořenové autority z **důvěryhodných kořenových certifikačních autorit** a **osobní** složky tak, že kliknete pravým tlačítkem na certifikát a pak kliknete na **Odstranit**.</span><span class="sxs-lookup"><span data-stu-id="b6ef8-148">Be sure to delete any temporary root authority certificates from the **Trusted Root Certification Authorities** and **Personal** folders by right-clicking the certificate, then clicking **Delete**.</span></span>

## <a name="see-also"></a><span data-ttu-id="b6ef8-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b6ef8-149">See also</span></span>

- [<span data-ttu-id="b6ef8-150">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="b6ef8-150">Working with Certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="b6ef8-151">Postupy: Zobrazení certifikátů pomocí modulu snap-in konzoly MMC</span><span class="sxs-lookup"><span data-stu-id="b6ef8-151">How to: View Certificates with the MMC Snap-in</span></span>](how-to-view-certificates-with-the-mmc-snap-in.md)
- [<span data-ttu-id="b6ef8-152">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="b6ef8-152">Securing Services and Clients</span></span>](securing-services-and-clients.md)
