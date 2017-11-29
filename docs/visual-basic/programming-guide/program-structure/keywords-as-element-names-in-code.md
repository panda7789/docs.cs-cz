---
title: "Klíčová slova jako názvy elementu v kódu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f410a0eaac0dcc034d406a89ed1d01a8f228a583
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a>Klíčová slova jako názvy elementu v kódu (Visual Basic)
Žádné program element – například proměnné, třída nebo člen – může mít stejný název jako s omezeným přístupem – klíčové slovo. Například můžete vytvořit proměnné s názvem `Loop`. Však k odkazování na vaší verzi, který má stejný název jako s omezeným přístupem `Loop` – klíčové slovo – musí předcházet řetězcem úplné kvalifikace nebo hranaté závorky (`[ ]`), jak ukazuje následující příklad.  
  
 [!code-vb[VbVbcnConventions#8](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/keywords-as-element-names-in-code_1.vb)]  
  
 Pokud neprovedete tyto, pak jazyka Visual Basic předpokládá použití vnitřní `Loop` – klíčové slovo a vytvoří chybu, jako v následujícím příkladu:  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 Hranaté závorky můžete použít k odkazování na formuláře a ovládací prvky a pokud deklarace proměnné nebo definování procedura se stejným názvem jako s omezeným přístupem – klíčové slovo. Může být snadno nezapomněli kvalifikovat názvy nebo zahrnují hranaté závorky a proto zavést kódu chyby a znesnadňuje ke čtení. Z tohoto důvodu doporučujeme používat s omezeným přístupem klíčová slova jako názvy elementů programu. Ale pokud budoucí verze aplikace Visual Basic definuje new – klíčové slovo, které jsou v konfliktu s existující formuláře nebo název ovládacího prvku, pak můžete tento postup při aktualizaci kódu pro práci s novou verzí.  
  
> [!NOTE]
>  Váš program také mohou zahrnovat názvy elementů od ostatních odkazované sestavení. Pokud tyto názvy v konfliktu s omezeným klíčová slova, pak umístění hranaté závorky je obcházet způsobí, že je interpretovat jako definované prvky jazyka Visual Basic.  
  
## <a name="see-also"></a>Viz také  
 [Zásady vytváření názvů jazyka Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [Struktura programu a pravidla týkající se kódu](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
