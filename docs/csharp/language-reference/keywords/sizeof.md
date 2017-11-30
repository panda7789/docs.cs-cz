---
title: "sizeof (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords: sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0148ae8381804ca9286315251582c8ab40778369
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
  
 Pro všechny ostatní typy, včetně struktur, `sizeof` operátor lze použít pouze v blocích nezabezpečený kód. Přestože je možné použít <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> metoda, hodnota vrácená touto metodou není vždy stejná jako hodnota vrácený `sizeof`. <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType>Vrátí velikost po typ byl zařazen, zatímco `sizeof` vrátí velikost, protože byla přidělena modul common language runtime, včetně všech odsazení.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csrefKeywordsOperator#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/sizeof_1.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Klíčová slova operátorů](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [výčet](../../../csharp/language-reference/keywords/enum.md)  
 [Nezabezpečený kód a ukazatele](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [Struktury](../../../csharp/programming-guide/classes-and-structs/structs.md)  
 [Konstanty](../../../csharp/programming-guide/classes-and-structs/constants.md)
