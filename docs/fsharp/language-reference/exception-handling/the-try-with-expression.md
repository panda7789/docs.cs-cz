---
title: 'Výjimky: Výraz try...with (F#)'
description: "Další informace o použití F # 'try... with\"výraz pro zpracování výjimek."
ms.date: 05/16/2016
ms.openlocfilehash: 588960c0f8ccedb431c37d0f1314bf1a293b638c
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44042163"
---
# <a name="exceptions-the-trywith-expression"></a>Výjimky: Výraz try...with

Toto téma popisuje `try...with` výraz, výraz, který se používá pro zpracování výjimek v jazyce F #.

## <a name="syntax"></a>Syntaxe

```fsharp
try
    expression1
with
| pattern1 -> expression2
| pattern2 -> expression3
...
```

## <a name="remarks"></a>Poznámky

`try...with` Výraz je použit pro zpracování výjimek v jazyce F #. Se podobá `try...catch` příkaz v jazyce C#. V předchozí syntaxi, kód v *expression1* může vygenerovat výjimku. `try...with` Výraz vrátí hodnotu. Pokud není vyvolána žádná výjimka, celý výraz vrátí hodnotu *expression1*. Pokud je vyvolána výjimka, každý *vzor* je pak porovnána s výjimkou a pro první odpovídající vzor odpovídající *výraz*, označované jako *obslužnérutinyvýjimek*, je proveden tuto větev a celkové výraz vrací hodnotu výrazu v této obslužné rutiny výjimky. Pokud žádný vzor odpovídá, výjimka šíří výše v zásobníku volání, dokud není nalezena odpovídající obslužná rutina. Typy hodnot vrácených z každého výrazu v obslužných rutinách výjimek musí shodovat s typem vrácená z výrazu v `try` bloku.

Fakt, že došlo k chybě také často, znamená, že neexistuje platná hodnota vrácená z výrazů v každé obslužné rutiny výjimky. Časté je typu výrazu možné typ možnosti. Následující příklad kódu ukazuje tento model.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5601.fs)]

Výjimky mohou být výjimky .NET, nebo mohou být výjimky F #. Můžete definovat výjimky F # s použitím `exception` – klíčové slovo.

Různé vzorce můžete použít k filtrování podle typu výjimky a dalších podmínek; Možnosti jsou shrnuty v následující tabulce.

|Vzor|Popis|
|-------|-----------|
|:? *Typ výjimky*|Neodpovídá zadanému typu výjimky .NET.|
|:? *Typ výjimky* jako *identifikátor*|Neodpovídá zadanému typu výjimky .NET, ale dává výjimku pojmenovaná hodnota.|
|*název výjimky*(*argumenty*)|Odpovídá typu výjimky F # a sváže s argumenty.|
|*identifikátor*|Odpovídá jakékoli výjimce a sváže s názvem objektu výjimky. Ekvivalentní **:? System.Exception jako *** identifikátor*|
|*identifikátor* při *podmínku*|Odpovídá jakoukoliv výjimku, pokud je podmínka pravdivá.|

## <a name="examples"></a>Příklady

Následující příklady ilustrují použití různých vzorů obslužné rutiny výjimky.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5602.fs)]

>[!NOTE]
`try...with` Konstruktor je zvláštní výraz z `try...finally` výrazu. Proto pokud váš kód vyžaduje obě `with` bloku a `finally` bloku, budete muset vnořit dvou výrazů.

>[!NOTE]
Můžete použít `try...with` v asynchronních pracovních postupech a jiných výrazech výpočtu, ve kterém malá a velká přizpůsobenou verzi `try...with` výraz je použit. Další informace najdete v tématu [asynchronní pracovní postupy](../asynchronous-workflows.md), a [výrazech výpočtu](../computation-expressions.md).

## <a name="see-also"></a>Viz také:

- [Zpracování výjimek](index.md)
- [Typy výjimek](exception-types.md)
- [Výjimky: `try...finally` výraz](the-try-finally-expression.md)
