---
title: '&lt;persistableType&gt;'
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: 92c59b3804e22c62340acccc1e12e594203c8e8b
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145416"
---
# <a name="ltpersistabletypegt"></a><span data-ttu-id="e47bf-102">&lt;persistableType&gt;</span><span class="sxs-lookup"><span data-stu-id="e47bf-102">&lt;persistableType&gt;</span></span>
<span data-ttu-id="e47bf-103">Určuje trvalé typy.</span><span class="sxs-lookup"><span data-stu-id="e47bf-103">Specifies all the persistable types.</span></span>  
  
 <span data-ttu-id="e47bf-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e47bf-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e47bf-105">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="e47bf-105">\<comContracts></span></span>  
<span data-ttu-id="e47bf-106">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="e47bf-106">\<comContract></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e47bf-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e47bf-107">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="e47bf-108">Typ</span><span class="sxs-lookup"><span data-stu-id="e47bf-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e47bf-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e47bf-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e47bf-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e47bf-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e47bf-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="e47bf-111">Attributes</span></span>  
  
|<span data-ttu-id="e47bf-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="e47bf-112">Attribute</span></span>|<span data-ttu-id="e47bf-113">Popis</span><span class="sxs-lookup"><span data-stu-id="e47bf-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e47bf-114">id</span><span class="sxs-lookup"><span data-stu-id="e47bf-114">id</span></span>|<span data-ttu-id="e47bf-115">Požadovaný atribut, který obsahuje řetězec určující jedinečný identifikátor typu trvalé.</span><span class="sxs-lookup"><span data-stu-id="e47bf-115">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="e47bf-116">name</span><span class="sxs-lookup"><span data-stu-id="e47bf-116">name</span></span>|<span data-ttu-id="e47bf-117">Volitelný atribut, který obsahuje řetězec určující název typu trvalé.</span><span class="sxs-lookup"><span data-stu-id="e47bf-117">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e47bf-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e47bf-118">Child Elements</span></span>  
 <span data-ttu-id="e47bf-119">Žádná</span><span class="sxs-lookup"><span data-stu-id="e47bf-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e47bf-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e47bf-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e47bf-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="e47bf-121">Element</span></span>|<span data-ttu-id="e47bf-122">Popis</span><span class="sxs-lookup"><span data-stu-id="e47bf-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e47bf-123">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="e47bf-123">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)|<span data-ttu-id="e47bf-124">Kolekce `persistableType` elementy.</span><span class="sxs-lookup"><span data-stu-id="e47bf-124">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e47bf-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="e47bf-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>  
 [<span data-ttu-id="e47bf-126">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="e47bf-126">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [<span data-ttu-id="e47bf-127">Integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="e47bf-127">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="e47bf-128">Postupy: Konfigurace nastavení služby modelu COM +</span><span class="sxs-lookup"><span data-stu-id="e47bf-128">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
