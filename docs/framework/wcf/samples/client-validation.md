---
title: Ověřování ze strany klienta
ms.date: 03/30/2017
ms.assetid: f0c1f805-1a81-4d0d-a112-bf5e2e87a631
ms.openlocfilehash: 6e34ca8e1bb14f610e363c02eaeb94b7fa5e27c7
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="client-validation"></a>Ověřování ze strany klienta
Služby často publikování metadat povolit automatické generování a konfigurace různých typů klientů proxy serveru. Pokud služba není důvěryhodný, klientské aplikace by měl ověřit, že metadata, splňuje zásady klientské aplikace týkající se zabezpečení, transakce, typ kontrakt služby a tak dále. Následující příklad ukazuje, jak zapsat klienta chování koncového bodu, která ověřuje koncový bod služby k zajištění, že tento koncový bod služby lze bezpečně používat.  
  
 Službu zpřístupní čtyři koncové body služby. První koncový bod používá – WSDualHttpBinding, druhý koncový bod používá ověřování protokolem NTLM, třetí koncový bod umožňuje toku transakcí a čtvrtý koncový bod používá ověřování založené na certifikátu.  
  
 Klient použije <xref:System.ServiceModel.Description.MetadataResolver> třída načíst metadata pro službu. Klient vynucuje zásady zakazující duplexní vazby, ověřování protokolem NTLM a pomocí ověřování chování toku transakcí. Pro každou <xref:System.ServiceModel.Description.ServiceEndpoint> instance importovat z metadat služby, klientská aplikace přidá instanci `InternetClientValidatorBehavior` chování koncový bod <xref:System.ServiceModel.Description.ServiceEndpoint> před pokusem o používání klienta Windows Communication Foundation (WCF) pro připojení k koncový bod. Chování `Validate` metoda spustí před jakékoli operace služby, se nazývají a vynucuje zásady klienta po vyvolání výjimky `InvalidOperationExceptions`.  
  
### <a name="to-build-the-sample"></a>Chcete-li sestavit ukázku  
  
1.  Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Ke spuštění ukázky ve stejném počítači  
  
1.  Otevřete příkazový řádek sady Visual Studio s oprávněními správce a spusťte Setup.bat z ukázkové složky instalace. Tím se nainstaluje všechny certifikáty, které jsou potřebné ke spuštění ukázky.  
  
2.  Spusťte aplikaci služby z \service\bin\Debug.  
  
3.  Spusťte klientskou aplikaci z \client\bin\Debug. Činnost klienta se zobrazí na klientskou aplikaci konzoly.  
  
4.  Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
5.  Odeberte certifikáty spuštěním Cleanup.bat po dokončení se vzorkem. Další ukázky zabezpečení použijte stejné certifikáty.  
  
### <a name="to-run-the-sample-across-computers"></a>Ke spuštění ukázky mezi počítači  
  
1.  Na serveru, v příkazovém řádku Visual Studio spustit s oprávněními správce, zadejte `setup.bat service`. Spuštění `setup.bat` s `service` argument vytvoří certifikát služby s plně kvalifikovaný název domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.  
  
2.  Na serveru upravte App.config tak, aby odrážely novou název certifikátu. To znamená, změnit `findValue` atribut [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) element plně kvalifikovaný název domény počítače.  
  
3.  Zkopírujte soubor Service.cer z adresáře služby k adresáři klienta v klientském počítači.  
  
4.  Na klientovi, otevřete příkazový řádek sady Visual Studio s oprávněními správce a zadejte `setup.bat client`. Spuštění `setup.bat` s `client` argument vytvoří klientský certifikát s názvem Client.com a exportuje certifikát klienta do souboru s názvem Client.cer.  
  
5.  V souboru client.cs změňte hodnotu adresa koncového bodu MEX a `findValue` k nastavení výchozí certifikát serveru tak, aby odpovídala nové adresy vaší služby. Provedete to nahrazením localhost plně kvalifikovaný název domény serveru. Znovu sestavte.  
  
6.  Zkopírujte soubor Client.cer z adresáře klienta do adresáře služby na serveru.  
  
7.  V klientovi spusťte ImportServiceCert.bat v z příkazového řádku Visual Studia otevřít s oprávněními správce. Tento certifikát služby naimportuje ze souboru Service.cer do CurrentUser - TrustedPeople úložiště.  
  
8.  Na serveru spusťte ImportClientCert.bat v sadě Visual Studio příkazový řádek s oprávněními správce otevřít. Tento certifikát klienta naimportuje ze souboru Client.cer do LocalMachine - úložiště TrustedPeople.  
  
9. Na počítači se službou sestavte projekt služby v sadě Visual Studio a spusťte service.exe.  
  
10. Na klientském počítači spusťte client.exe.  
  
    1.  Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-clean-up-after-the-sample"></a>Vyčistěte po vzorku  
  
-   Po dokončení spuštění ukázky, spusťte Cleanup.bat ve složce Ukázky.  
  
    > [!NOTE]
    >  Tento skript neodebere certifikáty služby v klientském počítači při spuštění této ukázce mezi počítači. Pokud jste spustili Ukázky WCF, které používají certifikáty mezi počítači, je nutné vymazat certifikáty služby, které byly nainstalovány v CurrentUser - TrustedPeople uložit. Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>. For example: certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="see-also"></a>Viz také  
 [Používání metadat](../../../../docs/framework/wcf/feature-details/using-metadata.md)
