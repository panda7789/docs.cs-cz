---
title: Vlastní zabezpečený koncový bod metadat
ms.date: 03/30/2017
ms.assetid: 9e369e99-ea4a-49ff-aed2-9fdf61091a48
ms.openlocfilehash: bc96b21c4432c204160a951e5990ee1751f60e21
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2019
ms.locfileid: "56303904"
---
# <a name="custom-secure-metadata-endpoint"></a>Vlastní zabezpečený koncový bod metadat
Tento příklad ukazuje, jak implementovat službu s koncovým bodem zabezpečené metadata, která používá jedna z vazeb neobsahující metadata exchange a konfigurace [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nebo klientům pro načtení metadata z těchto koncových bodů metadat. Dostupné jsou dvě vazby poskytované systémem vystavení koncové body metadat: mexHttpBinding a mexHttpsBinding. mexHttpBinding se používá k vystavení koncový bod metadat prostřednictvím protokolu HTTP nezabezpečené způsobem. mexHttpsBinding se používá k vystavení koncový bod metadat prostřednictvím protokolu HTTPS bezpečným způsobem. Tento příklad ukazuje, jak vystavit koncový bod metadat zabezpečené pomocí <xref:System.ServiceModel.WSHttpBinding>. Chcete to provést, když chcete změnit nastavení zabezpečení v rámci vazby, ale nechcete, aby používal protokol HTTPS. Pokud používáte mexHttpsBinding váš koncový bod metadat budou zabezpečené, ale neexistuje žádný způsob, jak upravit nastavení vazby.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
## <a name="service"></a>Služba  
 Služby v této ukázce má dva koncové body. Koncový bod aplikace slouží `ICalculator` smlouvy na `WSHttpBinding` s `ReliableSession` povolené a `Message` zabezpečení pomocí certifikátů. Koncový bod metadat se používá také `WSHttpBinding`, se stejné nastavení zabezpečení, ale ne `ReliableSession`. Tady je odpovídající konfigurace:  
  
```xml  
<services>   
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
     <!-- use base address provided by host -->  
     <endpoint address=""  
       binding="wsHttpBinding"  
       bindingConfiguration="Binding2"  
       contract="Microsoft.ServiceModel.Samples.ICalculator" />  
     <endpoint address="mex"  
       binding="wsHttpBinding"  
       bindingConfiguration="Binding1"  
       contract="IMetadataExchange" />  
     </service>  
 </services>  
 <bindings>  
   <wsHttpBinding>  
     <binding name="Binding1">  
       <security mode="Message">  
         <message clientCredentialType="Certificate" />  
       </security>  
     </binding>  
     <binding name="Binding2">  
       <reliableSession inactivityTimeout="00:01:00" enabled="true" />  
       <security mode="Message">  
         <message clientCredentialType="Certificate" />  
       </security>  
     </binding>  
   </wsHttpBinding>  
 </bindings>  
```  
  
 V mnoha jiných vzorků, které se používá koncový bod metadat výchozí `mexHttpBinding`, která není zabezpečená. Tady metadata je zabezpečený pomocí `WSHttpBinding` s `Message` zabezpečení. Aby klienti metadata pro načtení těchto metadat musí být nakonfigurovaný s odpovídající vazbu. Tento příklad ukazuje dva těchto klientů.  
  
 První klient používá Svcutil.exe k načtení metadat a generovat kód klienta a konfigurace v době návrhu. Protože služba používá jiné než výchozí vazby pro metadata, nástroje Svcutil.exe musí být specificky konfigurována tak, aby ho můžete získat metadata ze služby pomocí této vazby.  
  
 Druhý klient použije `MetadataResolver` dynamicky načíst metadata pro známé smlouvu a pak vyvolání operací na straně klienta dynamicky generované.  
  
## <a name="svcutil-client"></a>Svcutil klienta  
 Při použití výchozí vazby k hostiteli vaše `IMetadataExchange` koncového bodu, můžete spustit Svcutil.exe adresou tohoto koncového bodu:  
  
```  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 a to funguje. Ale v této ukázce server používá k hostování metadata koncový bod jiné než výchozí. Takže Svcutil.exe musí být nastaven na použití správnou vazbu. To lze provést pomocí souboru Svcutil.exe.config.  
  
 Soubor Svcutil.exe.config vypadá jako normální klienta konfigurační soubor. Pouze neobvyklé aspekty jsou název koncového bodu klienta a smlouvy:  
  
```xml  
<endpoint name="http"  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"  
          behaviorConfiguration="ClientCertificateBehavior"  
          contract="IMetadataExchange" />  
```  
  
 Název koncového bodu musí být název schématu adresu, kde je hostovaný metadata a kontraktu koncového bodu musí být `IMetadataExchange`. Kdy je proto Svcutil.exe spustit pomocí příkazového řádku jako je následující:  
  
```  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 vypadá pro koncový bod s názvem "http" a kontrakt `IMetadataExchange` ke konfiguraci vazby a chování exchange komunikaci s koncovým bodem metadat. Zbytek souboru Svcutil.exe.config v ukázce určuje konfigurace vazby a chování přihlašovacích údajů tak, aby odpovídaly konfiguraci serveru koncový bod metadat.  
  
 Aby Svcutil.exe ke sbírání konfigurace v Svcutil.exe.config Svcutil.exe musí být ve stejném adresáři jako konfigurační soubor. V důsledku toho je nutné zkopírovat Svcutil.exe z umístění instalace do adresáře, který obsahuje soubor Svcutil.exe.config. Pak z tohoto adresáře, spusťte následující příkaz:  
  
```  
.\svcutil.exe http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 Úvodního ". \\"zajistí, že je použít kopie Svcutil.exe v tomto adresáři (ten, který má odpovídající Svcutil.exe.config).  
  
## <a name="metadataresolver-client"></a>Třídy MetadataResolver klienta  
 Pokud klient ví, kontrakt a jak se ptát metadat v době návrhu, klient může dynamicky zjistit vazeb a adresy koncových bodů aplikací použitím `MetadataResolver`. Tato ukázka klienta ukazuje to, ukazuje, jak nakonfigurovat přihlašovací údaje používané a vazby `MetadataResolver` ve vytváření a konfiguraci `MetadataExchangeClient`.  
  
 Stejné informace certifikátu a vazby, které se zobrazovalo v Svcutil.exe.config se dá nastavit imperativně na `MetadataExchangeClient`:  
  
```  
// Specify the Metadata Exchange binding and its security mode  
WSHttpBinding mexBinding = new WSHttpBinding(SecurityMode.Message);  
mexBinding.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
// Create a MetadataExchangeClient for retrieving metadata, and set the // certificate details  
MetadataExchangeClient mexClient = new MetadataExchangeClient(mexBinding);  
mexClient.SoapCredentials.ClientCertificate.SetCertificate(    StoreLocation.CurrentUser, StoreName.My,  
    X509FindType.FindBySubjectName, "client.com");  
mexClient.SoapCredentials.ServiceCertificate.Authentication.    CertificateValidationMode =    X509CertificateValidationMode.PeerOrChainTrust;  
mexClient.SoapCredentials.ServiceCertificate.SetDefaultCertificate(    StoreLocation.CurrentUser, StoreName.TrustedPeople,  
    X509FindType.FindBySubjectName, "localhost");  
```  
  
 S `mexClient` nakonfigurované, můžeme výčet kontrakty jsme zájem a `MetadataResolver` načíst seznam koncových bodů s těmito smlouvy:  
  
```  
// The contract we want to fetch metadata for  
Collection<ContractDescription> contracts =    new Collection<ContractDescription>();  
ContractDescription contract =    ContractDescription.GetContract(typeof(ICalculator));  
contracts.Add(contract);  
// Find endpoints for that contract  
EndpointAddress mexAddress = new    EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
ServiceEndpointCollection endpoints =    MetadataResolver.Resolve(contracts, mexAddress, mexClient);  
```  
  
 Nakonec informace z těchto koncových bodů můžete použít k inicializaci vazbu a adresu `ChannelFactory` použitý k vytvoření kanálů pro komunikaci s aplikačními koncovými body.  
  
```  
ChannelFactory<ICalculator> cf = new    ChannelFactory<ICalculator>(endpoint.Binding, endpoint.Address);  
```  
  
 Tato ukázka klienta klíčovým bodem tedy je předvést, pokud používáte `MetadataResolver`a je nutné zadat vlastní vazby nebo chování pro komunikaci metadata exchange, můžete použít `MetadataExchangeClient` zadat tato vlastní nastavení.  
  
#### <a name="to-set-up-and-build-the-sample"></a>K nastavení a sestavit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a>Ke spuštění ukázky ve stejném počítači  
  
1.  Spusťte Setup.bat z instalační složky s ukázkou. Tím se nainstaluje všechny certifikáty požadované ke spuštění ukázky. Všimněte si, že používá Setup.bat FindPrivateKey.exe nástroj, který je nainstalovaný spuštěním setupCertTool.bat z [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Spuštění klientské aplikace z \MetadataResolverClient\bin nebo \SvcutilClient\bin. Činnost klienta se zobrazí na klientské aplikace konzoly.  
  
3.  Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy poradce při potížích pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
4.  Odeberte certifikáty spuštěním Cleanup.bat po dokončení s ukázkou. Další ukázky zabezpečení použijte stejné certifikáty.  
  
#### <a name="to-run-the-sample-across-machines"></a>Ke spuštění ukázky v počítačích  
  
1.  Na serveru, spusťte `setup.bat service`. Spuštění `setup.bat` s `service` argument vytvoří certifikát služby se plně kvalifikovaný název domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.  
  
2.  Na serveru upravte soubor Web.config tak, aby odrážely nový název certifikátu. To znamená, změnit `findValue` atribut [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) elementu plně kvalifikovaný název domény počítače.  
  
3.  Zkopírujte soubor Service.cer z adresáře služby k adresáři klienta v klientském počítači.  
  
4.  Na straně klienta, spouštění `setup.bat client`. Spuštění `setup.bat` s `client` argument vytvoří klientský certifikát s názvem Client.com a exportuje certifikát klienta do souboru s názvem Client.cer.  
  
5.  V souboru App.config `MetadataResolverClient` na klientský počítač, změňte hodnotu adresu koncového bodu mex tak, aby odpovídala nové adresu služby. Provedete to nahrazením localhost plně kvalifikovaný název domény serveru. Výskyt řetězce "localhost" v souboru metadataResolverClient.cs také změňte na nový název certifikátu služby (plně kvalifikovaný název domény serveru). Stejnou věc uděláte pro App.config SvcutilClient projektu.  
  
6.  Zkopírujte soubor Client.cer z adresáře klienta do adresáře služby na serveru.  
  
7.  Na straně klienta, spouštění `ImportServiceCert.bat`. To importuje certifikát služby ze souboru Service.cer do CurrentUser - TrustedPeople úložiště.  
  
8.  Na serveru, spusťte `ImportClientCert.bat`, to importuje klientský certifikát ze souboru Client.cer do úložiště LocalMachine - TrustedPeople úložiště.  
  
9. Na počítači služby sestavení projektu služby v sadě Visual Studio a vyberte na stránce nápovědy ve webovém prohlížeči a ověřte, zda je spuštěna.  
  
10. V klientském počítači spusťte MetadataResolverClient nebo SvcutilClient z VS.  
  
    1.  Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy poradce při potížích pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>K vyčištění po vzorku  
  
-   Spusťte Cleanup.bat ve složce samples po dokončení spuštění ukázky.  
  
    > [!NOTE]
    >  Tento skript neodebere certifikáty služeb v klientském počítači při spuštění této ukázky napříč počítači. Pokud jste provedli ukázky Windows Communication Foundation (WCF), které používají certifikáty mezi počítači, je potřeba vymazat certifikáty služeb, které jsou nainstalovány v CurrentUser - TrustedPeople úložiště. Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`. Například: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\CustomMexEndpoint`  
  
## <a name="see-also"></a>Viz také:
