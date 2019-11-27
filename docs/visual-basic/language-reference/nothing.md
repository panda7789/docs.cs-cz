---
title: Nothing – klíčové slovo
ms.date: 07/20/2015
f1_keywords:
- Nothing
- vb.Nothing
helpviewer_keywords:
- Nothing keyword [Visual Basic]
- Nothing keyword [Visual Basic], syntax
ms.assetid: 06176e2d-bbf7-4a37-afaa-a86ad21ee99f
ms.openlocfilehash: 3bd4681341a33cc8db4ecbc2b284be243db56549
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344165"
---
# <a name="nothing-keyword-visual-basic"></a>Nothing – klíčové slovo (Visual Basic)

Představuje výchozí hodnotu libovolného datového typu. Pro typy odkazů je výchozí hodnotou odkaz `null`. U hodnotových typů závisí výchozí hodnota na tom, zda je typ hodnoty null.

> [!NOTE]
> U typů hodnot bez hodnoty null se `Nothing` v Visual Basic liší od `null` v C#. Pokud v Visual Basic nastavíte proměnnou typu hodnoty, která není null, na `Nothing`, proměnná je nastavena na výchozí hodnotu pro deklarovaný typ. Pokud C#v nástroji přiřadíte proměnnou typu hodnoty, která není null, k `null`, dojde k chybě při kompilaci.

## <a name="remarks"></a>Poznámky

`Nothing` představuje výchozí hodnotu datového typu. Výchozí hodnota závisí na tom, zda je proměnná typ hodnoty nebo typ odkazu.

Proměnná *typu hodnoty* přímo obsahuje její hodnotu. Typy hodnot zahrnují všechny číselné datové typy, `Boolean`, `Char`, `Date`, všechny struktury a všechny výčty. Proměnná *typu odkazu* ukládá odkaz na instanci objektu v paměti. Typy odkazů zahrnují třídy, pole, delegáty a řetězce. Další informace naleznete v tématu [typy hodnot a typy odkazů](../programming-guide/language-features/data-types/value-types-and-reference-types.md).

Pokud je proměnná typu hodnoty, chování `Nothing` závisí na tom, zda je proměnná datovým typem s možnou hodnotou null. Pro reprezentaci typu hodnoty s možnou hodnotou null přidejte modifikátor `?` k názvu typu. Přiřazení `Nothing` k proměnné s možnou hodnotou null nastaví hodnotu na `null`. Další informace a příklady naleznete v tématu [typy hodnot s možnou hodnotou null](../programming-guide/language-features/data-types/nullable-value-types.md).

Pokud je proměnná typu hodnoty, která nemůže mít hodnotu null, přiřazením `Nothing` ji nastaví na výchozí hodnotu pro deklarovaný typ. Pokud tento typ obsahuje členy proměnné, všechny jsou nastaveny na výchozí hodnoty. Následující příklad ukazuje tento pro skalární typy.

[!code-vb[VbVbalrKeywords#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class2.vb#7)]

Pokud je proměnná typu odkazu, přiřazení `Nothing` k proměnné nastaví na `null` odkaz typu proměnné. Proměnná, která je nastavena na odkaz `null`, není přidružena k žádnému objektu. Následující příklad ukazuje toto:

[!code-vb[VbVbalrKeywords#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class3.vb#8)]

Při kontrole, zda je proměnná odkaz (nebo typ hodnoty s možnou hodnotou null) `null`, nepoužívejte `= Nothing` ani `<> Nothing`. Vždy používejte `Is Nothing` nebo `IsNot Nothing`.

Pro řetězce v Visual Basic se prázdný řetězec rovná `Nothing`. Proto `"" = Nothing` má hodnotu true.

Následující příklad ukazuje porovnání, které používají operátory `Is` a `IsNot`:

[!code-vb[VbVbalrKeywords#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class4.vb#9)]

Pokud deklarujete proměnnou bez použití klauzule `As` a nastavíte ji na `Nothing`, proměnná má typ `Object`. Příkladem je `Dim something = Nothing`. V takovém případě dojde k chybě při kompilaci, pokud je `Option Strict` zapnutá a `Option Infer` je vypnutá.

Když přiřadíte `Nothing` proměnné objektu, již neodkazuje na žádnou instanci objektu. Pokud proměnná dříve odkazovala na instanci, její nastavení na `Nothing` neukončí samotnou instanci. Instance se ukončí a uvolní se paměťové a systémové prostředky, které jsou k ní přidružené, a to až po zjištění uvolňování paměti (GC), že nezbývá žádný aktivní odkaz.

`Nothing` se liší od objektu <xref:System.DBNull>, který představuje Neinicializovaný typ variant nebo neexistující sloupec databáze.

## <a name="see-also"></a>Viz také:

- [Příkaz Dim](./statements/dim-statement.md)
- [Doba života objektu: Vytváření a zničení objektů](../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Doba života v Visual Basic](../programming-guide/language-features/declared-elements/lifetime.md)
- [Operátor Is](./operators/is-operator.md)
- [Operátor IsNot](./operators/isnot-operator.md)
- [Typy hodnot s povolenou hodnotou Null](../programming-guide/language-features/data-types/nullable-value-types.md)
