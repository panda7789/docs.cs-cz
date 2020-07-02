---
ms.openlocfilehash: 4a65e721e5639f12445a9a44f46baa0d26898a88
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615637"
---
### <a name="il-ret-not-allowed-in-a-try-region"></a>V oblasti try není povolená technologie IL ret

#### <a name="details"></a>Podrobnosti

Na rozdíl od JIT64 kompilátoru za běhu nepovoluje RyuJIT (používá se v .NET Framework 4,6) instrukci IL v oblasti try. Vrácení z oblasti try není povoleno specifikací ECMA-335 a žádný známý spravovaný kompilátor takové IL negeneruje. Nicméně kompilátor JIT64 spustí takové IL, pokud je vygenerován pomocí generování reflexe.

#### <a name="suggestion"></a>Návrh

Pokud aplikace generuje IL, která zahrnuje ret v oblasti try, aplikace může cílit .NET Framework 4,5, aby používala starou JIT a zabránila tomuto přerušení. Případně je možné vygenerované IL aktualizovat, aby se vracely po oblasti try.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Edge        |
| Verze | 4.6         |
| Typ    | Změna cílení |
