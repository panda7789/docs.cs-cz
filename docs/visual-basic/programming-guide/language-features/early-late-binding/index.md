---
title: Statické a pozdní vazby (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- early binding [Visual Basic]
- objects [Visual Basic], late-bound
- objects [Visual Basic], early-bound
- objects [Visual Basic], late bound
- early binding [Visual Basic], Visual Basic compiler
- binding [Visual Basic], late and early
- objects [Visual Basic], early bound
- Visual Basic compiler, early and late binding
- late binding [Visual Basic]
- late binding [Visual Basic], Visual Basic compiler
ms.assetid: d6ff7f1e-b94f-4205-ab8d-5cfa91758724
ms.openlocfilehash: 20eb96d0d9f81ec9dfa359edf63a60f72a45aa01
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824790"
---
# <a name="early-and-late-binding-visual-basic"></a>Statické a pozdní vazby (Visual Basic)
Kompilátor jazyka Visual Basic provádí proces s názvem `binding` když objekt přiřazen do proměnné objektu. Objekt je *časné* při je přiřazena k proměnné deklarované jako konkrétní typy objektů. Časná vázaným objektům povolení kompilátoru přidělení paměti a provádět další optimalizace před spuštěním aplikace. Například následující fragment kódu deklaruje proměnnou typu <xref:System.IO.FileStream>:  
  
 [!code-vb[VbVbalrOOP#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#90)]  
  
 Protože <xref:System.IO.FileStream> je konkrétní typy objektů, přiřazenou instanci `FS` časná vazba.  
  
 Naopak je objekt *pozdní vazby* při je přiřazena k proměnné deklarované jako typ `Object`. Objekty tohoto typu můžou obsahovat odkazy na libovolný objekt, ale nemají mnohé z výhod časnou vazbou. Například následující fragment kódu deklaruje proměnnou objektu pro objekt vrácený `CreateObject` funkce:  
  
 [!code-vb[VbVbalrOOP#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/LateBinding.vb#91)]  
  
## <a name="advantages-of-early-binding"></a>Výhody časná vazba  
 Časné vazby objektů pokaždé, když je to možné, byste měli použít, protože umožňují kompilátor, aby byl důležité optimalizace, které vrací efektivnější aplikace. Časné vazby objektů jsou výrazně rychlejší než objekty s pozdní vazbou a byl kód čitelnější a udržovat tím, že s informacemi o tom právě jaký druh objekty používají. Časná vazba Další výhodou je, že umožňuje užitečných funkcí, jako je doplňování kódu pro automatickou a dynamická Nápověda, protože integrovaného vývojového prostředí (IDE) sady Visual Studio můžete určit přesně jaký typ objektu pracujete s při úpravě kód. Časné vazby snižuje množství a závažnosti chyby za běhu, protože umožňuje kompilátoru zprávy o chybách při kompilaci programu.  
  
> [!NOTE]
>  Pozdní vazby jde použít jenom pro přístup ke členům typu, které jsou deklarovány jako `Public`. Přístup k členům deklarován jako `Friend` nebo `Protected Friend` vede k chybě za běhu.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>
- [Doba života objektu: Způsob vytváření a zničení objektů](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Datový typ Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)
