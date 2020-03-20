---
title: Konfigurace a rozšíření modulu runtime s chováním
ms.date: 03/30/2017
helpviewer_keywords:
- attaching extensions using behaviors [WCF]
ms.assetid: 149b99b6-6eb6-4f45-be22-c967279677d9
ms.openlocfilehash: 67db06649d6059ff6b6e6fb8d84058621fcc7dab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185658"
---
# <a name="configuring-and-extending-the-runtime-with-behaviors"></a>Konfigurace a rozšíření modulu runtime s chováním
Chování umožňují změnit výchozí chování a přidat vlastní rozšíření, která kontrolují a ověřují konfiguraci služby nebo upravují chování za běhu v klientských a servisních aplikacích WCF (Windows Communication Foundation). Toto téma popisuje rozhraní chování, jak je implementovat a jak je přidat do popisu služby (v aplikaci služby) nebo koncovém bodu (v klientské aplikaci) programově nebo v konfiguračním souboru. Další informace o použití chování poskytovaného systémem naleznete [v tématu Určení chování za běhu služby](../specifying-service-run-time-behavior.md) a [určení chování za běhu klienta](../specifying-client-run-time-behavior.md).  
  
## <a name="behaviors"></a>Chování  
 Typy chování jsou přidány do objektů popisu služby nebo koncového bodu služby (na službu nebo klienta, respektive) před tyto objekty jsou používány Windows Communication Foundation (WCF) k vytvoření runtime, který provádí službu WCF nebo WCF klienta. Pokud jsou tato chování volána během procesu výstavby za běhu, jsou pak schopni získat přístup k vlastnostem a metodám runtime, které upravují za běhu vytvořený smlouvou, vazbami a adresami.  
  
### <a name="behavior-methods"></a>Metody chování  
 Všechna chování mají `AddBindingParameters` `ApplyDispatchBehavior` metodu, metodu, `Validate` metodu a metodu <xref:System.ServiceModel.Description.IServiceBehavior> `ApplyClientBehavior` `ApplyClientBehavior` s jednou výjimkou: Protože nelze spustit v klientovi, neimplementuje .  
  
- Pomocí `AddBindingParameters` metody můžete upravit nebo přidat vlastní objekty do kolekce, ke které mají vlastní vazby přístup pro jejich použití při vytvoření runtime. Například to, jak jsou určeny požadavky na ochranu, které ovlivňují způsob, jakým je kanál sestaven, ale nejsou známy vývojářkanálu.  
  
- Pomocí `Validate` metody můžete prozkoumat strom popisu a odpovídající objekt runtime, abyste se ujistili, že odpovídá určité sadě kritérií.  
  
- Pomocí `ApplyDispatchBehavior` metod `ApplyClientBehavior` a prozkoumejte strom popisu a upravte dobu runtime pro určitý obor ve službě nebo klientovi. Můžete také vložit objekty rozšíření.  
  
    > [!NOTE]
    > Ačkoli je v těchto metodách uveden strom popisu, je určen pouze k vyšetření. Pokud je změněn strom popisu, chování není definováno.  
  
 Vlastnosti, které můžete upravit, a rozhraní pro přizpůsobení, která můžete implementovat, jsou přístupné prostřednictvím tříd služby a modulu runtime klienta. Typy služeb jsou <xref:System.ServiceModel.Dispatcher.DispatchRuntime> <xref:System.ServiceModel.Dispatcher.DispatchOperation> a třídy. Typy klientů jsou <xref:System.ServiceModel.Dispatcher.ClientRuntime> <xref:System.ServiceModel.Dispatcher.ClientOperation> a třídy. A <xref:System.ServiceModel.Dispatcher.ClientRuntime> <xref:System.ServiceModel.Dispatcher.DispatchRuntime> třídy jsou vstupní body rozšiřitelnosti pro přístup k vlastnostem runtime pro celý klient a službu a kolekce rozšíření. Podobně <xref:System.ServiceModel.Dispatcher.ClientOperation> a <xref:System.ServiceModel.Dispatcher.DispatchOperation> třídy vystavit operace klienta a operace služby runtime vlastnosti a rozšíření kolekce, v uvedeném pořadí. Můžete však získat přístup k širšímu objektu runtime s rozsahem z objektu runtime operace a naopak, pokud je to nutné.  
  
> [!NOTE]
> Diskuse o vlastnostech runtime a typech rozšíření, které můžete použít k úpravě chování spuštění klienta, naleznete [v tématu Rozšíření klientů](extending-clients.md). Diskuse o vlastnostech runtime a typech rozšíření, které můžete použít k úpravě chování spuštění dispečera služby, naleznete [v tématu Rozšíření dispečerů](extending-dispatchers.md).  
  
 Většina uživatelů WCF neinteraguje přímo s runtime; místo toho používají konstrukce základního programovacího modelu, jako jsou koncové body, smlouvy, vazby, adresy a atributy chování na třídách nebo chování v konfiguračních souborech. Tyto konstrukce tvoří *strom popisu*, což je úplná specifikace pro vytvoření za běhu pro podporu služby nebo klienta popsaného stromem popisu.  
  
 Existují čtyři druhy chování v WCF:  
  
- Chování služby<xref:System.ServiceModel.Description.IServiceBehavior> (typy) umožňují přizpůsobení celého <xref:System.ServiceModel.ServiceHostBase>běhu služby včetně .  
  
- Chování koncového<xref:System.ServiceModel.Description.IEndpointBehavior> bodu (typy) umožňují přizpůsobení koncových <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> bodů služby a jejich přidružených objektů.  
  
- Chování smlouvy<xref:System.ServiceModel.Description.IContractBehavior> (typy) umožňují přizpůsobení <xref:System.ServiceModel.Dispatcher.ClientRuntime> jak <xref:System.ServiceModel.Dispatcher.DispatchRuntime> třídy, tak tříd v klientských a servisních aplikacích.  
  
- Chování operace<xref:System.ServiceModel.Description.IOperationBehavior> (typy) umožňují přizpůsobení <xref:System.ServiceModel.Dispatcher.ClientOperation> <xref:System.ServiceModel.Dispatcher.DispatchOperation> tříd a opět v klientovi a službě.  
  
 Tato chování můžete přidat do různých objektů popisu implementací vlastních atributů, pomocí konfiguračních souborů aplikace nebo přímo jejich přidáním do kolekce chování na příslušném objektu popisu. Musí však být přidán do popisu služby nebo předmětu <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> popisu <xref:System.ServiceModel.ServiceHost> koncového bodu služby před voláním na nebo <xref:System.ServiceModel.ChannelFactory%601>.  
  
### <a name="behavior-scopes"></a>Obory chování  
 Existují čtyři typy chování, z nichž každý odpovídá určitému rozsahu přístupu za běhu.  
  
#### <a name="service-behaviors"></a>Chování služby  
 Chování služby, <xref:System.ServiceModel.Description.IServiceBehavior>které implementují , jsou primární mechanismus, kterým můžete upravit celou zaběhu služby. Existují tři mechanismy pro přidání chování služby do služby.  
  
1. Použití atributu ve třídě služby.  Při <xref:System.ServiceModel.ServiceHost> vytvoření je k <xref:System.ServiceModel.ServiceHost> dispozici, implementace používá reflexe zjistit sadu atributů na typu služby. Pokud některý z těchto atributů <xref:System.ServiceModel.Description.IServiceBehavior>jsou implementace , jsou přidány <xref:System.ServiceModel.Description.ServiceDescription>do kolekce chování na . To umožňuje tyto chování k účasti na konstrukci běhu služby.  
  
2. Programově přidání chování do kolekce chování <xref:System.ServiceModel.Description.ServiceDescription>na . Toho lze dosáhnout pomocí následujících řádků kódu:  
  
    ```csharp
    ServiceHost host = new ServiceHost(/* Parameters */);  
    host.Description.Behaviors.Add(/* Service Behavior */);  
    ```  
  
3. Implementace vlastní, <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> která rozšiřuje konfiguraci. To umožňuje použití chování služby z konfiguračních souborů aplikace.  
  
 Příklady chování služby v WCF <xref:System.ServiceModel.ServiceBehaviorAttribute> patří <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>atribut, <xref:System.ServiceModel.Description.ServiceMetadataBehavior> , a chování.  
  
#### <a name="contract-behaviors"></a>Chování smlouvy  
 Chování smlouvy, které <xref:System.ServiceModel.Description.IContractBehavior> implementují rozhraní, se používají k rozšíření modulu runtime klienta i služby napříč smlouvou.  
  
 Existují dva mechanismy pro přidání chování smlouvy smlouvy.  Prvním mechanismem je vytvoření vlastního atributu, který se má použít v rozhraní smlouvy. Při předání rozhraní smlouvy buď <xref:System.ServiceModel.ServiceHost> nebo <xref:System.ServiceModel.ChannelFactory%601>nebo , WCF zkoumá atributy na rozhraní. Pokud některé atributy jsou <xref:System.ServiceModel.Description.IContractBehavior>implementace , jsou přidány do <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> kolekce chování na vytvořené pro toto rozhraní.  
  
 Můžete také implementovat <xref:System.ServiceModel.Description.IContractBehaviorAttribute?displayProperty=nameWithType> atribut chování vlastní smlouvy. V tomto případě chování je následující při použití na:  
  
 •Smluvní rozhraní. V tomto případě chování se použije na všechny kontrakty tohoto typu v libovolném <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A?displayProperty=nameWithType> koncovém bodu a WCF ignoruje hodnotu vlastnosti.  
  
 •Servisní třída. V tomto případě chování se použije pouze pro koncové body, <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> jejichž smlouva je hodnota vlastnosti.  
  
 •Třída zpětného volání. V tomto případě chování se použije na koncový bod duplexní klienta a <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> WCF ignoruje hodnotu vlastnosti.  
  
 Druhý mechanismus je přidat chování do kolekce <xref:System.ServiceModel.Description.ContractDescription>chování na .  
  
 Příklady chování smlouvy v WCF <xref:System.ServiceModel.DeliveryRequirementsAttribute?displayProperty=nameWithType> patří atribut. Další informace a příklad naleznete v referenčním tématu.  
  
#### <a name="endpoint-behaviors"></a>Chování koncového bodu  
 Chování koncového bodu, <xref:System.ServiceModel.Description.IEndpointBehavior>které implementují , jsou primární mechanismus, kterým můžete upravit celou službu nebo čas spuštění klienta pro konkrétní koncový bod.  
  
 Existují dva mechanismy pro přidání chování koncového bodu do služby.  
  
1. Přidejte chování <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> do vlastnosti.  
  
2. Implementujte <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> vlastní, který rozšiřuje konfiguraci.  
  
 Další informace a příklad naleznete v referenčním tématu.  
  
#### <a name="operation-behaviors"></a>Chování operace  
 Chování operace, které <xref:System.ServiceModel.Description.IOperationBehavior> implementují rozhraní, se používají k rozšíření modulu runtime klienta i služby pro každou operaci.  
  
 Existují dva mechanismy pro přidání chování operace do operace. První mechanismus je vytvořit vlastní atribut, který má být použit na metodu, která modeluje operaci. Při přidání operace buď <xref:System.ServiceModel.ServiceHost> nebo <xref:System.ServiceModel.ChannelFactory>nebo , WCF přidá všechny <xref:System.ServiceModel.Description.IOperationBehavior> atributy <xref:System.ServiceModel.Description.OperationDescription> do kolekce chování na vytvořené pro tuto operaci.  
  
 Druhý mechanismus je přímým přidáním chování do kolekce <xref:System.ServiceModel.Description.OperationDescription>chování na vyrobeno .  
  
 Příklady chování operace v WCF <xref:System.ServiceModel.OperationBehaviorAttribute> patří <xref:System.ServiceModel.TransactionFlowAttribute>a .  
  
 Další informace a příklad naleznete v referenčním tématu.  
  
### <a name="using-configuration-to-create-behaviors"></a>Použití konfigurace k vytvoření chování  
 Služba a koncový bod a chování smlouvy může být navržen tak, aby byly určeny v kódu nebo pomocí atributů; pomocí konfiguračních souborů aplikace nebo webu lze konfigurovat pouze chování služby a koncového bodu. Vystavení chování pomocí atributů umožňuje vývojářům určit chování v době kompilace, které nelze přidat, odebrat nebo upravit za běhu. To je často vhodné pro chování, které jsou vždy požadovány pro správnou funkci služby <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType> (například parametry související s transakcí atributu). Vystavení chování pomocí konfigurace umožňuje vývojářům ponechat specifikaci a konfiguraci těchto chování těm, kteří nasazují službu. To je vhodné pro chování, které jsou volitelné součásti nebo jiné konfigurace specifické pro nasazení, například zda metadata jsou vystaveny pro službu nebo konkrétní konfigurace autorizace pro službu.  
  
> [!NOTE]
> Můžete také použít chování, které podporují konfiguraci k vynucení zásad firemních aplikací jejich vložením do konfiguračního souboru machine.config a uzamčením těchto položek. Popis a příklad najdete v tématu [Jak: Uzamčení koncových bodů v rozlehlé síti](how-to-lock-down-endpoints-in-the-enterprise.md).  
  
 Chcete-li vystavit chování pomocí konfigurace, vývojář musí <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> vytvořit odvozenou třídu a potom zaregistrovat toto rozšíření s konfigurací.  
  
 Následující příklad kódu ukazuje, <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>jak implementuje <xref:System.ServiceModel.Description.IEndpointBehavior> :  
  
```csharp
// BehaviorExtensionElement members  
public override Type BehaviorType  
{  
  get { return typeof(EndpointBehaviorMessageInspector); }  
}  
  
protected override object CreateBehavior()  
{  
  return new EndpointBehaviorMessageInspector();  
}  
```  
  
 Aby mohl konfigurační systém <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>načíst vlastní , musí být registrován jako rozšíření. Následující příklad kódu ukazuje konfigurační soubor pro předchozí chování koncového bodu:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service
        name="Microsoft.WCF.Documentation.SampleService"  
        behaviorConfiguration="metadataSupport"  
      >  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8080/ServiceMetadata" />  
          </baseAddresses>  
        </host>  
        <endpoint  
          address="/SampleService"  
          binding="wsHttpBinding"  
          behaviorConfiguration="withMessageInspector"
          contract="Microsoft.WCF.Documentation.ISampleService"  
        />  
        <endpoint  
           address="mex"  
           binding="mexHttpBinding"  
           contract="IMetadataExchange"  
        />  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
      <behavior name="metadataSupport">  
        <serviceMetadata httpGetEnabled="true" httpGetUrl=""/>  
      </behavior>  
      </serviceBehaviors>  
      <endpointBehaviors>  
        <behavior name="withMessageInspector">  
          <endpointMessageInspector />  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <extensions>  
      <behaviorExtensions>  
        <add
          name="endpointMessageInspector"  
          type="Microsoft.WCF.Documentation.EndpointBehaviorMessageInspector, HostApplication, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null"  
        />  
      </behaviorExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
 Kde `Microsoft.WCF.Documentation.EndpointBehaviorMessageInspector` je typ rozšíření `HostApplication` chování a je název sestavení, do kterého byla tato třída zkompilována.  
  
### <a name="evaluation-order"></a>Pořadí hodnocení  
 A <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> a <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> jsou zodpovědné za vytváření runtime z programovacímodel a popis. Chování, jak již bylo popsáno, přispívají k tomuto procesu sestavení ve službě, koncovém bodu, smlouvě a operaci.  
  
 Platí <xref:System.ServiceModel.ServiceHost> chování v následujícím pořadí:  
  
1. Služba  
  
2. Kontrakt  
  
3. Koncový bod  
  
4. Operace  
  
 V rámci jakékoli kolekce chování není zaručena žádná objednávka.  
  
 Platí <xref:System.ServiceModel.ChannelFactory%601> chování v následujícím pořadí:  
  
1. Kontrakt  
  
2. Koncový bod  
  
3. Operace  
  
 V rámci jakékoli kolekce chování, opět žádné pořadí je zaručena.  
  
### <a name="adding-behaviors-programmatically"></a>Programové přidávání chování  
 Vlastnosti <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> aplikace služby nesmí být změněny <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType> po <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>metodě na . Některé členy, <xref:System.ServiceModel.ServiceHostBase.Credentials%2A?displayProperty=nameWithType> jako je `AddServiceEndpoint` vlastnost <xref:System.ServiceModel.ServiceHostBase> <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>a metody na a , vyvolat výjimku, pokud změněn a za tento bod. Jiné umožňují jejich úpravy, ale výsledek není definován.  
  
 Podobně na straně klienta <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> hodnoty nesmí být změněny po volání <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> na . <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> Vlastnost <xref:System.ServiceModel.ChannelFactory.Credentials%2A?displayProperty=nameWithType> vyvolá výjimku, pokud je změněna za tento bod, ale ostatní hodnoty popisu klienta lze změnit bez chyby. Výsledek však není definován.  
  
 Ať už se jedná o službu nebo klienta, <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType>doporučujeme upravit popis před voláním .  
  
### <a name="inheritance-rules-for-behavior-attributes"></a>Pravidla dědičnosti pro atributy chování  
 Všechny čtyři typy chování mohou být naplněny pomocí atributů – chování služby a chování smlouvy. Vzhledem k tomu, že atributy jsou definovány na spravovaných objektech a členech a spravované objekty a členové podporují dědičnost, je nutné definovat, jak atributy chování fungují v kontextu dědičnosti.  
  
 Na vysoké úrovni je pravidlem, že pro určitý obor (například služba, smlouva nebo operace) jsou použity všechny atributy chování v hierarchii dědičnosti pro daný obor. Pokud existují dva atributy chování stejného typu, používá se pouze nejvíce odvozený typ.  
  
#### <a name="service-behaviors"></a>Chování služby  
 Pro danou třídu služby jsou použity všechny atributy chování služby v této třídě a na rodiče této třídy. Pokud je stejný typ atributu použit na více místech v hierarchii dědičnosti, použije se nejvíce odvozený typ.  
  
```csharp  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Multiple)]  
[AspNetCompatibilityRequirementsAttribute(  
    AspNetCompatibilityRequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]  
public class A { /* … */ }  
  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
public class B : A { /* … */}  
```  
  
 Například v předchozím případě služba B skončí s <xref:System.ServiceModel.InstanceContextMode> <xref:System.ServiceModel.InstanceContextMode.Single>of <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> , <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>režim a <xref:System.ServiceModel.ConcurrencyMode> <xref:System.ServiceModel.ConcurrencyMode.Single>. Is <xref:System.ServiceModel.ConcurrencyMode> <xref:System.ServiceModel.ConcurrencyMode.Single>, <xref:System.ServiceModel.ServiceBehaviorAttribute> protože atribut v službě B je na "více odvozené" než v provozu A.  
  
#### <a name="contract-behaviors"></a>Chování smlouvy  
 Pro danou smlouvu jsou použity všechny atributy chování smlouvy v tomto rozhraní a na rodiče tohoto rozhraní. Pokud je stejný typ atributu použit na více místech v hierarchii dědičnosti, použije se nejvíce odvozený typ.  
  
#### <a name="operation-behaviors"></a>Chování operace  
 Pokud daná operace nepřepíše existující abstraktní nebo virtuální operaci, neplatí žádná pravidla dědičnosti.  
  
 Pokud operace přepsat existující operaci, pak jsou použity všechny atributy chování operace na této operaci a na nadřazené této operace.  Pokud je stejný typ atributu použit na více místech v hierarchii dědičnosti, použije se nejvíce odvozený typ.
