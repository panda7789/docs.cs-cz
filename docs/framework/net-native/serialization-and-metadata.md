---
title: Serializace a metadata
ms.date: 03/30/2017
ms.assetid: 619ecf1c-1ca5-4d66-8934-62fe7aad78c6
ms.openlocfilehash: cc9adf0e6627ef3190e74fea5d4f0f3afd581811
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389222"
---
# <a name="serialization-and-metadata"></a><span data-ttu-id="2c86c-102">Serializace a metadata</span><span class="sxs-lookup"><span data-stu-id="2c86c-102">Serialization and Metadata</span></span>

<span data-ttu-id="2c86c-103">Pokud vaše aplikace serializuje a reserializuje objekty, bude pravděpodobně nutné přidat položky do souboru direktiv runtime (.rd.xml), abyste zajistili, že potřebná metadata budou přítomna za běhu.</span><span class="sxs-lookup"><span data-stu-id="2c86c-103">If your app serializes and deserializes objects, you may need to add entries to your runtime directives (.rd.xml) file to ensure that the necessary metadata is present at run time.</span></span> <span data-ttu-id="2c86c-104">Existují dvě kategorie serializátorů a každá vyžaduje jiné zpracování v souboru direktiv runtime:</span><span class="sxs-lookup"><span data-stu-id="2c86c-104">There are two categories of serializers, and each requires different handling in your runtime directives file:</span></span>  
  
- <span data-ttu-id="2c86c-105">Serializátory třetích stran založené na reflexi.</span><span class="sxs-lookup"><span data-stu-id="2c86c-105">Reflection-based third-party serializers.</span></span> <span data-ttu-id="2c86c-106">Ty vyžadují změny souboru direktiv runtime a jsou popsány v další části.</span><span class="sxs-lookup"><span data-stu-id="2c86c-106">These require modifications to your runtime directives file, and are discussed in the next section.</span></span>  
  
- <span data-ttu-id="2c86c-107">Serializátory založené na odrazu nalezené v knihovně tříd rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2c86c-107">Non-reflection-based serializers found in the .NET Framework class library.</span></span> <span data-ttu-id="2c86c-108">Ty mohou vyžadovat změny souboru direktiv runtime a jsou popsány v části [Microsoft serializers.](#Microsoft)</span><span class="sxs-lookup"><span data-stu-id="2c86c-108">These may require modifications to your runtime directives file, and are discussed in the [Microsoft serializers](#Microsoft) section.</span></span>  
  
<a name="ThirdParty"></a>
## <a name="third-party-serializers"></a><span data-ttu-id="2c86c-109">Serializátory jiných výrobců</span><span class="sxs-lookup"><span data-stu-id="2c86c-109">Third-party serializers</span></span>

 <span data-ttu-id="2c86c-110">Třetí část serializátory, včetně Newtonsoft.JSON, jsou obvykle reflexe-založené.</span><span class="sxs-lookup"><span data-stu-id="2c86c-110">Third-part serializers, including Newtonsoft.JSON, typically are reflection-based.</span></span> <span data-ttu-id="2c86c-111">Vzhledem k tomu, binární velký objekt (BLOB) serializovaných dat, pole v datech jsou přiřazeny k konkrétní typ vyhledáním pole cílového typu podle názvu.</span><span class="sxs-lookup"><span data-stu-id="2c86c-111">Given a binary large object (BLOB) of serialized data, the fields in the data are assigned to a concrete type by looking up the fields of the target type by name.</span></span> <span data-ttu-id="2c86c-112">Použití těchto knihoven přinejmenším způsobí [výjimky MissingMetadataException](missingmetadataexception-class-net-native.md) pro každý <xref:System.Type> objekt, který se pokusíte `List<Type>` serializovat nebo rekonstruovat v kolekci.</span><span class="sxs-lookup"><span data-stu-id="2c86c-112">At a minimum, using these libraries causes [MissingMetadataException](missingmetadataexception-class-net-native.md) exceptions for each <xref:System.Type> object that you try to serialize or deserialize in a `List<Type>` collection.</span></span>  
  
 <span data-ttu-id="2c86c-113">Nejjednodušší způsob, jak řešit problémy způsobené chybějícími metadaty pro tyto serializátory, je shromáždit typy, `App.Models`které budou `Serialize` použity při serializaci v rámci jednoho oboru názvů (například ) a použít na něj direktivu metadat:</span><span class="sxs-lookup"><span data-stu-id="2c86c-113">The easiest way to address issues caused by missing metadata for these serializers is to collect types that will be used in serialization under a single namespace (such as `App.Models`) and apply a `Serialize` metadata directive to it:</span></span>  
  
```xml  
<Namespace Name="App.Models" Serialize="Required PublicAndInternal" />  
```  
  
 <span data-ttu-id="2c86c-114">Informace o syntaxi použité v příkladu naleznete v [ \<tématu Obor názvů> Element](namespace-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="2c86c-114">For information about the syntax used in the example, see [\<Namespace> Element](namespace-element-net-native.md).</span></span>  
  
<a name="Microsoft"></a>
## <a name="microsoft-serializers"></a><span data-ttu-id="2c86c-115">Serializátory společnosti Microsoft</span><span class="sxs-lookup"><span data-stu-id="2c86c-115">Microsoft serializers</span></span>

 <span data-ttu-id="2c86c-116">Přestože <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, <xref:System.Xml.Serialization.XmlSerializer> a třídy nespoléhají na reflexi, vyžadují kód, který má být generován na základě objektu, který má být serializován nebo deserializován.</span><span class="sxs-lookup"><span data-stu-id="2c86c-116">Although the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes do not rely on reflection, they do require code to be generated based on the object to be serialized or deserialized.</span></span> <span data-ttu-id="2c86c-117">Přetížené konstruktory pro každý serializátor obsahují <xref:System.Type> parametr, který určuje typ, který má být serializován nebo reserializován.</span><span class="sxs-lookup"><span data-stu-id="2c86c-117">The overloaded constructors for each serializer include a <xref:System.Type> parameter that specifies the type to be serialized or deserialized.</span></span> <span data-ttu-id="2c86c-118">Způsob zadání tohoto typu v kódu definuje akci, kterou je třeba provést, jak je popsáno v následujících dvou částech.</span><span class="sxs-lookup"><span data-stu-id="2c86c-118">How you specify that type in your code defines the action you must take, as discussed in the next two sections.</span></span>  
  
### <a name="typeof-used-in-the-constructor"></a><span data-ttu-id="2c86c-119">typ použitého v konstruktoru</span><span class="sxs-lookup"><span data-stu-id="2c86c-119">typeof used in the constructor</span></span>

 <span data-ttu-id="2c86c-120">Pokud voláte konstruktor těchto tříd serializace a zahrnout [c# typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) operátor ve volání metody, **není třeba provést žádnou další práci**.</span><span class="sxs-lookup"><span data-stu-id="2c86c-120">If you call a constructor of these serialization classes and include the C# [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) operator in the method call, **you do not have to do any additional work**.</span></span> <span data-ttu-id="2c86c-121">Například v každé z následujících volání konstruktoru `typeof` třídy serializace se klíčové slovo používá jako součást výrazu předaného konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="2c86c-121">For example, in each of the following calls to a serialization class constructor, the `typeof` keyword is used as part of the expression passed to the constructor.</span></span>  
  
 [!code-csharp[ProjectN#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#5)]  
  
 <span data-ttu-id="2c86c-122">Nativní kompilátor .NET bude automaticky zpracovávat tento kód.</span><span class="sxs-lookup"><span data-stu-id="2c86c-122">The .NET Native compiler will automatically handle this code.</span></span>  
  
### <a name="typeof-used-outside-the-constructor"></a><span data-ttu-id="2c86c-123">typ použitého mimo konstruktor</span><span class="sxs-lookup"><span data-stu-id="2c86c-123">typeof used outside the constructor</span></span>

 <span data-ttu-id="2c86c-124">Pokud voláte konstruktor těchto tříd serializace a používáte operátor [C# typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) mimo <xref:System.Type> výraz dodaný parametru konstruktoru, jako v následujícím kódu, kompilátor .NET Native nemůže přeložit typ:</span><span class="sxs-lookup"><span data-stu-id="2c86c-124">If you call a constructor of these serialization classes and use the C# [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) operator outside the expression supplied to the constructor’s <xref:System.Type> parameter, as in the following code, the .NET Native compiler cannot resolve the type:</span></span>  
  
 [!code-csharp[ProjectN#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#6)]  
  
 <span data-ttu-id="2c86c-125">V takovém případě je nutné zadat typ v souboru direktiv runtime přidáním položky takto:</span><span class="sxs-lookup"><span data-stu-id="2c86c-125">In this case, you must specify the type in the runtime directives file by adding an entry like this:</span></span>  
  
```xml  
<Type Name="DataSet" Browse="Required Public" />  
```  
  
 <span data-ttu-id="2c86c-126">Podobně pokud voláte konstruktor, <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29> například a poskytnout <xref:System.Type> pole další objekty serializovat, jako v následujícím kódu, kompilátor .NET Native nelze vyřešit tyto typy.</span><span class="sxs-lookup"><span data-stu-id="2c86c-126">Similarly, if you call a constructor such as <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29> and provide an array of additional <xref:System.Type> objects to serialize, as in the following code, the .NET Native compiler cannot resolve these types.</span></span>  
  
 [!code-csharp[ProjectN#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#7)]  
  
<span data-ttu-id="2c86c-127">Do souboru direktiv runtime přidejte následující položky, například následující:</span><span class="sxs-lookup"><span data-stu-id="2c86c-127">Add entries such as the following for each type to the runtime directives file:</span></span>  
  
```xml  
<Type Name="t" Browse="Required Public" />  
```  
  
<span data-ttu-id="2c86c-128">Informace o syntaxi použité v [ \<](type-element-net-native.md)příkladu naleznete v tématu Typ> Element .</span><span class="sxs-lookup"><span data-stu-id="2c86c-128">For information about the syntax used in the example, see [\<Type> Element](type-element-net-native.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c86c-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="2c86c-129">See also</span></span>

- [<span data-ttu-id="2c86c-130">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="2c86c-130">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="2c86c-131">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="2c86c-131">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="2c86c-132">\<Typ> element</span><span class="sxs-lookup"><span data-stu-id="2c86c-132">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="2c86c-133">\<> element oboru názvů</span><span class="sxs-lookup"><span data-stu-id="2c86c-133">\<Namespace> Element</span></span>](namespace-element-net-native.md)
