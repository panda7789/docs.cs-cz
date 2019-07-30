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
# <a name="copy-and-update-record-expressions"></a><span data-ttu-id="43d70-103">Kopírování a aktualizace výrazů záznamů</span><span class="sxs-lookup"><span data-stu-id="43d70-103">Copy and Update Record Expressions</span></span>

<span data-ttu-id="43d70-104">*Výraz záznamu kopírování a aktualizace* je výraz, který zkopíruje existující záznam, aktualizuje zadaná pole a vrátí aktualizovaný záznam.</span><span class="sxs-lookup"><span data-stu-id="43d70-104">A *copy and update record expression* is an expression that copies an existing record, updates specified fields, and returns the updated record.</span></span>

## <a name="syntax"></a><span data-ttu-id="43d70-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43d70-105">Syntax</span></span>

```fsharp
{ record-name with
    updated-labels }

{| anonymous-record-name with
    updated-labels |}
```

## <a name="remarks"></a><span data-ttu-id="43d70-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="43d70-106">Remarks</span></span>

<span data-ttu-id="43d70-107">Záznamy a anonymní záznamy jsou ve výchozím nastavení neměnné, takže není možné aktualizovat existující záznam.</span><span class="sxs-lookup"><span data-stu-id="43d70-107">Records and anonymous records are immutable by default, so that there is no update to an existing record possible.</span></span> <span data-ttu-id="43d70-108">Chcete-li vytvořit aktualizovaný záznam, bude nutné znovu zadat všechna pole záznamu.</span><span class="sxs-lookup"><span data-stu-id="43d70-108">To create an updated record all the fields of a record would have to be specified again.</span></span> <span data-ttu-id="43d70-109">Pro zjednodušení této úlohy lze použít *výraz kopírování a aktualizace* .</span><span class="sxs-lookup"><span data-stu-id="43d70-109">To simplify this task a *copy and update expression* can be used.</span></span> <span data-ttu-id="43d70-110">Tento výraz přebírá existující záznam, vytvoří nový stejný typ pomocí zadaných polí z výrazu a chybějící pole určené výrazem.</span><span class="sxs-lookup"><span data-stu-id="43d70-110">This expression takes an existing record, creates a new one of the same type by using specified fields from the expression and the missing field specified by the expression.</span></span>

<span data-ttu-id="43d70-111">To může být užitečné v případě, že je nutné zkopírovat existující záznam a případně změnit některé hodnoty polí.</span><span class="sxs-lookup"><span data-stu-id="43d70-111">This can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span>

<span data-ttu-id="43d70-112">Proveďte instanci nově vytvořeného záznamu.</span><span class="sxs-lookup"><span data-stu-id="43d70-112">Take for instance a newly created record.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="43d70-113">Pokud jste chtěli aktualizovat pouze v poli tohoto záznamu, můžete použít *výraz záznamu kopírování a aktualizace* , jako je následující:</span><span class="sxs-lookup"><span data-stu-id="43d70-113">If you were to update only on field of that record you could use the *copy and update record expression* like the following:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a><span data-ttu-id="43d70-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="43d70-114">See also</span></span>

- [<span data-ttu-id="43d70-115">Záznamy</span><span class="sxs-lookup"><span data-stu-id="43d70-115">Records</span></span>](records.md)
- [<span data-ttu-id="43d70-116">Anonymní záznamy</span><span class="sxs-lookup"><span data-stu-id="43d70-116">Anonymous Records</span></span>](anonymous-records.md)
- [<span data-ttu-id="43d70-117">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="43d70-117">F# Language Reference</span></span>](index.md)
