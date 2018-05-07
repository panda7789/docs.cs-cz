---
title: Zabalení typů s povolenou hodnotou Null (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- boxing [C#], nullable types
- unboxing [C#], nullable types
- nullable types [C#], boxing and unboxing
ms.assetid: bdb5b626-abc0-405d-8f64-0f0a0bf883a4
ms.openlocfilehash: e2c7602bf45f1861d3a32a73824e9fedf0a4d29d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="boxing-nullable-types-c-programming-guide"></a>Zabalení typů s povolenou hodnotou Null (Průvodce programováním v C#)
Objekty na základě typů s povolenou hodnotou Null se do pouze pole, pokud se objekt nesmí být nulová. Pokud <xref:System.Nullable%601.HasValue%2A> je `false`, odkaz na objekt je přiřazena k `null` místo zabalení. Příklad:  
  
```csharp  
bool? b = null;  
object o = b;  
// Now o is null.  
```  
  
 Pokud se objekt jinou hodnotu než null – Pokud <xref:System.Nullable%601.HasValue%2A> je `true` – pak zabalení dojde, ale jenom základní typ, který je na základě objekt s možnou hodnotou null je zabalená. Zabalení typ s možnou hodnotou Null hodnotu než null oknech samostatně, typ hodnoty není <xref:System.Nullable%601?displayProperty=nameWithType> který zabalí typ hodnoty. Příklad:  
  
```csharp  
bool? b = false;  
int? i = 44;  
object bBoxed = b; // bBoxed contains a boxed bool.  
object iBoxed = i; // iBoxed contains a boxed int.  
```  
  
 Dva zabalené objekty jsou stejné jako ty vytvořené zabalení typů hodnotu Null. A, stejně jako použití hodnot Null pevně určené typy, může se jednat o nezabalený na typy s možnou hodnotou Null, jako v následujícím příkladu:  
  
```csharp  
bool? b2 = (bool?)bBoxed;  
int? i2 = (int?)iBoxed;  
```  
  
## <a name="remarks"></a>Poznámky  
 Chování typy s možnou hodnotou Null, pokud do pole nabízí dvě výhody:  
  
1.  Null lze testovat s možnou hodnotou Null objekty a jejich zabalené protějšku:  
  
    ```csharp  
    bool? b = null;  
    object boxedB = b;  
    if (b == null)  
    {  
      // True.  
    }  
    if (boxedB == null)  
    {  
      // Also true.  
    }  
    ```  
  
2.  Pevně určené typy s možnou hodnotou Null plně podporují funkce základní typ:  
  
    ```csharp  
    double? d = 44.4;  
    object iBoxed = d;  
    // Access IConvertible interface implemented by double.  
    IConvertible ic = (IConvertible)iBoxed;  
    int i = ic.ToInt32(null);  
    string str = ic.ToString();  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Typy s povolenou hodnotou Null](../../../csharp/programming-guide/nullable-types/index.md)  
 [Postupy: Identifikace typu s povolenou hodnotou Null](../../../csharp/programming-guide/nullable-types/how-to-identify-a-nullable-type.md)
