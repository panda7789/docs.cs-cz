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
# <a name="how-to-customize-feeds-with-the-reflection-provider-wcf-data-services"></a><span data-ttu-id="ddeff-102">Postupy: přizpůsobení informačních kanálů pomocí poskytovatele reflexe (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="ddeff-102">How to: Customize Feeds with the Reflection Provider (WCF Data Services)</span></span>
<span data-ttu-id="ddeff-103">WCF Data Services umožňuje přizpůsobit serializaci Atom v odpovědi na datovou službu, takže vlastnosti entity mohou být namapovány na nepoužívané prvky, které jsou definovány v protokolu AtomPub.</span><span class="sxs-lookup"><span data-stu-id="ddeff-103">WCF Data Services enables you to customize the Atom serialization in a data service response so that properties of an entity may be mapped to unused elements that are defined in the AtomPub protocol.</span></span> <span data-ttu-id="ddeff-104">Toto téma ukazuje, jak definovat atributy mapování pro typy entit v datovém modelu, který je definován pomocí poskytovatele reflexe.</span><span class="sxs-lookup"><span data-stu-id="ddeff-104">This topic shows how to define mapping attributes for the entity types in a data model that is defined by using the reflection provider.</span></span> <span data-ttu-id="ddeff-105">Další informace najdete v tématu [přizpůsobení informačního kanálu](feed-customization-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="ddeff-105">For more information, see [Feed Customization](feed-customization-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="ddeff-106">Datový model pro tento příklad je definován v tématu [Postupy: vytvoření datové služby pomocí zprostředkovatele reflexe](create-a-data-service-using-rp-wcf-data-services.md)</span><span class="sxs-lookup"><span data-stu-id="ddeff-106">The data model for this example is defined in the topic [How to: Create a Data Service Using the Reflection Provider](create-a-data-service-using-rp-wcf-data-services.md)</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddeff-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="ddeff-107">Example</span></span>  
 <span data-ttu-id="ddeff-108">V následujícím příkladu jsou obě vlastnosti `Order`ho typu mapovány na existující prvky Atom.</span><span class="sxs-lookup"><span data-stu-id="ddeff-108">In the following example, both properties of the `Order` type are mapped to existing Atom elements.</span></span> <span data-ttu-id="ddeff-109">Vlastnost `Product` typu `Item` je namapována na vlastní atribut informačního kanálu v samostatném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ddeff-109">The `Product` property of the `Item` type is mapped to a custom feed attribute in a separate namespace.</span></span>  
  
 [!code-csharp[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_custom_feeds/cs/orderitems.svc.cs#customiqueryablefeeds)]
 [!code-vb[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_custom_feeds/vb/orderitems.svc.vb#customiqueryablefeeds)]  
  
## <a name="example"></a><span data-ttu-id="ddeff-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="ddeff-110">Example</span></span>  
 <span data-ttu-id="ddeff-111">Předchozí příklad vrátí následující výsledek pro identifikátor URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items`.</span><span class="sxs-lookup"><span data-stu-id="ddeff-111">The previous example returns the following result for the URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items`.</span></span>  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResultInline](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/iqueryablefeedresultinline.xml#iqueryablefeedresultinline)]  
  
## <a name="see-also"></a><span data-ttu-id="ddeff-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ddeff-112">See also</span></span>

- [<span data-ttu-id="ddeff-113">Zprostředkovatel reflexe</span><span class="sxs-lookup"><span data-stu-id="ddeff-113">Reflection Provider</span></span>](reflection-provider-wcf-data-services.md)
