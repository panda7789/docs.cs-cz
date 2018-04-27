---
title: Statické a pozdní vazby (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 10ecc965fb6d728454b3af33a6e93b2d7dbc327d
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="early-and-late-binding-visual-basic"></a>Statické a pozdní vazby (Visual Basic)
Visual Basic – kompilátor provede proces nazvaný `binding` když je objekt přiřazení proměnné objektu. Je-li objekt *časné* když je přiřazený k proměnné deklarované jako konkrétní typy objektů. Časná vázaným objektům povolení kompilátoru přidělit paměť a provádět další optimalizace před spuštěním aplikace. Například následující fragment kódu deklaruje proměnnou být typu <xref:System.IO.FileStream>:  
  
 [!code-vb[VbVbalrOOP#90](../../../../visual-basic/misc/codesnippet/VisualBasic/early-and-late-binding_1.vb)]  
  
 Protože <xref:System.IO.FileStream> je konkrétní typy objektů, instance přiřazené `FS` je již v rané fázi vázána.  
  
 Naopak je objekt *pozdní vazba* když je přiřazený k proměnné deklarované jako typ `Object`. Objekty tohoto typu udržení odkazů na libovolného objektu, ale nemají mnoho výhod časné vazby objektů. Například následující fragment kódu deklaruje proměnné objektu pro objekt vrácený `CreateObject` funkce:  
  
 [!code-vb[VbVbalrOOP#91](../../../../visual-basic/misc/codesnippet/VisualBasic/early-and-late-binding_2.vb)]  
  
## <a name="advantages-of-early-binding"></a>Výhody časná vazba  
 Měli byste použít objekty časné vazby, pokud je to možné, protože kompilátor, aby byl důležité optimalizace, které vrací efektivnější aplikace. Objekty časné vazby je výrazně rychlejší než pozdní vazbou a snadněji číst a údržbě, protože s informacemi o tom přesně jaký typ objektů, které používají váš kód. Časná vazba Další výhodou je, že umožňuje užitečných funkcí, jako je doplňování kódu pro automatické a dynamické nápovědy, protože [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] integrované vývojové prostředí (IDE) můžete určit přesně jaký typ objektu práci se při úpravě kód. Časná vazba snižuje počet a závažnost běhové chyby, protože umožňuje kompilátoru zprávy o chybách, když je program kompilován.  
  
> [!NOTE]
>  Pozdní vazba pouze umožňuje přístup ke členům typu, které jsou deklarované jako `Public`. Přístup ke členům deklarován jako `Friend` nebo `Protected Friend` výsledkem chyba spuštění.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>  
 [Doba života objektu: Vytváření a zničení objektů](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)  
 [Datový typ Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)
