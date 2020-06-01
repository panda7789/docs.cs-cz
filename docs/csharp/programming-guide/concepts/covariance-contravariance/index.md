---
title: Kovariance a kontravariance (C#)
ms.date: 07/20/2015
ms.assetid: 066d9a3c-aab7-4ea6-826d-0b1a85399c74
ms.openlocfilehash: 23633675059b9c295dda7ddf3d78754c0223f5f8
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241367"
---
# <a name="covariance-and-contravariance-c"></a>Kovariance a kontravariance (C#)
V jazyce C# umožňuje kovariance a kontravariance implicitní převod odkazů pro typy polí, typy delegátů a argumenty obecného typu. Kovariance zachovává kompatibilitu přiřazení a kontravariance ji obrátí.  
  
 Následující kód ukazuje rozdíl mezi kompatibilitou přiřazení, koodchylky a kontravariance.  
  
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
  
 Kovariance pro pole umožňuje implicitní převod pole více odvozeného typu na pole méně odvozeného typu. Tato operace ale není typově bezpečná, jak je znázorněno v následujícím příkladu kódu.  
  
```csharp  
object[] array = new String[10];  
// The following statement produces a run-time exception.  
// array[0] = 10;  
```  
  
 Kovariance a podpora kontravariance pro skupiny metod umožňuje porovnávací signatury metod s typy delegátů. To vám umožňuje přiřadit delegáty nejen metody, které mají odpovídající signatury, ale také metody, které vracejí více odvozené typy (kovariance), nebo které přijímají parametry, které mají méně odvozené typy (kontravariance), než je určeno typem delegáta. Další informace naleznete v tématech [Variance v delegátech (c#)](./variance-in-delegates.md) a [použití variance v delegátech (c#)](./using-variance-in-delegates.md).  
  
 Následující příklad kódu ukazuje kovariance a podporu kontravariance pro skupiny metod.  
  
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
  
 V .NET Framework 4 a novějších verzích C# podporuje kovarianci a kontravariance v obecných rozhraních a delegátech a povoluje implicitní převod parametrů obecného typu. Další informace najdete v tématech [Variance v obecných rozhraních (c#)](./variance-in-generic-interfaces.md) a [Variance v delegátech (c#)](./variance-in-delegates.md).  
  
 Následující příklad kódu ukazuje implicitní převod odkazu pro Obecná rozhraní.  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 Obecné rozhraní nebo delegát se nazývá *typ variant* , pokud jsou jeho obecné parametry deklarovány kovariantní nebo kontravariantní. Jazyk C# umožňuje vytvářet vlastní variantní rozhraní a delegáty. Další informace naleznete v tématu [vytváření variant obecných rozhraní (c#)](./creating-variant-generic-interfaces.md) a [Variance v delegátech (c#)](./variance-in-delegates.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Nadpis|Popis|  
|-----------|-----------------|  
|[Variance v obecných rozhraních (C#)](./variance-in-generic-interfaces.md)|Popisuje kovarianci a kontravariance v obecných rozhraních a poskytuje seznam variantních obecných rozhraní v .NET Framework.|  
|[Vytváření variantních obecných rozhraní (C#)](./creating-variant-generic-interfaces.md)|Ukazuje, jak vytvořit vlastní variantní rozhraní.|  
|[Použití variance v rozhraních pro obecné kolekce (C#)](./using-variance-in-interfaces-for-generic-collections.md)|Ukazuje, jak se podpora kovariance a kontravariance <xref:System.Collections.Generic.IEnumerable%601> v <xref:System.IComparable%601> rozhraních a může pomoci znovu použít kód.|  
|[Variance v delegátech (C#)](./variance-in-delegates.md)|Popisuje kovarianci a kontravariance v obecných a neobecných delegátech a poskytuje seznam variant obecných delegátů v .NET Framework.|  
|[Použití variance v delegátech (C#)](./using-variance-in-delegates.md)|Ukazuje, jak použít kovarianci a podporu kontravariance v neobecných delegátech pro porovnávání signatur metod s typy delegátů.|  
|[Použití odchylky pro obecné delegáty Func a Action (C#)](./using-variance-for-func-and-action-generic-delegates.md)|Ukazuje, jak se podpora kovariance a kontravariance `Func` v `Action` delegátech a může pomoci znovu použít kód.|
