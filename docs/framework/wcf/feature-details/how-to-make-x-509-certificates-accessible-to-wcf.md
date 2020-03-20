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
ms.openlocfilehash: 14f2242ab55795c74fa169382fef846bc0e60ace
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184899"
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a>Postupy: Zpřístupnění certifikátů X.509 pro WCF
Chcete-li zpřístupnit certifikát X.509 systému Windows Communication Foundation (WCF), musí kód aplikace určit název a umístění úložiště certifikátů. Za určitých okolností musí mít identita procesu přístup k souboru, který obsahuje soukromý klíč přidružený k certifikátu X.509. Chcete-li získat soukromý klíč přidružený k certifikátu X.509 v úložišti certifikátů, wcf musí mít oprávnění k tomu. Ve výchozím nastavení může k soukromému klíči certifikátu přistupovat pouze vlastník a systémový účet.  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a>Zpřístupnění certifikátů X.509 wcf  
  
1. Podejte účet, pod kterým WCF je spuštěn přístup pro čtení do souboru, který obsahuje soukromý klíč přidružený k certifikátu X.509.  
  
    1. Zjistěte, zda WCF vyžaduje přístup pro čtení k soukromému klíči pro certifikát X.509.  
  
         V následující tabulce je podrobně uveden, zda musí být soukromý klíč k dispozici při použití certifikátu X.509.  
  
        |Použití certifikátu X.509|Privátní klíč|  
        |---------------------------|-----------------|  
        |Digitální podepisování odchozí zprávy SOAP.|Ano|  
        |Ověření podpisu příchozí zprávy SOAP.|Ne|  
        |Šifrování odchozí zprávy SOAP.|Ne|  
        |Dešifrování příchozí zprávy SOAP.|Ano|  
  
    2. Určete umístění úložiště certifikátů a název, ve kterém je certifikát uložen.  
  
         Úložiště certifikátů, ve kterém je certifikát uložen, je určeno v kódu aplikace nebo v konfiguraci. Například následující příklad určuje, že certifikát je `CurrentUser` umístěn `My`v úložišti certifikátů s názvem .  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3. Zjistěte, kde je soukromý klíč certifikátu umístěn v počítači pomocí nástroje [NajítprivateKey.](../../../../docs/framework/wcf/samples/findprivatekey.md)  
  
         Nástroj [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) vyžaduje název úložiště certifikátů, umístění úložiště certifikátů a něco, co jednoznačně identifikuje certifikát. Nástroj přijímá název předmětu certifikátu nebo jeho kryptografický otisk jako jedinečný identifikátor. Další informace o tom, jak určit kryptografický otisk certifikátu, naleznete v tématu [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
         Následující příklad kódu používá nástroj [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) k určení umístění soukromého `My` klíče `CurrentUser` pro certifikát v `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`úložišti v úložišti pomocí kryptografického otisku .  
  
        ```console
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4. Určete účet, pod kterým je wcf spuštěn.  
  
         V následující tabulce je podrobně uveden účet, pod kterým wcf běží pro daný scénář.  
  
        |Scénář|Identita procesu|  
        |--------------|----------------------|  
        |Klient (konzola nebo aplikace WinForms).|Aktuálně přihlášený uživatel.|  
        |Služba, která je hostována samostatně.|Aktuálně přihlášený uživatel.|  
        |Služba hostovaná ve službě IIS 6.0 (Windows Server 2003) nebo IIS 7.0 (Windows Vista).|SÍŤOVÁ SLUŽBA|  
        |Služba hostovaná ve službě IIS 5.X (Windows XP).|Řízeno `<processModel>` prvkem v souboru Machine.config. Výchozí účet je ASPNET.|  
  
    5. Udělit přístup pro čtení do souboru, který obsahuje soukromý klíč k účtu, který WCF je spuštěna pod pomocí nástroje, jako je například icacls.exe.  
  
         Následující příklad kódu upevrdne volitelný seznam řízení přístupu (DACL) pro zadaný soubor, aby účet SÍŤOVÉ SLUŽBY získal přístup k souboru.The following code example uetily the discretionary access control list (DACL) for the specified file to grant the NETWORK SERVICE account read (:R) access to the file.  
  
        ```console
        icacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /grant "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a>Viz také

- [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md)
- [Postupy: Načtení kryptografického otisku certifikátu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
- [Práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
