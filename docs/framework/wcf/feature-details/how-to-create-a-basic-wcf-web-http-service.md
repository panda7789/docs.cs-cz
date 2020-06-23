---
title: 'Postupy: Vytvoření základní webové služby HTTP WCF'
description: Naučte se vytvořit službu, která zveřejňuje webový koncový bod ve službě WCF. Webové koncové body odesílají data pomocí XML nebo JSON. Není k dispozici žádná obálka SOAP.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 877662d3-d372-4e08-b417-51f66a0095cd
ms.openlocfilehash: 7481367f27d973ba809dff5ca1c4a4f168fbbb98
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247101"
---
# <a name="how-to-create-a-basic-wcf-web-http-service"></a>Postupy: Vytvoření základní webové služby HTTP WCF

Windows Communication Foundation (WCF) umožňuje vytvořit službu, která zveřejňuje webový koncový bod. Webové koncové body odesílají data pomocí kódu XML nebo JSON, ale není k dispozici žádná obálka SOAP. Toto téma ukazuje, jak vystavit takový koncový bod.

> [!NOTE]
> Jediným způsobem, jak zajistit zabezpečení webového koncového bodu, je jeho zpřístupnění prostřednictvím protokolu HTTPS pomocí zabezpečení přenosu. Při použití zabezpečení založeného na zprávách jsou informace o zabezpečení obvykle umístěny v hlavičkách SOAP a protože zprávy odeslané koncovým bodům bez protokolu SOAP neobsahují žádnou obálku SOAP, je nikde umístit informace o zabezpečení a musíte spoléhat na zabezpečení přenosu.

## <a name="to-create-a-web-endpoint"></a>Vytvoření webového koncového bodu

1. Definujte kontrakt služby pomocí rozhraní označeného <xref:System.ServiceModel.ServiceContractAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> <xref:System.ServiceModel.Web.WebGetAttribute> atributem a.

     [!code-csharp[htBasicService#0](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#0)]
     [!code-vb[htBasicService#0](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#0)]

    > [!NOTE]
    > Ve výchozím nastavení <xref:System.ServiceModel.Web.WebInvokeAttribute> MAPUJE post volání operace. Můžete však zadat metodu HTTP (například HEAD, PUT nebo DELETE) k mapování na operaci zadáním parametru "Method =". <xref:System.ServiceModel.Web.WebGetAttribute>nemá parametr "Method =" a pouze mapuje volání GET na operaci služby.

2. Implementujte kontrakt služby.

     [!code-csharp[htBasicService#1](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#1)]
     [!code-vb[htBasicService#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#1)]

## <a name="to-host-the-service"></a>Hostování služby

1. Vytvořte <xref:System.ServiceModel.Web.WebServiceHost> objekt.

     [!code-csharp[htBasicService#2](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#2)]
     [!code-vb[htBasicService#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#2)]

2. Přidejte <xref:System.ServiceModel.Description.ServiceEndpoint> s <xref:System.ServiceModel.Description.WebHttpBehavior> .

     [!code-csharp[htBasicService#3](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#3)]
     [!code-vb[htBasicService#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#3)]

    > [!NOTE]
    > Pokud koncový bod nepřidáte, <xref:System.ServiceModel.Web.WebServiceHost> automaticky vytvoří výchozí koncový bod. <xref:System.ServiceModel.Web.WebServiceHost>také přidá <xref:System.ServiceModel.Description.WebHttpBehavior> a zakáže stránku Nápověda http a funkci get jazyka WSDL (Web Services Description Language), takže koncový bod metadat nekoliduje s výchozím koncovým bodem http.
    >
    >  Přidání koncového bodu bez protokolu SOAP s adresou URL "" způsobí neočekávané chování při pokusu o volání operace na koncovém bodu. Důvodem je, že identifikátor URI příposlechu koncového bodu je stejný jako identifikátor URI stránky s nápovědu (stránka, která se zobrazí při procházení k základní adrese služby WCF).

     K tomu, abyste zabránili tomu, můžete provést jednu z následujících akcí:

    - Vždy zadejte neprázdný identifikátor URI pro koncový bod, který není typu SOAP.

    - Vypněte stránku s usnadněním. To lze provést pomocí následujícího kódu:

     [!code-csharp[htBasicService#4](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#4)]
     [!code-vb[htBasicService#4](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#4)]

3. Otevřete hostitele služby a počkejte, dokud uživatel nestiskne klávesu ENTER.

     [!code-csharp[htBasicService#5](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#5)]
     [!code-vb[htBasicService#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#5)]

     Tato ukázka předvádí, jak hostovat službu webového stylu pomocí konzolové aplikace. Takovou službu můžete hostovat i v rámci služby IIS. Provedete to tak, že zadáte <xref:System.ServiceModel.Activation.WebServiceHostFactory> třídu v souboru. svc, jak ukazuje následující kód.

    ```text
    <%ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Samples.Service"
        Factory=System.ServiceModel.Activation.WebServiceHostFactory%>
    ```

## <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a>Volání operací služby mapovaných na získání v aplikaci Internet Explorer

1. Spusťte Internet Explorer a zadejte " `http://localhost:8000/EchoWithGet?s=Hello, world!` " a stiskněte klávesu ENTER. Adresa URL obsahuje základní adresu služby ( `http://localhost:8000/` ), relativní adresu koncového bodu (""), volanou operaci služby ("EchoWithGet") a otazník následovaný seznamem pojmenovaných parametrů oddělených ampersandem (&).

## <a name="to-call-service-operations-in-code"></a>Volání operací služby v kódu

1. Vytvoří instanci <xref:System.ServiceModel.ChannelFactory%601> v rámci `using` bloku.

     [!code-csharp[htBasicService#6](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#6)]
     [!code-vb[htBasicService#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#6)]

2. Přidejte <xref:System.ServiceModel.Description.WebHttpBehavior> do koncového bodu <xref:System.ServiceModel.ChannelFactory%601> volání.

     [!code-csharp[htBasicService#7](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#7)]
     [!code-vb[htBasicService#7](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#7)]

3. Vytvořte kanál a zavolejte službu.

     [!code-csharp[htBasicService#8](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#8)]
     [!code-vb[htBasicService#8](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#8)]

4. Zavřete <xref:System.ServiceModel.Web.WebServiceHost> .

     [!code-csharp[htBasicService#9](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#9)]
     [!code-vb[htBasicService#9](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#9)]

## <a name="example"></a>Příklad

Následuje úplný výpis kódu pro tento příklad.

[!code-csharp[htBasicService#10](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#10)]
[!code-vb[htBasicService#10](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#10)]

## <a name="compiling-the-code"></a>Zkompilování kódu

Při kompilování Service.cs referenčních System.ServiceModel.dll a System.ServiceModel.Web.dll.

## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
- <xref:System.ServiceModel.Web.WebInvokeAttribute>
- <xref:System.ServiceModel.Web.WebServiceHost>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [Programovací model webových služeb HTTP WCF](wcf-web-http-programming-model.md)
