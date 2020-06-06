---
title: <add> z <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: d75142209ad8706d0cad5ce188d9d991a5e881bc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850593"
---
# <a name="add-of-baseaddresses"></a><span data-ttu-id="1de86-102">\<add> z \<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="1de86-102">\<add> of \<baseAddresses></span></span>
<span data-ttu-id="1de86-103">Představuje prvek konfigurace, který určuje základní adresy používané hostitelem služby.</span><span class="sxs-lookup"><span data-stu-id="1de86-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<baseAddresses>**](baseaddresses.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="1de86-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1de86-104">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a><span data-ttu-id="1de86-105">Typ</span><span class="sxs-lookup"><span data-stu-id="1de86-105">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1de86-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1de86-106">Attributes and Elements</span></span>  
 <span data-ttu-id="1de86-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1de86-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1de86-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="1de86-108">Attributes</span></span>  
  
|<span data-ttu-id="1de86-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="1de86-109">Attribute</span></span>|<span data-ttu-id="1de86-110">Popis</span><span class="sxs-lookup"><span data-stu-id="1de86-110">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="1de86-111">Řetězec, který určuje základní adresu, kterou používá hostitel služby.</span><span class="sxs-lookup"><span data-stu-id="1de86-111">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1de86-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1de86-112">Child Elements</span></span>  
 <span data-ttu-id="1de86-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="1de86-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1de86-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1de86-114">Parent Elements</span></span>  
  
|<span data-ttu-id="1de86-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="1de86-115">Element</span></span>|<span data-ttu-id="1de86-116">Description</span><span class="sxs-lookup"><span data-stu-id="1de86-116">Description</span></span>|  
|-------------|-----------------|  
|[\<baseAddresses>](baseaddresses.md)|<span data-ttu-id="1de86-117">Kolekce `baseAddress` prvků.</span><span class="sxs-lookup"><span data-stu-id="1de86-117">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1de86-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="1de86-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="1de86-119">Hosting</span><span class="sxs-lookup"><span data-stu-id="1de86-119">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
