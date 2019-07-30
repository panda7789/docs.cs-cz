---
title: 'Výjimky: Výraz try...with'
description: Naučte se používat F# try... výraz with pro zpracování výjimek.
ms.date: 05/16/2016
ms.openlocfilehash: e4d615086a93e26b76cca460e797659ca13792b5
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630244"
---
# <a name="exceptions-the-trywith-expression"></a>Výjimky: Výraz try...with

Toto téma popisuje `try...with` výraz, který se používá pro zpracování výjimek v F# jazyce.

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

Výraz se používá ke zpracování výjimek v F# `try...with` Je podobný `try...catch` příkazu v. C# V předchozí syntaxi kód v *Výraz1* může generovat výjimku. `try...with` Výraz vrací hodnotu. Pokud není vyvolána žádná výjimka, vrátí celý výraz hodnotu *Výraz1*. Je-li vyvolána výjimka, je každý *vzor* porovnán s výjimkou a pro první odpovídající vzor, odpovídající *výraz*, který je známý jako *obslužná rutina výjimky*, pro tuto větev je spuštěn a celkový výraz Vrátí hodnotu výrazu v této obslužné rutině výjimky. Pokud žádný vzor neodpovídá, výjimka rozšíří zásobník volání, dokud není nalezena odpovídající obslužná rutina. Typy hodnot vrácených z každého výrazu v obslužných rutinách výjimek se musí shodovat s typem vráceným z výrazu v `try` bloku.

Často skutečnost, že došlo k chybě, také znamená, že neexistuje žádná platná hodnota, která může být vrácena z výrazů v každé obslužné rutině výjimky. Častým vzorem je, že typ výrazu je typ možnosti. Následující příklad kódu ukazuje tento model.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5601.fs)]

Výjimky mohou být výjimky rozhraní .NET nebo mohou být F# výjimky. Výjimky lze definovat F# pomocí `exception` klíčového slova.

Můžete použít celou řadu vzorů k filtrování typu výjimky a dalších podmínek. Tyto možnosti jsou shrnuté v následující tabulce.

|Vzor|Popis|
|-------|-----------|
|:? *exception-type*|Odpovídá zadanému typu výjimky .NET.|
|:? *Typ výjimky* jako *identifikátoru*|Odpovídá zadanému typu výjimky .NET, ale poskytuje výjimku jako pojmenovanou hodnotu.|
|*název výjimky* (*argumenty*)|Odpovídá typu F# výjimky a váže argumenty.|
|*RID*|Odpovídá jakékoli výjimce a váže název objektu výjimky. **Ekvivalent:? System. Exception**–_identifikátor_|
|*identifikátor* za *podmínkou*|Odpovídá jakékoli výjimce, pokud je podmínka pravdivá.|

## <a name="examples"></a>Příklady

Následující příklady kódu ilustrují použití různých vzorů obslužných rutin výjimek.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5602.fs)]

> [!NOTE]
> Konstrukce je samostatný výraz `try...finally` z výrazu. `try...with` Proto pokud váš kód vyžaduje `with` blok `finally` i blok, bude nutné vnořené dva výrazy vnořit.

> [!NOTE]
> Můžete použít `try...with` v asynchronních pracovních postupech a jiných výrazech výpočtu. v takovém případě se používá `try...with` přizpůsobená verze výrazu. Další informace najdete v tématu [asynchronní pracovní postupy](../asynchronous-workflows.md)a [výpočetní výrazy](../computation-expressions.md).

## <a name="see-also"></a>Viz také:

- [Zpracování výjimek](index.md)
- [Typy výjimek](exception-types.md)
- [Výjimky: `try...finally` Výraz](the-try-finally-expression.md)
