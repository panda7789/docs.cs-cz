---
title: Vlastní zabezpečený koncový bod metadat
ms.date: 03/30/2017
ms.assetid: 9e369e99-ea4a-49ff-aed2-9fdf61091a48
ms.openlocfilehash: 072d2551acaae87904bb12c5e8edafa788674322
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045127"
---
# <a name="custom-secure-metadata-endpoint"></a>Vlastní zabezpečený koncový bod metadat
Tato ukázka předvádí, jak implementovat službu pomocí zabezpečeného koncového bodu metadat, který používá jednu z vazeb mimo Metadata Exchange a jak nakonfigurovat nástroj pro nástroj pro dokládání [metadat (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nebo klienty, aby načetl metadata z takového koncový bod metadat K dispozici jsou dvě systémové vazby pro vystavování koncových bodů metadat: mexHttpBinding a mexHttpsBinding. mexHttpBinding se používá k vystavení koncového bodu metadat přes protokol HTTP nezabezpečeným způsobem. mexHttpsBinding se používá k vystavení koncového bodu metadat přes HTTPS zabezpečeným způsobem. Tento příklad ukazuje, jak vystavit zabezpečený koncový bod <xref:System.ServiceModel.WSHttpBinding>metadat pomocí. Tuto možnost byste měli udělat, když chcete změnit nastavení zabezpečení vazby, ale nechcete používat protokol HTTPS. Pokud použijete mexHttpsBinding, váš koncový bod metadat bude zabezpečený, ale neexistuje žádný způsob, jak upravit nastavení vazby.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
## <a name="service"></a>Služba  
 Služba v této ukázce má dva koncové body. Koncový bod aplikace obsluhuje `ICalculator` kontrakt `WSHttpBinding` s `ReliableSession` povoleným a `Message` zabezpečením pomocí certifikátů. Koncový bod metadat také používá `WSHttpBinding`se stejným nastavením zabezpečení, ale bez. `ReliableSession` Tady je příslušná konfigurace:  
  
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
  
 V řadě dalších ukázek používá koncový bod metadat výchozí `mexHttpBinding`, což není bezpečné. Tato metadata jsou zabezpečená pomocí `WSHttpBinding` `Message` zabezpečení. Aby klienti metadat mohli tato metadata načíst, musí být nakonfigurovány s vyhovující vazbou. Tato ukázka ukazuje dva takové klienty.  
  
 První klient používá Svcutil. exe k načtení metadat a generuje kód klienta a konfiguraci v době návrhu. Vzhledem k tomu, že služba používá pro metadata jinou než výchozí vazbu, musí být nástroj Svcutil. exe specificky nakonfigurován tak, aby mohl získat metadata ze služby pomocí této vazby.  
  
 Druhý klient používá nástroj `MetadataResolver` k dynamickému načítání metadat pro známý kontrakt a následné vyvolání operací na dynamicky generovaného klientovi.  
  
## <a name="svcutil-client"></a>Klient Svcutil  
 Při použití výchozí vazby k hostování `IMetadataExchange` koncového bodu můžete spustit Svcutil. exe s adresou tohoto koncového bodu:  
  
```  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 a funguje. V této ukázce ale server používá k hostování metadat jiný než výchozí koncový bod. Proto musí být Svcutil. exe pokyn pro použití správné vazby. To lze provést pomocí souboru Svcutil. exe. config.  
  
 Soubor Svcutil. exe. config vypadá jako normální konfigurační soubor klienta. Jedinými neobvyklými aspekty jsou název koncového bodu klienta a kontrakt:  
  
```xml  
<endpoint name="http"  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"  
          behaviorConfiguration="ClientCertificateBehavior"  
          contract="IMetadataExchange" />  
```  
  
 Název koncového bodu musí být název schématu adresy, na které se hostují metadata, a kontrakt koncového bodu musí být `IMetadataExchange`. Proto při spuštění Svcutil. exe s příkazovým řádkem, jako je například následující:  
  
```  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 hledá koncový bod s názvem "http" a kontrakt `IMetadataExchange` pro konfiguraci vazby a chování komunikačního výměny s koncovým bodem metadat. Zbytek souboru Svcutil. exe. config v ukázce určuje přihlašovací údaje konfigurace a chování vazby, aby odpovídaly konfiguraci serveru koncového bodu metadat.  
  
 Aby Svcutil. exe mohl vybrat konfiguraci v Svcutil. exe. config, Svcutil. exe musí být ve stejném adresáři jako konfigurační soubor. V důsledku toho je nutné zkopírovat Svcutil. exe z jeho umístění instalace do adresáře, který obsahuje soubor Svcutil. exe. config. Pak z tohoto adresáře spusťte následující příkaz:  
  
```  
.\svcutil.exe http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 Úvodní ". \\"zajistí, že se spustí kopie Svcutil. exe v tomto adresáři (ta, která má odpovídající Svcutil. exe. config).  
  
## <a name="metadataresolver-client"></a>Klient třídy MetadataResolver  
 Pokud klient zná kontrakt a postup, jak se v době návrhu spojit s metadaty, může klient dynamicky zjistit vazbu a adresu koncových bodů aplikace pomocí `MetadataResolver`. Tento ukázkový klient ukazuje, jak nakonfigurovat vazbu a přihlašovací údaje používané `MetadataResolver` vytvořením a `MetadataExchangeClient`konfigurací.  
  
 Stejné informace o vazbách a certifikátech, které se objevily v souboru Svcutil. exe. config, `MetadataExchangeClient`lze zadat imperativně na těchto počítačích:  
  
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
  
 Po `mexClient` nakonfigurování můžeme vypsat kontrakty, které vás zajímají, a použít `MetadataResolver` k načtení seznamu koncových bodů s těmito kontrakty:  
  
```  
// The contract we want to fetch metadata for  
Collection<ContractDescription> contracts =    new Collection<ContractDescription>();  
ContractDescription contract =    ContractDescription.GetContract(typeof(ICalculator));  
contracts.Add(contract);  
// Find endpoints for that contract  
EndpointAddress mexAddress = new    EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
ServiceEndpointCollection endpoints =    MetadataResolver.Resolve(contracts, mexAddress, mexClient);  
```  
  
 Nakonec můžeme použít informace z těchto koncových bodů k inicializaci vazby a adresy `ChannelFactory` použité k vytvoření kanálů pro komunikaci s koncovými body aplikace.  
  
```  
ChannelFactory<ICalculator> cf = new    ChannelFactory<ICalculator>(endpoint.Binding, endpoint.Address);  
```  
  
 Klíčovým bodem tohoto ukázkového klienta je Ukázat, že pokud používáte `MetadataResolver`, a musíte zadat vlastní vazby nebo chování pro komunikaci výměny metadat, můžete `MetadataExchangeClient` použít k zadání těchto vlastních nastavení.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Nastavení a sestavení ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Při sestavování řešení postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a>Spuštění ukázky na stejném počítači  
  
1. Z ukázkové instalační složky spusťte Setup. bat. Tím se nainstalují všechny certifikáty, které jsou potřebné ke spuštění ukázky. Všimněte si, že soubor Setup. bat používá nástroj FindPrivateKey. exe, který je nainstalován spuštěním souboru setupCertTool. bat, a to z [procesu jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Spuštění klientské aplikace z \MetadataResolverClient\bin nebo \SvcutilClient\bin. Aktivita klienta se zobrazí v klientské aplikaci konzoly.  
  
3. Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
4. Po dokončení s ukázkou odeberte certifikáty spuštěním souboru Cleanup. bat. Další ukázky zabezpečení používají stejné certifikáty.  
  
#### <a name="to-run-the-sample-across-machines"></a>Spuštění ukázky napříč počítači  
  
1. Na serveru spusťte `setup.bat service`. Při `setup.bat` spuštění`service` s argumentem se vytvoří certifikát služby s plně kvalifikovaným názvem domény počítače a vyexportuje certifikát služby do souboru s názvem Service. cer.  
  
2. Na serveru upravte Web. config tak, aby odrážel nový název certifikátu. To znamená, že změníte `findValue` atribut [ \<v serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) elementu na plně kvalifikovaný název domény počítače.  
  
3. Zkopírujte soubor Service. cer z adresáře služby do adresáře klienta v klientském počítači.  
  
4. Na straně klienta spusťte `setup.bat client`. Při `setup.bat` spuštění`client` s argumentem se vytvoří klientský certifikát s názvem Client.com a exportuje se klientský certifikát do souboru s názvem Client. cer.  
  
5. V souboru `MetadataResolverClient` App. config v klientském počítači změňte hodnotu adresy koncového bodu MEX tak, aby odpovídala nové adrese vaší služby. To provedete tak, že nahradíte localhost názvem domény pro plně kvalifikovaný název domény serveru. Také změňte výskyt "localhost" v souboru metadataResolverClient.cs na nový název certifikátu služby (plně kvalifikovaný název domény serveru). Proveďte stejnou věc pro soubor App. config projektu SvcutilClient.  
  
6. Zkopírujte soubor Client. cer z adresáře klienta do adresáře služby na serveru.  
  
7. Na straně klienta spusťte `ImportServiceCert.bat`. Tím se certifikát služby importuje ze souboru Service. cer do úložiště CurrentUser-TrustedPeople.  
  
8. Na tomto serveru `ImportClientCert.bat`tento příkaz importuje klientský certifikát ze souboru Client. cer do úložiště LocalMachine-TrustedPeople.  
  
9. Na počítači služby Sestavte projekt služby v aplikaci Visual Studio a ve webovém prohlížeči vyberte stránku s usnadněním, abyste ověřili, že je spuštěná.  
  
10. Na klientském počítači spusťte MetadataResolverClient nebo SvcutilClient z VS.  
  
    1. Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>Vyčištění po ukázce  
  
- Po dokončení ukázky spusťte na složce Samples Cleanup. bat.  
  
    > [!NOTE]
    > Tento skript při spuštění této ukázky mezi počítači neodebere certifikáty služby na klientovi. Pokud jste spustili ukázky Windows Communication Foundation (WCF), které používají certifikáty napříč počítači, nezapomeňte vymazat certifikáty služby, které byly nainstalovány v úložišti CurrentUser-TrustedPeople. K tomu použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`. Například: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\CustomMexEndpoint`  
