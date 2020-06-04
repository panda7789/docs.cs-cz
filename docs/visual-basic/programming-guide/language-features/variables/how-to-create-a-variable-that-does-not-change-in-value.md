---
title: 'Postupy: Vytvoření proměnné, která se nezmění na hodnotu.'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
ms.openlocfilehash: 04e08784b5cfbdeb6db73b9b00fe9afa201bd06d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410513"
---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a>Postupy: Vytvoření proměnné, která se nezmění na hodnotu (Visual Basic).

Pojem proměnné, která nemění jeho hodnotu, může být neprotichůdný. Existují však situace, kdy konstanta není proveditelná a je užitečné mít proměnnou s pevnou hodnotou. V takovém případě můžete definovat členskou proměnnou s klíčovým slovem [ReadOnly](../../../language-reference/modifiers/readonly.md) .

[Příkaz const](../../../language-reference/statements/const-statement.md) nelze použít k deklaraci a přiřazení konstantní hodnoty v následujících situacích:

- `Const`Příkaz nepřijímá datový typ, který chcete použít.

- Neznáte hodnotu v době kompilace.

- Nemůžete vypočítat konstantní hodnotu v době kompilace.

### <a name="to-create-a-variable-that-does-not-change-in-value"></a>Vytvoření proměnné, která se nemění v hodnotě

1. Na úrovni modulu deklarujte členskou proměnnou pomocí [příkazu Dim](../../../language-reference/statements/dim-statement.md)a přidejte klíčové slovo [ReadOnly](../../../language-reference/modifiers/readonly.md) .

    ```vb
    Dim ReadOnly timeStarted
    ```

    Můžete zadat `ReadOnly` pouze pro členskou proměnnou. To znamená, že je nutné definovat proměnnou na úrovni modulu, mimo jakoukoli proceduru.

2. Pokud můžete vypočítat hodnotu v jednom příkazu v době kompilace, použijte klauzuli inicializace v `Dim` příkazu. Použijte klauzuli [as](../../../language-reference/statements/as-clause.md) se symbolem rovná se ( `=` ) následovaným výrazem. Ujistěte se, že kompilátor může tento výraz vyhodnotit na konstantní hodnotu.

    ```vb
    Dim ReadOnly timeStarted As Date = Now
    ```

    Hodnotu proměnné můžete přiřadit `ReadOnly` pouze jednou. Jakmile to uděláte, žádný kód nemůže někdy změnit jeho hodnotu.

    Pokud neznáte hodnotu v době kompilace nebo ji nelze vypočítat v době kompilace v rámci jednoho příkazu, lze ji v konstruktoru přiřadit v době běhu. K tomu je nutné deklarovat `ReadOnly` proměnnou na úrovni třídy nebo struktury. V konstruktoru této třídy nebo struktury vypočítáte pevnou hodnotu proměnné a před návratem z konstruktoru ji přiřaďte proměnné.

## <a name="see-also"></a>Viz také

- [WriteOnly](../../../language-reference/modifiers/writeonly.md)
- [Const – příkaz](../../../language-reference/statements/const-statement.md)
