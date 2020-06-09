---
title: Ověřování ze strany klienta
ms.date: 03/30/2017
ms.assetid: f0c1f805-1a81-4d0d-a112-bf5e2e87a631
ms.openlocfilehash: dce11ec2e3ef552c0c53e1faf89a12bc13b66ae0
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585321"
---
# <a name="client-validation"></a>Ověřování ze strany klienta
Služby často publikují metadata, aby umožňovaly automatické generování a konfiguraci typů proxy serveru klienta. Pokud není služba důvěryhodná, klientské aplikace by měly ověřit, že metadata odpovídají zásadám klientské aplikace týkající se zabezpečení, transakcí, typu kontraktu služby a tak dále. Následující příklad ukazuje, jak napsat chování koncového bodu klienta, který ověřuje koncový bod služby, aby bylo zajištěno, že je koncový bod služby bezpečně používán.  
  
 Služba zveřejňuje čtyři koncové body služby. První koncový bod používá WSDualHttpBinding, druhý koncový bod používá ověřování NTLM, třetí koncový bod umožňuje tok transakce a čtvrtý koncový bod používá ověřování založené na certifikátech.  
  
 Klient používá <xref:System.ServiceModel.Description.MetadataResolver> třídu k načtení metadat pro službu. Klient vynutil zásadu zakázání duplexních vazeb, ověřování NTLM a toku transakce pomocí chování ověřování. Pro každou <xref:System.ServiceModel.Description.ServiceEndpoint> instanci importovanou z metadat služby přidá klientská aplikace `InternetClientValidatorBehavior` do rozhraní <xref:System.ServiceModel.Description.ServiceEndpoint> před tím, než se pokusí použít klienta služby Windows Communication Foundation (WCF) pro připojení ke koncovému bodu instanci chování koncového bodu. Metoda chování se `Validate` spouští před voláním jakékoli operace služby a vynutila zásady klienta vyvoláním `InvalidOperationExceptions` .  
  
### <a name="to-build-the-sample"></a>Sestavení ukázky  
  
1. Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Spuštění ukázky na stejném počítači  
  
1. Otevřete Developer Command Prompt pro Visual Studio s oprávněními správce a spusťte Setup. bat z ukázkové instalační složky. Tím se nainstalují všechny certifikáty, které jsou potřebné ke spuštění ukázky.  
  
2. Spuštění aplikace služby z \service\bin\Debug.  
  
3. Spuštění klientské aplikace z \client\bin\Debug. Aktivita klienta se zobrazí v klientské aplikaci konzoly.  
  
4. Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
5. Po dokončení s ukázkou odeberte certifikáty spuštěním souboru Cleanup. bat. Další ukázky zabezpečení používají stejné certifikáty.  
  
### <a name="to-run-the-sample-across-computers"></a>Spuštění ukázky mezi počítači  
  
1. Na serveru v Developer Command Prompt pro Visual Studio spusťte s oprávněními správce, zadejte `setup.bat service` . Při spuštění `setup.bat` s `service` argumentem se vytvoří certifikát služby s plně kvalifikovaným názvem domény počítače a vyexportuje certifikát služby do souboru s názvem Service. cer.  
  
2. Na serveru upravte soubor App. config tak, aby odrážel nový název certifikátu. To znamená změnit `findValue` atribut v [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) elementu na plně kvalifikovaný název domény počítače.  
  
3. Zkopírujte soubor Service. cer z adresáře služby do adresáře klienta v klientském počítači.  
  
4. V klientovi otevřete Developer Command Prompt pro Visual Studio s oprávněními správce a zadejte `setup.bat client` . Při spuštění `setup.bat` s `client` argumentem se vytvoří klientský certifikát s názvem Client.com a exportuje se klientský certifikát do souboru s názvem Client. cer.  
  
5. V souboru client.cs změňte hodnotu adresy koncového bodu MEX a `findValue` nastavte výchozí certifikát serveru tak, aby odpovídal nové adrese vaší služby. To provedete tak, že nahradíte localhost názvem domény pro plně kvalifikovaný název domény serveru. Znovu sestavit.  
  
6. Zkopírujte soubor Client. cer z adresáře klienta do adresáře služby na serveru.  
  
7. Na straně klienta spusťte ImportServiceCert. bat ve Developer Command Prompt pro Visual Studio otevřené s oprávněními správce. Tím se certifikát služby importuje ze souboru Service. cer do úložiště CurrentUser-TrustedPeople.  
  
8. Na serveru spusťte ImportClientCert. bat ve Developer Command Prompt pro Visual Studio otevřené s oprávněními správce. Tím se certifikát klienta importuje ze souboru Client. cer do úložiště LocalMachine-TrustedPeople.  
  
9. Na počítači služby Sestavte projekt služby v aplikaci Visual Studio a spusťte Service. exe.  
  
10. V klientském počítači spusťte soubor Client. exe.  
  
    1. Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Vyčištění po ukázce  
  
- Po dokončení ukázky spusťte na složce Samples Cleanup. bat.  
  
    > [!NOTE]
    > Tento skript při spuštění této ukázky mezi počítači neodebere certifikáty služby na klientovi. Pokud jste spustili ukázky WCF, které používají certifikáty napříč počítači, ujistěte se, že jste vymazali certifikáty služby nainstalované v úložišti CurrentUser-TrustedPeople. K tomu použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>. For example: certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com` .  
  
## <a name="see-also"></a>Viz také

- [Používání metadat](../feature-details/using-metadata.md)
