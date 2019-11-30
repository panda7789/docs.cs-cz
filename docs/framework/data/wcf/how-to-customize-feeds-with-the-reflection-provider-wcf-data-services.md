---
title: 'Postupy: přizpůsobení informačních kanálů pomocí poskytovatele reflexe (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: 00c23dcf-9bb8-459a-a012-6c4d9bcad7e9
ms.openlocfilehash: d3e2d587978a4c82784c8cfc8a7acc17cf601c3a
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569148"
---
# <a name="how-to-customize-feeds-with-the-reflection-provider-wcf-data-services"></a>Postupy: přizpůsobení informačních kanálů pomocí poskytovatele reflexe (WCF Data Services)
WCF Data Services umožňuje přizpůsobit serializaci Atom v odpovědi na datovou službu, takže vlastnosti entity mohou být namapovány na nepoužívané prvky, které jsou definovány v protokolu AtomPub. Toto téma ukazuje, jak definovat atributy mapování pro typy entit v datovém modelu, který je definován pomocí poskytovatele reflexe. Další informace najdete v tématu [přizpůsobení informačního kanálu](feed-customization-wcf-data-services.md).  
  
 Datový model pro tento příklad je definován v tématu [Postupy: vytvoření datové služby pomocí zprostředkovatele reflexe](create-a-data-service-using-rp-wcf-data-services.md)  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu jsou obě vlastnosti `Order`ho typu mapovány na existující prvky Atom. Vlastnost `Product` typu `Item` je namapována na vlastní atribut informačního kanálu v samostatném oboru názvů.  
  
 [!code-csharp[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_custom_feeds/cs/orderitems.svc.cs#customiqueryablefeeds)]
 [!code-vb[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_custom_feeds/vb/orderitems.svc.vb#customiqueryablefeeds)]  
  
## <a name="example"></a>Příklad  
 Předchozí příklad vrátí následující výsledek pro identifikátor URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items`.  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResultInline](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/iqueryablefeedresultinline.xml#iqueryablefeedresultinline)]  
  
## <a name="see-also"></a>Viz také:

- [Zprostředkovatel reflexe](reflection-provider-wcf-data-services.md)
