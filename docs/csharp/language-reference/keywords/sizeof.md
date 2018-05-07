---
title: sizeof (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: 83038255160ec778c71120566cf8f99092761add
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="sizeof-c-reference"></a>sizeof (Referenční dokumentace jazyka C#)
Umožňuje získat velikost v bajtech pro typ nespravované. Nespravované typy patří vestavěné typy, které jsou uvedeny v následující tabulce a také následující:  
  
-   Typy výčtu  
  
-   Typy ukazatelů  
  
-   Uživatelem definované struktury, které neobsahují žádná pole nebo vlastnosti, které jsou odkazové typy  
  
 Následující příklad ukazuje, jak načíst velikost `int`:  
  
```csharp  
// Constant value 4:  
int intSize = sizeof(int);   
```  
  
## <a name="remarks"></a>Poznámky  
 Počínaje verzí 2.0 jazyka C#, použití `sizeof` na předdefinované typy už vyžaduje, aby [unsafe](../../../csharp/language-reference/keywords/unsafe.md) režim použít.  
  
 `sizeof` Operátor nemohou být přetíženy. Hodnoty vrácené `sizeof` operátor jsou typu `int`. V následující tabulce jsou konstantní hodnoty, které jsou nahrazeny pro `sizeof` výrazy, které mají určité vestavěné typy jako operandy.  
  
|Výraz|Konstantní hodnota|  
|----------------|--------------------|  
|`sizeof(sbyte)`|1|  
|`sizeof(byte)`|1|  
|`sizeof(short)`|2|  
|`sizeof(ushort)`|2|  
|`sizeof(int)`|4|  
|`sizeof(uint)`|4|  
|`sizeof(long)`|8|  
|`sizeof(ulong)`|8|  
|`sizeof(char)`|2 (Unicode)|  
|`sizeof(float)`|4|  
|`sizeof(double)`|8|  
|`sizeof(decimal)`|16|  
|`sizeof(bool)`|1|  
  
 Pro všechny ostatní typy, včetně struktur, `sizeof` operátor lze použít pouze v blocích nezabezpečený kód. Přestože je možné použít <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> metoda, hodnota vrácená touto metodou není vždy stejná jako hodnota vrácený `sizeof`. <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> Vrátí velikost po typ byl zařazen, zatímco `sizeof` vrátí velikost, protože byla přidělena modul common language runtime, včetně všech odsazení.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csrefKeywordsOperator#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/sizeof_1.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Klíčová slova operátorů](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [enum](../../../csharp/language-reference/keywords/enum.md)  
 [Nebezpečný kód a ukazatele](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [Struktury](../../../csharp/programming-guide/classes-and-structs/structs.md)  
 [Konstanty](../../../csharp/programming-guide/classes-and-structs/constants.md)
