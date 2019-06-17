---
title: Kopírování a aktualizace výrazů záznamů
description: Další informace o zápisu "kopírování a aktualizace výraz", který zkopíruje existující záznam nebo anonymní záznamu, aktualizace zadaná pole a vrátí aktualizovaný záznam nebo anonymní záznamu.
author: ChrSteinert
ms.date: 06/12/2019
ms.openlocfilehash: d16f5ca337047ab2eecc8828b21d8a423bf39a1f
ms.sourcegitcommit: c4dfe37032c64a1fba2cc3d5947550d79f95e3b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/13/2019
ms.locfileid: "67041740"
---
# <a name="copy-and-update-record-expressions"></a>Kopírování a aktualizace výrazů záznamů

A *kopírování a aktualizace výrazů záznamů* je výraz, který zkopíruje existující záznam, aktualizuje zadaná pole a vrátí aktualizovaný záznam.

## <a name="syntax"></a>Syntaxe

```fsharp
{ record-name with
    updated-labels }

{| anonymous-record-name with
    updated-labels |}
```

## <a name="remarks"></a>Poznámky

Anonymní záznamů a záznamů jsou neměnné ve výchozím nastavení, takže není možné žádná aktualizace s existujícím záznamem. Chcete-li vytvořit všechna pole záznamu aktualizovaný záznam byste museli znovu zadat. Pro zjednodušení tohoto úkolu *kopírování a aktualizace výrazů* lze použít. Tento výraz má existující záznam, vytvoří nový stejného typu pomocí zadaná pole z výrazu a chybějící pole určeného výrazu.

To může být užitečné, když je nutné zkopírovat existující záznam a případně změnit některé z hodnot pole.

Provést pro instanci nově vytvořený záznam.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

Pokud chcete aktualizovat pouze na pole daného záznamu můžete použít *kopírování a aktualizace výrazů záznamů* podobně jako následující:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a>Viz také:

- [Záznamy](records.md)
- [Anonymní záznamů](anonymous-records.md)
- [Referenční dokumentace jazyka F#](index.md)
