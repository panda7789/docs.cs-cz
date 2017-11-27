---
title: "Kopírování a aktualizace záznamů výrazy (F #)"
description: "Další informace o zápisu, kopírování a aktualizace záznamů výraz, který kopíruje existující aktualizace záznamů, zadaná pole a vrátí aktualizované záznam."
keywords: "Visual f #, f #, funkční programování"
author: ChrSteinert
ms.author: phcart
ms.date: 06/04/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: b5fc4ef0-64eb-4272-96a7-bb4dffbb634a
ms.openlocfilehash: 2eb51842b678780a1d6da96e237ebb92d1ea5cec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
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

[Referenční dokumentace jazyka F #](index.md)
