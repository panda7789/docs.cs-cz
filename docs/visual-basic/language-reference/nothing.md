---
title: Nothing (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Nothing
- vb.Nothing
helpviewer_keywords:
- Nothing keyword [Visual Basic]
- Nothing keyword [Visual Basic], syntax
ms.assetid: 06176e2d-bbf7-4a37-afaa-a86ad21ee99f
ms.openlocfilehash: b8dfc166681dbadf1d2f4ba5a985011f5427f50a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981423"
---
# <a name="nothing-visual-basic"></a>Nothing (Visual Basic)
Představuje výchozí hodnotu libovolného datového typu. U referenčních typů je výchozí hodnota `null` odkaz. U typů hodnot výchozí hodnota závisí na tom, jestli je typ hodnoty s možnou hodnotou Null.  
  
> [!NOTE]
>  Pro typy hodnot neumožňující hodnotu `Nothing` v jazyce Visual Basic se liší od `null` v C#. V jazyce Visual Basic, pokud jste nastavili proměnné typu hodnotu Null pro `Nothing`, proměnná je nastavena na výchozí hodnotu pro jeho deklarovaného typu. V C#, je-li přiřadit proměnné typu hodnotu Null pro `null`, dojde k chybě kompilace.  
  
## <a name="remarks"></a>Poznámky  
 `Nothing` představuje výchozí hodnotu datového typu. Výchozí hodnota závisí na tom, jestli je proměnná hodnotového typu nebo typu odkazu.  
  
 Proměnné *typ hodnoty* přímo obsahuje jeho hodnotu. Zahrnout všechny číselné datové typy, typy hodnot `Boolean`, `Char`, `Date`, všechny struktury a všechny výčty. Proměnné *odkazovat na typ* uchovává odkaz na instanci objektu v paměti. Odkazové typy zahrnují třídy, pole, delegáty a řetězce. Další informace najdete v tématu [typy hodnot a odkazové typy](../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
 Pokud je proměnná hodnotu zadejte, chování `Nothing` závisí na tom, zda je proměnná typu s možnou hodnotou Null data. Pro reprezentaci typu s možnou hodnotou Null, přidejte `?` modifikátor názvu typu. Přiřazení `Nothing` s možnou hodnotou Null proměnné nastaví hodnotu `null`. Další informace a příklady najdete v tématu [hodnotové typy s možnou hodnotou Null](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).  
  
 Pokud je proměnná typu hodnoty, který není s možnou hodnotou Null, přiřazení `Nothing` do je nastaví ji na výchozí hodnotu pro příslušným deklarovaným typem. Pokud daný typ obsahuje proměnné členů, jsou nastavené na výchozí hodnoty. Následující příklad ukazuje to pro skalární typy.  
  
 [!code-vb[VbVbalrKeywords#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class2.vb#7)]  
  
 Pokud je proměnná typu odkazu, přiřazení `Nothing` proměnné se nastaví na `null` odkaz proměnnou typu. Proměnné, který je nastaven `null` odkaz není spojen s libovolný objekt. Následující příklad ukazuje to.  
  
 [!code-vb[VbVbalrKeywords#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class3.vb#8)]  
  
 Při kontrole, zda odkaz (nebo typ s možnou hodnotou Null) proměnné je `null`, nepoužívejte `= Nothing` nebo `<> Nothing`. Vždy používejte `Is Nothing` nebo `IsNot Nothing`.  
  
 Pro řetězce v jazyce Visual Basic, prázdný řetězec rovná `Nothing`. Proto `"" = Nothing` má hodnotu true.  
  
 Následující příklad ukazuje porovnání, která používají `Is` a `IsNot` operátory.  
  
 [!code-vb[VbVbalrKeywords#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class4.vb#9)]  
  
 Pokud deklarujete proměnnou bez použití `As` klauzule a nastavte ho na `Nothing`, je proměnná typu `Object`. Příkladem je `Dim something = Nothing`. V tomto případě dojde k chybě v době kompilace při `Option Strict` zapnutý a `Option Infer` je vypnuté.  
  
 Když přiřadíte `Nothing` do proměnné objektu, už odkazuje na jakoukoli instanci objektu. Pokud proměnná měla dříve uvedené instance, jeho nastavení na hodnotu `Nothing` neukončí samotné instanci. Instance se ukončí a uvolnění paměti a systém prostředků s ním spojená, až poté, co systému uvolňování paměti (GC) zjistí, že neexistují žádné aktivní odkazy zbývající.  
  
 `Nothing` se liší od <xref:System.DBNull> objektu, který představuje Neinicializovaný typ variant nebo neexistující databázový sloupec.  
  
## <a name="see-also"></a>Viz také:
- [Příkaz Dim](../../visual-basic/language-reference/statements/dim-statement.md)
- [Doba života objektu: Způsob vytváření a zničení objektů](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Doba platnosti v jazyce Visual Basic](../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Operátor Is](../../visual-basic/language-reference/operators/is-operator.md)
- [Operátor IsNot](../../visual-basic/language-reference/operators/isnot-operator.md)
- [Typy hodnot s povolenou hodnotou Null](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
