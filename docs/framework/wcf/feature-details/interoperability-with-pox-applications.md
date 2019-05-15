---
title: Vzájemná funkční spolupráce s aplikacemi POX
ms.date: 03/30/2017
ms.assetid: 449276b8-4633-46f0-85c9-81f01d127636
ms.openlocfilehash: 17b85ab41589a130e950cd52c759305cc17e92b7
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591045"
---
# <a name="interoperability-with-pox-applications"></a>Vzájemná funkční spolupráce s aplikacemi POX

"Plain Old XML" (POX) aplikace komunikovat výměnou nezpracované zprávy protokolu HTTP, které obsahují pouze data aplikací XML, která není uzavřen v rámci obálky protokolu SOAP. Windows Communication Foundation (WCF) můžete poskytovat služby a klienti, kteří používají POX zprávy. Ve službě je možné k implementaci služeb, které zpřístupňují koncové body pro klienty, například webových prohlížečů a skriptovací jazyky, které odesílání a příjem zpráv POX WCF. Na straně klienta je možné implementovat klienty, kteří komunikují se službami na základě POX programovacího modelu WCF.  
  
> [!NOTE]
> Tento dokument byl původně zapsán pro rozhraní .NET Framework 3.0.  Rozhraní .NET framework 3.5 obsahuje integrovanou podporu pro práci s aplikacemi POX. Další informace o najdete v tématu [WCF Web HTTP programovací Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md).
  
## <a name="pox-programming-with-wcf"></a>POX programování s použitím technologie WCF

Služby WCF, které komunikují prostřednictvím protokolu HTTP použijte POX zprávy [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).

```xml
<customBinding>
   <binding name="poxServerBinding">
       <textMessageEncoding messageVersion="None" />
       <httpTransport />
   </binding>
</customBinding>
```

Tato vlastní vazba obsahuje dva prvky:

- [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md)

- [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md)

Standardní kodér textu zprávy WCF je speciálně nakonfigurován pro použití <xref:System.ServiceModel.Channels.MessageVersion.None%2A> hodnotu, která umožňuje zpracování XML zprávy datových částí, které přicházejí nejsou zabaleny v obálce SOAP.

Klienti WCF, které komunikují prostřednictvím protokolu HTTP POX zprávy použijte podobně jako vazbu (viz následující imperativního kódu).

```csharp
private static Binding CreatePoxBinding()
{
    TextMessageEncodingBindingElement encoder =
        new TextMessageEncodingBindingElement( MessageVersion.None, Encoding.UTF8 );
    HttpTransportBindingElement transport = new HttpTransportBindingElement();
    transport.ManualAddressing = true;
    return new CustomBinding( new BindingElement[] { encoder, transport } );
}
```

Vzhledem k tomu POX klienty musíte explicitně zadat identifikátory URI, na který odesílají zprávy, se obvykle musí nakonfigurovat <xref:System.ServiceModel.Channels.HttpTransportBindingElement> k ruční režim adresování tak, že nastavíte <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> vlastnost `true` u elementu. To umožňuje zprávy bylo nutné řešit explicitně kód aplikace a není nutné vytvořit novou <xref:System.ServiceModel.ChannelFactory> pokaždé, když aplikace odešle zprávu do jiný identifikátor URI HTTP.

Protože POX zprávy nepoužívejte k předání informací důležité protokolu SOAP záhlaví, POX klienty a služby často manipulovat kusy podkladový požadavek HTTP, který se použije k odeslání nebo přijetí zprávy. Protokol HTTP konkrétní informace, jako jsou hlavičky protokolu HTTP a stavové kódy jsou prezentované v programovacího modelu WCF pomocí dvou tříd:

- <xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, který obsahuje informace o požadavku HTTP, jako jsou metody a žádost o hlavičky protokolu HTTP.

- <xref:System.ServiceModel.Channels.HttpResponseMessageProperty>, který obsahuje informace odpovědi HTTP, jako je například popis stavu HTTP kódu a stav, stejně jako všechny hlavičky odpovědí HTTP.
  
Následující příklad kódu ukazuje, jak vytvořit požadavku HTTP GET, adresovanou `http://localhost:8100/customers`.

```csharp
Message request = Message.CreateMessage( MessageVersion.None, String.Empty );
request.Headers.To = "http://localhost:8100/customers";

HttpRequestMessageProperty property = new HttpRequestMessageProperty();
property.Method = "GET";
property.SuppressEntityBody = true;
request.Properties.Add( HttpRequestMessageProperty.Name, property );
```

První, žádost o vyprázdnění <xref:System.ServiceModel.Channels.Message> je vytvořen zavoláním <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29>. <xref:System.ServiceModel.Channels.MessageVersion.None%2A> Parametr se používá k označení, že není potřeba obálku protokolu SOAP a <xref:System.String.Empty> parametr se předává jako akce. Zprávy s požadavkem je pak určena nastavením <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> záhlaví na požadovaný identifikátor URI. Další <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> se vytvoří a <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> je nastavena na příkaz HTTP GET metody a <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> je nastavena na `true` k označení, že by se posílat žádná data v těle odchozí zpráva požadavku HTTP. Nakonec je přidána vlastnost požadavek <xref:System.ServiceModel.Channels.Message.Properties%2A> kolekce zprávy s požadavkem, může ovlivnit, jak přenos pomocí protokolu HTTP odesílá požadavek. Zprávu je připravený k odeslání přes příslušné instanci <xref:System.ServiceModel.Channels.IRequestChannel>.

Podobné techniky slouží ve službě k extrakci <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> z k příchozí zprávě a konstrukce odpověď.
