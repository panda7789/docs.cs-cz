---
title: 'Postupy: Zpřístupnění certifikátů X.509 pro WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- X.509 certificates [WCF]
- certificates [WCF], making X.509 certificates accessible to WCF
- X.509 certificates [WCF], making accessible to WCF
ms.assetid: a54e407c-c2b5-4319-a648-60e43413664b
ms.openlocfilehash: 401371bf01a62a20f2834cb76df19d9ddaacf83d
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972357"
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a>Postupy: Zpřístupnění certifikátů X.509 pro WCF
Aby byl certifikát X. 509 přístupný Windows Communication Foundation (WCF), kód aplikace musí určovat název a umístění úložiště certifikátů. V určitých případech musí mít identita procesu přístup k souboru, který obsahuje privátní klíč přidružený k certifikátu X. 509. K získání privátního klíče přidruženého k certifikátu X. 509 v úložišti certifikátů musí mít WCF oprávnění k tomu. Ve výchozím nastavení má přístup k privátnímu klíči certifikátu pouze vlastník a systémový účet.  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a>Zpřístupnění certifikátů X. 509 pro WCF  
  
1. Udělte účtu, pod kterým má WCF spuštěný přístup pro čtení k souboru, který obsahuje privátní klíč přidružený k certifikátu X. 509.  
  
    1. Určete, zda WCF vyžaduje přístup pro čtení k privátnímu klíči pro certifikát X. 509.  
  
         Následující tabulka popisuje, jestli musí být při použití certifikátu X. 509 k dispozici privátní klíč.  
  
        |Použití certifikátu X. 509|Privátní klíč|  
        |---------------------------|-----------------|  
        |Digitální podepisování odchozí zprávy SOAP.|Ano|  
        |Ověřuje se podpis příchozí zprávy SOAP.|Ne|  
        |Šifrování odchozí zprávy SOAP.|Ne|  
        |Probíhá dešifrování příchozí zprávy protokolu SOAP.|Ano|  
  
    2. Určete umístění a název úložiště certifikátů, ve kterém je certifikát uložený.  
  
         Úložiště certifikátů, ve kterém je certifikát uložený, je zadané buď v kódu aplikace, nebo v konfiguraci. Například následující příklad určuje, že certifikát je umístěn v `CurrentUser` úložišti certifikátů s názvem. `My`  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3. Pomocí nástroje [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) určete, kde se privátní klíč pro certifikát nachází v počítači.  
  
         Nástroj [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) vyžaduje název úložiště certifikátů, umístění úložiště certifikátů a něco, co certifikát jedinečně identifikuje. Nástroj přijme buď název předmětu certifikátu, nebo jeho kryptografický otisk jako jedinečný identifikátor. Další informace o tom, jak určit kryptografický otisk certifikátu, najdete v tématu [How to: Načtení kryptografického otisku certifikátu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
         Následující příklad kódu používá nástroj [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) k určení umístění privátního klíče pro certifikát v `My` úložišti v `CurrentUser` nástroji s kryptografickým otiskem `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.  
  
        ```console
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4. Určete účet, pod kterým je WCF spuštěno.  
  
         Následující tabulka podrobně popisuje účet, pod kterým je WCF spuštěno pro daný scénář.  
  
        |Scénář|Identita procesu|  
        |--------------|----------------------|  
        |Klient (aplikace konzoly nebo WinForms).|Aktuálně přihlášený uživatel.|  
        |Služba, která je samostatně hostována.|Aktuálně přihlášený uživatel.|  
        |Služba, která je hostovaná ve službě[!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]IIS 6,0 () nebo[!INCLUDE[wv](../../../../includes/wv-md.md)]IIS 7,0 ().|SÍŤOVÁ SLUŽBA|  
        |Služba, která je hostována ve službě IIS 5[!INCLUDE[wxp](../../../../includes/wxp-md.md)]. X ().|`<processModel>` Řízeno prvkem v souboru Machine. config. Výchozí účet je ASPNET.|  
  
    5. Udělte oprávnění ke čtení souboru, který obsahuje privátní klíč, k účtu, pod kterým běží WCF, pomocí nástroje, jako je Icacls. exe.  
  
         Následující příklad kódu upraví volitelný seznam řízení přístupu (DACL) pro zadaný soubor a udělí účtu síťové služby čtení (: R) přístup k souboru.  
  
        ```console 
        icacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /grant "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a>Viz také:

- [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md)
- [Postupy: Načtení kryptografického otisku certifikátu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
- [Práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
