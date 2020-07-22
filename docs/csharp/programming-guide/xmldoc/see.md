---
title: <see>– Průvodce programováním v C#
ms.date: 07/20/2015
f1_keywords:
- <see>
- see
helpviewer_keywords:
- cref [C#], <see> tag
- <see> C# XML tag
- cross-references [C#]
- see C# XML tag
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
ms.openlocfilehash: 731e42a6d4d354b043a56dbe150bb03a693a9454
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86863783"
---
# <a name="see-c-programming-guide"></a><span data-ttu-id="f724c-102">\<see>(Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="f724c-102">\<see> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="f724c-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f724c-103">Syntax</span></span>

```xml
<see cref="member"/>
```

## <a name="parameters"></a><span data-ttu-id="f724c-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="f724c-104">Parameters</span></span>

- <span data-ttu-id="f724c-105">cref = " `member` "</span><span class="sxs-lookup"><span data-stu-id="f724c-105">cref = "`member`"</span></span>

  <span data-ttu-id="f724c-106">Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="f724c-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="f724c-107">Kompilátor kontroluje, zda daný prvek kódu existuje a zda předává `member` do názvu prvku ve výstupním souboru XML.</span><span class="sxs-lookup"><span data-stu-id="f724c-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="f724c-108">Umístit *člena* v uvozovkách ("").</span><span class="sxs-lookup"><span data-stu-id="f724c-108">Place *member* within double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="f724c-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f724c-109">Remarks</span></span>

<span data-ttu-id="f724c-110">`<see>`Značka umožňuje zadat odkaz v rámci textu.</span><span class="sxs-lookup"><span data-stu-id="f724c-110">The `<see>` tag lets you specify a link from within text.</span></span> <span data-ttu-id="f724c-111">Použijte [\<seealso>](./seealso.md) k označení, že text by měl být umístěn v části Viz také.</span><span class="sxs-lookup"><span data-stu-id="f724c-111">Use [\<seealso>](./seealso.md) to indicate that text should be placed in a See Also section.</span></span> <span data-ttu-id="f724c-112">Pomocí [atributu cref](./cref-attribute.md) můžete vytvořit interní hypertextové odkazy na stránky dokumentace pro prvky kódu.</span><span class="sxs-lookup"><span data-stu-id="f724c-112">Use the [cref Attribute](./cref-attribute.md) to create internal hyperlinks to documentation pages for code elements.</span></span> <span data-ttu-id="f724c-113">Také ``href`` je platný atribut, který bude fungovat jako hypertextový odkaz.</span><span class="sxs-lookup"><span data-stu-id="f724c-113">Also, ``href`` is a valid Attribute that will function as a hyperlink.</span></span>

<span data-ttu-id="f724c-114">Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="f724c-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

<span data-ttu-id="f724c-115">Následující příklad ukazuje `<see>` značku v rámci oddílu Summary.</span><span class="sxs-lookup"><span data-stu-id="f724c-115">The following example shows a `<see>` tag within a summary section.</span></span>

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

## <a name="see-also"></a><span data-ttu-id="f724c-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="f724c-116">See also</span></span>

- [<span data-ttu-id="f724c-117">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="f724c-117">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="f724c-118">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="f724c-118">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
