---
title: '&lt;add&gt; elementu &lt;declaredTypes&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
ms.openlocfilehash: 90eaf11ce8b9e3675a23ed3875680b03f149b56b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltdeclaredtypesgt-element"></a><span data-ttu-id="1a6d4-102">&lt;add&gt; elementu &lt;declaredTypes&gt;</span><span class="sxs-lookup"><span data-stu-id="1a6d4-102">&lt;add&gt; of &lt;declaredTypes&gt; Element</span></span>
<span data-ttu-id="1a6d4-103">Přidá typ používaný <xref:System.Runtime.Serialization.DataContractSerializer> během deserializace.</span><span class="sxs-lookup"><span data-stu-id="1a6d4-103">Adds a type used by the <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="1a6d4-104">Každý deklarovaný typ obsahuje známé typy, které bude vrácen jako pole nebo vlastnost deklarovaného typu.</span><span class="sxs-lookup"><span data-stu-id="1a6d4-104">Each declared type includes the known types that will be returned as a field or property of the declared type.</span></span>  
  
 <span data-ttu-id="1a6d4-105">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="1a6d4-105">system.runtime.serialization</span></span>  
<span data-ttu-id="1a6d4-106">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="1a6d4-106">\<dataContractSerializer></span></span>  
<span data-ttu-id="1a6d4-107">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="1a6d4-107">\<declaredTypes></span></span>  
<span data-ttu-id="1a6d4-108">\<Přidat > z \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="1a6d4-108">\<add> of \<declaredTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a6d4-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a6d4-109">Syntax</span></span>  
  
```xml  
<add type="String">  
   <knownType type="String">  
       <parameter index="Integer"  
                  type="String" />  
   </knownType>  
</add>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1a6d4-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1a6d4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1a6d4-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1a6d4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1a6d4-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="1a6d4-112">Attributes</span></span>  
  
|<span data-ttu-id="1a6d4-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="1a6d4-113">Attribute</span></span>|<span data-ttu-id="1a6d4-114">Popis</span><span class="sxs-lookup"><span data-stu-id="1a6d4-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1a6d4-115">– typ</span><span class="sxs-lookup"><span data-stu-id="1a6d4-115">type</span></span>|<span data-ttu-id="1a6d4-116">Požadovaný atribut typu string.</span><span class="sxs-lookup"><span data-stu-id="1a6d4-116">Required string attribute.</span></span><br /><br /> <span data-ttu-id="1a6d4-117">Určuje název typu (včetně oboru názvů), název sestavení, číslo verze, jazykové verze a tokenu veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="1a6d4-117">Specifies the type name (including namespace), assembly name, version number, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1a6d4-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1a6d4-118">Child Elements</span></span>  
  
|<span data-ttu-id="1a6d4-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="1a6d4-119">Element</span></span>|<span data-ttu-id="1a6d4-120">Popis</span><span class="sxs-lookup"><span data-stu-id="1a6d4-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1a6d4-121">\<Třída knownType ></span><span class="sxs-lookup"><span data-stu-id="1a6d4-121">\<knownType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|<span data-ttu-id="1a6d4-122">Určuje známý typ deklarovaný typ, který je přidáván.</span><span class="sxs-lookup"><span data-stu-id="1a6d4-122">Specifies the known type for the declared type that is being added.</span></span> <span data-ttu-id="1a6d4-123">Pokud deklarovaný typ je obecný typ, pak musíte taky přidat parametr element na `<knownType>` elementu, který chcete určit, které obecný parametr se používá k vrácení známý typ.</span><span class="sxs-lookup"><span data-stu-id="1a6d4-123">If the declared type is a generic type, then you must also add a parameter element to the `<knownType>` element to specify which generic parameter is used to return the known type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1a6d4-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1a6d4-124">Parent Elements</span></span>  
  
|<span data-ttu-id="1a6d4-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="1a6d4-125">Element</span></span>|<span data-ttu-id="1a6d4-126">Popis</span><span class="sxs-lookup"><span data-stu-id="1a6d4-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1a6d4-127">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="1a6d4-127">\<declaredTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/declaredtypes.md)|<span data-ttu-id="1a6d4-128">Obsahuje typy, které vyžadují známé typy během deserializace pomocí <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="1a6d4-128">Contains the types that require known types during deserialization by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a6d4-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1a6d4-129">Remarks</span></span>  
 <span data-ttu-id="1a6d4-130">Další informace o známé typy najdete v tématu [známé typy kontraktů dat](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) a <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="1a6d4-130">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="1a6d4-131">Najdete v článku [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) příklad použití tohoto elementu.</span><span class="sxs-lookup"><span data-stu-id="1a6d4-131">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1a6d4-132">Pokud přidáte <xref:System.Object> zadejte jako `<declaredType>`, <xref:System.Configuration.ConfigurationErrorsException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="1a6d4-132">If you add the <xref:System.Object> type as a `<declaredType>`, a <xref:System.Configuration.ConfigurationErrorsException> is thrown.</span></span> <span data-ttu-id="1a6d4-133">Důvodem je, že <xref:System.Object> typu nelze použít jako deklarovaný typ v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="1a6d4-133">This is because the <xref:System.Object> type cannot be used as a declared type in configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a6d4-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="1a6d4-134">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1a6d4-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="1a6d4-135">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="1a6d4-136">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="1a6d4-136">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="1a6d4-137">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="1a6d4-137">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="1a6d4-138">\<Přidat > z \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="1a6d4-138">\<add> of \<declaredTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
