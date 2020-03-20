---
title: Formátovací modul a selektor operace
ms.date: 03/30/2017
ms.assetid: 1c27e9fe-11f8-4377-8140-828207b98a0e
ms.openlocfilehash: 9d1bc0afa54f89e064eab3f3e45da60c8d10de38
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144276"
---
# <a name="operation-formatter-and-operation-selector"></a>Formátovací modul a selektor operace
Tato ukázka ukazuje, jak windows communication foundation (WCF) body rozšiřitelnosti lze povolit data zprávy v jiném formátu, než wcf očekává. Ve výchozím nastavení WCF formatters očekávat parametry `soap:body` metody, které mají být zahrnuty do prvku. Ukázka ukazuje, jak implementovat vlastní operace formatter, který analyzuje data parametrů z řetězce dotazu HTTP GET místo a vyvolá metody pomocí dat.  
  
 Ukázka je založena na [začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), `ICalculator` který implementuje servisní smlouvy. Ukazuje, jak přidat, odečíst, násobit a rozdělit zprávy lze změnit na použití HTTP GET pro požadavky klienta na server a HTTP POST se zprávami POX pro odpovědi mezi servery.  
  
 Chcete-li tak učinit, ukázka poskytuje následující:  
  
- `QueryStringFormatter`, který <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> implementuje a <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> pro klienta a server, respektive a zpracovává data v řetězci dotazu.  
  
- `UriOperationSelector`, který <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementuje na serveru k provedení expedice operace na základě názvu operace v požadavku GET.  
  
- `EnableHttpGetRequestsBehavior`koncového bodu (a odpovídající konfigurace), který přidá potřebný volič operací do běhu.  
  
- Ukazuje, jak vložit novou operaci forpono do modulu runtime.  
  
- V této ukázce jsou klient a služba konzolové aplikace (.exe).  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
## <a name="key-concepts"></a>Klíčové koncepty  
 `QueryStringFormatter`- Operace formátovací modul je součást wcf, který je zodpovědný za převod zprávy do pole parametr objekty a pole parametr objekty do zprávy. To se provádí na <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> straně klienta pomocí <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> rozhraní a na serveru s rozhraním. Tato rozhraní umožňují uživatelům získat zprávy požadavku `Serialize` a `Deserialize` odpovědi z metody a.  
  
 V této `QueryStringFormatter` ukázce implementuje obě tato rozhraní a je implementována na straně klienta a serveru.  
  
 Požadavek:  
  
- Ukázka používá <xref:System.ComponentModel.TypeConverter> třídu k převodu dat parametrů ve zprávě požadavku na řetězce a z řetězce. Pokud <xref:System.ComponentModel.TypeConverter> a není k dispozici pro konkrétní typ, ukázkový formavý modul vyvolá výjimku.  
  
- V `IClientMessageFormatter.SerializeRequest` metodě na straně klienta vytvoří modul pro formátování ano s příslušnou adresou To a připojí název operace jako příponu. Tento název se používá k odeslání do příslušné operace na serveru. Potom převezme pole objektů parametrů a serializuje data parametrů do řetězce dotazu URI pomocí názvů <xref:System.ComponentModel.TypeConverter> parametrů a hodnot převedených třídou. <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> Vlastnosti <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> a jsou pak nastaveny na tento identifikátor URI. <xref:System.ServiceModel.Channels.MessageProperties>je přístupný prostřednictvím ubytovacího <xref:System.ServiceModel.Channels.Message.Properties%2A> zařízení.  
  
- V `IDispatchMessageFormatter.DeserializeRequest` metodě na serveru formátovací modul `Via` načte identifikátor URI ve vlastnostech zprávy příchozího požadavku. Analyzuje dvojice název-hodnota v řetězci dotazu URI na názvy a hodnoty parametrů a používá názvy parametrů a hodnoty k naplnění pole parametrů předaných do metody. Všimněte si, že operace odeslání již došlo, takže název operace přípona je ignorována v této metodě.  
  
 Odpověď:  
  
- V této ukázce HTTP GET se používá pouze pro požadavek. Formátovací modul deleguje odesílání odpovědi na původní formátovací modul, který by byl použit ke generování zprávy XML. Jedním z cílů této ukázky je ukázat, jak může být implementována taková delegující forponáta.  
  
### <a name="uripathsuffixoperationselector-class"></a>Třída UriPathSuffixOperationSelector  
 Rozhraní <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> umožňuje uživatelům implementovat vlastní logiku, pro kterou by měla být odeslána určitá zpráva.  
  
 V této `UriPathSuffixOperationSelector` ukázce musí být implementována na serveru vybrat příslušnou operaci, protože název operace je součástí HTTP GET URI spíše než záhlaví akce ve zprávě. Ukázka je nastavena tak, aby umožňovala pouze názvy operací bez rozlišování velkých a malých písmen.  
  
 Metoda `SelectOperation` převezme příchozí zprávu a vyhledá `Via` identifikátor URI ve svých vlastnostech zprávy. Extrahuje příponu názvu operace z identifikátoru URI, vyhledá interní tabulku, aby získal název operace, do které by měla být zpráva odeslána, a vrátí tento název operace.  
  
### <a name="enablehttpgetrequestsbehavior-class"></a>Povolit třídu HttpGetRequestsBehavior  
 Součást `UriPathSuffixOperationSelector` lze nastavit programově nebo pomocí chování koncového bodu. Ukázka implementuje `EnableHttpGetRequestsBehavior` chování, které je určeno v konfiguračním souboru aplikace služby.  
  
 Na serveru:  
  
 Je <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> nastavena <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> na implementaci.  
  
 Ve výchozím nastavení wcf používá filtr adresy přesné shody. Identifikátor URI na příchozí zprávě obsahuje příponu názvu operace následovanou řetězcem dotazu, který obsahuje data parametrů, takže chování koncového bodu také změní filtr adresy na filtr shody předpony. Používá WCF<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> pro tento účel.  
  
### <a name="installing-operation-formatters"></a>Instalace provozních formatters  
 Chování operace, které určují formatters jsou jedinečné. Jedno takové chování je vždy implementováno ve výchozím nastavení pro každou operaci k vytvoření potřebné operace formatter. Toto chování však vypadat jako jen další operace chování; nejsou identifikovatelné žádným jiným atributem. Chcete-li nainstalovat náhradní chování, implementace musí hledat konkrétní formatter chování, které jsou nainstalovány zavaděč typu WCF ve výchozím nastavení a buď jej nahradit nebo přidat kompatibilní chování spustit po výchozí chování.  
  
 Tyto operace formatters chování lze nastavit programově <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> před voláním nebo zadáním chování operace, která je provedena po výchozí. Nelze jej však snadno nastavit podle chování koncového bodu (a tedy podle konfigurace), protože model chování neumožňuje chování nahradit jiné chování nebo jinak upravit strom popisu.  
  
 Na straně klienta:  
  
 Implementace <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> musí být implementována tak, aby bylo možné převést požadavky na požadavky HTTP GET a delegovat na původní modul pro formátování pro odpovědi. To se provádí `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` voláním pomocné metody.  
  
 To musí být `CreateChannel`provedeno před voláním .  
  
```csharp  
void ReplaceFormatterBehavior(OperationDescription operationDescription, EndpointAddress address)  
{  
    // Remove the DataContract behavior if it is present.  
    IOperationBehavior formatterBehavior = operationDescription.Behaviors.Remove<DataContractSerializerOperationBehavior>();  
    if (formatterBehavior == null)  
    {  
        // Remove the XmlSerializer behavior if it is present.  
        formatterBehavior = operationDescription.Behaviors.Remove<XmlSerializerOperationBehavior>();  
        ...  
    }  
  
    // Remember what the innerFormatterBehavior was.  
    DelegatingFormatterBehavior delegatingFormatterBehavior = new DelegatingFormatterBehavior(address);  
    delegatingFormatterBehavior.InnerFormatterBehavior = formatterBehavior;  
   operationDescription.Behaviors.Add(delegatingFormatterBehavior);  
}  
```  
  
 Na serveru:  
  
- Rozhraní <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> musí být implementováno tak, aby bylo možné číst požadavky HTTP GET a delegovat na původní návrhový modul pro zápis odpovědí. To se provádí voláním stejné `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` pomocné metody jako klient (viz předchozí ukázka kódu).  
  
- To musí být <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> provedeno dříve, než se nazývá. V této ukázce ukážeme, jak je <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>modul vzorníku ručně upraven před voláním . Dalším způsobem, jak dosáhnout stejné věci, <xref:System.ServiceModel.ServiceHost> je odvodit třídu, ze které je volání `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` před otevřením (viz hosting dokumentace a ukázky pro příklady).  
  
### <a name="user-experience"></a>Uživatelské prostředí  
 Na serveru:  
  
- Implementace `ICalculator` serveru není nutné měnit.  
  
- Nástroj App.config pro službu musí používat vlastní `messageVersion` vazbu `textMessageEncoding` POX, která nastaví atribut prvku na `None`.  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="poxBinding">  
          <textMessageEncoding messageVersion="None" />  
          <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
- App.config pro službu také musí `EnableHttpGetRequestsBehavior` zadat vlastní přidáním do oddílu rozšíření chování a jeho použití.  
  
    ```xml  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="enableHttpGetRequestsBehavior">  
          <enableHttpGetRequests />  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  
    <extensions>  
      <behaviorExtensions>  
        <!-- Enabling HTTP GET requests: Behavior Extension -->  
        <add
          name="enableHttpGetRequests"           type="Microsoft.ServiceModel.Samples.EnableHttpGetRequestsBehaviorElement, QueryStringFormatter, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </behaviorExtensions>  
    </extensions>  
    ```  
  
- Přidat operace formatters <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>před voláním .  
  
 Na straně klienta:  
  
- Implementace klienta není nutné změnit.  
  
- Nástroj App.config pro klienta musí používat vlastní `messageVersion` vazbu `textMessageEncoding` POX, která nastaví atribut prvku na `None`. Jeden rozdíl od služby je, že klient musí povolit ruční adresování tak, aby odchozí adresa může být změněna.  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="poxBinding">  
          <textMessageEncoding messageVersion="None" />  
          <httpTransport manualAddressing="True" />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
- Nástroj App.config pro klienta musí `EnableHttpGetRequestsBehavior` zadat stejný vlastní jako server.  
  
- Přidat operace formatters <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>před voláním .  
  
 Při spuštění ukázky jsou v okně klientské konzole zobrazeny požadavky na operaci a odpovědi. Všechny čtyři operace (Přidat, Odečíst, Násobit a Rozdělit) musí být úspěšné.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Formatters\QueryStringFormatter`  
  
##### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
