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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59517197"
---
# <a name="how-to-customize-feeds-with-the-reflection-provider-wcf-data-services"></a><span data-ttu-id="e8099-102">Postupy: Přizpůsobení informačních kanálů prostřednictvím zprostředkovatele reflexe (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="e8099-102">How to: Customize Feeds with the Reflection Provider (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] <span data-ttu-id="e8099-103">Umožňuje přizpůsobit Atom serializaci v odpovědi služby data tak, aby vlastnosti entity mohou být namapovány na nepoužívané prvky, které jsou definovány v AtomPub protokolu.</span><span class="sxs-lookup"><span data-stu-id="e8099-103">enables you to customize the Atom serialization in a data service response so that properties of an entity may be mapped to unused elements that are defined in the AtomPub protocol.</span></span> <span data-ttu-id="e8099-104">Toto téma ukazuje, jak definovat atributů mapování pro typy entity v datovém modelu, který je definován pomocí zprostředkovatel reflexe.</span><span class="sxs-lookup"><span data-stu-id="e8099-104">This topic shows how to define mapping attributes for the entity types in a data model that is defined by using the reflection provider.</span></span> <span data-ttu-id="e8099-105">Další informace najdete v tématu [přizpůsobení informačního kanálu](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="e8099-105">For more information, see [Feed Customization](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="e8099-106">Datový model v tomto příkladu je definována v tématu [jak: Vytvoření datové služby pomocí zprostředkovatel reflexe](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)</span><span class="sxs-lookup"><span data-stu-id="e8099-106">The data model for this example is defined in the topic [How to: Create a Data Service Using the Reflection Provider](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8099-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="e8099-107">Example</span></span>  
 <span data-ttu-id="e8099-108">V následujícím příkladu, obě vlastnosti `Order` typu jsou namapovány na stávající elementy Atom.</span><span class="sxs-lookup"><span data-stu-id="e8099-108">In the following example, both properties of the `Order` type are mapped to existing Atom elements.</span></span> <span data-ttu-id="e8099-109">`Product` Vlastnost `Item` typ je mapována na atribut vlastní informační kanály v samostatném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e8099-109">The `Product` property of the `Item` type is mapped to a custom feed attribute in a separate namespace.</span></span>  
  
 [!code-csharp[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_custom_feeds/cs/orderitems.svc.cs#customiqueryablefeeds)]
 [!code-vb[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_custom_feeds/vb/orderitems.svc.vb#customiqueryablefeeds)]  
  
## <a name="example"></a><span data-ttu-id="e8099-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="e8099-110">Example</span></span>  
 <span data-ttu-id="e8099-111">V předchozím příkladu vrátí následující výsledek pro identifikátor URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items`.</span><span class="sxs-lookup"><span data-stu-id="e8099-111">The previous example returns the following result for the URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items`.</span></span>  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResultInline](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/iqueryablefeedresultinline.xml#iqueryablefeedresultinline)]  
  
## <a name="see-also"></a><span data-ttu-id="e8099-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e8099-112">See also</span></span>

- [<span data-ttu-id="e8099-113">Zprostředkovatel reflexe</span><span class="sxs-lookup"><span data-stu-id="e8099-113">Reflection Provider</span></span>](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)
