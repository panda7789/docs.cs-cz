---
title: "omezující vlastnost"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 91c4e6aa-3e54-4b6c-a38a-abf27808cc85
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e72ecd610951a42ceb5c3aa581bf70f255e5e2f7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="facet"></a><span data-ttu-id="cc5e3-102">omezující vlastnost</span><span class="sxs-lookup"><span data-stu-id="cc5e3-102">facet</span></span>
<span data-ttu-id="cc5e3-103">A *omezující vlastnost* se používá k přidání podrobností do definice vlastnost primitivního typu.</span><span class="sxs-lookup"><span data-stu-id="cc5e3-103">A *facet* is used to add detail to a primitive type property definition.</span></span> <span data-ttu-id="cc5e3-104">A [vlastnost](../../../../docs/framework/data/adonet/property.md) definice obsahuje informace o vlastnost typu, ale často je nutné podrobněji.</span><span class="sxs-lookup"><span data-stu-id="cc5e3-104">A [property](../../../../docs/framework/data/adonet/property.md) definition contains information about the property type, but often more detail is necessary.</span></span> <span data-ttu-id="cc5e3-105">Typ entity v konceptuálním modelu například může mít vlastnost typu `String` jehož hodnota nemůže být nastavena na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="cc5e3-105">For example, an entity type in a conceptual model might have a property of type `String` whose value cannot be set to null.</span></span> <span data-ttu-id="cc5e3-106">Omezující vlastnosti umožňují určit tato úroveň podrobností.</span><span class="sxs-lookup"><span data-stu-id="cc5e3-106">Facets allow you to specify this level of detail.</span></span>  
  
 <span data-ttu-id="cc5e3-107">Následující tabulka popisuje omezující vlastnosti, které jsou podporovány v modelu EDM.</span><span class="sxs-lookup"><span data-stu-id="cc5e3-107">The table below describes the facets that are supported in the EDM.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cc5e3-108">Běhové prostředí, která používá implementace EDM určuje přesné hodnoty a chování omezující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="cc5e3-108">The exact values and behaviors of facets are determined by the run-time environment that uses an EDM implementation.</span></span>  
  
|<span data-ttu-id="cc5e3-109">Omezující vlastnost</span><span class="sxs-lookup"><span data-stu-id="cc5e3-109">Facet</span></span>|<span data-ttu-id="cc5e3-110">Popis</span><span class="sxs-lookup"><span data-stu-id="cc5e3-110">Description</span></span>|<span data-ttu-id="cc5e3-111">Platí pro</span><span class="sxs-lookup"><span data-stu-id="cc5e3-111">Applies to</span></span>|  
|-----------|-----------------|----------------|  
|`Collation`|<span data-ttu-id="cc5e3-112">Určuje pořadí řazení (nebo pořadí řazení) pro použití při provádění porovnání a řazení operací na hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="cc5e3-112">Specifies the collating sequence (or sorting sequence) to be used when performing comparison and ordering operations on values of the property.</span></span>|`String`|  
|`ConcurrencyMode`|<span data-ttu-id="cc5e3-113">Označuje, že hodnota vlastnosti má být použita pro optimistickou metodu souběžného kontroly.</span><span class="sxs-lookup"><span data-stu-id="cc5e3-113">Indicates that the value of the property should be used for optimistic concurrency checks.</span></span>|<span data-ttu-id="cc5e3-114">Všechny vlastnosti primitivní typ</span><span class="sxs-lookup"><span data-stu-id="cc5e3-114">All primitive type properties</span></span>|  
|`Default`|<span data-ttu-id="cc5e3-115">Určuje výchozí hodnotu vlastnosti, pokud při vytváření instance je zadána žádná hodnota.</span><span class="sxs-lookup"><span data-stu-id="cc5e3-115">Specifies the default value of the property if no value is supplied upon instantiation.</span></span>|<span data-ttu-id="cc5e3-116">Všechny vlastnosti primitivní typ</span><span class="sxs-lookup"><span data-stu-id="cc5e3-116">All primitive type properties</span></span>|  
|`FixedLength`|<span data-ttu-id="cc5e3-117">Určuje, zda se může lišit délka hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="cc5e3-117">Specifies whether the length of the property value can vary.</span></span>|<span data-ttu-id="cc5e3-118">`Binary`, `String`</span><span class="sxs-lookup"><span data-stu-id="cc5e3-118">`Binary`, `String`</span></span>|  
|`MaxLength`|<span data-ttu-id="cc5e3-119">Určuje maximální délku hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="cc5e3-119">Specifies the maximum length of the property value.</span></span>|<span data-ttu-id="cc5e3-120">`Binary`, `String`</span><span class="sxs-lookup"><span data-stu-id="cc5e3-120">`Binary`, `String`</span></span>|  
|`Nullable`|<span data-ttu-id="cc5e3-121">Určuje, zda vlastnost může mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="cc5e3-121">Specifies whether the property can have a null value.</span></span>|<span data-ttu-id="cc5e3-122">Všechny vlastnosti primitivní typ</span><span class="sxs-lookup"><span data-stu-id="cc5e3-122">All primitive type properties</span></span>|  
|`Precision`|<span data-ttu-id="cc5e3-123">Pro vlastnosti typu `Decimal`, určuje počet číslic, může mít hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="cc5e3-123">For properties of type `Decimal`, specifies the number of digits a property value can have.</span></span> <span data-ttu-id="cc5e3-124">Pro vlastnosti typu `Time`, `DateTime`, a `DateTimeOffset`, určuje počet číslic za desetinnou čárkou sekund hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="cc5e3-124">For properties of type `Time`, `DateTime`, and `DateTimeOffset`, specifies the number of digits for the fractional part of seconds of the property value.</span></span>|<span data-ttu-id="cc5e3-125">`DateTime`, `DateTimeOffset`, `Decimal`, `Time`,</span><span class="sxs-lookup"><span data-stu-id="cc5e3-125">`DateTime`, `DateTimeOffset`, `Decimal`, `Time`,</span></span>|  
|`Scale`|<span data-ttu-id="cc5e3-126">Určuje počet číslic vpravo od desetinné čárky hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="cc5e3-126">Specifies the number of digits to the right of the decimal point for the property value.</span></span>|<span data-ttu-id="cc5e3-127">Desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="cc5e3-127">Decimal</span></span>|  
|`Unicode`|<span data-ttu-id="cc5e3-128">Určuje, zda hodnota vlastnosti je uložena ve formátu Unicode.</span><span class="sxs-lookup"><span data-stu-id="cc5e3-128">Indicates whether the property value is stored as Unicode.</span></span>|`String`|  
  
## <a name="example"></a><span data-ttu-id="cc5e3-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="cc5e3-129">Example</span></span>  
 <span data-ttu-id="cc5e3-130">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) používá specifické pro doménu jazyka (DSL) nazývaného konceptuálního schématu definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) k definování konceptuálních modelech.</span><span class="sxs-lookup"><span data-stu-id="cc5e3-130">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="cc5e3-131">Definuje následující CSDL `Book` typ entity.</span><span class="sxs-lookup"><span data-stu-id="cc5e3-131">The following CSDL defines a `Book` entity type.</span></span> <span data-ttu-id="cc5e3-132">Všimněte si, že omezující vlastnosti jsou implementované jako atributy XML.</span><span class="sxs-lookup"><span data-stu-id="cc5e3-132">Note that facets are implemented as XML attributes.</span></span> <span data-ttu-id="cc5e3-133">Hodnoty omezující vlastnosti udávají, že žádná vlastnost může být nastavena na hodnotu null a který `Scale` a `Precision` z `Revision` každou vlastnost je nastavena na 29.</span><span class="sxs-lookup"><span data-stu-id="cc5e3-133">The facet values indicate that no property can be set to null, and that the `Scale` and `Precision` of the `Revision` property are each set to 29.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a><span data-ttu-id="cc5e3-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="cc5e3-134">See Also</span></span>  
 [<span data-ttu-id="cc5e3-135">Entity Data Model klíčové koncepty</span><span class="sxs-lookup"><span data-stu-id="cc5e3-135">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="cc5e3-136">Datového modelu entity</span><span class="sxs-lookup"><span data-stu-id="cc5e3-136">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
