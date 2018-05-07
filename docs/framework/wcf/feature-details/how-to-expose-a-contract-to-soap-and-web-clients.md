---
title: 'Postupy: vystavení kontraktu protokolu SOAP a webovými klienty'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bb765a48-12f2-430d-a54d-6f0c20f2a23a
ms.openlocfilehash: a9a730fe94d1df8c887a2eaf20c1e338bd056ed5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-expose-a-contract-to-soap-and-web-clients"></a>Postupy: vystavení kontraktu protokolu SOAP a webovými klienty
Ve výchozím nastavení Windows Communication Foundation (WCF) zpřístupňuje koncové body k dispozici pouze klientům protokolu SOAP. V [postupy: vytvoření základní služby WCF Web HTTP](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md), koncový bod je k dispozici pro klienty protokolu SOAP. Může nastat situace, kdy chcete zpřístupnit stejné smlouvy obou směrech, a to jako koncový bod webové a jako koncový bod protokolu SOAP. Toto téma ukazuje příklad toho, jak to udělat.  
  
### <a name="to-define-the-service-contract"></a>K definování kontraktu služby  
  
1.  Definování kontraktu služby pomocí rozhraní označené jako <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> a <xref:System.ServiceModel.Web.WebGetAttribute> atributy, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[htSoapWeb#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#0)]
     [!code-vb[htSoapWeb#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#0)]  
  
    > [!NOTE]
    >  Ve výchozím nastavení <xref:System.ServiceModel.Web.WebInvokeAttribute> mapuje POST volání operace. Můžete však zadat metodu pro mapování na operaci zadáním "metoda =" parametr. <xref:System.ServiceModel.Web.WebGetAttribute> nemá "metoda =" parametr a pouze mapy GET volání operace služby.  
  
2.  Implementujte kontrakt služby, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[htSoapWeb#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#1)]
     [!code-vb[htSoapWeb#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#1)]  
  
### <a name="to-host-the-service"></a>K hostování služby  
  
1.  Vytvoření <xref:System.ServiceModel.ServiceHost> objektu, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[htSoapWeb#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#2)]
     [!code-vb[htSoapWeb#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#2)]  
  
2.  Přidat <xref:System.ServiceModel.Description.ServiceEndpoint> s <xref:System.ServiceModel.BasicHttpBinding> SOAP koncového bodu, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[htSoapWeb#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#3)]
     [!code-vb[htSoapWeb#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#3)]  
  
3.  Přidat <xref:System.ServiceModel.Description.ServiceEndpoint> s <xref:System.ServiceModel.WebHttpBinding> pro koncový bod protokolu SOAP a přidejte <xref:System.ServiceModel.Description.WebHttpBehavior> ke koncovému bodu, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[htSoapWeb#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#4)]
     [!code-vb[htSoapWeb#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#4)]  
  
4.  Volání `Open()` na <xref:System.ServiceModel.ServiceHost> instance pro otevření hostitele služby, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[htSoapWeb#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#5)]
     [!code-vb[htSoapWeb#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#5)]  
  
### <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a>K volání operací služby namapované na GET v Internet Exploreru  
  
1.  Otevřete Internet Explorer a zadejte "`http://localhost:8000/Web/EchoWithGet?s=Hello, world!`" a stiskněte klávesu ENTER. Adresa URL obsahuje základní adresa služby ("http://localhost:8000/"), relativní adresa koncového bodu (""), operace služby k volání ("EchoWithGet") a otazník následuje seznam pojmenované parametry oddělených ampersandem (&).  
  
### <a name="to-call-service-operations-on-the-web-endpoint-in-code"></a>K volání operací služby na koncový bod webové v kódu  
  
1.  Vytvoření instance <xref:System.ServiceModel.Web.WebChannelFactory%601> v rámci `using` blokovat, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[htSoapWeb#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#6)]
     [!code-vb[htSoapWeb#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#6)]  
  
> [!NOTE]
>  `Close()` je automaticky volána na konci kanálu `using` bloku.  
  
1.  Vytvoření kanálu a volání služby, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[htSoapWeb#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#8)]
     [!code-vb[htSoapWeb#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#8)]  
  
### <a name="to-call-service-operations-on-the-soap-endpoint"></a>K volání operací služby na koncový bod protokolu SOAP  
  
1.  Vytvoření instance <xref:System.ServiceModel.ChannelFactory> v rámci `using` blokovat, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[htSoapWeb#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#10)]
     [!code-vb[htSoapWeb#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#10)]  
  
2.  Vytvoření kanálu a volání služby, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[htSoapWeb#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#11)]
     [!code-vb[htSoapWeb#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#11)]  
  
### <a name="to-close-the-service-host"></a>Zavřete hostitele služby  
  
1.  Zavřete hostitele služby, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[htSoapWeb#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#9)]
     [!code-vb[htSoapWeb#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#9)]  
  
## <a name="example"></a>Příklad  
 Zde je kód úplný výpis pro toto téma.  
  
 [!code-csharp[htSoapWeb#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#13)]
 [!code-vb[htSoapWeb#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#13)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Při kompilování Service.cs, odkaz System.ServiceModel.dll a System.ServiceModel.Web.dll.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>  
 <xref:System.ServiceModel.Web.WebInvokeAttribute>  
 <xref:System.ServiceModel.Web.WebServiceHost>  
 <xref:System.ServiceModel.ChannelFactory>  
 <xref:System.ServiceModel.Description.WebHttpBehavior>  
 [Programovací model webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
