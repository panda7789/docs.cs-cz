---
title: <permission> - Průvodce programováním jazyka C#
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: 4f76d28d5531c1b9f01fa950589407934cc1244a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093471"
---
# <a name="permission-c-programming-guide"></a><span data-ttu-id="da591-102">\<> oprávnění (průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="da591-102">\<permission> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="da591-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da591-103">Syntax</span></span>

```xml
<permission cref="member">description</permission>
```

## <a name="parameters"></a><span data-ttu-id="da591-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="da591-104">Parameters</span></span>

- <span data-ttu-id="da591-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="da591-105">cref = " `member`"</span></span>

  <span data-ttu-id="da591-106">Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="da591-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="da591-107">Kompilátor zkontroluje, zda daný prvek `member` kódu existuje, a překládá se do názvu kanonického prvku ve výstupním XML.</span><span class="sxs-lookup"><span data-stu-id="da591-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="da591-108">*člen* musí být uveden v uvozovkách (" ").</span><span class="sxs-lookup"><span data-stu-id="da591-108">*member* must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="da591-109">Informace o tom, jak vytvořit odkaz na obecný typ, naleznete v [atributu cref](./cref-attribute.md).</span><span class="sxs-lookup"><span data-stu-id="da591-109">For information on how to create a cref reference to a generic type, see [cref attribute](./cref-attribute.md).</span></span>

- `description`

  <span data-ttu-id="da591-110">Popis přístupu k členu.</span><span class="sxs-lookup"><span data-stu-id="da591-110">A description of the access to the member.</span></span>

## <a name="remarks"></a><span data-ttu-id="da591-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="da591-111">Remarks</span></span>

<span data-ttu-id="da591-112">Značka \<oprávnění> umožňuje dokumentovat přístup člena.</span><span class="sxs-lookup"><span data-stu-id="da591-112">The \<permission> tag lets you document the access of a member.</span></span> <span data-ttu-id="da591-113">Třída <xref:System.Security.PermissionSet> umožňuje určit přístup k členu.</span><span class="sxs-lookup"><span data-stu-id="da591-113">The <xref:System.Security.PermissionSet> class lets you specify access to a member.</span></span>

<span data-ttu-id="da591-114">Kompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentů komentáře do souboru.</span><span class="sxs-lookup"><span data-stu-id="da591-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="da591-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="da591-115">Example</span></span>

[!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]

## <a name="see-also"></a><span data-ttu-id="da591-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="da591-116">See also</span></span>

- [<span data-ttu-id="da591-117">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="da591-117">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="da591-118">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="da591-118">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
