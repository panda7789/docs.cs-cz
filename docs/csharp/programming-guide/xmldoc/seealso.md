---
title: <seealso> – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cref
- <seealso>
- seealso
helpviewer_keywords:
- cref [C#], see also
- seealso C# XML tag
- cref [C#]
- cross-references [C#], tags
- <seealso> C# XML tag
ms.assetid: 8e157f3f-f220-4fcf-9010-88905b080b18
ms.openlocfilehash: 3ddaa7efec2b4bf5ffa53971aa6f380a1be9bad8
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587658"
---
# <a name="seealso-c-programming-guide"></a><span data-ttu-id="a5fa5-102">\<SeeAlso > (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="a5fa5-102">\<seealso> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="a5fa5-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5fa5-103">Syntax</span></span>  
  
```xml  
<seealso cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5fa5-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="a5fa5-104">Parameters</span></span>  
 <span data-ttu-id="a5fa5-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="a5fa5-105">cref = " `member`"</span></span>  
 <span data-ttu-id="a5fa5-106">Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="a5fa5-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="a5fa5-107">Kompilátor kontroluje, zda daný prvek kódu existuje a zda předává `member` do názvu prvku ve výstupním souboru XML.`member`</span><span class="sxs-lookup"><span data-stu-id="a5fa5-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.`member`</span></span> <span data-ttu-id="a5fa5-108">v uvozovkách ("") se musí vyskytovat.</span><span class="sxs-lookup"><span data-stu-id="a5fa5-108">must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="a5fa5-109">Informace o tom, jak vytvořit odkaz cref na obecný typ, naleznete [ \<v tématu viz >](./see.md).</span><span class="sxs-lookup"><span data-stu-id="a5fa5-109">For information on how to create a cref reference to a generic type, see [\<see>](./see.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5fa5-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a5fa5-110">Remarks</span></span>  
 <span data-ttu-id="a5fa5-111">Značka \<> SeeAlso umožňuje určit text, který se může objevit v části Viz také.</span><span class="sxs-lookup"><span data-stu-id="a5fa5-111">The \<seealso> tag lets you specify the text that you might want to appear in a See Also section.</span></span> <span data-ttu-id="a5fa5-112">Pomocí položky Zobrazit > můžete zadat odkaz z textu. [ \<](./see.md)</span><span class="sxs-lookup"><span data-stu-id="a5fa5-112">Use [\<see>](./see.md) to specify a link from within text.</span></span>  
  
 <span data-ttu-id="a5fa5-113">Zkompilujte pomocí [/doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte dokumentační komentáře do souboru.</span><span class="sxs-lookup"><span data-stu-id="a5fa5-113">Compile with [/doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5fa5-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="a5fa5-114">Example</span></span>  
 <span data-ttu-id="a5fa5-115">Příklad použití\<SeeAlso > naleznete v tématu [ \<Summary >](./summary.md) .</span><span class="sxs-lookup"><span data-stu-id="a5fa5-115">See [\<summary>](./summary.md) for an example of using \<seealso>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5fa5-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a5fa5-116">See also</span></span>

- [<span data-ttu-id="a5fa5-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="a5fa5-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a5fa5-118">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="a5fa5-118">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
