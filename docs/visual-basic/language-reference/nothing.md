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
ms.openlocfilehash: 12c88db49dc7723fc269195e7d174bfa822c64d3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963750"
---
# <a name="nothing-visual-basic"></a>Nothing (Visual Basic)
Představuje výchozí hodnotu libovolného datového typu. Pro typy odkazů je `null` výchozí hodnotou odkaz. U hodnotových typů závisí výchozí hodnota na tom, zda je typ hodnoty null.  
  
> [!NOTE]
> U typů hodnot bez hodnoty null se `Nothing` v Visual Basic liší od `null` v C#. Pokud jste v Visual Basic nastavili proměnnou typu hodnoty, na `Nothing`který nepovoluje hodnotu null, je proměnná nastavena na výchozí hodnotu pro deklarovaný typ. Pokud C#v nástroji přiřadíte proměnnou typu hodnoty, která není null, dojde `null`k chybě při kompilaci.  
  
## <a name="remarks"></a>Poznámky  
 `Nothing`představuje výchozí hodnotu datového typu. Výchozí hodnota závisí na tom, zda je proměnná typ hodnoty nebo typ odkazu.  
  
 Proměnná *typu hodnoty* přímo obsahuje její hodnotu. Typy hodnot zahrnují všechny číselné datové typy, `Boolean`, `Char`, `Date`, všechny struktury a všechny výčty. Proměnná *typu odkazu* ukládá odkaz na instanci objektu v paměti. Typy odkazů zahrnují třídy, pole, delegáty a řetězce. Další informace naleznete v tématu [typy hodnot a typy odkazů](../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
 Pokud je proměnná typu hodnoty, chování `Nothing` závisí na tom, zda je proměnná datového typu s možnou hodnotou null. Pro reprezentaci typu hodnoty s možnou hodnotou `?` null přidejte modifikátor na název typu. Přiřazení `Nothing` proměnné s možnou hodnotou null nastaví hodnotu `null`na. Další informace a příklady naleznete v tématu [typy hodnot](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)s možnou hodnotou null.  
  
 Pokud je proměnná typu hodnoty, která není null, přiřadí `Nothing` se k ní nastavená výchozí hodnota pro deklarovaný typ. Pokud tento typ obsahuje členy proměnné, všechny jsou nastaveny na výchozí hodnoty. Následující příklad ukazuje tento pro skalární typy.  
  
 [!code-vb[VbVbalrKeywords#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class2.vb#7)]  
  
 Pokud je proměnná typu odkazu, přiřazení `Nothing` k proměnné ji nastaví `null` na odkaz typu proměnné. Proměnná, která je nastavena na `null` odkaz, není přidružena k žádnému objektu. Následující příklad ukazuje to.  
  
 [!code-vb[VbVbalrKeywords#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class3.vb#8)]  
  
 Při kontrole, zda odkaz (nebo typ hodnoty s možnou hodnotou `null`null) je proměnná `= Nothing` , `<> Nothing`nepoužívejte nebo. Vždy použijte `Is Nothing` nebo `IsNot Nothing`.  
  
 Pro řetězce v Visual Basic se prázdný řetězec rovná `Nothing`. `"" = Nothing` Proto má hodnotu true.  
  
 Následující příklad ukazuje porovnání, které používají `Is` operátory a. `IsNot`  
  
 [!code-vb[VbVbalrKeywords#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class4.vb#9)]  
  
 Pokud deklarujete proměnnou bez použití `As` klauzule a nastavíte ji na `Nothing`, `Object`proměnná má typ. Příkladem je `Dim something = Nothing`. V tomto případě dojde k chybě při kompilaci, pokud `Option Strict` je zapnutý `Option Infer` a je vypnutý.  
  
 Když přiřadíte `Nothing` proměnné objektu, již neodkazuje na žádnou instanci objektu. Pokud proměnná dříve odkazovala na instanci, její nastavení na `Nothing` neukončí samotnou instanci. Instance se ukončí a uvolní se paměťové a systémové prostředky, které jsou k ní přidružené, a to až po zjištění uvolňování paměti (GC), že nezbývá žádný aktivní odkaz.  
  
 `Nothing`se liší od <xref:System.DBNull> objektu, který představuje Neinicializovaný typ variant nebo neexistující sloupec databáze.  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Dim](../../visual-basic/language-reference/statements/dim-statement.md)
- [Doba života objektu: Vytváření a zničení objektů](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Doba života v Visual Basic](../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Operátor Is](../../visual-basic/language-reference/operators/is-operator.md)
- [Operátor IsNot](../../visual-basic/language-reference/operators/isnot-operator.md)
- [Typy hodnot s povolenou hodnotou Null](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
