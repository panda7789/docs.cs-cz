---
title: 'Postupy: Vytvoření základního informačního kanálu Atom'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 6e0cacc1-9b11-4665-adb7-577a62626fd6
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 26e5bf0771e3b8d700efeaf4f63b9866534db68a
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-create-a-basic-atom-feed"></a>Postupy: Vytvoření základního informačního kanálu Atom
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Umožňuje vytvořit službu, která zveřejňuje syndikace informačního kanálu. Toto téma popisuje postup vytvoření syndikace služby, která zveřejňuje Atom syndikace informačního kanálu.  
  
### <a name="to-create-a-basic-syndication-service"></a>Vytvoření služby základní syndikace  
  
1.  Definování kontraktu služby pomocí rozhraní označené jako <xref:System.ServiceModel.Web.WebGetAttribute> atribut. Každé operace, která je vystavená, protože by měla vrátit syndikace informační kanál <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> objektu.  
  
     [!code-csharp[htAtomBasic#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#0)]
     [!code-vb[htAtomBasic#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#0)]  
  
    > [!NOTE]
    >  Všechny operace služby, které se vztahují <xref:System.ServiceModel.Web.WebGetAttribute> jsou namapované na požadavky HTTP GET. Pokud chcete mapovat tuto operaci na jinou metodu HTTP, používat <xref:System.ServiceModel.Web.WebInvokeAttribute> místo. Další informace najdete v tématu [postupy: vytvoření základní služby WCF Web HTTP](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md).  
  
2.  Implementujte kontrakt služby.  
  
     [!code-csharp[htAtomBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#1)]
     [!code-vb[htAtomBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#1)]  
  
3.  Vytvoření <xref:System.ServiceModel.Syndication.SyndicationFeed> objektu a přidejte vytváření, kategorie a popis.  
  
     [!code-csharp[htAtomBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#2)]
     [!code-vb[htAtomBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#2)]  
  
4.  Vytvořit několik <xref:System.ServiceModel.Syndication.SyndicationItem> objekty.  
  
     [!code-csharp[htAtomBasic#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#3)]
     [!code-vb[htAtomBasic#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#3)]  
  
5.  Přidat <xref:System.ServiceModel.Syndication.SyndicationItem> objekty k informačnímu kanálu.  
  
     [!code-csharp[htAtomBasic#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#4)]
     [!code-vb[htAtomBasic#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#4)]  
  
6.  Vrátí informačního kanálu.  
  
     [!code-csharp[htAtomBasic#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#5)]
     [!code-vb[htAtomBasic#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a>K hostování služby  
  
1.  Vytvoření <xref:System.ServiceModel.Web.WebServiceHost> objektu.  
  
     [!code-csharp[htAtomBasic#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#6)]
     [!code-vb[htAtomBasic#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#6)]  
  
2.  Otevření hostitele služby, načtěte informačního kanálu ze služby, zobrazit informační kanál a počkejte uživateli stiskněte klávesu ENTER.  
  
     [!code-csharp[htAtomBasic#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#8)]
     [!code-vb[htAtomBasic#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a>K volání GetBlog() s HTTP GET  
  
1.  Otevřete Internet Explorer, zadejte následující adresu URL a stiskněte klávesu ENTER: http://localhost:8000/BlogService/GetBlog  
  
     Adresa URL obsahuje základní adresa služby (http://localhost:8000/BlogService), relativní adresa koncového bodu a volat operace služby.  
  
### <a name="to-call-getblog-from-code"></a>GetBlog() volat z kódu  
  
1.  Vytvoření <xref:System.Xml.XmlReader> s základní adresu a při volání metody.  
  
     [!code-csharp[htAtomBasic#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#9)]
     [!code-vb[htAtomBasic#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#9)]  
  
2.  Zavolejte statickou <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> předávání v případě metody <xref:System.Xml.XmlReader> jste právě vytvořili.  
  
     [!code-csharp[htAtomBasic#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#10)]
     [!code-vb[htAtomBasic#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#10)]  
  
     To vyvolá operaci služby a naplní novou <xref:System.ServiceModel.Syndication.SyndicationFeed> k formátování vrácená z operace služby.  
  
3.  Přístup k objekt informačního kanálu.  
  
     [!code-csharp[htAtomBasic#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#11)]
     [!code-vb[htAtomBasic#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#11)]  
  
## <a name="example"></a>Příklad  
 Zde je úplný výpis pro tento příklad kódu.  
  
 [!code-csharp[htAtomBasic#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#12)]
 [!code-vb[htAtomBasic#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#12)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Při kompilování předchozí kód, odkazuje System.ServiceModel.dll a System.ServiceModel.Web.dll.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>
