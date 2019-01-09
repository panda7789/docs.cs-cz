---
title: '&lt;add&gt; elementu &lt;declaredTypes&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
ms.openlocfilehash: 587c70a7b583c99e66eebac4055415e1e6a635b2
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146105"
---
# <a name="ltaddgt-of-ltdeclaredtypesgt-element"></a><span data-ttu-id="68c93-102">&lt;add&gt; elementu &lt;declaredTypes&gt;</span><span class="sxs-lookup"><span data-stu-id="68c93-102">&lt;add&gt; of &lt;declaredTypes&gt; Element</span></span>
<span data-ttu-id="68c93-103">Přidá typ používaný <xref:System.Runtime.Serialization.DataContractSerializer> během deserializace.</span><span class="sxs-lookup"><span data-stu-id="68c93-103">Adds a type used by the <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="68c93-104">Každý deklarovaný typ obsahuje známé typy, které budou vráceny jako pole nebo vlastnost deklarovaného typu.</span><span class="sxs-lookup"><span data-stu-id="68c93-104">Each declared type includes the known types that will be returned as a field or property of the declared type.</span></span>  
  
 <span data-ttu-id="68c93-105">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="68c93-105">system.runtime.serialization</span></span>  
<span data-ttu-id="68c93-106">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="68c93-106">\<dataContractSerializer></span></span>  
<span data-ttu-id="68c93-107">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="68c93-107">\<declaredTypes></span></span>  
<span data-ttu-id="68c93-108">\<Přidat > z \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="68c93-108">\<add> of \<declaredTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68c93-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68c93-109">Syntax</span></span>  
  
```xml  
<add type="String">
  <knownType type="String">
    <parameter index="Integer"
               type="String" />
  </knownType>
</add>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="68c93-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="68c93-110">Attributes and Elements</span></span>  
 <span data-ttu-id="68c93-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="68c93-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="68c93-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="68c93-112">Attributes</span></span>  
  
|<span data-ttu-id="68c93-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="68c93-113">Attribute</span></span>|<span data-ttu-id="68c93-114">Popis</span><span class="sxs-lookup"><span data-stu-id="68c93-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="68c93-115">– typ</span><span class="sxs-lookup"><span data-stu-id="68c93-115">type</span></span>|<span data-ttu-id="68c93-116">Požadovaný atribut typu string.</span><span class="sxs-lookup"><span data-stu-id="68c93-116">Required string attribute.</span></span><br /><br /> <span data-ttu-id="68c93-117">Určuje název typu (včetně oboru názvů), název sestavení, číslo verze, jazykovou verzi a token veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="68c93-117">Specifies the type name (including namespace), assembly name, version number, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="68c93-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="68c93-118">Child Elements</span></span>  
  
|<span data-ttu-id="68c93-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="68c93-119">Element</span></span>|<span data-ttu-id="68c93-120">Popis</span><span class="sxs-lookup"><span data-stu-id="68c93-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="68c93-121">\<Třída knownType ></span><span class="sxs-lookup"><span data-stu-id="68c93-121">\<knownType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|<span data-ttu-id="68c93-122">Určuje známý typ deklarovaný typ, který je přidáván.</span><span class="sxs-lookup"><span data-stu-id="68c93-122">Specifies the known type for the declared type that is being added.</span></span> <span data-ttu-id="68c93-123">Pokud je deklarovaný typ obecného typu, pak musíte taky přidat prvek parametru, který se `<knownType>` element k určení, které obecný parametr se používá k vrácení známého typu.</span><span class="sxs-lookup"><span data-stu-id="68c93-123">If the declared type is a generic type, then you must also add a parameter element to the `<knownType>` element to specify which generic parameter is used to return the known type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="68c93-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="68c93-124">Parent Elements</span></span>  
  
|<span data-ttu-id="68c93-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="68c93-125">Element</span></span>|<span data-ttu-id="68c93-126">Popis</span><span class="sxs-lookup"><span data-stu-id="68c93-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="68c93-127">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="68c93-127">\<declaredTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/declaredtypes.md)|<span data-ttu-id="68c93-128">Obsahuje typy, které vyžadují během deserializace za pomocí známých typů <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="68c93-128">Contains the types that require known types during deserialization by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68c93-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="68c93-129">Remarks</span></span>  
 <span data-ttu-id="68c93-130">Další informace o známých typů najdete v tématu [známé typy kontraktů dat.](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) a <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="68c93-130">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="68c93-131">Zobrazit [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) příklad použití tohoto prvku.</span><span class="sxs-lookup"><span data-stu-id="68c93-131">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="68c93-132">Pokud chcete přidat <xref:System.Object> jako typ `<declaredType>`, <xref:System.Configuration.ConfigurationErrorsException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="68c93-132">If you add the <xref:System.Object> type as a `<declaredType>`, a <xref:System.Configuration.ConfigurationErrorsException> is thrown.</span></span> <span data-ttu-id="68c93-133">Je to proto, <xref:System.Object> typ nelze použít jako deklarovaný typ v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="68c93-133">This is because the <xref:System.Object> type cannot be used as a declared type in configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68c93-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="68c93-134">Example</span></span>  
  
```xml  
<add type="MyCompany.Library.Shape,
           MyAssembly, Version=2.0.0.0, Culture=neutral,
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">
  <knownType type="MyCompany.Library.Circle,
                   MyAssembly, Version=2.0.0.0, Culture=neutral,
                   PublicKeyToken=XXXXXX,
                   processorArchitecture=MSIL" />
</add>
```  
  
## <a name="see-also"></a><span data-ttu-id="68c93-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="68c93-135">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="68c93-136">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="68c93-136">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="68c93-137">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="68c93-137">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="68c93-138">\<Přidat > z \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="68c93-138">\<add> of \<declaredTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
