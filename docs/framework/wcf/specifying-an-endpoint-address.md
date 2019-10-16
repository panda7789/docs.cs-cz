---
title: Zadání adresy koncového bodu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], addressing
ms.assetid: ac24f5ad-9558-4298-b168-c473c68e819b
ms.openlocfilehash: 47a7bb42ea2441ffef2fd27f26a20beceb871173
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321137"
---
# <a name="specifying-an-endpoint-address"></a>Zadání adresy koncového bodu

Veškerá komunikace se službou Windows Communication Foundation (WCF) probíhá prostřednictvím svých koncových bodů. Každý <xref:System.ServiceModel.Description.ServiceEndpoint> obsahuje <xref:System.ServiceModel.Description.ServiceEndpoint.Address%2A>, a <xref:System.ServiceModel.Description.ServiceEndpoint.Binding%2A> a <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A>. Kontrakt Určuje, které operace jsou k dispozici. Vazba určuje, jak komunikovat se službou a adresa určuje, kde má být služba nalezena. Každý koncový bod musí mít jedinečnou adresu. Adresa koncového bodu je reprezentována třídou <xref:System.ServiceModel.EndpointAddress>, která obsahuje identifikátor URI (Uniform Resource Identifier), který představuje adresu služby, <xref:System.ServiceModel.EndpointAddress.Identity%2A>, která představuje identitu zabezpečení služby, a kolekci volitelných <xref:System.ServiceModel.EndpointAddress.Headers%2A>. Volitelná záhlaví poskytují podrobnější informace adresování pro identifikaci nebo interakci s koncovým bodem. Například hlavičky mohou označovat, jak zpracovat příchozí zprávu, kde koncový bod by měl poslat zprávu odpovědi, nebo kterou instanci služby použít ke zpracování příchozí zprávy od určitého uživatele, pokud je k dispozici více instancí.

## <a name="definition-of-an-endpoint-address"></a>Definice adresy koncového bodu

V rámci WCF model <xref:System.ServiceModel.EndpointAddress> odkazuje na koncový bod (EPR), jak je definováno ve standardu WS-Addressing.

Identifikátor URI adresy pro většinu přenosů má čtyři části. Například tento identifikátor URI `http://www.fabrikam.com:322/mathservice.svc/secureEndpoint` má následující čtyři části:

- Schéma: http:

- Počítač: `www.fabrikam.com`

- Volitelné Port: 322

- Cesta:/mathservice.svc/secureEndpoint

Součástí modelu EPR je, že každý odkaz na koncový bod může mít několik referenčních parametrů, které přidávají dodatečné identifikační informace. V rámci WCF jsou tyto parametry odkazu modelovány jako instance třídy <xref:System.ServiceModel.Channels.AddressHeader>.

Adresu koncového bodu pro službu lze zadat buď imperativně pomocí kódu, nebo deklarativně prostřednictvím konfigurace. Definování koncových bodů v kódu obvykle není praktické, protože vazby a adresy nasazené služby se obvykle liší od těch, které se použily při vývoji služby. Obecně je praktické definovat koncové body služby pomocí konfigurace namísto kódu. Zachování vazby a adresování informací z kódu umožňuje jejich změnu bez nutnosti opětovné kompilace a opětovného nasazení aplikace. Pokud v kódu nebo v konfiguraci nejsou zadány žádné koncové body, modul runtime přidá jeden výchozí koncový bod na každou základní adresu pro každou smlouvu implementovanou službou.

Existují dva způsoby, jak zadat adresy koncových bodů pro službu ve službě WCF. Pro každý koncový bod, který je přidružený ke službě, můžete zadat absolutní adresu, nebo můžete zadat základní adresu pro <xref:System.ServiceModel.ServiceHost> služby a pak zadat adresu každého koncového bodu přidruženého k této službě, který je definovaný relativně k této základní adrese. Jednotlivé postupy můžete použít k zadání adres koncového bodu služby v konfiguraci nebo kódu. Pokud nezadáte relativní adresu, služba použije základní adresu. Pro službu můžete mít také více základních adres, ale každá služba je pro každý přenos povolena pouze jedna základní adresa. Pokud máte více koncových bodů, z nichž každá je nakonfigurována s jinou vazbou, jejich adresy musí být jedinečné. Koncové body, které používají stejnou vazbu, ale různé kontrakty můžou používat stejnou adresu.

Při hostování se službou IIS nespravujete instanci <xref:System.ServiceModel.ServiceHost> sami. Základní adresa je vždy adresa zadaná v souboru. svc pro službu při hostování ve službě IIS. Proto je nutné pro koncové body služby hostované službou IIS použít relativní adresy koncových bodů. Poskytnutí plně kvalifikované adresy koncového bodu může vést k chybám v nasazení služby. Další informace najdete v tématu [nasazení služby WCF hostované Internetová informační služba](./feature-details/deploying-an-internet-information-services-hosted-wcf-service.md).

## <a name="defining-endpoint-addresses-in-configuration"></a>Definování adres koncových bodů v konfiguraci

Chcete-li definovat koncový bod v konfiguračním souboru, použijte prvek [\<endpoint >](../configure-apps/file-schema/wcf/endpoint-element.md) .

[!code-xml[S_UEHelloWorld#5](../../../samples/snippets/common/VS_Snippets_CFX/s_uehelloworld/common/serviceapp2.config#5)]

Když je volána metoda <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> (to znamená, když se hostující aplikace pokusí službu spustit), systém vyhledá element [\<service >](../configure-apps/file-schema/wcf/service.md) s atributem Name, který určuje "UE". Samples. HelloService ". Pokud je nalezen element [\<service >](../configure-apps/file-schema/wcf/service.md) , systém načte zadanou třídu a vytvoří koncové body pomocí definice koncových bodů, které jsou k dispozici v konfiguračním souboru. Tento mechanismus umožňuje načíst a spustit službu se dvěma řádky kódu a přitom zachovat informace o vazbách a adresování z vašeho kódu. Výhodou tohoto přístupu je, že tyto změny lze provést bez nutnosti opětovné kompilace nebo opětovného nasazení aplikace.

Volitelné hlavičky jsou deklarovány v [> \<headers](../configure-apps/file-schema/wcf/headers-element.md). Následuje příklad prvků, které slouží k určení koncových bodů pro službu v konfiguračním souboru, který rozlišuje dvě hlavičky: "Gold" klienti z `http://tempuri1.org/` a "standardní" klienti od `http://tempuri2.org/`. Klient, který volá tuto službu, musí mít ve svém konfiguračním souboru odpovídající [> \<headers](../configure-apps/file-schema/wcf/headers-element.md) .

[!code-xml[S_UEHelloWorld#1](../../../samples/snippets/common/VS_Snippets_CFX/s_uehelloworld/common/serviceapp.config#1)]

Záhlaví lze také nastavit pro jednotlivé zprávy, nikoli pro všechny zprávy na koncovém bodu (jak je uvedeno dříve). K tomu je potřeba použít <xref:System.ServiceModel.OperationContextScope> k vytvoření nového kontextu v klientské aplikaci, aby se do odchozí zprávy přidala vlastní hlavička, jak je znázorněno v následujícím příkladu.

[!code-csharp[OperationContextScope#4](../../../samples/snippets/csharp/VS_Snippets_CFX/operationcontextscope/cs/client.cs#4)]
[!code-vb[OperationContextScope#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/operationcontextscope/vb/client.vb#4)]

## <a name="endpoint-address-in-metadata"></a>Adresa koncového bodu v metadatech

Adresa koncového bodu je zastoupena v jazyce WSDL (Web Services Description Language) jako element WS-Addressing `EndpointReference` (EPR) uvnitř elementu `wsdl:port` příslušného koncového bodu. EPR obsahuje adresu koncového bodu a také všechny vlastnosti adresy. Všimněte si, že EPR uvnitř `wsdl:port` nahrazuje `soap:Address`, jak je vidět v následujícím příkladu.

## <a name="defining-endpoint-addresses-in-code"></a>Definování adres koncových bodů v kódu

Adresa koncového bodu může být vytvořena v kódu s třídou <xref:System.ServiceModel.EndpointAddress>. Identifikátor URI zadaný pro adresu koncového bodu může být plně kvalifikovaná cesta nebo cesta, která je relativní vzhledem k základní adrese služby. Následující kód ukazuje, jak vytvořit instanci třídy <xref:System.ServiceModel.EndpointAddress> a přidat ji do instance <xref:System.ServiceModel.ServiceHost>, která je hostitelem služby.

Následující příklad ukazuje, jak zadat úplnou adresu koncového bodu v kódu.

[!code-csharp[S_UEHelloWorld#2](../../../samples/snippets/csharp/VS_Snippets_CFX/s_uehelloworld/cs/snippet.cs#2)]

Následující příklad ukazuje, jak přidat relativní adresu ("Mojesluzba") na základní adresu hostitele služby.

[!code-csharp[S_UEHelloWorld#3](../../../samples/snippets/csharp/VS_Snippets_CFX/s_uehelloworld/cs/snippet.cs#3)]

> [!NOTE]
> Vlastnosti <xref:System.ServiceModel.Description.ServiceDescription> v aplikaci služby se nesmí upravovat za metodou <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> v <xref:System.ServiceModel.ServiceHostBase>. Někteří členové, například vlastnost <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> a metody `AddServiceEndpoint` v <xref:System.ServiceModel.ServiceHostBase> a <xref:System.ServiceModel.ServiceHost>, vyvolávají výjimku, pokud se po tomto bodu upraví. Jiné vám umožní je upravovat, ale výsledek není definován.
>
> Podobně na straně klienta nesmí být hodnoty <xref:System.ServiceModel.Description.ServiceEndpoint> měněny po volání <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> na <xref:System.ServiceModel.ChannelFactory>. Vlastnost <xref:System.ServiceModel.ChannelFactory.Credentials%2A> vyvolá výjimku, pokud byla změněna po tomto bodu. Ostatní hodnoty popisů klienta lze upravovat bez chyb, ale výsledek není definován.
>
> Bez ohledu na to, jestli pro službu nebo klienta, se doporučuje změnit popis před voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.

## <a name="using-default-endpoints"></a>Používání výchozích koncových bodů

Pokud v kódu nebo v konfiguraci nejsou zadány žádné koncové body, modul runtime poskytuje výchozí koncové body přidáním jednoho výchozího koncového bodu na každou základní adresu pro každý kontrakt služby implementovaný službou. Základní adresu lze zadat v kódu nebo v konfiguraci a výchozí koncové body jsou přidány při volání <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> v <xref:System.ServiceModel.ServiceHost>.

Pokud jsou koncové body explicitně poskytnuty, lze výchozí koncové body přidat voláním <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> na <xref:System.ServiceModel.ServiceHost> před voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. Další informace o výchozích koncových bodech, vazbách a chování najdete v tématu [zjednodušená konfigurace](simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](./samples/simplified-configuration-for-wcf-services.md).

## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.EndpointAddress>
- [Identita a ověřování služby](./feature-details/service-identity-and-authentication.md)
- [Přehled vytváření koncových bodů](endpoint-creation-overview.md)
- [Hostování](./feature-details/hosting.md)
