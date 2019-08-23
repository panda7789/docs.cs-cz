---
title: Konfigurace a rozšíření modulu runtime s chováním
ms.date: 03/30/2017
helpviewer_keywords:
- attaching extensions using behaviors [WCF]
ms.assetid: 149b99b6-6eb6-4f45-be22-c967279677d9
ms.openlocfilehash: 481e0983a40bb551d08894ea32f76f332b8fe5a3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943140"
---
# <a name="configuring-and-extending-the-runtime-with-behaviors"></a>Konfigurace a rozšíření modulu runtime s chováním
Chování umožňují upravit výchozí chování a přidat vlastní rozšíření, která kontrolují a ověřují konfiguraci služby nebo mění chování modulu runtime v klientech a aplikacích služby Windows Communication Foundation (WCF). Toto téma popisuje rozhraní chování, způsob jejich implementace a postup jejich přidání do popisu služby (v aplikaci služby) nebo koncového bodu (v klientské aplikaci) prostřednictvím kódu programu nebo v konfiguračním souboru. Další informace o použití chování poskytované systémem naleznete v tématu [Určení chování služby](../../../../docs/framework/wcf/specifying-service-run-time-behavior.md) za běhu a [Určení chování při spuštění klienta](../../../../docs/framework/wcf/specifying-client-run-time-behavior.md).  
  
## <a name="behaviors"></a>Chování  
 Typy chování jsou přidány do objektů služby nebo popisu koncového bodu služby (ve službě nebo klientovi) předtím, než tyto objekty používají Windows Communication Foundation (WCF) k vytvoření modulu runtime, který spouští službu WCF nebo klienta WCF. Když jsou tato chování volána během procesu výroby za běhu, pak mají přístup k vlastnostem a metodám modulu runtime, které upravují modul runtime vytvořený Smlouvou, vazbami a adresami.  
  
### <a name="behavior-methods"></a>Metody chování  
 Všechna chování mají `AddBindingParameters` metodu `ApplyDispatchBehavior` , metodu, `Validate` metodu a `ApplyClientBehavior` metodu s jednou výjimkou: Vzhledem <xref:System.ServiceModel.Description.IServiceBehavior> k tomu, že nelze provést v klientovi, neimplementuje. `ApplyClientBehavior`  
  
- `AddBindingParameters` Použijte metodu pro úpravu nebo přidání vlastních objektů do kolekce, které vlastní vazby mají přístup k jejich použití, když je modul runtime vytvořen. Například to, jak jsou zadány požadavky na ochranu, které ovlivňují způsob sestavení kanálu, ale nejsou známy vývojářem kanálu.  
  
- `Validate` Použijte metodu k prohlédnutí stromu popis a odpovídajícího běhového objektu, abyste se ujistili, že je v souladu s určitou sadou kritérií.  
  
- Použijte metody `ApplyClientBehavior` a k prohlédnutí stromu Description a upravte modul runtime pro konkrétní obor buď na službě, nebo na klientovi. `ApplyDispatchBehavior` Také můžete vkládat i objekty rozšíření.  
  
    > [!NOTE]
    > I když je v těchto metodách k dispozici strom popisu, je určen pouze k posouzení. Pokud se změní strom popisu, chování není definováno.  
  
 Vlastnosti, které lze upravit, a rozhraní vlastního nastavení, které lze implementovat, jsou k dispozici prostřednictvím tříd modulu runtime služby a klienta. Typy služeb jsou <xref:System.ServiceModel.Dispatcher.DispatchRuntime> třídy a <xref:System.ServiceModel.Dispatcher.DispatchOperation> . Typy klientů jsou <xref:System.ServiceModel.Dispatcher.ClientRuntime> třídy a <xref:System.ServiceModel.Dispatcher.ClientOperation> . Třídy <xref:System.ServiceModel.Dispatcher.ClientRuntime> a<xref:System.ServiceModel.Dispatcher.DispatchRuntime> jsou vstupními body rozšiřitelnosti pro přístup k běhovým vlastnostem a kolekcím rozšíření v rámci služby na úrovni klienta. Podobně třídy <xref:System.ServiceModel.Dispatcher.DispatchOperation> a zveřejňují operace klienta a vlastnosti a kolekce rozšíření běhu služby. <xref:System.ServiceModel.Dispatcher.ClientOperation> V případě potřeby však můžete získat přístup k širšímu objektu modulu runtime z běhového objektu operace a naopak.  
  
> [!NOTE]
> Diskuzi o vlastnostech běhového prostředí a typech rozšíření, které můžete použít k úpravě chování klienta, najdete v tématu [rozšíření klientů](../../../../docs/framework/wcf/extending/extending-clients.md). Diskuzi o vlastnostech běhového prostředí a typech rozšíření, které můžete použít k úpravě chování vykonávání dispečera služby, najdete v tématu [rozšíření expedičních](../../../../docs/framework/wcf/extending/extending-dispatchers.md)modulů.  
  
 Většina uživatelů WCF nekomunikuje s modulem runtime přímo; místo toho používají konstrukce základního programovacího modelu, jako jsou koncové body, kontrakty, vazby, adresy a atributy chování pro třídy nebo chování v konfiguračních souborech. Tyto konstrukce tvoří *strom popisů*, což je kompletní specifikace pro sestavení modulu runtime pro podporu služby nebo klienta popsaných ve stromu popis.  
  
 WCF nabízí čtyři druhy chování:  
  
- Chování služby (<xref:System.ServiceModel.Description.IServiceBehavior> typy) umožňuje přizpůsobení celého modulu runtime služby, včetně. <xref:System.ServiceModel.ServiceHostBase>  
  
- Chování koncového<xref:System.ServiceModel.Description.IEndpointBehavior> bodu (typy) umožňují přizpůsobení koncových bodů služby a <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> jejich přidružených objektů.  
  
- Chování kontraktu<xref:System.ServiceModel.Description.IContractBehavior> (typy) umožňuje přizpůsobení <xref:System.ServiceModel.Dispatcher.ClientRuntime> tříd a <xref:System.ServiceModel.Dispatcher.DispatchRuntime> v aplikacích klienta i služby.  
  
- Chování operace (<xref:System.ServiceModel.Description.IOperationBehavior> typy) umožňují v klientech a <xref:System.ServiceModel.Dispatcher.ClientOperation> službách <xref:System.ServiceModel.Dispatcher.DispatchOperation> znovu přizpůsobit třídy a.  
  
 Tato chování můžete přidat do různých objektů popisu implementací vlastních atributů, pomocí konfiguračních souborů aplikace nebo přímo jejich přidáním do kolekce chování na příslušném objektu Description. Před voláním metody <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> <xref:System.ServiceModel.ServiceHost> nebo <xref:System.ServiceModel.ChannelFactory%601>je však nutné přidat k objektu popisu služby nebo popisu koncového bodu služby.  
  
### <a name="behavior-scopes"></a>Rozsahy chování  
 Existují čtyři typy chování, z nichž každý odpovídá konkrétnímu oboru přístupu za běhu.  
  
#### <a name="service-behaviors"></a>Chování služby  
 Chování služby, které implementuje <xref:System.ServiceModel.Description.IServiceBehavior>, jsou primárním mechanismem, pomocí kterého upravujete celý modul runtime služby. Existují tři mechanismy pro přidání chování služby ke službě.  
  
1. Použití atributu pro třídu služby.  Když je vytvořen <xref:System.ServiceModel.ServiceHost> , implementace používá reflexi k zjištění sady atributů typu služby. <xref:System.ServiceModel.ServiceHost> Pokud jsou některé z těchto atributů implementace <xref:System.ServiceModel.Description.IServiceBehavior>, jsou přidány do kolekce chování v <xref:System.ServiceModel.Description.ServiceDescription>nástroji. To umožňuje, aby se toto chování účastnilo konstrukce doby běhu služby.  
  
2. Programové přidání chování do kolekce chování na <xref:System.ServiceModel.Description.ServiceDescription>. To lze provést s následujícími řádky kódu:  
  
    ```csharp
    ServiceHost host = new ServiceHost(/* Parameters */);  
    host.Description.Behaviors.Add(/* Service Behavior */);  
    ```  
  
3. Implementace vlastního <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> , který rozšiřuje konfiguraci. To umožňuje použití chování služby z konfiguračních souborů aplikace.  
  
 Příklady chování služby ve službě WCF zahrnují <xref:System.ServiceModel.ServiceBehaviorAttribute> atribut <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>, a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> chování.  
  
#### <a name="contract-behaviors"></a>Chování kontraktu  
 Chování kontraktu, které implementuje <xref:System.ServiceModel.Description.IContractBehavior> rozhraní, slouží k rozšiřování klienta i modulu runtime služby v rámci smlouvy.  
  
 Existují dva mechanismy pro přidání chování kontraktu do smlouvy.  Prvním mechanismem je vytvoření vlastního atributu pro použití v rozhraní kontraktu. Když je rozhraní kontraktu předáno do <xref:System.ServiceModel.ServiceHost> <xref:System.ServiceModel.ChannelFactory%601>nebo, WCF prověřuje atributy v rozhraní. Pokud jsou některé atributy implementace <xref:System.ServiceModel.Description.IContractBehavior>, přidají se do kolekce <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> chování vytvořené pro toto rozhraní.  
  
 <xref:System.ServiceModel.Description.IContractBehaviorAttribute?displayProperty=nameWithType> U atributu chování vlastní smlouvy taky můžete implementovat. V takovém případě je chování následující při použití na:  
  
 • Rozhraní kontraktu. V takovém případě se chování použije na všechny kontrakty daného typu v libovolném koncovém bodě a WCF ignoruje hodnotu <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A?displayProperty=nameWithType> vlastnosti.  
  
 • Třída služby. V tomto případě se chování aplikuje jenom na koncové body, jejichž kontrakt je hodnota <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> vlastnosti.  
  
 • Třída zpětného volání. V takovém případě se chování aplikuje na koncový bod duplexního klienta a WCF ignoruje hodnotu <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> vlastnosti.  
  
 Druhým mechanismem je přidat chování do kolekce chování v <xref:System.ServiceModel.Description.ContractDescription>.  
  
 Příklady chování kontraktu ve službě WCF zahrnují <xref:System.ServiceModel.DeliveryRequirementsAttribute?displayProperty=nameWithType> atribut. Další informace a příklad najdete v referenčním tématu.  
  
#### <a name="endpoint-behaviors"></a>Chování koncového bodu  
 Chování koncového bodu, <xref:System.ServiceModel.Description.IEndpointBehavior>které implementuje, jsou primárním mechanismem, kterým měníte celou službu nebo dobu běhu klienta pro konkrétní koncový bod.  
  
 Existují dva mechanismy pro přidání chování koncového bodu ke službě.  
  
1. Přidejte chování do <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> vlastnosti.  
  
2. Implementujte vlastní <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> , který rozšiřuje konfiguraci.  
  
 Další informace a příklad najdete v referenčním tématu.  
  
#### <a name="operation-behaviors"></a>Chování operace  
 Chování operace, která implementuje <xref:System.ServiceModel.Description.IOperationBehavior> rozhraní, slouží k rozšiřování klienta i služby Service runtime pro každou operaci.  
  
 Existují dva mechanismy pro přidání chování operace do operace. Prvním mechanismem je vytvoření vlastního atributu, který bude použit pro metodu, která modeluje operaci. <xref:System.ServiceModel.ServiceHost> Při přidání operace do <xref:System.ServiceModel.ChannelFactory>nebo a přidá WCF všechny <xref:System.ServiceModel.Description.IOperationBehavior> atributy do kolekce <xref:System.ServiceModel.Description.OperationDescription> chování vytvořené pro tuto operaci.  
  
 Druhý mechanismus je přímým přidáním chování do kolekce chování na vytvořeném <xref:System.ServiceModel.Description.OperationDescription>.  
  
 Příklady chování operace ve službě WCF zahrnují <xref:System.ServiceModel.OperationBehaviorAttribute> <xref:System.ServiceModel.TransactionFlowAttribute>a.  
  
 Další informace a příklad najdete v referenčním tématu.  
  
### <a name="using-configuration-to-create-behaviors"></a>Chování při vytváření pomocí konfigurace  
 Chování služeb a koncových bodů a kontraktů může být navrženo v kódu nebo pomocí atributů; pomocí konfiguračních souborů aplikace nebo webu lze nakonfigurovat pouze chování služby a koncového bodu. Vystavení chování pomocí atributů umožňuje vývojářům určit chování při kompilaci, které nelze přidat, odebrat nebo upravit za běhu. To je často vhodné pro chování, která jsou vždy vyžadována pro správnou operaci služby (například parametry vztahující se k <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType> transakcím atributu). Vystavení chování pomocí konfigurace umožňuje vývojářům ponechat specifikaci a konfiguraci těchto chování pro ty, kteří nasazují službu. To je vhodné pro chování, které jsou volitelné součásti nebo jiná konfigurace specifická pro nasazení, jako je třeba to, jestli jsou metadata pro službu nebo konkrétní konfiguraci autorizace pro službu vystavená.  
  
> [!NOTE]
> Můžete také použít chování, které podporuje konfiguraci k vymáhání zásad firemních aplikací, a to tak, že je vložíte do konfiguračního souboru Machine. config a tyto položky zamknete. Popis a příklad naleznete v tématu [How to: Zamčení koncových bodů v](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md)podniku.  
  
 Aby bylo možné vystavit chování pomocí konfigurace, musí vývojář vytvořit odvozenou <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> třídu a pak toto rozšíření registrovat s konfigurací.  
  
 Následující příklad kódu ukazuje, jak <xref:System.ServiceModel.Description.IEndpointBehavior> implementace: <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>  
  
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
  
 Aby konfigurační systém mohl načíst vlastní <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>, musí být zaregistrován jako rozšíření. Následující příklad kódu ukazuje konfigurační soubor pro předchozí chování koncového bodu:  
  
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
  
 Kde `Microsoft.WCF.Documentation.EndpointBehaviorMessageInspector` je typ rozšíření chování a `HostApplication` je název sestavení, do kterého byla tato třída zkompilována.  
  
### <a name="evaluation-order"></a>Pořadí vyhodnocování  
 <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> Ajsouzodpovědnézasestavenímoduluruntimezprogramovacího<xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> modelu a popisu. Chování, jak je popsáno výše, přispívá k procesu sestavení v rámci služby, koncového bodu, kontraktu a operace.  
  
 Chování <xref:System.ServiceModel.ServiceHost> při použití v následujícím pořadí:  
  
1. Služba  
  
2. Kontrakt  
  
3. Koncový bod  
  
4. Operace  
  
 V rámci libovolné kolekce chování není zaručena žádná objednávka.  
  
 Chování <xref:System.ServiceModel.ChannelFactory%601> při použití v následujícím pořadí:  
  
1. Kontrakt  
  
2. Koncový bod  
  
3. Operace  
  
 V rámci libovolné kolekce chování není zaručena žádná objednávka.  
  
### <a name="adding-behaviors-programmatically"></a>Programové přidání chování  
 Vlastnosti v aplikaci služby nesmí být upraveny <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType> metodou na <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>. <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> Někteří členové, například vlastnost <xref:System.ServiceModel.ServiceHostBase.Credentials%2A?displayProperty=nameWithType> `AddServiceEndpoint` a metody na <xref:System.ServiceModel.ServiceHostBase> a <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>, vyvolávají výjimku, pokud byla změněna za tento bod. Jiné vám umožní je upravovat, ale výsledek není definován.  
  
 Podobně na straně klienta <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> hodnoty nesmí být upraveny po volání metody do. <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> <xref:System.ServiceModel.ChannelFactory.Credentials%2A?displayProperty=nameWithType> Vlastnost vyvolá výjimku, pokud byla změněna za tento bod, ale ostatní hodnoty Popis klienta lze upravovat bez chyby. Výsledek však není definován.  
  
 Bez ohledu na to, jestli pro službu nebo klienta, se doporučuje změnit popis před voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType>.  
  
### <a name="inheritance-rules-for-behavior-attributes"></a>Pravidla dědičnosti pro atributy chování  
 Všechny čtyři typy chování lze naplnit pomocí atributů – chování služby a chování kontraktu. Vzhledem k tomu, že atributy jsou definovány pro spravované objekty a členy a spravované objekty a členy podporují dědičnost, je nutné definovat způsob fungování atributů chování v kontextu dědičnosti.  
  
 Toto pravidlo je na nejvyšší úrovni nastaveno pro konkrétní obor (například služba, kontrakt nebo operace). jsou aplikovány všechny atributy chování v hierarchii dědičnosti pro daný obor. Pokud existují dva atributy chování stejného typu, je použit pouze nejvíc odvozený typ.  
  
#### <a name="service-behaviors"></a>Chování služby  
 Pro danou třídu služby se používají všechny atributy chování služby na této třídě a v nadřazených třídách dané třídy. Pokud je stejný typ atributu použit na více místech v hierarchii dědičnosti, je použit nejvíc odvozený typ.  
  
```csharp  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Multiple)]  
[AspNetCompatibilityRequirementsAttribute(  
    AspNetCompatibilityRequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]  
public class A { /* … */ }  
  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
public class B : A { /* … */}  
```  
  
 Například v předchozím případě služba B skončí s <xref:System.ServiceModel.InstanceContextMode> z <xref:System.ServiceModel.InstanceContextMode.Single>, <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> režimem <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>a a <xref:System.ServiceModel.ConcurrencyMode>. <xref:System.ServiceModel.ConcurrencyMode.Single> <xref:System.ServiceModel.ConcurrencyMode> Je ,<xref:System.ServiceModel.ConcurrencyMode.Single>protože atributuslužbyBjena"víceodvozených<xref:System.ServiceModel.ServiceBehaviorAttribute> ", než je u služby A.  
  
#### <a name="contract-behaviors"></a>Chování kontraktu  
 V případě konkrétní smlouvy se aplikují všechny atributy chování kontraktů na daném rozhraní a v nadřazených objektech tohoto rozhraní. Pokud je stejný typ atributu použit na více místech v hierarchii dědičnosti, je použit nejvíc odvozený typ.  
  
#### <a name="operation-behaviors"></a>Chování operace  
 Pokud daná operace nepřepisuje existující abstraktní nebo virtuální operaci, nepoužijí se žádná pravidla dědičnosti.  
  
 Pokud operace přepíše existující operaci, budou aplikovány všechny atributy chování operace v této operaci a v nadřazených objektech této operace.  Pokud je stejný typ atributu použit na více místech v hierarchii dědičnosti, je použit nejvíc odvozený typ.
