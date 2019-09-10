---
title: <namespaceTable>
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: aefe7beec7335d80341e670961800907c2bd0200
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855092"
---
# <a name="namespacetable"></a><span data-ttu-id="c8d31-101">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="c8d31-101">\<namespaceTable></span></span>

<span data-ttu-id="c8d31-102">Představuje konfigurační oddíl pro definování sady prvků, které obsahují obor názvů k mapování předpon, které lze následně použít ve filtrech XPath pro směrování.</span><span class="sxs-lookup"><span data-stu-id="c8d31-102">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

<span data-ttu-id="c8d31-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c8d31-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c8d31-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c8d31-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c8d31-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> směrování**](routing.md)</span><span class="sxs-lookup"><span data-stu-id="c8d31-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="c8d31-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> oboru názvů**</span><span class="sxs-lookup"><span data-stu-id="c8d31-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8d31-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c8d31-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c8d31-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c8d31-108">Attributes and elements</span></span>

<span data-ttu-id="c8d31-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c8d31-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c8d31-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="c8d31-110">Attributes</span></span>

<span data-ttu-id="c8d31-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="c8d31-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="c8d31-112">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="c8d31-112">Child elements</span></span>

|     | <span data-ttu-id="c8d31-113">Popis</span><span class="sxs-lookup"><span data-stu-id="c8d31-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="c8d31-114"> **\<Filtrovat >** </span><span class="sxs-lookup"><span data-stu-id="c8d31-114">**\<filter>**</span></span>](filter.md) | <span data-ttu-id="c8d31-115">Definuje mapování předpony oboru názvů používané pro výrazy XPath.</span><span class="sxs-lookup"><span data-stu-id="c8d31-115">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="c8d31-116">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="c8d31-116">Parent elements</span></span>

|     | <span data-ttu-id="c8d31-117">Popis</span><span class="sxs-lookup"><span data-stu-id="c8d31-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="c8d31-118"> **\<> směrování**</span><span class="sxs-lookup"><span data-stu-id="c8d31-118">**\<routing>**</span></span>](routing.md) | <span data-ttu-id="c8d31-119">Představuje konfigurační oddíl pro definování sady směrovacích filtrů, které určují typ Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> , který se má použít při vyhodnocování příchozích zpráv, jakož i směrovací tabulky, které definují cílové koncové body. Odeslat zprávy, když odpovídá filtr.</span><span class="sxs-lookup"><span data-stu-id="c8d31-119">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="c8d31-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c8d31-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
