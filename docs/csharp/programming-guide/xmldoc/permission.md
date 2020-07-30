---
title: <permission> – Průvodce programováním v C#
description: Další informace o XML <permission> Inteligentní. Tato značka vám umožní zdokumentovat přístup člena, zatímco třída PermissionSet vám umožní určit přístup ke členu.
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: 38c87505b8b2973875e474ffd296dc02b7fb9de6
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381720"
---
# <a name="permission-c-programming-guide"></a><span data-ttu-id="93497-105">\<permission>(Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="93497-105">\<permission> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="93497-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93497-106">Syntax</span></span>

```xml
<permission cref="member">description</permission>
```

## <a name="parameters"></a><span data-ttu-id="93497-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="93497-107">Parameters</span></span>

- <span data-ttu-id="93497-108">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="93497-108">cref = " `member`"</span></span>

  <span data-ttu-id="93497-109">Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="93497-109">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="93497-110">Kompilátor kontroluje, zda daný prvek kódu existuje, a překládá se na `member` název kanonického prvku ve výstupním souboru XML.</span><span class="sxs-lookup"><span data-stu-id="93497-110">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="93497-111">*člen* musí být v uvozovkách ("").</span><span class="sxs-lookup"><span data-stu-id="93497-111">*member* must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="93497-112">Informace o tom, jak vytvořit odkaz cref na obecný typ, naleznete v tématu [atribut cref](./cref-attribute.md).</span><span class="sxs-lookup"><span data-stu-id="93497-112">For information on how to create a cref reference to a generic type, see [cref attribute](./cref-attribute.md).</span></span>

- `description`

  <span data-ttu-id="93497-113">Popis přístupu ke členovi.</span><span class="sxs-lookup"><span data-stu-id="93497-113">A description of the access to the member.</span></span>

## <a name="remarks"></a><span data-ttu-id="93497-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="93497-114">Remarks</span></span>

<span data-ttu-id="93497-115">`<permission>`Značka vám umožní dokumentovat přístup člena.</span><span class="sxs-lookup"><span data-stu-id="93497-115">The `<permission>` tag lets you document the access of a member.</span></span> <span data-ttu-id="93497-116"><xref:System.Security.PermissionSet>Třída umožňuje zadat přístup ke členu.</span><span class="sxs-lookup"><span data-stu-id="93497-116">The <xref:System.Security.PermissionSet> class lets you specify access to a member.</span></span>

<span data-ttu-id="93497-117">Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="93497-117">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="93497-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="93497-118">Example</span></span>

[!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]

## <a name="see-also"></a><span data-ttu-id="93497-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="93497-119">See also</span></span>

- [<span data-ttu-id="93497-120">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="93497-120">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="93497-121">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="93497-121">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
