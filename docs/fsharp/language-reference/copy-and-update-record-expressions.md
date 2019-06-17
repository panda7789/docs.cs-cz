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
# <a name="copy-and-update-record-expressions"></a><span data-ttu-id="878de-103">Kopírování a aktualizace výrazů záznamů</span><span class="sxs-lookup"><span data-stu-id="878de-103">Copy and Update Record Expressions</span></span>

<span data-ttu-id="878de-104">A *kopírování a aktualizace výrazů záznamů* je výraz, který zkopíruje existující záznam, aktualizuje zadaná pole a vrátí aktualizovaný záznam.</span><span class="sxs-lookup"><span data-stu-id="878de-104">A *copy and update record expression* is an expression that copies an existing record, updates specified fields, and returns the updated record.</span></span>

## <a name="syntax"></a><span data-ttu-id="878de-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="878de-105">Syntax</span></span>

```fsharp
{ record-name with
    updated-labels }

{| anonymous-record-name with
    updated-labels |}
```

## <a name="remarks"></a><span data-ttu-id="878de-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="878de-106">Remarks</span></span>

<span data-ttu-id="878de-107">Anonymní záznamů a záznamů jsou neměnné ve výchozím nastavení, takže není možné žádná aktualizace s existujícím záznamem.</span><span class="sxs-lookup"><span data-stu-id="878de-107">Records and anonymous records are immutable by default, so that there is no update to an existing record possible.</span></span> <span data-ttu-id="878de-108">Chcete-li vytvořit všechna pole záznamu aktualizovaný záznam byste museli znovu zadat.</span><span class="sxs-lookup"><span data-stu-id="878de-108">To create an updated record all the fields of a record would have to be specified again.</span></span> <span data-ttu-id="878de-109">Pro zjednodušení tohoto úkolu *kopírování a aktualizace výrazů* lze použít.</span><span class="sxs-lookup"><span data-stu-id="878de-109">To simplify this task a *copy and update expression* can be used.</span></span> <span data-ttu-id="878de-110">Tento výraz má existující záznam, vytvoří nový stejného typu pomocí zadaná pole z výrazu a chybějící pole určeného výrazu.</span><span class="sxs-lookup"><span data-stu-id="878de-110">This expression takes an existing record, creates a new one of the same type by using specified fields from the expression and the missing field specified by the expression.</span></span>

<span data-ttu-id="878de-111">To může být užitečné, když je nutné zkopírovat existující záznam a případně změnit některé z hodnot pole.</span><span class="sxs-lookup"><span data-stu-id="878de-111">This can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span>

<span data-ttu-id="878de-112">Provést pro instanci nově vytvořený záznam.</span><span class="sxs-lookup"><span data-stu-id="878de-112">Take for instance a newly created record.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="878de-113">Pokud chcete aktualizovat pouze na pole daného záznamu můžete použít *kopírování a aktualizace výrazů záznamů* podobně jako následující:</span><span class="sxs-lookup"><span data-stu-id="878de-113">If you were to update only on field of that record you could use the *copy and update record expression* like the following:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a><span data-ttu-id="878de-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="878de-114">See also</span></span>

- [<span data-ttu-id="878de-115">Záznamy</span><span class="sxs-lookup"><span data-stu-id="878de-115">Records</span></span>](records.md)
- [<span data-ttu-id="878de-116">Anonymní záznamů</span><span class="sxs-lookup"><span data-stu-id="878de-116">Anonymous Records</span></span>](anonymous-records.md)
- [<span data-ttu-id="878de-117">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="878de-117">F# Language Reference</span></span>](index.md)
