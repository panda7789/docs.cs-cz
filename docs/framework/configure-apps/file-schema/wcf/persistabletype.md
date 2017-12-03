---
title: '&lt;persistableType&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 56443902885e191d93897096e55742f7665ba00a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltpersistabletypegt"></a><span data-ttu-id="4a597-102">&lt;persistableType&gt;</span><span class="sxs-lookup"><span data-stu-id="4a597-102">&lt;persistableType&gt;</span></span>
<span data-ttu-id="4a597-103">Určuje trvalá typy.</span><span class="sxs-lookup"><span data-stu-id="4a597-103">Specifies all the persistable types.</span></span>  
  
 <span data-ttu-id="4a597-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="4a597-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4a597-105">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="4a597-105">\<comContracts></span></span>  
<span data-ttu-id="4a597-106">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="4a597-106">\<comContract></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a597-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a597-107">Syntax</span></span>  
  
```xml  
<comContracts>  
  <comContract>  
      <persistableTypes>  
         <persistableType id="string"  
            name="string">  
         </persistableType>  
      </persistableTypes>  
  </comContract>  
</comContracts>  
```  
  
## <a name="type"></a><span data-ttu-id="4a597-108">Typ</span><span class="sxs-lookup"><span data-stu-id="4a597-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4a597-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4a597-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4a597-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4a597-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4a597-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="4a597-111">Attributes</span></span>  
  
|<span data-ttu-id="4a597-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="4a597-112">Attribute</span></span>|<span data-ttu-id="4a597-113">Popis</span><span class="sxs-lookup"><span data-stu-id="4a597-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4a597-114">id</span><span class="sxs-lookup"><span data-stu-id="4a597-114">id</span></span>|<span data-ttu-id="4a597-115">Požadovaný atribut, který obsahuje řetězec, který určuje jedinečný identifikátor typu trvalá.</span><span class="sxs-lookup"><span data-stu-id="4a597-115">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="4a597-116">name</span><span class="sxs-lookup"><span data-stu-id="4a597-116">name</span></span>|<span data-ttu-id="4a597-117">Volitelný atribut, který obsahuje řetězec, který určuje název typu trvalá.</span><span class="sxs-lookup"><span data-stu-id="4a597-117">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4a597-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4a597-118">Child Elements</span></span>  
 <span data-ttu-id="4a597-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="4a597-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4a597-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4a597-120">Parent Elements</span></span>  
  
|<span data-ttu-id="4a597-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="4a597-121">Element</span></span>|<span data-ttu-id="4a597-122">Popis</span><span class="sxs-lookup"><span data-stu-id="4a597-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4a597-123">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="4a597-123">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)|<span data-ttu-id="4a597-124">Kolekce `persistableType` elementy.</span><span class="sxs-lookup"><span data-stu-id="4a597-124">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4a597-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="4a597-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>  
 [<span data-ttu-id="4a597-126">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="4a597-126">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [<span data-ttu-id="4a597-127">Integrace s aplikacemi modelu COM +</span><span class="sxs-lookup"><span data-stu-id="4a597-127">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="4a597-128">Postupy: Konfigurace nastavení služby COM +</span><span class="sxs-lookup"><span data-stu-id="4a597-128">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
