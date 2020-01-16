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
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a>Postupy: vytváření dočasných certifikátů pro použití během vývoje

Při vývoji zabezpečené služby nebo klienta pomocí Windows Communication Foundation (WCF) je často nutné dodat certifikát X. 509, který se má použít jako přihlašovací údaje. Certifikát obvykle je součástí řetězce certifikátů s kořenovou autoritou, která se nachází v úložišti důvěryhodných kořenových certifikačních autorit počítače. Řetěz certifikátů vám umožní určit rozsah sady certifikátů, ve kterých je kořenová autorita z vaší organizace nebo organizační jednotky. Chcete-li tuto možnost emulovat v době vývoje, můžete vytvořit dva certifikáty, které splňují požadavky na zabezpečení. První je certifikát podepsaný svým držitelem, který je umístěn v úložišti důvěryhodných kořenových certifikačních autorit a druhý certifikát je vytvořen z prvního a je umístěn v osobním úložišti umístění místního počítače nebo osobního úložiště Aktuální umístění uživatele. Toto téma vás provede kroky k vytvoření těchto dvou certifikátů pomocí rutiny [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) prostředí PowerShell.

> [!IMPORTANT]
> Certifikáty, které generuje rutina New-SelfSignedCertificate, jsou k dispozici pouze pro účely testování. Při nasazování služby nebo klienta nezapomeňte použít příslušný certifikát poskytovaný certifikační autoritou. Může to být buď certifikát serveru Windows Server ve vaší organizaci, nebo třetí strana.
>
> Ve výchozím nastavení vytvoří rutina [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) certifikáty, které jsou podepsané svým držitelem, a tyto certifikáty jsou nezabezpečené. Umístění certifikátů podepsaných svým držitelem do úložiště důvěryhodných kořenových certifikačních autorit vám umožní vytvořit vývojové prostředí, které lépe simuluje prostředí nasazení.

 Další informace o vytváření a používání certifikátů najdete v tématu [práce s certifikáty](working-with-certificates.md). Další informace o použití certifikátu jako přihlašovacích údajů najdete v tématu [zabezpečení služeb a klientů](securing-services-and-clients.md). Kurz týkající se používání technologie Microsoft Authenticode naleznete v tématu [přehledy technologie Authenticode a kurzy](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537360(v=vs.85)).

## <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a>Vytvoření certifikátu kořenového úřadu podepsaného svým držitelem a export privátního klíče

Následující příkaz vytvoří certifikát podepsaný svým držitelem s názvem subjektu "RootCA" v aktuálním osobním úložišti uživatele.

```powershell
$rootcert = New-SelfSignedCertificate -CertStoreLocation Cert:\CurrentUser\My -DnsName "RootCA" -TextExtension @("2.5.29.19={text}CA=true") -KeyUsage CertSign,CrlSign,DigitalSignature
```

Musíme vyexportovat certifikát do souboru PFX, aby se mohl importovat do, kde bude potřeba v pozdějším kroku. Při exportu certifikátu s privátním klíčem je nutné zadat heslo k ochraně. Heslo ukládáme do `SecureString` a pomocí rutiny [Export-vybíráte](/powershell/module/pkiclient/export-pfxcertificate) vyexportujete certifikát s přidruženým privátním klíčem do souboru PFX. Do souboru CRT také ukládáme jenom veřejný certifikát pomocí rutiny [Export-Certificate](/powershell/module/pkiclient/export-certificate) .

```powershell
[System.Security.SecureString]$rootcertPassword = ConvertTo-SecureString -String "password" -Force -AsPlainText
[String]$rootCertPath = Join-Path -Path 'cert:\CurrentUser\My\' -ChildPath "$($rootcert.Thumbprint)"
Export-PfxCertificate -Cert $rootCertPath -FilePath 'RootCA.pfx' -Password $rootcertPassword
Export-Certificate -Cert $rootCertPath -FilePath 'RootCA.crt'
```

## <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a>Vytvoření nového certifikátu podepsaného certifikátem kořenové autority

Následující příkaz vytvoří certifikát podepsaný `RootCA`em s názvem subjektu "SignedByRootCA", který používá privátní klíč vystavitele.

```powershell
$testCert = New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "SignedByRootCA" -KeyExportPolicy Exportable -KeyLength 2048 -KeyUsage DigitalSignature,KeyEncipherment -Signer $rootCert
```

Podobně ukládáme podepsaný certifikát s privátním klíčem do souboru PFX a jenom veřejný klíč do souboru CRT.

```powershell
[String]$testCertPath = Join-Path -Path 'cert:\LocalMachine\My\' -ChildPath "$($testCert.Thumbprint)"
Export-PfxCertificate -Cert $testCertPath -FilePath testcert.pfx -Password $rootcertPassword
Export-Certificate -Cert $testCertPath -FilePath testcert.crt
```

## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a>Instalace certifikátu v úložišti důvěryhodných kořenových certifikačních autorit

Po vytvoření certifikátu podepsaného svým držitelem ho můžete nainstalovat v úložišti důvěryhodných kořenových certifikačních autorit. Všechny certifikáty, které jsou v tomto okamžiku podepsány certifikátem, jsou tímto počítačem důvěryhodné. Z tohoto důvodu odstraňte certifikát z úložiště, jakmile ho už nebudete potřebovat. Když odstraníte tento certifikát kořenové autority, všechny ostatní certifikáty, které s ním budou podepsané, se stanou neautorizovanými. Certifikáty kořenové autority jsou jednoduše mechanismem, který může podle potřeby vymezena skupina certifikátů. Například v aplikacích typu peer-to-peer není obvykle nutné, aby byla kořenová autorita, protože jednoduše důvěřujete identitě jednotlivce podle jeho poskytnutého certifikátu.

### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a>Instalace certifikátu podepsaného svým držitelem do důvěryhodných kořenových certifikačních autorit

1. Otevřete modul snap-in Certifikáty. Další informace najdete v tématu [Postup: zobrazení certifikátů pomocí modulu snap-in konzoly MMC](how-to-view-certificates-with-the-mmc-snap-in.md).

2. Otevřete složku pro uložení certifikátu, buď **místního počítače** , nebo **aktuálního uživatele**.

3. Otevřete složku **důvěryhodných kořenových certifikačních autorit** .

4. Klikněte pravým tlačítkem na složku **certifikáty** , klikněte na **všechny úlohy**a pak klikněte na **importovat**.

5. Postupujte podle pokynů Průvodce na obrazovce a importujte soubor RootCA. pfx do úložiště.

## <a name="using-certificates-with-wcf"></a>Používání certifikátů pomocí WCF

Po nastavení dočasných certifikátů je můžete použít k vývoji řešení WCF, která určují certifikáty jako typ pověření klienta. Například následující konfigurace XML určuje zabezpečení zprávy a certifikát jako typ přihlašovacích údajů klienta.

### <a name="to-specify-a-certificate-as-the-client-credential-type"></a>Určení certifikátu jako typ přihlašovacích údajů klienta

1. V konfiguračním souboru pro službu použijte následující kód XML pro nastavení režimu zabezpečení na zpráva a typ přihlašovacích údajů klienta na certifikát.

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

2. V konfiguračním souboru pro klienta použijte následující kód XML k určení toho, že se certifikát nachází v úložišti uživatele, a lze jej najít hledáním pole Subject pro hodnotu "CohoWinery".

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

Další informace o použití certifikátů v technologii WCF najdete v tématu [práce s certifikáty](working-with-certificates.md).

## <a name="net-framework-security"></a>zabezpečení v rozhraní .NET Framework

Nezapomeňte odstranit dočasné certifikáty kořenové autority z **důvěryhodných kořenových certifikačních autorit** a **osobní** složky tak, že kliknete pravým tlačítkem na certifikát a pak kliknete na **Odstranit**.

## <a name="see-also"></a>Viz také:

- [Práce s certifikáty](working-with-certificates.md)
- [Postupy: Zobrazení certifikátů pomocí modulu snap-in konzoly MMC](how-to-view-certificates-with-the-mmc-snap-in.md)
- [Zabezpečení služeb a klientů](securing-services-and-clients.md)
