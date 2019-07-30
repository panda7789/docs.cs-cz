---
title: Kopírování a aktualizace výrazů záznamů
description: Přečtěte si, jak napsat výraz kopírování a aktualizace, který zkopíruje existující záznam nebo anonymní záznam, aktualizuje zadaná pole a vrátí aktualizovaný záznam nebo anonymní záznam.
author: ChrSteinert
ms.date: 06/12/2019
ms.openlocfilehash: dfb20a6ff8282ae5988772cc0f0841db23aad942
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630374"
---
# <a name="copy-and-update-record-expressions"></a>Kopírování a aktualizace výrazů záznamů

*Výraz záznamu kopírování a aktualizace* je výraz, který zkopíruje existující záznam, aktualizuje zadaná pole a vrátí aktualizovaný záznam.

## <a name="syntax"></a>Syntaxe

```fsharp
{ record-name with
    updated-labels }

{| anonymous-record-name with
    updated-labels |}
```

## <a name="remarks"></a>Poznámky

Záznamy a anonymní záznamy jsou ve výchozím nastavení neměnné, takže není možné aktualizovat existující záznam. Chcete-li vytvořit aktualizovaný záznam, bude nutné znovu zadat všechna pole záznamu. Pro zjednodušení této úlohy lze použít *výraz kopírování a aktualizace* . Tento výraz přebírá existující záznam, vytvoří nový stejný typ pomocí zadaných polí z výrazu a chybějící pole určené výrazem.

To může být užitečné v případě, že je nutné zkopírovat existující záznam a případně změnit některé hodnoty polí.

Proveďte instanci nově vytvořeného záznamu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

Pokud jste chtěli aktualizovat pouze v poli tohoto záznamu, můžete použít *výraz záznamu kopírování a aktualizace* , jako je následující:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a>Viz také:

- [Záznamy](records.md)
- [Anonymní záznamy](anonymous-records.md)
- [Referenční dokumentace jazyka F#](index.md)
