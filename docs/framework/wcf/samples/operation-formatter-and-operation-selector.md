---
title: "Formátovací modul a selektor operace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c27e9fe-11f8-4377-8140-828207b98a0e
caps.latest.revision: "19"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c0e2dbd255a1fbadbd5dd4cd7e676b75e659fe2a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="operation-formatter-and-operation-selector"></a>Formátovací modul a selektor operace
Tento příklad ukazuje, jak [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] body rozšiřitelnosti lze povolit data zpráv do jiného formátu z co [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] očekává. Ve výchozím nastavení [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] formátování očekávat parametry metody, které mají být zahrnuty v části `soap:body` elementu. Ukázka ukazuje, jak implementovat vlastní operaci formátování, které analyzuje data parametr z řetězce dotazu HTTP GET místo a vyvolá metody pomocí tato data.  
  
 Ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), který implementuje `ICalculator` kontrakt služby. Ho ukazuje, jak přidat, odečíst násobkem a dělení zprávy můžete změnit tak, aby požadavky klienta na server pomocí metody GET protokolu HTTP a HTTP POST s POX zprávy pro klienta a serveru odpovědi.  
  
 Uděláte to tak, ukázka poskytuje následující:  
  
-   `QueryStringFormatter`, který implementuje <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> a <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> pro klienta a serveru, v uvedeném pořadí a zpracovává data v řetězci dotazu.  
  
-   `UriOperationSelector`, který implementuje <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> na serveru k provedení operace odesílání na základě názvu operace v požadavek GET.  
  
-   `EnableHttpGetRequestsBehavior`koncový bod chování (a odpovídající konfigurace), k modulu runtime přidává selektor potřebné operace.  
  
-   Ukazuje, jak nové formátování operaci vložení do modulu runtime.  
  
-   V této ukázce klienta a služby jsou konzolové aplikace (.exe).  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
## <a name="key-concepts"></a>Klíčové koncepty  
 `QueryStringFormatter`-Formátovací modul je součástí v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] který zodpovídá za převodu zprávy na pole objektů parametr a pole objektů parametr do zprávy. To se provádí na straně klienta pomocí <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> rozhraní a na serveru s <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> rozhraní. Povolit uživatelům získat zprávy požadavku a odpovědi z těchto rozhraní `Serialize` a `Deserialize` metody.  
  
 V této ukázce `QueryStringFormatter` implementuje obě tato rozhraní a je implementována na klientovi a serveru.  
  
 Žádost:  
  
-   Ukázce se používá <xref:System.ComponentModel.TypeConverter> – třída parametru data ve zprávě požadavku převést do a z řetězce. Pokud <xref:System.ComponentModel.TypeConverter> není k dispozici pro konkrétní typ, vrátí formátování ukázka výjimku.  
  
-   V `IClientMessageFormatter.SerializeRequest` metody na straně klienta, formátování vytvoří identifikátor URI s příslušnou adresu a připojí název operace jako příponu. Tento název se používá k odeslání do příslušné operaci na serveru. Potom provede pole objektů parametr a serializuje data parametru řetězce dotazu identifikátoru URI pomocí názvy parametrů a hodnot pomocí převedeny <xref:System.ComponentModel.TypeConverter> třídy. <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> a <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> vlastností pak nastavení tento identifikátor URI. <xref:System.ServiceModel.Channels.MessageProperties>je přístupné přes <xref:System.ServiceModel.Channels.Message.Properties%2A> vlastnost.  
  
-   V `IDispatchMessageFormatter.DeserializeRequest` načte formátovací modul metoda na serveru, `Via` URI ve vlastnostech příchozí zpráva požadavku. Ho analyzuje dvojice název hodnota v řetězci dotazu identifikátoru URI do názvy parametrů a hodnoty a využije k vyplnění pole parametry předané do metodu názvy parametrů a hodnoty. Všimněte si, že operace odesílání již došlo, proto je přípona názvu operaci je ignorován v této metodě.  
  
 Odpověď:  
  
-   V této ukázce metody GET protokolu HTTP se používá pouze pro požadavek. Formátovací modul deleguje odesílání odpovědi na původní formátovací modul, který by byl použit ke generování zprávu XML. Jedním z cílů tohoto příkladu je zobrazit, jak se dají implementovat delegování formátování.  
  
### <a name="uripathsuffixoperationselector-class"></a>UriPathSuffixOperationSelector – třída  
 <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> Rozhraní umožňuje uživatelům implementovat vlastní logiku, pro kterou operaci by měl určitou zprávu odeslat.  
  
 V této ukázce `UriPathSuffixOperationSelector` na serveru a vyberte příslušnou operaci, protože název operace je obsažena v identifikátoru URI HTTP GET, nikoli hlavičku akce ve zprávě, musí být implementována. Ukázka je nastavit a Povolit jenom velká a malá písmena operaci názvy.  
  
 `SelectOperation` Metoda přijímá příchozí zprávy a vyhledá `Via` URI v vlastností. Extrahuje příponu názvu operace z identifikátoru URI, vyhledává interní tabulku se získat název operace, který by měl být odeslaných zprávu a vrátí název této operace.  
  
### <a name="enablehttpgetrequestsbehavior-class"></a>EnableHttpGetRequestsBehavior – třída  
 `UriPathSuffixOperationSelector` Součást se dá nastavit prostřednictvím kódu programu, nebo prostřednictvím chování koncového bodu. Ukázka implementuje `EnableHttpGetRequestsBehavior` chování, který je uveden v konfiguračním souboru aplikace služby.  
  
 Na serveru:  
  
 <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> Je nastaven na <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementace.  
  
 Ve výchozím nastavení [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] používá filtr adres přesnou shodu. Identifikátor URI na příchozí zpráva obsahuje příponu názvu operaci následuje řetězec dotazu, který obsahuje parametr data, takže chování koncového bodu také změní filtr adres jako předponu odpovídají filtru. Použije [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> pro tento účel.  
  
### <a name="installing-operation-formatters"></a>Instalace operace formátování  
 Operace chování, které určují formátovací moduly jsou jedinečné. Jeden takové chování je vždy implementováno ve výchozím nastavení pro každou operaci vytvoření formátování potřebné operace. Ale tyto chování vypadat podobně jako jakékoli jiné operace chování; nejsou osobní jiných atributem. K instalaci nahrazení chování, implementace vyhledejte konkrétní formátování chování, které jsou nainstalované ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] typ zavaděč ve výchozím nastavení a nahraďte ji nebo přidat kompatibilní chování má spustit po výchozí chování.  
  
 Tyto operace formátování chování se dá nastavit prostřednictvím kódu programu před voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> nebo zadáním operaci chování, které se spustí až po výchozí nastavení. Ale ji nelze snadno nastavit tak, že chování koncového bodu (a proto konfigurace) protože modelu chování neumožňuje chování k upravit popis stromové struktuře a nahradit jiného chování.  
  
 Na straně klienta:  
  
 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> Implementace, musí být implementována, aby mohli převést požadavky na požadavky HTTP GET a delegovat na původní formátování odpovědi. To se provádí volání `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` metodu helper.  
  
 To je třeba provést před voláním `CreateChannel`.  
  
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
  
-   <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> Rozhraní musí být implementována, aby mohli číst požadavky HTTP GET a delegovat na původní formátovací modul pro zápis odpovědi. To se provádí volání stejné `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` Pomocná metoda jako klient (viz předchozí ukázka kódu).  
  
-   To je třeba provést před <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> je volána. V této ukázce ukážeme, jak je ručně změnit formátování před voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. Jiný způsob, jak dosáhnout samé je na odvození třídy z <xref:System.ServiceModel.ServiceHost> který zpřístupňuje volání `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` před otevřením (viz prosím hostování dokumentace a ukázky příklady).  
  
### <a name="user-experience"></a>Činnost koncového uživatele  
 Na serveru:  
  
-   Server `ICalculator` implementace není potřeba změnit.  
  
-   App.config služby musíte použít vlastní POX vazby, která nastavuje `messageVersion` atribut `textMessageEncoding` element `None`.  
  
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
  
-   App.config pro službu musíte zadat také vlastní `EnableHttpGetRequestsBehavior` tak, že ho přidáte do části rozšíření chování a jeho použití.  
  
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
  
-   Přidání formátovacích modulů operaci před voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.  
  
 Na straně klienta:  
  
-   Implementace klienta není potřeba změnit.  
  
-   App.config pro klienta, musíte použít vlastní POX vazby, která nastavuje `messageVersion` atribut `textMessageEncoding` element `None`. Jeden rozdíl ze služby je, že klient musí povolit ruční adresování tak, aby odchozí adresu můžete upravit.  
  
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
  
-   App.config pro klienta, musíte zadat stejné vlastní `EnableHttpGetRequestsBehavior` jako server.  
  
-   Přidání formátovacích modulů operaci před voláním <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>.  
  
 Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta. Všechny čtyři operace (přidat, odečíst, násobení a dělení) musí být úspěšné.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Formatters\QuieryStringFormatter`  
  
##### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Viz také
