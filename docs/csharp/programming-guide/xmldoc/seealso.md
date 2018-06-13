---
title: '&lt;Viz také&gt; (C# Průvodce programováním)'
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
ms.openlocfilehash: e3c9d68884e5cd4f5a4f81580f60cdde775458a3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349132"
---
# <a name="ltseealsogt-c-programming-guide"></a><span data-ttu-id="db617-102">&lt;Viz také&gt; (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="db617-102">&lt;seealso&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="db617-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db617-103">Syntax</span></span>  
  
```xml  
<seealso cref="member"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="db617-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="db617-104">Parameters</span></span>  
 <span data-ttu-id="db617-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="db617-105">cref = " `member`"</span></span>  
 <span data-ttu-id="db617-106">Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="db617-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="db617-107">Kompilátor kontroluje, zda daný prvek kódu existuje a zda předává `member` do názvu prvku ve výstupním souboru XML.`member`</span><span class="sxs-lookup"><span data-stu-id="db617-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.`member`</span></span> <span data-ttu-id="db617-108">musí být v rámci dvojitých uvozovek nahoře ("").</span><span class="sxs-lookup"><span data-stu-id="db617-108">must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="db617-109">Informace o tom, jak vytvořit cref odkaz na obecného typu najdete v tématu [ \<najdete v části >](../../../csharp/programming-guide/xmldoc/see.md).</span><span class="sxs-lookup"><span data-stu-id="db617-109">For information on how to create a cref reference to a generic type, see [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db617-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="db617-110">Remarks</span></span>  
 <span data-ttu-id="db617-111">\<Seealso > značka umožňuje zadat text, který chcete zobrazit v části Viz také.</span><span class="sxs-lookup"><span data-stu-id="db617-111">The \<seealso> tag lets you specify the text that you might want to appear in a See Also section.</span></span> <span data-ttu-id="db617-112">Použití [ \<najdete v části >](../../../csharp/programming-guide/xmldoc/see.md) zadat odkaz z v textu.</span><span class="sxs-lookup"><span data-stu-id="db617-112">Use [\<see>](../../../csharp/programming-guide/xmldoc/see.md) to specify a link from within text.</span></span>  
  
 <span data-ttu-id="db617-113">Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="db617-113">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db617-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="db617-114">Example</span></span>  
 <span data-ttu-id="db617-115">V tématu [ \<souhrnné >](../../../csharp/programming-guide/xmldoc/summary.md) příklad použití \<seealso >.</span><span class="sxs-lookup"><span data-stu-id="db617-115">See [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) for an example of using \<seealso>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db617-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="db617-116">See Also</span></span>  
 [<span data-ttu-id="db617-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="db617-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="db617-118">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="db617-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
