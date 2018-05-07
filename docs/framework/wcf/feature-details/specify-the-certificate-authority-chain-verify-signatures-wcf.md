---
title: 'Postupy: Zadání řetězu certifikátů certifikační autority používaného k ověřování podpisů (WCF)'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], specifying the certificate authority certificate chain
- certificates [WCF], verifying signatures
ms.assetid: 7c719355-aa41-4567-80d0-5115a8cf73fd
ms.openlocfilehash: 14f7691046f9512e25006bd6cd02749eed825003
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-specify-the-certificate-authority-certificate-chain-used-to-verify-signatures-wcf"></a>Postupy: Zadání řetězu certifikátů certifikační autority používaného k ověřování podpisů (WCF)
Když Windows Communication Foundation (WCF) obdrží zprávu protokolu SOAP podepsána pomocí certifikátu X.509, ve výchozím nastavení ověří, že certifikát X.509 byl vydán důvěryhodnou certifikační autoritou. K tomu je potřeba vyhledávání v úložišti certifikátů a určení, pokud pro tento certifikační autorita je klasifikován jako důvěryhodný certifikát. Aby WCF za účelem určení musí být nainstalován řetězu certifikátů certifikační autority v úložišti certifikátů správné.  
  
### <a name="to-install-a-certification-authority-certificate-chain"></a>Chcete-li nainstalovat řetěz certifikátů certifikační autority  
  
-   Pro každý certifikační autoritu, kterou chce příjemce zprávu protokolu SOAP důvěřovat certifikátů X.509 vystavených, nainstalujte řetězu certifikátů certifikační autority do úložiště certifikátů, že WCF je nakonfigurovaný k načtení certifikátů X.509 z.  
  
     Například pokud příjemce zprávu protokolu SOAP v úmyslu důvěřovat certifikátů X.509 vystavených společností Microsoft, řetězu certifikátů certifikační autority pro Microsoft musí být nainstalovaný v úložišti certifikátů, který je nastavený WCF a Hledat certifikáty X.509 z. Úložiště certifikátů, ve které WCF hledá certifikáty X.509 lze zadat v kódu nebo konfigurace. Například můžete zadat v kódu pomocí <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metoda nebo v konfiguraci několika způsoby, včetně [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) .  
  
     Protože systém Windows je dodáván s sadu výchozí řetězů certifikátů pro důvěryhodné certifikační autority, nemusí být potřeba instalovat řetěz certifikátů pro všechny certifikačních autorit.  
  
    1.  Exportujte řetězu certifikátů certifikační autority.  
  
         Přesně způsob provedení závisí na certifikační autoritě. Pokud certifikační autorita běží certifikační služby společnosti Microsoft, vyberte **stáhnout certifikát certifikační Autority, řetěz certifikátů nebo seznam CRL**a potom zvolte **stáhnout certifikát certifikační Autority**.  
  
    2.  Importujte řetězu certifikátů certifikační autority.  
  
         V Microsoft Management Console (MMC), otevřete modul snap-in Certifikáty. Úložiště certifikátů této WCF je nakonfigurované pro načtení certifikátů X.509 z vyberte **důvěryhodné kořenové** **certifikačních autorit**složky. V části **důvěryhodné kořenové certifikační autority** složku, klikněte pravým tlačítkem myši **certifikáty**složku, přejděte na příkaz **všechny úlohy**a potom klikněte na **importu** . Zadejte soubor exportovali v kroku.  
  
         Další informace o pomocí modulu snap-in Certifikáty konzoly MMC najdete v tématu [postupy: zobrazení certifikátů pomocí modulu Snap-in konzoly MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
## <a name="see-also"></a>Viz také  
 [Práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
