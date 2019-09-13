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
# <a name="apis-that-rely-on-reflection"></a>Rozhraní API, která závisí na reflexi
V některých případech není použití reflexe v kódu zřejmé, a proto řetěz nástrojů .NET Native nezachovává metadata potřebná v době běhu. Toto téma se zabývá některými běžnými rozhraními API nebo společnými programovacími vzory, které nejsou považovány za součást rozhraní API pro reflexi, ale které se spoléhají na úspěšné provedení Pokud je používáte ve zdrojovém kódu, můžete do souboru direktiv modulu runtime (. Rd. XML) přidat informace, aby volání těchto rozhraní API nevyvolávají výjimku [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) nebo jinou výjimku v době běhu.  
  
## <a name="typemakegenerictype-method"></a>Type. MakeGenericType – metoda  
 Můžete dynamicky vytvořit instanci obecného typu `AppClass<T>` <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> voláním metody pomocí kódu podobného tomuto:  
  
 [!code-csharp[ProjectN#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/type_makegenerictype1.cs#1)]  
  
 Aby byl tento kód v době běhu úspěšný, je nutné provést několik položek metadat. První je `Browse` metadata pro obecný typ bez `AppClass<T>`instancí:  
  
```xml  
<Type Name="App1.AppClass`1" Browse="Required PublicAndInternal" />  
```  
  
 To umožňuje, <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> aby bylo volání metody úspěšné a vrátilo <xref:System.Type> platný objekt.  
  
 Ale i když přidáváte metadata pro obecný typ bez instance, volání <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> metody vyvolá výjimku [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) :  
  
Tuto operaci nelze provést, protože z důvodů výkonu byla odebrána metadata pro následující typ:  
  
`App1.AppClass`1 < System. Int32 >.  
  
 Můžete přidat následující direktivu run-time do souboru direktiv modulu runtime a přidat `Activate` tak metadata pro konkrétní vytváření instancí <xref:System.Int32?displayProperty=nameWithType>přes `AppClass<T>` :  
  
```xml  
<TypeInstantiation Name="App1.AppClass" Arguments="System.Int32"   
                   Activate="Required Public" />  
```  
  
 Každá z různých instancí přes `AppClass<T>` vyžaduje samostatnou direktivu, pokud je vytvořena <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> metodou a nepoužívá se staticky.  
  
## <a name="methodinfomakegenericmethod-method"></a>MethodInfo. MakeGenericMethod – metoda  
 Vzhledem k třídě `Class1` s obecnou `GetMethod` metodou `GetMethod<T>(T t)`je možné ji vyvolat prostřednictvím reflexe pomocí kódu, například takto:  
  
 [!code-csharp[ProjectN#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/makegenericmethod1.cs#2)]  
  
 Aby bylo možné úspěšně spustit, vyžaduje tento kód několik položek metadat:  
  
- `Browse`metadata pro typ, jehož metoda má být volána.  
  
- `Browse`metadata pro metodu, kterou chcete volat.  Pokud se jedná o veřejnou metodu, přidání veřejných `Browse` metadat pro obsažený typ obsahuje také metodu.  
  
- Dynamická metadata pro metodu, kterou chcete volat, aby nebyl delegát volání reflexe odebrán řetězem nástrojů .NET Native. Pokud pro metodu chybí dynamická metadata, je vyvolána následující výjimka při <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> volání metody:  
  
    ```output
    MakeGenericMethod() cannot create this generic method instantiation because the instantiation was not metadata-enabled: 'App1.Class1.GenMethod<Int32>(Int32)'.  
    ```  
  
 Následující direktivy modulu runtime zajišťují, že jsou k dispozici všechna požadovaná metadata:  
  
```xml  
<Type Name="App1.Class1" Browse="Required PublicAndInternal">  
   <MethodInstantiation Name="GenMethod" Arguments="System.Int32" Dynamic="Required"/>  
</Type>  
```  
  
 Direktiva je vyžadována pro každou jinou instanci metody, která je dynamicky vyvolána, `Arguments` a prvek je aktualizován tak, aby odrážel každý jiný argument instance. `MethodInstantiation`  
  
## <a name="arraycreateinstance-and-typemaketypearray-methods"></a>Array. CreateInstance a Type. MakeTypeArray metody  
 Následující příklad volá <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> metody a <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> pro typ, `Class1`.  
  
 [!code-csharp[ProjectN#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/array1.cs#3)]  
  
 Pokud nejsou k dispozici žádná metadata pole, dojde k následující chybě:  
  
```output
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.Class1[]  
  
Unfortunately, no further information is available.  
```  
  
 `Browse`k dynamickému vytvoření instance se vyžaduje metadata pro typ pole.  Následující direktiva modulu runtime umožňuje dynamické vytváření instancí `Class1[]`.  
  
```xml  
<Type Name="App1.Class1[]" Browse="Required Public" />  
```  
  
## <a name="see-also"></a>Viz také:

- [Začínáme](../../../docs/framework/net-native/getting-started-with-net-native.md)
- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
