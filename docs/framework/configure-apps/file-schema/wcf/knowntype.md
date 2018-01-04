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
ms.workload: dotnet
ms.openlocfilehash: 439d241d73df4db2820eac72c5e88e7d9023c6a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltknowntypegt"></a><span data-ttu-id="704e9-102">&lt;Třída knownType&gt;</span><span class="sxs-lookup"><span data-stu-id="704e9-102">&lt;knownType&gt;</span></span>
<span data-ttu-id="704e9-103">Určuje typ má být používána <xref:System.Runtime.Serialization.DataContractSerializer> během deserializace.</span><span class="sxs-lookup"><span data-stu-id="704e9-103">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="704e9-104">Element "známému typu" Určuje, který vrátí pole nebo vlastnost "deklarovaný typ".</span><span class="sxs-lookup"><span data-stu-id="704e9-104">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="704e9-105">Další informace najdete v tématu [známé typy kontraktů dat](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="704e9-105">For more information, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="704e9-106">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="704e9-106">\<system.runtime.serialization></span></span>  
<span data-ttu-id="704e9-107">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="704e9-107">\<dataContractSerializer></span></span>  
<span data-ttu-id="704e9-108">\<declaredTypes > elementu</span><span class="sxs-lookup"><span data-stu-id="704e9-108">\<declaredTypes> Element</span></span>  
<span data-ttu-id="704e9-109">\<Přidat > z \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="704e9-109">\<add> of \<declaredTypes></span></span>  
<span data-ttu-id="704e9-110">\<Třída knownType > elementu</span><span class="sxs-lookup"><span data-stu-id="704e9-110">\<knownType> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="704e9-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="704e9-111">Syntax</span></span>  
  
```xml  
<knownType type="String">  
     <parameter index="Integer"  
                type="String" />  
</knownType>  
```  
  
## <a name="type"></a><span data-ttu-id="704e9-112">Typ</span><span class="sxs-lookup"><span data-stu-id="704e9-112">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="704e9-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="704e9-113">Attributes and Elements</span></span>  
 <span data-ttu-id="704e9-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="704e9-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="704e9-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="704e9-115">Attributes</span></span>  
  
|<span data-ttu-id="704e9-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="704e9-116">Attribute</span></span>|<span data-ttu-id="704e9-117">Popis</span><span class="sxs-lookup"><span data-stu-id="704e9-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="704e9-118">– typ</span><span class="sxs-lookup"><span data-stu-id="704e9-118">type</span></span>|<span data-ttu-id="704e9-119">Určuje typ (včetně oboru názvů), název sestavení, verze, jazykové verze a tokenu veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="704e9-119">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="704e9-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="704e9-120">Child Elements</span></span>  
  
|<span data-ttu-id="704e9-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="704e9-121">Element</span></span>|<span data-ttu-id="704e9-122">Popis</span><span class="sxs-lookup"><span data-stu-id="704e9-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="704e9-123">\<parametr ></span><span class="sxs-lookup"><span data-stu-id="704e9-123">\<parameter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/parameter.md)|<span data-ttu-id="704e9-124">Určuje indexu parametru, je-li deklarovaný typ obecného typu.</span><span class="sxs-lookup"><span data-stu-id="704e9-124">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="704e9-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="704e9-125">Parent Elements</span></span>  
  
|<span data-ttu-id="704e9-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="704e9-126">Element</span></span>|<span data-ttu-id="704e9-127">Popis</span><span class="sxs-lookup"><span data-stu-id="704e9-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="704e9-128">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="704e9-128">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|<span data-ttu-id="704e9-129">Deklarovaný typ přidá do kolekce deklarované typů.</span><span class="sxs-lookup"><span data-stu-id="704e9-129">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="704e9-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="704e9-130">Remarks</span></span>  
 <span data-ttu-id="704e9-131">Další informace o známé typy najdete v tématu [známé typy kontraktů dat](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) a <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="704e9-131">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="704e9-132">Najdete v článku [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) příklad použití tohoto elementu.</span><span class="sxs-lookup"><span data-stu-id="704e9-132">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="704e9-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="704e9-133">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="704e9-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="704e9-134">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="704e9-135">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="704e9-135">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="704e9-136">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="704e9-136">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="704e9-137">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="704e9-137">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
