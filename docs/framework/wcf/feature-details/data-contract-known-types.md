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
ms.openlocfilehash: b7d78def4d656dea59af5400c7ed7deeef28cd0c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597446"
---
# <a name="data-contract-known-types"></a><span data-ttu-id="0a299-102">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="0a299-102">Data Contract Known Types</span></span>
<span data-ttu-id="0a299-103"><xref:System.Runtime.Serialization.KnownTypeAttribute>Třída umožňuje zadat předem typy, které by měly být zahrnuty za účelem posouzení během deserializace.</span><span class="sxs-lookup"><span data-stu-id="0a299-103">The <xref:System.Runtime.Serialization.KnownTypeAttribute> class allows you to specify, in advance, the types that should be included for consideration during deserialization.</span></span> <span data-ttu-id="0a299-104">Pracovní příklad naleznete v příkladu [známých typů](../samples/known-types.md) .</span><span class="sxs-lookup"><span data-stu-id="0a299-104">For a working example, see the [Known Types](../samples/known-types.md) example.</span></span>  
  
 <span data-ttu-id="0a299-105">Obvykle při předávání parametrů a vrácení hodnot mezi klientem a službou se oba koncové body sdílí se všemi kontrakty dat dat, která se mají přenést.</span><span class="sxs-lookup"><span data-stu-id="0a299-105">Normally, when passing parameters and return values between a client and a service, both endpoints share all of the data contracts of the data to be transmitted.</span></span> <span data-ttu-id="0a299-106">Nejedná se však o případ v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="0a299-106">However, this is not the case in the following circumstances:</span></span>  
  
- <span data-ttu-id="0a299-107">Kontrakt odeslaných dat je odvozen od očekávaného kontraktu dat.</span><span class="sxs-lookup"><span data-stu-id="0a299-107">The sent data contract is derived from the expected data contract.</span></span> <span data-ttu-id="0a299-108">Další informace najdete v části o dědičnosti v [ekvivalentu kontraktu dat](data-contract-equivalence.md).</span><span class="sxs-lookup"><span data-stu-id="0a299-108">For more information, see the section about inheritance in [Data Contract Equivalence](data-contract-equivalence.md)).</span></span> <span data-ttu-id="0a299-109">V takovém případě přenosová data nemají stejný kontrakt dat, jak očekává přijímající koncový bod.</span><span class="sxs-lookup"><span data-stu-id="0a299-109">In that case, the transmitted data does not have the same data contract as expected by the receiving endpoint.</span></span>  
  
- <span data-ttu-id="0a299-110">Deklarovaný typ pro informace, které mají být přeneseny, je rozhraní, na rozdíl od třídy, struktury nebo výčtu.</span><span class="sxs-lookup"><span data-stu-id="0a299-110">The declared type for the information to be transmitted is an interface, as opposed to a class, structure, or enumeration.</span></span> <span data-ttu-id="0a299-111">Proto nemůže být znám předem, který typ, který implementuje rozhraní, je skutečně odeslán, a proto koncový bod nemůže určit předem kontrakt dat pro přenesená data.</span><span class="sxs-lookup"><span data-stu-id="0a299-111">Therefore, it cannot be known in advance which type that implements the interface is actually sent and therefore, the receiving endpoint cannot determine in advance the data contract for the transmitted data.</span></span>  
  
- <span data-ttu-id="0a299-112">Deklarovaný typ pro informace, které mají být přeneseny <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="0a299-112">The declared type for the information to be transmitted is <xref:System.Object>.</span></span> <span data-ttu-id="0a299-113">Vzhledem k tomu, že každý typ dědí z <xref:System.Object> a nelze jej znát předem, který typ je skutečně odeslán, nemůže koncový bod určit předem kontrakt dat pro přenesená data.</span><span class="sxs-lookup"><span data-stu-id="0a299-113">Because every type inherits from <xref:System.Object>, and it cannot be known in advance which type is actually sent, the receiving endpoint cannot determine in advance the data contract for the transmitted data.</span></span> <span data-ttu-id="0a299-114">Jedná se o zvláštní případ první položky: všechny kontrakty dat jsou odvozeny z výchozího, prázdný kontrakt dat, který je vygenerován pro <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="0a299-114">This is a special case of the first item: Every data contract derives from the default, a blank data contract that is generated for <xref:System.Object>.</span></span>  
  
- <span data-ttu-id="0a299-115">Některé typy, které zahrnují typy .NET Framework, mají členy, kteří jsou v jedné z předchozích tří kategorií.</span><span class="sxs-lookup"><span data-stu-id="0a299-115">Some types, which include .NET Framework types, have members that are in one of the preceding three categories.</span></span> <span data-ttu-id="0a299-116">Například <xref:System.Collections.Hashtable> používá <xref:System.Object> k uložení skutečných objektů v zatřiďovací tabulce.</span><span class="sxs-lookup"><span data-stu-id="0a299-116">For example, <xref:System.Collections.Hashtable> uses <xref:System.Object> to store the actual objects in the hash table.</span></span> <span data-ttu-id="0a299-117">Při serializaci těchto typů nemůže přijímající strana určit předem kontrakt dat pro tyto členy.</span><span class="sxs-lookup"><span data-stu-id="0a299-117">When serializing these types, the receiving side cannot determine in advance the data contract for these members.</span></span>  
  
## <a name="the-knowntypeattribute-class"></a><span data-ttu-id="0a299-118">Třída KnownTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="0a299-118">The KnownTypeAttribute Class</span></span>  
 <span data-ttu-id="0a299-119">Když data dorazí do přijímajícího koncového bodu, pokusí se modul runtime služby WCF deserializovat data do instance typu modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="0a299-119">When data arrives at a receiving endpoint, the WCF runtime attempts to deserialize the data into an instance of a common language runtime (CLR) type.</span></span> <span data-ttu-id="0a299-120">Typ, který je vytvořen pro deserializaci, je vybrán nejprve kontrolou příchozí zprávy a určením kontraktu dat, na který obsah zprávy odpovídá.</span><span class="sxs-lookup"><span data-stu-id="0a299-120">The type that is instantiated for deserialization is chosen by first inspecting the incoming message to determine the data contract to which the contents of the message conform.</span></span> <span data-ttu-id="0a299-121">Modul deserializace se pak pokusí najít typ CLR, který implementuje kontrakt dat kompatibilní s obsahem zprávy.</span><span class="sxs-lookup"><span data-stu-id="0a299-121">The deserialization engine then attempts to find a CLR type that implements a data contract compatible with the message contents.</span></span> <span data-ttu-id="0a299-122">Sada typů kandidátů, které v průběhu tohoto procesu umožňuje modul deserializace, je označována jako sada "známých typů" pro deserializaci.</span><span class="sxs-lookup"><span data-stu-id="0a299-122">The set of candidate types that the deserialization engine allows for during this process is referred to as the deserializer's set of "known types."</span></span>  
  
 <span data-ttu-id="0a299-123">Jedním ze způsobů, jak nechat modul deserializace informovat o typu, je pomocí <xref:System.Runtime.Serialization.KnownTypeAttribute> .</span><span class="sxs-lookup"><span data-stu-id="0a299-123">One way to let the deserialization engine know about a type is by using the <xref:System.Runtime.Serialization.KnownTypeAttribute>.</span></span> <span data-ttu-id="0a299-124">Atribut nelze použít pro jednotlivé datové členy, pouze pro celé typy kontraktů dat.</span><span class="sxs-lookup"><span data-stu-id="0a299-124">The attribute cannot be applied to individual data members, only to whole data contract types.</span></span> <span data-ttu-id="0a299-125">Atribut se aplikuje na *vnější typ* , který může být třída nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="0a299-125">The attribute is applied to an *outer type* that can be a class or a structure.</span></span> <span data-ttu-id="0a299-126">Ve většině základních použití atributu Určuje použití atributu typ jako "známý typ".</span><span class="sxs-lookup"><span data-stu-id="0a299-126">In its most basic usage, applying the attribute specifies a type as a "known type."</span></span> <span data-ttu-id="0a299-127">To způsobí, že známý typ bude součástí sady známých typů pokaždé, když dojde k deserializaci objektu vnějšího typu nebo jakéhokoliv objektu, na který odkazuje jeho členové.</span><span class="sxs-lookup"><span data-stu-id="0a299-127">This causes the known type to be a part of the set of known types whenever an object of the outer type or any object referred to through its members is being deserialized.</span></span> <span data-ttu-id="0a299-128"><xref:System.Runtime.Serialization.KnownTypeAttribute>Na stejný typ lze použít více než jeden atribut.</span><span class="sxs-lookup"><span data-stu-id="0a299-128">More than one <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute can be applied to the same type.</span></span>  
  
## <a name="known-types-and-primitives"></a><span data-ttu-id="0a299-129">Známé typy a primitivní prvky</span><span class="sxs-lookup"><span data-stu-id="0a299-129">Known Types and Primitives</span></span>  
 <span data-ttu-id="0a299-130">Primitivní typy a také určité typy považované za primitivní (například <xref:System.DateTime> a <xref:System.Xml.XmlElement> ) jsou vždy "známé" a nikdy nemusí být přidány prostřednictvím tohoto mechanismu.</span><span class="sxs-lookup"><span data-stu-id="0a299-130">Primitive types, as well as certain types treated as primitives (for example, <xref:System.DateTime> and <xref:System.Xml.XmlElement>) are always "known" and never have to be added through this mechanism.</span></span> <span data-ttu-id="0a299-131">Pole primitivních typů je však nutné přidat explicitně.</span><span class="sxs-lookup"><span data-stu-id="0a299-131">However, arrays of primitive types have to be added explicitly.</span></span> <span data-ttu-id="0a299-132">Většina kolekcí se považuje za ekvivalent polí.</span><span class="sxs-lookup"><span data-stu-id="0a299-132">Most collections are considered equivalent to arrays.</span></span> <span data-ttu-id="0a299-133">(Neobecné kolekce se považují za ekvivalentní k polím z <xref:System.Object> ).</span><span class="sxs-lookup"><span data-stu-id="0a299-133">(Non-generic collections are considered equivalent to arrays of <xref:System.Object>).</span></span> <span data-ttu-id="0a299-134">Příklad použití primitiv primitivních, primitivních polí a primitivních kolekcí najdete v příkladu 4.</span><span class="sxs-lookup"><span data-stu-id="0a299-134">For an example of the using primitives, primitive arrays, and primitive collections, see Example 4.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0a299-135">Na rozdíl od jiných primitivních typů <xref:System.DateTimeOffset> Struktura není ve výchozím nastavení známým typem, proto musí být ručně přidána do seznamu známých typů.</span><span class="sxs-lookup"><span data-stu-id="0a299-135">Unlike other primitive types, the <xref:System.DateTimeOffset> structure is not a known type by default, so it must be manually added to the list of known types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="0a299-136">Příklady</span><span class="sxs-lookup"><span data-stu-id="0a299-136">Examples</span></span>  
 <span data-ttu-id="0a299-137">Následující příklady znázorňují <xref:System.Runtime.Serialization.KnownTypeAttribute> třídu, která se používá.</span><span class="sxs-lookup"><span data-stu-id="0a299-137">The following examples show the <xref:System.Runtime.Serialization.KnownTypeAttribute> class in use.</span></span>  
  
#### <a name="example-1"></a><span data-ttu-id="0a299-138">Příklad 1</span><span class="sxs-lookup"><span data-stu-id="0a299-138">Example 1</span></span>  
 <span data-ttu-id="0a299-139">Existují tři třídy se vztahem dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="0a299-139">There are three classes with an inheritance relationship.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#1)]
 [!code-vb[C_KnownTypeAttribute#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#1)]  
  
 <span data-ttu-id="0a299-140">Následující `CompanyLogo` třídu lze serializovat, ale nelze ji deserializovat, pokud `ShapeOfLogo` je člen nastaven na hodnotu `CircleType` nebo `TriangleType` objekt, protože modul deserializace nerozpoznává žádné typy s názvy kontraktů dat "Circle" nebo "trojúhelníkem".</span><span class="sxs-lookup"><span data-stu-id="0a299-140">The following `CompanyLogo` class can be serialized, but cannot be deserialized if the `ShapeOfLogo` member is set to either a `CircleType` or a `TriangleType` object, because the deserialization engine does not recognize any types with data contract names "Circle" or "Triangle."</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#2)]
 [!code-vb[C_KnownTypeAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#2)]  
  
 <span data-ttu-id="0a299-141">Správný způsob, jak napsat `CompanyLogo` typ, je uveden v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="0a299-141">The correct way to write the `CompanyLogo` type is shown in the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#3)]
 [!code-vb[C_KnownTypeAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#3)]  
  
 <span data-ttu-id="0a299-142">Pokaždé, když `CompanyLogo2` je deserializován vnější typ, stroj deserializace ví o `CircleType` a `TriangleType` a, a proto je schopný najít vyhovující typy pro kontrakty dat "Circle" a "trojúhelník".</span><span class="sxs-lookup"><span data-stu-id="0a299-142">Whenever the outer type `CompanyLogo2` is being deserialized, the deserialization engine knows about `CircleType` and `TriangleType` and, therefore, is able to find matching types for the "Circle" and "Triangle" data contracts.</span></span>  
  
#### <a name="example-2"></a><span data-ttu-id="0a299-143">Příklad 2</span><span class="sxs-lookup"><span data-stu-id="0a299-143">Example 2</span></span>  
 <span data-ttu-id="0a299-144">V následujícím příkladu, i když obojí `CustomerTypeA` a `CustomerTypeB` má `Customer` kontrakt dat, instance `CustomerTypeB` je vytvořena při každém `PurchaseOrder` deserializaci, protože `CustomerTypeB` je znám pouze modulu deserializace.</span><span class="sxs-lookup"><span data-stu-id="0a299-144">In the following example, even though both `CustomerTypeA` and `CustomerTypeB` have the `Customer` data contract, an instance of `CustomerTypeB` is created whenever a `PurchaseOrder` is deserialized, because only `CustomerTypeB` is known to the deserialization engine.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#4)]
 [!code-vb[C_KnownTypeAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#4)]  
  
#### <a name="example-3"></a><span data-ttu-id="0a299-145">Příklad 3</span><span class="sxs-lookup"><span data-stu-id="0a299-145">Example 3</span></span>  
 <span data-ttu-id="0a299-146">V následujícím příkladu <xref:System.Collections.Hashtable> ukládá obsah interně jako <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="0a299-146">In the following example, a <xref:System.Collections.Hashtable> stores its contents internally as <xref:System.Object>.</span></span> <span data-ttu-id="0a299-147">Pro úspěšné deserializaci zatřiďovací tabulky musí modul deserializace znát sadu možných typů, které mohou nastat.</span><span class="sxs-lookup"><span data-stu-id="0a299-147">To successfully deserialize a hash table, the deserialization engine must know the set of possible types that can occur there.</span></span> <span data-ttu-id="0a299-148">V tomto případě víme, že pouze `Book` `Magazine` objekty a jsou uloženy v `Catalog` , takže jsou přidány pomocí <xref:System.Runtime.Serialization.KnownTypeAttribute> atributu.</span><span class="sxs-lookup"><span data-stu-id="0a299-148">In this case, we know in advance that only `Book` and `Magazine` objects are stored in the `Catalog`, so those are added using the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#5)]
 [!code-vb[C_KnownTypeAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#5)]  
  
#### <a name="example-4"></a><span data-ttu-id="0a299-149">Příklad 4</span><span class="sxs-lookup"><span data-stu-id="0a299-149">Example 4</span></span>  
 <span data-ttu-id="0a299-150">V následujícím příkladu kontrakt dat uchovává číslo a operaci, která se má provést na daném čísle.</span><span class="sxs-lookup"><span data-stu-id="0a299-150">In the following example, a data contract stores a number and an operation to perform on the number.</span></span> <span data-ttu-id="0a299-151">`Numbers`Datový člen může být celé číslo, pole celých čísel nebo <xref:System.Collections.Generic.List%601> , které obsahuje celá čísla.</span><span class="sxs-lookup"><span data-stu-id="0a299-151">The `Numbers` data member can be an integer, an array of integers, or a <xref:System.Collections.Generic.List%601> that contains integers.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="0a299-152">To bude fungovat jenom na straně klienta, pokud SVCUTIL. K vygenerování proxy serveru WCF se používá EXE.</span><span class="sxs-lookup"><span data-stu-id="0a299-152">This will only work on the client side if SVCUTIL.EXE is used to generate a WCF proxy.</span></span> <span data-ttu-id="0a299-153">Svcutil. EXE načítá metadata ze služby, včetně všech známých typů.</span><span class="sxs-lookup"><span data-stu-id="0a299-153">SVCUTIL.EXE retrieves metadata from the service including any known types.</span></span> <span data-ttu-id="0a299-154">Bez těchto informací klient nebude moci deserializovat typy.</span><span class="sxs-lookup"><span data-stu-id="0a299-154">Without this information a client will not be able to deserialize the types.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#6)]
 [!code-vb[C_KnownTypeAttribute#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#6)]  
  
 <span data-ttu-id="0a299-155">Toto je kód aplikace.</span><span class="sxs-lookup"><span data-stu-id="0a299-155">This is the application code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#7)]
 [!code-vb[C_KnownTypeAttribute#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#7)]  
  
## <a name="known-types-inheritance-and-interfaces"></a><span data-ttu-id="0a299-156">Známé typy, dědičnost a rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a299-156">Known Types, Inheritance, and Interfaces</span></span>  
 <span data-ttu-id="0a299-157">Pokud je známý typ přidružen k určitému typu pomocí `KnownTypeAttribute` atributu, je známý typ také přidružen ke všem odvozeným typům tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="0a299-157">When a known type is associated with a particular type using the `KnownTypeAttribute` attribute, the known type is also associated with all of the derived types of that type.</span></span> <span data-ttu-id="0a299-158">Podívejte se například na následující kód.</span><span class="sxs-lookup"><span data-stu-id="0a299-158">For example, see the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#8)]
 [!code-vb[C_KnownTypeAttribute#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#8)]  
  
 <span data-ttu-id="0a299-159">Třída nevyžaduje, `DoubleDrawing` `KnownTypeAttribute` aby atribut používal `Square` a `Circle` v `AdditionalShape` poli, protože základní třída ( `Drawing` ) již má tyto atributy použity.</span><span class="sxs-lookup"><span data-stu-id="0a299-159">The `DoubleDrawing` class does not require the `KnownTypeAttribute` attribute to use `Square` and `Circle` in the `AdditionalShape` field, because the base class (`Drawing`) already has these attributes applied.</span></span>  
  
 <span data-ttu-id="0a299-160">Známé typy lze přidružit pouze ke třídám a strukturám, nikoli rozhraním.</span><span class="sxs-lookup"><span data-stu-id="0a299-160">Known types can be associated only with classes and structures, not interfaces.</span></span>  
  
## <a name="known-types-using-open-generic-methods"></a><span data-ttu-id="0a299-161">Známé typy využívající otevřené obecné metody</span><span class="sxs-lookup"><span data-stu-id="0a299-161">Known Types Using Open Generic Methods</span></span>  
 <span data-ttu-id="0a299-162">Může být nutné přidat obecný typ jako známý typ.</span><span class="sxs-lookup"><span data-stu-id="0a299-162">It may be necessary to add a generic type as a known type.</span></span> <span data-ttu-id="0a299-163">Otevřený obecný typ však nelze předat jako parametr `KnownTypeAttribute` atributu.</span><span class="sxs-lookup"><span data-stu-id="0a299-163">However, an open generic type cannot be passed as a parameter to the `KnownTypeAttribute` attribute.</span></span>  
  
 <span data-ttu-id="0a299-164">Tento problém lze vyřešit pomocí alternativního mechanismu: napište metodu, která vrátí seznam typů, které se mají přidat do kolekce známých typů.</span><span class="sxs-lookup"><span data-stu-id="0a299-164">This problem can be solved by using an alternative mechanism: Write a method that returns a list of types to add to the known types collection.</span></span> <span data-ttu-id="0a299-165">Název metody je pak zadán jako řetězcový argument pro `KnownTypeAttribute` atribut z důvodu určitých omezení.</span><span class="sxs-lookup"><span data-stu-id="0a299-165">The name of the method is then specified as a string argument to the `KnownTypeAttribute` attribute due to some restrictions.</span></span>  
  
 <span data-ttu-id="0a299-166">Metoda musí existovat na typu, na který `KnownTypeAttribute` je atribut použit. musí být statická, nesmí přijímat žádné parametry a musí vracet objekt, který lze přiřadit k <xref:System.Collections.IEnumerable> <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="0a299-166">The method must exist on the type to which the `KnownTypeAttribute` attribute is applied, must be static, must accept no parameters, and must return an object that can be assigned to <xref:System.Collections.IEnumerable> of <xref:System.Type>.</span></span>  
  
 <span data-ttu-id="0a299-167">Nemůžete kombinovat `KnownTypeAttribute` atribut s názvem metody a `KnownTypeAttribute` atributy se skutečnými typy na stejném typu.</span><span class="sxs-lookup"><span data-stu-id="0a299-167">You cannot combine the `KnownTypeAttribute` attribute with a method name and `KnownTypeAttribute` attributes with actual types on the same type.</span></span> <span data-ttu-id="0a299-168">Kromě toho nemůžete použít více než jeden `KnownTypeAttribute` s názvem metody na stejný typ.</span><span class="sxs-lookup"><span data-stu-id="0a299-168">Furthermore, you cannot apply more than one `KnownTypeAttribute` with a method name to the same type.</span></span>  
  
 <span data-ttu-id="0a299-169">Podívejte se na následující třídu.</span><span class="sxs-lookup"><span data-stu-id="0a299-169">See the following class.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#9)]
 [!code-vb[C_KnownTypeAttribute#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#9)]  
  
 <span data-ttu-id="0a299-170">`theDrawing`Pole obsahuje instance obecné třídy `ColorDrawing` a obecné třídy `BlackAndWhiteDrawing` , z nichž obě dědí z obecné třídy `Drawing` .</span><span class="sxs-lookup"><span data-stu-id="0a299-170">The `theDrawing` field contains instances of a generic class `ColorDrawing` and a generic class `BlackAndWhiteDrawing`, both of which inherit from a generic class `Drawing`.</span></span> <span data-ttu-id="0a299-171">V normálním případě musí být oba přidány ke známým typům, ale následující nejsou platnou syntaxí pro atributy.</span><span class="sxs-lookup"><span data-stu-id="0a299-171">Normally, both must be added to known types, but the following is not valid syntax for attributes.</span></span>  
  
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
  
 <span data-ttu-id="0a299-172">Proto je nutné vytvořit metodu pro vrácení těchto typů.</span><span class="sxs-lookup"><span data-stu-id="0a299-172">Thus, a method must be created to return these types.</span></span> <span data-ttu-id="0a299-173">Správný způsob, jak tento typ napsat, je pak zobrazen v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="0a299-173">The correct way to write this type, then, is shown in the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#10)]
 [!code-vb[C_KnownTypeAttribute#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#10)]  
  
## <a name="additional-ways-to-add-known-types"></a><span data-ttu-id="0a299-174">Další způsoby, jak přidat známé typy</span><span class="sxs-lookup"><span data-stu-id="0a299-174">Additional Ways to Add Known Types</span></span>  
 <span data-ttu-id="0a299-175">Kromě toho je možné přidat známé typy prostřednictvím konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="0a299-175">Additionally, known types can be added through a configuration file.</span></span> <span data-ttu-id="0a299-176">To je užitečné v případě, že neřídíte typ, který vyžaduje známé typy pro správnou deserializaci, například při použití knihoven typů třetích stran s Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="0a299-176">This is useful when you do not control the type that requires known types for proper deserialization, such as when using third-party type libraries with Windows Communication Foundation (WCF).</span></span>  
  
 <span data-ttu-id="0a299-177">Následující konfigurační soubor ukazuje, jak zadat známý typ v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="0a299-177">The following configuration file shows how to specify a known type in a configuration file.</span></span>  
  
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
  
 <span data-ttu-id="0a299-178">V předchozím konfiguračním souboru je deklarovaný typ kontraktu dat, `MyCompany.Library.Shape` který má být `MyCompany.Library.Circle` označován jako známý typ.</span><span class="sxs-lookup"><span data-stu-id="0a299-178">In the preceding configuration file a data contract type called `MyCompany.Library.Shape` is declared to have `MyCompany.Library.Circle` as a known type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a299-179">Viz také</span><span class="sxs-lookup"><span data-stu-id="0a299-179">See also</span></span>

- <xref:System.Runtime.Serialization.KnownTypeAttribute>
- <xref:System.Collections.Hashtable>
- <xref:System.Object>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A>
- [<span data-ttu-id="0a299-180">Známé typy</span><span class="sxs-lookup"><span data-stu-id="0a299-180">Known Types</span></span>](../samples/known-types.md)
- [<span data-ttu-id="0a299-181">Ekvivalence kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="0a299-181">Data Contract Equivalence</span></span>](data-contract-equivalence.md)
- [<span data-ttu-id="0a299-182">Navrhování kontraktů služby</span><span class="sxs-lookup"><span data-stu-id="0a299-182">Designing Service Contracts</span></span>](../designing-service-contracts.md)
