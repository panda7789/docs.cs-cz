---
title: Rozhraní API, která závisí na reflexi
ms.date: 03/30/2017
ms.assetid: f9532629-6594-4a41-909f-d083f30a42f3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a32e12b593f273c8b812390306c81b311da7c2a4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624696"
---
# <a name="apis-that-rely-on-reflection"></a>Rozhraní API, která závisí na reflexi
V některých případech použití reflexe v kódu není zřejmé a proto [!INCLUDE[net_native](../../../includes/net-native-md.md)] řetězce nástrojů není zachovat metadata, která je potřeba v době běhu. Toto téma popisuje některé běžné rozhraní API nebo běžné vzory programování, které nejsou považované za součást rozhraní API reflexe, ale, který závisí na reflexi proběhl úspěšně. Pokud je použijete ve zdrojovém kódu, můžete přidat informace o nich do direktivy modulu runtime (. rd.xml) souboru tak, aby volání těchto rozhraní API nevyvolají výjimku [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) výjimky nebo jinou výjimku za běhu.  
  
## <a name="typemakegenerictype-method"></a>Type.MakeGenericType – metoda  
 Dynamicky vytvořit instanci obecného typu `AppClass<T>` voláním <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> metoda pomocí kódu takto:  
  
 [!code-csharp[ProjectN#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/type_makegenerictype1.cs#1)]  
  
 Pro tento kód v době spuštění úspěšné se vyžaduje několik položek metadat. První je `Browse` metadata pro obecný typ bez instancí `AppClass<T>`:  
  
```xml  
<Type Name="App1.AppClass`1" Browse="Required PublicAndInternal" />  
```  
  
 Díky tomu <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> volání metod, které proběhly úspěšně a vrátí platný <xref:System.Type> objektu.  
  
 Ale i v případě, že přidáte metadata pro obecný typ bez instancí, volání <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> vyvolá metoda výjimku [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) výjimka:  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.AppClass`1<System.Int32>.  
```  
  
 Následující direktiva běhu můžete přidat do souboru direktiv modulu runtime pro přidání `Activate` metadata pro konkrétní instanci přes `AppClass<T>` z <xref:System.Int32?displayProperty=nameWithType>:  
  
```xml  
<TypeInstantiation Name="App1.AppClass" Arguments="System.Int32"   
                   Activate="Required Public" />  
```  
  
 Každý různé vytváření instancí přes `AppClass<T>` vyžaduje samostatné směrnice, když se vytváří s <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> metoda a nepoužívá se staticky.  
  
## <a name="methodinfomakegenericmethod-method"></a>MethodInfo.MakeGenericMethod – metoda  
 Zadané třídy `Class1` obecnou metodou s `GetMethod<T>(T t)`, `GetMethod` lze vyvolat pomocí reflexe pomocí kódu takto:  
  
 [!code-csharp[ProjectN#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/makegenericmethod1.cs#2)]  
  
 Tento kód spustit, vyžaduje několik položek metadat:  
  
- `Browse` metadata pro typ, jehož metoda, kterou chcete volat.  
  
- `Browse` metadata pro metodu, kterou chcete volat.  Pokud je veřejná metoda, přidání veřejné `Browse` metadat pro typ obsahující metodu, obsahuje příliš.  
  
- Dynamická metadata pro metodu chcete volat, tak, aby se odebral delegáta volání reflexe [!INCLUDE[net_native](../../../includes/net-native-md.md)] nástroj řetězce. Pokud chybí metadata dynamické metody, je vyvolána následující výjimka, když <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> volání metody:  
  
    ```  
    MakeGenericMethod() cannot create this generic method instantiation because the instantiation was not metadata-enabled: 'App1.Class1.GenMethod<Int32>(Int32)'.  
    ```  
  
 Následující direktivy modulu runtime Ujistěte se, že všechna požadovaná metadata jsou k dispozici:  
  
```xml  
<Type Name="App1.Class1" Browse="Required PublicAndInternal">  
   <MethodInstantiation Name="GenMethod" Arguments="System.Int32" Dynamic="Required"/>  
</Type>  
```  
  
 A `MethodInstantiation` direktiva je potřebná pro každý různé vytváření instancí metody, která je dynamicky vyvolána, a `Arguments` element se aktualizuje tak, aby odrážely každý argument různé vytváření instancí.  
  
## <a name="arraycreateinstance-and-typemaketypearray-methods"></a>Metody Array.CreateInstance a Type.MakeTypeArray  
 Následující příklad volá <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> a <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> metody na typu, `Class1`.  
  
 [!code-csharp[ProjectN#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/array1.cs#3)]  
  
 Pokud je k dispozici žádná metadata pole, vrátí následující chybu:  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.Class1[]  
  
Unfortunately, no further information is available.  
```  
  
 `Browse` metadata pro typ pole je potřeba dynamicky vytvořit instanci.  Následující direktivy modulu runtime umožňuje dynamické vytváření instancí `Class1[]`.  
  
```xml  
<Type Name="App1.Class1[]" Browse="Required Public" />  
```  
  
## <a name="see-also"></a>Viz také:

- [Začínáme](../../../docs/framework/net-native/getting-started-with-net-native.md)
- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
