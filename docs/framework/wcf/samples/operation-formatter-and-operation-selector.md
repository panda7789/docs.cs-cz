---
title: Formátovací modul a selektor operace
ms.date: 03/30/2017
ms.assetid: 1c27e9fe-11f8-4377-8140-828207b98a0e
ms.openlocfilehash: a814de7433f2d06491245dc1d6e6e637b514118a
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/16/2018
ms.locfileid: "45666925"
---
# <a name="operation-formatter-and-operation-selector"></a>Formátovací modul a selektor operace
Tato ukázka předvádí, jak lze umožňující data zprávy v jiném formátu z co WCF očekává, že body rozšiřitelnosti Windows Communication Foundation (WCF). Ve výchozím nastavení, formátování WCF očekávat parametry metody mají být zahrnuty v části `soap:body` elementu. Vzorek ukazuje, jak implementovat vlastní operace formátování, které místo toho analyzuje data parametrů z řetězce dotazu HTTP GET a volá metody pomocí tato data.  
  
 Vzorek je založen na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), která implementuje `ICalculator` kontrakt služby. To ukazuje, jak přidat, odečte krát a dělení zprávy lze změnit na požadavky klienta na server pomocí HTTP GET a HTTP POST s POX zprávy pro server klient odpovědi.  
  
 Uděláte to tak, ukázka poskytuje následující:  
  
-   `QueryStringFormatter`, která implementuje <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> a <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> pro klienta a serveru, v uvedeném pořadí a zpracovává data v řetězci dotazu.  
  
-   `UriOperationSelector`, která implementuje <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> na serveru k provedení operace odeslání podle názvu operace v požadavek GET.  
  
-   `EnableHttpGetRequestsBehavior` konfigurace koncového bodu chování (a odpovídající), který modulu runtime přidá selektor potřebné operace.  
  
-   Ukazuje, jak vložit nový formátovací modul operace do modulu runtime.  
  
-   V této ukázce jsou klient a služba konzolové aplikace (.exe).  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
## <a name="key-concepts"></a>Klíčové koncepty  
 `QueryStringFormatter` -Operace formátování je součástí WCF, který je zodpovědný za převod zprávu do pole parametru objekty a pole objektů parametr do zprávy. To se provádí na straně klienta pomocí <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> rozhraní a na serveru se službou <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> rozhraní. Tato rozhraní umožňují uživatelům získat zprávy požadavků a odpovědí z `Serialize` a `Deserialize` metody.  
  
 V této ukázce `QueryStringFormatter` implementuje oba z těchto rozhraní a je implementována v klientem a serverem.  
  
 Žádost:  
  
-   Ukázka používá <xref:System.ComponentModel.TypeConverter> třída převést parametr data ve zprávě požadavku do a z řetězce. Pokud <xref:System.ComponentModel.TypeConverter> není k dispozici pro konkrétní typ, vyvolá formátování ukázka výjimku.  
  
-   V `IClientMessageFormatter.SerializeRequest` metody na straně klienta, formátovací modul vytváří identifikátor URI s příslušnou adresu a přidá název operace jako příponu. Tento název se používá k odeslání do příslušné operace na serveru. Potom přijímá pole objektů parametr a serializuje data parametru řetězce dotazu URI pomocí názvy parametrů a hodnot pomocí převedeny <xref:System.ComponentModel.TypeConverter> třídy. <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> a <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> vlastnosti jsou pak nastavte na tento identifikátor URI. <xref:System.ServiceModel.Channels.MessageProperties> je přístupný prostřednictvím <xref:System.ServiceModel.Channels.Message.Properties%2A> vlastnost.  
  
-   V `IDispatchMessageFormatter.DeserializeRequest` načte formátovací modul metoda na serveru, `Via` identifikátor URI ve vlastnostech příchozí zprávy požadavku. Analyzuje dvojice název hodnota v řetězci dotazu identifikátoru URI do názvy parametrů a hodnot a využije názvy parametrů a hodnoty k vyplnění pole parametry předané do metody. Všimněte si, že operace odeslání již došlo, tak v této metodě se ignoruje přípona názvu operace.  
  
 Odpověď:  
  
-   V této ukázce GET protokolu HTTP se používá pouze pro daný požadavek. Formátovací modul delegátů, odeslání odpovědi na původní formátovací modul, který by byl použit ke generování hlášení XML. Jedním z cílů tohoto příkladu je zobrazit, jak je možné implementovat Delegující formátování.  
  
### <a name="uripathsuffixoperationselector-class"></a>Třída UriPathSuffixOperationSelector  
 <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> Rozhraní umožňuje uživatelům implementovat své vlastní logiky, které operace by měla konkrétní zpráva odeslána.  
  
 V této ukázce `UriPathSuffixOperationSelector` musí implementovat na server vybrat příslušnou operaci, protože název operace je součástí identifikátoru URI HTTP GET, spíše než hlavičku akce ve zprávě. Ukázka je nastavit a povolit pouze malá a velká písmena operace názvy.  
  
 `SelectOperation` Metoda přijímá příchozí zprávy a vyhledá `Via` identifikátor URI ve vlastnostech zprávy. Extrahuje příponu názvu operace z identifikátoru URI, vyhledá a získat tak název operace, které zpráva by měla být odesláno do interní tabulku a vrátí název této operace.  
  
### <a name="enablehttpgetrequestsbehavior-class"></a>Třída EnableHttpGetRequestsBehavior  
 `UriPathSuffixOperationSelector` Komponenty lze nastavit programově nebo prostřednictvím chování koncového bodu. Ukázka implementuje `EnableHttpGetRequestsBehavior` chování, které je určeno v konfiguračním souboru aplikace služby.  
  
 Na serveru:  
  
 <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> Nastavena <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementace.  
  
 Ve výchozím nastavení používá WCF filtr adresy přesnou shodu. Identifikátor URI v příchozí zprávě obsahuje příponou název operace, za nímž následuje řetězec dotazu, který obsahuje data parametrů, takže chování koncového bodu se také změní filtr adres bude předpony, které odpovídají filtru. Používá WCF<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> pro tento účel.  
  
### <a name="installing-operation-formatters"></a>Instalace operace formátování  
 Chování operace, které zadejte formátovací moduly jsou jedinečné. Jeden takový chování je vždy implementováno ve výchozím nastavení pro každou operaci vytvoření nezbytných formátovací modul. Ale těchto projevů vypadat podobně jako jakékoli jiné chování operace; nejsou poznáte ho podle jiného atributu. Náhradní chování instalace, implementace musí vyhledat konkrétní formátovací modul chování, které jsou nainstalované ve WCF typ zavaděč ve výchozím nastavení a buď ji nahradit nebo přidat kompatibilní chování následný výchozí chování.  
  
 Tyto operace formátování chování lze nastavit programově před voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> nebo zadáním na operaci chování, která se spustí po výchozí hodnotu. Však ho nelze snadno nastavit pomocí chování koncového bodu (a tedy konfigurace) protože model chování nepovoluje chování a nahraďte Další chování nebo jinak upravit stromu popis.  
  
 Na straně klienta:  
  
 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> Implementace musí být implementované tak, aby ho převést požadavky na požadavky HTTP GET a delegovat na původní formátování odpovědi. To se provádí pomocí volání `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` Pomocná metoda.  
  
 To je nutné provést před voláním `CreateChannel`.  
  
```  
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
  
-   <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> Musí implementovat rozhraní, tak, aby může číst požadavky HTTP GET a delegovat na původní formátovací modul pro psaní odpovědi. To se provádí voláním stejné `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` pomocnou metodu jako klient (viz předchozí ukázka kódu).  
  
-   To je nutné provést před <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> je volána. V tomto příkladu vám ukážeme, jak formátovací modul ručně změnit před voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. Jiný způsob, jak dosáhnout stejnou věc je na odvození třídy z <xref:System.ServiceModel.ServiceHost> , která provádí volání na `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` před otevřením (podrobnosti najdete na hostování dokumentaci a ukázky pro příklady).  
  
### <a name="user-experience"></a>Činnost koncového uživatele  
 Na serveru:  
  
-   Server `ICalculator` implementace není potřeba změnit.  
  
-   App.config pro službu, musíte použít vlastní POX vazby, který nastaví `messageVersion` atribut `textMessageEncoding` elementu `None`.  
  
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
  
-   Souboru App.config pro službu musíte zadat také vlastní `EnableHttpGetRequestsBehavior` přidáním do oddílu rozšíření chování a jeho použití.  
  
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
  
-   Přidání operace formátování před voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.  
  
 Na straně klienta:  
  
-   Implementace klienta není potřeba změnit.  
  
-   App.config pro klienta, musíte použít vlastní POX vazby, který nastaví `messageVersion` atribut `textMessageEncoding` elementu `None`. Jedním z rozdílů ze služby je, že klient musí povolit ruční adresování tak, aby odesílaných na adresu je možné upravit.  
  
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
  
-   Souboru App.config pro klienta, musíte zadat stejné vlastní `EnableHttpGetRequestsBehavior` jako server.  
  
-   Přidání operace formátování před voláním <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>.  
  
 Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta. Všechny čtyři operace (přidat, odečítání, násobení a rozdělit) musí být úspěšný.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Formatters\QuieryStringFormatter`  
  
##### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Viz také
