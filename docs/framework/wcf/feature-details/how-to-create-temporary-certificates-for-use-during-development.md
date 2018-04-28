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
ms.openlocfilehash: ccbc8c6fa638c674dea28c312b2dedbc9d41968a
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a>Postupy: vytváření dočasných certifikátů pro použití při vývoji
Při vývoji zabezpečení služby nebo klienta s použitím [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], je často potřeba zadat certifikát X.509, který se má použít jako pověření. Certifikát je obvykle součástí řetěz certifikátů s kořenovou autoritou nalezen v úložišti Důvěryhodné kořenové certifikační autority počítače. S řetěz certifikátů umožňuje určit obor sadu certifikáty, které obvykle kořenovou autoritou je z vaší organizace nebo organizační jednotka. To emulovat v době vývoje, můžete vytvořit dva certifikáty splňovat požadavky na zabezpečení. První je certifikát podepsaný svým držitelem, který je umístěn v úložišti důvěryhodných kořenových certifikačních autorit a druhý certifikát je vytvořený z první a je umístěn v osobním úložišti umístění místního počítače nebo osobním úložišti Aktuální umístění uživatele. Toto téma vás provede kroky k vytvoření těchto dvou certifikátů pomocí [nástroje vytvoření certifikátu (MakeCert.exe)](http://go.microsoft.com/fwlink/?LinkId=248185), poskytnutá [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] SDK.  
  
> [!IMPORTANT]
>  Certifikáty, které generuje nástroj pro vytváření certifikační jsou k dispozici jenom pro účely testování. Pokud nasazujete službu nebo klienta, je nutné používat příslušný certifikát od certifikační autority. To může být buď z [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] certifikátů serveru ve vaší organizaci nebo třetí strany.  
>   
>  Ve výchozím nastavení [Makecert.exe (nástroj pro vytvoření certifikátu)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d) vytvoří certifikáty, jejichž kořenové autority se označuje jako "kořenový agentura **."** Protože agentura"kořenový" není v úložišti důvěryhodných kořenových certifikačních autorit, díky tyto certifikáty nezabezpečené. Vytvořit certifikát podepsaný svým držitelem, který je umístěn v důvěryhodných kořenových certifikačních autorit úložiště můžete vytvořit prostředí pro vývoj, která simuluje přesněji prostředí pro nasazení.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] vytváření a používání certifikátů, najdete v části [práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)] pomocí certifikátu jako přihlašovací údaje, najdete v tématu [zabezpečení služeb a klientů](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md). Podívejte se kurz o pomocí technologie Microsoft Authenticode [Authenticode přehledy a kurzy](http://go.microsoft.com/fwlink/?LinkId=88919).  
  
### <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a>Chcete-li vytvořit certifikát podepsaný svým držitelem kořenové autority a exportovat soukromý klíč  
  
1.  Pomocí nástroje MakeCert.exe s následující přepínače:  
  
    1.  `-n` `subjectName`. Určuje název předmětu. Konvence je jako předpona názvu subjektu s "CN =" pro "Běžný název".  
  
    2.  `-r`. Určuje, že bude certifikát podepsaný svým držitelem.  
  
    3.  `-sv` `privateKeyFile`. Určuje soubor, který obsahuje kontejner soukromého klíče.  
  
     Například následující příkaz vytvoří certifikát podepsaný svým držitelem s názvem subjektu "CN = TempCA."  
  
    ```  
    makecert -n "CN=TempCA" -r -sv TempCA.pvk TempCA.cer  
    ```  
  
     Zobrazí se výzva k zadání hesla k ochraně soukromého klíče. Heslo je vyžadováno, při vytváření certifikát podepsaný tento kořenový certifikát.  
  
### <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a>Chcete-li vytvořit nový certifikát podepsaný službou kořenového certifikátu autority  
  
1.  Pomocí nástroje MakeCert.exe s následující přepínače:  
  
    1.  `-sk` `subjectKey`. Umístění kontejneru klíčů daného subjektu, který obsahuje soukromý klíč. Pokud kontejner klíčů neexistuje, je vytvořen jeden. Pokud žádná z možností -sk nebo - sv se používá, se ve výchozím nastavení vytvoří kontejner klíčů názvem JoeSoft.  
  
    2.  `-n` `subjectName`. Určuje název předmětu. Konvence je jako předpona názvu subjektu s "CN =" pro "Běžný název".  
  
    3.  `-iv` `issuerKeyFile`. Určuje soubor privátního klíče vystavitele.  
  
    4.  `-ic` `issuerCertFile`. Určuje umístění vystavitele certifikátu.  
  
     Například následující příkaz vytvoří certifikát podepsaný službou `TempCA` kořenové autority s názvem subjektu `"CN=SignedByCA"` pomocí soukromého klíče vystavitele.  
  
    ```  
    makecert -sk SignedByCA -iv TempCA.pvk -n "CN=SignedByCA" -ic TempCA.cer SignedByCA.cer -sr currentuser -ss My  
    ```  
  
## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a>Instalace certifikátu do důvěryhodného úložiště kořenové certifikační autority  
 Jakmile se vytvoří certifikát podepsaný svým držitelem, můžete ji nainstalovat v úložišti důvěryhodných kořenových certifikačních autorit. Všechny certifikáty, které jsou podepsané certifikátem v tomto okamžiku jsou důvěryhodné počítače. Z tohoto důvodu odstraňte certifikát z úložiště, jakmile ji už nepotřebujete. Při odstranění tohoto kořenového certifikátu autority, stane neoprávněným všechny další certifikáty, které s ním podepsané. Certifikáty kořenové autority se jednoduše mechanismus které může být skupinu certifikáty vymezena podle potřeby. Například v aplikacích peer-to-peer, je obvykle není nutné mít kořenovou autoritou vzhledem k tomu, že důvěřujete identitě osoby, jednoduše podle jeho poskytnutý certifikát.  
  
#### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a>Chcete-li nainstalovat certifikát podepsaný svým držitelem v důvěryhodné kořenové certifikační autority  
  
1.  Otevřete modul snap-in certifikátů. Další informace najdete v tématu [postupy: zobrazení certifikátů pomocí modulu Snap-in konzoly MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
2.  Otevřete složku, která se má certifikát uložit buď **místního počítače** nebo **aktuální uživatel**.  
  
3.  Otevřete **důvěryhodné kořenové certifikační autority** složky.  
  
4.  Klikněte pravým tlačítkem myši **certifikáty** složky a klikněte na tlačítko **všechny úlohy**, pak klikněte na tlačítko **Import**.  
  
5.  Na obrazovce průvodce podle pokynů k importu TempCa.cer do úložiště.  
  
## <a name="using-certificates-with-wcf"></a>Použití certifikátů s WCF  
 Jakmile jste nastavili dočasné certifikáty, můžete je používat pro vývoj řešení WCF, které určují certifikáty jako typ pověření klienta. Například následující konfigurační soubor XML určuje zabezpečení zpráv a certifikátu jako typ pověření klienta.  
  
#### <a name="to-specify-a-certificate-as-the-client-credential-type"></a>K určení certifikátu jako typ pověření klienta  
  
-   V konfiguračním souboru pro službu použijte následující kód XML nastavení režimu zabezpečení na zprávu a typ pověření klienta k certifikátu.  
  
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
  
 V konfiguračním souboru pro klienta použijte následující kód XML k určení, že je certifikát nalezen v úložišti uživatele a můžete najít tak, že SubjectName pole pro tuto hodnotu "CohoWinery."  
  
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
  
 Další informace o používání certifikátů ve službě WCF najdete v tématu [práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Nezapomeňte odstranit všechny dočasné kořenových certifikátů úřadu z **důvěryhodné kořenové certifikační autority** a **osobní** složky tak, že kliknete pravým tlačítkem na certifikát, pak kliknutím na tlačítko  **Odstranit**.  
  
## <a name="see-also"></a>Viz také  
 [Práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Postupy: Zobrazení certifikátů pomocí modulu snap-in konzoly MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)  
 [Zabezpečení služeb a klientů](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
