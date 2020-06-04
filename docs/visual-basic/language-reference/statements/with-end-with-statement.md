---
title: With...End With – příkaz
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
ms.openlocfilehash: 50f3bd0c6e96254274b429794901e2e4ac719ad0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401378"
---
# <a name="withend-with-statement-visual-basic"></a>With...End With – příkaz (Visual Basic)

Vykoná řadu příkazů, které opakovaně odkazují na jeden objekt nebo strukturu, takže příkazy mohou při přístupu k členům tohoto objektu nebo struktury použít zjednodušenou syntaxi.  Při použití struktury lze číst pouze hodnoty členů nebo vyvolat metody a při pokusu o přiřazení hodnot členům struktury použité v příkazu se zobrazí chyba `With...End With` .

## <a name="syntax"></a>Syntaxe

```vb
With objectExpression
    [ statements ]
End With
```

## <a name="parts"></a>Součásti

|Pojem|Definice|
|---|---|
|`objectExpression`|Povinná hodnota. Výraz, který se vyhodnotí na objekt. Výraz může být libovolně složitý a vyhodnotí se pouze jednou. Výraz lze vyhodnotit na libovolný datový typ včetně základních typů.|
|`statements`|Nepovinný parametr. Jeden nebo více příkazů mezi `With` a `End With` , které mohou odkazovat na členy objektu, který je vytvořen vyhodnocením `objectExpression` .|
|`End With`|Povinná hodnota. Ukončí definici `With` bloku.|

## <a name="remarks"></a>Poznámky

Pomocí `With...End With` můžete provést sérii příkazů na zadaném objektu bez zadání názvu objektu vícekrát. V rámci `With` bloku příkazu můžete určit člena objektu začínajícího tečkou, jako by byl `With` před ním uveden objekt příkazu.

Chcete-li například změnit více vlastností na jednom objektu, umístěte příkazy přiřazení vlastností dovnitř `With...End With` bloku a odkaz na objekt pouze jednou pro každé přiřazení vlastnosti.

Pokud váš kód přistupuje ke stejnému objektu ve více příkazech, získáte následující výhody pomocí `With` příkazu:

- Nemusíte vyhodnocovat složitý výraz vícekrát ani přiřazovat výsledek k dočasné proměnné, chcete-li na jeho členy odkazovat vícekrát.

- Odstraněním opakovaných kvalifikačních výrazů zlepšíte přehlednost kódu.

Datový typ `objectExpression` může být libovolný typ třídy nebo struktury nebo i Visual Basic základní typ, jako je `Integer` .  Pokud je `objectExpression` výsledkem cokoli jiného než objekt, můžete číst pouze hodnoty jeho členů nebo vyvolat metody a při pokusu o přiřazení hodnot členům struktury použité v příkazu se zobrazí chyba `With...End With` .  Jedná se o stejnou chybu, která by se vám měla zobrazit, pokud jste vyvolali metodu, která vrátila strukturu a hned k ní přistupovala hodnotu a přiřadili ji členu výsledku funkce, jako je například `GetAPoint().x = 1` .  Problémem je v obou případech to, že tato struktura existuje pouze v zásobníku volání a neexistuje žádný způsob, jak člena změněné struktury v těchto situacích zapsat někam tak, aby jakýkoli jiný kód v programu tuto změnu zpozoroval.

`objectExpression`Je vyhodnocen jednou při vstupu do bloku. Nemůžete znovu přiřadit v `objectExpression` rámci `With` bloku.

V rámci `With` bloku máte přístup k metodám a vlastnostem pouze zadaného objektu, aniž byste je museli kvalifikovat. Můžete použít metody a vlastnosti jiného objektu, musíte je ale kvalifikovat pomocí názvů jejich objektů.

Jeden příkaz můžete umístit `With...End With` do jiného. Vnořené `With...End With` příkazy mohou být matoucí, pokud objekty, na které se říkáte, nejsou jasné z kontextu. Je nutné zadat plně kvalifikovaný odkaz na objekt, který je uvnitř vnějšího `With` bloku, pokud je objekt odkazován z vnitřního `With` bloku.

Do bloku příkazu nemůžete vytvořit větev `With` mimo blok.

Pokud blok neobsahuje cyklus, spustí se příkazy pouze jednou. Je možné vnořovat různé druhy řídicích struktur. Další informace najdete v tématu [vnořené řídicí struktury](../../programming-guide/language-features/control-flow/nested-control-structures.md).

> [!NOTE]
> Klíčové slovo lze použít `With` také v inicializátorech objektů. Další informace a příklady naleznete v tématu [Inicializátory objektů: pojmenované a anonymní typy](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) a [anonymní typy](../../programming-guide/language-features/objects-and-classes/anonymous-types.md).
>
> Pokud používáte `With` blok pouze k inicializaci vlastností nebo polí objektu, který jste právě vytvořili, zvažte místo toho použití inicializátoru objektu.

## <a name="example"></a>Příklad

V následujícím příkladu každý `With` blok provádí sérii příkazů na jednom objektu.

[!code-vb[VbVbalrWithStatement#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#2)]

## <a name="example"></a>Příklad

Následující příklad vnořování `With…End With` příkazů. V rámci vnořeného `With` příkazu syntaxe odkazuje na vnitřní objekt.

[!code-vb[VbVbalrWithStatement#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a>Viz také

- <xref:System.Collections.Generic.List%601>
- [Vnořené řídicí struktury](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [Inicializátory objektů: pojmenované a anonymní typy](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Anonymní typy](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)
