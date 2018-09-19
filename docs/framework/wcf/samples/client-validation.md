---
title: Ověřování ze strany klienta
ms.date: 03/30/2017
ms.assetid: f0c1f805-1a81-4d0d-a112-bf5e2e87a631
ms.openlocfilehash: 3f8b5ec3f8652ef50bbda3456669f2abf456472b
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46003955"
---
# <a name="client-validation"></a>Ověřování ze strany klienta
Služby často publikování metadat povolit automatické generování a konfigurace proxy serveru typů klientů. Pokud služba není důvěryhodný, klientské aplikace by měl ověřit, metadata odpovídá klientská aplikace zásady týkající se zabezpečení, transakce, typ kontraktu služby a tak dále. Následující příklad ukazuje, jak zapsat klienta chování koncového bodu, která ověřuje koncový bod služby k zajištění, že tento koncový bod služby je bezpečné používat.  
  
 Služba poskytuje čtyři koncových bodů služby. První koncový bod používá WSDualHttpBinding, druhý používá ověřování protokolem NTLM, třetí koncový bod umožňuje tok transakcí a čtvrtý koncový bod používá ověřování prostřednictvím certifikátu.  
  
 Klient použije <xref:System.ServiceModel.Description.MetadataResolver> třídy pro načtení metadat služby. Klient vynucuje zásady zakazující duplexní vazby, ověřování NTLM a toku transakce pomocí ověřování chování. Pro každou <xref:System.ServiceModel.Description.ServiceEndpoint> instance naimportované z metadat služby, klientská aplikace přidá instanci `InternetClientValidatorBehavior` chování koncového bodu <xref:System.ServiceModel.Description.ServiceEndpoint> před pokusem o používání klienta Windows Communication Foundation (WCF) pro připojení k koncový bod. Chování `Validate` metoda běží před voláním jakékoli operace ve službě jsou a vynucuje zásady klienta vyvoláním `InvalidOperationExceptions`.  
  
### <a name="to-build-the-sample"></a>K vytvoření vzorku  
  
1.  Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Ke spuštění ukázky ve stejném počítači  
  
1.  Otevřete příkazový řádek sady Visual Studio s oprávněními správce a spusťte Setup.bat z instalační složky s ukázkou. Tím se nainstaluje všechny certifikáty požadované ke spuštění ukázky.  
  
2.  Spusťte aplikaci služby z \service\bin\Debug.  
  
3.  Spuštění klientské aplikace z \client\bin\Debug. Činnost klienta se zobrazí na klientské aplikace konzoly.  
  
4.  Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy k řešení potíží s](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
5.  Odeberte certifikáty spuštěním Cleanup.bat po dokončení s ukázkou. Další ukázky zabezpečení použijte stejné certifikáty.  
  
### <a name="to-run-the-sample-across-computers"></a>Ke spuštění ukázky v počítačích  
  
1.  Na serveru, v příkazovém řádku aplikace Visual Studio spusťte s oprávněními správce, zadejte `setup.bat service`. Spuštění `setup.bat` s `service` argument vytvoří certifikát služby se plně kvalifikovaný název domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.  
  
2.  Na serveru upravte App.config tak, aby odrážely nový název certifikátu. To znamená, změnit `findValue` atribut [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) elementu plně kvalifikovaný název domény počítače.  
  
3.  Zkopírujte soubor Service.cer z adresáře služby k adresáři klienta v klientském počítači.  
  
4.  V klientském počítači, otevřete příkazový řádek sady Visual Studio s oprávněními správce a typ `setup.bat client`. Spuštění `setup.bat` s `client` argument vytvoří klientský certifikát s názvem Client.com a exportuje certifikát klienta do souboru s názvem Client.cer.  
  
5.  V souboru client.cs změnit hodnotu adresy koncového bodu MEX a `findValue` pro nastavení výchozí certifikát serveru tak, aby odpovídala nové adresu služby. Provedete to nahrazením localhost plně kvalifikovaný název domény serveru. Znovu sestavte.  
  
6.  Zkopírujte soubor Client.cer z adresáře klienta do adresáře služby na serveru.  
  
7.  Na straně klienta spouštění ImportServiceCert.bat v příkazovém řádku aplikace Visual Studio otevřeného s oprávněními správce. To importuje certifikát služby ze souboru Service.cer do CurrentUser - TrustedPeople úložiště.  
  
8.  Na serveru spusťte ImportClientCert.bat v příkazovém řádku aplikace Visual Studio otevřeného s oprávněními správce. To importuje klientský certifikát ze souboru Client.cer do úložiště LocalMachine - TrustedPeople úložiště.  
  
9. Na počítači se službou sestavte projekt služby v sadě Visual Studio a spusťte service.exe.  
  
10. Na klientském počítači spusťte client.exe.  
  
    1.  Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy k řešení potíží s](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-clean-up-after-the-sample"></a>K vyčištění po vzorku  
  
-   Spusťte Cleanup.bat ve složce samples po dokončení spuštění ukázky.  
  
    > [!NOTE]
    >  Tento skript neodebere certifikáty služeb v klientském počítači při spuštění této ukázky na počítačích. Pokud jste spustili Ukázky WCF, které používají certifikáty na počítačích, je nutné vymazat certifikáty služeb, které jsou nainstalovány v CurrentUser - TrustedPeople uložit. Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>. For example: certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="see-also"></a>Viz také  
 [Používání metadat](../../../../docs/framework/wcf/feature-details/using-metadata.md)
