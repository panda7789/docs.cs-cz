---
title: Vlastní zabezpečený koncový bod metadat
ms.date: 03/30/2017
ms.assetid: 9e369e99-ea4a-49ff-aed2-9fdf61091a48
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 2baa99ddaf5de60407b233b5a6ea013ad87401f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33508058"
---
# <a name="custom-secure-metadata-endpoint"></a>Vlastní zabezpečený koncový bod metadat
Tento příklad znázorňuje, jak implementovat služby Zabezpečené metadata koncový bod, který používá jedna z vazeb neobsahující metadata exchange a postup konfigurace [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nebo klientům načíst metadata z těchto metadat koncového bodu. Nejsou k dispozici pro vystavení koncové body metadat dvě vazby poskytované systémem: mexHttpBinding a mexHttpsBinding. mexHttpBinding se používá ke zveřejnění způsobem nezabezpečené koncový bod metadat prostřednictvím protokolu HTTP. mexHttpsBinding se používá ke zveřejnění koncový bod metadat prostřednictvím protokolu HTTPS zabezpečeným způsobem. Tato ukázka znázorňuje, jak vystavit koncový bod metadat zabezpečené pomocí <xref:System.ServiceModel.WSHttpBinding>. Chcete by se to udělat, když chcete změnit nastavení zabezpečení na vazby, ale nechcete používat protokol HTTPS. Pokud použijete mexHttpsBinding bude váš koncový bod metadat zabezpečené, ale neexistuje žádný způsob, jak upravit nastavení vazby.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
## <a name="service"></a>Služba  
 Služba v této ukázce má dva koncové body. Koncový bod aplikace slouží `ICalculator` smlouvy na `WSHttpBinding` s `ReliableSession` povolená a `Message` zabezpečení pomocí certifikátů. Koncový bod metadat také používá `WSHttpBinding`, stejné nastavení zabezpečení, ale ne `ReliableSession`. Tady je relevantní konfigurace:  
  
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
  
 V mnoha dalších ukázky koncový bod metadat používá výchozí `mexHttpBinding`, která není zabezpečená. Zde je metadata zabezpečené pomocí `WSHttpBinding` s `Message` zabezpečení. Aby klienti metadata k načtení těchto metadat musejí být nakonfigurovány s odpovídající vazby. Tento příklad ukazuje dva těchto klientů.  
  
 První klient použije Svcutil.exe pro načtení metadat a generovat kód klienta a konfigurace v době návrhu. Protože služba používá jiné než výchozí vazbu pro metadata, nástroje Svcutil.exe je potřeba nakonfigurovat tak, aby ho můžete získat metadata ze služby pomocí této vazby.  
  
 Druhý klient použije `MetadataResolver` dynamicky načíst metadata pro kontraktu známé a pak vyvolání operací v dynamicky generovaném klientovi.  
  
## <a name="svcutil-client"></a>Svcutil klienta  
 Při použití výchozí vazbu na hostitele vaší `IMetadataExchange` koncový bod, můžete spustit Svcutil.exe s adresou tohoto koncového bodu:  
  
```  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 a metoda funguje. Ale v této ukázce server používá k hostování metadata koncový bod jiné než výchozí. Proto musí být Svcutil.exe pokyn k použití správné vazby. To lze provést pomocí souboru Svcutil.exe.config.  
  
 Soubor Svcutil.exe.config vypadá jako normální klienta konfiguračního souboru. Pouze neobvyklou aspekty jsou název koncového bodu klienta a kontraktu:  
  
```xml  
<endpoint name="http"  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"  
          behaviorConfiguration="ClientCertificateBehavior"  
          contract="IMetadataExchange" />  
```  
  
 Název koncového bodu musí být název schématu adresy, na kterém je hostována metadata a koncového bodu kontraktu musí být `IMetadataExchange`. Když je proto Svcutil.exe spusťte pomocí příkazového řádku například následující:  
  
```  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 Vypadá to, pro koncový bod s názvem "http" a kontrakt `IMetadataExchange` ke konfiguraci vazby a chování exchange pro komunikaci s koncovým bodem metadat. Zbytek souboru Svcutil.exe.config v ukázce určuje Konfigurace vazeb a chování přihlašovacích údajů podle serveru konfigurace koncového bodu metadat.  
  
 Aby Svcutil.exe zachycení konfigurace v Svcutil.exe.config Svcutil.exe musí být ve stejném adresáři jako konfigurační soubor. V důsledku toho je nutné zkopírovat Svcutil.exe z umístění instalace do adresáře, který obsahuje soubor Svcutil.exe.config. Potom z adresáře, spusťte následující příkaz:  
  
```  
.\svcutil.exe http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 Úvodního ". \\"zajistí, že je použít kopii Svcutil.exe v tomto adresáři (ten, který má odpovídající Svcutil.exe.config).  
  
## <a name="metadataresolver-client"></a>Třídy MetadataResolver klienta  
 Pokud klient zná kontrakt a postupy, aby komunikoval s metadaty v době návrhu, klienta můžete dynamicky zjistit vazeb a adresy koncových bodů aplikace pomocí `MetadataResolver`. Tato ukázka klienta ukazuje to, znázorňující postup konfigurace vazby a pověření používaná `MetadataResolver` pomocí vytvoření a konfigurace `MetadataExchangeClient`.  
  
 Imperativní na lze zadat stejný certifikát a vazeb informace, které zobrazovaly v Svcutil.exe.config `MetadataExchangeClient`:  
  
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
  
 S `mexClient` nakonfigurovaná, jsme výčet kontrakty jsme zájem a použijte `MetadataResolver` načíst seznam koncových bodů s tyto smlouvy:  
  
```  
// The contract we want to fetch metadata for  
Collection<ContractDescription> contracts =    new Collection<ContractDescription>();  
ContractDescription contract =    ContractDescription.GetContract(typeof(ICalculator));  
contracts.Add(contract);  
// Find endpoints for that contract  
EndpointAddress mexAddress = new    EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
ServiceEndpointCollection endpoints =    MetadataResolver.Resolve(contracts, mexAddress, mexClient);  
```  
  
 Nakonec informace z těchto koncových bodů můžete použít k chybě při inicializaci vazby a adresu `ChannelFactory` použít k vytvoření kanálů pro komunikaci s koncovými body aplikace.  
  
```  
ChannelFactory<ICalculator> cf = new    ChannelFactory<ICalculator>(endpoint.Binding, endpoint.Address);  
```  
  
 Bodem klíče klienta Tato ukázka je prokázat, že, pokud používáte `MetadataResolver`a je nutné zadat vlastní vazby nebo chování pro komunikaci se exchange metadata, můžete použít `MetadataExchangeClient` k určení tato vlastní nastavení.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Jak nastavit a sestavit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a>Ke spuštění ukázky na stejném počítači  
  
1.  Spuštění Setup.bat od vzorku instalační složku. Tím se nainstaluje všechny certifikáty, které jsou potřebné ke spuštění ukázky. Všimněte si, že Setup.bat používá nástroj FindPrivateKey.exe, který je nainstalovaná, spuštěním setupCertTool.bat z [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Spusťte klientskou aplikaci z \MetadataResolverClient\bin nebo \SvcutilClient\bin. Činnost klienta se zobrazí na klientskou aplikaci konzoly.  
  
3.  Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
4.  Odeberte certifikáty spuštěním Cleanup.bat po dokončení se vzorkem. Další ukázky zabezpečení použijte stejné certifikáty.  
  
#### <a name="to-run-the-sample-across-machines"></a>Ke spuštění ukázky mezi počítači  
  
1.  Na serveru, spusťte `setup.bat service`. Spuštění `setup.bat` s `service` argument vytvoří certifikát služby s plně kvalifikovaný název domény počítače a exportuje certifikát služby do souboru s názvem Service.cer.  
  
2.  Na serveru upravte soubor Web.config tak, aby odrážely novou název certifikátu. To znamená, změnit `findValue` atribut [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) element plně kvalifikovaný název domény počítače.  
  
3.  Zkopírujte soubor Service.cer z adresáře služby k adresáři klienta v klientském počítači.  
  
4.  Na klientovi, spusťte `setup.bat client`. Spuštění `setup.bat` s `client` argument vytvoří klientský certifikát s názvem Client.com a exportuje certifikát klienta do souboru s názvem Client.cer.  
  
5.  V souboru App.config `MetadataResolverClient` na klientský počítač, změňte hodnotu adresa koncového bodu mex tak, aby odpovídala nové adresy vaší služby. Provedete to nahrazením localhost plně kvalifikovaný název domény serveru. Výskyt řetězce "localhost" v souboru metadataResolverClient.cs také změníte na nový název certifikátu služby (plně kvalifikovaný název domény serveru). Stejnou věc udělat pro App.config SvcutilClient projektu.  
  
6.  Zkopírujte soubor Client.cer z adresáře klienta do adresáře služby na serveru.  
  
7.  Na klientovi, spusťte `ImportServiceCert.bat`. Tento certifikát služby naimportuje ze souboru Service.cer do CurrentUser - TrustedPeople úložiště.  
  
8.  Na serveru, spusťte `ImportClientCert.bat`, tento klientský certifikát naimportuje ze souboru Client.cer do LocalMachine - úložiště TrustedPeople.  
  
9. Na počítači služby sestavení projektu služby v sadě Visual Studio a vyberte stránku nápovědy ve webovém prohlížeči a ověřte, zda je spuštěna.  
  
10. V klientském počítači spusťte MetadataResolverClient nebo SvcutilClient ze sady VS.  
  
    1.  Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>Vyčistěte po vzorku  
  
-   Po dokončení spuštění ukázky, spusťte Cleanup.bat ve složce Ukázky.  
  
    > [!NOTE]
    >  Tento skript neodebere certifikáty služby v klientském počítači při spuštění této ukázce mezi počítači. Pokud jste spustili ukázky Windows Communication Foundation (WCF), které používají certifikáty mezi počítači, je nutné vymazat certifikáty služby, které byly nainstalovány v CurrentUser - úložiště TrustedPeople. Chcete-li to provést, použijte následující příkaz: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`. Příklad: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\CustomMexEndpoint`  
  
## <a name="see-also"></a>Viz také
