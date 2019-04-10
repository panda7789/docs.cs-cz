---
title: Serializace a metadata
ms.date: 03/30/2017
ms.assetid: 619ecf1c-1ca5-4d66-8934-62fe7aad78c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c82d32fe5b1e62a19ff5e2920c5943f1303b2d64
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207029"
---
# <a name="serialization-and-metadata"></a><span data-ttu-id="ef69d-102">Serializace a metadata</span><span class="sxs-lookup"><span data-stu-id="ef69d-102">Serialization and Metadata</span></span>
<span data-ttu-id="ef69d-103">Pokud vaše aplikace serializuje a deserializuje objekty, budete muset přidat položky do vašich direktivy modulu runtime (. rd.xml) souboru k zajištění, že je k dispozici v době běhu potřebná metadata.</span><span class="sxs-lookup"><span data-stu-id="ef69d-103">If your app serializes and deserializes objects, you may need to add entries to your runtime directives (.rd.xml) file to ensure that the necessary metadata is present at run time.</span></span> <span data-ttu-id="ef69d-104">Existují dvě kategorie serializátory a vyžaduje jiný zpracování v souboru direktiv modulu runtime:</span><span class="sxs-lookup"><span data-stu-id="ef69d-104">There are two categories of serializers, and each requires different handling in your runtime directives file:</span></span>  
  
-   <span data-ttu-id="ef69d-105">Serializátory založenými na reflexi třetích stran.</span><span class="sxs-lookup"><span data-stu-id="ef69d-105">Reflection-based third-party serializers.</span></span> <span data-ttu-id="ef69d-106">Ty vyžadují změny do souboru direktiv modulu runtime a jsou popsané v další části.</span><span class="sxs-lookup"><span data-stu-id="ef69d-106">These require modifications to your runtime directives file, and are discussed in the next section.</span></span>  
  
-   <span data-ttu-id="ef69d-107">Na Non reflexi serializátory najdete v knihovně tříd rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ef69d-107">Non-reflection based serializers found in the .NET Framework class library.</span></span> <span data-ttu-id="ef69d-108">Ty mohou vyžadovat změny do souboru direktiv modulu runtime a jsou popsány v [Microsoft serializátory](#Microsoft) oddílu.</span><span class="sxs-lookup"><span data-stu-id="ef69d-108">These may require modifications to your runtime directives file, and are discussed in the [Microsoft serializers](#Microsoft) section.</span></span>  
  
<a name="ThirdParty"></a>   
## <a name="third-party-serializers"></a><span data-ttu-id="ef69d-109">Serializátory třetích stran</span><span class="sxs-lookup"><span data-stu-id="ef69d-109">Third-party serializers</span></span>  
 <span data-ttu-id="ef69d-110">Třetí část, včetně Newtonsoft.JSON, obvykle serializátory založenými na reflexi.</span><span class="sxs-lookup"><span data-stu-id="ef69d-110">Third-part serializers, including Newtonsoft.JSON, typically are reflection-based.</span></span> <span data-ttu-id="ef69d-111">Zadaný binární velkých objektů (BLOB) serializovaných dat, pole v datech jsou přiřazeny k konkrétního typu implementujícího typ vyhledá pole cílového typu podle názvu.</span><span class="sxs-lookup"><span data-stu-id="ef69d-111">Given a binary large object (BLOB) of serialized data, the fields in the data are assigned to a concrete type by looking up the fields of the target type by name.</span></span> <span data-ttu-id="ef69d-112">Pomocí těchto knihoven způsobí minimálně [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) výjimky pro každou <xref:System.Type> objekt, který pokusu o serializaci nebo deserializaci v `List<Type>` kolekce.</span><span class="sxs-lookup"><span data-stu-id="ef69d-112">At a minimum, using these libraries causes [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exceptions for each <xref:System.Type> object that you try to serialize or deserialize in a `List<Type>` collection.</span></span>  
  
 <span data-ttu-id="ef69d-113">Je nejjednodušší způsob, jak řešit problémy způsobené chybí metadata pro tyto serializátory shromažďovat typy, které se použijí v serializaci v rámci jednoho oboru názvů (jako `App.Models`) a použít `Serialize` směrnice metadata do ní:</span><span class="sxs-lookup"><span data-stu-id="ef69d-113">The easiest way to address issues caused by missing metadata for these serializers is to collect types that will be used in serialization under a single namespace (such as `App.Models`) and apply a `Serialize` metadata directive to it:</span></span>  
  
```xml  
<Namespace Name="App.Models" Serialize="Required PublicAndInternal" />  
```  
  
 <span data-ttu-id="ef69d-114">Informace o syntaxi použitých v příkladu najdete v tématu [ \<Namespace > Element](../../../docs/framework/net-native/namespace-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="ef69d-114">For information about the syntax used in the example, see [\<Namespace> Element](../../../docs/framework/net-native/namespace-element-net-native.md).</span></span>  
  
<a name="Microsoft"></a>   
## <a name="microsoft-serializers"></a><span data-ttu-id="ef69d-115">Microsoft serializátorů</span><span class="sxs-lookup"><span data-stu-id="ef69d-115">Microsoft serializers</span></span>  
 <span data-ttu-id="ef69d-116">I když <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, a <xref:System.Xml.Serialization.XmlSerializer> třídy není závisí na reflexi, vyžadují kód vygenerování založené na objekt, který má být serializován nebo deserializován.</span><span class="sxs-lookup"><span data-stu-id="ef69d-116">Although the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes do not rely on reflection, they do require code to be generated based on the object to be serialized or deserialized.</span></span> <span data-ttu-id="ef69d-117">Přetížené konstruktory jednotlivých převodník do sériového tvaru zahrnout <xref:System.Type> parametr, který určuje typ, který má být serializován nebo deserializován.</span><span class="sxs-lookup"><span data-stu-id="ef69d-117">The overloaded constructors for each serializer include a <xref:System.Type> parameter that specifies the type to be serialized or deserialized.</span></span> <span data-ttu-id="ef69d-118">Jak určit, že typ v kódu určuje akci, kterou je třeba provést, jak je popsáno v následujících dvou částech.</span><span class="sxs-lookup"><span data-stu-id="ef69d-118">How you specify that type in your code defines the action you must take, as discussed in the next two sections.</span></span>  
  
### <a name="typeof-used-in-the-constructor"></a><span data-ttu-id="ef69d-119">typeof použít v konstruktoru</span><span class="sxs-lookup"><span data-stu-id="ef69d-119">typeof used in the constructor</span></span>  
 <span data-ttu-id="ef69d-120">Pokud volání konstruktoru z těchto tříd serializace a uveďte C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) – klíčové slovo ve volání metody **nemusíte dělat nic dalšího**.</span><span class="sxs-lookup"><span data-stu-id="ef69d-120">If you call a constructor of these serialization classes and include the C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) keyword in the method call, **you do not have to do any additional work**.</span></span> <span data-ttu-id="ef69d-121">Například v každé z následujících volání konstruktoru třídy serializace `typeof` – klíčové slovo se používá jako součást výrazu předaný konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="ef69d-121">For example, in each of the following calls to a serialization class constructor, the `typeof` keyword is used as part of the expression passed to the constructor.</span></span>  
  
 [!code-csharp[ProjectN#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#5)]  
  
 <span data-ttu-id="ef69d-122">[!INCLUDE[net_native](../../../includes/net-native-md.md)] Kompilátor automaticky zpracovává tento kód.</span><span class="sxs-lookup"><span data-stu-id="ef69d-122">The [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler will automatically handle this code.</span></span>  
  
### <a name="typeof-used-outside-the-constructor"></a><span data-ttu-id="ef69d-123">typeof použít mimo konstruktor</span><span class="sxs-lookup"><span data-stu-id="ef69d-123">typeof used outside the constructor</span></span>  
 <span data-ttu-id="ef69d-124">Pokud volání konstruktoru z těchto tříd serializace a použít C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) – klíčové slovo mimo výraz zadaný konstruktoru <xref:System.Type> parametr, stejně jako v následujícím kódu [!INCLUDE[net_native](../../../includes/net-native-md.md)] kompilátoru Nelze přeložit typ:</span><span class="sxs-lookup"><span data-stu-id="ef69d-124">If you call a constructor of these serialization classes and use the C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) keyword outside the expression supplied to the constructor’s <xref:System.Type> parameter, as in the following code, the [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler cannot resolve the type:</span></span>  
  
 [!code-csharp[ProjectN#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#6)]  
  
 <span data-ttu-id="ef69d-125">V takovém případě je nutné zadat typ v souboru direktiv modulu runtime přidáním položky jako je tato:</span><span class="sxs-lookup"><span data-stu-id="ef69d-125">In this case, you must specify the type in the runtime directives file by adding an entry like this:</span></span>  
  
```xml  
<Type Name="DataSet" Browse="Required Public" />  
```  
  
 <span data-ttu-id="ef69d-126">Podobně jako při volání konstruktoru <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType> a poskytují celou řadu dalších <xref:System.Type> objekty k serializaci, stejně jako v následujícím kódu [!INCLUDE[net_native](../../../includes/net-native-md.md)] kompilátor nemůže vyřešit tyto typy.</span><span class="sxs-lookup"><span data-stu-id="ef69d-126">Similarly, if you call a constructor such as <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType> and provide an array of additional <xref:System.Type> objects to serialize, as in the following code, the [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler cannot resolve these types.</span></span>  
  
 [!code-csharp[ProjectN#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#7)]  
  
 <span data-ttu-id="ef69d-127">Do souboru direktiv modulu runtime, je nutné přidat položky jako je například pro každý typ následující:</span><span class="sxs-lookup"><span data-stu-id="ef69d-127">You must add entries such as the following for each type to the runtime directives file:</span></span>  
  
```xml  
<Type Name="t" Browse="Required Public" />  
```  
  
 <span data-ttu-id="ef69d-128">Informace o syntaxi použitých v příkladu najdete v tématu [ \<typ > elementu](../../../docs/framework/net-native/type-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="ef69d-128">For information about the syntax used in the example, see [\<Type> Element](../../../docs/framework/net-native/type-element-net-native.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef69d-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ef69d-129">See also</span></span>

- [<span data-ttu-id="ef69d-130">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="ef69d-130">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="ef69d-131">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="ef69d-131">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
- [<span data-ttu-id="ef69d-132">\<Typ > – Element</span><span class="sxs-lookup"><span data-stu-id="ef69d-132">\<Type> Element</span></span>](../../../docs/framework/net-native/type-element-net-native.md)
- [<span data-ttu-id="ef69d-133">\<Namespace > – Element</span><span class="sxs-lookup"><span data-stu-id="ef69d-133">\<Namespace> Element</span></span>](../../../docs/framework/net-native/namespace-element-net-native.md)
