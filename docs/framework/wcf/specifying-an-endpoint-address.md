---
title: Zadání adresy koncového bodu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], addressing
ms.assetid: ac24f5ad-9558-4298-b168-c473c68e819b
ms.openlocfilehash: 784b0fe3e2b23287d458f9aa4d8276e10dd6ed97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="specifying-an-endpoint-address"></a>Zadání adresy koncového bodu
Veškerá komunikace se službou Windows Communication Foundation (WCF) dojde k prostřednictvím své koncové body. Každý <xref:System.ServiceModel.Description.ServiceEndpoint> obsahuje <xref:System.ServiceModel.Description.ServiceEndpoint.Address%2A>, <xref:System.ServiceModel.Description.ServiceEndpoint.Binding%2A>a <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A>. Kontrakt určuje operací, které jsou k dispozici. Vazba Určuje, jak se komunikovat se službou a adresu určuje, kde najít službu. Každý koncový bod musí mít jedinečnou adresu. Adresa koncového bodu je reprezentována <xref:System.ServiceModel.EndpointAddress> třídy, která obsahuje identifikátor URI (Uniform Resource) představující adresu služby, <xref:System.ServiceModel.EndpointAddress.Identity%2A>, který představuje identitu zabezpečení služby a kolekce volitelné <xref:System.ServiceModel.EndpointAddress.Headers%2A>. Volitelné záhlaví obsahují podrobnější informace o přidělování k vaší identifikaci nebo interakci s koncovým bodem. Například záhlaví můžete určit, jak zpracovávat příchozí zprávy, kde má koncový bod odeslat zprávu odpovědi nebo které instanci služby pro použití ke zpracování příchozí zprávy z určitého uživatele, když jsou k dispozici více instancí.  
  
## <a name="definition-of-an-endpoint-address"></a>Definice adresu koncového bodu  
 V [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], <xref:System.ServiceModel.EndpointAddress> modelů odkaz na koncový bod (EPR), jak je definované ve standardu adresování WS.  
  
 Adresa URI pro většinu přenosy má čtyři části. Například tento identifikátor URI "http://www.fabrikam.com:322/mathservice.svc/secureEndpoint" má následující čtyři části:  
  
-   Schéma: http:  
  
-   Počítač: www.fabrikam.com  
  
-   (Volitelné) Port: 322  
  
-   Path: /mathservice.svc/secureEndpoint  
  
 Součást EPR modelu je, že každý koncový bod odkaz přenášet některé odkaz parametry, které přidat velmi identifikační informace. V [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], tyto parametry odkaz jsou modelovat jako instance <xref:System.ServiceModel.Channels.AddressHeader> třídy.  
  
 Adresa koncového bodu pro služby lze imperativní pomocí kódu nebo deklarativně pomocí konfigurace. Definování koncové body v kódu obvykle není praktické protože jsou obvykle liší od těch, které používá při služby je vyvíjen vazeb a adresy pro v nasazené službě. Obecně je praktičtější definovat koncové body služby pomocí konfigurace, nikoli kódu. Zachování vazby a adresování informace mimo kód vám umožní se změnit bez nutnosti znovu zkompiluje a znovu nasaďte aplikaci. Pokud žádné koncové body jsou nastaveny v kódu nebo v konfiguraci, modul runtime přidá jeden výchozí koncový bod na každé základní adresa pro každý kontrakt implementované službu.  
  
 Existují dva způsoby k zadání adresy koncového bodu služby v [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]. Můžete zadat absolutní adresu pro každý koncový bod spojené s touto službou, nebo můžete zadat bázové adresy pro <xref:System.ServiceModel.ServiceHost> služby a pak zadejte adresu pro každý koncový bod přidruženého k této službě, která je definována relativně k této základní Adresa. Všechny tyto postupy můžete použít k určení adresy koncových bodů pro službu s konfigurací nebo kódu. Pokud nezadáte relativní adresa, služba používá základní adresu. Také může mít více základní adresy pro služby, ale každá služba je povolen pouze jeden základní adresa pro každý přenos. Pokud máte několik koncových bodů, z nichž každý je nakonfigurován s jinou vazbou, jejich adresy musí být jedinečný. Koncové body, které používají stejné vazby ale odlišným kontrakty můžete použít stejné adresy.  
  
 Při hostování službou IIS, kterou spravujete <xref:System.ServiceModel.ServiceHost> instance sami. Základní adresa je vždy adresu určenou v souboru .svc pro službu při hostování ve službě IIS. Proto je nutné použít relativní koncový bod adresy pro koncové body služby hostované službou IIS. Poskytuje adresu plně kvalifikovaný koncového bodu může vést k chybám v nasazení služby. Další informace najdete v tématu [nasazení služby WCF Internet Information Services-Hosted](../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md).  
  
## <a name="defining-endpoint-addresses-in-configuration"></a>Definování adresy koncových bodů v konfiguraci  
 Chcete-li definovat koncový bod v konfiguračním souboru, použijte [ \<endpoint >](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) element.  
  
 [!code-xml[S_UEHelloWorld#5](../../../samples/snippets/common/VS_Snippets_CFX/s_uehelloworld/common/serviceapp2.config#5)]  
  
 Když <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> metoda je volána (při hostování aplikace pokusí o spuštění služby), systém vyhledá [ \<služby >](../../../docs/framework/configure-apps/file-schema/wcf/service.md) element s názvem atributu, který určuje "UE. Samples.HelloService". Pokud [ \<služby >](../../../docs/framework/configure-apps/file-schema/wcf/service.md) nebyl nalezen prvek, načte zadanou třídu systému a vytvoří koncové body pomocí definice koncových bodů zadaný v konfiguračním souboru. Tento mechanismus umožňuje načíst a spustit službu s dva řádky kódu při zachování vazby a adresování informace z vašeho kódu. Výhodou tohoto přístupu je, že tyto změny provést bez nutnosti znovu zkompiluje nebo znovu nasadit aplikaci.  
  
 Volitelné hlavičky jsou deklarované v [ \<hlavičky >](../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md). Následuje příklad elementů slouží k zadání koncové body pro službu v konfiguračním souboru, který slouží k rozlišení mezi dvěma hlavičky: "Zlatá" klienty z http://tempuri1.org/ a "Standard" klientů z http://tempuri2.org/. Klient pro volání tato služba musí mít odpovídající [ \<hlavičky >](../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md) v konfiguračního souboru.  
  
 [!code-xml[S_UEHelloWorld#1](../../../samples/snippets/common/VS_Snippets_CFX/s_uehelloworld/common/serviceapp.config#1)]  
  
 Záhlaví lze také nastavit na jednotlivé zprávy místo všechny zprávy v koncovém bodě (jak je uvedeno výše). To se provádí pomocí <xref:System.ServiceModel.OperationContextScope> vytvořit nový kontext v aplikaci klienta přidat vlastní hlavičku do odchozí zprávy, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[OperationContextScope#4](../../../samples/snippets/csharp/VS_Snippets_CFX/operationcontextscope/cs/client.cs#4)]
 [!code-vb[OperationContextScope#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/operationcontextscope/vb/client.vb#4)]  
  
## <a name="endpoint-address-in-metadata"></a>Adresa koncového bodu v metadatech  
 Představuje adresu koncového bodu v webové služby WSDL (Description Language) jako WS-Addressing `EndpointReference` (EPR) prvku v odpovídající koncový bod `wsdl:port` elementu. EPR obsahuje adresu pro koncový bod, jakož i všechny vlastnosti adresy. Všimněte si, že EPR uvnitř `wsdl:port` nahrazuje `soap:Address` jak je vidět v následujícím příkladu.  
  
  
  
## <a name="defining-endpoint-addresses-in-code"></a>Definování adresy koncových bodů v kódu  
 Adresy koncového bodu se dají vytvářet v kódu pomocí <xref:System.ServiceModel.EndpointAddress> třídy. Identifikátor URI zadaná adresa koncového bodu může být plně kvalifikovanou cestu nebo cestu, která je relativní vzhledem k základní adresa služby. Následující kód ukazuje, jak vytvořit instanci <xref:System.ServiceModel.EndpointAddress> třídu a přidejte ho do <xref:System.ServiceModel.ServiceHost> instance, který je hostitelem služby.  
  
 Následující příklad ukazuje, jak zadat adresu úplné koncového bodu v kódu.  
  
 [!code-csharp[S_UEHelloWorld#2](../../../samples/snippets/csharp/VS_Snippets_CFX/s_uehelloworld/cs/snippet.cs#2)]  
  
 Následující příklad ukazuje, jak přidat relativní adresu ("Moje_služba") na základní adresu hostitele služby.  
  
 [!code-csharp[S_UEHelloWorld#3](../../../samples/snippets/csharp/VS_Snippets_CFX/s_uehelloworld/cs/snippet.cs#3)]  
  
> [!NOTE]
>  Vlastnosti <xref:System.ServiceModel.Description.ServiceDescription> ve službě aplikace nesmí být upravit subsequent tak, aby <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> metodu <xref:System.ServiceModel.ServiceHostBase>. Některé členy, jako <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> vlastnost a `AddServiceEndpoint` metody na <xref:System.ServiceModel.ServiceHostBase> a <xref:System.ServiceModel.ServiceHost>, způsobí výjimku, pokud se změní po tomto okamžiku. Ostatní umožňují je upravovat, ale výsledek není definován.  
>   
>  Podobně na straně klienta <xref:System.ServiceModel.Description.ServiceEndpoint> po zavolání nesmí měnit hodnoty <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> na <xref:System.ServiceModel.ChannelFactory>. <xref:System.ServiceModel.ChannelFactory.Credentials%2A> Vlastnost vyvolá výjimku, pokud se změní po tomto okamžiku. Ostatní hodnoty klienta popis můžete změnit bez chyby, ale výsledek není definován.  
>   
>  Zda se služba nebo klienta, se doporučuje, když je upravit popis před voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.  
  
## <a name="using-default-endpoints"></a>Pomocí výchozí koncové body  
 Pokud nejsou zadány žádné koncové body, v kódu nebo v konfiguraci modulu runtime poskytuje výchozí koncové body přidáním jeden výchozí koncový bod na každé základní adresa pro každý kontrakt služby implementované službu. Základní adresa může být určený v kódu nebo v konfiguraci a jsou výchozí koncové body se přidají při <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> se volá na <xref:System.ServiceModel.ServiceHost>.  
  
 Pokud jsou k dispozici explicitně koncových bodů, jsou výchozí koncové body může být přidán voláním <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> na <xref:System.ServiceModel.ServiceHost> před voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. Další informace o výchozí koncové body, vazby a chování najdete v tématu [zjednodušená konfigurace](../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.EndpointAddress>  
 [Identita a ověřování služby](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Přehled vytváření koncových bodů](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Hostování](../../../docs/framework/wcf/feature-details/hosting.md)
