---
title: "&lt;Třída knownType&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bedebb98e5fc48292c503eef30cee30c8d29c41c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltknowntypegt"></a><span data-ttu-id="b49dd-102">&lt;Třída knownType&gt;</span><span class="sxs-lookup"><span data-stu-id="b49dd-102">&lt;knownType&gt;</span></span>
<span data-ttu-id="b49dd-103">Určuje typ má být používána <xref:System.Runtime.Serialization.DataContractSerializer> během deserializace.</span><span class="sxs-lookup"><span data-stu-id="b49dd-103">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="b49dd-104">Element "známému typu" Určuje, který vrátí pole nebo vlastnost "deklarovaný typ".</span><span class="sxs-lookup"><span data-stu-id="b49dd-104">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="b49dd-105">Další informace najdete v tématu [známé typy kontraktů dat](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="b49dd-105">For more information, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="b49dd-106">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="b49dd-106">\<system.runtime.serialization></span></span>  
<span data-ttu-id="b49dd-107">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="b49dd-107">\<dataContractSerializer></span></span>  
<span data-ttu-id="b49dd-108">\<declaredTypes > elementu</span><span class="sxs-lookup"><span data-stu-id="b49dd-108">\<declaredTypes> Element</span></span>  
<span data-ttu-id="b49dd-109">\<Přidat > z \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="b49dd-109">\<add> of \<declaredTypes></span></span>  
<span data-ttu-id="b49dd-110">\<Třída knownType > elementu</span><span class="sxs-lookup"><span data-stu-id="b49dd-110">\<knownType> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b49dd-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b49dd-111">Syntax</span></span>  
  
```xml  
<knownType type="String">  
     <parameter index="Integer"  
                type="String" />  
</knownType>  
```  
  
## <a name="type"></a><span data-ttu-id="b49dd-112">Typ</span><span class="sxs-lookup"><span data-stu-id="b49dd-112">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b49dd-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b49dd-113">Attributes and Elements</span></span>  
 <span data-ttu-id="b49dd-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b49dd-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b49dd-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="b49dd-115">Attributes</span></span>  
  
|<span data-ttu-id="b49dd-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="b49dd-116">Attribute</span></span>|<span data-ttu-id="b49dd-117">Popis</span><span class="sxs-lookup"><span data-stu-id="b49dd-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b49dd-118">– typ</span><span class="sxs-lookup"><span data-stu-id="b49dd-118">type</span></span>|<span data-ttu-id="b49dd-119">Určuje typ (včetně oboru názvů), název sestavení, verze, jazykové verze a tokenu veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="b49dd-119">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b49dd-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b49dd-120">Child Elements</span></span>  
  
|<span data-ttu-id="b49dd-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="b49dd-121">Element</span></span>|<span data-ttu-id="b49dd-122">Popis</span><span class="sxs-lookup"><span data-stu-id="b49dd-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b49dd-123">\<parametr ></span><span class="sxs-lookup"><span data-stu-id="b49dd-123">\<parameter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/parameter.md)|<span data-ttu-id="b49dd-124">Určuje indexu parametru, je-li deklarovaný typ obecného typu.</span><span class="sxs-lookup"><span data-stu-id="b49dd-124">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b49dd-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b49dd-125">Parent Elements</span></span>  
  
|<span data-ttu-id="b49dd-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="b49dd-126">Element</span></span>|<span data-ttu-id="b49dd-127">Popis</span><span class="sxs-lookup"><span data-stu-id="b49dd-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b49dd-128">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="b49dd-128">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|<span data-ttu-id="b49dd-129">Deklarovaný typ přidá do kolekce deklarované typů.</span><span class="sxs-lookup"><span data-stu-id="b49dd-129">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b49dd-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b49dd-130">Remarks</span></span>  
 <span data-ttu-id="b49dd-131">Další informace o známé typy najdete v tématu [známé typy kontraktů dat](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) a <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="b49dd-131">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="b49dd-132">Najdete v článku [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) příklad použití tohoto elementu.</span><span class="sxs-lookup"><span data-stu-id="b49dd-132">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b49dd-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="b49dd-133">Example</span></span>  
  
```xml  
<add type="MyCompany.Library.Shape,   
           MyAssembly, Version=2.0.0.0, Culture=neutral,  
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">  
           <knownType type="MyCompany.Library.Circle,   
                      MyAssembly, Version=2.0.0.0, Culture=neutral,  
                      PublicKeyToken=XXXXXX,  
                      processorArchitecture=MSIL"/>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b49dd-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="b49dd-134">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="b49dd-135">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="b49dd-135">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="b49dd-136">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="b49dd-136">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="b49dd-137">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="b49dd-137">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
