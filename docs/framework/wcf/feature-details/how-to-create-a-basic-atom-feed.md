---
title: 'Postupy: Vytvoření základního informačního kanálu Atom'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6e0cacc1-9b11-4665-adb7-577a62626fd6
ms.openlocfilehash: 0317e7b42f589b31f5c77b89d26cb46815f13054
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599045"
---
# <a name="how-to-create-a-basic-atom-feed"></a>Postupy: Vytvoření základního informačního kanálu Atom
Windows Communication Foundation (WCF) umožňuje vytvořit službu, která zveřejňuje kanál syndikace. Toto téma popisuje, jak vytvořit službu syndikace, která zveřejňuje kanál syndikace Atom.  
  
### <a name="to-create-a-basic-syndication-service"></a>Vytvoření služby syndikace na úrovni Basic  
  
1. Definujte kontrakt služby pomocí rozhraní označeného <xref:System.ServiceModel.Web.WebGetAttribute> atributem. Každá operace, která je vystavena jako syndikační kanál, by měla vracet <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> objekt.  
  
     [!code-csharp[htAtomBasic#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#0)]
     [!code-vb[htAtomBasic#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#0)]  
  
    > [!NOTE]
    > Všechny operace služby, které používají, <xref:System.ServiceModel.Web.WebGetAttribute> jsou mapovány na požadavky HTTP GET. K namapování operace na jinou metodu HTTP použijte <xref:System.ServiceModel.Web.WebInvokeAttribute> místo nich. Další informace naleznete v tématu [How to: Create a Basic WCF web http Service](how-to-create-a-basic-wcf-web-http-service.md).  
  
2. Implementujte kontrakt služby.  
  
     [!code-csharp[htAtomBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#1)]
     [!code-vb[htAtomBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#1)]  
  
3. Vytvořte <xref:System.ServiceModel.Syndication.SyndicationFeed> objekt a přidejte jeho autora, kategorii a popis.  
  
     [!code-csharp[htAtomBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#2)]
     [!code-vb[htAtomBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#2)]  
  
4. Vytvořte několik <xref:System.ServiceModel.Syndication.SyndicationItem> objektů.  
  
     [!code-csharp[htAtomBasic#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#3)]
     [!code-vb[htAtomBasic#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#3)]  
  
5. Přidejte <xref:System.ServiceModel.Syndication.SyndicationItem> objekty do informačního kanálu.  
  
     [!code-csharp[htAtomBasic#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#4)]
     [!code-vb[htAtomBasic#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#4)]  
  
6. Vrácení informačního kanálu  
  
     [!code-csharp[htAtomBasic#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#5)]
     [!code-vb[htAtomBasic#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a>Hostování služby  
  
1. Vytvořte <xref:System.ServiceModel.Web.WebServiceHost> objekt.  
  
     [!code-csharp[htAtomBasic#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#6)]
     [!code-vb[htAtomBasic#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#6)]  
  
2. Otevřete hostitele služby, načtěte kanál ze služby, zobrazte informační kanál a počkejte, než uživatel stiskne klávesu ENTER.  
  
     [!code-csharp[htAtomBasic#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#8)]
     [!code-vb[htAtomBasic#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a>Volání metody getblog () pomocí protokolu HTTP GET  
  
1. Otevřete Internet Explorer, zadejte následující adresu URL a stiskněte klávesu ENTER:`http://localhost:8000/BlogService/GetBlog`  
  
     Adresa URL obsahuje základní adresu služby ( `http://localhost:8000/BlogService` ), relativní adresu koncového bodu a volanou operaci služby.  
  
### <a name="to-call-getblog-from-code"></a>Volání metody getblog () z kódu  
  
1. Vytvořte <xref:System.Xml.XmlReader> se základní adresou a metodou, kterou voláte.  
  
     [!code-csharp[htAtomBasic#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#9)]
     [!code-vb[htAtomBasic#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#9)]  
  
2. Zavolejte statickou <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> metodu a předejte ji <xref:System.Xml.XmlReader> právě vytvořenou.  
  
     [!code-csharp[htAtomBasic#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#10)]
     [!code-vb[htAtomBasic#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#10)]  
  
     Tím se vyvolá operace služby a naplní se <xref:System.ServiceModel.Syndication.SyndicationFeed> formátovací modul vrácený funkcí operace služby.  
  
3. Přístup k objektu informačního kanálu  
  
     [!code-csharp[htAtomBasic#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#11)]
     [!code-vb[htAtomBasic#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#11)]  
  
## <a name="example"></a>Příklad  
 Následuje úplný výpis kódu pro tento příklad.  
  
 [!code-csharp[htAtomBasic#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#12)]
 [!code-vb[htAtomBasic#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#12)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Při kompilování předchozího kódu, odkazuje na System. ServiceModel. dll a System. ServiceModel. Web. dll.  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
