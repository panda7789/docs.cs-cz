---
title: 'Postupy: Vytvoření základního informačního kanálu Atom'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6e0cacc1-9b11-4665-adb7-577a62626fd6
ms.openlocfilehash: 11aa71f82af5a1bd764a4cc9e3514a795d559fc2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59311848"
---
# <a name="how-to-create-a-basic-atom-feed"></a>Postupy: Vytvoření základního informačního kanálu Atom
Windows Communication Foundation (WCF) umožňuje vytvořit službu, která zveřejňuje informačního kanálu syndikace. Toto téma popisuje, jak vytvořit služby syndikace, který zpřístupňuje informačního kanálu syndikace Atom.  
  
### <a name="to-create-a-basic-syndication-service"></a>Chcete-li vytvořit základní syndikační služby  
  
1. Definování kontraktu služby pomocí rozhraní označené <xref:System.ServiceModel.Web.WebGetAttribute> atribut. Každá operace, která je vystavena jako informační kanál syndikace by mělo vrátit <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> objektu.  
  
     [!code-csharp[htAtomBasic#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#0)]
     [!code-vb[htAtomBasic#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#0)]  
  
    > [!NOTE]
    >  Všechny operace služby, které se vztahují <xref:System.ServiceModel.Web.WebGetAttribute> jsou mapovány na požadavky HTTP GET. Chcete-li namapovat operace jinou metodu HTTP, použijte <xref:System.ServiceModel.Web.WebInvokeAttribute> místo. Další informace najdete v tématu [jak: Vytvoření webové služby HTTP WCF základní](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md).  
  
2. Implementace kontraktu služby.  
  
     [!code-csharp[htAtomBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#1)]
     [!code-vb[htAtomBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#1)]  
  
3. Vytvoření <xref:System.ServiceModel.Syndication.SyndicationFeed> objektu a přidejte Autor, kategorie a popis.  
  
     [!code-csharp[htAtomBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#2)]
     [!code-vb[htAtomBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#2)]  
  
4. Vytvoření několika <xref:System.ServiceModel.Syndication.SyndicationItem> objekty.  
  
     [!code-csharp[htAtomBasic#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#3)]
     [!code-vb[htAtomBasic#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#3)]  
  
5. Přidat <xref:System.ServiceModel.Syndication.SyndicationItem> objekty do informačního kanálu.  
  
     [!code-csharp[htAtomBasic#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#4)]
     [!code-vb[htAtomBasic#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#4)]  
  
6. Vrátí informačního kanálu.  
  
     [!code-csharp[htAtomBasic#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#5)]
     [!code-vb[htAtomBasic#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a>K hostování služby  
  
1. Vytvoření <xref:System.ServiceModel.Web.WebServiceHost> objektu.  
  
     [!code-csharp[htAtomBasic#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#6)]
     [!code-vb[htAtomBasic#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#6)]  
  
2. Otevření hostitele služby, načtení informačního kanálu ze služby, zobrazit informační kanál a čekat, uživatel stisknout klávesu ENTER.  
  
     [!code-csharp[htAtomBasic#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#8)]
     [!code-vb[htAtomBasic#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a>Chcete-li volat GetBlog() s HTTP GET  
  
1. Spusťte aplikaci Internet Explorer, zadejte následující adresu URL a stiskněte klávesu ENTER: `http://localhost:8000/BlogService/GetBlog`  
  
     Adresa URL obsahuje základní adresa služby (`http://localhost:8000/BlogService`), relativní adresu koncového bodu a operace služby, která volá.  
  
### <a name="to-call-getblog-from-code"></a>GetBlog() volat z kódu  
  
1. Vytvoření <xref:System.Xml.XmlReader> k základní adrese a metodu voláte.  
  
     [!code-csharp[htAtomBasic#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#9)]
     [!code-vb[htAtomBasic#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#9)]  
  
2. Zavolejte statickou <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> metodu <xref:System.Xml.XmlReader> jste právě vytvořili.  
  
     [!code-csharp[htAtomBasic#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#10)]
     [!code-vb[htAtomBasic#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#10)]  
  
     To vyvolá operaci služby a naplní nový <xref:System.ServiceModel.Syndication.SyndicationFeed> formátování vrácená z operace služby.  
  
3. Přístup k objekt informačního kanálu.  
  
     [!code-csharp[htAtomBasic#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#11)]
     [!code-vb[htAtomBasic#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#11)]  
  
## <a name="example"></a>Příklad  
 Následuje úplný výpis v tomto příkladu kódu.  
  
 [!code-csharp[htAtomBasic#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#12)]
 [!code-vb[htAtomBasic#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#12)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Při kompilaci předchozí kód, odkazovat System.ServiceModel.dll a System.ServiceModel.Web.dll.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
