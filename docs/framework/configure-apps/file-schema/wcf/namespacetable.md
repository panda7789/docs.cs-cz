---
title: <namespaceTable>
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: 0316e983446644671ead2f8f843dc91b493b29c9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933172"
---
# <a name="namespacetable"></a><span data-ttu-id="de39e-101">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="de39e-101">\<namespaceTable></span></span>

<span data-ttu-id="de39e-102">Představuje konfigurační oddíl pro definování sady prvků, které obsahují obor názvů k mapování předpon, které lze následně použít ve filtrech XPath pro směrování.</span><span class="sxs-lookup"><span data-stu-id="de39e-102">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

<span data-ttu-id="de39e-103">**\<system.serviceModel>**  </span><span class="sxs-lookup"><span data-stu-id="de39e-103">**\<system.serviceModel>** </span></span>  
<span data-ttu-id="de39e-104">&nbsp;&nbsp; **\<> směrování** </span><span class="sxs-lookup"><span data-stu-id="de39e-104">&nbsp;&nbsp;**\<routing>** </span></span>  
<span data-ttu-id="de39e-105">&nbsp;&nbsp;&nbsp;&nbsp; **\<namespaceTable>**</span><span class="sxs-lookup"><span data-stu-id="de39e-105">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="de39e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de39e-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <routing>
    <namespaceTable>
      <add namespace="String"
           prefix="String" />
    </namespaceTable>
  </routing>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de39e-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="de39e-107">Attributes and elements</span></span>

<span data-ttu-id="de39e-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="de39e-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="de39e-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="de39e-109">Attributes</span></span>

<span data-ttu-id="de39e-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="de39e-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="de39e-111">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="de39e-111">Child elements</span></span>

|     | <span data-ttu-id="de39e-112">Popis</span><span class="sxs-lookup"><span data-stu-id="de39e-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="de39e-113"> **\<Filtrovat >** </span><span class="sxs-lookup"><span data-stu-id="de39e-113">**\<filter>**</span></span>](filter.md) | <span data-ttu-id="de39e-114">Definuje mapování předpony oboru názvů používané pro výrazy XPath.</span><span class="sxs-lookup"><span data-stu-id="de39e-114">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="de39e-115">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="de39e-115">Parent elements</span></span>

|     | <span data-ttu-id="de39e-116">Popis</span><span class="sxs-lookup"><span data-stu-id="de39e-116">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="de39e-117"> **\<> směrování**</span><span class="sxs-lookup"><span data-stu-id="de39e-117">**\<routing>**</span></span>](routing.md) | <span data-ttu-id="de39e-118">Představuje konfigurační oddíl pro definování sady směrovacích filtrů, které určují typ Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> , který se má použít při vyhodnocování příchozích zpráv, jakož i směrovací tabulky, které definují cílové koncové body. Odeslat zprávy, když odpovídá filtr.</span><span class="sxs-lookup"><span data-stu-id="de39e-118">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="de39e-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="de39e-119">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
