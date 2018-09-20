---
title: 'Postupy: zveřejnění kontraktu klientům SOAP a webovým klientům'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bb765a48-12f2-430d-a54d-6f0c20f2a23a
ms.openlocfilehash: d82c5e3fc33528eadc3c404cca59a3dcf905e0e2
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46323970"
---
# <a name="how-to-expose-a-contract-to-soap-and-web-clients"></a>Postupy: zveřejnění kontraktu klientům SOAP a webovým klientům

Ve výchozím nastavení Windows Communication Foundation (WCF) díky koncové body k dispozici jenom klientům SOAP. V [postupy: vytvoření základní služby WCF Web HTTP](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md), koncový bod je k dispozici pro klienty protokolu SOAP. Může nastat situace, kdy budete chtít zpřístupnit stejný kontrakt oba způsoby jako webový koncový bod a jako koncový bod SOAP. Toto téma ukazuje příklad toho, jak to provést.

## <a name="to-define-the-service-contract"></a>K definování kontraktu služby

1. Definování kontraktu služby pomocí rozhraní označené <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> a <xref:System.ServiceModel.Web.WebGetAttribute> atributy, jak je znázorněno v následujícím kódu:

    [!code-csharp[htSoapWeb#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#0)]
    [!code-vb[htSoapWeb#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#0)]

    > [!NOTE]
    > Ve výchozím nastavení <xref:System.ServiceModel.Web.WebInvokeAttribute> mapuje příspěvek volání operace. Můžete však určit metody, která mapují na operace tak, že zadáte "metoda =" parametr. <xref:System.ServiceModel.Web.WebGetAttribute> nemá "metoda =" parametr a jen mapy GET volání operace služby.

2. Implementace kontraktu služby, jak je znázorněno v následujícím kódu:

     [!code-csharp[htSoapWeb#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#1)]
     [!code-vb[htSoapWeb#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#1)]

## <a name="to-host-the-service"></a>K hostování služby

1. Vytvoření <xref:System.ServiceModel.ServiceHost> objektu, jak je znázorněno v následujícím kódu:

     [!code-csharp[htSoapWeb#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#2)]
     [!code-vb[htSoapWeb#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#2)]

2. Přidat <xref:System.ServiceModel.Description.ServiceEndpoint> s <xref:System.ServiceModel.BasicHttpBinding> pro koncový bod SOAP, jak je znázorněno v následujícím kódu:

     [!code-csharp[htSoapWeb#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#3)]
     [!code-vb[htSoapWeb#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#3)]

3. Přidat <xref:System.ServiceModel.Description.ServiceEndpoint> s <xref:System.ServiceModel.WebHttpBinding> pro koncový bod protokolu SOAP a přidejte <xref:System.ServiceModel.Description.WebHttpBehavior> ke koncovému bodu, jak je znázorněno v následujícím kódu:

     [!code-csharp[htSoapWeb#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#4)]
     [!code-vb[htSoapWeb#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#4)]

4. Volání `Open()` na <xref:System.ServiceModel.ServiceHost> instance otevřít hostitele služby, jak je znázorněno v následujícím kódu:

     [!code-csharp[htSoapWeb#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#5)]
     [!code-vb[htSoapWeb#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#5)]

## <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a>K volání operací služby namapované k získání přístupu v aplikaci Internet Explorer

1. Otevřete aplikaci Internet Explorer a zadejte "`http://localhost:8000/Web/EchoWithGet?s=Hello, world!`" a stiskněte klávesu ENTER. Adresa URL obsahuje základní adresa služby (`http://localhost:8000/`), relativní adresu koncového bodu (""), operace služby k volání ("EchoWithGet") a otazník následovaný seznamem pojmenovaných parametrů oddělených ampersandem (&).

## <a name="to-call-service-operations-on-the-web-endpoint-in-code"></a>K volání operací služby na webový koncový bod v kódu

1. Vytvoření instance <xref:System.ServiceModel.Web.WebChannelFactory%601> v rámci `using` blokovat, jak je znázorněno v následujícím kódu.

     [!code-csharp[htSoapWeb#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#6)]
     [!code-vb[htSoapWeb#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#6)]

> [!NOTE]
> `Close()` je automaticky volána v kanálu na konci `using` bloku.

1. Vytvoření kanálu a volání služby, jak je znázorněno v následujícím kódu.

     [!code-csharp[htSoapWeb#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#8)]
     [!code-vb[htSoapWeb#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#8)]

## <a name="to-call-service-operations-on-the-soap-endpoint"></a>K volání operací služby na koncový bod SOAP

1. Vytvoření instance <xref:System.ServiceModel.ChannelFactory> v rámci `using` blokovat, jak je znázorněno v následujícím kódu.

    [!code-csharp[htSoapWeb#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#10)]
    [!code-vb[htSoapWeb#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#10)]

2. Vytvoření kanálu a volání služby, jak je znázorněno v následujícím kódu.

    [!code-csharp[htSoapWeb#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#11)]
    [!code-vb[htSoapWeb#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#11)]

## <a name="to-close-the-service-host"></a>Zavřete hostitele služby

1. Hostitel služby zavřete, jak je znázorněno v následujícím kódu.

    [!code-csharp[htSoapWeb#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#9)]
    [!code-vb[htSoapWeb#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#9)]

## <a name="example"></a>Příklad

Následuje úplný výpis pro toto téma kódu:

[!code-csharp[htSoapWeb#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#13)]
[!code-vb[htSoapWeb#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#13)]

## <a name="compiling-the-code"></a>Kompilování kódu

 Při kompilaci Service.cs odkazovat System.ServiceModel.dll a System.ServiceModel.Web.dll.

## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
- <xref:System.ServiceModel.Web.WebInvokeAttribute>
- <xref:System.ServiceModel.Web.WebServiceHost>
- <xref:System.ServiceModel.ChannelFactory>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [Programovací model webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)