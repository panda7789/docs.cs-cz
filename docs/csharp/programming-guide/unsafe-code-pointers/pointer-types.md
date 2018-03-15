---
title: "Typy ukazatelů (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.assetid: 3319faf9-336d-4148-9af2-1da2579cdd1e
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fe7b926bdf9f662d25f2fe960b51fc8254b7aa3a
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2018
---
# <a name="pointer-types-c-programming-guide"></a>Typy ukazatelů (Průvodce programováním v C#)
V nezabezpečeném kontextu lze jako konkrétní typ použít typ ukazatele, typ hodnoty nebo typ odkazu. Deklarace typu ukazatele má jednu z následujících forem:  
  
```  
type* identifier;  
void* identifier; //allowed but not recommended  
```  
  
 Typem ukazatele může být jakýkoli z následujících typů:  
  
-   [SByte –](../../../csharp/language-reference/keywords/sbyte.md), [bajtů](../../../csharp/language-reference/keywords/byte.md), [krátké](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [Celé_číslo](../../../csharp/language-reference/keywords/uint.md), [ dlouhé](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [char](../../../csharp/language-reference/keywords/char.md), [float](../../../csharp/language-reference/keywords/float.md), [dvojité](../../../csharp/language-reference/keywords/double.md), [decimal](../../../csharp/language-reference/keywords/decimal.md), nebo [bool](../../../csharp/language-reference/keywords/bool.md).  
  
-   Všechny [výčtu](../../../csharp/language-reference/keywords/enum.md) typu.  
  
-   Jakýkoli typ ukazatele.  
  
-   Jakýkoli typ struktury definované uživatelem, který obsahuje pouze pole nespravovaných typů.  
  
 Typy ukazatelů nedědí z [objekt](../../../csharp/language-reference/keywords/object.md) a neexistují žádné převody mezi typy ukazatelů a `object`. Dále není pro ukazatele k dispozici podpora zabalení a rozbalení. Můžete však převádět mezi různými typy ukazatele, nebo mezi různými typy ukazatele a integrálními typy.  
  
 Při deklaraci většího počtu ukazatelů ve stejné deklaraci je spolu se základním typem zapsán pouze symbol hvězdičky (*). Nepoužívá se jako předpona u názvů jednotlivých ukazatelů. Příklad:  
  
```  
int* p1, p2, p3;   // Ok  
int *p1, *p2, *p3;   // Invalid in C#  
```  
  
 Ukazatel nemůže odkazovat na odkaz nebo na [struktura](../../../csharp/language-reference/keywords/struct.md) obsahující odkazy, protože odkaz na objekt může být uvolnění z paměti i v případě, že ukazatel ukazovat na ni. Systém uvolňování paměti neukládá přehled o tom, zda na konkrétní objekt neodkazují některé typy ukazatele.  
  
 Hodnoty proměnné ukazatele typu `myType*` je adresa proměnné typu `myType`. Následují příklady deklarace typu ukazatele:  
  
|Příklad|Popis|  
|-------------|-----------------|  
|`int* p`|`p` je zde ukazatel na celé číslo.|  
|`int** p`|`p` je zde ukazatel na ukazatel na celé číslo.|  
|`int*[] p`|`p` je jednorozměrná pole ukazatele na celá čísla.|  
|`char* p`|`p` je zde ukazatel na char.|  
|`void* p`|`p` je zde ukazatel na neznámého typu.|  
  
 Operátor dereference ukazatele * lze použít pro přístup k obsahu v umístění, na které odkazuje proměnná ukazatele. Předpokládejme například následující deklaraci:  
  
```  
int* myVariable;  
```  
  
 Výraz `*myVariable` označuje `int` proměnná najít na adrese obsažené v `myVariable`.  
  
 Existuje několik příkladů ukazatele v tématech [příkazu pevnou](../../../csharp/language-reference/keywords/fixed-statement.md) a [převody ukazatele](../../../csharp/programming-guide/unsafe-code-pointers/pointer-conversions.md).  Následující příklad ukazuje potřebu `unsafe` – klíčové slovo a `fixed` příkaz a jak se zvýší vnitřní ukazatel.  Tento kód spustíte vložením do funkce Main konzolové aplikace. (Nezapomeňte povolit nezabezpečený kód v **Návrhář projektu**; zvolte **projektu**, **vlastnosti** v nabídce panelu a pak vyberte **povolit nezabezpečený kód** v **sestavení** karta.)  
  
```  
// Normal pointer to an object.  
int[] a = new int[5] {10, 20, 30, 40, 50};  
// Must be in unsafe code to use interior pointers.  
unsafe  
{  
    // Must pin object on heap so that it doesn't move while using interior pointers.  
    fixed (int* p = &a[0])  
    {  
        // p is pinned as well as object, so create another pointer to show incrementing it.  
        int* p2 = p;  
        Console.WriteLine(*p2);  
        // Incrementing p2 bumps the pointer by four bytes due to its type ...  
        p2 += 1;  
        Console.WriteLine(*p2);  
        p2 += 1;  
        Console.WriteLine(*p2);  
        Console.WriteLine("--------");  
        Console.WriteLine(*p);  
        // Deferencing p and incrementing changes the value of a[0] ...  
        *p += 1;  
        Console.WriteLine(*p);  
        *p += 1;  
        Console.WriteLine(*p);  
    }  
}  
  
Console.WriteLine("--------");  
Console.WriteLine(a[0]);  
Console.ReadLine();  
  
// Output:  
//10  
//20  
//30  
//--------  
//10  
//11  
//12  
//--------  
//12  
```  
  
 Deferenční operátor nelze použít pro ukazatel typu `void*`. Můžete však použít přetypování neplatného ukazatele a převést jej na jiný typ ukazatele, a naopak.  
  
 Může být ukazatel `null`. Použití operátoru dereference na ukazatele null způsobí chování definované implementací.  
  
 Předávání ukazatelů mezi metodami může způsobit nedefinované chování. Vezměte v úvahu metodu, která vrací ukazatel na místní proměnné prostřednictvím `in`, `out` nebo `ref` parametr nebo v důsledku funkce. Pokud byl ukazatel nastaven v pevném bloku, pak proměnná, na kterou odkazuje, již nemusí být pevně stanovená.  
  
 V následující tabulce je uveden seznam operátorů a příkazů, které mohou fungovat u ukazatelů v nezabezpečeném kontextu:  
  
|Operátor/Příkaz|Použití|  
|-------------------------|---------|  
|*|Provádí dereferenci ukazatele.|  
|->|Zpřístupňuje člen struktury prostřednictvím ukazatele.|  
|[]|Indexuje ukazatel.|  
|`&`|Získá adresu proměnné.|  
|++ a --|Zvýší a sníží ukazatele.|  
|+ a -|Provádí aritmetické operace ukazatele.|  
|==,! =, \<, >, \<=, a > =|Porovnává ukazatele.|  
|`stackalloc`|Přidělí paměť v zásobníku.|  
|`fixed` Příkaz|Dočasně pevně stanoví proměnnou tak, aby bylo možné vyhledat její adresu.|  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Nebezpečný kód a ukazatele](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [Převody ukazatele](../../../csharp/programming-guide/unsafe-code-pointers/pointer-conversions.md)  
 [Výrazy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [Typy](../../../csharp/language-reference/keywords/types.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed – příkaz](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)  
 [Zabalení a rozbalení](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
