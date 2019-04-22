---
title: <persistableType>
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: 939a29e90ee21e94ccb78842d6f7224e9a6288d0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59083735"
---
# <a name="persistabletype"></a><span data-ttu-id="67c61-101">\<persistableType></span><span class="sxs-lookup"><span data-stu-id="67c61-101">\<persistableType></span></span>
<span data-ttu-id="67c61-102">Určuje trvalé typy.</span><span class="sxs-lookup"><span data-stu-id="67c61-102">Specifies all the persistable types.</span></span>  
  
 <span data-ttu-id="67c61-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="67c61-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="67c61-104">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="67c61-104">\<comContracts></span></span>  
<span data-ttu-id="67c61-105">\<comContract></span><span class="sxs-lookup"><span data-stu-id="67c61-105">\<comContract></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67c61-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="67c61-106">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="67c61-107">Type</span><span class="sxs-lookup"><span data-stu-id="67c61-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="67c61-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="67c61-108">Attributes and Elements</span></span>  
 <span data-ttu-id="67c61-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="67c61-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="67c61-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="67c61-110">Attributes</span></span>  
  
|<span data-ttu-id="67c61-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="67c61-111">Attribute</span></span>|<span data-ttu-id="67c61-112">Popis</span><span class="sxs-lookup"><span data-stu-id="67c61-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="67c61-113">id</span><span class="sxs-lookup"><span data-stu-id="67c61-113">id</span></span>|<span data-ttu-id="67c61-114">Požadovaný atribut, který obsahuje řetězec určující jedinečný identifikátor typu trvalé.</span><span class="sxs-lookup"><span data-stu-id="67c61-114">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="67c61-115">name</span><span class="sxs-lookup"><span data-stu-id="67c61-115">name</span></span>|<span data-ttu-id="67c61-116">Volitelný atribut, který obsahuje řetězec určující název typu trvalé.</span><span class="sxs-lookup"><span data-stu-id="67c61-116">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="67c61-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="67c61-117">Child Elements</span></span>  
 <span data-ttu-id="67c61-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="67c61-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="67c61-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="67c61-119">Parent Elements</span></span>  
  
|<span data-ttu-id="67c61-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="67c61-120">Element</span></span>|<span data-ttu-id="67c61-121">Popis</span><span class="sxs-lookup"><span data-stu-id="67c61-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="67c61-122">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="67c61-122">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)|<span data-ttu-id="67c61-123">Kolekce `persistableType` elementy.</span><span class="sxs-lookup"><span data-stu-id="67c61-123">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="67c61-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="67c61-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>
- [<span data-ttu-id="67c61-125">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="67c61-125">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)
- [<span data-ttu-id="67c61-126">Integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="67c61-126">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="67c61-127">Postupy: Konfigurace nastavení služby modelu COM +</span><span class="sxs-lookup"><span data-stu-id="67c61-127">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
