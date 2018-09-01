---
title: 'Postupy: vytváření dočasných certifikátů pro použití během vývoje.'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], creating temporary certificates
- temporary certificates [WCF]
ms.assetid: bc5f6637-5513-4d27-99bb-51aad7741e4a
ms.openlocfilehash: d3b051c7ea152606721388ea35b6f508eada1c5d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43385174"
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a>Postupy: vytváření dočasných certifikátů pro použití během vývoje.
Při vývoji zabezpečenou službu nebo klienta s použitím Windows Communication Foundation (WCF), je často nutné zadat certifikát X.509, které se použijí jako přihlašovací údaje. Certifikát je obvykle součástí řetěz certifikátů s kořenovou autoritou nalezen v úložišti důvěryhodných kořenových certifikačních autorit počítače. S řetěz certifikátů umožňuje určit obor sady certifikátů, kdy obvykle kořenová autorita je z vaší organizace nebo organizační jednotka. Pro emulaci to při vývoji, vytvoříte dva certifikáty splňovat požadavky na zabezpečení. První je certifikát podepsaný svým držitelem, který je umístěn v úložišti Důvěryhodné kořenové certifikační autority, a druhý certifikát je vytvořený z první a je umístěn v osobním úložišti umístění místního počítače nebo osobním úložišti Aktuální umístění uživatele. Toto téma vás provede kroky k vytvoření těchto dvou certifikáty pomocí [Certificate Creation Tool (MakeCert.exe)](https://go.microsoft.com/fwlink/?LinkId=248185), která poskytuje [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] SDK.  
  
> [!IMPORTANT]
>  Certifikáty, které generuje nástroj pro vytváření certifikační jsou k dispozici pouze pro účely testování. Při nasazování služby ani klienta, nezapomeňte použít příslušný certifikát k dispozici certifikační autoritou. To může být buď z [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] certifikátů serveru ve vaší organizaci nebo třetí strana.  
>   
>  Ve výchozím nastavení [Makecert.exe (Certificate Creation Tool)](https://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d) vytvoří certifikáty, jejichž kořenovou autoritou se nazývá "kořenový agentura **."** Protože agentura"Root" není v úložišti důvěryhodných kořenových certifikačních autorit, díky tomu tyto certifikáty nezabezpečené. Vytváří se certifikát podepsaný svým držitelem, který je umístěn v kořenové certifikační autority úložiště vám umožní vytvořit prostředí pro vývoj, která lépe napodobuje prostředí pro nasazení.  
  
 Další informace o vytváření a používání certifikátů najdete v tématu [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md). Další informace o používání certifikátu jako přihlašovací údaje, najdete v části [zabezpečení služeb a klientů](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md). Kurz o pomocí technologie Authenticode Microsoftu, najdete v tématu [Authenticode přehledy a kurzy](https://go.microsoft.com/fwlink/?LinkId=88919).  
  
### <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a>Vytvořit certifikát podepsaný svým držitelem kořenové autority a exportovat privátní klíč  
  
1.  Pomocí nástroje MakeCert.exe následující přepínače:  
  
    1.  `-n` `subjectName`. Určuje název předmětu. V rámci konvence se jako předpona názvu subjektu s "CN =" pro "Běžný název".  
  
    2.  `-r`. Určuje, zda certifikát podepsaný svým držitelem.  
  
    3.  `-sv` `privateKeyFile`. Určuje soubor, který obsahuje kontejner soukromého klíče.  
  
     Například následující příkaz vytvoří certifikát podepsaný svým držitelem se název předmětu "CN = TempCA."  
  
    ```  
    makecert -n "CN=TempCA" -r -sv TempCA.pvk TempCA.cer  
    ```  
  
     Zobrazí se výzva k zadání hesla k ochraně soukromého klíče. Toto heslo se vyžaduje při vytvoření certifikátu podepsány tento kořenový certifikát.  
  
### <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a>Chcete-li vytvořit nový certifikát podepsaný certifikátem kořenového certifikátu autority  
  
1.  Pomocí nástroje MakeCert.exe následující přepínače:  
  
    1.  `-sk` `subjectKey`. Umístění kontejneru klíče předmětu, který obsahuje privátní klíč. Pokud kontejner klíčů neexistuje, vytvoří se. Pokud žádná z možností – sk nebo - sv se používá, se standardně vytvoří kontejner klíče se nazývá JoeSoft.  
  
    2.  `-n` `subjectName`. Určuje název předmětu. V rámci konvence se jako předpona názvu subjektu s "CN =" pro "Běžný název".  
  
    3.  `-iv` `issuerKeyFile`. Určuje soubor privátního klíče vystavitele.  
  
    4.  `-ic` `issuerCertFile`. Určuje umístění certifikátu vystavitele.  
  
     Například následující příkaz vytvoří certifikát podepsaný službou `TempCA` kořenový certifikát autority s názvem subjektu `"CN=SignedByCA"` pomocí soukromého klíče vydavatele.  
  
    ```  
    makecert -sk SignedByCA -iv TempCA.pvk -n "CN=SignedByCA" -ic TempCA.cer SignedByCA.cer -sr currentuser -ss My  
    ```  
  
## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a>Instalace certifikátu v důvěryhodné Store autority certifikační kořenové  
 Jakmile se vytvoří certifikát podepsaný svým držitelem, můžete nainstalovat v úložišti Důvěryhodné kořenové certifikační autority. Všechny certifikáty, které jsou podepsány pomocí certifikátu v tomto okamžiku jsou důvěryhodné počítače. Z tohoto důvodu se odstraní certifikát z úložiště, jakmile ho už nepotřebují. Při odstranění tento kořenový certifikát autority stane neoprávněné všechny certifikáty, které s ním podepsané. Kořenových certifikátů úřadu slouží jednoduše jako mechanismus, kterým skupinu certifikátů můžete zařadit do oboru podle potřeby. Třeba aplikace peer-to-peer, není obvykle nutné pro kořenovou autoritou vzhledem k tomu, že důvěřujete identity individuální uživatel jednoduše podle jeho zadaný certifikát.  
  
#### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a>Chcete-li nainstalovat certifikát podepsaný svým držitelem v důvěryhodných kořenových certifikačních autorit  
  
1.  Otevřete modul snap-in certifikátu. Další informace najdete v tématu [postupy: zobrazení certifikátů pomocí modulu Snap-in konzoly MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
2.  Otevřete složku, která se má certifikát uložit buď **místního počítače** nebo **aktuálního uživatele**.  
  
3.  Otevřít **důvěryhodných kořenových certifikačních autorit** složky.  
  
4.  Klikněte pravým tlačítkem na **certifikáty** složky a klikněte na tlačítko **všechny úkoly**, pak klikněte na tlačítko **Import**.  
  
5.  Na obrazovce průvodce podle pokynů TempCa.cer naimportujte do úložiště.  
  
## <a name="using-certificates-with-wcf"></a>Použití certifikátů s použitím technologie WCF  
 Po nastavení dočasných certifikátů můžete je použít pro vývoj řešení pro WCF, které určují certifikáty jako typ pověření klienta. Například následující XML konfigurace určuje zabezpečení zpráv a certifikát jako typ pověření klienta.  
  
#### <a name="to-specify-a-certificate-as-the-client-credential-type"></a>Chcete-li určit certifikát jako typ pověření klienta  
  
-   V konfiguračním souboru pro službu použijte následující kód XML pro nastavení režimu zabezpečení zpráv a typu pověření klienta k certifikátu.  
  
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
  
 V konfiguračním souboru pro klienta použijte následující kód XML k určení, že certifikát je nalezena v úložišti uživatele a najdete tak, že pole SubjectName pro hodnotu "CohoWinery."  
  
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
  
 Další informace o používání certifikátů ve službě WCF najdete v tématu [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Nezapomeňte odstranit všechny dočasné kořenových certifikátů úřadu z **důvěryhodných kořenových certifikačních autorit** a **osobní** složek tak, že kliknete pravým tlačítkem certifikát, pak kliknutím na  **Odstranit**.  
  
## <a name="see-also"></a>Viz také  
 [Práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Postupy: Zobrazení certifikátů pomocí modulu snap-in konzoly MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)  
 [Zabezpečení služeb a klientů](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
