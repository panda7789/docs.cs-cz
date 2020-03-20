---
title: Rozhraní API, která závisí na reflexi
ms.date: 03/30/2017
ms.assetid: f9532629-6594-4a41-909f-d083f30a42f3
ms.openlocfilehash: 1d8daceb6b744b984f86b011ad7952d0da583a79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181095"
---
# <a name="apis-that-rely-on-reflection"></a><span data-ttu-id="f067c-102">Rozhraní API, která závisí na reflexi</span><span class="sxs-lookup"><span data-stu-id="f067c-102">APIs That Rely on Reflection</span></span>
<span data-ttu-id="f067c-103">V některých případech použití reflexe v kódu není zřejmé, a proto řetězec nástrojů .NET Native nezachová metadata, která je potřeba za běhu.</span><span class="sxs-lookup"><span data-stu-id="f067c-103">In some cases, the use of reflection in code isn't obvious, and so the .NET Native tool chain doesn't preserve metadata that is needed at run time.</span></span> <span data-ttu-id="f067c-104">Toto téma popisuje některé běžné rozhraní API nebo běžné programovací vzory, které nejsou považovány za součást reflexe rozhraní API, ale které spoléhají na reflexi úspěšně spustit.</span><span class="sxs-lookup"><span data-stu-id="f067c-104">This topic covers some common APIs or common programming patterns that aren't considered part of the reflection API but that rely on reflection to execute successfully.</span></span> <span data-ttu-id="f067c-105">Pokud je používáte ve zdrojovém kódu, můžete přidat informace o nich do souboru direktiv runtime (.rd.xml), aby volání těchto rozhraní API nevyvolávala výjimku [MissingMetadataException](missingmetadataexception-class-net-native.md) nebo jinou výjimku za běhu.</span><span class="sxs-lookup"><span data-stu-id="f067c-105">If you use them in your source code, you can add information about them to the runtime directives (.rd.xml) file so that calls to these APIs do not throw a [MissingMetadataException](missingmetadataexception-class-net-native.md) exception or some other exception at run time.</span></span>  
  
## <a name="typemakegenerictype-method"></a><span data-ttu-id="f067c-106">Metoda Type.MakeGenericType</span><span class="sxs-lookup"><span data-stu-id="f067c-106">Type.MakeGenericType method</span></span>  
 <span data-ttu-id="f067c-107">Můžete dynamicky vytvořit instanci `AppClass<T>` obecného <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> typu voláním metody pomocí kódu, jako je tento:</span><span class="sxs-lookup"><span data-stu-id="f067c-107">You can dynamically instantiate a generic type `AppClass<T>` by calling the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method by using code like this:</span></span>  
  
 [!code-csharp[ProjectN#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/type_makegenerictype1.cs#1)]  
  
 <span data-ttu-id="f067c-108">Aby byl tento kód úspěšný za běhu, je vyžadováno několik položek metadat.</span><span class="sxs-lookup"><span data-stu-id="f067c-108">For this code to succeed at run time, several items of metadata are required.</span></span> <span data-ttu-id="f067c-109">První z `Browse` prvních jsou metadata pro nerychlý `AppClass<T>`obecný typ:</span><span class="sxs-lookup"><span data-stu-id="f067c-109">The first is `Browse` metadata for the uninstantiated generic type, `AppClass<T>`:</span></span>  
  
```xml  
<Type Name="App1.AppClass`1" Browse="Required PublicAndInternal" />  
```  
  
 <span data-ttu-id="f067c-110">To umožňuje <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> volání metody úspěšné a <xref:System.Type> vrátit platný objekt.</span><span class="sxs-lookup"><span data-stu-id="f067c-110">This allows the <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> method call to succeed and return a valid <xref:System.Type> object.</span></span>  
  
 <span data-ttu-id="f067c-111">Ale i když přidáte metadata pro neokamžitý obecný typ, volání <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> metody vyvolá výjimku [MissingMetadataException:](missingmetadataexception-class-net-native.md)</span><span class="sxs-lookup"><span data-stu-id="f067c-111">But even when you add metadata for the uninstantiated generic type, calling the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method throws a [MissingMetadataException](missingmetadataexception-class-net-native.md) exception:</span></span>  
  
<span data-ttu-id="f067c-112">Tuto operaci nelze provést, protože metadata pro následující typ byla odebrána z důvodů výkonu:</span><span class="sxs-lookup"><span data-stu-id="f067c-112">This operation cannot be carried out as metadata for the following type was removed for performance reasons:</span></span>  
  
<span data-ttu-id="f067c-113">`App1.AppClass`1<System.Int32>".</span><span class="sxs-lookup"><span data-stu-id="f067c-113">`App1.AppClass`1<System.Int32>\`.</span></span>  
  
 <span data-ttu-id="f067c-114">Do souboru direktiv runtime můžete přidat následující `Activate` direktivu za `AppClass<T>` běhu <xref:System.Int32?displayProperty=nameWithType>a přidat metadata pro konkrétní instanci přes :</span><span class="sxs-lookup"><span data-stu-id="f067c-114">You can add the following run-time directive to the runtime directives file to add `Activate` metadata for the specific instantiation over `AppClass<T>` of <xref:System.Int32?displayProperty=nameWithType>:</span></span>  
  
```xml  
<TypeInstantiation Name="App1.AppClass" Arguments="System.Int32"
                   Activate="Required Public" />  
```  
  
 <span data-ttu-id="f067c-115">Každý jiný konsidatér přes `AppClass<T>` vyžaduje samostatnou <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> direktivu, pokud je vytvářen s metodou a není použit staticky.</span><span class="sxs-lookup"><span data-stu-id="f067c-115">Each different instantiation over `AppClass<T>` requires a separate directive if it is being created with the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method and not used statically.</span></span>  
  
## <a name="methodinfomakegenericmethod-method"></a><span data-ttu-id="f067c-116">Metoda MethodInfo.MakeGenericMethod</span><span class="sxs-lookup"><span data-stu-id="f067c-116">MethodInfo.MakeGenericMethod method</span></span>  
 <span data-ttu-id="f067c-117">Dané třídy `Class1` s `GetMethod<T>(T t)`obecnou `GetMethod` metodou , lze vyvolat prostřednictvím reflexe pomocí kódu, jako je tento:</span><span class="sxs-lookup"><span data-stu-id="f067c-117">Given a class `Class1` with a generic method `GetMethod<T>(T t)`, `GetMethod` can be invoked through reflection by using code like this:</span></span>  
  
 [!code-csharp[ProjectN#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/makegenericmethod1.cs#2)]  
  
 <span data-ttu-id="f067c-118">Chcete-li úspěšně spustit, tento kód vyžaduje několik položek metadat:</span><span class="sxs-lookup"><span data-stu-id="f067c-118">To run successfully, this code requires several items of metadata:</span></span>  
  
- <span data-ttu-id="f067c-119">`Browse`metadata pro typ, jehož metodu chcete volat.</span><span class="sxs-lookup"><span data-stu-id="f067c-119">`Browse` metadata for the type whose method you want to call.</span></span>  
  
- <span data-ttu-id="f067c-120">`Browse`metadata pro metodu, kterou chcete volat.</span><span class="sxs-lookup"><span data-stu-id="f067c-120">`Browse` metadata for the method you want to call.</span></span>  <span data-ttu-id="f067c-121">Pokud se jedná o veřejnou metodu, přidání veřejných `Browse` metadat pro obsahující typ zahrnuje také metodu.</span><span class="sxs-lookup"><span data-stu-id="f067c-121">If it is a public method, adding public `Browse` metadata for the containing type includes the method, too.</span></span>  
  
- <span data-ttu-id="f067c-122">Dynamická metadata pro metodu, kterou chcete volat, aby delegát vyvolání odrazu nebyl odebrán řetězcem nástrojů .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f067c-122">Dynamic metadata for the method you want to call, so that the reflection invocation delegate is not removed by the .NET Native tool chain.</span></span> <span data-ttu-id="f067c-123">Pokud chybí dynamická metadata pro metodu, je <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> vyvolána následující výjimka při volání metody:</span><span class="sxs-lookup"><span data-stu-id="f067c-123">If dynamic metadata is missing for the method, the following exception is thrown when the <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> method is called:</span></span>  
  
    ```output
    MakeGenericMethod() cannot create this generic method instantiation because the instantiation was not metadata-enabled: 'App1.Class1.GenMethod<Int32>(Int32)'.  
    ```  
  
 <span data-ttu-id="f067c-124">Následující direktivy modulu runtime zajišťují, že jsou k dispozici všechna požadovaná metadata:</span><span class="sxs-lookup"><span data-stu-id="f067c-124">The following runtime directives ensure that all required metadata is available:</span></span>  
  
```xml  
<Type Name="App1.Class1" Browse="Required PublicAndInternal">  
   <MethodInstantiation Name="GenMethod" Arguments="System.Int32" Dynamic="Required"/>  
</Type>  
```  
  
 <span data-ttu-id="f067c-125">Směrnice `MethodInstantiation` je vyžadována pro každou jinou instanci metody, která `Arguments` je dynamicky vyvolána, a prvek je aktualizován tak, aby odrážel každý jiný argument instance.</span><span class="sxs-lookup"><span data-stu-id="f067c-125">A `MethodInstantiation` directive is required for each different instantiation of the method that is dynamically invoked, and the `Arguments` element is updated to reflect each different instantiation argument.</span></span>  
  
## <a name="arraycreateinstance-and-typemaketypearray-methods"></a><span data-ttu-id="f067c-126">Metody Array.CreateInstance a Type.MakeTypeArray</span><span class="sxs-lookup"><span data-stu-id="f067c-126">Array.CreateInstance and Type.MakeTypeArray methods</span></span>  
 <span data-ttu-id="f067c-127">Následující příklad volá <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> metody a typu `Class1`.</span><span class="sxs-lookup"><span data-stu-id="f067c-127">The following example calls the <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> and <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> methods on a type, `Class1`.</span></span>  
  
 [!code-csharp[ProjectN#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/array1.cs#3)]  
  
 <span data-ttu-id="f067c-128">Pokud nejsou k dispozici žádná metadata pole, výsledkem je následující chyba:</span><span class="sxs-lookup"><span data-stu-id="f067c-128">If no array metadata is present, the following error results:</span></span>  
  
```output
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.Class1[]  
  
Unfortunately, no further information is available.  
```  
  
 <span data-ttu-id="f067c-129">`Browse`metadata pro typ pole je nutné dynamicky konstanci.</span><span class="sxs-lookup"><span data-stu-id="f067c-129">`Browse` metadata for the array type is required to dynamically instantiate it.</span></span>  <span data-ttu-id="f067c-130">Následující direktiva runtime `Class1[]`umožňuje dynamickou instanciaci .</span><span class="sxs-lookup"><span data-stu-id="f067c-130">The following runtime directive allows dynamic instantiation of `Class1[]`.</span></span>  
  
```xml  
<Type Name="App1.Class1[]" Browse="Required Public" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="f067c-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="f067c-131">See also</span></span>

- [<span data-ttu-id="f067c-132">Začínáme</span><span class="sxs-lookup"><span data-stu-id="f067c-132">Getting Started</span></span>](getting-started-with-net-native.md)
- [<span data-ttu-id="f067c-133">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="f067c-133">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
