---
title: <pnrpPeerResolver>
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: d3e88d7f2dd991091d3d7abdc715e125ddc9ac56
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738776"
---
# \<pnrpPeerResolver>
<span data-ttu-id="29a1f-101">Určuje, že jako překladač se použije překladač PNRP (Peer Name Resolution Protocol).</span><span class="sxs-lookup"><span data-stu-id="29a1f-101">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="29a1f-102">Tento prvek je nepovinný, protože PNRP je výchozí překladač.</span><span class="sxs-lookup"><span data-stu-id="29a1f-102">This element is optional because PNRP is the default resolver.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<pnrpResolver>**  
  
## <a name="syntax"></a><span data-ttu-id="29a1f-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29a1f-103">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29a1f-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="29a1f-104">Attributes and Elements</span></span>  
 <span data-ttu-id="29a1f-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="29a1f-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29a1f-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="29a1f-106">Attributes</span></span>  
  
|<span data-ttu-id="29a1f-107">Atribut</span><span class="sxs-lookup"><span data-stu-id="29a1f-107">Attribute</span></span>|<span data-ttu-id="29a1f-108">Popis</span><span class="sxs-lookup"><span data-stu-id="29a1f-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="29a1f-109">Typ překladače</span><span class="sxs-lookup"><span data-stu-id="29a1f-109">resolverType</span></span>|<span data-ttu-id="29a1f-110">Řetězec, který určuje překladač, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="29a1f-110">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="29a1f-111">Tento atribut je nepovinný.</span><span class="sxs-lookup"><span data-stu-id="29a1f-111">This attribute is optional.</span></span> <span data-ttu-id="29a1f-112">Pokud není nastavená, nebo pokud je nastavená na prázdný řetězec, použije se PNRP.</span><span class="sxs-lookup"><span data-stu-id="29a1f-112">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="29a1f-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="29a1f-113">Child Elements</span></span>  
 <span data-ttu-id="29a1f-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="29a1f-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="29a1f-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="29a1f-115">Parent Elements</span></span>  
  
|<span data-ttu-id="29a1f-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="29a1f-116">Element</span></span>|<span data-ttu-id="29a1f-117">Description</span><span class="sxs-lookup"><span data-stu-id="29a1f-117">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="29a1f-118">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="29a1f-118">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="29a1f-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="29a1f-119">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a><span data-ttu-id="29a1f-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="29a1f-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="29a1f-121">Vazby</span><span class="sxs-lookup"><span data-stu-id="29a1f-121">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="29a1f-122">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="29a1f-122">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="29a1f-123">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="29a1f-123">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="29a1f-124">Překladače partnerských uzlů</span><span class="sxs-lookup"><span data-stu-id="29a1f-124">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
