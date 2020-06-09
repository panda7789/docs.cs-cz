---
title: Interoperabilita s aplikacemi POX
ms.date: 03/30/2017
ms.assetid: 449276b8-4633-46f0-85c9-81f01d127636
ms.openlocfilehash: 64a6d850a32b14bc60cd43466e04b53a7a39be81
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579264"
---
# <a name="interoperability-with-pox-applications"></a>Interoperabilita s aplikacemi POX

"Obyčejné staré aplikace XML" (POX) komunikují výměnou nezpracovaných zpráv HTTP, které obsahují jenom data aplikace XML, která nejsou uzavřená v obálce protokolu SOAP. Windows Communication Foundation (WCF) může poskytovat služby i klienty, kteří používají zprávy POX. Ve službě lze WCF použít k implementaci služeb, které zpřístupňují koncové body klientům, jako jsou webové prohlížeče a skriptovací jazyky, které odesílají a získávají zprávy POX. Na straně klienta lze použít programovací model WCF k implementaci klientů, kteří komunikují se službami založeným na POX.  
  
> [!NOTE]
> Tento dokument byl původně napsán pro .NET Framework 3,0.  .NET Framework 3,5 obsahuje integrovanou podporu pro práci s POX aplikacemi. Další informace najdete v tématu [model programování webového protokolu HTTP WCF](wcf-web-http-programming-model.md).
  
## <a name="pox-programming-with-wcf"></a>POX programování pomocí WCF

Služby WCF, které komunikují přes protokol HTTP pomocí zpráv POX, používají [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) .

```xml
<customBinding>
   <binding name="poxServerBinding">
       <textMessageEncoding messageVersion="None" />
       <httpTransport />
   </binding>
</customBinding>
```

Tato vlastní vazba obsahuje dva prvky:

- [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md)

- [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md)

Standardní kodér textových zpráv WCF je speciálně nakonfigurován tak, aby používal <xref:System.ServiceModel.Channels.MessageVersion.None%2A> hodnotu, což umožňuje zpracovat datové části zpráv XML, které nepřicházejí do obálky protokolu SOAP.

Klienti WCF, kteří komunikují přes HTTP pomocí zpráv POX, používají podobnou vazbu (viz následující imperativní kód).

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

Vzhledem k tomu, že klienti POX musí explicitně zadat identifikátory URI, na které odesílají zprávy, obvykle musí nakonfigurovat <xref:System.ServiceModel.Channels.HttpTransportBindingElement> režim ruční adresování nastavením vlastnosti na hodnotu <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> `true` elementu. To umožňuje, aby zprávy byly explicitně řešeny kódem aplikace a není nutné vytvářet nové, <xref:System.ServiceModel.ChannelFactory> kdykoli aplikace odešle zprávu na jiný identifikátor URI protokolu HTTP.

Vzhledem k tomu, že zprávy POX nepoužívají hlavičky protokolu SOAP k předávání důležitých informací o protokolu, musí klienti a služby POX často manipulovat s částmi základní žádosti HTTP použitou k odeslání nebo přijetí zprávy. Informace protokolu specifické pro protokol HTTP, jako jsou hlavičky protokolu HTTP a stavové kódy, jsou umístěny v programovacím modelu WCF prostřednictvím dvou tříd:

- <xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, který obsahuje informace o požadavku HTTP, jako je například metoda HTTP a Hlavička požadavku.

- <xref:System.ServiceModel.Channels.HttpResponseMessageProperty>, který obsahuje informace o odpovědi HTTP, například stavový kód HTTP a popis stavu a také všechny hlavičky odpovědí HTTP.
  
Následující příklad kódu ukazuje, jak vytvořit zprávu požadavku HTTP GET, která je adresována na `http://localhost:8100/customers` .

```csharp
Message request = Message.CreateMessage( MessageVersion.None, String.Empty );
request.Headers.To = "http://localhost:8100/customers";

HttpRequestMessageProperty property = new HttpRequestMessageProperty();
property.Method = "GET";
property.SuppressEntityBody = true;
request.Properties.Add( HttpRequestMessageProperty.Name, property );
```

Nejprve je vytvořen prázdný požadavek <xref:System.ServiceModel.Channels.Message> voláním <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29> . <xref:System.ServiceModel.Channels.MessageVersion.None%2A>Parametr se používá k označení, že obálka SOAP není povinná a <xref:System.String.Empty> jako akce se předává parametr. Zpráva s požadavkem se pak řeší nastavením <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> hlavičky na požadovaný identifikátor URI. Dále <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> je vytvořena a je nastavena na <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> metodu Get příkazu HTTP a <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> je nastavena na hodnotu `true` , která označuje, že v těle zprávy odchozího požadavku HTTP by neměly být odesílána žádná data. Nakonec se do kolekce zprávy požadavku přidá vlastnost Request <xref:System.ServiceModel.Channels.Message.Properties%2A> , aby mohla ovlivnit, jak přenos HTTP posílá požadavek. Zpráva je pak připravena k odeslání prostřednictvím vhodné instance <xref:System.ServiceModel.Channels.IRequestChannel> .

Podobné techniky lze použít na službu k extrakci <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> z příchozí zprávy a vytvoření odpovědi.
