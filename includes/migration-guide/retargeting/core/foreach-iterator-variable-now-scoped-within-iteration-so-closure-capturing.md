---
ms.openlocfilehash: 9a2d6a25a8ab1b8bf65b947557802e0805a7f826
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617198"
---
### <a name="foreach-iterator-variable-is-now-scoped-within-the-iteration-so-closure-capturing-semantics-are-different-in-c5"></a>Proměnná iterátoru foreach je teď vymezená v rámci iterace, takže se sémantika zachytávání uzávěry liší (v C# 5).

#### <a name="details"></a>Podrobnosti

Počínaje jazykem C# 5 (Visual Studio 2012) `foreach` jsou proměnné iterátoru vymezeny v rámci iterace. To může způsobit přerušení v případě, že kód byl dříve v závislosti na proměnných, které nebudou zahrnuty do `foreach` ukončení. Příznakem této změny je, že proměnná iterátoru předaná delegátovi je považována za hodnotu, kterou má v době, kdy je delegát vytvořen, nikoli na hodnotu, která je v době volání delegáta.

#### <a name="suggestion"></a>Návrh

V ideálním případě by měl být kód aktualizován, aby bylo možné očekávat nové chování kompilátoru. Pokud je vyžadována stará sémantika, může být proměnná iterátoru nahrazena samostatnou proměnnou, která je explicitně umístěna mimo rozsah smyčky.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Hlavní       |
| Verze | 4.5         |
| Typ    | Změna cílení |
