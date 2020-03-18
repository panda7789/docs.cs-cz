---
title: Kovariance a kontravariance (C#)
ms.date: 07/20/2015
ms.assetid: 066d9a3c-aab7-4ea6-826d-0b1a85399c74
ms.openlocfilehash: 80b4d703bb88d0bf1f7f48236c21b7698017e7f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79169867"
---
# <a name="covariance-and-contravariance-c"></a>Kovariance a kontravariance (C#)
V C#, kovariance a contravariance povolit implicitní převod odkazu pro typy polí, typy delegátů a argumenty obecného typu. Kovariance zachovává kompatibilitu přiřazení a kontravariance ji obrátí.  
  
 Následující kód ukazuje rozdíl mezi kompatibilitou přiřazení, kovariance a kontravariance.  
  
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
  
 Kovariance pro pole umožňuje implicitní převod pole více odvozeného typu na pole méně odvozeného typu. Ale tato operace není typ bezpečné, jak je znázorněno v následujícím příkladu kódu.  
  
```csharp  
object[] array = new String[10];  
// The following statement produces a run-time exception.  
// array[0] = 10;  
```  
  
 Kovariance a podpora kontravariance pro skupiny metod umožňuje odpovídající podpisy metod s typy delegátů. To umožňuje přiřadit delegátům nejen metody, které mají odpovídající podpisy, ale také metody, které vracejí více odvozených typů (kovariance) nebo které přijímají parametry, které mají méně odvozených typů (kontravariance) než ty, které jsou určeny typem delegáta. Další informace naleznete [v tématech Odchylka v delegátech (C#)](./variance-in-delegates.md) a [Použití odchylky v delegátech (C#)](./using-variance-in-delegates.md).  
  
 Následující příklad kódu ukazuje kovariance a contravariance podporu pro skupiny metod.  
  
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
  
 V rozhraní .NET Framework 4 nebo novější C# podporuje kovariance a contravariance v obecných rozhraních a delegáty a umožňuje implicitní převod parametrů obecného typu. Další informace naleznete [v tématu Odchylka v obecných rozhraních (C#)](./variance-in-generic-interfaces.md) a [Odchylka v delegátech (C#)](./variance-in-delegates.md).  
  
 Následující příklad kódu ukazuje implicitní převod odkazu pro obecná rozhraní.  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 Obecné rozhraní nebo delegát se nazývá *varianta,* pokud jsou jeho obecné parametry deklarovány kovariantní nebo kontravariantní. C# umožňuje vytvořit vlastní variantní rozhraní a delegáty. Další informace naleznete [v tématu Vytváření variantních obecných rozhraní (C#)](./creating-variant-generic-interfaces.md) a [odchylky v delegátech (C#).](./variance-in-delegates.md)  
  
## <a name="related-topics"></a>Související témata  
  
|Nadpis|Popis|  
|-----------|-----------------|  
|[Odchylka v obecných rozhraních (C#)](./variance-in-generic-interfaces.md)|Popisuje kovariance a kontravariance v obecných rozhraních a poskytuje seznam variant obecných rozhraní v rozhraní .NET Framework.|  
|[Vytváření variantních obecných rozhraní (C#)](./creating-variant-generic-interfaces.md)|Ukazuje, jak vytvořit vlastní variantní rozhraní.|  
|[Použití odchylky v rozhraních pro obecné kolekce (C#)](./using-variance-in-interfaces-for-generic-collections.md)|Ukazuje, jak kovariance a contravariance podpora v <xref:System.Collections.Generic.IEnumerable%601> a <xref:System.IComparable%601> rozhraní vám může pomoci znovu použít kód.|  
|[Odchylka v delegátech (C#)](./variance-in-delegates.md)|Popisuje kovariance a kontravariance v obecné a neobecné delegáty a poskytuje seznam variant obecných delegátů v rozhraní .NET Framework.|  
|[Použití odchylky v delegátech (C#)](./using-variance-in-delegates.md)|Ukazuje, jak používat kovariance a kontravariance podporu v neobecných delegátů k sladění podpisy metody s typy delegátů.|  
|[Použití odchylky pro obecné delegáty aplikace Func a obecné akce (C#)](./using-variance-for-func-and-action-generic-delegates.md)|Ukazuje, jak kovariance a contravariance podpora v `Func` a `Action` delegáti vám může pomoci znovu použít kód.|
