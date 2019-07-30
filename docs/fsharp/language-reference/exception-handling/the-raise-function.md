---
title: 'Výjimky: Funkce raise'
description: Přečtěte si F# , jak se používá funkce ' vyvolání ' k indikaci, že došlo k chybě nebo mimořádné podmínce.
ms.date: 05/16/2016
ms.openlocfilehash: e0cc8da8310203c537b8081af8a225671bd8c6a3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630285"
---
# <a name="exceptions-the-raise-function"></a>Výjimky: Funkce raise

`raise` Funkce slouží k označení, že došlo k chybě nebo mimořádné podmínce. Informace o chybě jsou zachyceny v objektu výjimky.

## <a name="syntax"></a>Syntaxe

```fsharp
raise (expression)
```

## <a name="remarks"></a>Poznámky

`raise` Funkce vygeneruje objekt výjimky a zahájí proces odvíjení zásobníku. Proces odvíjení zásobníku je spravován modulem CLR (Common Language Runtime), takže chování tohoto procesu je stejné jako v jakémkoli jiném jazyce .NET. Proces odvíjení zásobníku je hledání obslužné rutiny výjimky, která odpovídá vygenerované výjimce. Hledání se spustí v aktuálním `try...with` výrazu, pokud existuje. Každý vzor `with` bloku je zkontrolován v pořadí. Pokud je nalezena vyhovující obslužná rutina výjimky, je výjimka považována za zpracovanou; v opačném případě je zásobník rozpadl `with` a zablokuje řetěz volání, dokud není nalezena vyhovující obslužná rutina. Všechny `finally` bloky, které se vyskytují v řetězu volání, jsou také spuštěny v sekvenci jako odvinutí zásobníku.

Funkce je ekvivalentem C# v nebo C++ `throw` `raise` Použijte `reraise` v obslužné rutině catch k šíření stejné výjimky v řetězu volání.

Následující příklady kódu ilustrují použití `raise` funkce pro vygenerování výjimky.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5801.fs)]

`raise` Funkci lze také použít k vyvolání výjimek rozhraní .NET, jak je znázorněno v následujícím příkladu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5802.fs)]

## <a name="see-also"></a>Viz také:

- [Zpracování výjimek](index.md)
- [Typy výjimek](exception-types.md)
- [Výjimky: `try...with` Výraz](the-try-with-expression.md)
- [Výjimky: `try...finally` Výraz](the-try-finally-expression.md)
- [Výjimky: `failwith` Funkce](the-failwith-function.md)
- [Výjimky: `invalidArg` Funkce](the-invalidArg-function.md)
