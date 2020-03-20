---
title: Vlastní zabezpečený koncový bod metadat
ms.date: 03/30/2017
ms.assetid: 9e369e99-ea4a-49ff-aed2-9fdf61091a48
ms.openlocfilehash: 89f12b4490d556884aaa15dcb102b5ad876707ba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183851"
---
# <a name="custom-secure-metadata-endpoint"></a>Vlastní zabezpečený koncový bod metadat
Tato ukázka ukazuje, jak implementovat službu s koncovým bodem zabezpečené metadata, který používá jednu z vazby exchange non-metadata a jak nakonfigurovat [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nebo klienty pro načtení metadat z takového koncového bodu metadat. Pro vystavení koncových bodů metadat jsou k dispozici dvě vazby poskytované systémem: mexHttpBinding a mexHttpsBinding. mexHttpBinding se používá k vystavení koncového bodu metadat přes protokol HTTP nezabezpečeným způsobem. mexHttpsBinding se používá k vystavení koncového bodu metadat přes protokol HTTPS zabezpečeným způsobem. Tato ukázka ukazuje, jak vystavit koncový bod <xref:System.ServiceModel.WSHttpBinding>zabezpečené metadata pomocí . To byste chtěli provést, pokud chcete změnit nastavení zabezpečení ve vazbě, ale nechcete používat protokol HTTPS. Pokud použijete mexHttpsBinding koncový bod metadat bude zabezpečený, ale neexistuje žádný způsob, jak změnit nastavení vazby.  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
## <a name="service"></a>Služba  
 Služba v této ukázce má dva koncové body. Koncový bod aplikace `ICalculator` slouží smlouvy `WSHttpBinding` `ReliableSession` s `Message` povolenou a zabezpečení pomocí certifikátů. Koncový bod metadat také `WSHttpBinding`používá , se stejným `ReliableSession`nastavením zabezpečení, ale bez . Zde je příslušná konfigurace:  
  
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
  
 V mnoha dalších ukázkách koncový bod metadat `mexHttpBinding`používá výchozí , který není zabezpečený. Zde jsou metadata `WSHttpBinding` zabezpečena pomocí `Message` zabezpečení. Aby klienti metadat načíst tato metadata, musí být nakonfigurován s odpovídající vazby. Tato ukázka ukazuje dva takové klienty.  
  
 První klient používá Svcutil.exe k načtení metadat a generování klientského kódu a konfigurace v době návrhu. Vzhledem k tomu, že služba používá pro metadata nevýchozí vazbu, musí být nástroj Svcutil.exe specificky nakonfigurován tak, aby mohl získat metadata ze služby pomocí této vazby.  
  
 Druhý klient používá `MetadataResolver` dynamicky načíst metadata pro známé smlouvy a potom vyvolat operace na dynamicky generované klienta.  
  
## <a name="svcutil-client"></a>Klient Svcutil  
 Při použití výchozí vazby `IMetadataExchange` k hostování koncového bodu můžete spustit svcutil.exe s adresou tohoto koncového bodu:  
  
```console  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 a funguje to. Ale v této ukázce server používá mimo výchozí koncový bod k hostování metadat. Takže Svcutil.exe musí být instruován, aby použil správnou vazbu. To lze provést pomocí souboru Svcutil.exe.config.  
  
 Soubor Svcutil.exe.config vypadá jako normální konfigurační soubor klienta. Jedinými neobvyklými aspekty jsou název koncového bodu klienta a smlouva:  
  
```xml  
<endpoint name="http"  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"  
          behaviorConfiguration="ClientCertificateBehavior"  
          contract="IMetadataExchange" />  
```  
  
 Název koncového bodu musí být název schématu adresy, kde jsou metadata hostována, a kontrakt koncového bodu musí být `IMetadataExchange`. Proto při Svcutil.exe je spuštěn s příkazovým řádkem, jako je následující:  
  
```console  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 vyhledá koncový bod s názvem "http" a smlouvy `IMetadataExchange` pro konfiguraci vazby a chování výměny komunikace s koncovým bodem metadat. Zbytek souboru Svcutil.exe.config v ukázce určuje pověření konfigurace vazby a chování tak, aby odpovídaly konfiguraci koncového bodu metadat na serveru.  
  
 Aby svcutil.exe vyzvednout konfiguraci v Svcutil.exe.config, Svcutil.exe musí být ve stejném adresáři jako konfigurační soubor. V důsledku toho je nutné zkopírovat soubor Svcutil.exe z jeho umístění instalace do adresáře, který obsahuje soubor Svcutil.exe.config. Potom z tohoto adresáře spusťte následující příkaz:  
  
```console  
.\svcutil.exe http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 Vedoucí ". \\" zajišťuje spuštění kopie souboru Svcutil.exe v tomto adresáři (ten, který má odpovídající soubor Svcutil.exe.config).  
  
## <a name="metadataresolver-client"></a>Klient MetadataResolver  
 Pokud klient zná smlouvu a jak mluvit s metadaty v době návrhu, klient může dynamicky `MetadataResolver`zjistit vazbu a adresu koncových bodů aplikace pomocí . Tento ukázkový klient to ukazuje a ukazuje, jak `MetadataResolver` nakonfigurovat vazbu `MetadataExchangeClient`a pověření používaná vytvořením a konfigurací rozhraní .  
  
 Stejné informace o vazbě a certifikátu, které se objevily v svcutil.exe.config, lze imperativně zadat na `MetadataExchangeClient`:  
  
```csharp  
// Specify the Metadata Exchange binding and its security mode  
WSHttpBinding mexBinding = new WSHttpBinding(SecurityMode.Message);  
mexBinding.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
// Create a MetadataExchangeClient for retrieving metadata, and set the // certificate details  
MetadataExchangeClient mexClient = new MetadataExchangeClient(mexBinding);  
mexClient.SoapCredentials.ClientCertificate.SetCertificate(    StoreLocation.CurrentUser, StoreName.My,  
    X509FindType.FindBySubjectName, "client.com");  
mexClient.SoapCredentials.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
mexClient.SoapCredentials.ServiceCertificate.SetDefaultCertificate(    StoreLocation.CurrentUser, StoreName.TrustedPeople,  
    X509FindType.FindBySubjectName, "localhost");  
```  
  
 S `mexClient` nakonfigurované, můžeme výčet smluv, které `MetadataResolver` nás zajímají, a použít k načtení seznamu koncových bodů s těmito smlouvami:  
  
```csharp  
// The contract we want to fetch metadata for  
Collection<ContractDescription> contracts = new Collection<ContractDescription>();  
ContractDescription contract = ContractDescription.GetContract(typeof(ICalculator));  
contracts.Add(contract);  
// Find endpoints for that contract  
EndpointAddress mexAddress = new EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
ServiceEndpointCollection endpoints = MetadataResolver.Resolve(contracts, mexAddress, mexClient);  
```  
  
 Nakonec můžeme použít informace z těchto koncových bodů k inicializaci vazby a adresy `ChannelFactory` slouží k vytvoření kanálů pro komunikaci s koncovými body aplikace.  
  
```csharp  
ChannelFactory<ICalculator> cf = new ChannelFactory<ICalculator>(endpoint.Binding, endpoint.Address);  
```  
  
 Klíčovým bodem tohoto ukázkového klienta je ukázat, `MetadataResolver`že pokud používáte , a je nutné zadat vlastní vazby `MetadataExchangeClient` nebo chování pro komunikaci výměny metadat, můžete použít k určení těchto vlastních nastavení.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Nastavení a sestavení ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a>Spuštění ukázky ve stejném počítači  
  
1. Spusťte soubor Setup.bat z ukázkové instalační složky. Tím nainstalujete všechny certifikáty potřebné pro spuštění ukázky. Všimněte si, že Setup.bat používá nástroj FindPrivateKey.exe, který je nainstalován spuštěním setupCertTool.bat z [jednorázového postupu instalace pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Spusťte klientskou aplikaci z \MetadataResolverClient\bin nebo \SvcutilClient\bin. Aktivita klienta je zobrazena v aplikaci klientské konzole.  
  
3. Pokud klient a služba nejsou schopni komunikovat, naleznete [v tématu Tipy pro řešení potíží pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
4. Po dokončení ukázky odeberte certifikáty spuštěním souboru Cleanup.bat. Jiné ukázky zabezpečení používají stejné certifikáty.  
  
#### <a name="to-run-the-sample-across-machines"></a>Spuštění ukázky napříč počítači  
  
1. Na serveru spusťte . `setup.bat service` Spuštění `setup.bat` s `service` argumentem vytvoří certifikát služby s plně kvalifikovaným názvem domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.  
  
2. Na serveru upravte web.config tak, aby odrážel nový název certifikátu. To znamená změnit `findValue` atribut v [ \<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) element plně kvalifikovaný název domény počítače.  
  
3. Zkopírujte soubor Service.cer z adresáře služby do klientského adresáře v klientském počítači.  
  
4. Na straně klienta spusťte `setup.bat client`. Spuštění `setup.bat` s `client` argumentem vytvoří klientský certifikát s názvem Client.com a exportuje klientský certifikát do souboru s názvem Client.cer.  
  
5. V souboru App.config `MetadataResolverClient` v klientském počítači změňte hodnotu adresy koncového bodu mex tak, aby odpovídala nové adrese vaší služby. Provést nahrazením localhost plně kvalifikovaný název domény serveru. Změňte také výskyt "localhost" v souboru metadataResolverClient.cs na nový název certifikátu služby (plně kvalifikovaný název domény serveru). Proveďte totéž pro App.config projektu SvcutilClient.  
  
6. Zkopírujte soubor Client.cer z adresáře klienta do adresáře služby na serveru.  
  
7. Na straně klienta spusťte `ImportServiceCert.bat`. Tím se importuje certifikát služby ze souboru Service.cer do úložiště CurrentUser - TrustedPeople.  
  
8. Na serveru, `ImportClientCert.bat`spustit , To importuje klientský certifikát ze souboru Client.cer do úložiště LocalMachine - TrustedPeople.  
  
9. Na servisním počítači vytvořte projekt služby v sadě Visual Studio a vyberte stránku nápovědy ve webovém prohlížeči a ověřte, zda je spuštěný.  
  
10. V klientském počítači spusťte metadataResolverClient nebo SvcutilClient z VS.  
  
    1. Pokud klient a služba nejsou schopni komunikovat, naleznete [v tématu Tipy pro řešení potíží pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>Chcete-li vyčistit po vzorku  
  
- Po dokončení spuštění ukázky spusťte soubor Cleanup.bat ve složce ukázek.  
  
    > [!NOTE]
    > Tento skript neodebere certifikáty služeb na straně klienta při spuštění této ukázky v počítačích. Pokud jste schovali ukázky WCF (Windows Communication Foundation), které používají certifikáty napříč počítači, nezapomeňte vymazat certifikáty služeb, které byly nainstalovány v úložišti CurrentUser - TrustedPeople. Chcete-li to provést, `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`použijte následující příkaz: . Například: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\CustomMexEndpoint`  
