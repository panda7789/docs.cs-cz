---
title: "Konfigurace a rozšíření modulu runtime s chováním"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: attaching extensions using behaviors [WCF]
ms.assetid: 149b99b6-6eb6-4f45-be22-c967279677d9
caps.latest.revision: "20"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: aab2d1d8c676a70b0fb4cfa80a16d52cd6f8b800
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="configuring-and-extending-the-runtime-with-behaviors"></a>Konfigurace a rozšíření modulu runtime s chováním
Chování umožňují upravit výchozí chování a přidat vlastní rozšíření, která kontrolují a ověření konfigurace služby nebo změňte chování za běhu v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] klienta a aplikaci služby. Toto téma popisuje chování rozhraní, jak pro jejich implementaci a jak je přidáte do popisu služby (v aplikaci služby) nebo koncový bod (v aplikaci klienta) prostřednictvím kódu programu, nebo v konfiguračním souboru. Další informace o používání poskytované systémem chování najdete v tématu [určení chování služby Run-Time](../../../../docs/framework/wcf/specifying-service-run-time-behavior.md) a [zadání běhového chování klienta](../../../../docs/framework/wcf/specifying-client-run-time-behavior.md).  
  
## <a name="behaviors"></a>Chování  
 Chování typy jsou přidány do služby nebo objekty popis koncový bod služby (na služba nebo klienta, v uvedeném pořadí) před tyto objekty používají [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] vytvořit modul runtime, který provede [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby nebo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta. Pokud tyto chování jsou volány během procesu vytváření modulu runtime jsou pak mít přístup k modulu runtime vlastnosti a metody, které upravují runtime sestavený kontrakt, vazeb a adresy.  
  
### <a name="behavior-methods"></a>Chování metod  
 Mají všechny chování `AddBindingParameters` metody `ApplyDispatchBehavior` metoda, `Validate` metoda a `ApplyClientBehavior` metoda s jednou výjimkou: protože <xref:System.ServiceModel.Description.IServiceBehavior> nelze provést v klientovi, neimplementuje `ApplyClientBehavior`.  
  
-   Použít `AddBindingParameters` metoda změnit nebo přidat vlastní objekty do kolekce, která vlastní vazby můžete přístup k jejich použití, když se modul runtime. Například to jak jsou určené požadavky na ochranu, která ovlivňují způsob je integrovaný kanál, ale nejsou známé vývojáře kanálu.  
  
-   Použití `Validate` metoda prozkoumat stromu popis a odpovídající objektu runtime tak, aby byl odpovídá některé sadu kritérií.  
  
-   Použití `ApplyDispatchBehavior` a `ApplyClientBehavior` metody prozkoumat popis stromu a upravit modulu runtime pro konkrétní obor na službu nebo klienta. Můžete také vložit také objekty rozšíření.  
  
    > [!NOTE]
    >  I když stromu popis najdete v těchto metod, je pro prozkoumání jenom. Pokud je upraven popis stromu, chování nedefinovaný.  
  
 Můžete upravit vlastnosti a přizpůsobení rozhraní, které můžete implementovat jsou přístupné prostřednictvím modulu runtime třídy klienta a služby. Typy služby jsou <xref:System.ServiceModel.Dispatcher.DispatchRuntime> a <xref:System.ServiceModel.Dispatcher.DispatchOperation> třídy. Typy klienta <xref:System.ServiceModel.Dispatcher.ClientRuntime> a <xref:System.ServiceModel.Dispatcher.ClientOperation> třídy. <xref:System.ServiceModel.Dispatcher.ClientRuntime> a <xref:System.ServiceModel.Dispatcher.DispatchRuntime> třídy jsou vstupní body rozšiřitelnosti pro přístup k vlastnosti úrovni klienta a služby modulu runtime a rozšíření kolekce. Podobně <xref:System.ServiceModel.Dispatcher.ClientOperation> a <xref:System.ServiceModel.Dispatcher.DispatchOperation> třídy vystavit provoz klienta a vlastnosti runtime operace služby a rozšíření kolekce, v uvedeném pořadí. Můžete, ale potřebovat přístup k širší vymezená runtime objektu z modulu runtime objekt a naopak naopak operace, pokud se.  
  
> [!NOTE]
>  Informace o vlastnosti runtime a typy rozšíření, které můžete použít k úpravě chování při spuštění klienta, najdete v části [rozšíření klienti](../../../../docs/framework/wcf/extending/extending-clients.md). Informace o vlastnosti runtime a typy rozšíření, které můžete použít k úpravě chování při spuštění služby odesílatele, najdete v části [rozšíření dispečerů](../../../../docs/framework/wcf/extending/extending-dispatchers.md).  
  
 Většina [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uživatelé není komunikovat s modulem runtime přímo; místo toho používají základní programovací model konstrukce jako koncové body, kontrakty, vazby, adresy a chování atributy třídy nebo chování v konfiguračních souborech. Tvoří tyto konstrukce *popis stromu*, což je specifikace dokončení pro vytváření modulu runtime pro podporu služby nebo klienta popsaného stromu popis.  
  
 Existují čtyři typy chování v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:  
  
-   Chování služby (<xref:System.ServiceModel.Description.IServiceBehavior> typy) povolte přizpůsobení celé služby modulu runtime včetně <xref:System.ServiceModel.ServiceHostBase>.  
  
-   Koncový bod chování (<xref:System.ServiceModel.Description.IEndpointBehavior> typy) povolte přizpůsobení koncové body služby a jejich přidružené <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> objekty.  
  
-   Sbalit chování (<xref:System.ServiceModel.Description.IContractBehavior> typy) povolte přizpůsobení i <xref:System.ServiceModel.Dispatcher.ClientRuntime> a <xref:System.ServiceModel.Dispatcher.DispatchRuntime> třídy v aplikacích pro klienta a služby v uvedeném pořadí.  
  
-   Operace chování (<xref:System.ServiceModel.Description.IOperationBehavior> typy) povolit možnosti vlastního nastavení <xref:System.ServiceModel.Dispatcher.ClientOperation> a <xref:System.ServiceModel.Dispatcher.DispatchOperation> třídy, znovu na klientovi a služby.  
  
 Tyto chování můžete přidat k různým objektům popis implementací vlastní atributy, pomocí konfigurační soubory aplikace, nebo přímo jejich přidáním do kolekce chování na příslušné popis objektu. Musí však být přidán do popis služby nebo objekt popis koncový bod služby před voláním <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> na <xref:System.ServiceModel.ServiceHost> nebo <xref:System.ServiceModel.ChannelFactory%601>.  
  
### <a name="behavior-scopes"></a>Chování oborů  
 Existují čtyři typy chování, z nichž každý odpovídá na konkrétní rozsah přístupu modulu runtime.  
  
#### <a name="service-behaviors"></a>Chování služby  
 Chování služby, které implementují třídu <xref:System.ServiceModel.Description.IServiceBehavior>, jsou primární mechanismus, pomocí kterého upravíte celé služby modulu runtime. Existují tři mechanismy pro přidání chování služby do služby.  
  
1.  Pomocí atributu na třídě služby.  Když <xref:System.ServiceModel.ServiceHost> vytvořen, <xref:System.ServiceModel.ServiceHost> implementace používá reflexe zjistit sadu atributů pro typ služby. Pokud některá z těchto atributů implementace <xref:System.ServiceModel.Description.IServiceBehavior>, budou přidány do kolekce chování na <xref:System.ServiceModel.Description.ServiceDescription>. To umožňuje tyto chování k účasti ve vytváření běh služby.  
  
2.  Programové přidání chování ke kolekci chování na <xref:System.ServiceModel.Description.ServiceDescription>. Můžete to provést pomocí následující řádky kódu:  
  
    ```  
    ServiceHost host = new ServiceHost(/* Parameters */);  
    host.Description.Behaviors.Add(/* Service Behavior */);  
    ```  
  
3.  Implementace vlastní <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> který rozšiřuje konfigurace. To umožňuje použití chování služby z konfigurační soubory aplikace.  
  
 Příklady chování služby v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zahrnují <xref:System.ServiceModel.ServiceBehaviorAttribute> atribut, <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> chování.  
  
#### <a name="contract-behaviors"></a>Chování kontraktu  
 Sbalit chování, které implementují třídu <xref:System.ServiceModel.Description.IContractBehavior> rozhraní, se používají k rozšíření klient a služba runtime napříč kontraktu.  
  
 Pro přidání smlouvy chování do kontraktu dvěma způsoby.  První mechanismus je vytvoření vlastních atributů, který se má použít na rozhraní kontraktu. Když rozhraní kontraktu je předán buď <xref:System.ServiceModel.ServiceHost> nebo <xref:System.ServiceModel.ChannelFactory%601>, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] atributy na rozhraní. Pokud jsou všechny atributy implementace <xref:System.ServiceModel.Description.IContractBehavior>, ty jsou přidány do kolekce chování na <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> vytvořili pro toto rozhraní.  
  
 Můžete taky implementovat <xref:System.ServiceModel.Description.IContractBehaviorAttribute?displayProperty=nameWithType> na atribut chování vlastní kontrakt. V takovém případě chování je následující při použití:  
  
 •A rozhraní kontraktu. V takovém případě chování platí pro všechny smlouvy daného typu v žádný koncový bod a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ignoruje hodnotu <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A?displayProperty=nameWithType> vlastnost.  
  
 Třída •A služby. V takovém případě chování platí pouze pro koncové body smlouvy, což je hodnota <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> vlastnost.  
  
 Třída •A zpětného volání. V takovém případě se použije chování koncovému bodu duplexní klienta a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ignoruje hodnotu <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> vlastnost.  
  
 Druhý mechanismus je přidat do kolekce chování chování na <xref:System.ServiceModel.Description.ContractDescription>.  
  
 Příklady kontrakt chování v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zahrnují <xref:System.ServiceModel.DeliveryRequirementsAttribute?displayProperty=nameWithType> atribut. Další informace a příklady naleznete v tématu referenční téma.  
  
#### <a name="endpoint-behaviors"></a>Koncový bod chování  
 Koncový bod chování, které implementují třídu <xref:System.ServiceModel.Description.IEndpointBehavior>, jsou primární mechanismus, pomocí kterého upravíte celé služby nebo dobu spuštění pro koncový bod konkrétní klienta.  
  
 Pro přidání chování koncový bod služby dvěma způsoby.  
  
1.  Přidejte požadované chování, <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> vlastnost.  
  
2.  Implementovat vlastní <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> který rozšiřuje konfigurace.  
  
 Další informace a příklady naleznete v tématu referenční téma.  
  
#### <a name="operation-behaviors"></a>Operace chování  
 Operace chování, které implementují třídu <xref:System.ServiceModel.Description.IOperationBehavior> rozhraní, se používají k rozšíření klient a služba runtime pro každou operaci.  
  
 Pro přidání operace chování pro operaci dvěma způsoby. První mechanismus je vytvoření vlastních atributů, který se má použít na metodu, která modelů operaci. Když se operace přidá do buď <xref:System.ServiceModel.ServiceHost> nebo <xref:System.ServiceModel.ChannelFactory>, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] přidá všechny <xref:System.ServiceModel.Description.IOperationBehavior> atributy ke kolekci chování na <xref:System.ServiceModel.Description.OperationDescription> vytvořené pro tuto operaci.  
  
 Druhý mechanismus je přímo přidáním chování ke kolekci chování na vytvořený <xref:System.ServiceModel.Description.OperationDescription>.  
  
 Příklady chování operace v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zahrnují <xref:System.ServiceModel.OperationBehaviorAttribute> a <xref:System.ServiceModel.TransactionFlowAttribute>.  
  
 Další informace a příklady naleznete v tématu referenční téma.  
  
### <a name="using-configuration-to-create-behaviors"></a>Použití konfigurace k vytvoření chování  
 Služby a koncového bodu a kontrakt chování může pomocí navržený tak, aby se zadaný v kódu nebo pomocí atributů; pomocí aplikace nebo webové konfigurační soubory můžete nakonfigurovat pouze chování služby a koncového bodu. Vystavení Chování pomocí atributů umožňuje vývojářům umožňuje zadat chování během kompilace, který nelze přidat, odebrat nebo změnit za běhu. Obvykle je vhodné pro chování, které jsou vždy vyžaduje pro správné fungování služby (například související transakci parametry, které chcete <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType> atributu). Vystavení Chování pomocí konfigurace umožňuje vývojářům zůstat specifikaci a konfiguraci těchto chování uživatelů, kteří nasazení služby. To je vhodné pro chování, které jsou volitelné součásti nebo jiné konfigurace specifické pro nasazení, jako je například, jestli je vystaven metadata pro službu nebo konkrétní autorizace konfigurace pro službu.  
  
> [!NOTE]
>  Můžete také použít chování, které podporují konfigurace k vynucování zásad společnosti aplikace podle jejich vložením do konfiguračního souboru machine.config a zamykání tyto položky. Popis a příklad najdete v tématu [postup: uzamčení mimo provoz koncovými body v podnikové síti](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md).  
  
 Ke zveřejnění chování pomocí konfigurace, musí vývojář vytvořit odvozené třídu <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> a potom proveďte registraci rozšíření s konfigurací.  
  
 Následující příklad kódu ukazuje jak <xref:System.ServiceModel.Description.IEndpointBehavior> implementuje <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>:  
  
```  
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
  
 Aby konfiguračního systému se načíst vlastní <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>, musí být zaregistrovaný jako rozšíření. Následující příklad kódu ukazuje konfiguračního souboru pro předchozí chování koncového bodu:  
  
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
  
 Kde `Microsoft.WCF.Documentation.EndpointBehaviorMessageInspector` je typ rozšíření chování a `HostApplication` je název sestavení, do které byl zkompilován třídy.  
  
### <a name="evaluation-order"></a>Pořadí vyhodnocení  
 <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> a <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> jsou zodpovědného za sestavení modulu runtime z programovací model a popis. Chování, jak se popisuje výš, přispívat k, které proces na služby, koncový bod, kontrakt a operace sestavení.  
  
 <xref:System.ServiceModel.ServiceHost> Platí chování v následujícím pořadí:  
  
1.  Služba  
  
2.  Kontrakt  
  
3.  Koncový bod  
  
4.  Operace  
  
 V rámci shromažďování těchto chování žádné pořadí záruku, že se.  
  
 <xref:System.ServiceModel.ChannelFactory%601> Platí chování v následujícím pořadí:  
  
1.  Kontrakt  
  
2.  Koncový bod  
  
3.  Operace  
  
 V rámci jakoukoli kolekci chování, žádné pořadí záruku, že se.  
  
### <a name="adding-behaviors-programmatically"></a>Přidání chování prostřednictvím kódu programu  
 Vlastnosti <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> ve službě aplikace nesmí být upravit subsequent tak, aby <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType> metodu <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>. Některé členy, jako <xref:System.ServiceModel.ServiceHostBase.Credentials%2A?displayProperty=nameWithType> vlastnost a `AddServiceEndpoint` metody na <xref:System.ServiceModel.ServiceHostBase> a <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>, způsobí výjimku, pokud se změní za tento bod. Ostatní umožňují je upravovat, ale výsledek není definován.  
  
 Podobně na straně klienta <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> po zavolání nesmí měnit hodnoty <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> na <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>. <xref:System.ServiceModel.ChannelFactory.Credentials%2A?displayProperty=nameWithType> Vlastnost vyvolá výjimku, pokud se změní za tento bod, ale ostatní hodnoty klienta popis můžete změnit bez chyby. Výsledek, ale není definován.  
  
 Zda se služba nebo klienta, se doporučuje, když je upravit popis před voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType>.  
  
### <a name="inheritance-rules-for-behavior-attributes"></a>Dědičnost pravidla pro atributy chování  
 Všechny čtyři typy chování je možné importovat pomocí atributů – chování služby a chování kontrakt. Protože atributy jsou definovány na spravované objekty a členy a spravované objekty a členy podporují dědičnosti, je nutné definovat, jak fungují atributy chování v kontextu dědičnosti.  
  
 Na vysoké úrovni je pravidlo pro konkrétní obor (například služby kontrakt operaci nebo), platí všechny atributy chování v hierarchii dědičnosti pro tento obor. Pokud existují dva atributy chování stejného typu, použije se pouze typu odvozeného většinu.  
  
#### <a name="service-behaviors"></a>Chování služby  
 Pro třídu uvedená služba všechny atributy chování služby na této třídě a na nadřazených tříd, platí. Pokud stejný typ atributu se použije na více místech v hierarchii dědičnosti, použije se většinou odvozených typů.  
  
```  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Multiple)]  
[AspNetCompatibilityRequirementsAttribute(  
    AspNetCompatibilityRequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]  
public class A { /* … */ }  
  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
public class B : A { /* … */}  
```  
  
 Například v předchozím případě službu B bude mít <xref:System.ServiceModel.InstanceContextMode> z <xref:System.ServiceModel.InstanceContextMode.Single>, <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> režim <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>a <xref:System.ServiceModel.ConcurrencyMode> z <xref:System.ServiceModel.ConcurrencyMode.Single>. <xref:System.ServiceModel.ConcurrencyMode> Je <xref:System.ServiceModel.ConcurrencyMode.Single>, protože <xref:System.ServiceModel.ServiceBehaviorAttribute> atribut služby B je na "více odvozené" než na služby A.  
  
#### <a name="contract-behaviors"></a>Chování kontraktu  
 Pro danou zakázku všechny smlouvy atributy chování na které rozhraní a jsou použity na nadřazených položek tohoto rozhraní. Pokud stejný typ atributu se použije na více místech v hierarchii dědičnosti, použije se většinou odvozených typů.  
  
#### <a name="operation-behaviors"></a>Operace chování  
 Pokud danou operaci nepřepisuje existující abstraktní nebo virtuální operace, žádná pravidla dědičnosti platit.  
  
 Pokud operace přepsat existující operace, pak všechny atributy chování operaci na tuto operaci a nadřazených položek této operace, se použijí.  Pokud stejný typ atributu se použije na více místech v hierarchii dědičnosti, použije se většinou odvozených typů.
