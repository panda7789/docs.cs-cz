---
title: <privacyNoticeAt>
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: 2ff70d3a8636970434582e417e4549ab6b433fc1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738761"
---
# \<privacyNoticeAt>
<span data-ttu-id="d3521-101">Představuje prvek konfigurace, který určuje oznámení o ochraně osobních údajů používané ve `wsFederationHttp` vazbě.</span><span class="sxs-lookup"><span data-stu-id="d3521-101">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<privacyNotice>**  
  
## <a name="syntax"></a><span data-ttu-id="d3521-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3521-102">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"
               version="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="d3521-103">Typ</span><span class="sxs-lookup"><span data-stu-id="d3521-103">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3521-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d3521-104">Attributes and Elements</span></span>  
 <span data-ttu-id="d3521-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d3521-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3521-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="d3521-106">Attributes</span></span>  
  
|<span data-ttu-id="d3521-107">Atribut</span><span class="sxs-lookup"><span data-stu-id="d3521-107">Attribute</span></span>|<span data-ttu-id="d3521-108">Popis</span><span class="sxs-lookup"><span data-stu-id="d3521-108">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="d3521-109">Řetězec určující identifikátor URI, na kterém je umístěno oznámení o ochraně osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="d3521-109">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="d3521-110">Celé číslo, které určuje verzi tohoto oznámení o ochraně osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="d3521-110">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d3521-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d3521-111">Child Elements</span></span>  
 <span data-ttu-id="d3521-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="d3521-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d3521-113">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d3521-113">Parent Elements</span></span>  
  
|<span data-ttu-id="d3521-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="d3521-114">Element</span></span>|<span data-ttu-id="d3521-115">Description</span><span class="sxs-lookup"><span data-stu-id="d3521-115">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="d3521-116">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="d3521-116">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d3521-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="d3521-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>
- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="d3521-118">Vazby</span><span class="sxs-lookup"><span data-stu-id="d3521-118">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d3521-119">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="d3521-119">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="d3521-120">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="d3521-120">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
