---
title: Uživatelský datový typ (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- UserDefined
- UDT
- vb.UDT
- User-Defined
- vb.UserDefined
- vb.User-Defined
helpviewer_keywords:
- user-defined data types [Visual Basic], Visual Basic
- user-defined types
- structures [Visual Basic], as user-defined data types
- user-defined types [Visual Basic], Visual Basic
- user-defined types [Visual Basic], structure declaration
- user-defined types [Visual Basic], structures in Visual Basic
- user-defined data types [Visual Basic], structure declaration
- data types [Visual Basic], assigning
- Structure statement [Visual Basic]
- data types [Visual Basic], user-defined
- user-defined data types [Visual Basic], structures in Visual Basic
- user-defined data types
- types [Visual Basic], user-defined
ms.assetid: be913dca-a364-4a51-96a1-549a1b390b0a
ms.openlocfilehash: 42aecd0a5d948ab76d7bd11990d4cdbdce611015
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64646953"
---
# <a name="user-defined-data-type"></a>Uživatelský datový typ
Obsahuje data ve formátu, který definujete. `Structure` Prohlášení definuje formát.  
  
 Předchozí verze jazyka Visual Basic podporují uživatelem definovaný typ (UDT). Rozbalí UDT na aktuální verzi *struktura*. Struktura je složen z jednoho nebo více *členy* různých datových typů. Jazyka Visual Basic struktury považuje za jednu jednotku, i když se dá dostat taky jejích členů jednotlivě.  
  
## <a name="remarks"></a>Poznámky  
 Definujte a použijte datový typ struktura, když je nutné sloučit různé datové typy do jedné jednotky, nebo když žádný základní datové typy sloužit vašim potřebám.  
  
 Výchozí hodnota datového typu Struktura se skládá z kombinace výchozí hodnoty všech jejích členů.  
  
## <a name="declaration-format"></a>Formát deklarace  
 Deklarace struktury začíná [Structure – příkaz](../../../visual-basic/language-reference/statements/structure-statement.md) a končí `End Structure` příkaz. `Structure` Příkaz poskytuje název struktury, což je také identifikátor datového typu, který definuje strukturu. Ostatní části kódu můžete použít tento identifikátor pro deklaraci proměnné, parametry a funkce vrátí hodnoty, které mají být tato struktura datového typu.  
  
 Deklarace mezi `Structure` a `End Structure` příkazů definovat členy struktury.  
  
## <a name="member-access-levels"></a>Úrovně přístupu členů  
 Je třeba deklarovat každého člena pomocí [příkazu Dim](../../../visual-basic/language-reference/statements/dim-statement.md) nebo příkaz, který určuje úroveň přístupu, jako například [veřejné](../../../visual-basic/language-reference/modifiers/public.md), [typu Friend](../../../visual-basic/language-reference/modifiers/friend.md), nebo [privátní](../../../visual-basic/language-reference/modifiers/private.md). Pokud používáte `Dim` prohlášení, výchozí úrovně přístupu na veřejnou.  
  
## <a name="programming-tips"></a>Tipy k programování  
  
- **Využití paměti.** Stejně jako u všech složených datových typů nelze bezpečně vypočítat celkovou spotřebu paměti struktury sečtením nominálních přidělení úložiště jejích členů. Kromě toho nelze bezpečně předpokládat, že pořadí úložiště v paměti je stejné jako vaše pořadí prohlášení. Pokud potřebujete řídit rozložení úložiště struktury, můžete použít <xref:System.Runtime.InteropServices.StructLayoutAttribute> atribut `Structure` příkazu.  
  
- **Spolupráce aspekty.** Při vzájemném propojování součástí, které nejsou napsané pro rozhraní .NET Framework, například objekty automatizace nebo COM, mějte na paměti, že v jiných prostředích, uživatelem definované typy nejsou kompatibilní s jazykem Visual Basic struktury typů.  
  
- **Rozšíření.** Neexistuje žádný automatický převod do nebo z libovolného datového typu Struktura. Můžete definovat operátory převodu na váš pomocí struktury [Operator – příkaz](../../../visual-basic/language-reference/statements/operator-statement.md), a deklarujete každý operátor převodu na `Widening` nebo `Narrowing`.  
  
- **Znaky typu.** Struktura datové typy mít žádné – znak typu literálu nebo – znak typu identifikátoru.  
  
- **Typ architektury.** Neexistuje žádný odpovídající typ v rozhraní .NET Framework. Všechny struktury dědí z třídy rozhraní .NET Framework <xref:System.ValueType?displayProperty=nameWithType>, ale žádné jednotlivých struktura odpovídá <xref:System.ValueType?displayProperty=nameWithType>.  
  
## <a name="example"></a>Příklad  
 Následující paradigma ukazuje obrys deklaraci struktury.  
  
```  
[Public | Protected | Friend | Protected Friend | Private] Structure structname  
    {Dim | Public | Friend | Private} member1 As datatype1  
    ' ...  
    {Dim | Public | Friend | Private} memberN As datatypeN  
End Structure  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ValueType>
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- [Datové typy](../../../visual-basic/language-reference/data-types/index.md)
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Widening](../../../visual-basic/language-reference/modifiers/widening.md)
- [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
