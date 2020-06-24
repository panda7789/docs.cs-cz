---
title: Známé typy kontraktů dat
description: Zjistěte, jak model kontraktu dat používá třídu KnownTypeAttribute k určení typů, které mají být zahrnuty během deserializace v rámci služby WCF.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], known types
- KnownTypeAttribute [WCF]
- KnownTypes [WCF]
ms.assetid: 1a0baea1-27b7-470d-9136-5bbad86c4337
ms.openlocfilehash: 52b0caaaac976893dcf5ef5c228ccc4f53bdbe9e
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247478"
---
# <a name="data-contract-known-types"></a><span data-ttu-id="feff0-103">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="feff0-103">Data Contract Known Types</span></span>
<span data-ttu-id="feff0-104"><xref:System.Runtime.Serialization.KnownTypeAttribute>Třída umožňuje zadat předem typy, které by měly být zahrnuty za účelem posouzení během deserializace.</span><span class="sxs-lookup"><span data-stu-id="feff0-104">The <xref:System.Runtime.Serialization.KnownTypeAttribute> class allows you to specify, in advance, the types that should be included for consideration during deserialization.</span></span> <span data-ttu-id="feff0-105">Pracovní příklad naleznete v příkladu [známých typů](../samples/known-types.md) .</span><span class="sxs-lookup"><span data-stu-id="feff0-105">For a working example, see the [Known Types](../samples/known-types.md) example.</span></span>  
  
 <span data-ttu-id="feff0-106">Obvykle při předávání parametrů a vrácení hodnot mezi klientem a službou se oba koncové body sdílí se všemi kontrakty dat dat, která se mají přenést.</span><span class="sxs-lookup"><span data-stu-id="feff0-106">Normally, when passing parameters and return values between a client and a service, both endpoints share all of the data contracts of the data to be transmitted.</span></span> <span data-ttu-id="feff0-107">Nejedná se však o případ v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="feff0-107">However, this is not the case in the following circumstances:</span></span>  
  
- <span data-ttu-id="feff0-108">Kontrakt odeslaných dat je odvozen od očekávaného kontraktu dat.</span><span class="sxs-lookup"><span data-stu-id="feff0-108">The sent data contract is derived from the expected data contract.</span></span> <span data-ttu-id="feff0-109">Další informace najdete v části o dědičnosti v [ekvivalentu kontraktu dat](data-contract-equivalence.md).</span><span class="sxs-lookup"><span data-stu-id="feff0-109">For more information, see the section about inheritance in [Data Contract Equivalence](data-contract-equivalence.md)).</span></span> <span data-ttu-id="feff0-110">V takovém případě přenosová data nemají stejný kontrakt dat, jak očekává přijímající koncový bod.</span><span class="sxs-lookup"><span data-stu-id="feff0-110">In that case, the transmitted data does not have the same data contract as expected by the receiving endpoint.</span></span>  
  
- <span data-ttu-id="feff0-111">Deklarovaný typ pro informace, které mají být přeneseny, je rozhraní, na rozdíl od třídy, struktury nebo výčtu.</span><span class="sxs-lookup"><span data-stu-id="feff0-111">The declared type for the information to be transmitted is an interface, as opposed to a class, structure, or enumeration.</span></span> <span data-ttu-id="feff0-112">Proto nemůže být znám předem, který typ, který implementuje rozhraní, je skutečně odeslán, a proto koncový bod nemůže určit předem kontrakt dat pro přenesená data.</span><span class="sxs-lookup"><span data-stu-id="feff0-112">Therefore, it cannot be known in advance which type that implements the interface is actually sent and therefore, the receiving endpoint cannot determine in advance the data contract for the transmitted data.</span></span>  
  
- <span data-ttu-id="feff0-113">Deklarovaný typ pro informace, které mají být přeneseny <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="feff0-113">The declared type for the information to be transmitted is <xref:System.Object>.</span></span> <span data-ttu-id="feff0-114">Vzhledem k tomu, že každý typ dědí z <xref:System.Object> a nelze jej znát předem, který typ je skutečně odeslán, nemůže koncový bod určit předem kontrakt dat pro přenesená data.</span><span class="sxs-lookup"><span data-stu-id="feff0-114">Because every type inherits from <xref:System.Object>, and it cannot be known in advance which type is actually sent, the receiving endpoint cannot determine in advance the data contract for the transmitted data.</span></span> <span data-ttu-id="feff0-115">Jedná se o zvláštní případ první položky: všechny kontrakty dat jsou odvozeny z výchozího, prázdný kontrakt dat, který je vygenerován pro <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="feff0-115">This is a special case of the first item: Every data contract derives from the default, a blank data contract that is generated for <xref:System.Object>.</span></span>  
  
- <span data-ttu-id="feff0-116">Některé typy, které zahrnují typy .NET Framework, mají členy, kteří jsou v jedné z předchozích tří kategorií.</span><span class="sxs-lookup"><span data-stu-id="feff0-116">Some types, which include .NET Framework types, have members that are in one of the preceding three categories.</span></span> <span data-ttu-id="feff0-117">Například <xref:System.Collections.Hashtable> používá <xref:System.Object> k uložení skutečných objektů v zatřiďovací tabulce.</span><span class="sxs-lookup"><span data-stu-id="feff0-117">For example, <xref:System.Collections.Hashtable> uses <xref:System.Object> to store the actual objects in the hash table.</span></span> <span data-ttu-id="feff0-118">Při serializaci těchto typů nemůže přijímající strana určit předem kontrakt dat pro tyto členy.</span><span class="sxs-lookup"><span data-stu-id="feff0-118">When serializing these types, the receiving side cannot determine in advance the data contract for these members.</span></span>  
  
## <a name="the-knowntypeattribute-class"></a><span data-ttu-id="feff0-119">Třída KnownTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="feff0-119">The KnownTypeAttribute Class</span></span>  
 <span data-ttu-id="feff0-120">Když data dorazí do přijímajícího koncového bodu, pokusí se modul runtime služby WCF deserializovat data do instance typu modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="feff0-120">When data arrives at a receiving endpoint, the WCF runtime attempts to deserialize the data into an instance of a common language runtime (CLR) type.</span></span> <span data-ttu-id="feff0-121">Typ, který je vytvořen pro deserializaci, je vybrán nejprve kontrolou příchozí zprávy a určením kontraktu dat, na který obsah zprávy odpovídá.</span><span class="sxs-lookup"><span data-stu-id="feff0-121">The type that is instantiated for deserialization is chosen by first inspecting the incoming message to determine the data contract to which the contents of the message conform.</span></span> <span data-ttu-id="feff0-122">Modul deserializace se pak pokusí najít typ CLR, který implementuje kontrakt dat kompatibilní s obsahem zprávy.</span><span class="sxs-lookup"><span data-stu-id="feff0-122">The deserialization engine then attempts to find a CLR type that implements a data contract compatible with the message contents.</span></span> <span data-ttu-id="feff0-123">Sada typů kandidátů, které v průběhu tohoto procesu umožňuje modul deserializace, je označována jako sada "známých typů" pro deserializaci.</span><span class="sxs-lookup"><span data-stu-id="feff0-123">The set of candidate types that the deserialization engine allows for during this process is referred to as the deserializer's set of "known types."</span></span>  
  
 <span data-ttu-id="feff0-124">Jedním ze způsobů, jak nechat modul deserializace informovat o typu, je pomocí <xref:System.Runtime.Serialization.KnownTypeAttribute> .</span><span class="sxs-lookup"><span data-stu-id="feff0-124">One way to let the deserialization engine know about a type is by using the <xref:System.Runtime.Serialization.KnownTypeAttribute>.</span></span> <span data-ttu-id="feff0-125">Atribut nelze použít pro jednotlivé datové členy, pouze pro celé typy kontraktů dat.</span><span class="sxs-lookup"><span data-stu-id="feff0-125">The attribute cannot be applied to individual data members, only to whole data contract types.</span></span> <span data-ttu-id="feff0-126">Atribut se aplikuje na *vnější typ* , který může být třída nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="feff0-126">The attribute is applied to an *outer type* that can be a class or a structure.</span></span> <span data-ttu-id="feff0-127">Ve většině základních použití atributu Určuje použití atributu typ jako "známý typ".</span><span class="sxs-lookup"><span data-stu-id="feff0-127">In its most basic usage, applying the attribute specifies a type as a "known type."</span></span> <span data-ttu-id="feff0-128">To způsobí, že známý typ bude součástí sady známých typů pokaždé, když dojde k deserializaci objektu vnějšího typu nebo jakéhokoliv objektu, na který odkazuje jeho členové.</span><span class="sxs-lookup"><span data-stu-id="feff0-128">This causes the known type to be a part of the set of known types whenever an object of the outer type or any object referred to through its members is being deserialized.</span></span> <span data-ttu-id="feff0-129"><xref:System.Runtime.Serialization.KnownTypeAttribute>Na stejný typ lze použít více než jeden atribut.</span><span class="sxs-lookup"><span data-stu-id="feff0-129">More than one <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute can be applied to the same type.</span></span>  
  
## <a name="known-types-and-primitives"></a><span data-ttu-id="feff0-130">Známé typy a primitivní prvky</span><span class="sxs-lookup"><span data-stu-id="feff0-130">Known Types and Primitives</span></span>  
 <span data-ttu-id="feff0-131">Primitivní typy a také určité typy považované za primitivní (například <xref:System.DateTime> a <xref:System.Xml.XmlElement> ) jsou vždy "známé" a nikdy nemusí být přidány prostřednictvím tohoto mechanismu.</span><span class="sxs-lookup"><span data-stu-id="feff0-131">Primitive types, as well as certain types treated as primitives (for example, <xref:System.DateTime> and <xref:System.Xml.XmlElement>) are always "known" and never have to be added through this mechanism.</span></span> <span data-ttu-id="feff0-132">Pole primitivních typů je však nutné přidat explicitně.</span><span class="sxs-lookup"><span data-stu-id="feff0-132">However, arrays of primitive types have to be added explicitly.</span></span> <span data-ttu-id="feff0-133">Většina kolekcí se považuje za ekvivalent polí.</span><span class="sxs-lookup"><span data-stu-id="feff0-133">Most collections are considered equivalent to arrays.</span></span> <span data-ttu-id="feff0-134">(Neobecné kolekce se považují za ekvivalentní k polím z <xref:System.Object> ).</span><span class="sxs-lookup"><span data-stu-id="feff0-134">(Non-generic collections are considered equivalent to arrays of <xref:System.Object>).</span></span> <span data-ttu-id="feff0-135">Příklad použití primitiv primitivních, primitivních polí a primitivních kolekcí najdete v příkladu 4.</span><span class="sxs-lookup"><span data-stu-id="feff0-135">For an example of the using primitives, primitive arrays, and primitive collections, see Example 4.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="feff0-136">Na rozdíl od jiných primitivních typů <xref:System.DateTimeOffset> Struktura není ve výchozím nastavení známým typem, proto musí být ručně přidána do seznamu známých typů.</span><span class="sxs-lookup"><span data-stu-id="feff0-136">Unlike other primitive types, the <xref:System.DateTimeOffset> structure is not a known type by default, so it must be manually added to the list of known types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="feff0-137">Příklady</span><span class="sxs-lookup"><span data-stu-id="feff0-137">Examples</span></span>  
 <span data-ttu-id="feff0-138">Následující příklady znázorňují <xref:System.Runtime.Serialization.KnownTypeAttribute> třídu, která se používá.</span><span class="sxs-lookup"><span data-stu-id="feff0-138">The following examples show the <xref:System.Runtime.Serialization.KnownTypeAttribute> class in use.</span></span>  
  
#### <a name="example-1"></a><span data-ttu-id="feff0-139">Příklad 1</span><span class="sxs-lookup"><span data-stu-id="feff0-139">Example 1</span></span>  
 <span data-ttu-id="feff0-140">Existují tři třídy se vztahem dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="feff0-140">There are three classes with an inheritance relationship.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#1)]
 [!code-vb[C_KnownTypeAttribute#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#1)]  
  
 <span data-ttu-id="feff0-141">Následující `CompanyLogo` třídu lze serializovat, ale nelze ji deserializovat, pokud `ShapeOfLogo` je člen nastaven na hodnotu `CircleType` nebo `TriangleType` objekt, protože modul deserializace nerozpoznává žádné typy s názvy kontraktů dat "Circle" nebo "trojúhelníkem".</span><span class="sxs-lookup"><span data-stu-id="feff0-141">The following `CompanyLogo` class can be serialized, but cannot be deserialized if the `ShapeOfLogo` member is set to either a `CircleType` or a `TriangleType` object, because the deserialization engine does not recognize any types with data contract names "Circle" or "Triangle."</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#2)]
 [!code-vb[C_KnownTypeAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#2)]  
  
 <span data-ttu-id="feff0-142">Správný způsob, jak napsat `CompanyLogo` typ, je uveden v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="feff0-142">The correct way to write the `CompanyLogo` type is shown in the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#3)]
 [!code-vb[C_KnownTypeAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#3)]  
  
 <span data-ttu-id="feff0-143">Pokaždé, když `CompanyLogo2` je deserializován vnější typ, stroj deserializace ví o `CircleType` a `TriangleType` a, a proto je schopný najít vyhovující typy pro kontrakty dat "Circle" a "trojúhelník".</span><span class="sxs-lookup"><span data-stu-id="feff0-143">Whenever the outer type `CompanyLogo2` is being deserialized, the deserialization engine knows about `CircleType` and `TriangleType` and, therefore, is able to find matching types for the "Circle" and "Triangle" data contracts.</span></span>  
  
#### <a name="example-2"></a><span data-ttu-id="feff0-144">Příklad 2</span><span class="sxs-lookup"><span data-stu-id="feff0-144">Example 2</span></span>  
 <span data-ttu-id="feff0-145">V následujícím příkladu, i když obojí `CustomerTypeA` a `CustomerTypeB` má `Customer` kontrakt dat, instance `CustomerTypeB` je vytvořena při každém `PurchaseOrder` deserializaci, protože `CustomerTypeB` je znám pouze modulu deserializace.</span><span class="sxs-lookup"><span data-stu-id="feff0-145">In the following example, even though both `CustomerTypeA` and `CustomerTypeB` have the `Customer` data contract, an instance of `CustomerTypeB` is created whenever a `PurchaseOrder` is deserialized, because only `CustomerTypeB` is known to the deserialization engine.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#4)]
 [!code-vb[C_KnownTypeAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#4)]  
  
#### <a name="example-3"></a><span data-ttu-id="feff0-146">Příklad 3</span><span class="sxs-lookup"><span data-stu-id="feff0-146">Example 3</span></span>  
 <span data-ttu-id="feff0-147">V následujícím příkladu <xref:System.Collections.Hashtable> ukládá obsah interně jako <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="feff0-147">In the following example, a <xref:System.Collections.Hashtable> stores its contents internally as <xref:System.Object>.</span></span> <span data-ttu-id="feff0-148">Pro úspěšné deserializaci zatřiďovací tabulky musí modul deserializace znát sadu možných typů, které mohou nastat.</span><span class="sxs-lookup"><span data-stu-id="feff0-148">To successfully deserialize a hash table, the deserialization engine must know the set of possible types that can occur there.</span></span> <span data-ttu-id="feff0-149">V tomto případě víme, že pouze `Book` `Magazine` objekty a jsou uloženy v `Catalog` , takže jsou přidány pomocí <xref:System.Runtime.Serialization.KnownTypeAttribute> atributu.</span><span class="sxs-lookup"><span data-stu-id="feff0-149">In this case, we know in advance that only `Book` and `Magazine` objects are stored in the `Catalog`, so those are added using the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#5)]
 [!code-vb[C_KnownTypeAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#5)]  
  
#### <a name="example-4"></a><span data-ttu-id="feff0-150">Příklad 4</span><span class="sxs-lookup"><span data-stu-id="feff0-150">Example 4</span></span>  
 <span data-ttu-id="feff0-151">V následujícím příkladu kontrakt dat uchovává číslo a operaci, která se má provést na daném čísle.</span><span class="sxs-lookup"><span data-stu-id="feff0-151">In the following example, a data contract stores a number and an operation to perform on the number.</span></span> <span data-ttu-id="feff0-152">`Numbers`Datový člen může být celé číslo, pole celých čísel nebo <xref:System.Collections.Generic.List%601> , které obsahuje celá čísla.</span><span class="sxs-lookup"><span data-stu-id="feff0-152">The `Numbers` data member can be an integer, an array of integers, or a <xref:System.Collections.Generic.List%601> that contains integers.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="feff0-153">To bude fungovat jenom na straně klienta, pokud se k vygenerování proxy serveru WCF používá SVCUTIL.EXE.</span><span class="sxs-lookup"><span data-stu-id="feff0-153">This will only work on the client side if SVCUTIL.EXE is used to generate a WCF proxy.</span></span> <span data-ttu-id="feff0-154">SVCUTIL.EXE načítá metadata ze služby, včetně všech známých typů.</span><span class="sxs-lookup"><span data-stu-id="feff0-154">SVCUTIL.EXE retrieves metadata from the service including any known types.</span></span> <span data-ttu-id="feff0-155">Bez těchto informací klient nebude moci deserializovat typy.</span><span class="sxs-lookup"><span data-stu-id="feff0-155">Without this information a client will not be able to deserialize the types.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#6)]
 [!code-vb[C_KnownTypeAttribute#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#6)]  
  
 <span data-ttu-id="feff0-156">Toto je kód aplikace.</span><span class="sxs-lookup"><span data-stu-id="feff0-156">This is the application code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#7)]
 [!code-vb[C_KnownTypeAttribute#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#7)]  
  
## <a name="known-types-inheritance-and-interfaces"></a><span data-ttu-id="feff0-157">Známé typy, dědičnost a rozhraní</span><span class="sxs-lookup"><span data-stu-id="feff0-157">Known Types, Inheritance, and Interfaces</span></span>  
 <span data-ttu-id="feff0-158">Pokud je známý typ přidružen k určitému typu pomocí `KnownTypeAttribute` atributu, je známý typ také přidružen ke všem odvozeným typům tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="feff0-158">When a known type is associated with a particular type using the `KnownTypeAttribute` attribute, the known type is also associated with all of the derived types of that type.</span></span> <span data-ttu-id="feff0-159">Podívejte se například na následující kód.</span><span class="sxs-lookup"><span data-stu-id="feff0-159">For example, see the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#8)]
 [!code-vb[C_KnownTypeAttribute#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#8)]  
  
 <span data-ttu-id="feff0-160">Třída nevyžaduje, `DoubleDrawing` `KnownTypeAttribute` aby atribut používal `Square` a `Circle` v `AdditionalShape` poli, protože základní třída ( `Drawing` ) již má tyto atributy použity.</span><span class="sxs-lookup"><span data-stu-id="feff0-160">The `DoubleDrawing` class does not require the `KnownTypeAttribute` attribute to use `Square` and `Circle` in the `AdditionalShape` field, because the base class (`Drawing`) already has these attributes applied.</span></span>  
  
 <span data-ttu-id="feff0-161">Známé typy lze přidružit pouze ke třídám a strukturám, nikoli rozhraním.</span><span class="sxs-lookup"><span data-stu-id="feff0-161">Known types can be associated only with classes and structures, not interfaces.</span></span>  
  
## <a name="known-types-using-open-generic-methods"></a><span data-ttu-id="feff0-162">Známé typy využívající otevřené obecné metody</span><span class="sxs-lookup"><span data-stu-id="feff0-162">Known Types Using Open Generic Methods</span></span>  
 <span data-ttu-id="feff0-163">Může být nutné přidat obecný typ jako známý typ.</span><span class="sxs-lookup"><span data-stu-id="feff0-163">It may be necessary to add a generic type as a known type.</span></span> <span data-ttu-id="feff0-164">Otevřený obecný typ však nelze předat jako parametr `KnownTypeAttribute` atributu.</span><span class="sxs-lookup"><span data-stu-id="feff0-164">However, an open generic type cannot be passed as a parameter to the `KnownTypeAttribute` attribute.</span></span>  
  
 <span data-ttu-id="feff0-165">Tento problém lze vyřešit pomocí alternativního mechanismu: napište metodu, která vrátí seznam typů, které se mají přidat do kolekce známých typů.</span><span class="sxs-lookup"><span data-stu-id="feff0-165">This problem can be solved by using an alternative mechanism: Write a method that returns a list of types to add to the known types collection.</span></span> <span data-ttu-id="feff0-166">Název metody je pak zadán jako řetězcový argument pro `KnownTypeAttribute` atribut z důvodu určitých omezení.</span><span class="sxs-lookup"><span data-stu-id="feff0-166">The name of the method is then specified as a string argument to the `KnownTypeAttribute` attribute due to some restrictions.</span></span>  
  
 <span data-ttu-id="feff0-167">Metoda musí existovat na typu, na který `KnownTypeAttribute` je atribut použit. musí být statická, nesmí přijímat žádné parametry a musí vracet objekt, který lze přiřadit k <xref:System.Collections.IEnumerable> <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="feff0-167">The method must exist on the type to which the `KnownTypeAttribute` attribute is applied, must be static, must accept no parameters, and must return an object that can be assigned to <xref:System.Collections.IEnumerable> of <xref:System.Type>.</span></span>  
  
 <span data-ttu-id="feff0-168">Nemůžete kombinovat `KnownTypeAttribute` atribut s názvem metody a `KnownTypeAttribute` atributy se skutečnými typy na stejném typu.</span><span class="sxs-lookup"><span data-stu-id="feff0-168">You cannot combine the `KnownTypeAttribute` attribute with a method name and `KnownTypeAttribute` attributes with actual types on the same type.</span></span> <span data-ttu-id="feff0-169">Kromě toho nemůžete použít více než jeden `KnownTypeAttribute` s názvem metody na stejný typ.</span><span class="sxs-lookup"><span data-stu-id="feff0-169">Furthermore, you cannot apply more than one `KnownTypeAttribute` with a method name to the same type.</span></span>  
  
 <span data-ttu-id="feff0-170">Podívejte se na následující třídu.</span><span class="sxs-lookup"><span data-stu-id="feff0-170">See the following class.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#9)]
 [!code-vb[C_KnownTypeAttribute#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#9)]  
  
 <span data-ttu-id="feff0-171">`theDrawing`Pole obsahuje instance obecné třídy `ColorDrawing` a obecné třídy `BlackAndWhiteDrawing` , z nichž obě dědí z obecné třídy `Drawing` .</span><span class="sxs-lookup"><span data-stu-id="feff0-171">The `theDrawing` field contains instances of a generic class `ColorDrawing` and a generic class `BlackAndWhiteDrawing`, both of which inherit from a generic class `Drawing`.</span></span> <span data-ttu-id="feff0-172">V normálním případě musí být oba přidány ke známým typům, ale následující nejsou platnou syntaxí pro atributy.</span><span class="sxs-lookup"><span data-stu-id="feff0-172">Normally, both must be added to known types, but the following is not valid syntax for attributes.</span></span>  
  
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
  
 <span data-ttu-id="feff0-173">Proto je nutné vytvořit metodu pro vrácení těchto typů.</span><span class="sxs-lookup"><span data-stu-id="feff0-173">Thus, a method must be created to return these types.</span></span> <span data-ttu-id="feff0-174">Správný způsob, jak tento typ napsat, je pak zobrazen v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="feff0-174">The correct way to write this type, then, is shown in the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#10)]
 [!code-vb[C_KnownTypeAttribute#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#10)]  
  
## <a name="additional-ways-to-add-known-types"></a><span data-ttu-id="feff0-175">Další způsoby, jak přidat známé typy</span><span class="sxs-lookup"><span data-stu-id="feff0-175">Additional Ways to Add Known Types</span></span>  
 <span data-ttu-id="feff0-176">Kromě toho je možné přidat známé typy prostřednictvím konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="feff0-176">Additionally, known types can be added through a configuration file.</span></span> <span data-ttu-id="feff0-177">To je užitečné v případě, že neřídíte typ, který vyžaduje známé typy pro správnou deserializaci, například při použití knihoven typů třetích stran s Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="feff0-177">This is useful when you do not control the type that requires known types for proper deserialization, such as when using third-party type libraries with Windows Communication Foundation (WCF).</span></span>  
  
 <span data-ttu-id="feff0-178">Následující konfigurační soubor ukazuje, jak zadat známý typ v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="feff0-178">The following configuration file shows how to specify a known type in a configuration file.</span></span>  
  
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
  
 <span data-ttu-id="feff0-179">V předchozím konfiguračním souboru je deklarovaný typ kontraktu dat, `MyCompany.Library.Shape` který má být `MyCompany.Library.Circle` označován jako známý typ.</span><span class="sxs-lookup"><span data-stu-id="feff0-179">In the preceding configuration file a data contract type called `MyCompany.Library.Shape` is declared to have `MyCompany.Library.Circle` as a known type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feff0-180">Viz také</span><span class="sxs-lookup"><span data-stu-id="feff0-180">See also</span></span>

- <xref:System.Runtime.Serialization.KnownTypeAttribute>
- <xref:System.Collections.Hashtable>
- <xref:System.Object>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A>
- [<span data-ttu-id="feff0-181">Známé typy</span><span class="sxs-lookup"><span data-stu-id="feff0-181">Known Types</span></span>](../samples/known-types.md)
- [<span data-ttu-id="feff0-182">Ekvivalence kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="feff0-182">Data Contract Equivalence</span></span>](data-contract-equivalence.md)
- [<span data-ttu-id="feff0-183">Navrhování kontraktů služby</span><span class="sxs-lookup"><span data-stu-id="feff0-183">Designing Service Contracts</span></span>](../designing-service-contracts.md)
