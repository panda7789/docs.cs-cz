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
ms.openlocfilehash: 0177533f11b7dfa6c2561f1f519eacf8073bcd45
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62047942"
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a>Postupy: Zpřístupnění certifikátů X.509 pro WCF
Zpřístupnit certifikát X.509 do služby Windows Communication Foundation (WCF), musí kód aplikace zadejte název úložiště certifikátu a umístění. V některých případech se identita procesu, musí mít přístup k souboru, který obsahuje privátní klíč spojený s certifikátem X.509. K získání soukromého klíče přidružené k certifikátu v úložišti certifikátů X.509, WCF, musí mít oprávnění k tomuto. Ve výchozím nastavení můžete přístup pouze vlastník a účet System privátní klíč certifikátu.  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a>Pro zpřístupnění certifikátů X.509 pro WCF  
  
1. Zadejte účet, pod které WCF je spuštěna oprávnění ke čtení souboru, který obsahuje privátní klíč spojený s certifikátem X.509.  
  
    1. Zjistěte, zda WCF vyžaduje přístup pro čtení k privátnímu klíči certifikátu X.509.  
  
         Následující tabulka uvádí, zda privátní klíč musí být k dispozici při použití certifikátu X.509.  
  
        |Použití certifikátu X.509|privátní klíč|  
        |---------------------------|-----------------|  
        |Digitální podepisování odchozí zprávu protokolu SOAP.|Ano|  
        |Ověření podpisu příchozí zprávy protokolu SOAP.|Ne|  
        |Šifrování odchozí zprávu protokolu SOAP.|Ne|  
        |Dešifrování příchozí zprávy protokolu SOAP.|Ano|  
  
    2. Určete umístění úložiště certifikátů a název, který certifikát je uložen.  
  
         Úložiště certifikátů, ve kterém certifikát je uložen je zadat v kódu aplikace nebo v konfiguraci. Například následující příklad určuje, že certifikát je umístěn v `CurrentUser` úložiště certifikátů s názvem `My`.  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3. Určení, kde je umístěn privátní klíč pro certifikát v počítači pomocí [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) nástroj.  
  
         [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) nástroj vyžaduje název úložiště certifikátu, umístění úložiště certifikátů a něco, který jednoznačně identifikuje tento certifikát. Nástroj přijímá jako jedinečný identifikátor názvu subjektu certifikátu nebo jeho kryptografický otisk. Další informace o tom, jak určit kryptografický otisk certifikátu, naleznete v tématu [jak: Načtení kryptografického otisku certifikátu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
         Následující příklad kódu používá [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) nástroje k určení umístění privátního klíče pro certifikát v `My` ukládat v `CurrentUser` pomocí kryptografického otisku `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.  
  
        ```  
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4. Určete účet, ve které běží WCF.  
  
         Následující tabulka obsahuje podrobnosti o účtu, pod kterým běží WCF v daném scénáři.  
  
        |Scénář|Identita procesu|  
        |--------------|----------------------|  
        |Klient (konzole nebo aplikace WinForms).|Aktuálně přihlášeného uživatele.|  
        |Služba, která je v místním prostředí.|Aktuálně přihlášeného uživatele.|  
        |Služba, která je hostovaná ve službě IIS 6.0 ([!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]) nebo službu IIS 7.0 ([!INCLUDE[wv](../../../../includes/wv-md.md)]).|SÍŤOVÉ SLUŽBY|  
        |Službu, která je hostovaná v IIS 5.X ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]).|Řídí `<processModel>` element v souboru Machine.config. Je výchozího účtu ASPNET.|  
  
    5. Udělte oprávnění ke čtení souboru, který obsahuje privátní klíč k účtu, ve které WCF běží, pomocí nástroje, jako je například icacls.exe.  
  
         Následující příklad kódu upraví seznam řízení přístupu (DACL) pro zadaný soubor udělit čtení účtu síťové služby (: R) přístup k souboru.  
  
        ```  
        icacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /grant "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a>Viz také:

- [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md)
- [Postupy: Načtení kryptografického otisku certifikátu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
- [Práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
