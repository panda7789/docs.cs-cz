---
title: 'Kopírování a aktualizace záznamu výrazy (F #)'
description: Další informace o zápisu "kopírování a aktualizace záznamu výraz", který zkopíruje existující záznam, aktualizace zadaná pole a vrátí aktualizovaný záznam.
author: ChrSteinert
ms.date: 06/04/2016
ms.openlocfilehash: d2b089e8a7fc5c7ee26139003e23d2eaa8a3174e
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "45990840"
---
# <a name="copy-and-update-record-expressions"></a>Kopírování a aktualizace výrazů záznamů

A *kopírování a aktualizace výrazů záznamů* je výraz, který zkopíruje existující záznam, aktualizuje zadaná pole a vrátí aktualizovaný záznam.

## <a name="syntax"></a>Syntaxe

```fsharp
{ record-name with
    updated-member-definitions }
```

## <a name="remarks"></a>Poznámky

Záznamy jsou neměnné ve výchozím nastavení, takže není možné žádná aktualizace s existujícím záznamem. Chcete-li vytvořit všechna pole záznamu aktualizovaný záznam byste museli znovu zadat. Pro zjednodušení tohoto úkolu *kopírování a aktualizace výrazů záznamů* lze použít. Tento výraz má existující záznam, vytvoří nový stejného typu pomocí zadaná pole z výrazu a chybějící pole určeného výrazu.
To může být užitečné, když je nutné zkopírovat existující záznam a případně změnit některé z hodnot pole.

Provést pro instanci nově vytvořený záznam.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

Pokud chcete aktualizovat pouze na pole daného záznamu můžete použít *kopírování a aktualizace výrazů záznamů* podobně jako následující:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a>Viz také:

- [Záznamy](records.md)
- [Referenční dokumentace jazyka F#](index.md)
