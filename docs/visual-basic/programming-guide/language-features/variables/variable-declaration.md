---
title: Deklarace proměnné v jazyce Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], declaring
- member variables [Visual Basic], declarations
- Dim statement [Visual Basic], variable declaration
- declaring variables [Visual Basic]
- variables [Visual Basic], scope
- variables [Visual Basic], data types
- data types [Visual Basic], variable declarations
- lifetime [Visual Basic], variables
- variables [Visual Basic], lifetime
- access levels [Visual Basic], variables
- scope [Visual Basic], declaration statements
- variables [Visual Basic], access level
- local variables [Visual Basic], declarations
- scope [Visual Basic], variables
ms.assetid: d8f10226-92b1-480f-9f53-df377b2d7e15
caps.latest.revision: 31
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8edd0b65b08efd437cc35e8f58ed7ed423736920
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="variable-declaration-in-visual-basic"></a>Deklarace proměnné v jazyce Visual Basic
Je deklarovat proměnnou a určit její název a vlastností. Příkaz deklarace pro proměnné [Dim – příkaz](../../../../visual-basic/language-reference/statements/dim-statement.md). Její umístění a obsah zadat vlastnosti proměnnou.  
  
 Proměnné pravidla pojmenování a požadavky najdete v tématu [deklarované názvy elementů](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="declaration-levels"></a>Deklarace úrovně  
  
### <a name="local-and-member-variables"></a>Místní a členské proměnné  
 A *místní proměnné* je ten, který je deklarován v rámci procedury. A *členské proměnné* je členem skupiny typu jazyka Visual Basic; je deklarovaný na úrovni modulu, uvnitř třídy, struktury nebo modul, ale není v rámci žádné procedury interní třídy, struktury nebo modul.  
  
### <a name="shared-and-instance-variables"></a>Sdílené a instanci proměnné  
 Ve třídě nebo struktuře kategorii členské proměnné závisí na tom, jestli je sdílené. Pokud je deklarovaný s [sdílené](../../../../visual-basic/language-reference/modifiers/shared.md) – klíčové slovo, je *sdílené proměnné*, a existuje v jedné kopie sdílí všechny instance třídu nebo strukturu.  
  
 V opačném případě je *proměnnou instance*, a samostatnou kopii se vytvoří pro každou instanci třídu nebo strukturu. Kopii proměnnou instance dané je k dispozici pouze pro instanci třídu nebo strukturu, ve kterém byla vytvořena. Je nezávislé na kopii této instance proměnné v jeho ostatní instance třídu nebo strukturu.  
  
## <a name="declaring-data-type"></a>Deklarující typ dat  
 [Jako](../../../../visual-basic/language-reference/statements/as-clause.md) klauzule příkazu deklarace umožňuje definovat datový typ nebo typ objektu proměnné jsou deklarace. Můžete zadat jakýkoli z následujících typů proměnné:  
  
-   Základní datový typ, jako například `Boolean`, `Long`, nebo `Decimal`  
  
-   Složené datové typu, například pole nebo struktura  
  
-   Typ objektu nebo třída definovaná v aplikaci nebo v jiné aplikaci  
  
-   A [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] třídy, jako například <xref:System.Windows.Forms.Label> nebo <xref:System.Windows.Forms.TextBox>  
  
-   Typ rozhraní, jako například <xref:System.IComparable> nebo <xref:System.IDisposable>  
  
 Bez nutnosti opakování datový typ je možné deklarovat několik proměnné v jednom příkazu. V následující příkazy, proměnné `i`, `j`, a `k` je deklarován jako typ `Integer`, `l` a `m` jako `Long`, a `x` a `y` jako `Single`:  
  
```  
Dim i, j, k As Integer  
' All three variables in the preceding statement are declared as Integer.  
Dim l, m As Long, x, y As Single  
' In the preceding statement, l and m are Long, x and y are Single.  
```  
  
 Další informace o typech dat najdete v tématu [datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md). Další informace o objektech, najdete v části [objekty a třídy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) a [programování s komponentami](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3).  
  
## <a name="local-type-inference"></a>Odvození místního typu  
 *Odvození typu* slouží k určení datové typy lokální proměnné deklarované bez `As` klauzule. Kompilátor odvodí typ proměnné z typu inicializace výrazu. To umožňuje deklarujte proměnné bez explicitně s uvedením typu. V následujícím příkladu obě `num1` a `num2` jsou silného typu jako celá čísla.  
  
 [!code-vb[VbVbalrTypeInference#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/variable-declaration_1.vb)]  
  
 Pokud chcete použít odvození místního typu `Option Infer` musí být nastavena na `On`. Další informace najdete v tématu [odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) a [Option Infer – příkaz](../../../../visual-basic/language-reference/statements/option-infer-statement.md).  
  
## <a name="characteristics-of-declared-variables"></a>Vlastnosti deklarované proměnných  
 *Životnost* proměnné je doba, během které it je k dispozici pro použití. Obecně platí existuje proměnná tak dlouho, dokud elementu, který deklaruje (například postup nebo třída) i nadále existovat. Pokud proměnnou nemusíte pokračovat, existující mimo dobu životnosti obsaženého prvku, není potřeba provádět žádné zvláštní v deklaraci. Pokud proměnná musí pokračovat déle, než jeho obsahující element existovat, můžete zahrnout `Static` nebo `Shared` – klíčové slovo v jeho `Dim` příkaz. Další informace najdete v tématu [doba platnosti v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
 *Oboru* proměnné je sada všechen kód, který může na ni odkazuje bez určení názvu. Proměnnou rozsahu je určen podle kde je deklarován. Kód umístěný v dané oblasti, můžete použít proměnné definované v této oblasti bez nutnosti kvalifikaci jejich názvy. Další informace najdete v tématu [oboru v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).  
  
 Proměnnou *úroveň přístupu* je rozsah kód, který má oprávnění k přístupu. To je dáno – modifikátor přístupu (například [veřejné](../../../../visual-basic/language-reference/modifiers/public.md) nebo [privátní](../../../../visual-basic/language-reference/modifiers/private.md)) použitý v `Dim` příkaz. Další informace najdete v tématu [úrovně v jazyce Visual Basic přístupu](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Vytvoření nové proměnné](../../../../visual-basic/programming-guide/language-features/variables/how-to-create-a-new-variable.md)  
 [Postupy: Přesun dat do proměnné a z proměnné](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)  
 [Datové typy](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)  
 [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)  
 [Static](../../../../visual-basic/language-reference/modifiers/static.md)  
 [Deklarované charakteristiky elementů](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Příkaz Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
