---
title: "Vlastní hostitel služby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe16ff50-7156-4499-9c32-13d8a79dc100
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5faeb409e6076fe934d1b8c88423a8a348f786ca
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="custom-service-host"></a>Vlastní hostitel služby
Tento příklad ukazuje, jak použít vlastní odvozený ze <xref:System.ServiceModel.ServiceHost> tříd pro úpravu běhového chování služby. Tento přístup poskytuje opakovaně použitelné alternativu ke konfiguraci velký počet služeb v běžným způsobem. Ukázka také ukazuje, jak používat <xref:System.ServiceModel.Activation.ServiceHostFactory> třídu se má použít vlastní hostitel služby v Internetové informační služby (IIS) nebo služby Aktivace procesů systému Windows (WAS) hostitelské prostředí.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Hosting\CustomServiceHost`  
  
## <a name="about-the-scenario"></a>O scénář  
 Aby se zabránilo neúmyslnému zveřejnění metadata potenciálně citlivých služby, výchozí konfiguraci pro [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] zakáže publikování metadat služby. Toto chování je ve výchozím nastavení zabezpečení, ale také znamená, že nelze použít metadata importovat nástroj (například Svcutil.exe) ke generování kódu klienta pro volání služby, pokud není výslovně povolena chování publikování metadat služby v konfiguraci požadován.  
  
 Povolení publikování metadat pro velký počet služeb zahrnuje přidání stejné konfigurační prvky do každé jednotlivé služby, což vede k velké množství informace o konfiguraci, která je v podstatě stejné. Jako alternativu ke konfiguraci jednotlivých služeb jednotlivě je možné zapisovat imperativní kód, který umožňuje jednou publikování metadat a potom tento kód opakovaně napříč několik různých služeb. Toho dosahuje tak, že vytvoříte novou třídu odvozenou od <xref:System.ServiceModel.ServiceHost> a přepíše `ApplyConfiguration`() metoda imperativní přidat chování publikování metadat.  
  
> [!IMPORTANT]
>  Tato ukázka pro přehlednost, ukazuje, jak vytvořit koncový bod publikování zabezpečená metadat. Tyto koncové body jsou potenciálně dostupné pro anonymní neověřené spotřebitelů a musí dát pozor před nasazením těchto koncových bodů a zajistit tak veřejně předání metadata služby příslušné.  
  
## <a name="implementing-a-custom-servicehost"></a>Implementace vlastní hostitel služby  
 <xref:System.ServiceModel.ServiceHost> Třída zpřístupňuje několik užitečné virtuální metody, které můžete přepsat dědice ke změně chování spuštění služby. Například `ApplyConfiguration`() metoda čte informace o konfiguraci služeb z úložiště konfigurace a mění hostitele <xref:System.ServiceModel.Description.ServiceDescription> odpovídajícím způsobem. Výchozí implementace načte konfiguraci z konfiguračního souboru aplikace. Vlastní implementace můžete přepsat `ApplyConfiguration`(), aby další příkaz alter <xref:System.ServiceModel.Description.ServiceDescription> pomocí imperativní kódu nebo i zcela nahradit výchozí konfigurace úložiště. Chcete-li například přečíst konfiguraci koncového bodu služby z databáze místo konfigurační soubor aplikace.  
  
 V této ukázce jsme chcete vytvořit vlastní hostitel služby, který přidává ServiceMetadataBehavior, (umožňující publikování metadat), i když je toto chování není explicitně přidán v konfiguračním souboru služby. K tomu, vytvoříme novou třídu, která dědí z <xref:System.ServiceModel.ServiceHost> a přepíše `ApplyConfiguration`().  
  
```  
class SelfDescribingServiceHost : ServiceHost  
{  
    public SelfDescribingServiceHost(Type serviceType, params Uri[] baseAddresses)  
        : base(serviceType, baseAddresses) { }  
  
    //Overriding ApplyConfiguration() allows us to   
    //alter the ServiceDescription prior to opening  
    //the service host.   
    protected override void ApplyConfiguration()  
    {  
        //First, we call base.ApplyConfiguration()  
        //to read any configuration that was provided for  
        //the service we're hosting. After this call,  
        //this.Description describes the service  
        //as it was configured.  
        base.ApplyConfiguration();       
  
        //(rest of implementation elided for clarity)  
    }  
}  
```  
  
 Protože jsme nechcete ignorovat jakoukoli konfiguraci, která má byly zadány v konfiguračním souboru aplikace, je první věcí naše přepsání `ApplyConfiguration`nemá () je volání základní implementaci. Po dokončení této metody můžete imperativní přidáme <xref:System.ServiceModel.Description.ServiceMetadataBehavior> pomocí následujícího kódu imperativní popisu.  
  
```  
ServiceMetadataBehavior mexBehavior = this.Description.Behaviors.Find<ServiceMetadataBehavior>();  
if (mexBehavior == null)  
{  
    mexBehavior = new ServiceMetadataBehavior();  
    this.Description.Behaviors.Add(mexBehavior);  
}  
else  
{  
    //Metadata behavior has already been configured,   
    //so we do not have any work to do.  
    return;  
}  
```  
  
 Poslední věcí, kterou naše `ApplyConfiguration`přepsání (), musíte udělat je přidat výchozí koncový bod metadat. Podle konvence pro každý URI v kolekci BaseAddresses hostitele služby se vytvoří jeden koncový bod metadat.  
  
```  
//Add a metadata endpoint at each base address  
//using the "/mex" addressing convention  
foreach (Uri baseAddress in this.BaseAddresses)  
{  
    if (baseAddress.Scheme == Uri.UriSchemeHttp)  
    {  
        mexBehavior.HttpGetEnabled = true;  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexHttpBinding(),  
                                "mex");  
    }  
    else if (baseAddress.Scheme == Uri.UriSchemeHttps)  
    {  
        mexBehavior.HttpsGetEnabled = true;  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexHttpsBinding(),  
                                "mex");  
    }  
    else if (baseAddress.Scheme == Uri.UriSchemeNetPipe)  
    {  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexNamedPipeBinding(),  
                                "mex");  
    }  
    else if (baseAddress.Scheme == Uri.UriSchemeNetTcp)  
    {  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexTcpBinding(),  
                                "mex");  
    }  
}  
```  
  
## <a name="using-a-custom-servicehost-in-self-host"></a>Použití vlastní hostitel služby v hostování na vlastním serveru  
 Teď, když jsme dokončili naše vlastní implementaci ServiceHost, jsme slouží k hostování služby v rámci instance do jakoukoli službu, přidejte chování publikování metadat naše `SelfDescribingServiceHost`. Následující kód ukazuje, jak používat v případě hostování na vlastním serveru.  
  
```  
SelfDescribingServiceHost host =   
         new SelfDescribingServiceHost( typeof( Calculator ) );  
host.Open();  
```  
  
 Naše vlastní hostitel stále přečte konfigurace koncového bodu služby z konfiguračního souboru aplikace, stejně, jako by se měl jsme použili výchozí <xref:System.ServiceModel.ServiceHost> třída k hostování služby. Ale vzhledem k tomu, že jsme přidali logiku povolit publikování v rámci našeho vlastního hostitele metadat, jsme už musíte povolit explicitně chování publikování v konfiguraci metadat. Tento přístup má odlišné využít, když vytváříte aplikaci, která obsahuje několik služeb a chcete povolit publikování metadat na každý z nich bez nutnosti psaní stejné konfigurační prvky opakovaně.  
  
## <a name="using-a-custom-servicehost-in-iis-or-was"></a>Použití vlastní hostitel služby IIS nebo WAS  
 Použít vlastní služba hostitele ve scénářích hostování na vlastním serveru je jasné, protože je vaší aplikační kód, který se nakonec odpovědné za vytváření a otevírání instance hostitele služby. V IIS nebo WAS hostování prostředí, ale [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastruktury je vytvoření dynamicky instance hostitele služby v reakci na příchozí zprávy. Hostitelé služeb z vlastní můžete použít i v tomto hostování prostředí, ale vyžadují některé další kód ve formuláři třídy ServiceHostFactory. Následující kód ukazuje odvozený ze <xref:System.ServiceModel.Activation.ServiceHostFactory> který vrátí instance naše vlastní `SelfDescribingServiceHost`.  
  
```  
public class SelfDescribingServiceHostFactory : ServiceHostFactory  
{  
    protected override ServiceHost CreateServiceHost(Type serviceType,   
     Uri[] baseAddresses)  
    {  
        //All the custom factory does is return a new instance  
        //of our custom host class. The bulk of the custom logic should  
        //live in the custom host (as opposed to the factory)   
        //for maximum  
        //reuse value outside of the IIS/WAS hosting environment.  
        return new SelfDescribingServiceHost(serviceType,     
                                             baseAddresses);  
    }  
}  
```  
  
 Jak vidíte, implementace vlastní třídy ServiceHostFactory je velmi jednoduché. Všechny vlastní logiky nachází uvnitř ServiceHost implementace; objekt factory vrací instanci třídy odvozené třídy.  
  
 Používat vlastní objekt pro vytváření implementaci služby, musí přidáme některé další metadata do souboru .svc služby.  
  
```  
<%@ServiceHost Service="Microsoft.ServiceModel.Samples.CalculatorService"  
               Factory="Microsoft.ServiceModel.Samples.SelfDescribingServiceHostFactory"  
               language=c# Debug="true" %>  
```  
  
 Zde jsme přidali další `Factory` atribut `@ServiceHost` direktivy a předaný modulu CLR zadejte název objektu pro vytváření naše vlastní jako hodnotu atributu. Když se služba IIS nebo WAS přijme zprávu o pro tuto službu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hosting infrastruktury nejprve vytvoří instanci třídy ServiceHostFactory a potom vytvořte instanci hostitele služby samotné voláním `ServiceHostFactory.CreateServiceHost()`.  
  
## <a name="running-the-sample"></a>Spuštění ukázky  
 I když tato ukázka poskytovat klient plně funkční a implementaci služby, je bod vzorku ukazují, jak chcete změnit chování služby prostřednictvím vlastní hostitele., proveďte následující kroky:  
  
#### <a name="to-observe-the-effect-of-the-custom-host"></a>Chcete-li sledovat účinek vlastního hostitele  
  
1.  Otevřete soubor Web.config služby a sledovat, že neexistuje žádná konfigurace explicitně povolení metadata pro službu.  
  
2.  Otevřete soubor .svc služby a že jeho @ServiceHost – direktiva obsahuje atribut typu objektu pro vytváření, který určuje název vlastní třídy ServiceHostFactory.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Po vytvoření řešení, spusťte Setup.bat nastavit aplikaci ServiceModelSamples v [!INCLUDE[iisver](../../../../includes/iisver-md.md)]. Adresář ServiceModelSamples by se měla zobrazit jako [!INCLUDE[iisver](../../../../includes/iisver-md.md)] aplikace.  
  
4.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5.  Chcete-li odebrat [!INCLUDE[iisver](../../../../includes/iisver-md.md)] aplikace, spustit Cleanup.bat.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: hostování služby WCF ve službě IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
