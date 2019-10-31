---
title: Serializace a metadata
ms.date: 03/30/2017
ms.assetid: 619ecf1c-1ca5-4d66-8934-62fe7aad78c6
ms.openlocfilehash: 1805b6ca06d584237303d1366222419da3e8b9ef
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128113"
---
# <a name="serialization-and-metadata"></a><span data-ttu-id="7292a-102">Serializace a metadata</span><span class="sxs-lookup"><span data-stu-id="7292a-102">Serialization and Metadata</span></span>

<span data-ttu-id="7292a-103">Pokud vaše aplikace serializace a deserializace objekty, může být nutné přidat záznamy do souboru direktiv modulu runtime (. Rd. XML), aby bylo zajištěno, že potřebná metadata jsou přítomna v době běhu.</span><span class="sxs-lookup"><span data-stu-id="7292a-103">If your app serializes and deserializes objects, you may need to add entries to your runtime directives (.rd.xml) file to ensure that the necessary metadata is present at run time.</span></span> <span data-ttu-id="7292a-104">Existují dvě kategorie serializátorů a každá z nich vyžaduje jiné zpracování v souboru direktiv modulu runtime:</span><span class="sxs-lookup"><span data-stu-id="7292a-104">There are two categories of serializers, and each requires different handling in your runtime directives file:</span></span>  
  
- <span data-ttu-id="7292a-105">Serializátory třetích stran založené na reflexi.</span><span class="sxs-lookup"><span data-stu-id="7292a-105">Reflection-based third-party serializers.</span></span> <span data-ttu-id="7292a-106">Tyto požadavky vyžadují úpravy souboru direktiv modulu runtime a jsou popsány v následující části.</span><span class="sxs-lookup"><span data-stu-id="7292a-106">These require modifications to your runtime directives file, and are discussed in the next section.</span></span>  
  
- <span data-ttu-id="7292a-107">V knihovně tříd .NET Framework byly nalezeny serializátory založené na reflexi.</span><span class="sxs-lookup"><span data-stu-id="7292a-107">Non-reflection based serializers found in the .NET Framework class library.</span></span> <span data-ttu-id="7292a-108">Ty mohou vyžadovat úpravy souboru direktiv modulu runtime a jsou popsány v části [Microsoft serializátory](#Microsoft) .</span><span class="sxs-lookup"><span data-stu-id="7292a-108">These may require modifications to your runtime directives file, and are discussed in the [Microsoft serializers](#Microsoft) section.</span></span>  
  
<a name="ThirdParty"></a>
## <a name="third-party-serializers"></a><span data-ttu-id="7292a-109">Serializátory třetích stran</span><span class="sxs-lookup"><span data-stu-id="7292a-109">Third-party serializers</span></span>

 <span data-ttu-id="7292a-110">Serializace jiných částí, včetně Newtonsoft. JSON, jsou obvykle založené na reflexi.</span><span class="sxs-lookup"><span data-stu-id="7292a-110">Third-part serializers, including Newtonsoft.JSON, typically are reflection-based.</span></span> <span data-ttu-id="7292a-111">Vzhledem k binárnímu velkému objektu (BLOB) serializovaných dat jsou pole v datech přiřazena konkrétnímu typu vyhledáním polí cílového typu podle názvu.</span><span class="sxs-lookup"><span data-stu-id="7292a-111">Given a binary large object (BLOB) of serialized data, the fields in the data are assigned to a concrete type by looking up the fields of the target type by name.</span></span> <span data-ttu-id="7292a-112">Minimálně pomocí těchto knihoven způsobí [MissingMetadataException](missingmetadataexception-class-net-native.md) výjimky pro každý objekt <xref:System.Type>, který se pokoušíte serializovat nebo deserializovat v kolekci `List<Type>`.</span><span class="sxs-lookup"><span data-stu-id="7292a-112">At a minimum, using these libraries causes [MissingMetadataException](missingmetadataexception-class-net-native.md) exceptions for each <xref:System.Type> object that you try to serialize or deserialize in a `List<Type>` collection.</span></span>  
  
 <span data-ttu-id="7292a-113">Nejjednodušší způsob, jak řešit problémy způsobené chybějícími metadaty pro tyto serializátory, je shromáždit typy, které budou použity v serializaci v rámci jednoho oboru názvů (například `App.Models`) a použít direktivu `Serialize` metadata:</span><span class="sxs-lookup"><span data-stu-id="7292a-113">The easiest way to address issues caused by missing metadata for these serializers is to collect types that will be used in serialization under a single namespace (such as `App.Models`) and apply a `Serialize` metadata directive to it:</span></span>  
  
```xml  
<Namespace Name="App.Models" Serialize="Required PublicAndInternal" />  
```  
  
 <span data-ttu-id="7292a-114">Informace o syntaxi použité v příkladu naleznete v tématu [\<obor názvů > elementu](namespace-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="7292a-114">For information about the syntax used in the example, see [\<Namespace> Element](namespace-element-net-native.md).</span></span>  
  
<a name="Microsoft"></a>
## <a name="microsoft-serializers"></a><span data-ttu-id="7292a-115">Serializátory Microsoftu</span><span class="sxs-lookup"><span data-stu-id="7292a-115">Microsoft serializers</span></span>

 <span data-ttu-id="7292a-116">I když třídy <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>a <xref:System.Xml.Serialization.XmlSerializer> nespoléhají na reflexi, vyžadují, aby byl kód generován na základě objektu k serializaci nebo deserializaci.</span><span class="sxs-lookup"><span data-stu-id="7292a-116">Although the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes do not rely on reflection, they do require code to be generated based on the object to be serialized or deserialized.</span></span> <span data-ttu-id="7292a-117">Přetížené konstruktory pro každý serializátor zahrnují parametr <xref:System.Type>, který určuje typ, který se má serializovat nebo deserializovat.</span><span class="sxs-lookup"><span data-stu-id="7292a-117">The overloaded constructors for each serializer include a <xref:System.Type> parameter that specifies the type to be serialized or deserialized.</span></span> <span data-ttu-id="7292a-118">Způsob určení tohoto typu ve vašem kódu definuje akci, kterou je nutné provést, jak je popsáno v následujících dvou částech.</span><span class="sxs-lookup"><span data-stu-id="7292a-118">How you specify that type in your code defines the action you must take, as discussed in the next two sections.</span></span>  
  
### <a name="typeof-used-in-the-constructor"></a><span data-ttu-id="7292a-119">typeof použitý v konstruktoru</span><span class="sxs-lookup"><span data-stu-id="7292a-119">typeof used in the constructor</span></span>

 <span data-ttu-id="7292a-120">Pokud voláte konstruktor těchto tříd serializace a zahrnete C# do volání metody operátor [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) , **není nutné provádět žádnou další práci**.</span><span class="sxs-lookup"><span data-stu-id="7292a-120">If you call a constructor of these serialization classes and include the C# [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) operator in the method call, **you do not have to do any additional work**.</span></span> <span data-ttu-id="7292a-121">Například v každém z následujících volání konstruktoru třídy serializace je klíčové slovo `typeof` použito jako součást výrazu předaného konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="7292a-121">For example, in each of the following calls to a serialization class constructor, the `typeof` keyword is used as part of the expression passed to the constructor.</span></span>  
  
 [!code-csharp[ProjectN#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#5)]  
  
 <span data-ttu-id="7292a-122">Kompilátor .NET Native tento kód automaticky zpracuje.</span><span class="sxs-lookup"><span data-stu-id="7292a-122">The .NET Native compiler will automatically handle this code.</span></span>  
  
### <a name="typeof-used-outside-the-constructor"></a><span data-ttu-id="7292a-123">typeof se používá mimo konstruktor.</span><span class="sxs-lookup"><span data-stu-id="7292a-123">typeof used outside the constructor</span></span>

 <span data-ttu-id="7292a-124">Pokud voláte konstruktor těchto tříd serializace a použijete C# operátor [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) mimo výraz dodaný do <xref:System.Type> parametru konstruktoru, jako v následujícím kódu, kompilátor .NET Native nemůže přeložit typ:</span><span class="sxs-lookup"><span data-stu-id="7292a-124">If you call a constructor of these serialization classes and use the C# [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) operator outside the expression supplied to the constructor’s <xref:System.Type> parameter, as in the following code, the .NET Native compiler cannot resolve the type:</span></span>  
  
 [!code-csharp[ProjectN#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#6)]  
  
 <span data-ttu-id="7292a-125">V takovém případě je nutné zadat typ do souboru direktiv modulu runtime přidáním položky takto:</span><span class="sxs-lookup"><span data-stu-id="7292a-125">In this case, you must specify the type in the runtime directives file by adding an entry like this:</span></span>  
  
```xml  
<Type Name="DataSet" Browse="Required Public" />  
```  
  
 <span data-ttu-id="7292a-126">Podobně při volání konstruktoru, jako je například <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType> a poskytnutí pole dalších <xref:System.Type> objektů k serializaci, jako v následujícím kódu, kompilátor .NET Native nemůže tyto typy vyřešit.</span><span class="sxs-lookup"><span data-stu-id="7292a-126">Similarly, if you call a constructor such as <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType> and provide an array of additional <xref:System.Type> objects to serialize, as in the following code, the .NET Native compiler cannot resolve these types.</span></span>  
  
 [!code-csharp[ProjectN#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#7)]  
  
 <span data-ttu-id="7292a-127">Do souboru direktiv modulu runtime musíte přidat položky jako například následující pro každý typ:</span><span class="sxs-lookup"><span data-stu-id="7292a-127">You must add entries such as the following for each type to the runtime directives file:</span></span>  
  
```xml  
<Type Name="t" Browse="Required Public" />  
```  
  
 <span data-ttu-id="7292a-128">Informace o syntaxi použité v příkladu naleznete v tématu [\<Type > elementu](type-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="7292a-128">For information about the syntax used in the example, see [\<Type> Element](type-element-net-native.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7292a-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7292a-129">See also</span></span>

- [<span data-ttu-id="7292a-130">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="7292a-130">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="7292a-131">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="7292a-131">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="7292a-132">\<typ > elementu</span><span class="sxs-lookup"><span data-stu-id="7292a-132">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="7292a-133">\<> elementu oboru názvů</span><span class="sxs-lookup"><span data-stu-id="7292a-133">\<Namespace> Element</span></span>](namespace-element-net-native.md)
