---
title: <persistableType>
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: fcfd338e289b5151688724f0e84b6878707d32be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933824"
---
# <a name="persistabletype"></a><span data-ttu-id="18654-101">\<Prvků persistableType ></span><span class="sxs-lookup"><span data-stu-id="18654-101">\<persistableType></span></span>
<span data-ttu-id="18654-102">Určuje všechny trvalé typy.</span><span class="sxs-lookup"><span data-stu-id="18654-102">Specifies all the persistable types.</span></span>  
  
 <span data-ttu-id="18654-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="18654-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="18654-104">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="18654-104">\<comContracts></span></span>  
<span data-ttu-id="18654-105">\<comContract></span><span class="sxs-lookup"><span data-stu-id="18654-105">\<comContract></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18654-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18654-106">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="18654-107">type</span><span class="sxs-lookup"><span data-stu-id="18654-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="18654-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="18654-108">Attributes and Elements</span></span>  
 <span data-ttu-id="18654-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="18654-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="18654-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="18654-110">Attributes</span></span>  
  
|<span data-ttu-id="18654-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="18654-111">Attribute</span></span>|<span data-ttu-id="18654-112">Popis</span><span class="sxs-lookup"><span data-stu-id="18654-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="18654-113">id</span><span class="sxs-lookup"><span data-stu-id="18654-113">id</span></span>|<span data-ttu-id="18654-114">Požadovaný atribut, který obsahuje řetězec, který určuje jedinečný identifikátor pro trvalý typ.</span><span class="sxs-lookup"><span data-stu-id="18654-114">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="18654-115">name</span><span class="sxs-lookup"><span data-stu-id="18654-115">name</span></span>|<span data-ttu-id="18654-116">Volitelný atribut, který obsahuje řetězec, který určuje název trvalého typu.</span><span class="sxs-lookup"><span data-stu-id="18654-116">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="18654-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="18654-117">Child Elements</span></span>  
 <span data-ttu-id="18654-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="18654-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="18654-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="18654-119">Parent Elements</span></span>  
  
|<span data-ttu-id="18654-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="18654-120">Element</span></span>|<span data-ttu-id="18654-121">Popis</span><span class="sxs-lookup"><span data-stu-id="18654-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="18654-122">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="18654-122">\<persistableTypes></span></span>](persistabletypes.md)|<span data-ttu-id="18654-123">Kolekce `persistableType` prvků.</span><span class="sxs-lookup"><span data-stu-id="18654-123">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="18654-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="18654-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>
- [<span data-ttu-id="18654-125">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="18654-125">\<comContracts></span></span>](comcontracts.md)
- [<span data-ttu-id="18654-126">Integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="18654-126">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="18654-127">Postupy: Konfigurace nastavení služby modelu COM+</span><span class="sxs-lookup"><span data-stu-id="18654-127">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
