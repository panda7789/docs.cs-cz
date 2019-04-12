---
title: 'Postupy: Přizpůsobení informačních kanálů prostřednictvím zprostředkovatele reflexe (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: 00c23dcf-9bb8-459a-a012-6c4d9bcad7e9
ms.openlocfilehash: f09c9827498dfd6b85a8476e824d06bfb481d1f8
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/12/2019
ms.locfileid: "59517197"
---
# <a name="how-to-customize-feeds-with-the-reflection-provider-wcf-data-services"></a>Postupy: Přizpůsobení informačních kanálů prostřednictvím zprostředkovatele reflexe (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Umožňuje přizpůsobit Atom serializaci v odpovědi služby data tak, aby vlastnosti entity mohou být namapovány na nepoužívané prvky, které jsou definovány v AtomPub protokolu. Toto téma ukazuje, jak definovat atributů mapování pro typy entity v datovém modelu, který je definován pomocí zprostředkovatel reflexe. Další informace najdete v tématu [přizpůsobení informačního kanálu](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md).  
  
 Datový model v tomto příkladu je definována v tématu [jak: Vytvoření datové služby pomocí zprostředkovatel reflexe](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu, obě vlastnosti `Order` typu jsou namapovány na stávající elementy Atom. `Product` Vlastnost `Item` typ je mapována na atribut vlastní informační kanály v samostatném oboru názvů.  
  
 [!code-csharp[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_custom_feeds/cs/orderitems.svc.cs#customiqueryablefeeds)]
 [!code-vb[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_custom_feeds/vb/orderitems.svc.vb#customiqueryablefeeds)]  
  
## <a name="example"></a>Příklad  
 V předchozím příkladu vrátí následující výsledek pro identifikátor URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items`.  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResultInline](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/iqueryablefeedresultinline.xml#iqueryablefeedresultinline)]  
  
## <a name="see-also"></a>Viz také:

- [Zprostředkovatel reflexe](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)
