---
title: Rozhraní API, která závisí na reflexi
ms.date: 03/30/2017
ms.assetid: f9532629-6594-4a41-909f-d083f30a42f3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e7ec1280f3b7ba25367fac21d5160046915636a5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076858"
---
# <a name="apis-that-rely-on-reflection"></a><span data-ttu-id="1ae4b-102">Rozhraní API, která závisí na reflexi</span><span class="sxs-lookup"><span data-stu-id="1ae4b-102">APIs That Rely on Reflection</span></span>
<span data-ttu-id="1ae4b-103">V některých případech použití reflexe v kódu není zřejmé a proto [!INCLUDE[net_native](../../../includes/net-native-md.md)] řetězce nástrojů není zachovat metadata, která je potřeba v době běhu.</span><span class="sxs-lookup"><span data-stu-id="1ae4b-103">In some cases, the use of reflection in code isn't obvious, and so the [!INCLUDE[net_native](../../../includes/net-native-md.md)] tool chain doesn't preserve metadata that is needed at run time.</span></span> <span data-ttu-id="1ae4b-104">Toto téma popisuje některé běžné rozhraní API nebo běžné vzory programování, které nejsou považované za součást rozhraní API reflexe, ale, který závisí na reflexi proběhl úspěšně.</span><span class="sxs-lookup"><span data-stu-id="1ae4b-104">This topic covers some common APIs or common programming patterns that aren't considered part of the reflection API but that rely on reflection to execute successfully.</span></span> <span data-ttu-id="1ae4b-105">Pokud je použijete ve zdrojovém kódu, můžete přidat informace o nich do direktivy modulu runtime (. rd.xml) souboru tak, aby volání těchto rozhraní API nevyvolají výjimku [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) výjimky nebo jinou výjimku za běhu.</span><span class="sxs-lookup"><span data-stu-id="1ae4b-105">If you use them in your source code, you can add information about them to the runtime directives (.rd.xml) file so that calls to these APIs do not throw a [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exception or some other exception at run time.</span></span>  
  
## <a name="typemakegenerictype-method"></a><span data-ttu-id="1ae4b-106">Type.MakeGenericType – metoda</span><span class="sxs-lookup"><span data-stu-id="1ae4b-106">Type.MakeGenericType method</span></span>  
 <span data-ttu-id="1ae4b-107">Dynamicky vytvořit instanci obecného typu `AppClass<T>` voláním <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> metoda pomocí kódu takto:</span><span class="sxs-lookup"><span data-stu-id="1ae4b-107">You can dynamically instantiate a generic type `AppClass<T>` by calling the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method by using code like this:</span></span>  
  
 [!code-csharp[ProjectN#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/type_makegenerictype1.cs#1)]  
  
 <span data-ttu-id="1ae4b-108">Pro tento kód v době spuštění úspěšné se vyžaduje několik položek metadat.</span><span class="sxs-lookup"><span data-stu-id="1ae4b-108">For this code to succeed at run time, several items of metadata are required.</span></span> <span data-ttu-id="1ae4b-109">První je `Browse` metadata pro obecný typ bez instancí `AppClass<T>`:</span><span class="sxs-lookup"><span data-stu-id="1ae4b-109">The first is `Browse` metadata for the uninstantiated generic type, `AppClass<T>`:</span></span>  
  
```xml  
<Type Name="App1.AppClass`1" Browse="Required PublicAndInternal" />  
```  
  
 <span data-ttu-id="1ae4b-110">Díky tomu <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> volání metod, které proběhly úspěšně a vrátí platný <xref:System.Type> objektu.</span><span class="sxs-lookup"><span data-stu-id="1ae4b-110">This allows the <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> method call to succeed and return a valid <xref:System.Type> object.</span></span>  
  
 <span data-ttu-id="1ae4b-111">Ale i v případě, že přidáte metadata pro obecný typ bez instancí, volání <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> vyvolá metoda výjimku [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) výjimka:</span><span class="sxs-lookup"><span data-stu-id="1ae4b-111">But even when you add metadata for the uninstantiated generic type, calling the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method throws a [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exception:</span></span>  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.AppClass`1<System.Int32>.  
```  
  
 <span data-ttu-id="1ae4b-112">Následující direktiva běhu můžete přidat do souboru direktiv modulu runtime pro přidání `Activate` metadata pro konkrétní instanci přes `AppClass<T>` z <xref:System.Int32?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="1ae4b-112">You can add the following run-time directive to the runtime directives file to add `Activate` metadata for the specific instantiation over `AppClass<T>` of <xref:System.Int32?displayProperty=nameWithType>:</span></span>  
  
```xml  
<TypeInstantiation Name="App1.AppClass" Arguments="System.Int32"   
                   Activate="Required Public" />  
```  
  
 <span data-ttu-id="1ae4b-113">Každý různé vytváření instancí přes `AppClass<T>` vyžaduje samostatné směrnice, když se vytváří s <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> metoda a nepoužívá se staticky.</span><span class="sxs-lookup"><span data-stu-id="1ae4b-113">Each different instantiation over `AppClass<T>` requires a separate directive if it is being created with the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method and not used statically.</span></span>  
  
## <a name="methodinfomakegenericmethod-method"></a><span data-ttu-id="1ae4b-114">MethodInfo.MakeGenericMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="1ae4b-114">MethodInfo.MakeGenericMethod method</span></span>  
 <span data-ttu-id="1ae4b-115">Zadané třídy `Class1` obecnou metodou s `GetMethod<T>(T t)`, `GetMethod` lze vyvolat pomocí reflexe pomocí kódu takto:</span><span class="sxs-lookup"><span data-stu-id="1ae4b-115">Given a class `Class1` with a generic method `GetMethod<T>(T t)`, `GetMethod` can be invoked through reflection by using code like this:</span></span>  
  
 [!code-csharp[ProjectN#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/makegenericmethod1.cs#2)]  
  
 <span data-ttu-id="1ae4b-116">Tento kód spustit, vyžaduje několik položek metadat:</span><span class="sxs-lookup"><span data-stu-id="1ae4b-116">To run successfully, this code requires several items of metadata:</span></span>  
  
-   `Browse` <span data-ttu-id="1ae4b-117">metadata pro typ, jehož metoda, kterou chcete volat.</span><span class="sxs-lookup"><span data-stu-id="1ae4b-117">metadata for the type whose method you want to call.</span></span>  
  
-   `Browse` <span data-ttu-id="1ae4b-118">metadata pro metodu, kterou chcete volat.</span><span class="sxs-lookup"><span data-stu-id="1ae4b-118">metadata for the method you want to call.</span></span>  <span data-ttu-id="1ae4b-119">Pokud je veřejná metoda, přidání veřejné `Browse` metadat pro typ obsahující metodu, obsahuje příliš.</span><span class="sxs-lookup"><span data-stu-id="1ae4b-119">If it is a public method, adding public `Browse` metadata for the containing type includes the method, too.</span></span>  
  
-   <span data-ttu-id="1ae4b-120">Dynamická metadata pro metodu chcete volat, tak, aby se odebral delegáta volání reflexe [!INCLUDE[net_native](../../../includes/net-native-md.md)] nástroj řetězce.</span><span class="sxs-lookup"><span data-stu-id="1ae4b-120">Dynamic metadata for the method you want to call, so that the reflection invocation delegate is not removed by the [!INCLUDE[net_native](../../../includes/net-native-md.md)] tool chain.</span></span> <span data-ttu-id="1ae4b-121">Pokud chybí metadata dynamické metody, je vyvolána následující výjimka, když <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> volání metody:</span><span class="sxs-lookup"><span data-stu-id="1ae4b-121">If dynamic metadata is missing for the method, the following exception is thrown when the <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> method is called:</span></span>  
  
    ```  
    MakeGenericMethod() cannot create this generic method instantiation because the instantiation was not metadata-enabled: 'App1.Class1.GenMethod<Int32>(Int32)'.  
    ```  
  
 <span data-ttu-id="1ae4b-122">Následující direktivy modulu runtime Ujistěte se, že všechna požadovaná metadata jsou k dispozici:</span><span class="sxs-lookup"><span data-stu-id="1ae4b-122">The following runtime directives ensure that all required metadata is available:</span></span>  
  
```xml  
<Type Name="App1.Class1" Browse="Required PublicAndInternal">  
   <MethodInstantiation Name="GenMethod" Arguments="System.Int32" Dynamic="Required"/>  
</Type>  
```  
  
 <span data-ttu-id="1ae4b-123">A `MethodInstantiation` direktiva je potřebná pro každý různé vytváření instancí metody, která je dynamicky vyvolána, a `Arguments` element se aktualizuje tak, aby odrážely každý argument různé vytváření instancí.</span><span class="sxs-lookup"><span data-stu-id="1ae4b-123">A `MethodInstantiation` directive is required for each different instantiation of the method that is dynamically invoked, and the `Arguments` element is updated to reflect each different instantiation argument.</span></span>  
  
## <a name="arraycreateinstance-and-typemaketypearray-methods"></a><span data-ttu-id="1ae4b-124">Metody Array.CreateInstance a Type.MakeTypeArray</span><span class="sxs-lookup"><span data-stu-id="1ae4b-124">Array.CreateInstance and Type.MakeTypeArray methods</span></span>  
 <span data-ttu-id="1ae4b-125">Následující příklad volá <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> a <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> metody na typu, `Class1`.</span><span class="sxs-lookup"><span data-stu-id="1ae4b-125">The following example calls the <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> and <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> methods on a type, `Class1`.</span></span>  
  
 [!code-csharp[ProjectN#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/array1.cs#3)]  
  
 <span data-ttu-id="1ae4b-126">Pokud je k dispozici žádná metadata pole, vrátí následující chybu:</span><span class="sxs-lookup"><span data-stu-id="1ae4b-126">If no array metadata is present, the following error results:</span></span>  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.Class1[]  
  
Unfortunately, no further information is available.  
```  
  
 `Browse` <span data-ttu-id="1ae4b-127">metadata pro typ pole je potřeba dynamicky vytvořit instanci.</span><span class="sxs-lookup"><span data-stu-id="1ae4b-127">metadata for the array type is required to dynamically instantiate it.</span></span>  <span data-ttu-id="1ae4b-128">Následující direktivy modulu runtime umožňuje dynamické vytváření instancí `Class1[]`.</span><span class="sxs-lookup"><span data-stu-id="1ae4b-128">The following runtime directive allows dynamic instantiation of `Class1[]`.</span></span>  
  
```xml  
<Type Name="App1.Class1[]" Browse="Required Public" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="1ae4b-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1ae4b-129">See also</span></span>

- [<span data-ttu-id="1ae4b-130">Začínáme</span><span class="sxs-lookup"><span data-stu-id="1ae4b-130">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)
- [<span data-ttu-id="1ae4b-131">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="1ae4b-131">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
