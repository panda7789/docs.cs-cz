---
title: <useManagedPresentation>
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: bb2989ed52a88d805510d65e1dc1740df7bb55eb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73735937"
---
# \<useManagedPresentation>
<span data-ttu-id="00c8d-101">Prvek vazby, který slouží ke komunikaci se službou tokenu zabezpečení služby CardSpace, který podporuje profil služby CardSpace WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="00c8d-101">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="00c8d-102">Tento element nemá žádný atribut a je přítomný jako prázdný přepínač.</span><span class="sxs-lookup"><span data-stu-id="00c8d-102">This element has no attribute and is present as an empty switch.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useManagedPresentation>**  
  
## <a name="syntax"></a><span data-ttu-id="00c8d-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00c8d-103">Syntax</span></span>  
  
```xml  
<useManagedPresentation />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="00c8d-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="00c8d-104">Attributes and Elements</span></span>  
 <span data-ttu-id="00c8d-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="00c8d-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="00c8d-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="00c8d-106">Attributes</span></span>  
 <span data-ttu-id="00c8d-107">Žádné</span><span class="sxs-lookup"><span data-stu-id="00c8d-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="00c8d-108">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="00c8d-108">Child Elements</span></span>  
 <span data-ttu-id="00c8d-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="00c8d-109">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="00c8d-110">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="00c8d-110">Parent Elements</span></span>  
  
|<span data-ttu-id="00c8d-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="00c8d-111">Element</span></span>|<span data-ttu-id="00c8d-112">Description</span><span class="sxs-lookup"><span data-stu-id="00c8d-112">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="00c8d-113">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="00c8d-113">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00c8d-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="00c8d-114">Remarks</span></span>  
 <span data-ttu-id="00c8d-115">Tento prvek používá zprostředkovatel identity ke expresi v jeho zásadě fakt, že podporuje profil služby CardSpace WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="00c8d-115">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="00c8d-116">Zprostředkovatelé identity, kteří publikují takový kontrolní výraz zásad, by měli mít schopnost vystavit tokeny na základě tohoto profilu CardSpace.</span><span class="sxs-lookup"><span data-stu-id="00c8d-116">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00c8d-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="00c8d-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>
- <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="00c8d-118">Vazby</span><span class="sxs-lookup"><span data-stu-id="00c8d-118">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="00c8d-119">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="00c8d-119">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="00c8d-120">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="00c8d-120">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
