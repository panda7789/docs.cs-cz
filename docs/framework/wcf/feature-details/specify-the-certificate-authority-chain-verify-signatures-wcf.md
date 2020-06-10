---
title: 'Postupy: Zadání řetězu certifikátů certifikační autority používaného k ověřování podpisů (WCF)'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], specifying the certificate authority certificate chain
- certificates [WCF], verifying signatures
ms.assetid: 7c719355-aa41-4567-80d0-5115a8cf73fd
ms.openlocfilehash: 103d68d4ccb4cc243d28037260c1f9f380485ff6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600306"
---
# <a name="how-to-specify-the-certificate-authority-certificate-chain-used-to-verify-signatures-wcf"></a>Postupy: Zadání řetězu certifikátů certifikační autority používaného k ověřování podpisů (WCF)
Pokud Windows Communication Foundation (WCF) obdrží zprávu SOAP podepsaná pomocí certifikátu X. 509, ve výchozím nastavení ověří, že certifikát X. 509 byl vydán důvěryhodnou certifikační autoritou. Provedete to tak, že si vyhledáte úložiště certifikátů a určíte, jestli je certifikát pro tuto certifikační autoritu označený jako důvěryhodný. Aby mohl WCF toto určení provést, musí být řetěz certifikátů certifikační autority nainstalovaný ve správném úložišti certifikátů.  
  
### <a name="to-install-a-certification-authority-certificate-chain"></a>Instalace řetězu certifikátů certifikační autority  
  
- Pro každou certifikační autoritu, kterou příjemce zprávy protokolu SOAP zamýšlí důvěřovat certifikátům X. 509 vydaným z, nainstalujte řetěz certifikátů certifikační autority do úložiště certifikátů, ve kterém je WCF nakonfigurované pro načtení certifikátů X. 509.  
  
     Pokud například příjemce zprávy protokolu SOAP důvěřuje certifikátům X. 509 vydaných společností Microsoft, musí být v úložišti certifikátů, které je nastaveno pro technologii WCF, nainstalovaná certifikační autorita pro Microsoft, aby vyhledala certifikáty X. 509 z. Úložiště certifikátů, ve kterém bude WCF Hledat certifikáty X. 509, může být zadáno v kódu nebo v konfiguraci. To lze například zadat v kódu pomocí <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metody nebo v konfiguraci několika způsoby, včetně [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) .  
  
     Vzhledem k tomu, že se systém Windows dodává se sadou výchozích řetězů certifikátů pro důvěryhodné certifikační autority, nemusí být nutné instalovat řetěz certifikátů pro všechny certifikační autority.  
  
    1. Exportujte řetěz certifikátů certifikační autority.  
  
         Přesně to, jak se to dělá, závisí na certifikační autoritě. Pokud certifikační autorita používá službu Microsoft Certificate Services, vyberte **Stáhnout certifikát certifikační autority, řetěz certifikátů nebo seznam CRL**a pak zvolte **Stáhnout certifikát certifikační autority**.  
  
    2. Importujte řetěz certifikátů certifikační autority.  
  
         V konzole MMC (Microsoft Management Console) otevřete modul snap-in Certifikáty. V případě úložiště certifikátů, ze kterého je WCF nakonfigurované pro načtení certifikátů X. 509, vyberte složku **důvěryhodných kořenových** **certifikačních autorit** . Ve složce **Důvěryhodné kořenové certifikační autority** klikněte pravým tlačítkem na složku **certifikáty** , přejděte na **všechny úlohy**a klikněte na **importovat**. Zadejte soubor exportovaný v kroku a.  
  
         Další informace o použití modulu snap-in Certifikáty s konzolou MMC najdete v tématu [Postup: zobrazení certifikátů pomocí modulu snap-in konzoly MMC](how-to-view-certificates-with-the-mmc-snap-in.md).  
  
## <a name="see-also"></a>Viz také

- [Práce s certifikáty](working-with-certificates.md)
