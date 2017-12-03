---
title: "Postupy: Vytvoření základního kanálu RSS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 431879b8-a5f8-4947-ad1e-4768c726aca8
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 54b9932e081ab5f35b3c15c9e7d4025dfbb3703b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-basic-rss-feed"></a>Postupy: Vytvoření základního kanálu RSS
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Umožňuje vytvořit službu, která zveřejňuje syndikace informačního kanálu. Toto téma popisuje postup vytvoření syndikace služby, která zveřejňuje RSS syndikace informačního kanálu.  
  
### <a name="to-create-a-basic-syndication-service"></a>Vytvoření služby základní syndikace  
  
1.  Definování kontraktu služby pomocí rozhraní označené jako <xref:System.ServiceModel.Web.WebGetAttribute> atribut. Každé operace, která je vystavená, protože by měla vrátit syndikace informační kanál <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> objektu.  
  
     [!code-csharp[htRssBasic#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#0)]
     [!code-vb[htRssBasic#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#0)]  
  
    > [!NOTE]
    >  Všechny operace služby, které se vztahují <xref:System.ServiceModel.Web.WebGetAttribute> atribut jsou namapované na požadavky HTTP GET. Pokud chcete mapovat tuto operaci na jinou metodu HTTP, používat <xref:System.ServiceModel.Web.WebInvokeAttribute> místo. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Postupy: vytvoření webové služby HTTP WCF základní](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md).  
  
2.  Implementujte kontrakt služby.  
  
     [!code-csharp[htRssBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#1)]
     [!code-vb[htRssBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#1)]  
  
3.  Vytvoření <xref:System.ServiceModel.Syndication.SyndicationFeed> objektu a přidejte vytváření, kategorie a popis.  
  
     [!code-csharp[htRssBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#2)]
     [!code-vb[htRssBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#2)]  
  
4.  Vytvořit několik <xref:System.ServiceModel.Syndication.SyndicationItem> objekty.  
  
     [!code-csharp[htRssBasic#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#3)]
     [!code-vb[htRssBasic#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#3)]  
  
5.  Přidat <xref:System.ServiceModel.Syndication.SyndicationItem> k informačnímu kanálu.  
  
     [!code-csharp[htRssBasic#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#4)]
     [!code-vb[htRssBasic#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#4)]  
  
6.  Vrátí informačního kanálu.  
  
     [!code-csharp[htRssBasic#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#5)]
     [!code-vb[htRssBasic#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#5)]  
  
### <a name="to-host-a-service"></a>K hostování služby  
  
1.  Vytvoření <xref:System.ServiceModel.Web.WebServiceHost> objektu.  
  
     [!code-csharp[htRssBasic#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#6)]
     [!code-vb[htRssBasic#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#6)]  
  
2.  Otevření hostitele služby a počkejte, dokud uživatel stiskne klávesu ENTER.  
  
     [!code-csharp[htRssBasic#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#8)]
     [!code-vb[htRssBasic#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a>K volání GetBlog() s HTTP GET  
  
1.  Otevřete Internet Explorer, zadejte následující adresu URL a stiskněte klávesu ENTER: http://localhost: 8000/BlogService/GetBlog. Adresa URL obsahuje základní adresa služby (http://localhost: 8000/BlogService), relativní adresa koncového bodu a volat operace služby.  
  
### <a name="to-call-getblog-from-code"></a>GetBlog() volat z kódu  
  
1.  Vytvoření <xref:System.Xml.XmlReader> s základní adresu a při volání metody.  
  
     [!code-csharp[htRssBasic#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#9)]
     [!code-vb[htRssBasic#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#9)]  
  
2.  Zavolejte statickou <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> předávání v případě metody <xref:System.Xml.XmlReader> jste právě vytvořili.  
  
     [!code-csharp[htRssBasic#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#10)]
     [!code-vb[htRssBasic#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#10)]  
  
     To vyvolá operaci služby a naplní novou <xref:System.ServiceModel.Syndication.SyndicationFeed> k formátování vrácená z operace služby.  
  
3.  Přístup k objekt informačního kanálu.  
  
     [!code-csharp[htRssBasic#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#11)]
     [!code-vb[htRssBasic#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#11)]  
  
## <a name="example"></a>Příklad  
 Zde je úplný výpis pro tento příklad kódu.  
  
 [!code-csharp[htRssBasic#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#12)]
 [!code-vb[htRssBasic#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#12)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Při kompilování předchozí kód, odkazuje System.ServiceModel.dll a System.ServiceModel.Web.dll.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>
