---
title: <seealso> - C# Průvodce programováním
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
ms.openlocfilehash: cccb338d2dbed7889512428a53804324795c66bd
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498286"
---
# <a name="seealso-c-programming-guide"></a><span data-ttu-id="451b3-102">\<SeeAlso > (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="451b3-102">\<seealso> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="451b3-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="451b3-103">Syntax</span></span>  
  
```xml  
<seealso cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="451b3-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="451b3-104">Parameters</span></span>  
 <span data-ttu-id="451b3-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="451b3-105">cref = " `member`"</span></span>  
 <span data-ttu-id="451b3-106">Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="451b3-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="451b3-107">Kompilátor kontroluje, zda daný prvek kódu existuje a zda předává `member` do názvu prvku ve výstupním souboru XML.`member`</span><span class="sxs-lookup"><span data-stu-id="451b3-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.`member`</span></span> <span data-ttu-id="451b3-108">musí být uvedena v uvozovkách ("").</span><span class="sxs-lookup"><span data-stu-id="451b3-108">must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="451b3-109">Informace o tom, jak vytvořit cref odkaz na obecný typ, naleznete v tématu [ \<naleznete v tématu >](../../../csharp/programming-guide/xmldoc/see.md).</span><span class="sxs-lookup"><span data-stu-id="451b3-109">For information on how to create a cref reference to a generic type, see [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="451b3-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="451b3-110">Remarks</span></span>  
 <span data-ttu-id="451b3-111">\<Seealso > značky umožňuje zadat text, který chcete zobrazit v části Viz také.</span><span class="sxs-lookup"><span data-stu-id="451b3-111">The \<seealso> tag lets you specify the text that you might want to appear in a See Also section.</span></span> <span data-ttu-id="451b3-112">Použití [ \<naleznete v tématu >](../../../csharp/programming-guide/xmldoc/see.md) zadat odkaz v rámci textu.</span><span class="sxs-lookup"><span data-stu-id="451b3-112">Use [\<see>](../../../csharp/programming-guide/xmldoc/see.md) to specify a link from within text.</span></span>  
  
 <span data-ttu-id="451b3-113">Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="451b3-113">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="451b3-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="451b3-114">Example</span></span>  
 <span data-ttu-id="451b3-115">Zobrazit [ \<summary >](../../../csharp/programming-guide/xmldoc/summary.md) pro příklad použití \<seealso >.</span><span class="sxs-lookup"><span data-stu-id="451b3-115">See [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) for an example of using \<seealso>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="451b3-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="451b3-116">See also</span></span>

- [<span data-ttu-id="451b3-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="451b3-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="451b3-118">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="451b3-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
