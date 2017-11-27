---
title: "Uživatelský datový typ"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7e1876d61a2ce89b04c6e5061b868f0be365639f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="user-defined-data-type"></a>Uživatelský datový typ
Obsahuje data ve formátu, který definujete. `Structure` Příkaz definuje formát.  
  
 Předchozí verze jazyka Visual Basic podporují uživatelem definovaný typ (UDT). Aktuální verze rozšíří UDT k *struktura*. Struktura je zřetězení jednoho nebo více *členy* různých datových typů. Visual Basic struktura považuje za jedné jednotky, i když je dostupný také její členy jednotlivě.  
  
## <a name="remarks"></a>Poznámky  
 Definice a používání Struktura datový typ, když je nutné sloučit různé typy dat do jedné jednotky, nebo když žádný z základní datové typy slouží vašim potřebám.  
  
 Výchozí hodnota datového typu Struktura se skládá z kombinace výchozí hodnoty jednotlivých její členy.  
  
## <a name="declaration-format"></a>Formát deklarace  
 Deklarace struktury začíná [Structure – příkaz](../../../visual-basic/language-reference/statements/structure-statement.md) a končí `End``Structure` příkaz. `Structure` Příkaz poskytuje název struktury, což je také identifikátor datového typu, který definuje strukturu. Ostatní části kódu můžete použít tento identifikátor proměnné a parametry, funkce vrátí hodnoty, které mají být data typu tuto strukturu deklarovat.  
  
 Deklarace mezi `Structure` a `End``Structure` příkazy definovat členů struktury.  
  
## <a name="member-access-levels"></a>Úrovně přístupu členů  
 Je potřeba deklarovat každý člen pomocí [Dim – příkaz](../../../visual-basic/language-reference/statements/dim-statement.md) nebo příkazu, který určuje úroveň přístupu, jako například [veřejné](../../../visual-basic/language-reference/modifiers/public.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md), nebo [privátní](../../../visual-basic/language-reference/modifiers/private.md). Pokud používáte `Dim` prohlášení, výchozí hodnoty úrovně přístupu na hodnotu veřejná.  
  
## <a name="programming-tips"></a>Tipy k programování  
  
-   **Využití paměti.** Stejně jako u všech složené datové typy, nelze počítat bezpečně celkové paměti spotřeby strukturou společně přidáním přidělení nominální úložiště svých členů. Kromě toho nelze předpokládat bezpečně, že pořadí úložiště v paměti je stejný jako vaši objednávku deklarace. Pokud potřebujete k řízení rozložení úložiště struktury, můžete použít <xref:System.Runtime.InteropServices.StructLayoutAttribute> atribut `Structure` příkaz.  
  
-   **Spolupráce aspekty.** Pokud se propojení s součásti, které nejsou určeny pro rozhraní .NET Framework, například objekty automatizace nebo COM, mějte na paměti, že nejsou kompatibilní s jazykem Visual Basic uživatelem definované typy v jiných prostředích struktury typy.  
  
-   **Rozšíření.** Neexistuje žádný automatický převod na nebo z jakéhokoli struktura datového typu. Operátory převodu můžete definovat na váš struktura pomocí [Operator – příkaz](../../../visual-basic/language-reference/statements/operator-statement.md), a můžou deklarovat každý operátor převodu být `Widening` nebo `Narrowing`.  
  
-   **Znaky typu.** Struktura datové typy mít žádné – znak typu literálu ani – znak typu identifikátoru.  
  
-   **Typ Framework.** Neexistuje žádný odpovídající typ v rozhraní .NET Framework. Všechny struktury dědění ze třídy rozhraní .NET Framework <xref:System.ValueType?displayProperty=nameWithType>, ale bez individuálních struktura odpovídá <xref:System.ValueType?displayProperty=nameWithType>.  
  
## <a name="example"></a>Příklad  
 Následující zlepší ukazuje obrys deklaraci do struktury.  
  
```  
[Public | Protected | Friend | Protected Friend | Private] Structure structname  
    {Dim | Public | Friend | Private} member1 As datatype1  
    ' ...  
    {Dim | Public | Friend | Private} memberN As datatypeN  
End Structure  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ValueType>  
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>  
 [Datové typy](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Souhrn konverze](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Structure – příkaz](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Rozšíření](../../../visual-basic/language-reference/modifiers/widening.md)  
 [Zužující](../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
