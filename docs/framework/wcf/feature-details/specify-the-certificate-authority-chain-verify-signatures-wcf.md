---
title: 'Postupy: Zadání řetězu certifikátů certifikační autority používaného k ověřování podpisů (WCF)'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], specifying the certificate authority certificate chain
- certificates [WCF], verifying signatures
ms.assetid: 7c719355-aa41-4567-80d0-5115a8cf73fd
ms.openlocfilehash: 9e2ba9f3550442602cab217fec329e6c19efd3b3
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47080822"
---
# <a name="how-to-specify-the-certificate-authority-certificate-chain-used-to-verify-signatures-wcf"></a>Postupy: Zadání řetězu certifikátů certifikační autority používaného k ověřování podpisů (WCF)
Přijetí Windows Communication Foundation (WCF) protokolu SOAP zprávy podepsány pomocí certifikátu X.509, ve výchozím nastavení ověřuje, že certifikát X.509 byl vydán důvěryhodnou certifikační autoritou. To se provádí vyhledávání v úložišti certifikátů a určení, pokud certifikát u této certifikační autoritě je určený jako důvěryhodné. Aby WCF za účelem určení musí být nainstalována řetěz certifikátů certifikační autority v úložišti certifikátů správné.  
  
### <a name="to-install-a-certification-authority-certificate-chain"></a>Chcete-li nainstalovat řetěz certifikátů certifikační autority  
  
-   Pro každou certifikační autoritu, která si klade za cíl příjemce zprávy protokolu SOAP důvěřovat instalaci certifikátů X.509 vystavených, řetěz certifikátů certifikační autority do úložiště certifikátů, WCF je nakonfigurován k načtení certifikátů X.509 z.  
  
     Například pokud příjemce zprávu protokolu SOAP v úmyslu důvěřovat společnost Microsoft vydá nové certifikáty X.509, řetěz certifikátů certifikační autority pro Microsoft musí být nainstalován v úložišti certifikátů, které WCF je nastaven na Hledat certifikáty X.509. Úložiště certifikátů, ve kterém hledá WCF certifikáty X.509 je zadat v kódu nebo konfigurace. Například můžete zadat v kódu pomocí <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metoda nebo v konfiguraci několika způsoby, třeba [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) .  
  
     Protože Windows se dodává se sadou výchozích řetězy certifikátů pro důvěryhodné certifikační autority, nemusí být potřeba instalovat řetěz certifikátů pro všechny certifikační autority.  
  
    1.  Exportujte řetěz certifikátů certifikační autority.  
  
         Přesně jak je to závisí na certifikační autoritě. Pokud certifikační autorita běží certifikační služby společnosti Microsoft, vyberte **stáhnout certifikát certifikační Autority, řetěz certifikátů nebo seznam CRL**a klikněte na tlačítko **stáhnout certifikát certifikační Autority**.  
  
    2.  Importujte řetěz certifikátů certifikační autority.  
  
         V Microsoft Management Console (MMC), otevřete modul snap-in Certifikáty. Úložiště certifikátů je nakonfigurovaný tento WCF načíst certifikáty X.509 z vyberte **důvěryhodné kořenové** **certifikačních autorit** složky. V části **důvěryhodných kořenových certifikačních autorit** složky, klikněte pravým tlačítkem na **certifikáty** složku, přejděte na příkaz **všechny úkoly**a potom klikněte na tlačítko **Import** . Zadejte soubor exportovali v kroku.  
  
         Další informace o pomocí modulu snap-in Certifikáty konzoly MMC, naleznete v tématu [postupy: zobrazení certifikátů pomocí modulu Snap-in konzoly MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
## <a name="see-also"></a>Viz také  
 [Práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
