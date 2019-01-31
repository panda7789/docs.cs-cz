---
title: <persistableType>
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: 3ea99d360ceb1e3fe6e97cbf9c8827dd7c853f63
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55256521"
---
# <a name="persistabletype"></a><span data-ttu-id="6907c-101">\<persistableType></span><span class="sxs-lookup"><span data-stu-id="6907c-101">\<persistableType></span></span>
<span data-ttu-id="6907c-102">Určuje trvalé typy.</span><span class="sxs-lookup"><span data-stu-id="6907c-102">Specifies all the persistable types.</span></span>  
  
 <span data-ttu-id="6907c-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6907c-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="6907c-104">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="6907c-104">\<comContracts></span></span>  
<span data-ttu-id="6907c-105">\<comContract></span><span class="sxs-lookup"><span data-stu-id="6907c-105">\<comContract></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6907c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6907c-106">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="6907c-107">Typ</span><span class="sxs-lookup"><span data-stu-id="6907c-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6907c-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6907c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6907c-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6907c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6907c-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="6907c-110">Attributes</span></span>  
  
|<span data-ttu-id="6907c-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="6907c-111">Attribute</span></span>|<span data-ttu-id="6907c-112">Popis</span><span class="sxs-lookup"><span data-stu-id="6907c-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6907c-113">id</span><span class="sxs-lookup"><span data-stu-id="6907c-113">id</span></span>|<span data-ttu-id="6907c-114">Požadovaný atribut, který obsahuje řetězec určující jedinečný identifikátor typu trvalé.</span><span class="sxs-lookup"><span data-stu-id="6907c-114">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="6907c-115">name</span><span class="sxs-lookup"><span data-stu-id="6907c-115">name</span></span>|<span data-ttu-id="6907c-116">Volitelný atribut, který obsahuje řetězec určující název typu trvalé.</span><span class="sxs-lookup"><span data-stu-id="6907c-116">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6907c-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6907c-117">Child Elements</span></span>  
 <span data-ttu-id="6907c-118">Žádná</span><span class="sxs-lookup"><span data-stu-id="6907c-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6907c-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6907c-119">Parent Elements</span></span>  
  
|<span data-ttu-id="6907c-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="6907c-120">Element</span></span>|<span data-ttu-id="6907c-121">Popis</span><span class="sxs-lookup"><span data-stu-id="6907c-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6907c-122">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="6907c-122">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)|<span data-ttu-id="6907c-123">Kolekce `persistableType` elementy.</span><span class="sxs-lookup"><span data-stu-id="6907c-123">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6907c-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6907c-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>
- [<span data-ttu-id="6907c-125">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="6907c-125">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)
- [<span data-ttu-id="6907c-126">Integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="6907c-126">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="6907c-127">Postupy: Konfigurace nastavení služby modelu COM +</span><span class="sxs-lookup"><span data-stu-id="6907c-127">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
