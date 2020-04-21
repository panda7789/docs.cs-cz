---
title: Kopírování a aktualizace výrazů záznamů
description: Naučte se psát výraz kopírování a aktualizace, který kopíruje existující záznam nebo anonymní záznam, aktualizuje zadaná pole a vrací aktualizovaný nebo anonymní záznam.
author: ChrSteinert
ms.date: 06/12/2019
ms.openlocfilehash: bec3e0ac2fb34e358b199c509c4599b55d7bf35e
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739276"
---
# <a name="copy-and-update-record-expressions"></a><span data-ttu-id="84259-103">Kopírování a aktualizace výrazů záznamů</span><span class="sxs-lookup"><span data-stu-id="84259-103">Copy and Update Record Expressions</span></span>

<span data-ttu-id="84259-104">*Výraz záznamu kopírování a aktualizace* je výraz, který kopíruje existující záznam, aktualizuje zadaná pole a vrací aktualizovaný záznam.</span><span class="sxs-lookup"><span data-stu-id="84259-104">A *copy and update record expression* is an expression that copies an existing record, updates specified fields, and returns the updated record.</span></span>

## <a name="syntax"></a><span data-ttu-id="84259-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84259-105">Syntax</span></span>

```fsharp
{ record-name with
    updated-labels }

{| anonymous-record-name with
    updated-labels |}
```

## <a name="remarks"></a><span data-ttu-id="84259-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="84259-106">Remarks</span></span>

<span data-ttu-id="84259-107">Záznamy a anonymní záznamy jsou ve výchozím nastavení neměnné, takže není možné aktualizovat existující záznam.</span><span class="sxs-lookup"><span data-stu-id="84259-107">Records and anonymous records are immutable by default, so it is not possible to update an existing record.</span></span> <span data-ttu-id="84259-108">Chcete-li vytvořit aktualizovaný záznam, musí být znovu zadána všechna pole záznamu.</span><span class="sxs-lookup"><span data-stu-id="84259-108">To create an updated record all the fields of a record would have to be specified again.</span></span> <span data-ttu-id="84259-109">Pro zjednodušení tohoto úkolu lze použít *výraz kopírování a aktualizace.*</span><span class="sxs-lookup"><span data-stu-id="84259-109">To simplify this task a *copy and update expression* can be used.</span></span> <span data-ttu-id="84259-110">Tento výraz přebírá existující záznam, vytvoří nový stejného typu pomocí zadaných polí z výrazu a chybějícího pole určeného výrazem.</span><span class="sxs-lookup"><span data-stu-id="84259-110">This expression takes an existing record, creates a new one of the same type by using specified fields from the expression and the missing field specified by the expression.</span></span>

<span data-ttu-id="84259-111">To může být užitečné, pokud máte zkopírovat existující záznam a případně změnit některé hodnoty polí.</span><span class="sxs-lookup"><span data-stu-id="84259-111">This can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span>

<span data-ttu-id="84259-112">Vezměte například nově vytvořený záznam.</span><span class="sxs-lookup"><span data-stu-id="84259-112">Take for instance a newly created record.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="84259-113">Chcete-li aktualizovat pouze dvě pole v tomto záznamu, můžete použít *výraz kopírování a aktualizace záznamu*:</span><span class="sxs-lookup"><span data-stu-id="84259-113">To update only two fields in that record you can use the *copy and update record expression*:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a><span data-ttu-id="84259-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="84259-114">See also</span></span>

- [<span data-ttu-id="84259-115">Záznamy</span><span class="sxs-lookup"><span data-stu-id="84259-115">Records</span></span>](records.md)
- [<span data-ttu-id="84259-116">Anonymní záznamy</span><span class="sxs-lookup"><span data-stu-id="84259-116">Anonymous Records</span></span>](anonymous-records.md)
- [<span data-ttu-id="84259-117">Referenční příručka jazyka F#</span><span class="sxs-lookup"><span data-stu-id="84259-117">F# Language Reference</span></span>](index.md)
