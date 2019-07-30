---
title: 'Postupy: Vytvořit proměnnou, která se nemění v hodnotě (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
ms.openlocfilehash: d201e95463dd0431825fee03ebfd340ac80cc552
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630883"
---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a>Postupy: Vytvořit proměnnou, která se nemění v hodnotě (Visual Basic)

Pojem proměnné, která nemění jeho hodnotu, může být neprotichůdný. Existují však situace, kdy konstanta není proveditelná a je užitečné mít proměnnou s pevnou hodnotou. V takovém případě můžete definovat členskou proměnnou s klíčovým slovem [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) .

[Příkaz const](../../../../visual-basic/language-reference/statements/const-statement.md) nelze použít k deklaraci a přiřazení konstantní hodnoty v následujících situacích:

- `Const` Příkaz nepřijímá datový typ, který chcete použít.

- Neznáte hodnotu v době kompilace.

- Nemůžete vypočítat konstantní hodnotu v době kompilace.

### <a name="to-create-a-variable-that-does-not-change-in-value"></a>Vytvoření proměnné, která se nemění v hodnotě

1. Na úrovni modulu deklarujte členskou proměnnou pomocí [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)a přidejte klíčové slovo [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) .

    ```vb
    Dim ReadOnly timeStarted
    ```

    Můžete zadat `ReadOnly` pouze pro členskou proměnnou. To znamená, že je nutné definovat proměnnou na úrovni modulu, mimo jakoukoli proceduru.

2. Pokud můžete vypočítat hodnotu v jednom příkazu v době kompilace, použijte klauzuli inicializace v `Dim` příkazu. Použijte klauzuli [as](../../../../visual-basic/language-reference/statements/as-clause.md) se symbolem rovná se (`=`) následovaným výrazem. Ujistěte se, že kompilátor může tento výraz vyhodnotit na konstantní hodnotu.

    ```vb
    Dim ReadOnly timeStarted As Date = Now
    ```

    Hodnotu `ReadOnly` proměnné můžete přiřadit pouze jednou. Jakmile to uděláte, žádný kód nemůže někdy změnit jeho hodnotu.

    Pokud neznáte hodnotu v době kompilace nebo ji nelze vypočítat v době kompilace v rámci jednoho příkazu, lze ji v konstruktoru přiřadit v době běhu. K tomu je nutné deklarovat `ReadOnly` proměnnou na úrovni třídy nebo struktury. V konstruktoru této třídy nebo struktury vypočítáte pevnou hodnotu proměnné a před návratem z konstruktoru ji přiřaďte proměnné.

## <a name="see-also"></a>Viz také:

- [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)
- [Příkaz Const](../../../../visual-basic/language-reference/statements/const-statement.md)
