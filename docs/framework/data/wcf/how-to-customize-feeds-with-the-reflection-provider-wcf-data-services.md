---
title: 'Postupy: Přizpůsobení informačních kanálů pomocí poskytovatele reflexe (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: 00c23dcf-9bb8-459a-a012-6c4d9bcad7e9
ms.openlocfilehash: 43f46729ba84356bcb6507779bef9e4fd35bc315
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790673"
---
# <a name="how-to-customize-feeds-with-the-reflection-provider-wcf-data-services"></a>Postupy: Přizpůsobení informačních kanálů pomocí poskytovatele reflexe (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]umožňuje přizpůsobit serializaci Atom v odpovědi na datovou službu, takže vlastnosti entity mohou být namapovány na nepoužívané prvky, které jsou definovány v protokolu AtomPub. Toto téma ukazuje, jak definovat atributy mapování pro typy entit v datovém modelu, který je definován pomocí poskytovatele reflexe. Další informace najdete v tématu [přizpůsobení informačního kanálu](feed-customization-wcf-data-services.md).  
  
 Datový model pro tento příklad je definován v tématu [postupy: Vytvoření datové služby pomocí zprostředkovatele reflexe](create-a-data-service-using-rp-wcf-data-services.md)  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu jsou obě vlastnosti `Order` typu namapovány na existující prvky Atom. `Product` Vlastnost`Item` typu je namapována na vlastní atribut informačního kanálu v samostatném oboru názvů.  
  
 [!code-csharp[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_custom_feeds/cs/orderitems.svc.cs#customiqueryablefeeds)]
 [!code-vb[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_custom_feeds/vb/orderitems.svc.vb#customiqueryablefeeds)]  
  
## <a name="example"></a>Příklad  
 Předchozí příklad vrátí následující výsledek pro identifikátor URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items`.  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResultInline](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/iqueryablefeedresultinline.xml#iqueryablefeedresultinline)]  
  
## <a name="see-also"></a>Viz také:

- [Zprostředkovatel reflexe](reflection-provider-wcf-data-services.md)
