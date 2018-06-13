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
ms.openlocfilehash: cd13eae0a72ceaf5abfb93dfe84a53cfc3c8dec4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493703"
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a>Postupy: Zpřístupnění certifikátů X.509 pro WCF
Chcete-li certifikát X.509 dostupné pro Windows Communication Foundation (WCF), musíte zadat kód aplikace na název úložiště certifikátu a umístění. V některých případech identita procesu, musí mít přístup k souboru, který obsahuje soukromý klíč spojenou s certifikátem X.509. Pokud chcete získat soukromý klíč přidružený k certifikátu X.509. certifikát v úložišti certifikátů, WCF musí mít oprávnění k tomu. Ve výchozím nastavení může pouze vlastník a systémový účet přístup k privátnímu klíči certifikátu.  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a>Pro zpřístupnění certifikátů X.509 pro WCF  
  
1.  Zadejte účet, pod které WCF je spuštěna přístup pro čtení k souboru, který obsahuje soukromý klíč spojenou s certifikátem X.509.  
  
    1.  Zjistěte, zda WCF vyžaduje přístup pro čtení k privátnímu klíči certifikátu X.509.  
  
         Následující tabulka uvádí, zda privátní klíč musí být k dispozici při použití certifikátu X.509.  
  
        |Použití certifikátu X.509|privátní klíč|  
        |---------------------------|-----------------|  
        |Digitální podepisování odchozí zprávu protokolu SOAP.|Ano|  
        |Ověření podpisu příchozí zprávy protokolu SOAP.|Ne|  
        |Šifrování odchozí zprávu protokolu SOAP.|Ne|  
        |Dešifrování příchozí zprávu protokolu SOAP.|Ano|  
  
    2.  Určete umístění úložiště certifikátu a název, který certifikát je uložen.  
  
         Úložiště certifikátů, ve kterém je uložený certifikát je zadána v kódu aplikace nebo v konfiguraci. Například následující příklad určuje, že certifikát nachází v `CurrentUser` úložiště certifikátů s názvem `My`.  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3.  Určení umístění privátní klíč pro certifikát v počítači pomocí [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) nástroj.  
  
         [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) nástroj vyžaduje název úložiště certifikátu, umístění úložiště certifikátu a něco, která jednoznačně identifikuje certifikát. Nástroj přijme název subjektu certifikátu nebo jeho kryptografický otisk jako jedinečný identifikátor. Další informace o tom, jak určit kryptografický otisk certifikátu najdete v tématu [postupy: načtení kryptografického otisku certifikátu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
         Následující příklad kódu používá [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) nástroj k určení umístění privátního klíče certifikátu v `My` Uložit `CurrentUser` s kryptografickým otiskem `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.  
  
        ```  
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4.  Určete účet, který je spuštěno WCF.  
  
         V následující tabulce jsou účtu, pod kterým běží WCF v daném scénáři.  
  
        |Scénář|Identitě procesu|  
        |--------------|----------------------|  
        |Klient (konzole nebo WinForms aplikace).|Aktuálně přihlášeného uživatele.|  
        |Služba, která se hostuje sama.|Aktuálně přihlášeného uživatele.|  
        |Služby, který je hostován ve službě IIS 6.0 ([!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]) nebo IIS 7.0 ([!INCLUDE[wv](../../../../includes/wv-md.md)]).|SÍŤOVÉ SLUŽBY|  
        |Službu, která je hostovaná v IIS 5.X ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]).|Řízené `<processModel>` element v souboru Machine.config. Je výchozího účtu ASPNET.|  
  
    5.  Udělte oprávnění ke čtení k souboru, který obsahuje soukromý klíč k účtu, který WCF je spuštěná s pověřeními, pomocí nástroje, jako je cacls.exe.  
  
         Následující kód například úpravy (/ E) seznamu řízení přístupu (ACL) pro zadaný soubor udělit (/ G) účet NETWORK SERVICE pro čtení (: R) přístup k souboru.  
  
        ```  
        cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a>Viz také  
 [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md)  
 [Postupy: Načtení kryptografického otisku certifikátu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)  
 [Práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
