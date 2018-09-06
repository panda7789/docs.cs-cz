---
title: Deklarace proměnné v jazyce Visual Basic
ms.date: 07/20/2015
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
ms.openlocfilehash: 92a20e5fbe60c71ec3375ed35c919e1f88cf0a9c
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43737552"
---
# <a name="variable-declaration-in-visual-basic"></a>Deklarace proměnné v jazyce Visual Basic
Deklarujete proměnnou k určení jeho název a vlastnosti. Příkaz deklarace proměnných [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md). Jeho umístění a obsah zadat vlastnosti proměnnou.  
  
 Proměnné pravidla pojmenování, najdete v článku [deklarované názvy elementů](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="declaration-levels"></a>Deklarace úrovně  
  
### <a name="local-and-member-variables"></a>Místní a členské proměnné  
 A *lokální proměnná* je ten, který je deklarován v rámci procedury. A *členskou proměnnou* je členem typu jazyka Visual Basic je deklarován na úrovni modulu uvnitř třídy, struktury nebo modulu, ale ne v rámci žádné procedury interní této třídy, struktury nebo modulu.  
  
### <a name="shared-and-instance-variables"></a>Sdílené a Instance proměnné  
 Ve třídě nebo struktuře kategorie členskou proměnnou závisí Určuje, jestli se sdílí. Pokud je deklarovaná s [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) – klíčové slovo, je *sdílené proměnné*, a existuje v jedné kopii sdílí mezi všemi instancemi třídy nebo struktury.  
  
 V opačném případě se *proměnnou instance*, a samostatnou kopii se vytvoří pro každou instanci třídy nebo struktury. Dané kopie proměnnou instance je k dispozici pouze pro instanci třídy nebo struktury, ve kterém byla vytvořena. Je nezávislé na kopii této instance proměnné v jeho ostatní instance dané třídy nebo struktury.  
  
## <a name="declaring-data-type"></a>Deklarující typ dat  
 [Jako](../../../../visual-basic/language-reference/statements/as-clause.md) klauzuli v příkazu deklarace umožňuje definovat datový typ nebo typ objektu se deklarace proměnné. Můžete určit kterékoli z následujících typů proměnné:  
  
-   Základní datový typ, jako například `Boolean`, `Long`, nebo `Decimal`  
  
-   Složený datový typ, jako je například pole nebo strukturu  
  
-   Typ objektu nebo třída definovaná ve vaší aplikaci nebo v jiné aplikaci  
  
-   A [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] třídy, jako například <xref:System.Windows.Forms.Label> nebo <xref:System.Windows.Forms.TextBox>  
  
-   Typ rozhraní, jako například <xref:System.IComparable> nebo <xref:System.IDisposable>  
  
 Je možné deklarovat několik proměnných v jednom příkazu bez nutnosti opakování datového typu. V následující příkazy, proměnné `i`, `j`, a `k` jsou deklarovány jako typ `Integer`, `l` a `m` jako `Long`, a `x` a `y` jako `Single`:  
  
```  
Dim i, j, k As Integer  
' All three variables in the preceding statement are declared as Integer.  
Dim l, m As Long, x, y As Single  
' In the preceding statement, l and m are Long, x and y are Single.  
```  
  
 Další informace o typech dat najdete v části [datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md). Další informace o objektech naleznete v tématu [objekty a třídy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) a [programování pomocí komponent](https://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3).  
  
## <a name="local-type-inference"></a>Odvození místního typu  
 *Odvození typu* slouží k určení typů dat místní proměnné deklarované bez `As` klauzuli. Kompilátor odvodí typ proměnné z typu výrazu inicializace. To umožňuje deklarovat proměnné bez explicitní uvedení typu. V následujícím příkladu obě `num1` a `num2` jsou silného typu jako celá čísla.  
  
 [!code-vb[VbVbalrTypeInference#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/variable-declaration_1.vb)]  
  
 Pokud chcete použít odvození místního typu `Option Infer` musí být nastaveno na `On`. Další informace najdete v tématu [odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) a [Option Infer – příkaz](../../../../visual-basic/language-reference/statements/option-infer-statement.md).  
  
## <a name="characteristics-of-declared-variables"></a>Vlastnosti deklarované proměnné  
 *Životnost* proměnné je časové období, během které je k dispozici pro použití. Obecně platí proměnná existuje jako prvek, který deklaruje (například procedury nebo třídy) i nadále existovat. Pokud proměnná není potřeba pokračovat, existující za dobu života jeho nadřazeného elementu, není potřeba dělat nic zvláštního v deklaraci. Pokud proměnná je potřeba pokračovat déle než jeho nadřazený element, můžete zahrnout `Static` nebo `Shared` – klíčové slovo v jeho `Dim` příkazu. Další informace najdete v tématu [životnosti v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
 *Oboru* proměnné je sada veškerý kód, který na ni můžete odkazovat bez kvalifikace názvu. Obor proměnné je určeno ve kterém je deklarována. Proměnné definované v dané oblasti, aniž byste museli kvalifikovat jejich názvy můžete použít kód umístěný v dané oblasti. Další informace najdete v tématu [obor v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).  
  
 Proměnné *úroveň přístupu* je rozsah kód, který má oprávnění k přístupu. Ta se určují podle modifikátor přístupu (například [veřejné](../../../../visual-basic/language-reference/modifiers/public.md) nebo [privátní](../../../../visual-basic/language-reference/modifiers/private.md)), který používáte v `Dim` příkaz. Další informace najdete v tématu [úrovní v jazyce Visual Basic přístupu](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Vytvoření nové proměnné](../../../../visual-basic/programming-guide/language-features/variables/how-to-create-a-new-variable.md)  
 [Postupy: Přesun dat do proměnné a z proměnné](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)  
 [Datové typy](../../../../visual-basic/language-reference/data-types/index.md)  
 [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)  
 [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)  
 [Static](../../../../visual-basic/language-reference/modifiers/static.md)  
 [Deklarované charakteristiky elementů](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Příkaz Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
