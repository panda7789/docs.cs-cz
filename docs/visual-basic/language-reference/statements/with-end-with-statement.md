---
title: With...End With – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.With
helpviewer_keywords:
- With keyword [Visual Basic]
- loop structures [Visual Basic], and With...End With statements
- execution [Visual Basic], on object
- instructions, repeating
- With...End With statements [Visual Basic]
- With statement [Visual Basic]
- With statement [Visual Basic], nesting
- objects [Visual Basic], accessing
- With block
- End keyword [Visual Basic], With...End With statements
ms.assetid: 340d5fbb-4f43-48ec-a024-80843c137817
ms.openlocfilehash: 3da04b85865389a2b4466b78091ff28529346269
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582257"
---
# <a name="withend-with-statement-visual-basic"></a>With...End With – příkaz (Visual Basic)

Vykoná řadu příkazů, které opakovaně odkazují na jeden objekt nebo strukturu, takže příkazy mohou při přístupu k členům tohoto objektu nebo struktury použít zjednodušenou syntaxi.  Při použití struktury lze číst pouze hodnoty členů nebo vyvolat metody a při pokusu o přiřazení hodnot do členů struktury používané v příkazu `With...End With` se zobrazí chyba.

## <a name="syntax"></a>Syntaxe

```vb
With objectExpression
    [ statements ]
End With
```

## <a name="parts"></a>Součásti

|Termín|Definice|
|---|---|
|`objectExpression`|Požadováno. Výraz, který se vyhodnotí na objekt. Výraz může být libovolně složitý a vyhodnotí se pouze jednou. Výraz lze vyhodnotit na libovolný datový typ včetně základních typů.|
|`statements`|Volitelné. Jeden nebo více příkazů mezi `With` a `End With`, které mohou odkazovat na členy objektu, které jsou vytvářeny vyhodnocením `objectExpression`.|
|`End With`|Požadováno. Ukončí definici bloku `With`.|

## <a name="remarks"></a>Poznámky

Pomocí `With...End With` můžete provést sérii příkazů na zadaném objektu bez zadání názvu objektu vícekrát. V rámci bloku příkazu `With` můžete určit člena objektu začínajícího tečkou, jako kdyby před ním byl objekt příkazu `With`.

Chcete-li například změnit více vlastností na jednom objektu, umístěte příkazy přiřazení vlastností do bloku `With...End With`, který odkazuje na objekt pouze jednou, a to místo jednou pro každé přiřazení vlastnosti.

Pokud váš kód přistupuje ke stejnému objektu ve více příkazech, získáte následující výhody pomocí příkazu `With`:

- Nemusíte vyhodnocovat složitý výraz vícekrát ani přiřazovat výsledek k dočasné proměnné, chcete-li na jeho členy odkazovat vícekrát.

- Odstraněním opakovaných kvalifikačních výrazů zlepšíte přehlednost kódu.

Datový typ `objectExpression` může být libovolný typ třídy nebo struktury nebo i Visual Basic elementární typ, jako je například `Integer`.  Pokud je `objectExpression` výsledkem cokoli jiného než objekt, můžete číst pouze hodnoty jeho členů nebo vyvolat metody a při pokusu o přiřazení hodnot členům struktury používané v příkazu `With...End With` se zobrazí chyba.  Jedná se o stejnou chybu, která by se vám měla zobrazit, pokud jste vyvolali metodu, která vrátila strukturu a hned k ní přistupovala hodnotu a přiřadili ji členu výsledku funkce, například `GetAPoint().x = 1`.  Problémem je v obou případech to, že tato struktura existuje pouze v zásobníku volání a neexistuje žádný způsob, jak člena změněné struktury v těchto situacích zapsat někam tak, aby jakýkoli jiný kód v programu tuto změnu zpozoroval.

@No__t_0 je vyhodnocen jednou po vstupu do bloku. Nemůžete znovu přiřadit `objectExpression` v rámci bloku `With`.

V rámci `With` bloku máte přístup k metodám a vlastnostem pouze zadaného objektu, aniž byste je museli kvalifikovat. Můžete použít metody a vlastnosti jiného objektu, musíte je ale kvalifikovat pomocí názvů jejich objektů.

Jeden příkaz `With...End With` můžete umístit do jiného. Vnořené příkazy `With...End With` můžou být matoucí, pokud objekty, na které se říkáte, nejsou jasné z kontextu. Je nutné zadat plně kvalifikovaný odkaz na objekt, který je ve vnějším `With` bloku, pokud je objekt odkazován z vnitřního bloku `With`.

Do bloku příkazu `With` nemůžete vytvořit větev mimo blok.

Pokud blok neobsahuje cyklus, spustí se příkazy pouze jednou. Je možné vnořovat různé druhy řídicích struktur. Další informace najdete v tématu [vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).

> [!NOTE]
> Klíčové slovo `With` lze použít také v inicializátorech objektů. Další informace a příklady naleznete v tématu [Inicializátory objektů: pojmenované a anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) a [anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).
>
> Pokud používáte blok `With` jenom pro inicializaci vlastností nebo polí objektu, který jste právě vytvořili, zvažte místo toho použití inicializátoru objektu.

## <a name="example"></a>Příklad

V následujícím příkladu každý blok `With` provádí sérii příkazů na jednom objektu.

[!code-vb[VbVbalrWithStatement#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#2)]

## <a name="example"></a>Příklad

Následující příklad vnořování `With…End With` příkazy. V rámci vnořeného příkazu `With` syntaxe odkazuje na vnitřní objekt.

[!code-vb[VbVbalrWithStatement#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Generic.List%601>
- [Vnořené řídicí struktury](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Inicializátory objektů: pojmenované a anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
