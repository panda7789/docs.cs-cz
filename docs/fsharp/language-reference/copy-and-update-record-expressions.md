---
title: Kopírování a aktualizace výrazů záznamů
description: Naučte se psát výraz kopírování a aktualizace, který kopíruje existující záznam nebo anonymní záznam, aktualizuje zadaná pole a vrací aktualizovaný nebo anonymní záznam.
author: ChrSteinert
ms.date: 06/12/2019
ms.openlocfilehash: bec3e0ac2fb34e358b199c509c4599b55d7bf35e
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739276"
---
# <a name="copy-and-update-record-expressions"></a>Kopírování a aktualizace výrazů záznamů

*Výraz záznamu kopírování a aktualizace* je výraz, který kopíruje existující záznam, aktualizuje zadaná pole a vrací aktualizovaný záznam.

## <a name="syntax"></a>Syntaxe

```fsharp
{ record-name with
    updated-labels }

{| anonymous-record-name with
    updated-labels |}
```

## <a name="remarks"></a>Poznámky

Záznamy a anonymní záznamy jsou ve výchozím nastavení neměnné, takže není možné aktualizovat existující záznam. Chcete-li vytvořit aktualizovaný záznam, musí být znovu zadána všechna pole záznamu. Pro zjednodušení tohoto úkolu lze použít *výraz kopírování a aktualizace.* Tento výraz přebírá existující záznam, vytvoří nový stejného typu pomocí zadaných polí z výrazu a chybějícího pole určeného výrazem.

To může být užitečné, pokud máte zkopírovat existující záznam a případně změnit některé hodnoty polí.

Vezměte například nově vytvořený záznam.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

Chcete-li aktualizovat pouze dvě pole v tomto záznamu, můžete použít *výraz kopírování a aktualizace záznamu*:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a>Viz také

- [Záznamy](records.md)
- [Anonymní záznamy](anonymous-records.md)
- [Referenční příručka jazyka F#](index.md)
