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
# <a name="apis-that-rely-on-reflection"></a>Rozhraní API, která závisí na reflexi
V některých případech použití reflexe v kódu není zřejmé a proto [!INCLUDE[net_native](../../../includes/net-native-md.md)] nástroj řetězu není zachovat metadata, která je vyžadována v době běhu. Toto téma popisuje některé běžné rozhraní API nebo běžných programovací vzorů, které nejsou považovány za součást rozhraní API reflexe, ale který závisí na reflexi proběhl úspěšně. Pokud je používáte ve zdrojovém kódu, můžete přidat informace o nich do direktivy modulu runtime (. rd.xml) tak, aby volání tato rozhraní API nevyvolá výjimku [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) výjimky nebo některých jiných výjimky za běhu.  
  
## <a name="typemakegenerictype-method"></a>Type.MakeGenericType – metoda  
 Můžete vytvořit dynamicky instanci obecného typu `AppClass<T>` voláním <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> metoda pomocí kódu takto:  
  
 [!code-csharp[ProjectN#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/type_makegenerictype1.cs#1)]  
  
 Pro tento kód úspěšné za běhu jsou požadovány několik položek metadat. První je `Browse` metadata pro bez instancí obecného typu `AppClass<T>`:  
  
```xml  
<Type Name="App1.AppClass`1" Browse="Required PublicAndInternal" />  
```  
  
 To umožňuje <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> volání metody úspěšné a vrátíte se platná <xref:System.Type> objektu.  
  
 Ale i v případě, že přidáte metadata pro bez instancí obecného typu, volání <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> metoda vrátí [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) výjimka:  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.AppClass`1<System.Int32>.  
```  
  
 Následující direktiva běhu můžete přidat do souboru direktivy modulu runtime pro přidání `Activate` metadata pro konkrétní instanci přes `AppClass<T>` z <xref:System.Int32?displayProperty=nameWithType>:  
  
```xml  
<TypeInstantiation Name="App1.AppClass" Arguments="System.Int32"   
                   Activate="Required Public" />  
```  
  
 Každý jiný konkretizaci přes `AppClass<T>` vyžaduje samostatné – direktiva, když je vytvořena s <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> metoda a nepoužívá se staticky.  
  
## <a name="methodinfomakegenericmethod-method"></a>MethodInfo.MakeGenericMethod – metoda  
 Zadané třídy `Class1` s Obecná metoda `GetMethod<T>(T t)`, `GetMethod` vyvolat prostřednictvím reflexe pomocí kódu takto:  
  
 [!code-csharp[ProjectN#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/makegenericmethod1.cs#2)]  
  
 K úspěšnému spuštění tohoto kódu vyžaduje několik položek metadat:  
  
-   `Browse` metadata pro typ jehož metoda, kterou chcete volat.  
  
-   `Browse` metadata pro metodu, kterou chcete volat.  Pokud je veřejná metoda, přidáte veřejných `Browse` metadata pro typ obsahující zahrnuje metodu, příliš.  
  
-   Dynamické metadata pro metodu, kterou chcete volat, tak, aby delegát volání reflexe není odebraná pomocí [!INCLUDE[net_native](../../../includes/net-native-md.md)] nástroj řetězu. Pokud chybí dynamické metadata pro metodu, je vyvolána následující výjimka, kdy <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> metoda je volána:  
  
    ```  
    MakeGenericMethod() cannot create this generic method instantiation because the instantiation was not metadata-enabled: 'App1.Class1.GenMethod<Int32>(Int32)'.  
    ```  
  
 Následující direktivy modulu runtime Ujistěte se, že všechny požadované, metadata jsou k dispozici:  
  
```xml  
<Type Name="App1.Class1" Browse="Required PublicAndInternal">  
   <MethodInstantiation Name="GenMethod" Arguments="System.Int32" Dynamic="Required"/>  
</Type>  
```  
  
 A `MethodInstantiation` direktiva je potřebná pro každý jiný konkretizaci metody, která je volána dynamicky, a `Arguments` element aktualizován, aby odrážel všechny argumenty různých vytváření instancí.  
  
## <a name="arraycreateinstance-and-typemaketypearray-methods"></a>Metody Array.CreateInstance a Type.MakeTypeArray  
 Následující příklad volání <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> a <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> metody pro typ `Class1`.  
  
 [!code-csharp[ProjectN#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/array1.cs#3)]  
  
 Pokud je k dispozici žádná metadata pole, vrátí následující chybu:  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.Class1[]  
  
Unfortunately, no further information is available.  
```  
  
 `Browse` metadata pro typ pole je potřeba dynamicky vytvoří instanci.  Následující direktivy modulu runtime umožňuje dynamické vytvořením instance `Class1[]`.  
  
```xml  
<Type Name="App1.Class1[]" Browse="Required Public" />  
```  
  
## <a name="see-also"></a>Viz také  
 [Začínáme](../../../docs/framework/net-native/getting-started-with-net-native.md)  
 [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
