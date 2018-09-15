---
title: 'Kopírování a aktualizace záznamu výrazy (F #)'
description: Další informace o zápisu "kopírování a aktualizace záznamu výraz", který zkopíruje existující záznam, aktualizace zadaná pole a vrátí aktualizovaný záznam.
author: ChrSteinert
ms.date: 06/04/2016
ms.openlocfilehash: d2b089e8a7fc5c7ee26139003e23d2eaa8a3174e
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/15/2018
ms.locfileid: "45638344"
---
# <a name="copy-and-update-record-expressions"></a><span data-ttu-id="88569-103">Kopírování a aktualizace výrazů záznamů</span><span class="sxs-lookup"><span data-stu-id="88569-103">Copy and Update Record Expressions</span></span>

<span data-ttu-id="88569-104">A *kopírování a aktualizace výrazů záznamů* je výraz, který zkopíruje existující záznam, aktualizuje zadaná pole a vrátí aktualizovaný záznam.</span><span class="sxs-lookup"><span data-stu-id="88569-104">A *copy and update record expression* is an expression that copies an existing record, updates specified fields, and returns the updated record.</span></span>

## <a name="syntax"></a><span data-ttu-id="88569-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88569-105">Syntax</span></span>

```fsharp
{ record-name with
    updated-member-definitions }
```

## <a name="remarks"></a><span data-ttu-id="88569-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="88569-106">Remarks</span></span>

<span data-ttu-id="88569-107">Záznamy jsou neměnné ve výchozím nastavení, takže není možné žádná aktualizace s existujícím záznamem.</span><span class="sxs-lookup"><span data-stu-id="88569-107">Records are immutable by default, so that there is no update to an existing record possible.</span></span> <span data-ttu-id="88569-108">Chcete-li vytvořit všechna pole záznamu aktualizovaný záznam byste museli znovu zadat.</span><span class="sxs-lookup"><span data-stu-id="88569-108">To create an updated record all the fields of a record would have to be specified again.</span></span> <span data-ttu-id="88569-109">Pro zjednodušení tohoto úkolu *kopírování a aktualizace výrazů záznamů* lze použít.</span><span class="sxs-lookup"><span data-stu-id="88569-109">To simplify this task a *copy and update record expression* can be used.</span></span> <span data-ttu-id="88569-110">Tento výraz má existující záznam, vytvoří nový stejného typu pomocí zadaná pole z výrazu a chybějící pole určeného výrazu.</span><span class="sxs-lookup"><span data-stu-id="88569-110">This expression takes an existing record, creates a new one of the same type by using specified fields from the expression and the missing field specified by the expression.</span></span>
<span data-ttu-id="88569-111">To může být užitečné, když je nutné zkopírovat existující záznam a případně změnit některé z hodnot pole.</span><span class="sxs-lookup"><span data-stu-id="88569-111">This can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span>

<span data-ttu-id="88569-112">Provést pro instanci nově vytvořený záznam.</span><span class="sxs-lookup"><span data-stu-id="88569-112">Take for instance a newly created record.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="88569-113">Pokud chcete aktualizovat pouze na pole daného záznamu můžete použít *kopírování a aktualizace výrazů záznamů* podobně jako následující:</span><span class="sxs-lookup"><span data-stu-id="88569-113">If you were to update only on field of that record you could use the *copy and update record expression* like the following:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a><span data-ttu-id="88569-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="88569-114">See also</span></span>

- [<span data-ttu-id="88569-115">Záznamy</span><span class="sxs-lookup"><span data-stu-id="88569-115">Records</span></span>](records.md)
- [<span data-ttu-id="88569-116">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="88569-116">F# Language Reference</span></span>](index.md)
