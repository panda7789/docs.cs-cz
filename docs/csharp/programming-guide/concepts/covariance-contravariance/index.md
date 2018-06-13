---
title: Kovariance a kontravariance (C#)
ms.date: 07/20/2015
ms.assetid: 066d9a3c-aab7-4ea6-826d-0b1a85399c74
ms.openlocfilehash: bfd78b1a32b9d4fe11b1dce129c24ceb5aca6754
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334084"
---
# <a name="covariance-and-contravariance-c"></a>Kovariance a kontravariance (C#)
Kovariance a kontravariance povolit v jazyce C#, implicitní převod odkazu pro typy polí, typy delegáta a argumenty obecného typu. Kovariance zachovává kompatibility přiřazení a kontravariance obrátí ho.  
  
 Následující kód ukazuje rozdíl mezi kompatibility přiřazení, kovariance a kontravariance.  
  
```csharp  
// Assignment compatibility.   
string str = "test";  
// An object of a more derived type is assigned to an object of a less derived type.   
object obj = str;  
  
// Covariance.   
IEnumerable<string> strings = new List<string>();  
// An object that is instantiated with a more derived type argument   
// is assigned to an object instantiated with a less derived type argument.   
// Assignment compatibility is preserved.   
IEnumerable<object> objects = strings;  
  
// Contravariance.             
// Assume that the following method is in the class:   
// static void SetObject(object o) { }   
Action<object> actObject = SetObject;  
// An object that is instantiated with a less derived type argument   
// is assigned to an object instantiated with a more derived type argument.   
// Assignment compatibility is reversed.   
Action<string> actString = actObject;  
```  
  
 Kovariance pro pole umožňuje implicitní převod pole více odvozeného typu do pole méně odvozeného typu. Ale tato operace není typově bezpečný, jak je znázorněno v následujícím příkladu kódu.  
  
```csharp  
object[] array = new String[10];  
// The following statement produces a run-time exception.  
// array[0] = 10;  
```  
  
 Kovariance a kontravariance podpora pro metodu skupiny umožňuje odpovídající metoda podpisy s typy delegáta. To umožňuje přiřadit delegáty nejen metody, které mají odpovídající podpisy, ale také metody, které vracejí, že informace odvozené typy (kovariance) nebo který přijímáte parametry, které mají méně odvozené typy (kontravariance) než je určeno typ delegáta. Další informace najdete v tématu [odchylky v delegátech (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) a [použití odchylky v delegátech (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).  
  
 Následující příklad kódu ukazuje, že kovariance a kontravariance podpora pro metodu skupiny.  
  
```csharp  
static object GetObject() { return null; }  
static void SetObject(object obj) { }  
  
static string GetString() { return ""; }  
static void SetString(string str) { }  
  
static void Test()  
{  
    // Covariance. A delegate specifies a return type as object,  
    // but you can assign a method that returns a string.  
    Func<object> del = GetString;  
  
    // Contravariance. A delegate specifies a parameter type as string,  
    // but you can assign a method that takes an object.  
    Action<string> del2 = SetObject;  
}  
```  
  
 V rozhraní .NET Framework 4 nebo novější C# podporuje kovariance a kontravariance v obecných rozhraní a delegátů a umožňuje implicitní převod parametry obecného typu. Další informace najdete v tématu [odchylky obecných rozhraní (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) a [odchylky v delegátech (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).  
  
 Následující příklad kódu ukazuje implicitní převod odkazu pro obecná rozhraní.  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 Obecná rozhraní nebo delegáta nazývá *variant* pokud jeho obecné parametry jsou deklarovány kovariantní nebo kontravariant. C# umožňuje vytvářet vlastní variantních rozhraní a delegáti. Další informace najdete v tématu [vytváření variantních obecných rozhraní (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) a [odchylky v delegátech (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Odchylky obecných rozhraní (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)|Popisuje kovariance a kontravariance v obecných rozhraní a poskytuje seznam variantních obecných rozhraní v rozhraní .NET Framework.|  
|[Vytváření variantních obecných rozhraní (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)|Ukazuje, jak vytvořit vlastní variant rozhraní.|  
|[Použití odchylky v rozhraní pro obecné kolekce (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)|Ukazuje, jak podporují kovariance a kontravariance v <xref:System.Collections.Generic.IEnumerable%601> a <xref:System.IComparable%601> rozhraní umožňují opakované použití kódu.|  
|[Odchylky v delegátech (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)|Popisuje kovariance a kontravariance v obecných a neobecnou Delegáti a obsahuje seznam variant obecní delegáti v rozhraní .NET Framework.|  
|[Použití odchylek v delegátech (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)|Ukazuje, jak používat podporu kovariance a kontravariance v delegátech neobecnou tak, aby odpovídaly metoda podpisy s typy delegáta.|  
|[Použití odchylek pro Func a akce obecní delegáti (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)|Ukazuje, jak podporují kovariance a kontravariance v `Func` a `Action` Delegáti umožňují opakované použití kódu.|
