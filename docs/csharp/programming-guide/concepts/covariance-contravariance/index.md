---
title: Kovariance a kontravariance (C#)
ms.date: 07/20/2015
ms.assetid: 066d9a3c-aab7-4ea6-826d-0b1a85399c74
ms.openlocfilehash: bfd78b1a32b9d4fe11b1dce129c24ceb5aca6754
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61668559"
---
# <a name="covariance-and-contravariance-c"></a>Kovariance a kontravariance (C#)
V C#, kovariance a kontravariance povolit implicitní převod odkazu pro typy polí, typy delegátů a argumenty obecného typu. Kompatibility přiřazení zachová kovariance a kontravariance obrátí ho.  
  
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
  
 Kovariance polí umožňuje implicitní převod pole více odvozeného typu na celou řadu méně odvozeného typu. Ale tato operace není typově bezpečný, jak je znázorněno v následujícím příkladu kódu.  
  
```csharp  
object[] array = new String[10];  
// The following statement produces a run-time exception.  
// array[0] = 10;  
```  
  
 Kovariance a kontravariance podpora pro metodu skupiny umožňuje, aby pro spárování metod podpisů s typy delegáta. To umožňuje přiřadit delegáty pouze metody, které mají odpovídající podpisy, ale také metody, které vracejí, že více odvozené typy (kovariance) nebo které přijímáte parametry, které mají méně odvozené typy (kontravariance), než je určeno typ delegáta. Další informace najdete v tématu [odchylky v delegátech (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) a [použití odchylky v delegátech (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).  
  
 Následující příklad kódu ukazuje kovariance a kontravariance podporu pro skupiny metod.  
  
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
  
 V rozhraní .NET Framework 4 nebo novější C# podporuje kovariance a kontravariance v obecných rozhraních a delegátech a umožňuje implicitní převod parametrů obecného typu. Další informace najdete v tématu [odchylky obecných rozhraní (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) a [odchylky v delegátech (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).  
  
 Následující příklad kódu ukazuje implicitní referenční převod pro obecná rozhraní.  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 Obecná rozhraní nebo delegát se nazývá *variant* pokud jeho obecné parametry jsou deklarovány kovariantní nebo kontravariantní. C#umožňuje vytvářet vlastní variant rozhraní a delegátů. Další informace najdete v tématu [vytváření variantních obecných rozhraní (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) a [odchylky v delegátech (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Odchylky obecných rozhraní (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)|Tento článek popisuje kovariance a kontravariance v obecných rozhraních a obsahuje seznam variantních obecných rozhraní v rozhraní .NET Framework.|  
|[Vytváření variantních obecných rozhraní (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)|Ukazuje, jak vytvořit vlastní rozhraní variant.|  
|[Použití odchylky v rozhraní pro obecné kolekce (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)|Ukazuje, jak podporovat kovariance a kontravariance v <xref:System.Collections.Generic.IEnumerable%601> a <xref:System.IComparable%601> rozhraní vám umožňují opětovné použití kódu.|  
|[Odchylky v delegátech (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)|Tento článek popisuje kovariance a kontravariance v obecných a neobecných delegátů a obsahuje seznam variantních obecných delegátů v rozhraní .NET Framework.|  
|[Použití odchylek v delegátech (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)|Ukazuje, jak používat podporu kovariance a kontravariance v obecné delegáty tak, aby odpovídaly metod podpisů s typy delegáta.|  
|[Použití odchylek pro delegáty Func a Action obecný (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)|Ukazuje, jak podporovat kovariance a kontravariance v `Func` a `Action` delegáty umožňují opakované použití kódu.|
