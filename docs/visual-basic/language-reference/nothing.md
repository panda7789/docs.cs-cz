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
ms.openlocfilehash: fb1af7d748faac78b26177af453a0e858f9e97c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="nothing-visual-basic"></a>Nothing (Visual Basic)
Představuje výchozí hodnotu jakéhokoli datového typu. U typů odkazu, je výchozí hodnota `null` odkaz. U typů hodnot výchozí hodnota závisí na tom, zda hodnota typ s možnou hodnotou Null.  
  
> [!NOTE]
>  Pro typy hodnot neumožňující hodnotu Null `Nothing` v jazyce Visual Basic se liší od `null` v jazyce C#. V jazyce Visual Basic, pokud nastavíte proměnnou typu hodnot neumožňující hodnotu Null na `Nothing`, proměnná nastavená na výchozí hodnotu pro příslušným deklarovaným typem. V jazyce C#, chcete-li přiřadit proměnné typu hodnot neumožňující hodnotu Null na `null`, dojde k chybě kompilace.  
  
## <a name="remarks"></a>Poznámky  
 `Nothing` představuje výchozí hodnotu datového typu. Výchozí hodnota závisí na tom, jestli je proměnná hodnota typu nebo typu odkazu.  
  
 Proměnná *typ hodnoty* přímo obsahuje jeho hodnotu. Typy hodnot zahrnout všechny číselné datové typy, `Boolean`, `Char`, `Date`, všechny struktury a všechny výčty. Proměnná *odkazují na typ* ukládá odkaz na instanci objektu v paměti. Odkazové typy zahrnují třídy, pole, delegáti a řetězce. Další informace najdete v tématu [typy hodnot a typy odkazu](../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
 Pokud je proměnná hodnoty typ, chování `Nothing` závisí na tom, jestli je proměnná s možnou hodnotou Null datového typu. Chcete-li představují typ s možnou hodnotou Null hodnoty, přidejte `?` modifikátor k názvu typu. Přiřazení `Nothing` s možnou hodnotou Null proměnné nastaví hodnotu `null`. Další informace a příklady naleznete v tématu [typy s možnou hodnotou Null hodnot](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).  
  
 Pokud je proměnná typu hodnotu, která není null, přiřazení `Nothing` k nastaví se výchozí hodnota pro příslušným deklarovaným typem. Pokud se tento typ obsahuje proměnné členů, jsou nastavené na výchozí hodnoty. Následující příklad znázorňuje to pro skalární typy.  
  
 [!code-vb[VbVbalrKeywords#7](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_1.vb)]  
  
 Pokud je proměnná typu odkaz, přiřazení `Nothing` proměnnou ji nastaví na `null` odkazu proměnnou typu. Proměnné, který je nastaven `null` odkaz není spojen s libovolného objektu. Následující příklad ukazuje to.  
  
 [!code-vb[VbVbalrKeywords#8](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_2.vb)]  
  
 Při kontrole, jestli odkaz (nebo zadejte hodnot hodnotu Null) je proměnná `null`, nepoužívejte `= Nothing` nebo `<> Nothing`. Vždy používat `Is Nothing` nebo `IsNot Nothing`.  
  
 Pro řetězce v jazyce Visual Basic, prázdný řetězec rovná `Nothing`. Proto `"" = Nothing` hodnotu true.  
  
 Následující příklad ukazuje porovnání, které používají `Is` a `IsNot` operátory.  
  
 [!code-vb[VbVbalrKeywords#9](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_3.vb)]  
  
 Pokud je deklarovat proměnnou bez použití `As` klauzule a nastavte ji na `Nothing`, proměnná má typ `Object`. Příkladem je `Dim something = Nothing`. V takovém případě dojde k chybě kompilace při `Option Strict` na a `Option Infer` je vypnutý.  
  
 Přiřadíte-li `Nothing` proměnné objektu už odkazuje na jakoukoli instanci objektu. Pokud proměnná měl dříve uvedených instance, jeho nastavení na hodnotu `Nothing` nezavře instance sám sebe. Ukončení instance a uvolnění paměti a systém prostředků s ním spojená, až poté, co má systém uvolňování (GC) zjistí, že neexistují žádné aktivní odkazy zbývající.  
  
 `Nothing` se liší od <xref:System.DBNull> objekt, který představuje Neinicializovaný variant nebo sloupci neexistující databáze.  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Dim](../../visual-basic/language-reference/statements/dim-statement.md)  
 [Doba života objektu: Vytváření a zničení objektů](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)  
 [Doba platnosti v jazyce Visual Basic](../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [Operátor Is](../../visual-basic/language-reference/operators/is-operator.md)  
 [Operátor IsNot](../../visual-basic/language-reference/operators/isnot-operator.md)  
 [Typy hodnot s povolenou hodnotou Null](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
