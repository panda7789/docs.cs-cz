---
title: Vzájemná spolupráce s aplikacemi POX
ms.date: 03/30/2017
ms.assetid: 449276b8-4633-46f0-85c9-81f01d127636
ms.openlocfilehash: 7522233723b6b91d5a7b27d3f82ca328e29ce3f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="interoperability-with-pox-applications"></a>Vzájemná spolupráce s aplikacemi POX
"Prostý formát XML" aplikacemi (POX) komunikovat nahrazením nezpracovaná zpráv protokolu HTTP, které obsahují pouze data aplikací XML, který není umístěné do obálky protokolu SOAP. Windows Communication Foundation (WCF) nabízejí služby a klienti, kteří používají POX zprávy. Ve službě slouží k implementaci služeb, které zveřejňují koncové body pro klienty, například webové prohlížeče a skriptovací jazyky, které odesílat a přijímat zprávy POX WCF. Na straně klienta programovací model WCF slouží k implementaci klientů komunikujících s služeb založených na POX.  
  
> [!NOTE]
>  Tento dokument byl původně zapsán pro [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0.  [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.5 má integrovanou podporu pro práci s aplikacemi POX. Další informace najdete v tématu [WCF Web HTTP programovací Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
  
## <a name="pox-programming-with-wcf"></a>POX programování s použitím technologie WCF  
 Služby WCF, které komunikují přes protokol HTTP pomocí zprávy POX [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
```xml  
<customBinding>  
   <binding name="poxServerBinding">  
       <textMessageEncoding messageVersion="None" />  
       <httpTransport />  
   </binding>  
</customBinding>  
```  
  
 Tato vlastní vazby obsahuje dva elementy:  
  
-   [ \<HttpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) a  
  
-   [ \<TextMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).  
  
 Kodér textu zpráv WCF je speciálně nakonfigurovaný na použití standardu <xref:System.ServiceModel.Channels.MessageVersion.None%2A> hodnotu, která umožňuje zpracovat XML zprávy datové části není přicházející uzavřen do obálky protokolu SOAP.  
  
 Klienti WCF, které komunikují přes protokol HTTP pomocí POX zprávy použít vazbu podobné (viz následující imperativní kód).  
  
```  
private static Binding CreatePoxBinding()  
{  
    TextMessageEncodingBindingElement encoder =   
    new TextMessageEncodingBindingElement( MessageVersion.None, Encoding.UTF8 );  
    HttpTransportBindingElement transport = new HttpTransportBindingElement();  
    transport.ManualAddressing = true;  
    return new CustomBinding( new BindingElement[] { encoder, transport } );  
}   
```  
  
 Protože klienti POX musí explicitně zadat identifikátory URI, na který budou posílat zprávy, se obvykle musíte nakonfigurovat <xref:System.ServiceModel.Channels.HttpTransportBindingElement> na režim ručního adresování nastavením <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> vlastnost `true` v elementu. To umožňuje zprávy explicitně používala kódu aplikace a není nutné vytvořit nový <xref:System.ServiceModel.ChannelFactory> pokaždé, když aplikace odešle zprávu do jiný identifikátor URI HTTP.  
  
 Protože zprávy POX nepoužívají hlavičky SOAP pro vyjádření protokolu důležité informace, často služby a klienti POX upravit kusy základní požadavek HTTP umožňuje odesílat nebo přijímat zprávy. Protokol HTTP specifické informace, jako je záhlaví HTTP a stavové kódy jsou prezentované v programovací model WCF přes dvě třídy:  
  
-   <xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, který obsahuje informace o požadavku HTTP, jako je například metoda a požadavek hlavičky HTTP.  
  
-   <xref:System.ServiceModel.Channels.HttpResponseMessageProperty>, který obsahuje informace o odpovědi HTTP, například popis stav a kód stavu HTTP, stejně jako všechny hlavičky HTTP odpovědi.  
  
 Následující příklad kódu ukazuje, jak vytvořit zprávu požadavku HTTP GET, která je určena http://localhost:8100/customers.  
  
```  
Message request = Message.CreateMessage( MessageVersion.None, String.Empty );  
request.Headers.To = "http://localhost:8100/customers";  
  
HttpRequestMessageProperty property = new HttpRequestMessageProperty();  
property.Method = "GET";  
property.SuppressEntityBody = true;  
request.Properties.Add( HttpRequestMessageProperty.Name, property );  
```  
  
 První, žádost o vyprázdnění <xref:System.ServiceModel.Channels.Message> je vytvořená voláním <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29>. <xref:System.ServiceModel.Channels.MessageVersion.None%2A> Parametr se používá k označení, že není požadováno obálku protokolu SOAP a <xref:System.String.Empty> parametr se předává jako akce. Zpráva požadavku je pak řešit nastavením <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> záhlaví na požadovaný identifikátor URI. Dále <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> je vytvořena a <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> je nastaven na příkazu HTTP metodu GET a <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> je nastaven na `true` indikující, že by měl v těle odchozí zprávy požadavku HTTP odesílána žádná data. Nakonec je do vlastnost požadavku <xref:System.ServiceModel.Channels.Message.Properties%2A> kolekce zprávě požadavku, takže ho mohou mít vliv na to, jak přenos HTTP odešle žádost. Zpráva je pak budou odeslány přes příslušné instanci <xref:System.ServiceModel.Channels.IRequestChannel>.  
  
 Podobné techniky lze ve službě k extrakci <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> ze služby příchozí zprávy a konstrukce odpověď.
