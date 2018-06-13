---
title: 'Kopírování a aktualizace záznamů výrazy (F #)'
description: Další informace o zápisu, kopírování a aktualizace záznamů výraz, který kopíruje existující aktualizace záznamů, zadaná pole a vrátí aktualizované záznam.
author: ChrSteinert
ms.date: 06/04/2016
ms.openlocfilehash: 000746b6e76349ae6d8f338519a58034f4e29020
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563056"
---
# <a name="copy-and-update-record-expressions"></a>Kopírování a aktualizace záznamů výrazy

A *kopírování a aktualizace záznamů výraz* je výraz, který zkopíruje existující záznam, aktualizuje zadaná pole a vrátí aktualizované záznam.


## <a name="syntax"></a>Syntaxe

```fsharp
{ record-name with
    updated-member-definitions }
```

## <a name="remarks"></a>Poznámky
Záznamy jsou neměnné ve výchozím nastavení, tak, aby bylo možné žádná aktualizace s existujícím záznamem. K vytvoření záznamu aktualizovaný všechna pole záznamu muset zadat znovu. Pro zjednodušení této úlohy *kopírování a aktualizace záznamů výraz* lze použít. Tento výraz trvá existujícího záznamu, vytvoří novou stejného typu pomocí zadaná pole z výrazu a chybějící pole určeného výrazu.
To může být užitečné, když máte zkopírováním existujícího záznamu, a případně změnit některé hodnoty polí.

Proveďte pro instanci nově vytvořený záznam.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

Pokud byste chtěli aktualizovat pouze na pole daného záznamu můžete použít *kopírování a aktualizace záznamů výraz* podobně jako následující:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a>Viz také
[Záznamy](records.md)

[Referenční dokumentace jazyka F#](index.md)
