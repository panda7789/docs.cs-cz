---
title: Rozhraní API, která závisí na reflexi
ms.date: 03/30/2017
ms.assetid: f9532629-6594-4a41-909f-d083f30a42f3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 98488a8e552940055a6ea06d360af1bd2c6b6079
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33392210"
---
# <a name="apis-that-rely-on-reflection"></a><span data-ttu-id="9a161-102">Rozhraní API, která závisí na reflexi</span><span class="sxs-lookup"><span data-stu-id="9a161-102">APIs That Rely on Reflection</span></span>
<span data-ttu-id="9a161-103">V některých případech použití reflexe v kódu není zřejmé a proto [!INCLUDE[net_native](../../../includes/net-native-md.md)] nástroj řetězu není zachovat metadata, která je vyžadována v době běhu.</span><span class="sxs-lookup"><span data-stu-id="9a161-103">In some cases, the use of reflection in code isn't obvious, and so the [!INCLUDE[net_native](../../../includes/net-native-md.md)] tool chain doesn't preserve metadata that is needed at run time.</span></span> <span data-ttu-id="9a161-104">Toto téma popisuje některé běžné rozhraní API nebo běžných programovací vzorů, které nejsou považovány za součást rozhraní API reflexe, ale který závisí na reflexi proběhl úspěšně.</span><span class="sxs-lookup"><span data-stu-id="9a161-104">This topic covers some common APIs or common programming patterns that aren't considered part of the reflection API but that rely on reflection to execute successfully.</span></span> <span data-ttu-id="9a161-105">Pokud je používáte ve zdrojovém kódu, můžete přidat informace o nich do direktivy modulu runtime (. rd.xml) tak, aby volání tato rozhraní API nevyvolá výjimku [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) výjimky nebo některých jiných výjimky za běhu.</span><span class="sxs-lookup"><span data-stu-id="9a161-105">If you use them in your source code, you can add information about them to the runtime directives (.rd.xml) file so that calls to these APIs do not throw a [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exception or some other exception at run time.</span></span>  
  
## <a name="typemakegenerictype-method"></a><span data-ttu-id="9a161-106">Type.MakeGenericType – metoda</span><span class="sxs-lookup"><span data-stu-id="9a161-106">Type.MakeGenericType method</span></span>  
 <span data-ttu-id="9a161-107">Můžete vytvořit dynamicky instanci obecného typu `AppClass<T>` voláním <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> metoda pomocí kódu takto:</span><span class="sxs-lookup"><span data-stu-id="9a161-107">You can dynamically instantiate a generic type `AppClass<T>` by calling the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method by using code like this:</span></span>  
  
 [!code-csharp[ProjectN#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/type_makegenerictype1.cs#1)]  
  
 <span data-ttu-id="9a161-108">Pro tento kód úspěšné za běhu jsou požadovány několik položek metadat.</span><span class="sxs-lookup"><span data-stu-id="9a161-108">For this code to succeed at run time, several items of metadata are required.</span></span> <span data-ttu-id="9a161-109">První je `Browse` metadata pro bez instancí obecného typu `AppClass<T>`:</span><span class="sxs-lookup"><span data-stu-id="9a161-109">The first is `Browse` metadata for the uninstantiated generic type, `AppClass<T>`:</span></span>  
  
```xml  
<Type Name="App1.AppClass`1" Browse="Required PublicAndInternal" />  
```  
  
 <span data-ttu-id="9a161-110">To umožňuje <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> volání metody úspěšné a vrátíte se platná <xref:System.Type> objektu.</span><span class="sxs-lookup"><span data-stu-id="9a161-110">This allows the <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> method call to succeed and return a valid <xref:System.Type> object.</span></span>  
  
 <span data-ttu-id="9a161-111">Ale i v případě, že přidáte metadata pro bez instancí obecného typu, volání <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> metoda vrátí [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) výjimka:</span><span class="sxs-lookup"><span data-stu-id="9a161-111">But even when you add metadata for the uninstantiated generic type, calling the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method throws a [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exception:</span></span>  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.AppClass`1<System.Int32>.  
```  
  
 <span data-ttu-id="9a161-112">Následující direktiva běhu můžete přidat do souboru direktivy modulu runtime pro přidání `Activate` metadata pro konkrétní instanci přes `AppClass<T>` z <xref:System.Int32?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="9a161-112">You can add the following run-time directive to the runtime directives file to add `Activate` metadata for the specific instantiation over `AppClass<T>` of <xref:System.Int32?displayProperty=nameWithType>:</span></span>  
  
```xml  
<TypeInstantiation Name="App1.AppClass" Arguments="System.Int32"   
                   Activate="Required Public" />  
```  
  
 <span data-ttu-id="9a161-113">Každý jiný konkretizaci přes `AppClass<T>` vyžaduje samostatné – direktiva, když je vytvořena s <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> metoda a nepoužívá se staticky.</span><span class="sxs-lookup"><span data-stu-id="9a161-113">Each different instantiation over `AppClass<T>` requires a separate directive if it is being created with the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method and not used statically.</span></span>  
  
## <a name="methodinfomakegenericmethod-method"></a><span data-ttu-id="9a161-114">MethodInfo.MakeGenericMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="9a161-114">MethodInfo.MakeGenericMethod method</span></span>  
 <span data-ttu-id="9a161-115">Zadané třídy `Class1` s Obecná metoda `GetMethod<T>(T t)`, `GetMethod` vyvolat prostřednictvím reflexe pomocí kódu takto:</span><span class="sxs-lookup"><span data-stu-id="9a161-115">Given a class `Class1` with a generic method `GetMethod<T>(T t)`, `GetMethod` can be invoked through reflection by using code like this:</span></span>  
  
 [!code-csharp[ProjectN#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/makegenericmethod1.cs#2)]  
  
 <span data-ttu-id="9a161-116">K úspěšnému spuštění tohoto kódu vyžaduje několik položek metadat:</span><span class="sxs-lookup"><span data-stu-id="9a161-116">To run successfully, this code requires several items of metadata:</span></span>  
  
-   <span data-ttu-id="9a161-117">`Browse` metadata pro typ jehož metoda, kterou chcete volat.</span><span class="sxs-lookup"><span data-stu-id="9a161-117">`Browse` metadata for the type whose method you want to call.</span></span>  
  
-   <span data-ttu-id="9a161-118">`Browse` metadata pro metodu, kterou chcete volat.</span><span class="sxs-lookup"><span data-stu-id="9a161-118">`Browse` metadata for the method you want to call.</span></span>  <span data-ttu-id="9a161-119">Pokud je veřejná metoda, přidáte veřejných `Browse` metadata pro typ obsahující zahrnuje metodu, příliš.</span><span class="sxs-lookup"><span data-stu-id="9a161-119">If it is a public method, adding public `Browse` metadata for the containing type includes the method, too.</span></span>  
  
-   <span data-ttu-id="9a161-120">Dynamické metadata pro metodu, kterou chcete volat, tak, aby delegát volání reflexe není odebraná pomocí [!INCLUDE[net_native](../../../includes/net-native-md.md)] nástroj řetězu.</span><span class="sxs-lookup"><span data-stu-id="9a161-120">Dynamic metadata for the method you want to call, so that the reflection invocation delegate is not removed by the [!INCLUDE[net_native](../../../includes/net-native-md.md)] tool chain.</span></span> <span data-ttu-id="9a161-121">Pokud chybí dynamické metadata pro metodu, je vyvolána následující výjimka, kdy <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> metoda je volána:</span><span class="sxs-lookup"><span data-stu-id="9a161-121">If dynamic metadata is missing for the method, the following exception is thrown when the <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> method is called:</span></span>  
  
    ```  
    MakeGenericMethod() cannot create this generic method instantiation because the instantiation was not metadata-enabled: 'App1.Class1.GenMethod<Int32>(Int32)'.  
    ```  
  
 <span data-ttu-id="9a161-122">Následující direktivy modulu runtime Ujistěte se, že všechny požadované, metadata jsou k dispozici:</span><span class="sxs-lookup"><span data-stu-id="9a161-122">The following runtime directives ensure that all required metadata is available:</span></span>  
  
```xml  
<Type Name="App1.Class1" Browse="Required PublicAndInternal">  
   <MethodInstantiation Name="GenMethod" Arguments="System.Int32" Dynamic="Required"/>  
</Type>  
```  
  
 <span data-ttu-id="9a161-123">A `MethodInstantiation` direktiva je potřebná pro každý jiný konkretizaci metody, která je volána dynamicky, a `Arguments` element aktualizován, aby odrážel všechny argumenty různých vytváření instancí.</span><span class="sxs-lookup"><span data-stu-id="9a161-123">A `MethodInstantiation` directive is required for each different instantiation of the method that is dynamically invoked, and the `Arguments` element is updated to reflect each different instantiation argument.</span></span>  
  
## <a name="arraycreateinstance-and-typemaketypearray-methods"></a><span data-ttu-id="9a161-124">Metody Array.CreateInstance a Type.MakeTypeArray</span><span class="sxs-lookup"><span data-stu-id="9a161-124">Array.CreateInstance and Type.MakeTypeArray methods</span></span>  
 <span data-ttu-id="9a161-125">Následující příklad volání <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> a <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> metody pro typ `Class1`.</span><span class="sxs-lookup"><span data-stu-id="9a161-125">The following example calls the <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> and <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> methods on a type, `Class1`.</span></span>  
  
 [!code-csharp[ProjectN#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/array1.cs#3)]  
  
 <span data-ttu-id="9a161-126">Pokud je k dispozici žádná metadata pole, vrátí následující chybu:</span><span class="sxs-lookup"><span data-stu-id="9a161-126">If no array metadata is present, the following error results:</span></span>  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.Class1[]  
  
Unfortunately, no further information is available.  
```  
  
 <span data-ttu-id="9a161-127">`Browse` metadata pro typ pole je potřeba dynamicky vytvoří instanci.</span><span class="sxs-lookup"><span data-stu-id="9a161-127">`Browse` metadata for the array type is required to dynamically instantiate it.</span></span>  <span data-ttu-id="9a161-128">Následující direktivy modulu runtime umožňuje dynamické vytvořením instance `Class1[]`.</span><span class="sxs-lookup"><span data-stu-id="9a161-128">The following runtime directive allows dynamic instantiation of `Class1[]`.</span></span>  
  
```xml  
<Type Name="App1.Class1[]" Browse="Required Public" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="9a161-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="9a161-129">See Also</span></span>  
 [<span data-ttu-id="9a161-130">Začínáme</span><span class="sxs-lookup"><span data-stu-id="9a161-130">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)  
 [<span data-ttu-id="9a161-131">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="9a161-131">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
