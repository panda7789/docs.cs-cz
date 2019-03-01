---
title: <see> - C# Průvodce programováním
ms.custom: seodec18
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
ms.openlocfilehash: 1816aeb0ddf783c8ad0baa7f5d460f0fc60747e1
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974819"
---
# <a name="see-c-programming-guide"></a><span data-ttu-id="9b030-102">\<Zobrazit > (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="9b030-102">\<see> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="9b030-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b030-103">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9b030-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="9b030-104">Parameters</span></span>  
 <span data-ttu-id="9b030-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="9b030-105">cref = " `member`"</span></span>  
 <span data-ttu-id="9b030-106">Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="9b030-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="9b030-107">Kompilátor kontroluje, zda daný prvek kódu existuje a předá `member` do názvu prvku ve výstupním souboru XML.</span><span class="sxs-lookup"><span data-stu-id="9b030-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="9b030-108">Místo *člen* do dvojitých uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="9b030-108">Place *member* within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b030-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9b030-109">Remarks</span></span>  
 <span data-ttu-id="9b030-110">\<Naleznete v tématu > značky umožňuje zadat odkaz v rámci textu.</span><span class="sxs-lookup"><span data-stu-id="9b030-110">The \<see> tag lets you specify a link from within text.</span></span> <span data-ttu-id="9b030-111">Použití [ \<seealso >](../../../csharp/programming-guide/xmldoc/seealso.md) označit, že text by měl být umístěno v části Viz také.</span><span class="sxs-lookup"><span data-stu-id="9b030-111">Use [\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md) to indicate that text should be placed in a See Also section.</span></span> <span data-ttu-id="9b030-112">Použití [cref – atribut](../../../csharp/programming-guide/xmldoc/cref-attribute.md) k vytvoření interních hypertextových odkazů na stránky dokumentace prvků kódu.</span><span class="sxs-lookup"><span data-stu-id="9b030-112">Use the [cref Attribute](../../../csharp/programming-guide/xmldoc/cref-attribute.md) to create internal hyperlinks to documentation pages for code elements.</span></span>  
  
 <span data-ttu-id="9b030-113">Kompilovat s [-doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="9b030-113">Compile with [-doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
 <span data-ttu-id="9b030-114">Následující příklad ukazuje \<naleznete v tématu > značky v souhrnné části.</span><span class="sxs-lookup"><span data-stu-id="9b030-114">The following example shows a \<see> tag within a summary section.</span></span>  
  
 [!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]  
  
## <a name="see-also"></a><span data-ttu-id="9b030-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9b030-115">See also</span></span>

- [<span data-ttu-id="9b030-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="9b030-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="9b030-117">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="9b030-117">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
