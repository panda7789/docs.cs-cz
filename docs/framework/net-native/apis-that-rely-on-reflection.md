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
# <a name="apis-that-rely-on-reflection"></a>Rozhraní API, která závisí na reflexi
V některých případech použití reflexe v kódu není zřejmé, a proto řetězec nástrojů .NET Native nezachová metadata, která je potřeba za běhu. Toto téma popisuje některé běžné rozhraní API nebo běžné programovací vzory, které nejsou považovány za součást reflexe rozhraní API, ale které spoléhají na reflexi úspěšně spustit. Pokud je používáte ve zdrojovém kódu, můžete přidat informace o nich do souboru direktiv runtime (.rd.xml), aby volání těchto rozhraní API nevyvolávala výjimku [MissingMetadataException](missingmetadataexception-class-net-native.md) nebo jinou výjimku za běhu.  
  
## <a name="typemakegenerictype-method"></a>Metoda Type.MakeGenericType  
 Můžete dynamicky vytvořit instanci `AppClass<T>` obecného <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> typu voláním metody pomocí kódu, jako je tento:  
  
 [!code-csharp[ProjectN#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/type_makegenerictype1.cs#1)]  
  
 Aby byl tento kód úspěšný za běhu, je vyžadováno několik položek metadat. První z `Browse` prvních jsou metadata pro nerychlý `AppClass<T>`obecný typ:  
  
```xml  
<Type Name="App1.AppClass`1" Browse="Required PublicAndInternal" />  
```  
  
 To umožňuje <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> volání metody úspěšné a <xref:System.Type> vrátit platný objekt.  
  
 Ale i když přidáte metadata pro neokamžitý obecný typ, volání <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> metody vyvolá výjimku [MissingMetadataException:](missingmetadataexception-class-net-native.md)  
  
Tuto operaci nelze provést, protože metadata pro následující typ byla odebrána z důvodů výkonu:  
  
`App1.AppClass`1<System.Int32>".  
  
 Do souboru direktiv runtime můžete přidat následující `Activate` direktivu za `AppClass<T>` běhu <xref:System.Int32?displayProperty=nameWithType>a přidat metadata pro konkrétní instanci přes :  
  
```xml  
<TypeInstantiation Name="App1.AppClass" Arguments="System.Int32"
                   Activate="Required Public" />  
```  
  
 Každý jiný konsidatér přes `AppClass<T>` vyžaduje samostatnou <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> direktivu, pokud je vytvářen s metodou a není použit staticky.  
  
## <a name="methodinfomakegenericmethod-method"></a>Metoda MethodInfo.MakeGenericMethod  
 Dané třídy `Class1` s `GetMethod<T>(T t)`obecnou `GetMethod` metodou , lze vyvolat prostřednictvím reflexe pomocí kódu, jako je tento:  
  
 [!code-csharp[ProjectN#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/makegenericmethod1.cs#2)]  
  
 Chcete-li úspěšně spustit, tento kód vyžaduje několik položek metadat:  
  
- `Browse`metadata pro typ, jehož metodu chcete volat.  
  
- `Browse`metadata pro metodu, kterou chcete volat.  Pokud se jedná o veřejnou metodu, přidání veřejných `Browse` metadat pro obsahující typ zahrnuje také metodu.  
  
- Dynamická metadata pro metodu, kterou chcete volat, aby delegát vyvolání odrazu nebyl odebrán řetězcem nástrojů .NET Native. Pokud chybí dynamická metadata pro metodu, je <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> vyvolána následující výjimka při volání metody:  
  
    ```output
    MakeGenericMethod() cannot create this generic method instantiation because the instantiation was not metadata-enabled: 'App1.Class1.GenMethod<Int32>(Int32)'.  
    ```  
  
 Následující direktivy modulu runtime zajišťují, že jsou k dispozici všechna požadovaná metadata:  
  
```xml  
<Type Name="App1.Class1" Browse="Required PublicAndInternal">  
   <MethodInstantiation Name="GenMethod" Arguments="System.Int32" Dynamic="Required"/>  
</Type>  
```  
  
 Směrnice `MethodInstantiation` je vyžadována pro každou jinou instanci metody, která `Arguments` je dynamicky vyvolána, a prvek je aktualizován tak, aby odrážel každý jiný argument instance.  
  
## <a name="arraycreateinstance-and-typemaketypearray-methods"></a>Metody Array.CreateInstance a Type.MakeTypeArray  
 Následující příklad volá <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> metody a typu `Class1`.  
  
 [!code-csharp[ProjectN#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/array1.cs#3)]  
  
 Pokud nejsou k dispozici žádná metadata pole, výsledkem je následující chyba:  
  
```output
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.Class1[]  
  
Unfortunately, no further information is available.  
```  
  
 `Browse`metadata pro typ pole je nutné dynamicky konstanci.  Následující direktiva runtime `Class1[]`umožňuje dynamickou instanciaci .  
  
```xml  
<Type Name="App1.Class1[]" Browse="Required Public" />  
```  
  
## <a name="see-also"></a>Viz také

- [Začínáme](getting-started-with-net-native.md)
- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
