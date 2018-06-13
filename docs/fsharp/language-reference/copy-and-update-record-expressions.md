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
# <a name="copy-and-update-record-expressions"></a><span data-ttu-id="a1066-103">Kopírování a aktualizace záznamů výrazy</span><span class="sxs-lookup"><span data-stu-id="a1066-103">Copy and Update Record Expressions</span></span>

<span data-ttu-id="a1066-104">A *kopírování a aktualizace záznamů výraz* je výraz, který zkopíruje existující záznam, aktualizuje zadaná pole a vrátí aktualizované záznam.</span><span class="sxs-lookup"><span data-stu-id="a1066-104">A *copy and update record expression* is an expression that copies an existing record, updates specified fields, and returns the updated record.</span></span>


## <a name="syntax"></a><span data-ttu-id="a1066-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1066-105">Syntax</span></span>

```fsharp
{ record-name with
    updated-member-definitions }
```

## <a name="remarks"></a><span data-ttu-id="a1066-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a1066-106">Remarks</span></span>
<span data-ttu-id="a1066-107">Záznamy jsou neměnné ve výchozím nastavení, tak, aby bylo možné žádná aktualizace s existujícím záznamem.</span><span class="sxs-lookup"><span data-stu-id="a1066-107">Records are immutable by default, so that there is no update to an existing record possible.</span></span> <span data-ttu-id="a1066-108">K vytvoření záznamu aktualizovaný všechna pole záznamu muset zadat znovu.</span><span class="sxs-lookup"><span data-stu-id="a1066-108">To create an updated record all the fields of a record would have to be specified again.</span></span> <span data-ttu-id="a1066-109">Pro zjednodušení této úlohy *kopírování a aktualizace záznamů výraz* lze použít.</span><span class="sxs-lookup"><span data-stu-id="a1066-109">To simplify this task a *copy and update record expression* can be used.</span></span> <span data-ttu-id="a1066-110">Tento výraz trvá existujícího záznamu, vytvoří novou stejného typu pomocí zadaná pole z výrazu a chybějící pole určeného výrazu.</span><span class="sxs-lookup"><span data-stu-id="a1066-110">This expression takes an existing record, creates a new one of the same type by using specified fields from the expression and the missing field specified by the expression.</span></span>
<span data-ttu-id="a1066-111">To může být užitečné, když máte zkopírováním existujícího záznamu, a případně změnit některé hodnoty polí.</span><span class="sxs-lookup"><span data-stu-id="a1066-111">This can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span>

<span data-ttu-id="a1066-112">Proveďte pro instanci nově vytvořený záznam.</span><span class="sxs-lookup"><span data-stu-id="a1066-112">Take for instance a newly created record.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="a1066-113">Pokud byste chtěli aktualizovat pouze na pole daného záznamu můžete použít *kopírování a aktualizace záznamů výraz* podobně jako následující:</span><span class="sxs-lookup"><span data-stu-id="a1066-113">If you were to update only on field of that record you could use the *copy and update record expression* like the following:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a><span data-ttu-id="a1066-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="a1066-114">See Also</span></span>
[<span data-ttu-id="a1066-115">Záznamy</span><span class="sxs-lookup"><span data-stu-id="a1066-115">Records</span></span>](records.md)

[<span data-ttu-id="a1066-116">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="a1066-116">F# Language Reference</span></span>](index.md)
