---
title: <persistableType>
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: 328caaefe0cc24da45b460cab0a672dc8a6ccce1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855066"
---
# \<persistableType>
<span data-ttu-id="a00ee-101">Určuje všechny trvalé typy.</span><span class="sxs-lookup"><span data-stu-id="a00ee-101">Specifies all the persistable types.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<persistableTypes>**](persistabletypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<persistableType>**  
  
## <a name="syntax"></a><span data-ttu-id="a00ee-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a00ee-102">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="a00ee-103">Typ</span><span class="sxs-lookup"><span data-stu-id="a00ee-103">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a00ee-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a00ee-104">Attributes and Elements</span></span>  
 <span data-ttu-id="a00ee-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a00ee-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a00ee-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="a00ee-106">Attributes</span></span>  
  
|<span data-ttu-id="a00ee-107">Atribut</span><span class="sxs-lookup"><span data-stu-id="a00ee-107">Attribute</span></span>|<span data-ttu-id="a00ee-108">Popis</span><span class="sxs-lookup"><span data-stu-id="a00ee-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a00ee-109">id</span><span class="sxs-lookup"><span data-stu-id="a00ee-109">id</span></span>|<span data-ttu-id="a00ee-110">Požadovaný atribut, který obsahuje řetězec, který určuje jedinečný identifikátor pro trvalý typ.</span><span class="sxs-lookup"><span data-stu-id="a00ee-110">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="a00ee-111">name</span><span class="sxs-lookup"><span data-stu-id="a00ee-111">name</span></span>|<span data-ttu-id="a00ee-112">Volitelný atribut, který obsahuje řetězec, který určuje název trvalého typu.</span><span class="sxs-lookup"><span data-stu-id="a00ee-112">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a00ee-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a00ee-113">Child Elements</span></span>  
 <span data-ttu-id="a00ee-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="a00ee-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a00ee-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a00ee-115">Parent Elements</span></span>  
  
|<span data-ttu-id="a00ee-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="a00ee-116">Element</span></span>|<span data-ttu-id="a00ee-117">Description</span><span class="sxs-lookup"><span data-stu-id="a00ee-117">Description</span></span>|  
|-------------|-----------------|  
|[\<persistableTypes>](persistabletypes.md)|<span data-ttu-id="a00ee-118">Kolekce `persistableType` prvků.</span><span class="sxs-lookup"><span data-stu-id="a00ee-118">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a00ee-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="a00ee-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>
- [\<comContracts>](comcontracts.md)
- [<span data-ttu-id="a00ee-120">Integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="a00ee-120">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="a00ee-121">Postupy: Konfigurace nastavení služby modelu COM+</span><span class="sxs-lookup"><span data-stu-id="a00ee-121">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
