---
title: Řešení potíží – korelace
ms.date: 03/30/2017
ms.assetid: 98003875-233d-4512-a688-4b2a1b0b5371
ms.openlocfilehash: a5942c13bb4026cfeb8f664c60fb658373ffcca5
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596705"
---
# <a name="troubleshooting-correlation"></a>Řešení potíží – korelace
Korelace se používá ke vzájemnému propojení zpráv služby pracovních postupů a ke správné instanci pracovního postupu, ale pokud není správně nakonfigurovaná, zprávy se neobdrží a aplikace nebudou fungovat správně. V tomto tématu najdete přehled několika metod pro řešení problémů s korelací a také uvádí některé běžné problémy, které mohou nastat při použití korelace.

## <a name="handle-the-unknownmessagereceived-event"></a>Zpracování události UnknownMessageReceived
 K <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> události dojde, když služba obdrží neznámou zprávu, včetně zpráv, které nelze korelovat s existující instancí. V případě samoobslužných služeb je možné tuto událost zpracovat v hostitelské aplikaci.

```csharp
host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)
{
    Console.WriteLine("Unknown Message Received:");
    Console.WriteLine(e.Message);
};
```

 U služeb hostovaných na webu lze tuto událost zpracovat odvozením třídy z <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> a přepsáním <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A> .

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

 Tato vlastní <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> možnost se pak dá zadat v `svc` souboru pro službu.

`<% @ServiceHost Language="C#" Service="OrderServiceWorkflow" Factory="CustomFactory" %>`

 Při vyvolání této obslužné rutiny lze zprávu načíst pomocí <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> vlastnosti <xref:System.ServiceModel.UnknownMessageReceivedEventArgs> , a bude vypadat podobně jako následující zpráva.

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

 Kontrola zpráv odeslaných do <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> obslužné rutiny může poskytnout informace o tom, proč se zpráva nekoreluje s instancí služby pracovního postupu.

## <a name="use-tracking-to-monitor-the-progress-of-the-workflow"></a>Sledování průběhu pracovního postupu pomocí sledování
 Sledování poskytuje způsob, jak monitorovat průběh pracovního postupu. Ve výchozím nastavení jsou záznamy sledování vydávány pro události životního cyklu pracovního cyklu, události životního cyklu aktivity, šíření chyb a opětovné pokračování záložek. Vlastní záznamy sledování je navíc možné vysílat vlastními aktivitami. Při řešení potíží s korelacemi, záznamy sledování aktivity, pokračování záznamů a záznamy o šíření chyb jsou nejužitečnější. Záznamy sledování aktivit se dají použít k určení aktuálního průběhu pracovního postupu a můžou vám pomůžou určit, které aktivity zasílání zpráv aktuálně čekají na zprávy. Záznamy pokračování v záložek jsou užitečné, protože označují, že pracovní postup přijal zprávu, a záznamy o šíření chyb poskytují záznam všech chyb v pracovním postupu. Chcete-li povolit sledování, zadejte požadované <xref:System.Activities.Tracking.TrackingParticipant> v části <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> <xref:System.ServiceModel.Activities.WorkflowServiceHost> . V následujícím příkladu `ConsoleTrackingParticipant` je (z [vlastní ukázky sledování](../../windows-workflow-foundation/samples/custom-tracking.md) ) nakonfigurovaná pomocí výchozího profilu sledování.

```csharp
host.WorkflowExtensions.Add(new ConsoleTrackingParticipant());
```

 Sledování účastníka, jako je ConsoleTrackingParticipant, je užitečné pro samoobslužné služby pracovních postupů, které mají okno konzoly. V případě služby hostované na webu by se měla použít sledování účastníka, který zaznamenává informace o sledování do trvalého úložiště, jako je například integrovaný <xref:System.Activities.Tracking.EtwTrackingParticipant> nebo vlastní účastník sledování, který zaznamená informace do souboru.

 Další informace o sledování a konfiguraci sledování pro službu pracovního postupu hostované na webu najdete v tématech [sledování a trasování pracovních postupů](../../windows-workflow-foundation/workflow-tracking-and-tracing.md), [Konfigurace sledování pro pracovní postup](../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md)a [ukázky &#91;WF&#93;](../../windows-workflow-foundation/samples/tracking.md) ukázky.

## <a name="use-wcf-tracing"></a>Použití trasování WCF
 Trasování WCF poskytuje trasování toku zpráv do a ze služby pracovního postupu. Tyto trasovací informace jsou užitečné při řešení problémů korelace, zejména u korelace na základě obsahu. Chcete-li povolit trasování, zadejte požadované naslouchací procesy trasování v `system.diagnostics` části `web.config` souboru, pokud je služba pracovního postupu hostitelem webu, nebo soubor, `app.config` Pokud je služba pracovního postupu v místním prostředí. Chcete-li zahrnout obsah zpráv do trasovacího souboru, zadejte `true` pro `logEntireMessage` v `messageLogging` prvku v `diagnostics` části `system.serviceModel` . V následujícím příkladu jsou informace o trasování, včetně obsahu zpráv, nakonfigurované k zápisu do souboru s názvem `service.svclog` .

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

 Chcete-li zobrazit trasovací informace, které jsou obsaženy v `service.svclog` nástroji, je použit [Nástroj Prohlížeč trasování služby (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) . To je užitečné hlavně při řešení problémů korelace na základě obsahu, protože můžete zobrazit obsah zprávy a přesně zjistit, co se předává, a zda odpovídá <xref:System.ServiceModel.CorrelationQuery> pro korelaci na základě obsahu. Další informace o trasování WCF naleznete v tématu [Nástroj pro prohlížeč trasování služby (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md), [Konfigurace trasování](../diagnostics/tracing/configuring-tracing.md)a [používání trasování pro řešení potíží s aplikací](../diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).

## <a name="common-context-exchange-correlation-issues"></a>Problémy s korelací běžných kontextových Exchange
 Určité typy korelace vyžadují, aby se při správné práci korelace použil konkrétní typ vazby. Mezi příklady patří korelace požadavku a odpovědi, která vyžaduje obousměrnou vazbu, jako <xref:System.ServiceModel.BasicHttpBinding> je a korelace kontextu Exchange, která vyžaduje kontextovou vazbu, jako je například <xref:System.ServiceModel.BasicHttpContextBinding> . Většina vazeb podporuje obousměrné operace, takže se nejedná o běžný problém korelace požadavek-odpověď, ale pouze několik kontextových vazeb, včetně <xref:System.ServiceModel.BasicHttpContextBinding> , <xref:System.ServiceModel.WSHttpContextBinding> a <xref:System.ServiceModel.NetTcpContextBinding> . Pokud se jedna z těchto vazeb nepoužívá, bude prvotní volání služby pracovního postupu úspěšné, ale následné volání selžou s následujícím <xref:System.ServiceModel.FaultException> .

```output
There is no context attached to the incoming message for the service
and the current operation is not marked with "CanCreateInstance = true".
In order to communicate with this service check whether the incoming binding
supports the context protocol and has a valid context initialized.
```

 Kontextové informace, které se používají pro korelaci kontextu, mohou být vráceny <xref:System.ServiceModel.Activities.SendReply> <xref:System.ServiceModel.Activities.Receive> aktivitě, která inicializuje relaci kontextu při použití obousměrné operace, nebo může být zadána volajícím, pokud je operace jednosměrná. Pokud kontext není odesílán volajícím nebo vráceným službou pracovního postupu, pak bude <xref:System.ServiceModel.FaultException> při vyvolání následné operace vrácen výše popsané předchozí.

## <a name="common-request-reply-correlation-issues"></a>Běžné problémy s korelacemi požadavků a odpovědí
 Korelace požadavku a odpovědi se používá spolu s <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> dvojicí k implementaci obousměrné operace ve službě pracovních postupů a s <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> párem, která vyvolává obousměrnou operaci v jiné webové službě. Při volání obousměrné operace ve službě WCF může být služba buď tradiční imperativní služba WCF založená na kódu, nebo může být služba pracovního postupu. Chcete-li použít korelaci požadavek-odpověď, je třeba použít obousměrnou vazbu, například <xref:System.ServiceModel.BasicHttpBinding> a operace musí být obousměrné.

 Pokud má služba pracovního postupu obousměrné operace paralelně, nebo překrývající se <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> nebo <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> páry, pak není k dispozici možnost implicitního řízení korelace, která je poskytována nástrojem <xref:System.ServiceModel.Activities.WorkflowServiceHost> , zejména ve scénářích s vysokým důrazem a zprávy nemusí být správně směrovány. Chcete-li zabránit tomu, aby k tomuto problému došlo, doporučujeme <xref:System.ServiceModel.Activities.CorrelationHandle> při použití korelace požadavek-odpověď vždy explicitně zadat. Při použití šablon **SendAndReceiveReply** a **ReceiveAndSendReply** z části zasílání zpráv v sadě **nástrojů** v Návrháři pracovních postupů je ve <xref:System.ServiceModel.Activities.CorrelationHandle> výchozím nastavení explicitně nakonfigurován. Při sestavování pracovního postupu pomocí kódu <xref:System.ServiceModel.Activities.CorrelationHandle> je určena v <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> první aktivitě páru. V následujícím příkladu <xref:System.ServiceModel.Activities.Receive> je aktivita nakonfigurována s explicitním <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> zadáním v <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> .

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

 Trvalost není povolená mezi <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> dvojicí nebo <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> dvojicí. Vytvoří se zóna bez trvalého uložení, která trvá až do dokončení obou aktivit. Pokud je aktivita, například aktivita zpoždění, v této zóně No-retrvalá a způsobí, že pracovní postup přestane být činný, pracovní postup zůstane neuložený ani v případě, že je hostitel nakonfigurovaný tak, aby zachoval pracovní postupy, když se stanou nečinné. Pokud aktivita, jako je trvalá aktivita, se pokusí o explicitní uchování v zóně bez trvalého uložení, je vyvolána závažná výjimka, pracovní postup se přeruší a <xref:System.ServiceModel.FaultException> vrátí se volajícímu. Zpráva o závažných výjimkách je "System. InvalidOperationException: trvalé aktivity nelze zahrnout do bloků trvalého uložení". Tato výjimka se nevrátí volajícímu, ale může být pozorována v případě, že je povoleno sledování. Zpráva pro <xref:System.ServiceModel.FaultException> vráceného volajícímu je "operace nemohla být provedena, protože instance WorkflowInstance" 5836145b-7da2-49d0-A052-a49162adeab6 "byla dokončena".

 Další informace o korelaci požadavků a odpovědí najdete v tématu [požadavek-odpověď](request-reply-correlation.md).

## <a name="common-content-correlation-issues"></a>Běžné problémy korelace obsahu
 Korelace na základě obsahu se používá v případě, že služba pracovního postupu přijímá více zpráv a část dat vyměňovaných zpráv identifikuje požadovanou instanci. Korelace na základě obsahu používá tato data ve zprávě, jako je číslo zákazníka nebo ID objednávky, ke směrování zpráv do správné instance pracovního postupu. Tato část popisuje několik běžných problémů, ke kterým může dojít při použití korelace na základě obsahu.

### <a name="ensure-the-identifying-data-is-unique"></a>Ujistěte se, že identifikační data jsou jedinečná.
 Data, která se používají k identifikaci instance, se zahashují do korelačního klíče. Je nutné dbát na to, aby se data, která se používají pro korelace, mohla zajímat, nebo dojde k kolizi v klíči s hodnotou hash, která může vyskytnout chyby, a způsobit nesměrování zpráv. Korelace založená jenom na názvu zákazníka může například způsobit kolizi, protože může existovat více zákazníků se stejným názvem. Dvojtečka (:) neměl by být použit jako součást dat, která se používají ke korelaci zprávy, protože je již použita k vymezení klíče a hodnoty dotazu zprávy pro vytvoření řetězce, který je následně hash. Pokud se používá trvalost, ujistěte se, že aktuální identifikační data nebyla využívána dříve trvalou instancí. Dočasné zakázání trvalého blokování může přispět k identifikaci tohoto problému. Trasování WCF lze použít k zobrazení počítaného korelačního klíče a je užitečné pro ladění tohoto typu problému.

### <a name="race-conditions"></a>Konflikty časování
 Mezi službou, která přijímá zprávu, existuje malá mezera a v rámci které se v současnosti inicializuje korelace, během které budou následné zprávy ignorovány. Pokud služba pracovního postupu inicializuje korelaci založenou na obsahu pomocí dat předávaných z klienta přes jednosměrnou operaci a volající odesílá okamžité následné zprávy, budou tyto zprávy během tohoto intervalu ignorovány. K tomu je možné se vyhnout pomocí obousměrné operace pro inicializaci korelace nebo pomocí <xref:System.ServiceModel.Activities.TransactedReceiveScope> .

### <a name="correlation-query-issues"></a>Problémy s dotazem korelace
 Korelační dotazy se používají k určení toho, jaká data se ve zprávě mají použít ke korelaci zprávy. Tato data se zadává pomocí dotazu XPath. Pokud zprávy ke službě nejsou odesílány, i když vše vypadá jako správné, jedna strategie pro řešení potíží je zadat hodnotu literálu, která odpovídá hodnotě dat zprávy namísto dotazu XPath. Chcete-li zadat hodnotu literálu, použijte `string` funkci. V následujícím příkladu <xref:System.ServiceModel.MessageQuerySet> je nakonfigurována pro použití literálové hodnoty `11445` pro `OrderId` a dotaz XPath je zakomentován.

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

 Tato zpráva se používá <xref:System.ServiceModel.Activities.Receive> v aktivitě pracovního postupu. `CartId`V záhlaví zprávy se používá ke korelaci zprávy se správnou instancí. Pokud se dotaz XPath, který načte, `CartId` vytvoří pomocí dialogových oken korelace v Návrháři pracovních postupů, vygeneruje se následující nesprávný dotaz XPath.

```
sm:body()/xg0:AddItemMessage/xg0:CartId
```

 Tento dotaz XPath by byl správný, pokud <xref:System.ServiceModel.Activities.Receive> aktivita použila parametry pro data, ale vzhledem k tomu, že používá kontrakt zprávy, není správný. Následující dotaz XPath je správný dotaz XPath pro načtení `CartId` z hlavičky.

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

Následující příklad ukazuje <xref:System.ServiceModel.Activities.Receive> aktivitu nakonfigurovanou pro `AddItem` operaci, která používá předchozí kontrakt zprávy pro příjem dat. Dotaz XPath je správně nakonfigurován.

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
