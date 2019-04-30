---
title: 'Postupy: Vytvoření základní webové služby HTTP WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 877662d3-d372-4e08-b417-51f66a0095cd
ms.openlocfilehash: 1b76d21cb4f416aae76e7597ad16cfd45e5b7cad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61779194"
---
# <a name="how-to-create-a-basic-wcf-web-http-service"></a>Postupy: Vytvoření základní webové služby HTTP WCF

Windows Communication Foundation (WCF) umožňuje vytvořit službu, která zveřejňuje webový koncový bod. Koncové body webové odesílat data XML nebo JSON, neexistuje žádný obálku protokolu SOAP. Toto téma ukazuje, jak vystavit takové koncový bod.

> [!NOTE]
> Jediný způsob, jak zabezpečit webový koncový bod je zveřejnit přes HTTPS pomocí zabezpečení přenosu. Při použití zabezpečení na základě zpráv, informace o zabezpečení obvykle umístěny v záhlaví SOAP a protože zprávy odeslané do koncových bodů protokolu SOAP obsahovat žádné obálku protokolu SOAP, není nikde umístit informace o zabezpečení a musíte spoléhat na zabezpečení přenosu.

## <a name="to-create-a-web-endpoint"></a>Chcete-li vytvořit webový koncový bod

1. Definování kontraktu služby pomocí rozhraní označené <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> a <xref:System.ServiceModel.Web.WebGetAttribute> atributy.

     [!code-csharp[htBasicService#0](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#0)]
     [!code-vb[htBasicService#0](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#0)]

    > [!NOTE]
    > Ve výchozím nastavení <xref:System.ServiceModel.Web.WebInvokeAttribute> mapuje příspěvek volání operace. Můžete však určit metodu HTTP (například HEAD, PUT nebo DELETE) pro mapování na operaci zadáním "metoda =" parametr. <xref:System.ServiceModel.Web.WebGetAttribute> nemá "metoda =" parametr a jen mapy GET volání operace služby.

2. Implementace kontraktu služby.

     [!code-csharp[htBasicService#1](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#1)]
     [!code-vb[htBasicService#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#1)]

## <a name="to-host-the-service"></a>K hostování služby

1. Vytvoření <xref:System.ServiceModel.Web.WebServiceHost> objektu.

     [!code-csharp[htBasicService#2](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#2)]
     [!code-vb[htBasicService#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#2)]

2. Přidat <xref:System.ServiceModel.Description.ServiceEndpoint> s <xref:System.ServiceModel.Description.WebHttpBehavior>.

     [!code-csharp[htBasicService#3](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#3)]
     [!code-vb[htBasicService#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#3)]

    > [!NOTE]
    > Pokud nemůžete přidat koncový bod, <xref:System.ServiceModel.Web.WebServiceHost> automaticky vytvoří výchozí koncový bod. <xref:System.ServiceModel.Web.WebServiceHost> také přidá <xref:System.ServiceModel.Description.WebHttpBehavior> a zakáže stránky s nápovědou HTTP a funkci GET webové služby WSDL (Description Language), takže koncový bod metadat nebude v konfliktu s výchozí koncový bod HTTP.
    >
    >  Přidat koncový bod-protokolu SOAP s adresou URL "" způsobí neočekávané chování při pokusu o volání operace v koncovém bodě. Důvodem je listen URI koncového bodu je stejný jako identifikátor URI na stránce nápovědy (stránka, která se zobrazí, když přejdete na základní adresa služby WCF).

     Můžete provést jednu z následujících akcí k tomu nedocházelo:

    - Vždycky zadejte neprázdný identifikátor URI pro koncový bod-protokolu SOAP.

    - Vypněte stránky s nápovědou. To lze provést následujícím kódem:

     [!code-csharp[htBasicService#4](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#4)]
     [!code-vb[htBasicService#4](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#4)]

3. Otevření hostitele služby a počkejte, až uživatel stiskne klávesu ENTER.

     [!code-csharp[htBasicService#5](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#5)]
     [!code-vb[htBasicService#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#5)]

     Tento příklad ukazuje, jak hostování stylu webové služby pomocí konzolové aplikace. Také můžete hostovat služby, v rámci služby IIS. Chcete-li to provést, zadejte <xref:System.ServiceModel.Activation.WebServiceHostFactory> třídy v souboru SVC, jak ukazuje následující kód.

    ```
    <%ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Samples.Service"
        Factory=System.ServiceModel.Activation.WebServiceHostFactory%>
    ```

## <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a>K volání operací služby namapované k získání přístupu v aplikaci Internet Explorer

1. Otevřete aplikaci Internet Explorer a zadejte "`http://localhost:8000/EchoWithGet?s=Hello, world!`" a stiskněte klávesu ENTER. Adresa URL obsahuje základní adresa služby (`http://localhost:8000/`), relativní adresu koncového bodu (""), operace služby k volání ("EchoWithGet") a otazník následovaný seznamem pojmenovaných parametrů oddělených ampersandem (&).

## <a name="to-call-service-operations-in-code"></a>K volání operací služby v kódu

1. Vytvoření instance <xref:System.ServiceModel.ChannelFactory%601> v rámci `using` bloku.

     [!code-csharp[htBasicService#6](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#6)]
     [!code-vb[htBasicService#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#6)]

2. Přidat <xref:System.ServiceModel.Description.WebHttpBehavior> ke koncovému bodu <xref:System.ServiceModel.ChannelFactory%601> volání.

     [!code-csharp[htBasicService#7](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#7)]
     [!code-vb[htBasicService#7](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#7)]

3. Vytvoření kanálu a volání služby.

     [!code-csharp[htBasicService#8](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#8)]
     [!code-vb[htBasicService#8](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#8)]

4. Zavřít <xref:System.ServiceModel.Web.WebServiceHost>.

     [!code-csharp[htBasicService#9](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#9)]
     [!code-vb[htBasicService#9](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#9)]

## <a name="example"></a>Příklad

Následuje úplný výpis v tomto příkladu kódu.

[!code-csharp[htBasicService#10](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#10)]
[!code-vb[htBasicService#10](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#10)]

## <a name="compiling-the-code"></a>Kompilování kódu

Při kompilaci Service.cs reference System.ServiceModel.dll a System.ServiceModel.Web.dll.

## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
- <xref:System.ServiceModel.Web.WebInvokeAttribute>
- <xref:System.ServiceModel.Web.WebServiceHost>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [Programovací model webových služeb HTTP WCF](wcf-web-http-programming-model.md)