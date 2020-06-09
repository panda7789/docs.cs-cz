---
title: 'Postupy: Zveřejnění kontraktu klientům SOAP a webovým klientům'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bb765a48-12f2-430d-a54d-6f0c20f2a23a
ms.openlocfilehash: fa02260976c710401a05cce3d723cc0f66804c6e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593126"
---
# <a name="how-to-expose-a-contract-to-soap-and-web-clients"></a>Postupy: Zveřejnění kontraktu klientům SOAP a webovým klientům

Ve výchozím nastavení služba Windows Communication Foundation (WCF) zpřístupňuje koncové body pouze klientům SOAP. V tématu [Postupy: Vytvoření základní webové služby HTTP WCF](how-to-create-a-basic-wcf-web-http-service.md)je koncový bod zpřístupněn klientům bez protokolu SOAP. Může nastat situace, kdy budete chtít, aby stejný kontrakt byl dostupný jak jako koncový bod, tak jako koncový bod SOAP. Toto téma ukazuje příklad toho, jak to provést.

## <a name="to-define-the-service-contract"></a>Definování kontraktu služby

1. Definujte kontrakt služby pomocí rozhraní označeného <xref:System.ServiceModel.ServiceContractAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> <xref:System.ServiceModel.Web.WebGetAttribute> atributem a, jak je znázorněno v následujícím kódu:

    [!code-csharp[htSoapWeb#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#0)]
    [!code-vb[htSoapWeb#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#0)]

    > [!NOTE]
    > Ve výchozím nastavení <xref:System.ServiceModel.Web.WebInvokeAttribute> namapuje volání post na operaci. Můžete však zadat metodu pro mapování na operaci zadáním parametru "Method =". <xref:System.ServiceModel.Web.WebGetAttribute>nemá parametr "Method =" a pouze mapuje volání GET na operaci služby.

2. Implementujte kontrakt služby, jak je znázorněno v následujícím kódu:

     [!code-csharp[htSoapWeb#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#1)]
     [!code-vb[htSoapWeb#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#1)]

## <a name="to-host-the-service"></a>Hostování služby

1. Vytvořte <xref:System.ServiceModel.ServiceHost> objekt, jak je znázorněno v následujícím kódu:

     [!code-csharp[htSoapWeb#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#2)]
     [!code-vb[htSoapWeb#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#2)]

2. Přidejte objekt <xref:System.ServiceModel.Description.ServiceEndpoint> with <xref:System.ServiceModel.BasicHttpBinding> pro koncový bod SOAP, jak je znázorněno v následujícím kódu:

     [!code-csharp[htSoapWeb#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#3)]
     [!code-vb[htSoapWeb#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#3)]

3. Přidejte objekt <xref:System.ServiceModel.Description.ServiceEndpoint> with <xref:System.ServiceModel.WebHttpBinding> pro koncový bod bez SOAP a přidejte <xref:System.ServiceModel.Description.WebHttpBehavior> ho do koncového bodu, jak je znázorněno v následujícím kódu:

     [!code-csharp[htSoapWeb#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#4)]
     [!code-vb[htSoapWeb#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#4)]

4. Zavolejte `Open()` na <xref:System.ServiceModel.ServiceHost> instanci pro otevření hostitele služby, jak je znázorněno v následujícím kódu:

     [!code-csharp[htSoapWeb#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#5)]
     [!code-vb[htSoapWeb#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#5)]

## <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a>Volání operací služby mapovaných na získání v aplikaci Internet Explorer

1. Spusťte Internet Explorer a zadejte " `http://localhost:8000/Web/EchoWithGet?s=Hello, world!` " a stiskněte klávesu ENTER. Adresa URL obsahuje základní adresu služby ( `http://localhost:8000/` ), relativní adresu koncového bodu (""), volanou operaci služby ("EchoWithGet") a otazník následovaný seznamem pojmenovaných parametrů oddělených ampersandem (&).

## <a name="to-call-service-operations-on-the-web-endpoint-in-code"></a>Volání operací služby na koncovém bodu webu v kódu

1. Vytvořte instanci <xref:System.ServiceModel.Web.WebChannelFactory%601> v rámci `using` bloku, jak je znázorněno v následujícím kódu.

     [!code-csharp[htSoapWeb#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#6)]
     [!code-vb[htSoapWeb#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#6)]

> [!NOTE]
> `Close()`se automaticky volá na kanálu na konci `using` bloku.

1. Vytvořte kanál a zavolejte službu, jak je znázorněno v následujícím kódu.

     [!code-csharp[htSoapWeb#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#8)]
     [!code-vb[htSoapWeb#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#8)]

## <a name="to-call-service-operations-on-the-soap-endpoint"></a>Volání operací služby na koncovém bodu SOAP

1. Vytvořte instanci <xref:System.ServiceModel.ChannelFactory> v rámci `using` bloku, jak je znázorněno v následujícím kódu.

    [!code-csharp[htSoapWeb#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#10)]
    [!code-vb[htSoapWeb#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#10)]

2. Vytvořte kanál a zavolejte službu, jak je znázorněno v následujícím kódu.

    [!code-csharp[htSoapWeb#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#11)]
    [!code-vb[htSoapWeb#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#11)]

## <a name="to-close-the-service-host"></a>Zavření hostitele služby

1. Ukončete hostitele služby, jak je znázorněno v následujícím kódu.

    [!code-csharp[htSoapWeb#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#9)]
    [!code-vb[htSoapWeb#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#9)]

## <a name="example"></a>Příklad

V následujícím seznamu je uveden úplný výpis kódu pro toto téma:

[!code-csharp[htSoapWeb#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#13)]
[!code-vb[htSoapWeb#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#13)]

## <a name="compiling-the-code"></a>Zkompilování kódu

 Při kompilování Service.cs, reference System. ServiceModel. dll a System. ServiceModel. Web. dll.

## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
- <xref:System.ServiceModel.Web.WebInvokeAttribute>
- <xref:System.ServiceModel.Web.WebServiceHost>
- <xref:System.ServiceModel.ChannelFactory>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [Programovací model webových služeb HTTP WCF](wcf-web-http-programming-model.md)
