---
title: <persistableType>
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: 328caaefe0cc24da45b460cab0a672dc8a6ccce1
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855066"
---
# <a name="persistabletype"></a><span data-ttu-id="76289-101">\<Prvků persistableType ></span><span class="sxs-lookup"><span data-stu-id="76289-101">\<persistableType></span></span>
<span data-ttu-id="76289-102">Určuje všechny trvalé typy.</span><span class="sxs-lookup"><span data-stu-id="76289-102">Specifies all the persistable types.</span></span>  
  
<span data-ttu-id="76289-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="76289-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="76289-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="76289-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="76289-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Konfigurační oddíl comContracts >** ](comcontracts.md)</span><span class="sxs-lookup"><span data-stu-id="76289-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)</span></span>\
<span data-ttu-id="76289-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comContract >** ](comcontract.md)</span><span class="sxs-lookup"><span data-stu-id="76289-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)</span></span>\
<span data-ttu-id="76289-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<persistableTypes >** ](persistabletypes.md)</span><span class="sxs-lookup"><span data-stu-id="76289-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<persistableTypes>**](persistabletypes.md)</span></span>\
<span data-ttu-id="76289-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Prvků persistableType >**</span><span class="sxs-lookup"><span data-stu-id="76289-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<persistableType>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76289-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="76289-109">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract>
    <persistableTypes>
      <persistableType id="String"
                       name="String">
      </persistableType>
    </persistableTypes>
  </comContract>
</comContracts>
```  
  
## <a name="type"></a><span data-ttu-id="76289-110">type</span><span class="sxs-lookup"><span data-stu-id="76289-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="76289-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="76289-111">Attributes and Elements</span></span>  
 <span data-ttu-id="76289-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="76289-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="76289-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="76289-113">Attributes</span></span>  
  
|<span data-ttu-id="76289-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="76289-114">Attribute</span></span>|<span data-ttu-id="76289-115">Popis</span><span class="sxs-lookup"><span data-stu-id="76289-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="76289-116">id</span><span class="sxs-lookup"><span data-stu-id="76289-116">id</span></span>|<span data-ttu-id="76289-117">Požadovaný atribut, který obsahuje řetězec, který určuje jedinečný identifikátor pro trvalý typ.</span><span class="sxs-lookup"><span data-stu-id="76289-117">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="76289-118">name</span><span class="sxs-lookup"><span data-stu-id="76289-118">name</span></span>|<span data-ttu-id="76289-119">Volitelný atribut, který obsahuje řetězec, který určuje název trvalého typu.</span><span class="sxs-lookup"><span data-stu-id="76289-119">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="76289-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="76289-120">Child Elements</span></span>  
 <span data-ttu-id="76289-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="76289-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="76289-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="76289-122">Parent Elements</span></span>  
  
|<span data-ttu-id="76289-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="76289-123">Element</span></span>|<span data-ttu-id="76289-124">Popis</span><span class="sxs-lookup"><span data-stu-id="76289-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="76289-125">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="76289-125">\<persistableTypes></span></span>](persistabletypes.md)|<span data-ttu-id="76289-126">Kolekce `persistableType` prvků.</span><span class="sxs-lookup"><span data-stu-id="76289-126">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="76289-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="76289-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>
- [<span data-ttu-id="76289-128">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="76289-128">\<comContracts></span></span>](comcontracts.md)
- [<span data-ttu-id="76289-129">Integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="76289-129">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="76289-130">Postupy: Konfigurace nastavení služby modelu COM+</span><span class="sxs-lookup"><span data-stu-id="76289-130">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
