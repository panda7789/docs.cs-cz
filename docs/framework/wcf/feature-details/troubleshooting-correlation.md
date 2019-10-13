---
title: Řešení potíží s korelacemi
ms.date: 03/30/2017
ms.assetid: 98003875-233d-4512-a688-4b2a1b0b5371
ms.openlocfilehash: d4b7b4ecd724416256cf0b2499d7180200f4e75c
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291561"
---
# <a name="troubleshooting-correlation"></a>Řešení potíží s korelacemi
Korelace se používá ke vzájemnému propojení zpráv služby pracovních postupů a ke správné instanci pracovního postupu, ale pokud není správně nakonfigurovaná, zprávy se neobdrží a aplikace nebudou fungovat správně. V tomto tématu najdete přehled několika metod pro řešení problémů s korelací a také uvádí některé běžné problémy, které mohou nastat při použití korelace.

## <a name="handle-the-unknownmessagereceived-event"></a>Zpracování události UnknownMessageReceived
 Událost <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> nastane, když služba obdrží neznámou zprávu, včetně zpráv, které nelze korelovat s existující instancí. V případě samoobslužných služeb je možné tuto událost zpracovat v hostitelské aplikaci.

```csharp
host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)
{
    Console.WriteLine("Unknown Message Received:");
    Console.WriteLine(e.Message);
};
```

 U služeb hostovaných na webu lze tuto událost zpracovat odvozením třídy z <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> a přepsáním <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A>.

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

 Tento vlastní <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> lze potom zadat v souboru `svc` pro službu.

```
<% @ServiceHost Language="C#" Service="OrderServiceWorkflow" Factory="CustomFactory" %>
```

 Při vyvolání této obslužné rutiny lze zprávu načíst pomocí vlastnosti <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> <xref:System.ServiceModel.UnknownMessageReceivedEventArgs> a bude vypadat podobně jako následující zpráva.

```xml
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

 Kontrola zpráv odeslaných do obslužné rutiny <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> může poskytnout informace o tom, proč se zpráva nekoreluje s instancí služby pracovního postupu.

## <a name="use-tracking-to-monitor-the-progress-of-the-workflow"></a>Sledování průběhu pracovního postupu pomocí sledování
 Sledování poskytuje způsob, jak monitorovat průběh pracovního postupu. Ve výchozím nastavení jsou záznamy sledování vydávány pro události životního cyklu pracovního cyklu, události životního cyklu aktivity, šíření chyb a opětovné pokračování záložek. Vlastní záznamy sledování je navíc možné vysílat vlastními aktivitami. Při řešení potíží s korelacemi, záznamy sledování aktivity, pokračování záznamů a záznamy o šíření chyb jsou nejužitečnější. Záznamy sledování aktivit se dají použít k určení aktuálního průběhu pracovního postupu a můžou vám pomůžou určit, které aktivity zasílání zpráv aktuálně čekají na zprávy. Záznamy pokračování v záložek jsou užitečné, protože označují, že pracovní postup přijal zprávu, a záznamy o šíření chyb poskytují záznam všech chyb v pracovním postupu. Chcete-li povolit sledování, zadejte požadované <xref:System.Activities.Tracking.TrackingParticipant> v <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> <xref:System.ServiceModel.Activities.WorkflowServiceHost>. V následujícím příkladu je `ConsoleTrackingParticipant` (z [vlastní ukázky sledování](../../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) ) nakonfigurovaná pomocí výchozího profilu sledování.

```csharp
host.WorkflowExtensions.Add(new ConsoleTrackingParticipant());
```

 Sledování účastníka, jako je ConsoleTrackingParticipant, je užitečné pro samoobslužné služby pracovních postupů, které mají okno konzoly. V případě služby hostované na webu by se měla použít sledování účastníka, který zaznamenává informace o sledování do trvalého úložiště, jako je například integrovaný <xref:System.Activities.Tracking.EtwTrackingParticipant> nebo vlastní účastník sledování, který zaznamená informace do souboru.

 Další informace o sledování a konfiguraci sledování pro službu pracovního postupu hostované na webu najdete v tématech [sledování a trasování pracovních postupů](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md), [Konfigurace sledování pracovního postupu](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)a ukázky ukázek [ &#91;WF&#93; ](../../../../docs/framework/windows-workflow-foundation/samples/tracking.md) .

## <a name="use-wcf-tracing"></a>Použití trasování WCF
 Trasování WCF poskytuje trasování toku zpráv do a ze služby pracovního postupu. Tyto trasovací informace jsou užitečné při řešení problémů korelace, zejména u korelace na základě obsahu. Chcete-li povolit trasování, zadejte požadované naslouchací procesy trasování v části `system.diagnostics` souboru `web.config`, pokud je služba pracovního postupu hostitelem webu nebo soubor `app.config`, pokud je služba pracovního postupu v místním prostředí. Chcete-li zahrnout obsah zpráv do trasovacího souboru, zadejte `true` pro `logEntireMessage` v prvku `messageLogging` v části `diagnostics` `system.serviceModel`. V následujícím příkladu jsou informace o trasování, včetně obsahu zpráv, nakonfigurované tak, aby se zapsaly do souboru s názvem `service.svclog`.

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

 Chcete-li zobrazit informace o trasování, které jsou obsaženy v `service.svclog`, je použit [Nástroj Prohlížeč trasování služby (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) . To je zvlášť užitečné při řešení problémů s korelací na základě obsahu, protože můžete zobrazit obsah zprávy a přesně zjistit, co se předává, a zda odpovídá <xref:System.ServiceModel.CorrelationQuery> pro korelaci na základě obsahu. Další informace o trasování WCF naleznete v tématu [Nástroj pro prohlížeč trasování služby (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), [Konfigurace trasování](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)a [používání trasování pro řešení potíží s aplikací](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).

## <a name="common-context-exchange-correlation-issues"></a>Problémy s korelací běžných kontextových Exchange
 Určité typy korelace vyžadují, aby se při správné práci korelace použil konkrétní typ vazby. Mezi příklady patří korelace požadavku a odpovědi, která vyžaduje obousměrnou vazbu, jako je například <xref:System.ServiceModel.BasicHttpBinding> a korelace kontextu Exchange, která vyžaduje kontextovou vazbu, jako je například <xref:System.ServiceModel.BasicHttpContextBinding>. Většina vazeb podporuje obousměrné operace, takže se nejedná o běžný problém korelace požadavek-odpověď, ale pouze několik kontextových vazeb, včetně <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding> a <xref:System.ServiceModel.NetTcpContextBinding>. Pokud se jedna z těchto vazeb nepoužívá, bude počáteční volání služby pracovního postupu úspěšné, ale následné volání selžou s následujícím <xref:System.ServiceModel.FaultException>.

```output
There is no context attached to the incoming message for the service
and the current operation is not marked with "CanCreateInstance = true".
In order to communicate with this service check whether the incoming binding
supports the context protocol and has a valid context initialized.
```

 Kontextové informace, které se používají pro korelaci kontextu, mohou být vráceny <xref:System.ServiceModel.Activities.SendReply> do aktivity <xref:System.ServiceModel.Activities.Receive>, která inicializuje korelaci kontextu při použití obousměrné operace, nebo může být zadána volajícím, pokud je operace jednosměrná. Pokud kontext není odesílán volajícím nebo vráceným službou pracovního postupu, pak se při vyvolání následné operace vrátí stejný <xref:System.ServiceModel.FaultException> popsané dříve.

## <a name="common-request-reply-correlation-issues"></a>Běžné problémy s korelacemi požadavků a odpovědí
 Korelace požadavek-odpověď se používá s dvojicí <xref:System.ServiceModel.Activities.Receive> @ no__t-1 @ no__t-2 k implementaci obousměrné operace ve službě pracovních postupů a s dvojicí <xref:System.ServiceModel.Activities.Send> @ no__t-4 @ no__t-5, která vyvolává obousměrnou operaci v jiné webové službě. Při volání obousměrné operace ve službě WCF může být služba buď tradiční imperativní služba WCF založená na kódu, nebo může být služba pracovního postupu. Chcete-li použít korelaci požadavek-odpověď, je nutné použít obousměrnou vazbu, například <xref:System.ServiceModel.BasicHttpBinding> a operace musí být obousměrné.

 Pokud má služba pracovních postupů obousměrné operace paralelně nebo překrývající se páry <xref:System.ServiceModel.Activities.Receive> @ no__t-1 @ no__t-2 nebo <xref:System.ServiceModel.Activities.Send> @ no__t-4 @ no__t-5, nemusí být implicitní Správa korelace poskytovaná <xref:System.ServiceModel.Activities.WorkflowServiceHost> dostačující, obzvláště v horních zátěžích. scénáře a zprávy nemusí být správně směrovány. Chcete-li zabránit tomu, aby k tomuto problému došlo, doporučujeme při použití korelace požadavek-odpověď vždy zadat <xref:System.ServiceModel.Activities.CorrelationHandle>. Při použití šablon **SendAndReceiveReply** a **ReceiveAndSendReply** z části zasílání zpráv v sadě **nástrojů** návrháře pracovních postupů je ve výchozím nastavení explicitně nakonfigurován <xref:System.ServiceModel.Activities.CorrelationHandle>. Při sestavování pracovního postupu pomocí kódu je <xref:System.ServiceModel.Activities.CorrelationHandle> zadáno v <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> první aktivity ve páru. V následujícím příkladu je aktivita <xref:System.ServiceModel.Activities.Receive> konfigurovaná s explicitní <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> určenou v <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.

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

 Trvalost není povolená mezi dvojicí <xref:System.ServiceModel.Activities.Receive> @ no__t-1 @ no__t-2 nebo dvojicí <xref:System.ServiceModel.Activities.Send> @ no__t-4 @ no__t-5. Vytvoří se zóna bez trvalého uložení, která trvá až do dokončení obou aktivit. Pokud je aktivita, například aktivita zpoždění, v této zóně No-retrvalá a způsobí, že pracovní postup přestane být činný, pracovní postup zůstane neuložený ani v případě, že je hostitel nakonfigurovaný tak, aby zachoval pracovní postupy, když se stanou nečinné. Pokud se aktivita, jako je aktivita trvalosti, pokusí výslovně uchovávat v zóně bez trvalého uložení, je vyvolána závažná výjimka, pracovní postup se přeruší a <xref:System.ServiceModel.FaultException> se vrátí volajícímu. Zpráva o závažných výjimkách je "System. InvalidOperationException: trvalé aktivity nelze zahrnout do bloků trvalého uložení". Tato výjimka se nevrátí volajícímu, ale může být pozorována v případě, že je povoleno sledování. Zpráva pro <xref:System.ServiceModel.FaultException> vrácená volajícímu je "operace nemohla být provedena, protože instance WorkflowInstance" 5836145b-7da2-49d0-A052-a49162adeab6 "byla dokončena".

 Další informace o korelaci požadavků a odpovědí najdete v tématu [požadavek-odpověď](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md).

## <a name="common-content-correlation-issues"></a>Běžné problémy korelace obsahu
 Korelace na základě obsahu se používá v případě, že služba pracovního postupu přijímá více zpráv a část dat vyměňovaných zpráv identifikuje požadovanou instanci. Korelace na základě obsahu používá tato data ve zprávě, jako je číslo zákazníka nebo ID objednávky, ke směrování zpráv do správné instance pracovního postupu. Tato část popisuje několik běžných problémů, ke kterým může dojít při použití korelace na základě obsahu.

### <a name="ensure-the-identifying-data-is-unique"></a>Ujistěte se, že identifikační data jsou jedinečná.
 Data, která se používají k identifikaci instance, se zahashují do korelačního klíče. Je nutné dbát na to, aby se data, která se používají pro korelace, mohla zajímat, nebo dojde k kolizi v klíči s hodnotou hash, která může vyskytnout chyby, a způsobit nesměrování zpráv. Korelace založená jenom na názvu zákazníka může například způsobit kolizi, protože může existovat více zákazníků se stejným názvem. Dvojtečka (:) neměl by být použit jako součást dat, která se používají ke korelaci zprávy, protože je již použita k vymezení klíče a hodnoty dotazu zprávy pro vytvoření řetězce, který je následně hash. Pokud se používá trvalost, ujistěte se, že aktuální identifikační data nebyla využívána dříve trvalou instancí. Dočasné zakázání trvalého blokování může přispět k identifikaci tohoto problému. Trasování WCF lze použít k zobrazení počítaného korelačního klíče a je užitečné pro ladění tohoto typu problému.

### <a name="race-conditions"></a>Konflikty časování
 Mezi službou, která přijímá zprávu, existuje malá mezera a v rámci které se v současnosti inicializuje korelace, během které budou následné zprávy ignorovány. Pokud služba pracovního postupu inicializuje korelaci založenou na obsahu pomocí dat předávaných z klienta přes jednosměrnou operaci a volající odesílá okamžité následné zprávy, budou tyto zprávy během tohoto intervalu ignorovány. K tomu je možné se vyhnout pomocí oboustranné operace pro inicializaci korelace nebo pomocí <xref:System.ServiceModel.Activities.TransactedReceiveScope>.

### <a name="correlation-query-issues"></a>Problémy s dotazem korelace
 Korelační dotazy se používají k určení toho, jaká data se ve zprávě mají použít ke korelaci zprávy. Tato data se zadává pomocí dotazu XPath. Pokud zprávy ke službě nejsou odesílány, i když vše vypadá jako správné, jedna strategie pro řešení potíží je zadat hodnotu literálu, která odpovídá hodnotě dat zprávy namísto dotazu XPath. Chcete-li zadat hodnotu literálu, použijte funkci `string`. V následujícím příkladu je <xref:System.ServiceModel.MessageQuerySet> nakonfigurován pro použití literálové hodnoty `11445` pro `OrderId` a dotaz XPath je zakomentován.

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

 Pokud je dotaz XPath nesprávně nakonfigurovaný tak, že nejsou načtená žádná korelační data, vrátí se chybová zpráva s následující zprávou: "korelační dotaz vrátil prázdnou sadu výsledků. Ujistěte se prosím, že korelační dotazy pro koncový bod jsou správně nakonfigurované. Jedním z rychlých způsobů, jak tento problém vyřešit, je nahradit dotaz XPath hodnotou literálu, jak je popsáno v předchozí části. K tomuto problému může dojít, pokud použijete Tvůrce dotazů XPath v dialogových oknech **Přidat Inicializátory korelace** nebo **definice vlastnosti CorrelatesOn** a vaše služba pracovního postupu používá kontrakty zpráv. V následujícím příkladu je definována třída kontraktu zpráv.

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

 Tento kontrakt zprávy používá aktivita <xref:System.ServiceModel.Activities.Receive> v pracovním postupu. @No__t-0 v hlavičce zprávy slouží ke korelaci zprávy se správnou instancí. Pokud se dotaz XPath, který načítá `CartId`, vytvoří pomocí dialogových oken korelace v Návrháři pracovních postupů, vygeneruje se následující nesprávný dotaz XPath.

```
sm:body()/xg0:AddItemMessage/xg0:CartId
```

 Tento dotaz XPath by byl správný, pokud aktivita <xref:System.ServiceModel.Activities.Receive> použila pro data parametry, ale vzhledem k tomu, že používá kontrakt zprávy, není správný. Následující dotaz XPath je správný dotaz XPath pro načtení `CartId` z hlavičky.

```
sm:header()/tempuri:CartId
```

To lze potvrdit kontrolou textu zprávy.

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

Následující příklad ukazuje aktivitu <xref:System.ServiceModel.Activities.Receive> nakonfigurovanou pro operaci `AddItem`, která používá předchozí kontrakt zprávy pro příjem dat. Dotaz XPath je správně nakonfigurován.

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
