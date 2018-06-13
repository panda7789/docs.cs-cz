---
title: 'Postupy: vystavení informačního kanálu jako Atom a RSS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fe374932-67f5-487d-9325-f868812b92e4
ms.openlocfilehash: 4780e43679d461509911a4abda689a0c16112e4a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493422"
---
# <a name="how-to-expose-a-feed-as-both-atom-and-rss"></a>Postupy: vystavení informačního kanálu jako Atom a RSS
Windows Communication Foundation (WCF) umožňuje vytvořit službu, která zveřejňuje syndikace informačního kanálu. Toto téma popisuje postup vytvoření syndikace služby, která zveřejňuje syndikace kanálu pomocí RSS 2.0 a Atom 1.0. Tato služba zpřístupní jeden koncový bod, který může vrátit buď syndikace formátu. Pro zjednodušení službu používanou v této ukázce je sám sebou hostované. V produkčním prostředí by se v rámci služby IIS nebo WAS hostované služby tohoto typu. Další informace o různých WCF hostování možnosti najdete v tématu [hostitelský](../../../../docs/framework/wcf/feature-details/hosting.md).  
  
### <a name="to-create-a-basic-syndication-service"></a>Vytvoření služby základní syndikace  
  
1.  Definování kontraktu služby pomocí rozhraní označené jako <xref:System.ServiceModel.Web.WebGetAttribute> atribut. Každé operace, který je zveřejněný jako syndikace kanálu vrátí <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> objektu. Poznámka: parametry <xref:System.ServiceModel.Web.WebGetAttribute>. `UriTemplate` Určuje adresu URL použije k vyvolání operace této služby. Řetězec pro tento parametr obsahuje literály a proměnnou v závorkách ({*formát*}). Tato proměnná odpovídá operace služby `format` parametr. Další informace naleznete v tématu <xref:System.UriTemplate>. `BodyStyle` ovlivňuje, jak se zapisují zprávy, které tuto operaci služby odesílá a přijímá. <xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare> Určuje, že data odesílaná do a z této operace služby nejsou zabalené službou infrastruktury definované elementů XML. Další informace naleznete v tématu <xref:System.ServiceModel.Web.WebMessageBodyStyle>.  
  
     [!code-csharp[htAtomRss#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#0)]
     [!code-vb[htAtomRss#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#0)]  
  
    > [!NOTE]
    >  Použití <xref:System.ServiceModel.ServiceKnownTypeAttribute> určit typy, které jsou vráceny operacemi služby v tomto rozhraní.  
  
2.  Implementujte kontrakt služby.  
  
     [!code-csharp[htAtomRss#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#1)]
     [!code-vb[htAtomRss#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#1)]  
  
3.  Vytvoření <xref:System.ServiceModel.Syndication.SyndicationFeed> objektu a přidejte vytváření, kategorie a popis.  
  
     [!code-csharp[htAtomRss#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#2)]
     [!code-vb[htAtomRss#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#2)]  
  
4.  Vytvořit několik <xref:System.ServiceModel.Syndication.SyndicationItem> objekty.  
  
     [!code-csharp[htAtomRss#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#3)]
     [!code-vb[htAtomRss#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#3)]  
  
5.  Přidat <xref:System.ServiceModel.Syndication.SyndicationItem> objekty k informačnímu kanálu.  
  
     [!code-csharp[htAtomRss#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#4)]
     [!code-vb[htAtomRss#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#4)]  
  
6.  Použijte parametr formát vrátit požadovaný formát.  
  
     [!code-csharp[htAtomRss#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#5)]
     [!code-vb[htAtomRss#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a>K hostování služby  
  
1.  Vytvoření <xref:System.ServiceModel.Web.WebServiceHost> objektu. <xref:System.ServiceModel.Web.WebServiceHost> Třída automaticky přidá koncový bod na základní adresa služby, pokud v konfiguraci nebo kód byl zadán jeden. V této ukázce nejsou zadány žádné koncové body, je vystaven výchozí koncový bod.  
  
     [!code-csharp[htAtomRss#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#6)]
     [!code-vb[htAtomRss#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#6)]  
  
2.  Otevření hostitele služby, načtěte informačního kanálu ze služby, zobrazit informační kanál a počkejte uživateli stiskněte klávesu ENTER.  
  
     [!code-csharp[htAtomRss#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#8)]
     [!code-vb[htAtomRss#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a>K volání GetBlog s HTTP GET  
  
1.  Otevřete Internet Explorer, zadejte následující adresu URL a stiskněte klávesu ENTER. http://localhost:8000/BlogService/GetBlog  
  
     Adresa URL obsahuje základní adresa služby (http://localhost:8000/BlogService), relativní adresa koncového bodu a volat operace služby.  
  
### <a name="to-call-getblog-from-code"></a>GetBlog() volat z kódu  
  
1.  Vytvoření <xref:System.Xml.XmlReader> s základní adresu a při volání metody.  
  
     [!code-csharp[htAtomRss#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#9)]
     [!code-vb[htAtomRss#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#9)]  
  
2.  Zavolejte statickou <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> předávání v případě metody <xref:System.Xml.XmlReader> jste právě vytvořili.  
  
     [!code-csharp[htAtomRss#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#10)]
     [!code-vb[htAtomRss#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#10)]  
  
     To vyvolá operaci služby a naplní novou <xref:System.ServiceModel.Syndication.SyndicationFeed> k formátování vrácená z operace služby.  
  
3.  Přístup k objekt informačního kanálu.  
  
     [!code-csharp[htAtomRss#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#11)]
     [!code-vb[htAtomRss#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#11)]  
  
## <a name="example"></a>Příklad  
 Zde je úplný výpis pro tento příklad kódu.  
  
 [!code-csharp[htAtomRss#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#12)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Při kompilování předchozí kód, odkazuje System.ServiceModel.dll a System.ServiceModel.Web.dll.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>
