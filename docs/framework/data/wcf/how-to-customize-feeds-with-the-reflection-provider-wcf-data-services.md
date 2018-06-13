---
title: 'Postupy: přizpůsobení informačních kanálů s poskytovatelem reflexe (služby WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: 00c23dcf-9bb8-459a-a012-6c4d9bcad7e9
ms.openlocfilehash: 984a4aac43689be0ec80e7f6c289e8d5229e9e1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358005"
---
# <a name="how-to-customize-feeds-with-the-reflection-provider-wcf-data-services"></a>Postupy: přizpůsobení informačních kanálů s poskytovatelem reflexe (služby WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Umožňuje přizpůsobit Atom serializaci v odpovědi data služby tak, aby vlastnosti entity, může být namapovaný na nepoužívané elementy, které jsou definovány v AtomPub protokolu. Toto téma ukazuje, jak definovat mapování atributů pro typy entit v datovém modelu, který je definován pomocí reflexe zprostředkovatele. Další informace najdete v tématu [kanálu přizpůsobení](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md).  
  
 Datový model v tomto příkladu je definován v sekci [postup: vytvoření služby Data pomocí poskytovatele reflexe](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu, obě vlastnosti `Order` typu jsou namapované na stávající elementy Atom. `Product` Vlastnost `Item` typ je namapovaný na vlastní atribut informačního kanálu v samostatných oboru názvů.  
  
 [!code-csharp[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria custom feeds/cs/orderitems.svc.cs#customiqueryablefeeds)]
 [!code-vb[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria custom feeds/vb/orderitems.svc.vb#customiqueryablefeeds)]  
  
## <a name="example"></a>Příklad  
 Předchozí příklad vrátí následující výsledek pro identifikátor URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items`.  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResultInline](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/iqueryablefeedresultinline.xml#iqueryablefeedresultinline)]  
  
## <a name="see-also"></a>Viz také  
 [Zprostředkovatel reflexe](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)
