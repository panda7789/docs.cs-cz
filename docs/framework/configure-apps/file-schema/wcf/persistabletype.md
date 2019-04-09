---
title: <persistableType>
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: 939a29e90ee21e94ccb78842d6f7224e9a6288d0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083735"
---
# <a name="persistabletype"></a><span data-ttu-id="e4f67-101">\<persistableType></span><span class="sxs-lookup"><span data-stu-id="e4f67-101">\<persistableType></span></span>
<span data-ttu-id="e4f67-102">Určuje trvalé typy.</span><span class="sxs-lookup"><span data-stu-id="e4f67-102">Specifies all the persistable types.</span></span>  
  
 <span data-ttu-id="e4f67-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e4f67-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="e4f67-104">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="e4f67-104">\<comContracts></span></span>  
<span data-ttu-id="e4f67-105">\<comContract></span><span class="sxs-lookup"><span data-stu-id="e4f67-105">\<comContract></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4f67-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4f67-106">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="e4f67-107">Type</span><span class="sxs-lookup"><span data-stu-id="e4f67-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4f67-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e4f67-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e4f67-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e4f67-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4f67-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="e4f67-110">Attributes</span></span>  
  
|<span data-ttu-id="e4f67-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="e4f67-111">Attribute</span></span>|<span data-ttu-id="e4f67-112">Popis</span><span class="sxs-lookup"><span data-stu-id="e4f67-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e4f67-113">id</span><span class="sxs-lookup"><span data-stu-id="e4f67-113">id</span></span>|<span data-ttu-id="e4f67-114">Požadovaný atribut, který obsahuje řetězec určující jedinečný identifikátor typu trvalé.</span><span class="sxs-lookup"><span data-stu-id="e4f67-114">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="e4f67-115">name</span><span class="sxs-lookup"><span data-stu-id="e4f67-115">name</span></span>|<span data-ttu-id="e4f67-116">Volitelný atribut, který obsahuje řetězec určující název typu trvalé.</span><span class="sxs-lookup"><span data-stu-id="e4f67-116">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e4f67-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e4f67-117">Child Elements</span></span>  
 <span data-ttu-id="e4f67-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="e4f67-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e4f67-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e4f67-119">Parent Elements</span></span>  
  
|<span data-ttu-id="e4f67-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="e4f67-120">Element</span></span>|<span data-ttu-id="e4f67-121">Popis</span><span class="sxs-lookup"><span data-stu-id="e4f67-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e4f67-122">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="e4f67-122">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)|<span data-ttu-id="e4f67-123">Kolekce `persistableType` elementy.</span><span class="sxs-lookup"><span data-stu-id="e4f67-123">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e4f67-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e4f67-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>
- [<span data-ttu-id="e4f67-125">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="e4f67-125">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)
- [<span data-ttu-id="e4f67-126">Integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="e4f67-126">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="e4f67-127">Postupy: Konfigurace nastavení služby modelu COM+</span><span class="sxs-lookup"><span data-stu-id="e4f67-127">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
