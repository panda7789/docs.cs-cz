---
title: Kovariance a kontravariance (C#)
ms.date: 07/20/2015
ms.assetid: 066d9a3c-aab7-4ea6-826d-0b1a85399c74
ms.openlocfilehash: 1d5a1de1825e585512f694a0cd72cee9b37cda36
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595283"
---
# <a name="covariance-and-contravariance-c"></a>Kovariance a kontravariance (C#)
V C#, kovariance a kontravariance umožňují implicitní převod odkazů pro typy polí, typy delegátů a argumenty obecného typu. Kovariance zachovává kompatibilitu přiřazení a kontravariance ji obrátí.  
  
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
  
 Kovariance a podpora kontravariance pro skupiny metod umožňuje porovnávací signatury metod s typy delegátů. To vám umožňuje přiřadit delegáty nejen metody, které mají odpovídající signatury, ale také metody, které vracejí více odvozené typy (kovariance), nebo které přijímají parametry, které mají méně odvozené typy (kontravariance), než je určeno typem delegáta. Další informace naleznete v tématu [Variance in DelegatesC#()](./variance-in-delegates.md) a [using Variance in Delegates (C#)](./using-variance-in-delegates.md).  
  
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
  
 V .NET Framework 4 nebo novější C# podporuje kovarianci a kontravariance v obecných rozhraních a delegátech a povoluje implicitní převod parametrů obecného typu. Další informace naleznete v tématu [Variance in Generic Interfaces (C#)](./variance-in-generic-interfaces.md) a [Variance in DelegatesC#()](./variance-in-delegates.md).  
  
 Následující příklad kódu ukazuje implicitní převod odkazu pro Obecná rozhraní.  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 Obecné rozhraní nebo delegát se nazývá *typ variant* , pokud jsou jeho obecné parametry deklarovány kovariantní nebo kontravariantní. C#umožňuje vytvořit vlastní variantní rozhraní a delegáty. Další informace najdete v tématu [Vytvoření variantních obecných rozhraníC#()](./creating-variant-generic-interfaces.md) a [Variance v delegátech (C#)](./variance-in-delegates.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Variance v obecných rozhraníchC#()](./variance-in-generic-interfaces.md)|Popisuje kovarianci a kontravariance v obecných rozhraních a poskytuje seznam variantních obecných rozhraní v .NET Framework.|  
|[Vytváření variantních obecných rozhraníC#()](./creating-variant-generic-interfaces.md)|Ukazuje, jak vytvořit vlastní variantní rozhraní.|  
|[Použití variance v rozhraních pro obecné kolekceC#()](./using-variance-in-interfaces-for-generic-collections.md)|Ukazuje, jak se podpora kovariance a kontravariance <xref:System.Collections.Generic.IEnumerable%601> v <xref:System.IComparable%601> rozhraních a může pomoci znovu použít kód.|  
|[Variance v delegátechC#()](./variance-in-delegates.md)|Popisuje kovarianci a kontravariance v obecných a neobecných delegátech a poskytuje seznam variant obecných delegátů v .NET Framework.|  
|[Použití variance v delegátechC#()](./using-variance-in-delegates.md)|Ukazuje, jak použít kovarianci a podporu kontravariance v neobecných delegátech pro porovnávání signatur metod s typy delegátů.|  
|[Použití odchylky pro obecné delegáty Func a ActionC#()](./using-variance-for-func-and-action-generic-delegates.md)|Ukazuje, jak se podpora kovariance a kontravariance `Func` v `Action` delegátech a může pomoci znovu použít kód.|
