---
title: 'Postupy: Zveřejnění informačního kanálu ve formátu Atom i RSS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fe374932-67f5-487d-9325-f868812b92e4
ms.openlocfilehash: e4ce1fa7b494c2317a1bddc57ee6b150c84b9a96
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593143"
---
# <a name="how-to-expose-a-feed-as-both-atom-and-rss"></a>Postupy: Zveřejnění informačního kanálu ve formátu Atom i RSS
Windows Communication Foundation (WCF) umožňuje vytvořit službu, která zveřejňuje kanál syndikace. Toto téma popisuje, jak vytvořit službu syndikace, která zveřejňuje kanál syndikace pomocí Atom 1,0 a RSS 2,0. Tato služba zpřístupňuje jeden koncový bod, který může vracet buď formát syndikace. Pro jednoduchost služby použité v této ukázce se jedná o samoobslužné hostování. V produkčním prostředí by služba tohoto typu byla hostována službou IIS nebo WAS. Další informace o různých možnostech hostování WCF naleznete v tématu [hosting](hosting.md).  
  
### <a name="to-create-a-basic-syndication-service"></a>Vytvoření služby syndikace na úrovni Basic  
  
1. Definujte kontrakt služby pomocí rozhraní označeného <xref:System.ServiceModel.Web.WebGetAttribute> atributem. Každá operace, která je vystavena jako syndikační kanál, vrací <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> objekt. Všimněte si parametrů pro <xref:System.ServiceModel.Web.WebGetAttribute> . `UriTemplate`Určuje adresu URL, která se používá k vyvolání této operace služby. Řetězec pro tento parametr obsahuje literály a proměnnou ve složených závorkách ({*Format*}). Tato proměnná odpovídá parametru operace služby `format` . Další informace naleznete v tématu <xref:System.UriTemplate>. `BodyStyle`má vliv na zápis zpráv, které tato operace služby odesílá a přijímá. <xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare>Určuje, že data odesílaná do a z této operace služby nejsou zabalena pomocí prvků XML definovaných v infrastruktuře. Další informace naleznete v tématu <xref:System.ServiceModel.Web.WebMessageBodyStyle>.  
  
     [!code-csharp[htAtomRss#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#0)]
     [!code-vb[htAtomRss#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#0)]  
  
    > [!NOTE]
    > Použijte <xref:System.ServiceModel.ServiceKnownTypeAttribute> k určení typů, které jsou vráceny operacemi služby v tomto rozhraní.  
  
2. Implementujte kontrakt služby.  
  
     [!code-csharp[htAtomRss#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#1)]
     [!code-vb[htAtomRss#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#1)]  
  
3. Vytvořte <xref:System.ServiceModel.Syndication.SyndicationFeed> objekt a přidejte jeho autora, kategorii a popis.  
  
     [!code-csharp[htAtomRss#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#2)]
     [!code-vb[htAtomRss#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#2)]  
  
4. Vytvořte několik <xref:System.ServiceModel.Syndication.SyndicationItem> objektů.  
  
     [!code-csharp[htAtomRss#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#3)]
     [!code-vb[htAtomRss#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#3)]  
  
5. Přidejte <xref:System.ServiceModel.Syndication.SyndicationItem> objekty do informačního kanálu.  
  
     [!code-csharp[htAtomRss#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#4)]
     [!code-vb[htAtomRss#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#4)]  
  
6. Pro vrácení požadovaného formátu použijte parametr format.  
  
     [!code-csharp[htAtomRss#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#5)]
     [!code-vb[htAtomRss#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a>Hostování služby  
  
1. Vytvořte <xref:System.ServiceModel.Web.WebServiceHost> objekt. <xref:System.ServiceModel.Web.WebServiceHost>Třída automaticky přidá koncový bod na základní adrese služby, není-li v kódu nebo konfiguraci zadána jedna. V této ukázce nejsou zadány žádné koncové body, aby byl výchozí koncový bod vystaven.  
  
     [!code-csharp[htAtomRss#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#6)]
     [!code-vb[htAtomRss#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#6)]  
  
2. Otevřete hostitele služby, načtěte kanál ze služby, zobrazte informační kanál a počkejte, než uživatel stiskne klávesu ENTER.  
  
     [!code-csharp[htAtomRss#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#8)]
     [!code-vb[htAtomRss#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a>Volání metody getblog s protokolem HTTP GET  
  
1. Otevřete Internet Explorer, zadejte následující adresu URL a stiskněte klávesu ENTER: `http://localhost:8000/BlogService/GetBlog` .
  
     Adresa URL obsahuje základní adresu služby ( `http://localhost:8000/BlogService` ), relativní adresu koncového bodu a volanou operaci služby.  
  
### <a name="to-call-getblog-from-code"></a>Volání metody getblog () z kódu  
  
1. Vytvořte <xref:System.Xml.XmlReader> se základní adresou a metodou, kterou voláte.  
  
     [!code-csharp[htAtomRss#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#9)]
     [!code-vb[htAtomRss#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#9)]  
  
2. Zavolejte statickou <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> metodu a předejte ji <xref:System.Xml.XmlReader> právě vytvořenou.  
  
     [!code-csharp[htAtomRss#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#10)]
     [!code-vb[htAtomRss#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#10)]  
  
     Tím se vyvolá operace služby a naplní se <xref:System.ServiceModel.Syndication.SyndicationFeed> formátovací modul vrácený funkcí operace služby.  
  
3. Přístup k objektu informačního kanálu  
  
     [!code-csharp[htAtomRss#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#11)]
     [!code-vb[htAtomRss#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#11)]  
  
## <a name="example"></a>Příklad  
 Následuje úplný výpis kódu pro tento příklad.  
  
 [!code-csharp[htAtomRss#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#12)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Při kompilování předchozího kódu, odkazuje na System. ServiceModel. dll a System. ServiceModel. Web. dll.  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
