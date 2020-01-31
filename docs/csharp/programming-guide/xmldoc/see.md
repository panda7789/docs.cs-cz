---
title: Průvodce C# programováním <see>
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
ms.openlocfilehash: 17d1d344b9a27ffd4995fa4849ee6d5ce7f90f29
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789693"
---
# <a name="see-c-programming-guide"></a><span data-ttu-id="7efc9-102">\<najdete v >C# (Průvodce programováním).</span><span class="sxs-lookup"><span data-stu-id="7efc9-102">\<see> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="7efc9-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7efc9-103">Syntax</span></span>

```xml
<see cref="member"/>
```

## <a name="parameters"></a><span data-ttu-id="7efc9-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="7efc9-104">Parameters</span></span>

- <span data-ttu-id="7efc9-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="7efc9-105">cref = " `member`"</span></span>

  <span data-ttu-id="7efc9-106">Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="7efc9-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="7efc9-107">Kompilátor zkontroluje, zda daný prvek kódu existuje a předá `member` k názvu elementu ve výstupním souboru XML.</span><span class="sxs-lookup"><span data-stu-id="7efc9-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="7efc9-108">Umístit *člena* v uvozovkách ("").</span><span class="sxs-lookup"><span data-stu-id="7efc9-108">Place *member* within double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="7efc9-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7efc9-109">Remarks</span></span>

<span data-ttu-id="7efc9-110">\<Zobrazit značku > umožňuje zadat odkaz v rámci textu.</span><span class="sxs-lookup"><span data-stu-id="7efc9-110">The \<see> tag lets you specify a link from within text.</span></span> <span data-ttu-id="7efc9-111">Použijte [\<seealso >](./seealso.md) k označení toho, že text by měl být umístěn v části Viz také.</span><span class="sxs-lookup"><span data-stu-id="7efc9-111">Use [\<seealso>](./seealso.md) to indicate that text should be placed in a See Also section.</span></span> <span data-ttu-id="7efc9-112">Pomocí [atributu cref](./cref-attribute.md) můžete vytvořit interní hypertextové odkazy na stránky dokumentace pro prvky kódu.</span><span class="sxs-lookup"><span data-stu-id="7efc9-112">Use the [cref Attribute](./cref-attribute.md) to create internal hyperlinks to documentation pages for code elements.</span></span>

<span data-ttu-id="7efc9-113">Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="7efc9-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

<span data-ttu-id="7efc9-114">Následující příklad ukazuje \<zobrazení značky > v rámci oddílu Summary.</span><span class="sxs-lookup"><span data-stu-id="7efc9-114">The following example shows a \<see> tag within a summary section.</span></span>

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

## <a name="see-also"></a><span data-ttu-id="7efc9-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7efc9-115">See also</span></span>

- [<span data-ttu-id="7efc9-116">C#Průvodce programováním</span><span class="sxs-lookup"><span data-stu-id="7efc9-116">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="7efc9-117">Doporučené značky pro dokumentační komentáře</span><span class="sxs-lookup"><span data-stu-id="7efc9-117">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
