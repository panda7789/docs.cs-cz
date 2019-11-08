---
title: <privacyNoticeAt>
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: 2ff70d3a8636970434582e417e4549ab6b433fc1
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738761"
---
# <a name="privacynoticeat"></a><span data-ttu-id="37c86-101">\<privacyNoticeAt ></span><span class="sxs-lookup"><span data-stu-id="37c86-101">\<privacyNoticeAt></span></span>
<span data-ttu-id="37c86-102">Představuje prvek konfigurace, který určuje oznámení o ochraně osobních údajů používané při `wsFederationHttp` vazbách.</span><span class="sxs-lookup"><span data-stu-id="37c86-102">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
<span data-ttu-id="37c86-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="37c86-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="37c86-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="37c86-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="37c86-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="37c86-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="37c86-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="37c86-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="37c86-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** </span><span class="sxs-lookup"><span data-stu-id="37c86-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="37c86-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<privacyNotice >**</span><span class="sxs-lookup"><span data-stu-id="37c86-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<privacyNotice>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37c86-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37c86-109">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"
               version="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="37c86-110">Typ</span><span class="sxs-lookup"><span data-stu-id="37c86-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="37c86-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="37c86-111">Attributes and Elements</span></span>  
 <span data-ttu-id="37c86-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="37c86-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="37c86-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="37c86-113">Attributes</span></span>  
  
|<span data-ttu-id="37c86-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="37c86-114">Attribute</span></span>|<span data-ttu-id="37c86-115">Popis</span><span class="sxs-lookup"><span data-stu-id="37c86-115">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="37c86-116">Řetězec určující identifikátor URI, na kterém je umístěno oznámení o ochraně osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="37c86-116">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="37c86-117">Celé číslo, které určuje verzi tohoto oznámení o ochraně osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="37c86-117">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="37c86-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="37c86-118">Child Elements</span></span>  
 <span data-ttu-id="37c86-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="37c86-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="37c86-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="37c86-120">Parent Elements</span></span>  
  
|<span data-ttu-id="37c86-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="37c86-121">Element</span></span>|<span data-ttu-id="37c86-122">Popis</span><span class="sxs-lookup"><span data-stu-id="37c86-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37c86-123">vazba \<</span><span class="sxs-lookup"><span data-stu-id="37c86-123">\<binding></span></span>](bindings.md)|<span data-ttu-id="37c86-124">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="37c86-124">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="37c86-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="37c86-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>
- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="37c86-126">Vazby</span><span class="sxs-lookup"><span data-stu-id="37c86-126">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="37c86-127">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="37c86-127">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="37c86-128">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="37c86-128">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="37c86-129">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="37c86-129">\<customBinding></span></span>](custombinding.md)
