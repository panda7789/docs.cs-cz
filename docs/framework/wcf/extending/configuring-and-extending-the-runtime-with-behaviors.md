---
title: Konfigurace a rozšíření modulu runtime s chováním
ms.date: 03/30/2017
helpviewer_keywords:
- attaching extensions using behaviors [WCF]
ms.assetid: 149b99b6-6eb6-4f45-be22-c967279677d9
ms.openlocfilehash: 707b365a0f64055497e6b8814633acf7f4d7097c
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50041190"
---
# <a name="configuring-and-extending-the-runtime-with-behaviors"></a>Konfigurace a rozšíření modulu runtime s chováním
Chování umožňují změnit výchozí chování a přidejte vlastní rozšíření, které kontrola a ověření konfigurace služby a změny chování za běhu v aplikacích pro klienta a služby Windows Communication Foundation (WCF). Toto téma popisuje chování rozhraní, jak je implementovat a jak přidat popis služby (v aplikaci služby) nebo koncový bod (v klientské aplikaci) prostřednictvím kódu programu nebo v konfiguračním souboru. Další informace o používání poskytované systémem chování najdete v tématu [určení chování za běhu služby](../../../../docs/framework/wcf/specifying-service-run-time-behavior.md) a [určení chování za běhu klienta](../../../../docs/framework/wcf/specifying-client-run-time-behavior.md).  
  
## <a name="behaviors"></a>Chování  
 Chování typy jsou přidány do služby nebo objekty popis koncový bod služby (na službu nebo klienta, v uvedeném pořadí) předtím, než tyto objekty se používají ve Windows Communication Foundation (WCF) k vytvoření modulu runtime, který se spustí služby WCF nebo klienta WCF. Při volání těchto projevů během procesu vytváření modulu runtime jsou pak přístup k modulu runtime vlastnosti a metody, které upravují modul runtime, a to provedením smlouvy, vazeb a adresy.  
  
### <a name="behavior-methods"></a>Chování metody  
 Mají všechny chování `AddBindingParameters` metoda, `ApplyDispatchBehavior` metoda, `Validate` metoda a `ApplyClientBehavior` metody s jednou výjimkou: protože <xref:System.ServiceModel.Description.IServiceBehavior> nelze provést v klientovi, neimplementuje `ApplyClientBehavior`.  
  
-   Použít `AddBindingParameters` metoda změnit nebo přidat vlastní objekty do kolekce, která vlastní vazby mít přístup k jejich použití, jakmile modul runtime je vytvořena. Například to způsob, jakým požadavkům na ochranu jsou zadány, která mají vliv na způsob je postavená na kanál, ale nejsou platná pro kanál pro vývojáře.  
  
-   Použití `Validate` metoda podívejte se na popis stromu a odpovídající objekt runtime tak, aby byl odpovídá některé sadu kritérií.  
  
-   Použití `ApplyDispatchBehavior` a `ApplyClientBehavior` metody ke kontrole popisu stromové struktury a upravit modul runtime pro konkrétní obor na službu nebo klienta. Můžete také vložit také objektů rozšíření.  
  
    > [!NOTE]
    >  I když popis stromu je k dispozici v těchto metod, je pro zkoumání pouze. Pokud se změní popis stromu, není chování definováno.  
  
 Vlastnosti můžete upravit a vlastního nastavení rozhraní, které můžete implementovat jsou přístupné prostřednictvím runtime třídy klienta a služby. Typy služby jsou <xref:System.ServiceModel.Dispatcher.DispatchRuntime> a <xref:System.ServiceModel.Dispatcher.DispatchOperation> třídy. Jsou typy klientů <xref:System.ServiceModel.Dispatcher.ClientRuntime> a <xref:System.ServiceModel.Dispatcher.ClientOperation> třídy. <xref:System.ServiceModel.Dispatcher.ClientRuntime> a <xref:System.ServiceModel.Dispatcher.DispatchRuntime> třídy jsou vstupní body rozšiřitelnosti pro přístup k úrovni klienta a služby modulu runtime, vlastnosti a kolekce rozšíření. Podobně platí <xref:System.ServiceModel.Dispatcher.ClientOperation> a <xref:System.ServiceModel.Dispatcher.DispatchOperation> třídy poskytují operace klienta a služby operace runtime vlastnosti a kolekce rozšíření, v uvedeném pořadí. Je možné, ale potřebovat přístup k širší s vymezeným oborem runtime objekt z modulu runtime a naopak versa operace by být.  
  
> [!NOTE]
>  Informace o modulu runtime vlastnosti a typy rozšíření, které můžete použít k úpravě chování při spuštění klienta, najdete v článku [rozšíření klienti](../../../../docs/framework/wcf/extending/extending-clients.md). Informace o modulu runtime vlastnosti a typy rozšíření, které můžete použít k úpravě chování při spuštění služby odesílatele, naleznete v tématu [rozšíření dispečerů](../../../../docs/framework/wcf/extending/extending-dispatchers.md).  
  
 Většina uživatelů WCF nemají možnost zasahovat modulu runtime přímo. Místo toho používají programovací model konstrukce, jako koncové body, kontrakty, vazby, adresy a chování atributů na třídy nebo chování v konfiguračních souborech core. Tyto konstrukce tvoří *popis stromu*, což je kompletní specifikace sestavení modulu runtime pro podporu služby nebo klienta popsal stromu popis.  
  
 Existují čtyři druhy chování ve službě WCF:  
  
-   Služba chování (<xref:System.ServiceModel.Description.IServiceBehavior> typy) povolte vlastní nastavení v celé služby modulu runtime, včetně <xref:System.ServiceModel.ServiceHostBase>.  
  
-   Chování koncového bodu (<xref:System.ServiceModel.Description.IEndpointBehavior> typy) umožňují přizpůsobení koncových bodů služby a jejich přidružených <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> objekty.  
  
-   Smlouvy chování (<xref:System.ServiceModel.Description.IContractBehavior> typy) umožňují přizpůsobení i <xref:System.ServiceModel.Dispatcher.ClientRuntime> a <xref:System.ServiceModel.Dispatcher.DispatchRuntime> třídy v aplikacích pro klienta a služby, v uvedeném pořadí.  
  
-   Chování operace (<xref:System.ServiceModel.Description.IOperationBehavior> typy) povolte vlastní nastavení <xref:System.ServiceModel.Dispatcher.ClientOperation> a <xref:System.ServiceModel.Dispatcher.DispatchOperation> třídy opět na klienta a služby.  
  
 Můžete přidat tyto chování s různými objekty popis implementací vlastní atributy, pomocí konfiguračních souborů aplikace, nebo přímo jejich přidáním do kolekce chování na objekt příslušný popis. Musíte však přidat popis služby nebo objekt popis koncový bod služby před voláním <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> na <xref:System.ServiceModel.ServiceHost> nebo <xref:System.ServiceModel.ChannelFactory%601>.  
  
### <a name="behavior-scopes"></a>Chování obory  
 Existují čtyři typy chování, každá z nich odpovídá na konkrétní rozsah přístupu modulu runtime.  
  
#### <a name="service-behaviors"></a>Chování služby  
 Chování služby, které implementují <xref:System.ServiceModel.Description.IServiceBehavior>, představují hlavní mechanismus, pomocí kterého upravíte celé služby modulu runtime. Existují tři mechanismy pro přidání chování služby ke službě.  
  
1.  Pomocí atributu na třídu služby.  Když <xref:System.ServiceModel.ServiceHost> je vytvořen, <xref:System.ServiceModel.ServiceHost> implementace používá reflexi ke zjišťování sady atributů na typ služby. Pokud tyto atributy jsou implementace <xref:System.ServiceModel.Description.IServiceBehavior>, se přidají do kolekce chování na <xref:System.ServiceModel.Description.ServiceDescription>. To umožňuje tohoto chování k účasti v konstrukci čas spuštění služby.  
  
2.  Programové přidání chování k kolekce chování na <xref:System.ServiceModel.Description.ServiceDescription>. Můžete to provést s následujícími řádky kódu:  
  
    ```csharp
    ServiceHost host = new ServiceHost(/* Parameters */);  
    host.Description.Behaviors.Add(/* Service Behavior */);  
    ```  
  
3.  Implementace vlastního <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> , který rozšiřuje konfigurace. To umožňuje použití chování služby z konfiguračních souborů aplikace.  
  
 Příklady chování služby ve službě WCF <xref:System.ServiceModel.ServiceBehaviorAttribute> atribut, <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> chování.  
  
#### <a name="contract-behaviors"></a>Chování kontraktu  
 Chování, které implementují smlouvy <xref:System.ServiceModel.Description.IContractBehavior> rozhraní, se používají k rozšíření modulu runtime klient a služba napříč kontrakt.  
  
 Existují dva mechanismy pro přidání smlouvy chování kontrakt.  První mechanismus je vytvoření vlastního atributu se použije na rozhraní kontraktu. Když rozhraní kontraktu je předán buď <xref:System.ServiceModel.ServiceHost> nebo <xref:System.ServiceModel.ChannelFactory%601>, WCF prozkoumá atributy na rozhraní. Pokud jsou všechny atributy implementace <xref:System.ServiceModel.Description.IContractBehavior>, ty jsou přidány do kolekce chování na <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> vytvořené pro dané rozhraní.  
  
 Můžete také implementovat <xref:System.ServiceModel.Description.IContractBehaviorAttribute?displayProperty=nameWithType> na atribut smlouvy vlastní chování. V takovém případě chování je následujícím způsobem při použití:  
  
 •A rozhraní kontraktu. V takovém případě je chování aplikováno na všechny kontrakty daného typu v libovolný koncový bod a WCF ignoruje <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A?displayProperty=nameWithType> vlastnost.  
  
 Třída •A služby. V takovém případě je chování aplikováno pouze ke koncovým bodům smlouvy, což je hodnota <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> vlastnost.  
  
 Třída •A zpětného volání. V takovém případě je chování aplikováno na duplexní klienta endpoint a WCF ignoruje <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> vlastnost.  
  
 Druhý mechanismus je přidat do kolekce chování chování na <xref:System.ServiceModel.Description.ContractDescription>.  
  
 Příklady smlouvy chování ve službě WCF <xref:System.ServiceModel.DeliveryRequirementsAttribute?displayProperty=nameWithType> atribut. Další informace a příklad najdete v tématu v referenčním tématu.  
  
#### <a name="endpoint-behaviors"></a>Chování koncového bodu  
 Chování koncového bodu, které implementují <xref:System.ServiceModel.Description.IEndpointBehavior>, představují hlavní mechanismus, pomocí kterého upravíte celou službu nebo klienta běhu pro určitý koncový bod.  
  
 Existují dva mechanismy pro přidání chování koncového bodu služby.  
  
1.  Přidání chování k <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> vlastnost.  
  
2.  Implementovat vlastní <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> , který rozšiřuje konfigurace.  
  
 Další informace a příklad najdete v tématu v referenčním tématu.  
  
#### <a name="operation-behaviors"></a>Chování operace  
 Chování operace, které implementují <xref:System.ServiceModel.Description.IOperationBehavior> rozhraní, se používají k rozšíření modulu runtime klient a služba pro každou operaci.  
  
 Přidání chování operace operace dvěma způsoby. První mechanismus je vytvoření vlastního atributu se použije na metodu, která modeluje operaci. Při operaci přidání buď <xref:System.ServiceModel.ServiceHost> nebo <xref:System.ServiceModel.ChannelFactory>, WCF přidá všechny <xref:System.ServiceModel.Description.IOperationBehavior> atributy do kolekce chování na <xref:System.ServiceModel.Description.OperationDescription> vytvoří pro danou operaci.  
  
 Druhý mechanismus je přímo přidáním chování do kolekce chování na konstruovaný <xref:System.ServiceModel.Description.OperationDescription>.  
  
 Příklady chování operace ve službě WCF <xref:System.ServiceModel.OperationBehaviorAttribute> a <xref:System.ServiceModel.TransactionFlowAttribute>.  
  
 Další informace a příklad najdete v tématu v referenčním tématu.  
  
### <a name="using-configuration-to-create-behaviors"></a>Použití konfigurace k vytvoření chování  
 Služby a koncového bodu a kontrakt chování může za účelem je zadat v kódu nebo použití atributů pouze chování služby a koncového bodu můžete konfigurovat pomocí aplikace nebo Web konfigurační soubory. Vystavení Chování pomocí atributů umožňuje vývojářům k určení chování v době kompilace, kterou nelze přidat, odebrat nebo změnit za běhu. To je často vhodné pro chování, které jsou vždy vyžaduje pro správné fungování služby (například transakce související s parametry, které mají <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType> atributu). Vystavení Chování pomocí konfigurace umožňuje vývojářům ponechte specifikaci a konfiguraci tohoto chování na ty, kteří nasazují služby. To je vhodné pro chování, které jsou volitelné součásti nebo jiná konfigurace specifické pro nasazení, jako je například určuje, zda je přístupný metadat pro konfiguraci konkrétní autorizace pro službu nebo služby.  
  
> [!NOTE]
>  Můžete také použít chování, které podporují konfigurace k vynucování zásad společnosti aplikaci tak, že jejich vložením do konfiguračního souboru machine.config a omezovat se jenom ty položky. Popis a příklad najdete v tématu [jak: zámek dolů koncových bodů v podniku](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md).  
  
 Pokud chcete zpřístupnit chování pomocí konfigurace, musíte vytvořit vývojář odvozenou třídu <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> a pak zaregistrovat toto rozšíření s konfigurací.  
  
 Následující příklad kódu ukazuje jak <xref:System.ServiceModel.Description.IEndpointBehavior> implementuje <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>:  
  
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
  
 Aby systém konfigurace načíst vlastní <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>, musí být registrovaný jako rozšíření. Následující příklad kódu ukazuje konfigurační soubor pro předchozí chování koncového bodu:  
  
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
  
 Kde `Microsoft.WCF.Documentation.EndpointBehaviorMessageInspector` je typ rozšíření chování a `HostApplication` je název sestavení, do kterého byl zkompilován dané třídy.  
  
### <a name="evaluation-order"></a>Pořadí vyhodnocení  
 <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> a <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> jsou zodpovědného za sestavení modulu runtime z programovací model a popis. Chování, jak je uvedeno výše, přispívají k, které proces na služby, koncový bod, kontrakt a operace sestavení.  
  
 <xref:System.ServiceModel.ServiceHost> Platí chování v následujícím pořadí:  
  
1.  Služba  
  
2.  Kontrakt  
  
3.  Koncový bod  
  
4.  Operace  
  
 V rámci každé kolekci chování žádné pořadí je zaručena.  
  
 <xref:System.ServiceModel.ChannelFactory%601> Platí chování v následujícím pořadí:  
  
1.  Kontrakt  
  
2.  Koncový bod  
  
3.  Operace  
  
 V rámci žádné kolekce chování, žádné pořadí je zaručena.  
  
### <a name="adding-behaviors-programmatically"></a>Přidání chování prostřednictvím kódu programu  
 Vlastnosti <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> ve službě application nesmí upravit subsequent tak, aby <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType> metodu na <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>. Některé členy, jako jsou <xref:System.ServiceModel.ServiceHostBase.Credentials%2A?displayProperty=nameWithType> vlastnost a `AddServiceEndpoint` metody <xref:System.ServiceModel.ServiceHostBase> a <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>, vyvolat výjimku, pokud byl změněn za tímto bodem. Ostatní umožňují upravovat, ale výsledek není definován.  
  
 Podobně na straně klienta <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> hodnoty nesmí být změněny po volání <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> na <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>. <xref:System.ServiceModel.ChannelFactory.Credentials%2A?displayProperty=nameWithType> Vlastnost vyvolá výjimku, pokud byl změněn za tímto bodem, ale ostatní hodnoty Popis klienta můžete změnit bez chyb. Výsledek, ale není definován.  
  
 Ať už pro službu nebo klienta, se doporučuje, že upravíte popis před voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType>.  
  
### <a name="inheritance-rules-for-behavior-attributes"></a>Pravidla dědičnosti pro atributy chování  
 Všechny čtyři typy chování je možné naplnit s použitím atributů – chování služby a chování kontraktu. Protože atributy jsou definovány na spravované objekty a členy a spravované objekty a členy podporují dědičnost, je potřeba definovat, jak fungují chování atributů v rámci dědičnosti.  
  
 Na vysoké úrovni je pravidlo určitého oboru (například služby, smlouvy nebo operace), platí všechny atributy chování v hierarchii dědičnosti pro tento obor. Pokud existují dva atributy chování stejného typu, se používá jenom nejvíce odvozeným typem.  
  
#### <a name="service-behaviors"></a>Chování služby  
 Pro třídu dané služby se použijí všechny atributy chování služby v dané třídě a na nadřazených objektů této třídy. Pokud stejný typ atributu se použije na více místech v hierarchii dědičnosti, použije se nejvíce odvozeným typem.  
  
```csharp  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Multiple)]  
[AspNetCompatibilityRequirementsAttribute(  
    AspNetCompatibilityRequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]  
public class A { /* … */ }  
  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
public class B : A { /* … */}  
```  
  
 Například v předchozím případě služba B skončilo <xref:System.ServiceModel.InstanceContextMode> z <xref:System.ServiceModel.InstanceContextMode.Single>, <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> režim <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>a <xref:System.ServiceModel.ConcurrencyMode> z <xref:System.ServiceModel.ConcurrencyMode.Single>. <xref:System.ServiceModel.ConcurrencyMode> Je <xref:System.ServiceModel.ConcurrencyMode.Single>, protože <xref:System.ServiceModel.ServiceBehaviorAttribute> atributu ve službě B je na "více odvozené" než na službu A.  
  
#### <a name="contract-behaviors"></a>Chování kontraktu  
 Pro daný kontrakt všechny smlouvy atributy chování na rozhraní, která se použijí na nadřazené rozhraní. Pokud stejný typ atributu se použije na více místech v hierarchii dědičnosti, použije se nejvíce odvozeným typem.  
  
#### <a name="operation-behaviors"></a>Chování operace  
 Pokud danou operaci nepřepisuje k existující abstraktní nebo virtuální operace, použijte žádná pravidla dědičnosti.  
  
 Pokud operace přepsat existující operace a pak všechny operace atributy chování pro tuto operaci a v této operace se soubory nadřazené, se použijí.  Pokud stejný typ atributu se použije na více místech v hierarchii dědičnosti, použije se nejvíce odvozeným typem.
