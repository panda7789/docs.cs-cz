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
# <a name="copy-and-update-record-expressions"></a><span data-ttu-id="f6a3d-104">Kopírování a aktualizace záznamů výrazy</span><span class="sxs-lookup"><span data-stu-id="f6a3d-104">Copy and Update Record Expressions</span></span>

<span data-ttu-id="f6a3d-105">A *kopírování a aktualizace záznamů výraz* je výraz, který zkopíruje existující záznam, aktualizuje zadaná pole a vrátí aktualizované záznam.</span><span class="sxs-lookup"><span data-stu-id="f6a3d-105">A *copy and update record expression* is an expression that copies an existing record, updates specified fields, and returns the updated record.</span></span>


## <a name="syntax"></a><span data-ttu-id="f6a3d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6a3d-106">Syntax</span></span>

```fsharp
{ record-name with
    updated-member-definitions }
```

## <a name="remarks"></a><span data-ttu-id="f6a3d-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f6a3d-107">Remarks</span></span>
<span data-ttu-id="f6a3d-108">Záznamy jsou neměnné ve výchozím nastavení, tak, aby bylo možné žádná aktualizace s existujícím záznamem.</span><span class="sxs-lookup"><span data-stu-id="f6a3d-108">Records are immutable by default, so that there is no update to an existing record possible.</span></span> <span data-ttu-id="f6a3d-109">K vytvoření záznamu aktualizovaný všechna pole záznamu muset zadat znovu.</span><span class="sxs-lookup"><span data-stu-id="f6a3d-109">To create an updated record all the fields of a record would have to be specified again.</span></span> <span data-ttu-id="f6a3d-110">Pro zjednodušení této úlohy *kopírování a aktualizace záznamů výraz* lze použít.</span><span class="sxs-lookup"><span data-stu-id="f6a3d-110">To simplify this task a *copy and update record expression* can be used.</span></span> <span data-ttu-id="f6a3d-111">Tento výraz trvá existujícího záznamu, vytvoří novou stejného typu pomocí zadaná pole z výrazu a chybějící pole určeného výrazu.</span><span class="sxs-lookup"><span data-stu-id="f6a3d-111">This expression takes an existing record, creates a new one of the same type by using specified fields from the expression and the missing field specified by the expression.</span></span>
<span data-ttu-id="f6a3d-112">To může být užitečné, když máte zkopírováním existujícího záznamu, a případně změnit některé hodnoty polí.</span><span class="sxs-lookup"><span data-stu-id="f6a3d-112">This can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span>

<span data-ttu-id="f6a3d-113">Proveďte pro instanci nově vytvořený záznam.</span><span class="sxs-lookup"><span data-stu-id="f6a3d-113">Take for instance a newly created record.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="f6a3d-114">Pokud byste chtěli aktualizovat pouze na pole daného záznamu můžete použít *kopírování a aktualizace záznamů výraz* podobně jako následující:</span><span class="sxs-lookup"><span data-stu-id="f6a3d-114">If you were to update only on field of that record you could use the *copy and update record expression* like the following:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a><span data-ttu-id="f6a3d-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="f6a3d-115">See Also</span></span>
[<span data-ttu-id="f6a3d-116">Záznamy</span><span class="sxs-lookup"><span data-stu-id="f6a3d-116">Records</span></span>](records.md)

[<span data-ttu-id="f6a3d-117">Referenční dokumentace jazyka F #</span><span class="sxs-lookup"><span data-stu-id="f6a3d-117">F# Language Reference</span></span>](index.md)
