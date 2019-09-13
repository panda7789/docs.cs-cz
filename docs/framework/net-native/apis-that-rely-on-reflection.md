---
title: Rozhraní API, která závisí na reflexi
ms.date: 03/30/2017
ms.assetid: f9532629-6594-4a41-909f-d083f30a42f3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ba60b6d97d1441cefc9392067c797504f454ac59
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894516"
---
# <a name="apis-that-rely-on-reflection"></a><span data-ttu-id="38edd-102">Rozhraní API, která závisí na reflexi</span><span class="sxs-lookup"><span data-stu-id="38edd-102">APIs That Rely on Reflection</span></span>
<span data-ttu-id="38edd-103">V některých případech není použití reflexe v kódu zřejmé, a proto řetěz nástrojů .NET Native nezachovává metadata potřebná v době běhu.</span><span class="sxs-lookup"><span data-stu-id="38edd-103">In some cases, the use of reflection in code isn't obvious, and so the .NET Native tool chain doesn't preserve metadata that is needed at run time.</span></span> <span data-ttu-id="38edd-104">Toto téma se zabývá některými běžnými rozhraními API nebo společnými programovacími vzory, které nejsou považovány za součást rozhraní API pro reflexi, ale které se spoléhají na úspěšné provedení</span><span class="sxs-lookup"><span data-stu-id="38edd-104">This topic covers some common APIs or common programming patterns that aren't considered part of the reflection API but that rely on reflection to execute successfully.</span></span> <span data-ttu-id="38edd-105">Pokud je používáte ve zdrojovém kódu, můžete do souboru direktiv modulu runtime (. Rd. XML) přidat informace, aby volání těchto rozhraní API nevyvolávají výjimku [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) nebo jinou výjimku v době běhu.</span><span class="sxs-lookup"><span data-stu-id="38edd-105">If you use them in your source code, you can add information about them to the runtime directives (.rd.xml) file so that calls to these APIs do not throw a [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exception or some other exception at run time.</span></span>  
  
## <a name="typemakegenerictype-method"></a><span data-ttu-id="38edd-106">Type. MakeGenericType – metoda</span><span class="sxs-lookup"><span data-stu-id="38edd-106">Type.MakeGenericType method</span></span>  
 <span data-ttu-id="38edd-107">Můžete dynamicky vytvořit instanci obecného typu `AppClass<T>` <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> voláním metody pomocí kódu podobného tomuto:</span><span class="sxs-lookup"><span data-stu-id="38edd-107">You can dynamically instantiate a generic type `AppClass<T>` by calling the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method by using code like this:</span></span>  
  
 [!code-csharp[ProjectN#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/type_makegenerictype1.cs#1)]  
  
 <span data-ttu-id="38edd-108">Aby byl tento kód v době běhu úspěšný, je nutné provést několik položek metadat.</span><span class="sxs-lookup"><span data-stu-id="38edd-108">For this code to succeed at run time, several items of metadata are required.</span></span> <span data-ttu-id="38edd-109">První je `Browse` metadata pro obecný typ bez `AppClass<T>`instancí:</span><span class="sxs-lookup"><span data-stu-id="38edd-109">The first is `Browse` metadata for the uninstantiated generic type, `AppClass<T>`:</span></span>  
  
```xml  
<Type Name="App1.AppClass`1" Browse="Required PublicAndInternal" />  
```  
  
 <span data-ttu-id="38edd-110">To umožňuje, <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> aby bylo volání metody úspěšné a vrátilo <xref:System.Type> platný objekt.</span><span class="sxs-lookup"><span data-stu-id="38edd-110">This allows the <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> method call to succeed and return a valid <xref:System.Type> object.</span></span>  
  
 <span data-ttu-id="38edd-111">Ale i když přidáváte metadata pro obecný typ bez instance, volání <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> metody vyvolá výjimku [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) :</span><span class="sxs-lookup"><span data-stu-id="38edd-111">But even when you add metadata for the uninstantiated generic type, calling the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method throws a [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exception:</span></span>  
  
<span data-ttu-id="38edd-112">Tuto operaci nelze provést, protože z důvodů výkonu byla odebrána metadata pro následující typ:</span><span class="sxs-lookup"><span data-stu-id="38edd-112">This operation cannot be carried out as metadata for the following type was removed for performance reasons:</span></span>  
  
<span data-ttu-id="38edd-113">`App1.AppClass`1 < System. Int32 >.</span><span class="sxs-lookup"><span data-stu-id="38edd-113">`App1.AppClass`1<System.Int32>\`.</span></span>  
  
 <span data-ttu-id="38edd-114">Můžete přidat následující direktivu run-time do souboru direktiv modulu runtime a přidat `Activate` tak metadata pro konkrétní vytváření instancí <xref:System.Int32?displayProperty=nameWithType>přes `AppClass<T>` :</span><span class="sxs-lookup"><span data-stu-id="38edd-114">You can add the following run-time directive to the runtime directives file to add `Activate` metadata for the specific instantiation over `AppClass<T>` of <xref:System.Int32?displayProperty=nameWithType>:</span></span>  
  
```xml  
<TypeInstantiation Name="App1.AppClass" Arguments="System.Int32"   
                   Activate="Required Public" />  
```  
  
 <span data-ttu-id="38edd-115">Každá z různých instancí přes `AppClass<T>` vyžaduje samostatnou direktivu, pokud je vytvořena <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> metodou a nepoužívá se staticky.</span><span class="sxs-lookup"><span data-stu-id="38edd-115">Each different instantiation over `AppClass<T>` requires a separate directive if it is being created with the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method and not used statically.</span></span>  
  
## <a name="methodinfomakegenericmethod-method"></a><span data-ttu-id="38edd-116">MethodInfo. MakeGenericMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="38edd-116">MethodInfo.MakeGenericMethod method</span></span>  
 <span data-ttu-id="38edd-117">Vzhledem k třídě `Class1` s obecnou `GetMethod` metodou `GetMethod<T>(T t)`je možné ji vyvolat prostřednictvím reflexe pomocí kódu, například takto:</span><span class="sxs-lookup"><span data-stu-id="38edd-117">Given a class `Class1` with a generic method `GetMethod<T>(T t)`, `GetMethod` can be invoked through reflection by using code like this:</span></span>  
  
 [!code-csharp[ProjectN#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/makegenericmethod1.cs#2)]  
  
 <span data-ttu-id="38edd-118">Aby bylo možné úspěšně spustit, vyžaduje tento kód několik položek metadat:</span><span class="sxs-lookup"><span data-stu-id="38edd-118">To run successfully, this code requires several items of metadata:</span></span>  
  
- <span data-ttu-id="38edd-119">`Browse`metadata pro typ, jehož metoda má být volána.</span><span class="sxs-lookup"><span data-stu-id="38edd-119">`Browse` metadata for the type whose method you want to call.</span></span>  
  
- <span data-ttu-id="38edd-120">`Browse`metadata pro metodu, kterou chcete volat.</span><span class="sxs-lookup"><span data-stu-id="38edd-120">`Browse` metadata for the method you want to call.</span></span>  <span data-ttu-id="38edd-121">Pokud se jedná o veřejnou metodu, přidání veřejných `Browse` metadat pro obsažený typ obsahuje také metodu.</span><span class="sxs-lookup"><span data-stu-id="38edd-121">If it is a public method, adding public `Browse` metadata for the containing type includes the method, too.</span></span>  
  
- <span data-ttu-id="38edd-122">Dynamická metadata pro metodu, kterou chcete volat, aby nebyl delegát volání reflexe odebrán řetězem nástrojů .NET Native.</span><span class="sxs-lookup"><span data-stu-id="38edd-122">Dynamic metadata for the method you want to call, so that the reflection invocation delegate is not removed by the .NET Native tool chain.</span></span> <span data-ttu-id="38edd-123">Pokud pro metodu chybí dynamická metadata, je vyvolána následující výjimka při <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> volání metody:</span><span class="sxs-lookup"><span data-stu-id="38edd-123">If dynamic metadata is missing for the method, the following exception is thrown when the <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> method is called:</span></span>  
  
    ```output
    MakeGenericMethod() cannot create this generic method instantiation because the instantiation was not metadata-enabled: 'App1.Class1.GenMethod<Int32>(Int32)'.  
    ```  
  
 <span data-ttu-id="38edd-124">Následující direktivy modulu runtime zajišťují, že jsou k dispozici všechna požadovaná metadata:</span><span class="sxs-lookup"><span data-stu-id="38edd-124">The following runtime directives ensure that all required metadata is available:</span></span>  
  
```xml  
<Type Name="App1.Class1" Browse="Required PublicAndInternal">  
   <MethodInstantiation Name="GenMethod" Arguments="System.Int32" Dynamic="Required"/>  
</Type>  
```  
  
 <span data-ttu-id="38edd-125">Direktiva je vyžadována pro každou jinou instanci metody, která je dynamicky vyvolána, `Arguments` a prvek je aktualizován tak, aby odrážel každý jiný argument instance. `MethodInstantiation`</span><span class="sxs-lookup"><span data-stu-id="38edd-125">A `MethodInstantiation` directive is required for each different instantiation of the method that is dynamically invoked, and the `Arguments` element is updated to reflect each different instantiation argument.</span></span>  
  
## <a name="arraycreateinstance-and-typemaketypearray-methods"></a><span data-ttu-id="38edd-126">Array. CreateInstance a Type. MakeTypeArray metody</span><span class="sxs-lookup"><span data-stu-id="38edd-126">Array.CreateInstance and Type.MakeTypeArray methods</span></span>  
 <span data-ttu-id="38edd-127">Následující příklad volá <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> metody a <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> pro typ, `Class1`.</span><span class="sxs-lookup"><span data-stu-id="38edd-127">The following example calls the <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> and <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> methods on a type, `Class1`.</span></span>  
  
 [!code-csharp[ProjectN#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/array1.cs#3)]  
  
 <span data-ttu-id="38edd-128">Pokud nejsou k dispozici žádná metadata pole, dojde k následující chybě:</span><span class="sxs-lookup"><span data-stu-id="38edd-128">If no array metadata is present, the following error results:</span></span>  
  
```output
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.Class1[]  
  
Unfortunately, no further information is available.  
```  
  
 <span data-ttu-id="38edd-129">`Browse`k dynamickému vytvoření instance se vyžaduje metadata pro typ pole.</span><span class="sxs-lookup"><span data-stu-id="38edd-129">`Browse` metadata for the array type is required to dynamically instantiate it.</span></span>  <span data-ttu-id="38edd-130">Následující direktiva modulu runtime umožňuje dynamické vytváření instancí `Class1[]`.</span><span class="sxs-lookup"><span data-stu-id="38edd-130">The following runtime directive allows dynamic instantiation of `Class1[]`.</span></span>  
  
```xml  
<Type Name="App1.Class1[]" Browse="Required Public" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="38edd-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="38edd-131">See also</span></span>

- [<span data-ttu-id="38edd-132">Začínáme</span><span class="sxs-lookup"><span data-stu-id="38edd-132">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)
- [<span data-ttu-id="38edd-133">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="38edd-133">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
