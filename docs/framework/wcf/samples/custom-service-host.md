---
title: Vlastní hostitel služby
ms.date: 03/30/2017
ms.assetid: fe16ff50-7156-4499-9c32-13d8a79dc100
ms.openlocfilehash: 2aed557d1d045c08aed206660aa7b4b75ffe0e2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145069"
---
# <a name="custom-service-host"></a>Vlastní hostitel služby
Tato ukázka ukazuje, jak použít <xref:System.ServiceModel.ServiceHost> vlastní derivaci třídy ke změně chování za běhu služby. Tento přístup poskytuje opakovaně použitelnou alternativu ke konfiguraci velkého počtu služeb běžným způsobem. Ukázka také ukazuje, jak <xref:System.ServiceModel.Activation.ServiceHostFactory> použít třídu k použití vlastního ServiceHost v internetové informační službě (IIS) nebo službě aktivace procesů systému Windows (WAS) hostingové prostředí.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Hosting\CustomServiceHost`  
  
## <a name="about-the-scenario"></a>O scénáři
 Chcete-li zabránit neúmyslnému zveřejnění potenciálně citlivých metadat služby, výchozí konfigurace pro služby WCF (Windows Communication Foundation) zakáže publikování metadat. Toto chování je ve výchozím nastavení zabezpečené, ale také znamená, že nelze použít nástroj pro import metadat (například Svcutil.exe) ke generování klientského kódu potřebného k volání služby, pokud není v konfiguraci explicitně povoleno chování publikování metadat služby.  
  
 Povolení publikování metadat pro velký počet služeb zahrnuje přidání stejných prvků konfigurace do každé jednotlivé služby, což má za následek velké množství informací o konfiguraci, která je v podstatě stejná. Jako alternativu ke konfiguraci jednotlivých služeb jednotlivě je možné napsat imperativní kód, který umožňuje publikování metadat jednou a potom znovu použít tento kód v několika různých službách. Toho lze dosáhnout vytvořením nové třídy, která je odvozena od <xref:System.ServiceModel.ServiceHost> a přepíše `ApplyConfiguration`() metodu, aby bylo nutné přidat chování publikování metadat.  
  
> [!IMPORTANT]
> Pro přehlednost tato ukázka ukazuje, jak vytvořit koncový bod publikování nezabezpečených metadat. Tyto koncové body jsou potenciálně k dispozici anonymní matné neověřené spotřebitele a je třeba dbát na to před nasazením těchto koncových bodů, aby bylo zajištěno, že je vhodné veřejně zveřejnit metadata služby.  
  
## <a name="implementing-a-custom-servicehost"></a>Implementace vlastního ServiceHost
 Třída <xref:System.ServiceModel.ServiceHost> zveřejňuje několik užitečných virtuálních metod, které dědicové mohou přepsat změnit chování za běhu služby. Například `ApplyConfiguration`() metoda čte informace o konfiguraci služby z <xref:System.ServiceModel.Description.ServiceDescription> úložiště konfigurace a odpovídajícím způsobem změní hostitele. Výchozí implementace čte konfiguraci z konfiguračního souboru aplikace. Vlastní implementace můžete `ApplyConfiguration`přepsat () dále <xref:System.ServiceModel.Description.ServiceDescription> změnit pomocí imperativní kód nebo dokonce nahradit výchozí úložiště konfigurace úplně. Chcete-li například číst konfiguraci koncového bodu služby z databáze namísto konfiguračního souboru aplikace.  
  
 V této ukázce chceme vytvořit vlastní ServiceHost, který přidá ServiceMetadataBehavior (který umožňuje publikování metadat), i v případě, že toto chování není explicitně přidán do konfiguračního souboru služby. K dosažení tohoto cíle vytvoříme novou <xref:System.ServiceModel.ServiceHost> třídu, `ApplyConfiguration`která dědí z a přepíše ().  
  
```csharp
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
  
 Vzhledem k tomu, že nechceme ignorovat žádnou konfiguraci, která byla poskytnuta `ApplyConfiguration`v konfiguračním souboru aplikace, první věc, kterou naše přepsání () dělá, je volání základní implementace. Jakmile tato metoda dokončí, můžeme imperativně přidat <xref:System.ServiceModel.Description.ServiceMetadataBehavior> do popisu pomocí následujícího imperativníkód.  
  
```csharp
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
  
 Poslední věc, `ApplyConfiguration`kterou naše () přepsání musí udělat, je přidat výchozí koncový bod metadat. Podle konvence je vytvořen jeden koncový bod metadat pro každý identifikátor URI v kolekci BaseAddresses hostitele služby.  
  
```csharp
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
  
## <a name="using-a-custom-servicehost-in-self-host"></a>Použití vlastního ServiceHost v samoobslužném hostiteli  
 Nyní, když jsme dokončili naši vlastní implementaci ServiceHost, můžeme ji použít k přidání chování publikování `SelfDescribingServiceHost`metadat do libovolné služby tím, že tuto službu hostujeme uvnitř instance našeho . Následující kód ukazuje, jak ji použít ve scénáři vlastního hostitele.  
  
```csharp
SelfDescribingServiceHost host =
         new SelfDescribingServiceHost( typeof( Calculator ) );  
host.Open();  
```  
  
 Náš vlastní hostitel stále čte konfiguraci koncového bodu služby z konfiguračního <xref:System.ServiceModel.ServiceHost> souboru aplikace, stejně jako kdybychom použili výchozí třídu k hostování služby. Protože jsme však přidali logiku umožňující publikování metadat uvnitř našeho vlastního hostitele, již nesmíme explicitně povolit chování publikování metadat v konfiguraci. Tento přístup má výraznou výhodu při vytváření aplikace, která obsahuje několik služeb a chcete povolit publikování metadat na každé z nich bez psaní stejné konfigurační prvky znovu a znovu.  
  
## <a name="using-a-custom-servicehost-in-iis-or-was"></a>Použití vlastního servicehost ve službě IIS nebo WAS  
 Použití vlastního hostitele služby ve scénářích vlastního hostitele je jednoduché, protože je to kód aplikace, který je nakonec zodpovědný za vytvoření a otevření instance hostitele služby. V hostitelském prostředí služby IIS nebo WAS však infrastruktura WCF dynamicky instanci hostitele služby v reakci na příchozí zprávy. Vlastní hostitelé služeb lze také použít v tomto hostitelském prostředí, ale vyžadují nějaký další kód ve formě ServiceHostFactory. Následující kód ukazuje <xref:System.ServiceModel.Activation.ServiceHostFactory> derivaci, která vrací `SelfDescribingServiceHost`instance našeho vlastního .  
  
```csharp
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
  
 Jak můžete vidět, implementace vlastní ServiceHostFactory je velmi jednoduchá. Všechny vlastní logiky se nachází uvnitř implementace ServiceHost; factory vrátí instanci odvozené třídy.  
  
 Chcete-li použít vlastní továrnu s implementací služby, musíme do souboru .svc služby přidat další metadata.  
  
```xml
<%@ServiceHost Service="Microsoft.ServiceModel.Samples.CalculatorService"
               Factory="Microsoft.ServiceModel.Samples.SelfDescribingServiceHostFactory"
               language=c# Debug="true" %>
```
  
 Zde jsme přidali `Factory` další `@ServiceHost` atribut směrnice a předal název typu CLR naší vlastní továrny jako hodnota atributu. Když služba IIS nebo WAS obdrží zprávu pro tuto službu, hostitelská infrastruktura WCF nejprve vytvoří instanci ServiceHostFactory a potom vytvoří instanci samotného hostitele služby voláním `ServiceHostFactory.CreateServiceHost()`.  
  
## <a name="running-the-sample"></a>Spuštění ukázky  
 I když tato ukázka poskytuje plně funkční implementaci klienta a služby, bod ukázky je ilustrovat, jak změnit chování služby za běhu pomocí vlastního hostitele., postupujte takto:  
  
### <a name="observe-the-effect-of-the-custom-host"></a>Sledujte účinek vlastního hostitele
  
1. Otevřete soubor Web.config služby a všimněte si, že neexistuje žádná konfigurace, která by explicitně povoluje metadata pro službu.  
  
2. Otevřete soubor .svc služby a @ServiceHost všimněte si, že jeho směrnice obsahuje atribut Factory, který určuje název vlastní ServiceHostFactory.  
  
### <a name="set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Chcete-li vytvořit řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](building-the-samples.md).

3. Po vytvoření řešení spusťte soubor Setup.bat a nastavte aplikaci ServiceModelSamples ve službě IIS 7.0. Adresář ServiceModelSamples by se nyní měl zobrazit jako aplikace služby IIS 7.0.

4. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](running-the-samples.md).

5. Chcete-li odebrat aplikaci služby IIS 7.0, spusťte *soubor Cleanup.bat*.

## <a name="see-also"></a>Viz také

- [Postupy: Hostování služby WCF v IIS](../feature-details/how-to-host-a-wcf-service-in-iis.md)
