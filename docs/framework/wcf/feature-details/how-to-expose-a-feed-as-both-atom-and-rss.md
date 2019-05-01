---
title: 'Postupy: Zveřejnění informačního kanálu ve formátu Atom i RSS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fe374932-67f5-487d-9325-f868812b92e4
ms.openlocfilehash: 824d2a08ddd36317fcdb8caa1690decb2f9c432a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62039557"
---
# <a name="how-to-expose-a-feed-as-both-atom-and-rss"></a>Postupy: Zveřejnění informačního kanálu ve formátu Atom i RSS
Windows Communication Foundation (WCF) umožňuje vytvořit službu, která zveřejňuje informačního kanálu syndikace. Toto téma popisuje, jak vytvořit služby syndikace, který zpřístupňuje kanálem syndikace Atom 1.0 i RSS 2.0. Tato služba poskytuje jeden koncový bod, který může vrátit buď souhrnný formát, který. Pro zjednodušení služby používané v tomto příkladu je nezávislý hostované. V produkčním prostředí by být hostované služby tohoto typu v rámci služby IIS nebo WAS. Další informace o různých WCF možnosti hostování naleznete v tématu [Hosting](../../../../docs/framework/wcf/feature-details/hosting.md).  
  
### <a name="to-create-a-basic-syndication-service"></a>Chcete-li vytvořit základní syndikační služby  
  
1. Definování kontraktu služby pomocí rozhraní označené <xref:System.ServiceModel.Web.WebGetAttribute> atribut. Každá operace, která je vystavena jako kanálu syndikace vrátí <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> objektu. Poznámka: parametry <xref:System.ServiceModel.Web.WebGetAttribute>. `UriTemplate` Určuje adresu URL použít k vyvolání operace této služby. Řetězec pro tento parametr obsahuje literály a proměnné ve složených závorkách ({*formátu*}). Tato proměnná odpovídá operaci služby `format` parametru. Další informace naleznete v tématu <xref:System.UriTemplate>. `BodyStyle` ovlivňuje, jak se zapisují zprávy, které tuto operaci služba odesílá a přijímá. <xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare> Určuje, že data odesílaná do a z této operace služby nejsou zabalené službou infrastruktury definované elementy XML. Další informace naleznete v tématu <xref:System.ServiceModel.Web.WebMessageBodyStyle>.  
  
     [!code-csharp[htAtomRss#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#0)]
     [!code-vb[htAtomRss#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#0)]  
  
    > [!NOTE]
    >  Použití <xref:System.ServiceModel.ServiceKnownTypeAttribute> určit typy, které jsou vráceny pomocí operací služby v tomto rozhraní.  
  
2. Implementace kontraktu služby.  
  
     [!code-csharp[htAtomRss#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#1)]
     [!code-vb[htAtomRss#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#1)]  
  
3. Vytvoření <xref:System.ServiceModel.Syndication.SyndicationFeed> objektu a přidejte Autor, kategorie a popis.  
  
     [!code-csharp[htAtomRss#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#2)]
     [!code-vb[htAtomRss#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#2)]  
  
4. Vytvoření několika <xref:System.ServiceModel.Syndication.SyndicationItem> objekty.  
  
     [!code-csharp[htAtomRss#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#3)]
     [!code-vb[htAtomRss#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#3)]  
  
5. Přidat <xref:System.ServiceModel.Syndication.SyndicationItem> objekty do informačního kanálu.  
  
     [!code-csharp[htAtomRss#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#4)]
     [!code-vb[htAtomRss#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#4)]  
  
6. Pomocí parametru formátu vrátit požadovanému formátu.  
  
     [!code-csharp[htAtomRss#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#5)]
     [!code-vb[htAtomRss#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a>K hostování služby  
  
1. Vytvoření <xref:System.ServiceModel.Web.WebServiceHost> objektu. <xref:System.ServiceModel.Web.WebServiceHost> Třída automaticky přidá koncový bod na základní adrese služby, pokud je zadaná v kódu nebo konfigurace. V této ukázce jsou určeny žádné koncové body tak výchozí koncový bod je přístupný.  
  
     [!code-csharp[htAtomRss#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#6)]
     [!code-vb[htAtomRss#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#6)]  
  
2. Otevření hostitele služby, načtení informačního kanálu ze služby, zobrazit informační kanál a čekat, uživatel stisknout klávesu ENTER.  
  
     [!code-csharp[htAtomRss#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#8)]
     [!code-vb[htAtomRss#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a>Chcete-li volat GetBlog s HTTP GET  
  
1. Spusťte aplikaci Internet Explorer a zadejte následující adresu URL, stiskněte klávesu ENTER: `http://localhost:8000/BlogService/GetBlog`.
  
     Adresa URL obsahuje základní adresa služby (`http://localhost:8000/BlogService`), relativní adresu koncového bodu a operace služby, která volá.  
  
### <a name="to-call-getblog-from-code"></a>GetBlog() volat z kódu  
  
1. Vytvoření <xref:System.Xml.XmlReader> k základní adrese a metodu voláte.  
  
     [!code-csharp[htAtomRss#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#9)]
     [!code-vb[htAtomRss#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#9)]  
  
2. Zavolejte statickou <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> metodu <xref:System.Xml.XmlReader> jste právě vytvořili.  
  
     [!code-csharp[htAtomRss#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#10)]
     [!code-vb[htAtomRss#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#10)]  
  
     To vyvolá operaci služby a naplní nový <xref:System.ServiceModel.Syndication.SyndicationFeed> formátování vrácená z operace služby.  
  
3. Přístup k objekt informačního kanálu.  
  
     [!code-csharp[htAtomRss#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#11)]
     [!code-vb[htAtomRss#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#11)]  
  
## <a name="example"></a>Příklad  
 Následuje úplný výpis v tomto příkladu kódu.  
  
 [!code-csharp[htAtomRss#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#12)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Při kompilaci předchozí kód, odkazovat System.ServiceModel.dll a System.ServiceModel.Web.dll.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
