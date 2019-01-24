---
title: Vlastní hostitel služby
ms.date: 03/30/2017
ms.assetid: fe16ff50-7156-4499-9c32-13d8a79dc100
ms.openlocfilehash: 09a69e489c4b4eb5d3af6e2e74316e678be3d049
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555996"
---
# <a name="custom-service-host"></a>Vlastní hostitel služby
Tato ukázka předvádí, jak používat vlastní odvozený ze <xref:System.ServiceModel.ServiceHost> třídy pro úpravu chování za běhu služby. Tento přístup poskytuje opakovaně použitelné alternativu ke konfiguraci velkým množstvím služeb v běžným způsobem. Ukázka také ukazuje, jak používat <xref:System.ServiceModel.Activation.ServiceHostFactory> třídu použít vlastní hostitel služby v prostředí hostování internetové informační služby (IIS) nebo Windows Process Activation Service (WAS).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Hosting\CustomServiceHost`  
  
## <a name="about-the-scenario"></a>O scénář  
 Pokud chcete zabránit neúmyslnému zveřejnění metadat služby potenciálně citlivých, výchozí konfigurace pro služby Windows Communication Foundation (WCF) zakáže publikování metadat. Toto chování je ve výchozím nastavení zabezpečený, ale také znamená, že nemůžete použít metadat importovat nástroj (například Svcutil.exe) ke generování kódu klienta, který je potřeba volat službu, není-li v konfiguraci není explicitně povoleno chování publikování metadat služby.  
  
 Publikování metadat pro velký počet služeb zahrnuje přidání stejné prvky konfigurace pro jednotlivé služby, což vede k velké množství informací o konfiguraci, která je v podstatě stejné. Jako alternativu ke konfiguraci jednotlivých služeb samostatně je možné psát imperativního kódu, který umožňuje publikování jednou metadat a pak znovu použít tento kód napříč několika různých služeb. To lze provést tak, že vytvoříte novou třídu, která je odvozena z <xref:System.ServiceModel.ServiceHost> a přepíše `ApplyConfiguration`– metoda () imperativně přidat chování publikování metadat.  
  
> [!IMPORTANT]
>  Pro přehlednost Tato ukázka ukazuje, jak vytvořit koncový bod publikování metadat zabezpečená. Tyto koncové body jsou potenciálně dostupné pro anonymní neověřené uživatele a musí tak, aby byl veřejně pocházejí metadata služby odpovídající věnovat pozornost před nasazením tyto koncové body.  
  
## <a name="implementing-a-custom-servicehost"></a>Implementace vlastní hostitel služby  
 <xref:System.ServiceModel.ServiceHost> Třída zveřejňuje několik užitečné virtuální metody, které můžete přepsat dědice ke změně chování za běhu služby. Například `ApplyConfiguration`– metoda () načte informace o konfiguraci služeb z konfigurace úložiště a mění hostitele <xref:System.ServiceModel.Description.ServiceDescription> odpovídajícím způsobem. Výchozí implementace načte konfiguraci z konfiguračního souboru aplikace. Můžete přepsat vlastní implementace `ApplyConfiguration`() pro další úpravu <xref:System.ServiceModel.Description.ServiceDescription> pomocí imperativního kódu nebo dokonce i úplně nahradit výchozí konfigurace úložiště. Chcete-li například čtení konfigurace koncového bodu služby z databáze místo souboru konfigurace aplikace.  
  
 V tomto příkladu chceme vytvořit vlastní hostitel služby, který přidá třídě ServiceMetadataBehavior (který umožňuje publikování metadat), i když toto chování se nepřidá explicitně v konfiguračním souboru služby. K tomu vytvoříme novou třídu, která dědí z <xref:System.ServiceModel.ServiceHost> a přepíše `ApplyConfiguration`().  
  
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
  
 Protože jsme nechcete ignorovat všechny konfigurace, který byl poskytnut v konfiguračním souboru aplikace, první věc, kterou naše přepsání `ApplyConfiguration`nemá () je volání základní implementaci. Po dokončení této metody můžete imperativně přidáme <xref:System.ServiceModel.Description.ServiceMetadataBehavior> popis, pomocí následujících imperativního kódu.  
  
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
  
 Poslední věcí, kterou naše `ApplyConfiguration`přepsání (), musíte udělat, je přidat výchozí koncový bod metadat. Podle konvence je vytvořen jeden koncový bod metadat pro každý identifikátor URI v kolekci adres BaseAddresses hostitele služby.  
  
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
 Teď, když jsme dokončili naše vlastní implementace ServiceHost, jsme slouží k přidání chování publikování metadat k libovolné službě hostováním danou službu v rámci instance naší `SelfDescribingServiceHost`. Následující kód ukazuje, jak ho použít ve scénáři hostování na vlastním serveru.  
  
```  
SelfDescribingServiceHost host =   
         new SelfDescribingServiceHost( typeof( Calculator ) );  
host.Open();  
```  
  
 Naše vlastního hostitele stále načítá konfigurace koncového bodu služby z konfiguračního souboru aplikace, tak, jako kdyby jsme použili výchozí <xref:System.ServiceModel.ServiceHost> třídy pro hostování služby. Ale vzhledem k tomu, že jsme přidali logiky povolit publikování v rámci naší vlastního hostitele metadat, jsme již musíte povolit explicitně chování při publikování v konfiguraci metadat. Tento přístup má různé výhody, pokud vytváříte aplikaci, která obsahuje několik služeb a chcete povolit publikování metadat na každém z nich bez psaní stejný konfigurační prvky pořád dokola.  
  
## <a name="using-a-custom-servicehost-in-iis-or-was"></a>Použití vlastní hostitel služby IIS nebo WAS  
 Používání vlastní hostitel služby ve scénářích hostování na vlastním serveru je jasné, protože je kód aplikace, která je nakonec odpovědné za vytváření a otevírání instance hostitele služby. IIS nebo WAS hostitelské prostředí ale infrastruktura WCF je dynamicky vytvoření instance hostitele vaší služby odpověď na příchozí zprávy. Vlastní Obsluha hostitelů lze také v toto hostitelské prostředí, ale vyžadují další kód ve formuláři ServiceHostFactory. Následující kód ukazuje odvozený ze <xref:System.ServiceModel.Activation.ServiceHostFactory> , který vrátí instance naší vlastní `SelfDescribingServiceHost`.  
  
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
  
 Jak je vidět, implementace vlastního ServiceHostFactory je velmi jednoduché. Všechny vlastní logiku se nachází uvnitř implementace ServiceHost; objekt pro vytváření vrátí instanci odvozené třídy.  
  
 Určený objekt pro vytváření vlastní implementace služby musí přidáme některá další metadata do souboru .svc služby.  
  
```  
<%@ServiceHost Service="Microsoft.ServiceModel.Samples.CalculatorService"  
               Factory="Microsoft.ServiceModel.Samples.SelfDescribingServiceHostFactory"  
               language=c# Debug="true" %>  
```  
  
 Tady jsme přidali další `Factory` atribut `@ServiceHost` směrnice a předané CLR zadejte název objektu pro vytváření naše vlastní jako hodnotu atributu. Když služba IIS nebo WAS obdrží zprávu pro tuto službu, infrastruktury hostování WCF nejprve vytvoří instanci ServiceHostFactory a potom vytvořte instanci samotného hostitele služby pomocí volání `ServiceHostFactory.CreateServiceHost()`.  
  
## <a name="running-the-sample"></a>Spuštění ukázky  
 I když tato ukázka poskytuje plně funkčního klienta a implementaci služby, je bod ukázku si ukážeme, jak chcete změnit chování služby za běhu pomocí vlastního hostitele., proveďte následující kroky:  
  
#### <a name="to-observe-the-effect-of-the-custom-host"></a>Chcete-li sledovat účinek vlastního hostitele  
  
1.  Otevřete soubor Web.config služby a podívejte se, že neexistuje žádná konfigurace explicitně povolení metadat služby.  
  
2.  Otevřete soubor SVC služby a zda se zobrazila zpráva jeho @ServiceHost direktiva obsahuje atribut Factory, který určuje název vlastního ServiceHostFactory.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Po řešení je sestavený Build, spusťte Setup.bat nastavit aplikaci ServiceModelSamples [!INCLUDE[iisver](../../../../includes/iisver-md.md)]. Adresář ServiceModelSamples by se měla objevit jako [!INCLUDE[iisver](../../../../includes/iisver-md.md)] aplikace.  
  
4.  Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5.  Chcete-li odebrat [!INCLUDE[iisver](../../../../includes/iisver-md.md)] běhu Cleanup.bat aplikace.  
  
## <a name="see-also"></a>Viz také:
- [Postupy: Hostování služby WCF v IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
