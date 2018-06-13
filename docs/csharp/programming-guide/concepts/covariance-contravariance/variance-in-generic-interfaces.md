---
title: Odchylky obecných rozhraní (C#)
ms.date: 07/20/2015
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
ms.openlocfilehash: fdcfd13a645ffc9b596beed65b74f8e593c642f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33326755"
---
# <a name="variance-in-generic-interfaces-c"></a>Odchylky obecných rozhraní (C#)
Rozhraní .NET framework 4 zavedly odchylku podporu pro několik existujících obecných rozhraní. Podpora odchylku umožňuje implicitní převod tříd, které implementují tato rozhraní. Následující rozhraní jsou nyní variant:  
  
-   <xref:System.Collections.Generic.IEnumerable%601> (T je kovariant)  
  
-   <xref:System.Collections.Generic.IEnumerator%601> (T je kovariant)  
  
-   <xref:System.Linq.IQueryable%601> (T je kovariant)  
  
-   <xref:System.Linq.IGrouping%602> (`TKey` a `TElement` jsou kovariantní)  
  
-   <xref:System.Collections.Generic.IComparer%601> (T je kontravariant)  
  
-   <xref:System.Collections.Generic.IEqualityComparer%601> (T je kontravariant)  
  
-   <xref:System.IComparable%601> (T je kontravariant)  
  
 Kovariance umožňuje metodu tak, aby měl více odvozené návratový typ než definované parametr obecného typu rozhraní. Pro ilustraci funkci kovariance, zvažte tyto obecná rozhraní: `IEnumerable<Object>` a `IEnumerable<String>`. `IEnumerable<String>` Rozhraní nedědí `IEnumerable<Object>` rozhraní. Ale `String` typ dědit vlastnosti `Object` typ a v některých případech můžete chtít přiřazovat objekty z těchto rozhraní k sobě navzájem. To je znázorněno v následujícím příkladu kódu.  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 V dřívějších verzích rozhraní .NET Framework, tento kód způsobí chybu kompilace v jazyce C# s `Option Strict On`. Teď můžete použít, ale `strings` místo `objects`, jak ukazuje předchozí příklad, protože <xref:System.Collections.Generic.IEnumerable%601> rozhraní je kovariant.  
  
 Kontravariance umožňuje metodu tak, aby měl typy argumentů, které jsou odvozené menší než je určeno obecný parametr rozhraní. Pro ilustraci kontravariance, předpokládá, že jste vytvořili `BaseComparer` třída k porovnání instance `BaseClass` třídy. `BaseComparer` Třída implementuje `IEqualityComparer<BaseClass>` rozhraní. Protože <xref:System.Collections.Generic.IEqualityComparer%601> rozhraní je nyní kontravariant, můžete použít `BaseComparer` k porovnání instance tříd, které dědí `BaseClass` třídy. To je znázorněno v následujícím příkladu kódu.  
  
```csharp  
// Simple hierarchy of classes.  
class BaseClass { }  
class DerivedClass : BaseClass { }  
  
// Comparer class.  
class BaseComparer : IEqualityComparer<BaseClass>   
{  
    public int GetHashCode(BaseClass baseInstance)  
    {  
        return baseInstance.GetHashCode();  
    }  
    public bool Equals(BaseClass x, BaseClass y)  
    {  
        return x == y;  
    }  
}  
class Program  
{  
    static void Test()  
    {  
        IEqualityComparer<BaseClass> baseComparer = new BaseComparer();  
  
        // Implicit conversion of IEqualityComparer<BaseClass> to   
        // IEqualityComparer<DerivedClass>.  
        IEqualityComparer<DerivedClass> childComparer = baseComparer;  
    }  
}  
```  
  
 Další příklady najdete v tématu [použití odchylky v rozhraní pro obecné kolekce (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).  
  
 Odchylky obecných rozhraní je podporována pro odkazové typy pouze. Typy hodnot nepodporují odchylky. Například `IEnumerable<int>` nelze implicitně převést na `IEnumerable<object>`, protože celých čísel jsou reprezentované pomocí typ hodnoty.  
  
```csharp  
IEnumerable<int> integers = new List<int>();  
// The following statement generates a compiler errror,  
// because int is a value type.  
// IEnumerable<Object> objects = integers;  
```  
  
 Je také důležité Pamatujte, že jsou stále invariantní třídy, které implementují rozhraní variant. Například i když <xref:System.Collections.Generic.List%601> implementuje rozhraní kovariantní <xref:System.Collections.Generic.IEnumerable%601>, nelze implicitně převést `List<Object>` k `List<String>`. To je znázorněno v následujícím příkladu kódu.  
  
```csharp  
// The following line generates a compiler error  
// because classes are invariant.  
// List<Object> list = new List<String>();  
  
// You can use the interface object instead.  
IEnumerable<Object> listObjects = new List<String>();  
```  
  
## <a name="see-also"></a>Viz také  
 [Použití odchylky v rozhraní pro obecné kolekce (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)  
 [Vytváření variantních obecných rozhraní (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)  
 [Obecná rozhraní](../../../../standard/generics/interfaces.md)  
 [Odchylky v delegátech (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
