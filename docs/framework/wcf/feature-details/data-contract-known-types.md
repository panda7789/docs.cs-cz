---
title: Známé typy kontraktů dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], known types
- KnownTypeAttribute [WCF]
- KnownTypes [WCF]
ms.assetid: 1a0baea1-27b7-470d-9136-5bbad86c4337
ms.openlocfilehash: dc297bd35d7bfdb25fc50135b8e684e1b9452cb2
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592582"
---
# <a name="data-contract-known-types"></a><span data-ttu-id="a180b-102">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="a180b-102">Data Contract Known Types</span></span>
<span data-ttu-id="a180b-103"><xref:System.Runtime.Serialization.KnownTypeAttribute> Třídy můžete zadat v předstihu, typy, které by měly být zahrnuty k posouzení vlastní během deserializace.</span><span class="sxs-lookup"><span data-stu-id="a180b-103">The <xref:System.Runtime.Serialization.KnownTypeAttribute> class allows you to specify, in advance, the types that should be included for consideration during deserialization.</span></span> <span data-ttu-id="a180b-104">Funkční příklad najdete v článku [známé typy](../../../../docs/framework/wcf/samples/known-types.md) příklad.</span><span class="sxs-lookup"><span data-stu-id="a180b-104">For a working example, see the [Known Types](../../../../docs/framework/wcf/samples/known-types.md) example.</span></span>  
  
 <span data-ttu-id="a180b-105">Za normálních okolností při předávání parametrů a vrácených hodnot mezi klientem a službou, oba koncové body sdílet všechny kontrakty dat data předávají.</span><span class="sxs-lookup"><span data-stu-id="a180b-105">Normally, when passing parameters and return values between a client and a service, both endpoints share all of the data contracts of the data to be transmitted.</span></span> <span data-ttu-id="a180b-106">Ale to není případ v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="a180b-106">However, this is not the case in the following circumstances:</span></span>  
  
- <span data-ttu-id="a180b-107">Kontrakt odeslaná data jsou odvozena z smlouvy očekávaná data.</span><span class="sxs-lookup"><span data-stu-id="a180b-107">The sent data contract is derived from the expected data contract.</span></span> <span data-ttu-id="a180b-108">Další informace najdete v části o dědičnosti v [ekvivalence kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)).</span><span class="sxs-lookup"><span data-stu-id="a180b-108">For more information, see the section about inheritance in [Data Contract Equivalence](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)).</span></span> <span data-ttu-id="a180b-109">V takovém případě přenášených dat nemá stejná data smlouvy podle očekávání tím přijímající koncový bod.</span><span class="sxs-lookup"><span data-stu-id="a180b-109">In that case, the transmitted data does not have the same data contract as expected by the receiving endpoint.</span></span>  
  
- <span data-ttu-id="a180b-110">Deklarovaný typ informace předávají je rozhraní, na rozdíl od třídy, struktury nebo výčtu.</span><span class="sxs-lookup"><span data-stu-id="a180b-110">The declared type for the information to be transmitted is an interface, as opposed to a class, structure, or enumeration.</span></span> <span data-ttu-id="a180b-111">Proto ho nemůže být známé předem jakým typem, že implementuje rozhraní je ve skutečnosti odesílány. a proto přijímající koncový bod nemůže určit předem kontraktu dat pro přenášená data.</span><span class="sxs-lookup"><span data-stu-id="a180b-111">Therefore, it cannot be known in advance which type that implements the interface is actually sent and therefore, the receiving endpoint cannot determine in advance the data contract for the transmitted data.</span></span>  
  
- <span data-ttu-id="a180b-112">Je deklarovaný typ informace předávají <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="a180b-112">The declared type for the information to be transmitted is <xref:System.Object>.</span></span> <span data-ttu-id="a180b-113">Protože každý typ dědí z <xref:System.Object>a to nemůže být předem známý typů, které se skutečně přijde, přijímající koncový bod nemůže určit předem kontraktu dat pro přenášená data.</span><span class="sxs-lookup"><span data-stu-id="a180b-113">Because every type inherits from <xref:System.Object>, and it cannot be known in advance which type is actually sent, the receiving endpoint cannot determine in advance the data contract for the transmitted data.</span></span> <span data-ttu-id="a180b-114">Toto je zvláštní případ první položky: Každý kontraktu dat. je odvozena z výchozí prázdné datové kontrakt, který je generován pro <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="a180b-114">This is a special case of the first item: Every data contract derives from the default, a blank data contract that is generated for <xref:System.Object>.</span></span>  
  
- <span data-ttu-id="a180b-115">Některé typy, jako je například typy .NET Framework, mají členy, které jsou v jednom z předchozích tří kategorií.</span><span class="sxs-lookup"><span data-stu-id="a180b-115">Some types, which include .NET Framework types, have members that are in one of the preceding three categories.</span></span> <span data-ttu-id="a180b-116">Například <xref:System.Collections.Hashtable> používá <xref:System.Object> k uložení skutečných objektů v zatřiďovací tabulce.</span><span class="sxs-lookup"><span data-stu-id="a180b-116">For example, <xref:System.Collections.Hashtable> uses <xref:System.Object> to store the actual objects in the hash table.</span></span> <span data-ttu-id="a180b-117">Při serializaci těchto typů nelze určit přijímající straně předem kontraktu dat pro tyto členy.</span><span class="sxs-lookup"><span data-stu-id="a180b-117">When serializing these types, the receiving side cannot determine in advance the data contract for these members.</span></span>  
  
## <a name="the-knowntypeattribute-class"></a><span data-ttu-id="a180b-118">Třída KnownTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="a180b-118">The KnownTypeAttribute Class</span></span>  
 <span data-ttu-id="a180b-119">Po přijetí na koncový bod příjmu dat, pokusí se modul runtime WCF deserializovat data do instance stejného typu language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="a180b-119">When data arrives at a receiving endpoint, the WCF runtime attempts to deserialize the data into an instance of a common language runtime (CLR) type.</span></span> <span data-ttu-id="a180b-120">Typ, který je vytvořena instance pro deserializaci je vybrán zkontrolováním první příchozí zprávy k určení dat smlouvy tak, aby odpovídal který obsah zprávy.</span><span class="sxs-lookup"><span data-stu-id="a180b-120">The type that is instantiated for deserialization is chosen by first inspecting the incoming message to determine the data contract to which the contents of the message conform.</span></span> <span data-ttu-id="a180b-121">Modul deserializace se pak pokusí se najít typ CLR, který implementuje kontrakt dat kompatibilní s obsah zprávy.</span><span class="sxs-lookup"><span data-stu-id="a180b-121">The deserialization engine then attempts to find a CLR type that implements a data contract compatible with the message contents.</span></span> <span data-ttu-id="a180b-122">Sadu Release candidate typů, které modul deserializace umožňuje během tohoto procesu se označuje jako sada deserializátor "známých typů."</span><span class="sxs-lookup"><span data-stu-id="a180b-122">The set of candidate types that the deserialization engine allows for during this process is referred to as the deserializer's set of "known types."</span></span>  
  
 <span data-ttu-id="a180b-123">Jedním ze způsobů, aby modul deserializace vědět o typu je pomocí <xref:System.Runtime.Serialization.KnownTypeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a180b-123">One way to let the deserialization engine know about a type is by using the <xref:System.Runtime.Serialization.KnownTypeAttribute>.</span></span> <span data-ttu-id="a180b-124">Atribut nelze použít pro jednotlivé datové členy pouze pro celé datové typy kontraktu.</span><span class="sxs-lookup"><span data-stu-id="a180b-124">The attribute cannot be applied to individual data members, only to whole data contract types.</span></span> <span data-ttu-id="a180b-125">Atribut je použit *vnějšího typu* , může být třída nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="a180b-125">The attribute is applied to an *outer type* that can be a class or a structure.</span></span> <span data-ttu-id="a180b-126">Ve své nejzákladnější využití použití atributu určuje typ jako "známý typ".</span><span class="sxs-lookup"><span data-stu-id="a180b-126">In its most basic usage, applying the attribute specifies a type as a "known type."</span></span> <span data-ttu-id="a180b-127">To způsobí, že známý typ jako součást sadu známých typů pokaždé, když se objekt z vnějšího typu nebo libovolný objekt označovány prostřednictvím jejích členů je deserializován.</span><span class="sxs-lookup"><span data-stu-id="a180b-127">This causes the known type to be a part of the set of known types whenever an object of the outer type or any object referred to through its members is being deserialized.</span></span> <span data-ttu-id="a180b-128">Více než jeden <xref:System.Runtime.Serialization.KnownTypeAttribute> atribut lze použít pro stejného typu.</span><span class="sxs-lookup"><span data-stu-id="a180b-128">More than one <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute can be applied to the same type.</span></span>  
  
## <a name="known-types-and-primitives"></a><span data-ttu-id="a180b-129">Známé typy a primitiv</span><span class="sxs-lookup"><span data-stu-id="a180b-129">Known Types and Primitives</span></span>  
 <span data-ttu-id="a180b-130">Primitivní typy, jakož i určité typy, které jsou považovány za primitivních elementů (například <xref:System.DateTime> a <xref:System.Xml.XmlElement>) jsou vždy "označuje" a už nikdy nemusíte přidají díky tomuto mechanismu.</span><span class="sxs-lookup"><span data-stu-id="a180b-130">Primitive types, as well as certain types treated as primitives (for example, <xref:System.DateTime> and <xref:System.Xml.XmlElement>) are always "known" and never have to be added through this mechanism.</span></span> <span data-ttu-id="a180b-131">Pole jednoduchých typů je však nutné explicitně přidat.</span><span class="sxs-lookup"><span data-stu-id="a180b-131">However, arrays of primitive types have to be added explicitly.</span></span> <span data-ttu-id="a180b-132">Většina kolekce se považují za ekvivalentní k polím.</span><span class="sxs-lookup"><span data-stu-id="a180b-132">Most collections are considered equivalent to arrays.</span></span> <span data-ttu-id="a180b-133">(Neobecné kolekce se považují za ekvivalentní polí <xref:System.Object>).</span><span class="sxs-lookup"><span data-stu-id="a180b-133">(Non-generic collections are considered equivalent to arrays of <xref:System.Object>).</span></span> <span data-ttu-id="a180b-134">Příklad pomocí primitiv, primitivní pole a kolekce primitivní, najdete v příkladu 4.</span><span class="sxs-lookup"><span data-stu-id="a180b-134">For an example of the using primitives, primitive arrays, and primitive collections, see Example 4.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a180b-135">Na rozdíl od jiných primitivní typy <xref:System.DateTimeOffset> struktura není známý typ ve výchozím nastavení, takže ho musí ručně přidat do seznamu známých typů.</span><span class="sxs-lookup"><span data-stu-id="a180b-135">Unlike other primitive types, the <xref:System.DateTimeOffset> structure is not a known type by default, so it must be manually added to the list of known types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="a180b-136">Příklady</span><span class="sxs-lookup"><span data-stu-id="a180b-136">Examples</span></span>  
 <span data-ttu-id="a180b-137">Následující příklady ukazují <xref:System.Runtime.Serialization.KnownTypeAttribute> třída používá.</span><span class="sxs-lookup"><span data-stu-id="a180b-137">The following examples show the <xref:System.Runtime.Serialization.KnownTypeAttribute> class in use.</span></span>  
  
#### <a name="example-1"></a><span data-ttu-id="a180b-138">Příklad 1</span><span class="sxs-lookup"><span data-stu-id="a180b-138">Example 1</span></span>  
 <span data-ttu-id="a180b-139">Existují tři třídy s vztah dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="a180b-139">There are three classes with an inheritance relationship.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#1)]
 [!code-vb[C_KnownTypeAttribute#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#1)]  
  
 <span data-ttu-id="a180b-140">Následující `CompanyLogo` třídy lze serializovat, ale nelze deserializovat, pokud `ShapeOfLogo` členů je nastaven na hodnotu `CircleType` nebo `TriangleType` objektu, protože modul deserializace nerozpozná žádné typy s názvy datových kontraktů " Kruh"nebo"Trojúhelník".</span><span class="sxs-lookup"><span data-stu-id="a180b-140">The following `CompanyLogo` class can be serialized, but cannot be deserialized if the `ShapeOfLogo` member is set to either a `CircleType` or a `TriangleType` object, because the deserialization engine does not recognize any types with data contract names "Circle" or "Triangle."</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#2)]
 [!code-vb[C_KnownTypeAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#2)]  
  
 <span data-ttu-id="a180b-141">Správný způsob zápisu `CompanyLogo` typ je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="a180b-141">The correct way to write the `CompanyLogo` type is shown in the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#3)]
 [!code-vb[C_KnownTypeAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#3)]  
  
 <span data-ttu-id="a180b-142">Pokaždé, když vnější typ `CompanyLogo2` je deserializován, modul deserializace ví o `CircleType` a `TriangleType` a proto je schopen vyhledat odpovídající typy kontraktů dat "Kruh" a "Trojúhelník".</span><span class="sxs-lookup"><span data-stu-id="a180b-142">Whenever the outer type `CompanyLogo2` is being deserialized, the deserialization engine knows about `CircleType` and `TriangleType` and, therefore, is able to find matching types for the "Circle" and "Triangle" data contracts.</span></span>  
  
#### <a name="example-2"></a><span data-ttu-id="a180b-143">Příklad 2</span><span class="sxs-lookup"><span data-stu-id="a180b-143">Example 2</span></span>  
 <span data-ttu-id="a180b-144">V následujícím příkladu i v případě, obě `CustomerTypeA` a `CustomerTypeB` mít `Customer` kontraktu dat, instance `CustomerTypeB` vždy, když se vytvoří `PurchaseOrder` je deserializovat, protože pouze `CustomerTypeB` se ví, modul deserializace.</span><span class="sxs-lookup"><span data-stu-id="a180b-144">In the following example, even though both `CustomerTypeA` and `CustomerTypeB` have the `Customer` data contract, an instance of `CustomerTypeB` is created whenever a `PurchaseOrder` is deserialized, because only `CustomerTypeB` is known to the deserialization engine.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#4)]
 [!code-vb[C_KnownTypeAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#4)]  
  
#### <a name="example-3"></a><span data-ttu-id="a180b-145">Příklad 3</span><span class="sxs-lookup"><span data-stu-id="a180b-145">Example 3</span></span>  
 <span data-ttu-id="a180b-146">V následujícím příkladu <xref:System.Collections.Hashtable> ukládá obsah interně jako <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="a180b-146">In the following example, a <xref:System.Collections.Hashtable> stores its contents internally as <xref:System.Object>.</span></span> <span data-ttu-id="a180b-147">Úspěšně deserializovat zatřiďovací tabulku, musíte znát modul deserializace sadu možných typů, které se mohou vyskytnout existuje.</span><span class="sxs-lookup"><span data-stu-id="a180b-147">To successfully deserialize a hash table, the deserialization engine must know the set of possible types that can occur there.</span></span> <span data-ttu-id="a180b-148">V tomto případě jsme předem vědět pouze `Book` a `Magazine` objekty jsou uloženy v `Catalog`, takže ty jsou přidány pomocí <xref:System.Runtime.Serialization.KnownTypeAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="a180b-148">In this case, we know in advance that only `Book` and `Magazine` objects are stored in the `Catalog`, so those are added using the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#5)]
 [!code-vb[C_KnownTypeAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#5)]  
  
#### <a name="example-4"></a><span data-ttu-id="a180b-149">Příklad 4:</span><span class="sxs-lookup"><span data-stu-id="a180b-149">Example 4</span></span>  
 <span data-ttu-id="a180b-150">V následujícím příkladu kontrakt dat ukládá číslo a operace provádět na číslo.</span><span class="sxs-lookup"><span data-stu-id="a180b-150">In the following example, a data contract stores a number and an operation to perform on the number.</span></span> <span data-ttu-id="a180b-151">`Numbers` Datový člen může být celé číslo, pole celých čísel, nebo <xref:System.Collections.Generic.List%601> obsahující celá čísla.</span><span class="sxs-lookup"><span data-stu-id="a180b-151">The `Numbers` data member can be an integer, an array of integers, or a <xref:System.Collections.Generic.List%601> that contains integers.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="a180b-152">Bude to fungovat jenom na straně klienta Pokud SVCUTIL. Soubor EXE slouží ke generování WCF proxy.</span><span class="sxs-lookup"><span data-stu-id="a180b-152">This will only work on the client side if SVCUTIL.EXE is used to generate a WCF proxy.</span></span> <span data-ttu-id="a180b-153">SVCUTIL. Soubor EXE načte metadata ze služby včetně všech známých typů.</span><span class="sxs-lookup"><span data-stu-id="a180b-153">SVCUTIL.EXE retrieves metadata from the service including any known types.</span></span> <span data-ttu-id="a180b-154">Bez těchto informací klienta nebude možné deserializovat typy.</span><span class="sxs-lookup"><span data-stu-id="a180b-154">Without this information a client will not be able to deserialize the types.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#6)]
 [!code-vb[C_KnownTypeAttribute#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#6)]  
  
 <span data-ttu-id="a180b-155">Toto je kód aplikace.</span><span class="sxs-lookup"><span data-stu-id="a180b-155">This is the application code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#7)]
 [!code-vb[C_KnownTypeAttribute#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#7)]  
  
## <a name="known-types-inheritance-and-interfaces"></a><span data-ttu-id="a180b-156">Známých typů, dědičnost a rozhraní</span><span class="sxs-lookup"><span data-stu-id="a180b-156">Known Types, Inheritance, and Interfaces</span></span>  
 <span data-ttu-id="a180b-157">Pokud je spojené s konkrétní typ použitím známý typ `KnownTypeAttribute` atribut, známý typ je přidružen také všechny odvozené typy tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="a180b-157">When a known type is associated with a particular type using the `KnownTypeAttribute` attribute, the known type is also associated with all of the derived types of that type.</span></span> <span data-ttu-id="a180b-158">Například viz následující kód.</span><span class="sxs-lookup"><span data-stu-id="a180b-158">For example, see the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#8)]
 [!code-vb[C_KnownTypeAttribute#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#8)]  
  
 <span data-ttu-id="a180b-159">`DoubleDrawing` Třída nevyžaduje, aby `KnownTypeAttribute` atribut používat `Square` a `Circle` v `AdditionalShape` pole, protože základní třída (`Drawing`) už má tyto atributy použité.</span><span class="sxs-lookup"><span data-stu-id="a180b-159">The `DoubleDrawing` class does not require the `KnownTypeAttribute` attribute to use `Square` and `Circle` in the `AdditionalShape` field, because the base class (`Drawing`) already has these attributes applied.</span></span>  
  
 <span data-ttu-id="a180b-160">Známé typy lze přidružit pouze k tříd a struktur, není rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a180b-160">Known types can be associated only with classes and structures, not interfaces.</span></span>  
  
## <a name="known-types-using-open-generic-methods"></a><span data-ttu-id="a180b-161">Známé typy pomocí otevřené obecné metody</span><span class="sxs-lookup"><span data-stu-id="a180b-161">Known Types Using Open Generic Methods</span></span>  
 <span data-ttu-id="a180b-162">Může být potřeba přidat jako známý typ obecného typu.</span><span class="sxs-lookup"><span data-stu-id="a180b-162">It may be necessary to add a generic type as a known type.</span></span> <span data-ttu-id="a180b-163">Otevřený obecný typ. však nelze předat jako parametr `KnownTypeAttribute` atribut.</span><span class="sxs-lookup"><span data-stu-id="a180b-163">However, an open generic type cannot be passed as a parameter to the `KnownTypeAttribute` attribute.</span></span>  
  
 <span data-ttu-id="a180b-164">Tento problém můžete vyřešit pomocí alternativní mechanismus: Zapsat metodu, která vrátí seznam typů, který chcete přidat do kolekce známých typů.</span><span class="sxs-lookup"><span data-stu-id="a180b-164">This problem can be solved by using an alternative mechanism: Write a method that returns a list of types to add to the known types collection.</span></span> <span data-ttu-id="a180b-165">Název metody je pak zadaný jako argument řetězec k `KnownTypeAttribute` atribut z důvodu určitá omezení.</span><span class="sxs-lookup"><span data-stu-id="a180b-165">The name of the method is then specified as a string argument to the `KnownTypeAttribute` attribute due to some restrictions.</span></span>  
  
 <span data-ttu-id="a180b-166">Metodu, musí existovat v typu, na který `KnownTypeAttribute` atributu se použije, musí být statická, musí přijmout žádné parametry a musí vrátit objekt, který lze přiřadit k <xref:System.Collections.IEnumerable> z <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="a180b-166">The method must exist on the type to which the `KnownTypeAttribute` attribute is applied, must be static, must accept no parameters, and must return an object that can be assigned to <xref:System.Collections.IEnumerable> of <xref:System.Type>.</span></span>  
  
 <span data-ttu-id="a180b-167">Nelze kombinovat `KnownTypeAttribute` atribut s názvem metody a `KnownTypeAttribute` atributy se skutečné typy na stejného typu.</span><span class="sxs-lookup"><span data-stu-id="a180b-167">You cannot combine the `KnownTypeAttribute` attribute with a method name and `KnownTypeAttribute` attributes with actual types on the same type.</span></span> <span data-ttu-id="a180b-168">Kromě toho není možné použít více než jeden `KnownTypeAttribute` s názvem metody do stejného typu.</span><span class="sxs-lookup"><span data-stu-id="a180b-168">Furthermore, you cannot apply more than one `KnownTypeAttribute` with a method name to the same type.</span></span>  
  
 <span data-ttu-id="a180b-169">Podívejte se následující třídy.</span><span class="sxs-lookup"><span data-stu-id="a180b-169">See the following class.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#9)]
 [!code-vb[C_KnownTypeAttribute#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#9)]  
  
 <span data-ttu-id="a180b-170">`theDrawing` Obsahuje pole instance generické třídy `ColorDrawing` a obecnou třídu `BlackAndWhiteDrawing`, které dědí z obecné třídy `Drawing`.</span><span class="sxs-lookup"><span data-stu-id="a180b-170">The `theDrawing` field contains instances of a generic class `ColorDrawing` and a generic class `BlackAndWhiteDrawing`, both of which inherit from a generic class `Drawing`.</span></span> <span data-ttu-id="a180b-171">Za normálních okolností obě musí být přidané do známé typy, ale následující není platnou syntaxi pro atributy.</span><span class="sxs-lookup"><span data-stu-id="a180b-171">Normally, both must be added to known types, but the following is not valid syntax for attributes.</span></span>  
  
```csharp  
// Invalid syntax for attributes:  
// [KnownType(typeof(ColorDrawing<T>))]  
// [KnownType(typeof(BlackAndWhiteDrawing<T>))]  
```  
  
```vb  
' Invalid syntax for attributes:  
' <KnownType(GetType(ColorDrawing(Of T))), _  
' KnownType(GetType(BlackAndWhiteDrawing(Of T)))>  
```  
  
 <span data-ttu-id="a180b-172">Díky tomu se metoda musí být vytvořený vracet tyto typy.</span><span class="sxs-lookup"><span data-stu-id="a180b-172">Thus, a method must be created to return these types.</span></span> <span data-ttu-id="a180b-173">Správný způsob zápisu tohoto typu, zobrazí se v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="a180b-173">The correct way to write this type, then, is shown in the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#10)]
 [!code-vb[C_KnownTypeAttribute#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#10)]  
  
## <a name="additional-ways-to-add-known-types"></a><span data-ttu-id="a180b-174">Další způsoby, jak přidat známé typy</span><span class="sxs-lookup"><span data-stu-id="a180b-174">Additional Ways to Add Known Types</span></span>  
 <span data-ttu-id="a180b-175">Kromě toho známé typy, které je možné přidat prostřednictvím konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="a180b-175">Additionally, known types can be added through a configuration file.</span></span> <span data-ttu-id="a180b-176">To je užitečné, pokud není ovládací prvek na typ, který vyžaduje známých typů pro správné deserializace, jako je například při použití jiných výrobců zadejte knihovny Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a180b-176">This is useful when you do not control the type that requires known types for proper deserialization, such as when using third-party type libraries with Windows Communication Foundation (WCF).</span></span>  
  
 <span data-ttu-id="a180b-177">Následující konfigurační soubor ukazuje, jak určit známý typ v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="a180b-177">The following configuration file shows how to specify a known type in a configuration file.</span></span>  
  
 `<configuration>`  
  
 `<system.runtime.serialization>`  
  
 `<dataContractSerializer>`  
  
 `<declaredTypes>`  
  
 `<add type="MyCompany.Library.Shape,`  
  
 `MyAssembly, Version=2.0.0.0, Culture=neutral,`  
  
 `PublicKeyToken=XXXXXX, processorArchitecture=MSIL">`  
  
 `<knownType type="MyCompany.Library.Circle,`  
  
 `MyAssembly, Version=2.0.0.0, Culture=neutral,`  
  
 `PublicKeyToken=XXXXXX, processorArchitecture=MSIL"/>`  
  
 `</add>`  
  
 `</declaredTypes>`  
  
 `</dataContractSerializer>`  
  
 `</system.runtime.serialization>`  
  
 `</configuration>`  
  
 <span data-ttu-id="a180b-178">V předchozí konfiguraci souboru typ kontraktu dat s názvem `MyCompany.Library.Shape` je deklarován mít `MyCompany.Library.Circle` jako známý typ.</span><span class="sxs-lookup"><span data-stu-id="a180b-178">In the preceding configuration file a data contract type called `MyCompany.Library.Shape` is declared to have `MyCompany.Library.Circle` as a known type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a180b-179">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a180b-179">See also</span></span>

- <xref:System.Runtime.Serialization.KnownTypeAttribute>
- <xref:System.Collections.Hashtable>
- <xref:System.Object>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A>
- [<span data-ttu-id="a180b-180">Známé typy</span><span class="sxs-lookup"><span data-stu-id="a180b-180">Known Types</span></span>](../../../../docs/framework/wcf/samples/known-types.md)
- [<span data-ttu-id="a180b-181">Ekvivalence kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="a180b-181">Data Contract Equivalence</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [<span data-ttu-id="a180b-182">Navrhování kontraktů služby</span><span class="sxs-lookup"><span data-stu-id="a180b-182">Designing Service Contracts</span></span>](../../../../docs/framework/wcf/designing-service-contracts.md)
