---
title: "Postupy: Zadání řetězu certifikátů certifikační autority používaného k ověřování podpisů (WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates [WCF], specifying the certificate authority certificate chain
- certificates [WCF], verifying signatures
ms.assetid: 7c719355-aa41-4567-80d0-5115a8cf73fd
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ce846d5637c6d49b4a3b1c6f28ae533e4900f696
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-specify-the-certificate-authority-certificate-chain-used-to-verify-signatures-wcf"></a>Postupy: Zadání řetězu certifikátů certifikační autority používaného k ověřování podpisů (WCF)
Když [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] obdrží zprávu protokolu SOAP podepsána pomocí certifikátu X.509, ve výchozím nastavení ověřuje, že certifikát X.509 byl vydán důvěryhodnou certifikační autoritou. K tomu je potřeba vyhledávání v úložišti certifikátů a určení, pokud pro tento certifikační autorita je klasifikován jako důvěryhodný certifikát. Aby [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] za účelem určení, musí být nainstalován řetězu certifikátů certifikační autority v úložišti certifikátů správné.  
  
### <a name="to-install-a-certification-authority-certificate-chain"></a>Chcete-li nainstalovat řetěz certifikátů certifikační autority  
  
-   Pro každý certifikační autoritu, kterou chce příjemce zprávu protokolu SOAP důvěřovat vystavené certifikáty X.509, který ukládání instalace řetězu certifikátů certifikační autority do certifikátu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] je nakonfigurován k načtení certifikátů X.509 z.  
  
     Například pokud příjemce zprávu protokolu SOAP v úmyslu důvěřovat certifikátů X.509 vystavených společností Microsoft, řetězu certifikátů certifikační autority pro Microsoft musí být nainstalován v certifikátu uložit, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nastavena tak, aby Hledat certifikáty X.509 z. Úložiště certifikátů, ve kterém [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vypadá pro certifikáty X.509 lze zadat v kódu nebo konfigurace. Například můžete zadat v kódu pomocí <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metoda nebo v konfiguraci několika způsoby, včetně [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) .  
  
     Protože systém Windows je dodáván s sadu výchozí řetězů certifikátů pro důvěryhodné certifikační autority, nemusí být potřeba instalovat řetěz certifikátů pro všechny certifikačních autorit.  
  
    1.  Exportujte řetězu certifikátů certifikační autority.  
  
         Přesně způsob provedení závisí na certifikační autoritě. Pokud certifikační autorita běží certifikační služby společnosti Microsoft, vyberte **stáhnout certifikát certifikační Autority, řetěz certifikátů nebo seznam CRL**a potom zvolte **stáhnout certifikát certifikační Autority**.  
  
    2.  Importujte řetězu certifikátů certifikační autority.  
  
         V Microsoft Management Console (MMC), otevřete modul snap-in Certifikáty. Pro certifikát úložiště, který [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] je nakonfigurován k načtení certifikátů X.509 z vyberte **důvěryhodné kořenové** **certifikačních autorit**složky. V části **důvěryhodné kořenové certifikační autority** složku, klikněte pravým tlačítkem myši **certifikáty**složku, přejděte na příkaz **všechny úlohy**a potom klikněte na **importu** . Zadejte soubor exportovali v kroku.  
  
         [!INCLUDE[crabout](../../../../includes/crabout-md.md)]pomocí modulu snap-in Certifikáty konzoly MMC, najdete v části [postupy: zobrazení certifikátů pomocí modulu Snap-in konzoly MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
## <a name="see-also"></a>Viz také  
 [Práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
