---
title: Řešení potíží – korelace
ms.date: 03/30/2017
ms.assetid: 98003875-233d-4512-a688-4b2a1b0b5371
ms.openlocfilehash: fecfaf7374823bb19a4ad3d7f6cb2dbbdf139703
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48793731"
---
# <a name="troubleshooting-correlation"></a>Řešení potíží – korelace
Korelace se používá k propojení zprávy služby pracovního postupu k sobě navzájem a pro instanci pracovního postupu správný, ale pokud není správně nakonfigurována, nebude přijímat zprávy a aplikace nebude fungovat správně. Toto téma obsahuje základní informace o několik metod pro řešení potíží s korelace a také uvádí některé běžné problémy, které může dojít, když použijete korelace.

## <a name="handle-the-unknownmessagereceived-event"></a>Zpracování události UnknownMessageReceived
 <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> Události dojde, když je přijata Neznámá zpráva podle služby, včetně zpráv, které nemůže být přiřazeny k existující instanci. V místním prostředí služby mohou být zpracovány tuto událost v hostitelské aplikace.

```csharp
host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)
{
    Console.WriteLine("Unknown Message Received:");
    Console.WriteLine(e.Message);
};
```

 Pro hostované webové služby, může být zpracována tato událost odvození třídy z <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> a přepsáním <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A>.

```csharp
class CustomFactory : WorkflowServiceHostFactory
{
    protected override WorkflowServiceHost CreateWorkflowServiceHost(Activity activity, Uri[] baseAddresses)
    {
        // Create the WorkflowServiceHost.
        WorkflowServiceHost host = new WorkflowServiceHost(activity, baseAddresses);

        // Handle the UnknownMessageReceived event.
        host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)
        {
            Console.WriteLine("Unknown Message Received:");
            Console.WriteLine(e.Message);
        };

        return host;
    }
}
```

 Tato vlastní <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> lze zadat v `svc` souboru služby.

```
<% @ServiceHost Language="C#" Service="OrderServiceWorkflow" Factory="CustomFactory" %>
```

 Po vyvolání Tato obslužná rutina zprávy lze načíst s použitím <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> vlastnost <xref:System.ServiceModel.UnknownMessageReceivedEventArgs>a bude vypadat podobně jako následující zpráva.

```Output
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header>
    <To s:mustUnderstand="1" xmlns="http://schemas.microsoft.com/ws/2005/05/addressing/none">http://localhost:8080/OrderService</To>
    <Action s:mustUnderstand="1" xmlns="http://schemas.microsoft.com/ws/2005/05/addressing/none">http://tempuri.org/IService/AddItem</Action>
  </s:Header>
  <s:Body>
    <AddItem xmlns="http://tempuri.org/">
      <Item>Books</Item>
    </AddItem>
  </s:Body>
</s:Envelope>
```

 Kontrola zprávy odeslána <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> obslužná rutina může poskytnout příčiny o Proč není korelaci zprávy do instance služby pracovního postupu.

## <a name="use-tracking-to-monitor-the-progress-of-the-workflow"></a>Používání sledování můžete sledovat průběh pracovního postupu
 Sledování poskytuje způsob, jak monitorovat průběh pracovního postupu. Ve výchozím nastavení jsou vydávány sledování záznamů pro pracovní postup události životního cyklu, události životního cyklu aktivit, šíření chyb a záložku obnovení. Kromě toho může být vygenerována vlastní záznamy sledování vlastních aktivit. Při řešení potíží – korelace, jsou zvláště užitečná sledování záznamů, záložku obnovení záznamů a chyby šíření hodnoty záznamů aktivit. Aktivita sledování záznamů je možné určit aktuální průběh pracovního postupu a může pomoct identifikovat, které zasílání zpráv aktivity je aktuálně čeká na zprávy. Záložku obnovení záznamů jsou užitečné, protože označují, že byla přijata zpráva tímto pracovním postupem a chyby šíření záznamy obsahují záznam o všechny chyby, v pracovním postupu. Chcete-li povolit sledování, zadejte požadovaný <xref:System.Activities.Tracking.TrackingParticipant> v <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> z <xref:System.ServiceModel.Activities.WorkflowServiceHost>. V následujícím příkladu `ConsoleTrackingParticipant` (z [vlastní sledování](../../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) ukázkové) je nakonfigurován s použitím výchozí profil sledování tracking profile.

```csharp
host.WorkflowExtensions.Add(new ConsoleTrackingParticipant());
```

 Sledování účastník, jako je například ConsoleTrackingParticipant je užitečné pro pracovní postup v místním prostředí služby, které mají okno konzoly. Pro hostované webové služby, třeba použít účastníkem sledování, která zaznamenává informace o sledování do odolného úložiště, jako je například předdefinované <xref:System.Activities.Tracking.EtwTrackingParticipant>, nebo vlastní sledování účastník, který protokoluje informace do souboru.

 Další informace o sledování a konfiguraci sledování pro služby hostované webového pracovního procesu, naleznete v tématu [pracovního postupu pro sledování a trasování](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md), [konfigurace sledování pracovního postupu](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)a [ Sledování &#91;ukázky WF&#93; ](../../../../docs/framework/windows-workflow-foundation/samples/tracking.md) ukázky.

## <a name="use-wcf-tracing"></a>Použít trasování WCF
 Trasování WCF obsahuje trasování toku zpráv do a ze služby pracovních postupů. Tyto informace trasování jsou užitečné při řešení problémů korelace, zejména u korelace na základě obsahu. Povolení trasování, určete naslouchací procesy požadované trasování v `system.diagnostics` část `web.config` souboru, pokud služba pracovního postupu je Web hostovaný, nebo `app.config` souboru, pokud je služba pracovního postupu v místním prostředí. Chcete-li zahrnout obsah zprávy do souboru trasování, zadejte `true` pro `logEntireMessage` v `messageLogging` element v `diagnostics` část `system.serviceModel`. V následujícím příkladu je nakonfigurované trasovací informace, včetně obsahu zpráv, má být zapsán do souboru s názvem `service.svclog`.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.diagnostics>
    <sources>
      <source name="System.ServiceModel" switchValue="Information" propagateActivity="true">
        <listeners>
          <add name="corr"/>
        </listeners>
      </source>
      <source name="System.ServiceModel.MessageLogging">
        <listeners>
          <add name="corr"/>
        </listeners>
      </source>
    </sources>

    <sharedListeners>
      <add name="corr" type="System.Diagnostics.XmlWriterTraceListener" initializeData="c:\logs\service.svclog">
      </add>
    </sharedListeners>
  </system.diagnostics>

  <system.serviceModel>
    <diagnostics>
      <messageLogging logEntireMessage="true" logMalformedMessages="false"
         logMessagesAtServiceLevel="false" logMessagesAtTransportLevel="true" maxSizeOfMessageToLog="2147483647">
      </messageLogging>
    </diagnostics>
  </system.serviceModel>
</configuration>
```

 Chcete-li zobrazit trasovací informace, které je součástí `service.svclog`, [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) se používá. To je zvlášť užitečné při řešení potíží – korelace na základě obsahu problémy, protože můžete zobrazit obsah zprávy a podívejte se, právě co je předávána a určuje, zda odpovídá <xref:System.ServiceModel.CorrelationQuery> pro korelaci založené na obsahu. Další informace o trasování WCF najdete v tématu [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), [Konfigurace trasování](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md), a [pomocí trasování řešení potíží s aplikací](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).

## <a name="common-context-exchange-correlation-issues"></a>Běžné problémy korelace místní Exchange
 Určité typy korelace vyžadovat, že se konkrétní typ vazby používá pro korelaci fungovat správně. Mezi příklady patří korelace požadavku a odpovědi, která vyžaduje Obousměrná vazba například <xref:System.ServiceModel.BasicHttpBinding>a korelace kontextové výměny, který vyžaduje základě kontextu vazby, jako <xref:System.ServiceModel.BasicHttpContextBinding>. Většina vazby podporují obousměrné operace, nejedná se o běžný problém pro korelace požadavku a odpovědi, ale jenom na několik na základě kontextu vazby, včetně <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, a <xref:System.ServiceModel.NetTcpContextBinding>. Jednu z těchto vazeb se nepoužívá, počáteční volání služby pracovního postupu bude úspěšné, ale následná volání nebudou úspěšná následujícím <xref:System.ServiceModel.FaultException>.

```Output
There is no context attached to the incoming message for the service
and the current operation is not marked with "CanCreateInstance = true".
In order to communicate with this service check whether the incoming binding
supports the context protocol and has a valid context initialized.
```

 Informace o kontextu, který slouží pro korelaci kontextu může být vrácen <xref:System.ServiceModel.Activities.SendReply> k <xref:System.ServiceModel.Activities.Receive> aktivitu, která inicializuje korelaci kontextu při použití obousměrný operaci, nebo je možné zadat tak volající Pokud je operace jednosměrná. Pokud není kontext odesílaných volající nebo vrácený služby pracovního postupu a pak stejné <xref:System.ServiceModel.FaultException> popsané dříve se vrátí, pokud je vyvolána následná operace.

## <a name="common-request-reply-correlation-issues"></a>Běžné problémy korelace požadavku a odpovědi
 Korelace požadavku a odpovědi se používá s <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pár pro implementaci obousměrný operace ve službě pracovních postupů a se <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> pár, který vyvolá obousměrný operaci na jiném webu Služba. Při vyvolání obousměrný operace ve službě WCF, služba může být buď tradiční služba WCF imperativní založený na kódu nebo to může být služba pracovního postupu. Použití korelace požadavku a odpovědi Obousměrná vazba musí být použita, jako například <xref:System.ServiceModel.BasicHttpBinding>, a operace musí být obousměrné.

 Pokud má služba pracovního postupu obousměrný operace v paralelní nebo překrývající se <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> nebo <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> páry a potom implicitní korelace postupovat při správě poskytované <xref:System.ServiceModel.Activities.WorkflowServiceHost>nemusí být dostatečné, zejména ve scénářích vysoké zatížení, a nemusí správně směrovat zprávy. K tomuto problému zabránit, doporučujeme vám, že je vždy explicitně zadat <xref:System.ServiceModel.Activities.CorrelationHandle> při použití korelace požadavku a odpovědi. Při použití **SendAndReceiveReply** a **ReceiveAndSendReply** šablony z části zasílání zpráv **nástrojů** v Návrháři pracovních postupů <xref:System.ServiceModel.Activities.CorrelationHandle> explicitně nakonfigurované ve výchozím nastavení. Při vytváření pracovního postupu pomocí kódu, <xref:System.ServiceModel.Activities.CorrelationHandle> je zadán v <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> sady první aktivity v páru. V následujícím příkladu <xref:System.ServiceModel.Activities.Receive> aktivita je konfigurována s explicitní <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> zadané v poli <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.

```csharp
Variable<CorrelationHandle> RRHandle = new Variable<CorrelationHandle>();

Receive StartOrder = new Receive
{
    CanCreateInstance = true,
    ServiceContractName = OrderContractName,
    OperationName = "StartOrder",
    CorrelationInitializers =
    {
        new RequestReplyCorrelationInitializer
        {
            CorrelationHandle = RRHandle
        }
    }
};

SendReply ReplyToStartOrder = new SendReply
{
    Request = StartOrder,
    Content = ... // Contains the return value, if any.
};

// Construct a workflow using StartOrder and ReplyToStartOrder.
```

 Mezi není povolena trvalost <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pár nebo <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> pár. No-persist zóny se vytvoří s platností dokončením obě aktivity. Pokud aktivita, jako je aktivita zpoždění, je v této zóně no-persist a způsobí, že pracovní postup na nečinnost, nezachovají pracovní postup i v případě, pokud je hostitel konfigurován k uchování pracovních postupů, kdy se stanou nečinné. Pokud aktivity, jako je aktivita zachovat, se pokusí explicitně zachovat v zóně trvalého Ne, je závažnou výjimku vyvolána, přerušení pracovního postupu a <xref:System.ServiceModel.FaultException> je vrátit zpět volajícímu. Zpráva kritické výjimky "System.InvalidOperationException: uchování aktivity nelze zahrnout do dočasných bloků.". Tato výjimka není vrátit zpět volajícímu, ale můžete pozorovat, pokud je povoleno sledování. Zpráva pro <xref:System.ServiceModel.FaultException> vrátit zpět volajícímu je "operaci nelze provést, protože dokončení instance pracovního postupu"5836145b 7da2 - 49 d 0-a052-a49162adeab6"".

 Další informace o korelace požadavku a odpovědi najdete v tématu [Request-Reply](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md).

## <a name="common-content-correlation-issues"></a>Běžné problémy obsahu korelace
 Korelace na základě obsahu se používá v případě služby pracovního postupu přijímá více zpráv a část dat ve výměně zpráv určuje požadovanou instanci. Korelace na základě obsahu používá tato data ve zprávě, jako je číslo nebo pořadí ID zákazníka, pro směrování zpráv do instance pracovního postupu správné. Tato část popisuje několik běžných problémů, které mohou nastat při používání korelace na základě obsahu.

### <a name="ensure-the-identifying-data-is-unique"></a>Ujistěte se, že je jedinečné identifikační údaje
 Data, která se používá k identifikaci instance se po zahašování použije na klíč korelace. Chcete-li zaručit, že data, která slouží pro korelaci je jedinečný, jinak může dojít a způsobit zpráv se nesprávně směrovanými kolizí v klíči hash musí věnovat pozornost. Například korelace založen pouze na název zákazníka může způsobit ke kolizi, protože může být více zákazníků, kteří mají stejný název. Dvojtečka (:) by neměl používá jako součást data, která slouží ke sladění zprávy, protože se už používá pro vymezení klíč a hodnotu, která tvoří řetězec, který se následně mají hodnotu hash dotazu zprávu. Pokud trvalost, se používá, ujistěte se, že aktuální identifikační data nebyla použita dříve drženého instancí. Dočasně zakážete trvalost může pomoci identifikovat problém. Trasování WCF slouží k zobrazení počítané korelace klíč a je užitečné pro ladění tento druh problému.

### <a name="race-conditions"></a>Konflikty časování
 Existuje malé mezera v době mezi službu přijetí zprávy a korelace ve skutečnosti inicializovaný, během které zpracování zprávy budou ignorovány. Pokud služby pracovního postupu inicializuje korelaci založené na obsahu s využitím dat předávaných od klienta přes jednocestnou operaci a odesílá okamžité zpracování zpráv, ignorují se tyto zprávy během tohoto intervalu. Toho se lze vyvarovat pomocí obousměrné operace inicializace korelace, nebo pomocí <xref:System.ServiceModel.Activities.TransactedReceiveScope>.

### <a name="correlation-query-issues"></a>Korelace dotazů problémy
 Korelace dotazů se používají k určení, jaká data ve zprávě se používá ke korelaci zprávy. Tato data je určen pomocí dotazu XPath. Pokud zprávy do služby nejsou distribuovanou i v případě, že všechno, co se zobrazí správný, je jednou z možných strategií pro řešení potíží s zadat hodnotu literálu, který se shoduje s hodnotou data zprávy místo dotaz XPath. Pokud chcete zadat hodnotu literálu, použijte `string` funkce. V následujícím příkladu <xref:System.ServiceModel.MessageQuerySet> je nakonfigurován na použití hodnota literálu `11445` pro `OrderId` a dotaz XPath je označené jako komentář.

```csharp
MessageQuerySet = new MessageQuerySet
{
    {
        "OrderId",
        //new XPathMessageQuery("sm:body()/tempuri:StartOrderResponse/tempuri:OrderId")
        new XPathMessageQuery("string('11445')")
    }
}
```

 Pokud se dotaz XPath je správně nakonfigurovaná tak, že nebudou načtena žádná data pro korelace, vrátí se chyba s následující zprávou: "korelační dotaz vrátil prázdnou sadu výsledků. Ujistěte se, že jsou správně nakonfigurované korelačních dotazů pro koncový bod." Jeden rychlý způsob, jak toto řešení je dotaz XPath nahraďte hodnotu literálu jak je popsáno v předchozí části. Tomuto problému může dojít, pokud pomocí Tvůrce dotazů XPath v **přidat inicializátory korelace** nebo **definice vlastnosti CorrelatesOn** dialogová okna a služba pracovního postupu používá zprávy smlouvy. V následujícím příkladu je definován třídou kontraktu zprávy.

```csharp
[MessageContract]
public class AddItemMessage
{
    [MessageHeader]
    public string CartId;

    [MessageBodyMember]
    public string Item;
}
```

 Používá tento kontrakt zprávy <xref:System.ServiceModel.Activities.Receive> aktivity v pracovním postupu. `CartId` v záhlaví zprávy slouží ke sladění zpráva, která má správné instanci. Pokud dotaz XPath, který načte `CartId` je vytvořený pomocí dialogových oken korelace v Návrháři postupu provádění následujících nesprávnou XPath dotaz.

```
sm:body()/xg0:AddItemMessage/xg0:CartId
```

 Tento dotaz XPath by byly správné Pokud <xref:System.ServiceModel.Activities.Receive> aktivita používá parametry pro data, ale protože ho používá zprávy smlouvy je nesprávný. Následující dotaz XPath je správný výraz XPath dotaz pro načtení `CartId` z hlavičky.

```
sm:header()/tempuri:CartId
```

To můžete potvrdit prozkoumáním tělo zprávy.

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header>
    <Action s:mustUnderstand="1" xmlns="http://schemas.microsoft.com/ws/2005/05/addressing/none">http://tempuri.org/IService/AddItem</Action>
    <h:CartId xmlns:h="http://tempuri.org/">80c95b41-c98d-4660-a6c1-99412206e54c</h:CartId>
  </s:Header>
  <s:Body>
    <AddItemMessage xmlns="http://tempuri.org/">
      <Item>Books</Item>
    </AddItemMessage>
  </s:Body>
</s:Envelope>
```

Následující příklad ukazuje <xref:System.ServiceModel.Activities.Receive> aktivity, které jsou nakonfigurované pro `AddItem` operaci, která používá předchozí kontraktu zprávy přijímat data. Dotaz XPath je správně nakonfigurován.

```xaml
<Receive CorrelatesWith="[CCHandle] OperationName="AddItem" ServiceContractName="p:IService">
  <Receive.CorrelatesOn>
    <XPathMessageQuery x:Key="key1">
      <XPathMessageQuery.Namespaces>
        <ssx:XPathMessageContextMarkup>
          <x:String x:Key="xg0">http://schemas.datacontract.org/2004/07/MessageContractWFService</x:String>
        </ssx:XPathMessageContextMarkup>
      </XPathMessageQuery.Namespaces>sm:header()/tempuri:CartId</XPathMessageQuery>
  </Receive.CorrelatesOn>
  <ReceiveMessageContent DeclaredMessageType="m:AddItemMessage">
    <p1:OutArgument x:TypeArguments="m:AddItemMessage">[AddItemMessage]</p1:OutArgument>
  </ReceiveMessageContent>
</Receive>
```
