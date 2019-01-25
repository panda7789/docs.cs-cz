---
title: '&lt;persistableType&gt;'
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: b9d61a736a2f8650c543433931d57e156d115018
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706849"
---
# <a name="ltpersistabletypegt"></a><span data-ttu-id="dd2da-102">&lt;persistableType&gt;</span><span class="sxs-lookup"><span data-stu-id="dd2da-102">&lt;persistableType&gt;</span></span>
<span data-ttu-id="dd2da-103">Určuje trvalé typy.</span><span class="sxs-lookup"><span data-stu-id="dd2da-103">Specifies all the persistable types.</span></span>  
  
 <span data-ttu-id="dd2da-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="dd2da-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="dd2da-105">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="dd2da-105">\<comContracts></span></span>  
<span data-ttu-id="dd2da-106">\<comContract></span><span class="sxs-lookup"><span data-stu-id="dd2da-106">\<comContract></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd2da-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd2da-107">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="dd2da-108">Typ</span><span class="sxs-lookup"><span data-stu-id="dd2da-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd2da-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="dd2da-109">Attributes and Elements</span></span>  
 <span data-ttu-id="dd2da-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="dd2da-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd2da-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="dd2da-111">Attributes</span></span>  
  
|<span data-ttu-id="dd2da-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="dd2da-112">Attribute</span></span>|<span data-ttu-id="dd2da-113">Popis</span><span class="sxs-lookup"><span data-stu-id="dd2da-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dd2da-114">id</span><span class="sxs-lookup"><span data-stu-id="dd2da-114">id</span></span>|<span data-ttu-id="dd2da-115">Požadovaný atribut, který obsahuje řetězec určující jedinečný identifikátor typu trvalé.</span><span class="sxs-lookup"><span data-stu-id="dd2da-115">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="dd2da-116">name</span><span class="sxs-lookup"><span data-stu-id="dd2da-116">name</span></span>|<span data-ttu-id="dd2da-117">Volitelný atribut, který obsahuje řetězec určující název typu trvalé.</span><span class="sxs-lookup"><span data-stu-id="dd2da-117">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dd2da-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="dd2da-118">Child Elements</span></span>  
 <span data-ttu-id="dd2da-119">Žádná</span><span class="sxs-lookup"><span data-stu-id="dd2da-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dd2da-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="dd2da-120">Parent Elements</span></span>  
  
|<span data-ttu-id="dd2da-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="dd2da-121">Element</span></span>|<span data-ttu-id="dd2da-122">Popis</span><span class="sxs-lookup"><span data-stu-id="dd2da-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dd2da-123">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="dd2da-123">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)|<span data-ttu-id="dd2da-124">Kolekce `persistableType` elementy.</span><span class="sxs-lookup"><span data-stu-id="dd2da-124">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dd2da-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dd2da-125">See also</span></span>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>
- [<span data-ttu-id="dd2da-126">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="dd2da-126">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)
- [<span data-ttu-id="dd2da-127">Integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="dd2da-127">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="dd2da-128">Postupy: Konfigurace nastavení služby modelu COM +</span><span class="sxs-lookup"><span data-stu-id="dd2da-128">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
