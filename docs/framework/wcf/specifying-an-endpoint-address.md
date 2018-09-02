---
title: Zadání adresy koncového bodu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], addressing
ms.assetid: ac24f5ad-9558-4298-b168-c473c68e819b
ms.openlocfilehash: 718a0c086181546ba7b7fb3b31fce0732dd99382
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401764"
---
# <a name="specifying-an-endpoint-address"></a>Zadání adresy koncového bodu
Veškerá komunikace se službou Windows Communication Foundation (WCF) nastane prostřednictvím jeho koncových bodů. Každý <xref:System.ServiceModel.Description.ServiceEndpoint> obsahuje <xref:System.ServiceModel.Description.ServiceEndpoint.Address%2A>, <xref:System.ServiceModel.Description.ServiceEndpoint.Binding%2A>a <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A>. Kontrakt určuje operace, které jsou k dispozici. Určuje vazbu, jak komunikovat se službou a určuje adresu, kde najít službu. Každý koncový bod musí mít jedinečnou adresu. Adresa koncového bodu je reprezentována <xref:System.ServiceModel.EndpointAddress> třídu, která obsahuje identifikátor URI (Uniform Resource), který představuje adresu služby, <xref:System.ServiceModel.EndpointAddress.Identity%2A>, která představuje zabezpečení identity služby a kolekce volitelné <xref:System.ServiceModel.EndpointAddress.Headers%2A>. Volitelná záhlaví poskytují podrobnější informace o adresování k identifikaci a k interakci s koncovým bodem. Záhlaví může například signalizovat zpracování příchozí zprávy, kde koncový bod má odeslat zpráva s odpovědí nebo které instanci služby pro použití ke zpracování příchozí zprávy z konkrétního uživatele, když jsou k dispozici více instancí.  
  
## <a name="definition-of-an-endpoint-address"></a>Definice adresy koncového bodu  
 Ve službě WCF <xref:System.ServiceModel.EndpointAddress> modely referenci koncového bodu (EPR), jak jsou definovány ve standardu WS-Addressing.  
  
 Adresa URI pro většinu přenosy obsahuje čtyři části. Například tento identifikátor URI `http://www.fabrikam.com:322/mathservice.svc/secureEndpoint` má následující čtyři části:  
  
-   Schéma: http:  
  
-   Počítač: `www.fabrikam.com`  
  
-   (Volitelné) Port: 322  
  
-   Path: /mathservice.svc/secureEndpoint  
  
 Součástí modelu EPR je, že každý reference koncového bodu může obsahovat některé odkaz parametry, které přidávají další identifikační údaje. Ve službě WCF, jsou tyto parametry odkazů nemodelují jako instance <xref:System.ServiceModel.Channels.AddressHeader> třídy.  
  
 Adresa koncového bodu služby lze toho pomocí kódu nebo deklarativně prostřednictvím konfigurace. Definování koncových bodů v kódu není obvykle praktické protože vazeb a adresy pro službu nasazenou se obvykle liší od nastavení použít, je vyvíjena služby. Obecně je praktičtější k definování koncových bodů služby pomocí konfigurace namísto kódu. Udržování vazby a adresování informace mimo kód umožňující změnit bez nutnosti znovu kompilovat a opětovné nasazení aplikace. Pokud v kódu nebo v konfiguraci nejsou zadány žádné koncové body, modulu runtime přidá jeden výchozí koncový bod na každé základní adresa pro každý kontraktů implementovaných službou.  
  
 Existují dva způsoby, jak zadat koncový bod adresy pro službu ve službě WCF. Můžete zadat absolutní adresa pro každý koncový bod, související se službou, nebo můžete zadat základní adresu pro <xref:System.ServiceModel.ServiceHost> služby a potom zadejte adresu pro každý koncový bod spojený s touto službou, která je definována vzhledem k této základní Adresa. Každá z těchto postupů můžete použít k zadání adresy koncového bodu služby v konfiguraci nebo kódu. Pokud nezadáte relativní adresa, služba používá základní adresu. Můžete mít také více bázové adresy pro služby, ale každá služba je povolen pouze jednu základní adresu pro každou přenos. Pokud máte několik koncových bodů, z nichž každý má nakonfigurovanou jinou vazbou, jejich adresy musí být jedinečné. Koncové body, které používají stejné vazby ale různé kontrakty můžete použít stejnou adresu.  
  
 Při hostování za nástrojem službou IIS, nedokáže spravovat <xref:System.ServiceModel.ServiceHost> instance sami. Základní adresa je vždy adresa zadaná v souboru SVC pro službu, při hostování ve službě IIS. Proto je nutné použít relativní koncového bodu adresy koncových bodů služby hostované v IIS. Poskytuje adresu plně kvalifikovaný koncový bod může vést k chybám v nasazení služby. Další informace najdete v tématu [nasazení služby WCF Internet Information Services-Hosted](../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md).  
  
## <a name="defining-endpoint-addresses-in-configuration"></a>Definování adresy koncových bodů v konfiguraci  
 Chcete-li definovat koncový bod v konfiguračním souboru, použijte [ \<koncový bod >](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) elementu.  
  
 [!code-xml[S_UEHelloWorld#5](../../../samples/snippets/common/VS_Snippets_CFX/s_uehelloworld/common/serviceapp2.config#5)]  
  
 Když <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> metoda je volána (to znamená, když hostitelské aplikace došlo k pokusu o spuštění služby), hledá v systému [ \<služby >](../../../docs/framework/configure-apps/file-schema/wcf/service.md) element s názvem atribut, který určuje "UE. Samples.HelloService". Pokud [ \<služby >](../../../docs/framework/configure-apps/file-schema/wcf/service.md) nalezen element, načte zadanou třídu systému a vytvoří koncových bodů pomocí definic koncových bodů, které jsou k dispozici v konfiguračním souboru. Tento mechanismus umožňuje načtení a spuštění služby se dvěma řádky kódu při zachování vazby a adresování informace z vašeho kódu. Výhodou tohoto přístupu je, že tyto změny je možné provádět bez nutnosti znovu kompilovat nebo znovu nasadit aplikaci.  
  
 Volitelná záhlaví jsou deklarovány v [ \<záhlaví >](../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md). Následuje příklad z prvků, které slouží k určení koncových bodů služby v konfiguračním souboru, který rozlišuje mezi dvě záhlaví: "Zlatá" klienti z `http://tempuri1.org/` a "Standardní" klienti z `http://tempuri2.org/`. Volání této služby Klient musí mít odpovídající [ \<záhlaví >](../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md) v jeho konfiguračnímu souboru.  
  
 [!code-xml[S_UEHelloWorld#1](../../../samples/snippets/common/VS_Snippets_CFX/s_uehelloworld/common/serviceapp.config#1)]  
  
 Záhlaví můžete také nastavit pro jednotlivé zprávy místo všechny zprávy v koncovém bodě (jak je uvedeno dříve). To se provádí pomocí <xref:System.ServiceModel.OperationContextScope> vytvořit nový kontext v klientské aplikaci přidat vlastní hlavičku na odchozí zprávu, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[OperationContextScope#4](../../../samples/snippets/csharp/VS_Snippets_CFX/operationcontextscope/cs/client.cs#4)]
 [!code-vb[OperationContextScope#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/operationcontextscope/vb/client.vb#4)]  
  
## <a name="endpoint-address-in-metadata"></a>Adresa koncového bodu v metadatech  
 Adresy koncového bodu je reprezentován v webové služby WSDL (Description Language) jako WS-Addressing `EndpointReference` – element (EPR) uvnitř odpovídající koncový bod `wsdl:port` elementu. EPR obsahuje adresu koncového bodu, jakož i všechny vlastnosti adresy. Všimněte si, že EPR uvnitř `wsdl:port` nahradí `soap:Address` jak je znázorněno v následujícím příkladu.  
  
  
  
## <a name="defining-endpoint-addresses-in-code"></a>Definování adresy koncových bodů v kódu  
 Adresy koncového bodu je možné vytvořit v kódu pomocí <xref:System.ServiceModel.EndpointAddress> třídy. Identifikátor URI zadaný pro adresu koncového bodu může být plně kvalifikovanou cestu nebo cestu, která je relativní vzhledem k základní adresu služby. Následující kód ukazuje, jak vytvořit instanci <xref:System.ServiceModel.EndpointAddress> třídu a přidejte ho do <xref:System.ServiceModel.ServiceHost> instanci, která je hostitelem služby.  
  
 Následující příklad ukazuje, jak zadat adresu úplné koncový bod v kódu.  
  
 [!code-csharp[S_UEHelloWorld#2](../../../samples/snippets/csharp/VS_Snippets_CFX/s_uehelloworld/cs/snippet.cs#2)]  
  
 Následující příklad ukazuje, jak přidat relativní adresu ("Moje_služba") na základní adresu hostitele služby.  
  
 [!code-csharp[S_UEHelloWorld#3](../../../samples/snippets/csharp/VS_Snippets_CFX/s_uehelloworld/cs/snippet.cs#3)]  
  
> [!NOTE]
>  Vlastnosti <xref:System.ServiceModel.Description.ServiceDescription> ve službě application nesmí upravit subsequent tak, aby <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> metodu na <xref:System.ServiceModel.ServiceHostBase>. Některé členy, jako <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> vlastnost a `AddServiceEndpoint` metody <xref:System.ServiceModel.ServiceHostBase> a <xref:System.ServiceModel.ServiceHost>, vyvolat výjimku, pokud byl změněn po tomto okamžiku. Ostatní umožňují upravovat, ale výsledek není definován.  
>   
>  Podobně na straně klienta <xref:System.ServiceModel.Description.ServiceEndpoint> hodnoty nesmí být změněny po volání <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> na <xref:System.ServiceModel.ChannelFactory>. <xref:System.ServiceModel.ChannelFactory.Credentials%2A> Vlastnost vyvolá výjimku, pokud byl změněn po tomto okamžiku. Ostatní hodnoty Popis klienta můžete změnit bez chyb, ale výsledek není definován.  
>   
>  Ať už pro službu nebo klienta, se doporučuje, že upravíte popis před voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.  
  
## <a name="using-default-endpoints"></a>Pomocí výchozí koncové body  
 Pokud nejsou zadány žádné koncové body, v kódu nebo v konfiguraci modulu runtime poskytuje výchozí koncové body přidáním jeden výchozí koncový bod na každé základní adresu pro každou smlouvu službou implementována. Základní adresa se dá nastavit v kódu nebo v konfiguraci a jsou přidány výchozí koncové body, kdy <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> je volán na <xref:System.ServiceModel.ServiceHost>.  
  
 Pokud koncové body jsou explicitně zadán, výchozí koncové body může být přidána voláním <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> na <xref:System.ServiceModel.ServiceHost> před voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. Další informace o výchozí koncové body, vazby a chování najdete v tématu [zjednodušená konfigurace](../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.EndpointAddress>  
 [Identita a ověřování služby](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Přehled vytváření koncových bodů](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Hostování](../../../docs/framework/wcf/feature-details/hosting.md)
