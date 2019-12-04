---
title: Formátovací modul a selektor operace
ms.date: 03/30/2017
ms.assetid: 1c27e9fe-11f8-4377-8140-828207b98a0e
ms.openlocfilehash: 64f2d807946d5365c01cd1a46488c868ebc603ac
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714645"
---
# <a name="operation-formatter-and-operation-selector"></a>Formátovací modul a selektor operace
Tento příklad ukazuje, jak lze použít body rozšiřitelnosti Windows Communication Foundation (WCF) k povolení dat zprávy v jiném formátu, od kterého očekává WCF. Ve výchozím nastavení očekávají formátovací moduly WCF parametry metody, které mají být zahrnuty do prvku `soap:body`. Ukázka ukazuje, jak implementovat vlastní formátovací modul operace, který analyzuje data parametrů z řetězce dotazu HTTP GET a vyvolává metody používající tato data.  
  
 Ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), která implementuje kontrakt služby `ICalculator`. Zobrazuje způsob, jakým se dají zprávy přidat, odečíst, násobit a rozdělit použít k použití HTTP GET pro požadavky klienta na server a HTTP POST se POX zprávami pro odpovědi ze serveru na klienta.  
  
 V takovém případě ukázka poskytuje následující:  
  
- `QueryStringFormatter`, která implementuje <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> a <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> pro klienta a server, v uvedeném pořadí a zpracovává data v řetězci dotazu.  
  
- `UriOperationSelector`, která implementuje <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> na serveru k provedení odeslání operace na základě názvu operace v žádosti o získání.  
  
- chování koncového bodu `EnableHttpGetRequestsBehavior` (a odpovídající konfigurace), které do modulu runtime přidává potřebný selektor operací.  
  
- Ukazuje, jak vložit nový formátovací modul operace do modulu runtime.  
  
- V této ukázce je klient i služba Konzolová aplikace (. exe).  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
## <a name="key-concepts"></a>Klíčové koncepty  
 `QueryStringFormatter` – formátovací modul operace je součást služby WCF, která je odpovědná za převod zprávy na pole objektů parametrů a pole objektů parametrů do zprávy. To se provádí na klientovi pomocí rozhraní <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> a na serveru s rozhraním <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>. Tato rozhraní umožňují uživatelům získat zprávy žádosti a odpovědi z `Serialize` a `Deserialize`ch metod.  
  
 V této ukázce `QueryStringFormatter` implementuje obě tato rozhraní a je implementována na straně klienta a serveru.  
  
 Request  
  
- Ukázka používá třídu <xref:System.ComponentModel.TypeConverter> pro převod dat parametrů ve zprávě požadavku na a z řetězců. Pokud <xref:System.ComponentModel.TypeConverter> není pro určitý typ k dispozici, vygeneruje vzorový modul formátování výjimku.  
  
- V metodě `IClientMessageFormatter.SerializeRequest` v klientovi modul formátování vytvoří identifikátor URI s odpovídajícími adresami pro adresu a připojí název operace jako příponu. Tento název slouží k odeslání na příslušnou operaci na serveru. Pak převezme pole objektů parametrů a serializace data parametrů do řetězce dotazu identifikátoru URI pomocí názvů parametrů a hodnot převedených pomocí <xref:System.ComponentModel.TypeConverter> třídy. Vlastnosti <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> a <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> pak jsou nastaveny na tento identifikátor URI. k <xref:System.ServiceModel.Channels.MessageProperties> je k dispozici prostřednictvím vlastnosti <xref:System.ServiceModel.Channels.Message.Properties%2A>.  
  
- V metodě `IDispatchMessageFormatter.DeserializeRequest` na serveru načte formátovací modul `Via` identifikátor URI ve vlastnostech zprávy příchozího požadavku. Analyzuje páry název-hodnota v řetězci dotazu URI na názvy parametrů a hodnoty a používá názvy parametrů a hodnoty k naplnění pole parametrů předaných metodě. Všimněte si, že operace odeslání operace již proběhla, takže se v této metodě ignoruje přípona názvu operace.  
  
 Základě  
  
- V této ukázce se HTTP GET používá jenom pro požadavek. Formátovací modul deleguje odeslání odpovědi do původního formátovacího modulu, který by byl použit k vygenerování zprávy XML. Jedním z cílů této ukázky je Ukázat, jak se dá implementovat takový formátovací modul.  
  
### <a name="uripathsuffixoperationselector-class"></a>UriPathSuffixOperationSelector – třída  
 Rozhraní <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> umožňuje uživatelům implementovat svou vlastní logiku, pro kterou operace by měla být odeslána konkrétní zpráva.  
  
 V této ukázce musí být `UriPathSuffixOperationSelector` na serveru implementována, aby bylo možné vybrat příslušnou operaci, protože název operace je obsažen v identifikátoru URI požadavku HTTP, nikoli jako záhlaví akce ve zprávě. Ukázka je nastavena tak, aby povolovala pouze názvy operací nerozlišující malá a velká písmena.  
  
 Metoda `SelectOperation` přijímá příchozí zprávu a vyhledává identifikátor URI `Via` ve vlastnostech zprávy. Extrahuje příponu názvu operace z identifikátoru URI, vyhledá interní tabulku, aby získala název operace, na kterou by měla být zpráva odeslána, a vrátí tento název operace.  
  
### <a name="enablehttpgetrequestsbehavior-class"></a>EnableHttpGetRequestsBehavior – třída  
 Komponentu `UriPathSuffixOperationSelector` lze nastavit programově nebo prostřednictvím chování koncového bodu. Ukázka implementuje chování `EnableHttpGetRequestsBehavior`, které je zadáno v konfiguračním souboru aplikace služby.  
  
 Na serveru:  
  
 <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> je nastavená na implementaci <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector>.  
  
 Ve výchozím nastavení používá WCF Filtr adres přesně podle potřeby. Identifikátor URI příchozí zprávy obsahuje příponu názvu operace následovaný řetězcem dotazu, který obsahuje data parametrů, takže chování koncového bodu také změní Filtr adres tak, aby byl filtrem shody předpon. Pro tento účel používá<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> WCF.  
  
### <a name="installing-operation-formatters"></a>Instalace formátovacích modulů operací  
 Chování operací, které určují formátovací modul, je jedinečné. Toto chování je vždy implementováno ve výchozím nastavení pro každou operaci pro vytvoření formátovacího modulu nezbytné operace. Toto chování ale vypadá stejně jako jiné chování operace; nelze je identifikovat žádným jiným atributem. Chcete-li nainstalovat náhradní chování, implementace musí vyhledat specifické chování formátovacího modulu, které jsou ve výchozím nastavení nainstalovány nástrojem WCF Type Loader, a buď ho nahradit, nebo přidat kompatibilní chování, které se spustí po výchozím chování.  
  
 Chování těchto formátovacích funkcí operací lze nastavit programově před voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> nebo zadáním chování operace, která se spustí po výchozím nastavení. Nelze jej však snadno nastavit pomocí chování koncového bodu (a proto podle konfigurace), protože model chování neumožňuje chování nahradit jiná chování nebo jinak upravovat strom popisů.  
  
 Na klientovi:  
  
 Implementace <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> musí být implementovaná tak, aby mohla převádět požadavky na požadavky HTTP GET a delegovat na původní formátovací modul pro odpovědi. To se provádí voláním pomocné metody `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior`.  
  
 To je nutné provést před voláním `CreateChannel`.  
  
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
  
- Rozhraní <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> musí být implementováno, aby mohl číst požadavky HTTP GET a delegovat na původní formátovací modul pro psaní odpovědí. To se provádí voláním stejné pomocné metody `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` jako klienta (viz předchozí ukázka kódu).  
  
- To je nutné provést před voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. V této ukázce ukážeme, jak je formátovací modul ručně změněn před voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. Dalším způsobem, jak dosáhnout stejného účelu, je odvodit třídu z <xref:System.ServiceModel.ServiceHost>, která provádí volání `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` před otevřením (příklady najdete v dokumentaci k hostování a ukázky).  
  
### <a name="user-experience"></a>Činnost koncového uživatele  
 Na serveru:  
  
- Implementace `ICalculator` serveru se nemusí měnit.  
  
- Soubor App. config pro službu musí používat vlastní vazbu POX, která nastaví atribut `messageVersion` `textMessageEncoding` elementu na `None`.  
  
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
  
- Soubor App. config pro službu musí také určovat vlastní `EnableHttpGetRequestsBehavior` tím, že ho přidáte do části rozšíření chování a použijete ho.  
  
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
  
- Přidejte formátovací modul operací před voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.  
  
 Na klientovi:  
  
- Implementace klienta se nemusí měnit.  
  
- Soubor App. config pro klienta musí používat vlastní vazbu POX, která nastaví atribut `messageVersion` `textMessageEncoding` elementu na `None`. Jedním z rozdílů od služby je, že klient musí povolit ruční adresování, aby bylo možné upravit adresu odchozí na.  
  
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
  
- Soubor App. config pro klienta musí určovat stejný vlastní `EnableHttpGetRequestsBehavior` jako server.  
  
- Přidejte formátovací modul operací před voláním <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>.  
  
 Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi. Všechny čtyři operace (sčítání, odčítání, násobení a dělení) musí být úspěšné.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Formatters\QueryStringFormatter`  
  
##### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
