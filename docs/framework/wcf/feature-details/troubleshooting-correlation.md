---
title: Řešení potíží – korelace
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98003875-233d-4512-a688-4b2a1b0b5371
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2de3a8cac6e12d898173f8181b295c3e2e461cc7
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="troubleshooting-correlation"></a>Řešení potíží – korelace
Korelace se používá k propojení zpráv služby pracovního postupu se vzájemně k sobě a k instanci pracovního postupu správný, ale pokud není správně nakonfigurována, nebude přijaty zprávy a aplikace nebude správně fungovat. Toto téma obsahuje přehled několik metod pro řešení potíží s korelace a také uvádí některé běžné problémy, které může dojít, když používáte korelace.  
  
## <a name="handle-the-unknownmessagereceived-event"></a>Zpracovat událost UnknownMessageReceived  
 <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> Události dojde, když je neznámá zpráva přijatých služby, včetně zprávy, které nelze vztažen k existující instanci. Tato událost může pro samoobslužné hostované služby, ošetřit v hostitelskou aplikaci.  
  
```csharp  
host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)  
{  
    Console.WriteLine("Unknown Message Received:");  
    Console.WriteLine(e.Message);  
};  
```  
  
 Pro hostované webové služby, tato událost může ošetřit odvození třídy z <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> a přepsáním <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A>.  
  
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
  
 Tato vlastní <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> lze zadat v `svc` soubor služby.  
  
```  
<% @ServiceHost Language="C#" Service="OrderServiceWorkflow" Factory="CustomFactory" %>  
```  
  
 Po vyvolání této obslužné rutiny zprávy můžete načíst pomocí <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> vlastnost <xref:System.ServiceModel.UnknownMessageReceivedEventArgs>a bude připomínat následující zpráva.  
  
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
  
 Probíhá kontrola zpráv odeslaných <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> obslužná rutina může poskytnout proč zpráva není korelovat na instanci služby pracovního postupu, který následuje.  
  
## <a name="use-tracking-to-monitor-the-progress-of-the-workflow"></a>Používání sledování pro monitorování průběhu pracovního postupu  
 Sledování poskytuje způsob, jak monitorovat průběh pracovního postupu. Ve výchozím nastavení jsou záznamy o sledování vygenerované pro pracovní postup události životního cyklu, události životního cyklu aktivity, šíření selhání a obnovení záložku. Kromě toho můžete vlastní sledování záznamů vysílaných vlastní aktivity. Při řešení potíží – korelace, aktivita sledování záznamy, na záložku obnovení záznamy a záznamy šíření selhání jsou velmi užitečné. Aktivita sledování záznamů slouží k určení aktuální průběh pracovního postupu a může pomoct identifikovat, které zasílání zpráv aktivity je aktuálně čeká na zprávy. Záložku obnovení záznamy jsou užitečné, protože označují, že v tomto pracovním postupu byla přijata zpráva a selhání šíření záznamů poskytnout záznam všech chyb v pracovním postupu. Chcete-li povolit sledování, zadejte požadovanou <xref:System.Activities.Tracking.TrackingParticipant> v <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> z <xref:System.ServiceModel.Activities.WorkflowServiceHost>. V následujícím příkladu `ConsoleTrackingParticipant` (z [vlastní sledování](../../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) ukázkové) je nakonfigurována pomocí výchozí sledování profil.  
  
```csharp  
host.WorkflowExtensions.Add(new ConsoleTrackingParticipant());  
```  
  
 Sledování účastník například ConsoleTrackingParticipant je užitečné pro služeb vlastním hostováním pracovních postupů, které mají okna konzoly. Pro hostované webové služby, třeba použít sledování účastník, který zaznamenává informace o sledování odolná úložiště, jako je například integrované <xref:System.Activities.Tracking.EtwTrackingParticipant>, nebo vlastní sledování člena, který protokoluje informace do souboru, například `TextWriterTrackingParticpant` z [ Sledování pomocí textového souboru](../../../../docs/framework/windows-workflow-foundation/samples/tracking-using-a-text-file.md) ukázka.  
  
 Další informace o sledování a konfigurace sledování služby hostované webové pracovního postupu najdete v tématu [pracovního postupu pro sledování a trasování](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md), [konfigurace sledování pro pracovní postup](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)a [ Sledování &#91;ukázky WF&#93; ](../../../../docs/framework/windows-workflow-foundation/samples/tracking.md) ukázky.  
  
## <a name="use-wcf-tracing"></a>Pomocí trasování WCF  
 Trasování WCF poskytuje trasování toku zpráv do a ze služby pracovních postupů. Tyto informace trasování jsou užitečné při řešení problémů korelace, hlavně pro korelace na základě obsahu. Povolení trasování, zadejte požadované trasování – moduly naslouchání v `system.diagnostics` části `web.config` souboru pokud hostované webové služby pracovního postupu nebo `app.config` soubor, pokud se hostuje sama služby pracovního postupu. Chcete-li zahrnout obsah zprávy v trasovacím souboru, zadejte `true` pro `logEntireMessage` v `messageLogging` element v `diagnostics` části `system.serviceModel`. V následujícím příkladu je nakonfigurované informace trasování, včetně obsahu zprávy, k zápisu do souboru, který je pojmenován `service.svclog`.  
  
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
  
 Chcete-li zobrazit informace trasování, která je součástí `service.svclog`, [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) se používá. To je obzvláště užitečná při řešení potíží – korelace na základě obsahu problémy, protože můžete zobrazit obsah zprávy a zobrazit přesně co je předávána, a zda odpovídá <xref:System.ServiceModel.CorrelationQuery> pro korelace na základě obsahu. Další informace o trasování WCF najdete v tématu [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), [Konfigurace trasování](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md), a [pomocí trasování řešení potíží s aplikací](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).  
  
## <a name="common-context-exchange-correlation-issues"></a>Běžné problémy korelace Exchange kontextu  
 Určité typy korelace vyžadují, aby určitý typ vazby se používá pro korelaci fungovala správně. Mezi příklady patří korelace požadavku a odpovědi, které vyžaduje obousměrný vazbu, jako <xref:System.ServiceModel.BasicHttpBinding>a korelace kontextové výměny, který vyžaduje, na základě kontextu vazby, jako <xref:System.ServiceModel.BasicHttpContextBinding>. Většina vazby podporu obousměrný operací, nejedná se o běžné problémy, se pro korelace požadavku a odpovědi, ale existují jen někteří z nich na základě kontextu vazby, včetně <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, a <xref:System.ServiceModel.NetTcpContextBinding>. Jednu z těchto vazeb se nepoužívá, počáteční volání služby pracovního postupu bude úspěšné, ale následná volání nebudou úspěšná s následující <xref:System.ServiceModel.FaultException>.  
  
```Output  
There is no context attached to the incoming message for the service   
and the current operation is not marked with "CanCreateInstance = true".   
In order to communicate with this service check whether the incoming binding   
supports the context protocol and has a valid context initialized.  
```  
  
 Informace o kontextu, který slouží pro korelaci kontext může být vrácen pouze <xref:System.ServiceModel.Activities.SendReply> k <xref:System.ServiceModel.Activities.Receive> aktivity, která inicializuje kontext korelace, když pomocí obousměrné operaci, nebo ji lze zadat volající Pokud byla operace jednosměrná. Pokud není kontextu poslal volající nebo vrácené služby pracovního postupu pak stejné <xref:System.ServiceModel.FaultException> popsané dříve bude vrácen, pokud následné operace je volána.  
  
 Další informace najdete v tématu [kontextová výměna](../../../../docs/framework/wcf/feature-details/context-exchange-correlation.md).  
  
## <a name="common-request-reply-correlation-issues"></a>Běžné problémy korelace požadavku a odpovědi  
 Korelace požadavku a odpovědi se používá s <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pár implementovat obousměrný operace ve službě pracovního postupu a s <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> pár, který vyvolá obousměrný operaci v jiný Web Služba. Při vyvolání obousměrný operace ve službě WCF, služba může být buď tradiční imperativní založené na kódu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby, nebo může být služby pracovních postupů. Použít korelace požadavku a odpovědi vazba obousměrná musí být použita, jako například <xref:System.ServiceModel.BasicHttpBinding>, a operace musí být obousměrné.  
  
 Pokud službu pracovní postup obsahuje obousměrný operace paralelní nebo překrývající se <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> nebo <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> páry pak implicitní korelace zpracování Správa poskytovaná v rámci <xref:System.ServiceModel.Activities.WorkflowServiceHost>nemusí být plně dostačující, zejména ve scénářích velkými nároky a zprávy nebudou směrovány správně. Chcete-li zabránit výskytu tohoto problému, doporučujeme, aby vždy explicitně zadáte <xref:System.ServiceModel.Activities.CorrelationHandle> při použití korelace požadavku a odpovědi. Při použití **SendAndReceiveReply** a **ReceiveAndSendReply** šablony z části zasílání zpráv **sada nástrojů** v Návrháři pracovních postupů <xref:System.ServiceModel.Activities.CorrelationHandle> explicitně nakonfigurované ve výchozím nastavení. Při vytváření pracovního postupu pomocí kódu, <xref:System.ServiceModel.Activities.CorrelationHandle> je uveden v <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> první aktivitu v páru. V následujícím příkladu <xref:System.ServiceModel.Activities.Receive> aktivity je nakonfigurován pomocí explicitního <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> zadaný v <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.  
  
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
  
 Mezi není povolena trvalost <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pár nebo <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> pár. Je vytvořena zóna no-persist trvající až do dokončení obou aktivity. Pokud aktivity, jako je například aktivitu zpoždění je v této zóně no-persist a pracovní postup na nečinnost, pracovní postup neuchovává i v případě, pokud hostitel je nakonfigurovaný pro uchování pracovních postupů, kdy se stanou nečinné. Pokud aktivity, jako je například aktivitu zachovat pokusí explicitně zachovat v zóně ne zachovat, závažná je vyvolána výjimka, přerušení pracovního postupu a <xref:System.ServiceModel.FaultException> je vrácen volajícímu. Zpráva o závažné výjimce "System.InvalidOperationException: zachování aktivity nemůžou být obsažené v rámci bloků žádné trvalost.". Tato výjimka není vrácen volajícímu ale může být dodržen, pokud je povoleno sledování. Zpráva pro <xref:System.ServiceModel.FaultException> vrácen volajícímu je "operaci nelze provést, protože instance pracovního postupu '5836145b-7da2 - 49 d 0-a052-a49162adeab6' byla dokončena".  
  
 Další informace o korelace požadavku a odpovědi najdete v tématu [požadavku a odpovědi](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md).  
  
## <a name="common-content-correlation-issues"></a>Běžné problémy obsahu korelace  
 Korelace na základě obsahu se používá při služby pracovního postupu přijímá více zpráv a část dat v výměně zpráv určuje požadovanou instanci. Korelace na základě obsahu používá tato data ve zprávě, jako je například číslo nebo pořadí ID zákazníka, pro směrování zpráv do instance správný pracovního postupu. Tato část popisuje několik běžné problémy, které mohou nastat při použití korelace na základě obsahu.  
  
### <a name="ensure-the-identifying-data-is-unique"></a>Ujistěte se, že je jedinečné identifikační Data  
 Data, která se používá k identifikaci instance je algoritmus hash, do klíče korelace. Dbát musí zaručit, že data, která se používá pro korelačního jedinečné, jinak může dojít a způsobit zpráv, které mají být nesprávně směrovanými kolizí v klíči hash. Například existuje korelace pouze podle jméno zákazníka mohou způsobit kolize, protože může být více zákazníků, kteří mají stejný název. Jako součást data, která slouží ke sladění zprávu, protože se již používá pro vymezení klíč a hodnotu a vytvořit řetězec, který je následně rozdělí dotazu zprávu nepoužívejte dvojtečkou (:). Pokud trvalost se používá, ujistěte se, že data aktuálního identifikační nebyl použit dříve drženého instancí. Dočasně zakázat trvalost může pomoci identifikovat potíže. WCF trasování můžete použít k zobrazení počítané korelace klíč a slouží k ladění tento druh problému.  
  
### <a name="race-conditions"></a>Konflikty časování  
 Existuje malé mezera v době mezi službu přijetí zprávy a korelace ve skutečnosti inicializován, během které následné zprávy budou ignorovány. Pokud služby pracovního procesu inicializuje korelace na základě obsahu pomocí dat předávaných přes Jednosměrná operace z klienta, a odesílá okamžitou následné zprávy, se tyto zprávy ignorovat během tohoto intervalu. Tím se vyhnout pomocí obousměrné operace k chybě při inicializaci korelaci nebo pomocí <xref:System.ServiceModel.Activities.TransactedReceiveScope>.  
  
### <a name="correlation-query-issues"></a>Korelace dotazu problémy  
 Korelace dotazy se používají k určení, jaká data ve zprávě slouží ke sladění zprávy. Tato data je určena pomocí dotaz XPath. Pokud zprávy a pokuste se službu nejsou distribuovanou, i když všechno, co se zdá být správné, je jednou z možných strategií pro řešení potíží s zadejte literálu hodnotu, která odpovídá hodnotě data zpráv místo dotaz XPath. Pokud chcete zadat literálovou hodnotou, použijte `string` funkce. V následujícím příkladu <xref:System.ServiceModel.MessageQuerySet> je nakonfigurovaný na použití hodnotu literálu `11445` pro `OrderId` a dotaz XPath je označeno jako komentář.  
  
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
  
 Pokud dotaz XPath není správně nakonfigurovaná tak, že je načíst žádná data korelace, vrátí se chybu s následující zprávou: "dotazu korelace poskytuje prázdnou sadu výsledků. Ujistěte se, že jsou správně nakonfigurovány korelace dotazy pro koncový bod." Jeden rychlý způsob, jak toto řešení je nahradit dotaz XPath s literálovou hodnotou, jak je popsáno v předchozí části. Tento problém může dojít, pokud používáte Tvůrce dotazů XPath v **přidat inicializátory korelace** nebo **CorrelatesOn definice** dialogových oken a služby pracovního postupu používá kontrakty zpráv. V následujícím příkladu je definován třídou kontraktu zprávy.  
  
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
  
 Tento kontrakt zprávy používá <xref:System.ServiceModel.Activities.Receive> aktivity v pracovním postupu. `CartId` v záhlaví zprávy slouží ke sladění zprávu, která se správnou instanci. Pokud dotaz XPath, který načte `CartId` je vytvořený pomocí korelace dialogová okna v Návrháři pracovních postupů, následující nesprávnou XPath vygenerovat dotaz.  
  
```  
sm:body()/xg0:AddItemMessage/xg0:CartId  
```  
  
 Tento dotaz XPath by byly správné Pokud <xref:System.ServiceModel.Activities.Receive> aktivita používá parametry pro data, ale vzhledem k tomu, že používá kontrakt zprávy je nesprávný. Následující dotaz XPath je správný dotaz XPath pro načtení `CartId` z hlavičky.  
  
```  
sm:header()/tempuri:CartId  
```  
  
 To jde potvrdit tak, že prověří tělo zprávy.  
  
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
  
 Následující příklad ukazuje <xref:System.ServiceModel.Activities.Receive> aktivity, které jsou nakonfigurované pro `AddItem` operací, která používá předchozí kontrakt zprávy přijímat data. Dotaz XPath je správně nakonfigurován.  
  
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
  
 Další informace o korelace na základě obsahu najdete v tématu [na základě obsahu](../../../../docs/framework/wcf/feature-details/content-based-correlation.md) a [korelační kalkulačky](../../../../docs/framework/windows-workflow-foundation/samples/correlated-calculator.md) ukázka.
