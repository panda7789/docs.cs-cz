---
title: 'Postupy: Vytvoření základního kanálu RSS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 431879b8-a5f8-4947-ad1e-4768c726aca8
ms.openlocfilehash: 5bab8b5a19f33f8dcfcc5a5f5d882309a4b1cc99
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781443"
---
# <a name="how-to-create-a-basic-rss-feed"></a>Postupy: Vytvoření základního kanálu RSS
Windows Communication Foundation (WCF) umožňuje vytvořit službu, která zveřejňuje informačního kanálu syndikace. Toto téma popisuje, jak vytvořit služby syndikace, který zpřístupňuje informačního kanálu syndikace RSS.  
  
### <a name="to-create-a-basic-syndication-service"></a>Chcete-li vytvořit základní syndikační služby  
  
1. Definování kontraktu služby pomocí rozhraní označené <xref:System.ServiceModel.Web.WebGetAttribute> atribut. Každá operace, která je vystavena jako informační kanál syndikace by mělo vrátit <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> objektu.  
  
     [!code-csharp[htRssBasic#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#0)]
     [!code-vb[htRssBasic#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#0)]  
  
    > [!NOTE]
    >  Všechny operace služby, které se vztahují <xref:System.ServiceModel.Web.WebGetAttribute> atribut se mapují na požadavky HTTP GET. Chcete-li namapovat operace jinou metodu HTTP, použijte <xref:System.ServiceModel.Web.WebInvokeAttribute> místo. Další informace najdete v tématu [jak: Vytvoření webové služby HTTP WCF základní](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md).  
  
2. Implementace kontraktu služby.  
  
     [!code-csharp[htRssBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#1)]
     [!code-vb[htRssBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#1)]  
  
3. Vytvoření <xref:System.ServiceModel.Syndication.SyndicationFeed> objektu a přidejte Autor, kategorie a popis.  
  
     [!code-csharp[htRssBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#2)]
     [!code-vb[htRssBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#2)]  
  
4. Vytvoření několika <xref:System.ServiceModel.Syndication.SyndicationItem> objekty.  
  
     [!code-csharp[htRssBasic#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#3)]
     [!code-vb[htRssBasic#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#3)]  
  
5. Přidat <xref:System.ServiceModel.Syndication.SyndicationItem> do informačního kanálu.  
  
     [!code-csharp[htRssBasic#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#4)]
     [!code-vb[htRssBasic#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#4)]  
  
6. Vrátí informačního kanálu.  
  
     [!code-csharp[htRssBasic#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#5)]
     [!code-vb[htRssBasic#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#5)]  
  
### <a name="to-host-a-service"></a>K hostování služby  
  
1. Vytvoření <xref:System.ServiceModel.Web.WebServiceHost> objektu.  
  
     [!code-csharp[htRssBasic#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#6)]
     [!code-vb[htRssBasic#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#6)]  
  
2. Otevření hostitele služby a počkejte, až uživatel stiskne klávesu ENTER.  
  
     [!code-csharp[htRssBasic#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#8)]
     [!code-vb[htRssBasic#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a>Chcete-li volat GetBlog() s HTTP GET  
  
1. Spusťte aplikaci Internet Explorer a zadejte následující adresu URL, stiskněte klávesu ENTER: `http://localhost:8000/BlogService/GetBlog`. Adresa URL obsahuje základní adresa služby (`http://localhost:8000/BlogService`), relativní adresu koncového bodu a operace služby, která volá.  
  
### <a name="to-call-getblog-from-code"></a>GetBlog() volat z kódu  
  
1. Vytvoření <xref:System.Xml.XmlReader> k základní adrese a metodu voláte.  
  
     [!code-csharp[htRssBasic#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#9)]
     [!code-vb[htRssBasic#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#9)]  
  
2. Zavolejte statickou <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> metodu <xref:System.Xml.XmlReader> jste právě vytvořili.  
  
     [!code-csharp[htRssBasic#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#10)]
     [!code-vb[htRssBasic#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#10)]  
  
     To vyvolá operaci služby a naplní nový <xref:System.ServiceModel.Syndication.SyndicationFeed> formátování vrácená z operace služby.  
  
3. Přístup k objekt informačního kanálu.  
  
     [!code-csharp[htRssBasic#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#11)]
     [!code-vb[htRssBasic#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#11)]  
  
## <a name="example"></a>Příklad  
 Následuje úplný výpis v tomto příkladu kódu.  
  
 [!code-csharp[htRssBasic#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#12)]
 [!code-vb[htRssBasic#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#12)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Při kompilaci předchozí kód, odkazovat System.ServiceModel.dll a System.ServiceModel.Web.dll.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
