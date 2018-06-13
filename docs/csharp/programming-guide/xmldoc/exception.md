---
title: '&lt;výjimka&gt; (C# Průvodce programováním)'
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: eca61416077896c9fa7d5828bbab79b399ad69d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332657"
---
# <a name="ltexceptiongt-c-programming-guide"></a><span data-ttu-id="8fd34-102">&lt;výjimka&gt; (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="8fd34-102">&lt;exception&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="8fd34-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8fd34-103">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8fd34-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="8fd34-104">Parameters</span></span>  
 <span data-ttu-id="8fd34-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="8fd34-105">cref = " `member`"</span></span>  
 <span data-ttu-id="8fd34-106">Odkaz na výjimku, která je k dispozici z aktuální prostředí kompilace.</span><span class="sxs-lookup"><span data-stu-id="8fd34-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="8fd34-107">Kompilátor kontroluje, zda výjimka existuje a překládá `member` na element kanonický název ve výstupu XML.</span><span class="sxs-lookup"><span data-stu-id="8fd34-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="8fd34-108">`member` musí být v rámci dvojitých uvozovek nahoře ("").</span><span class="sxs-lookup"><span data-stu-id="8fd34-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="8fd34-109">Další informace o tom, jak vytvořit cref odkaz na obecného typu najdete v tématu [ \<najdete v části >](../../../csharp/programming-guide/xmldoc/see.md).</span><span class="sxs-lookup"><span data-stu-id="8fd34-109">For more information on how to create a cref reference to a generic type, see [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span></span>  
  
 `description`  
 <span data-ttu-id="8fd34-110">Popis výjimky.</span><span class="sxs-lookup"><span data-stu-id="8fd34-110">A description of the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8fd34-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8fd34-111">Remarks</span></span>  
 <span data-ttu-id="8fd34-112">\<Výjimka > značka umožňuje určit výjimek, které může být vyvolána.</span><span class="sxs-lookup"><span data-stu-id="8fd34-112">The \<exception> tag lets you specify which exceptions can be thrown.</span></span> <span data-ttu-id="8fd34-113">Tato značka můžete použít pro definice pro metody, vlastnosti, události a indexery.</span><span class="sxs-lookup"><span data-stu-id="8fd34-113">This tag can be applied to definitions for methods, properties, events, and indexers.</span></span>  
  
 <span data-ttu-id="8fd34-114">Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="8fd34-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
 <span data-ttu-id="8fd34-115">Další informace o zpracování výjimek najdete v tématu [výjimky a zpracování výjimek](../../../csharp/programming-guide/exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="8fd34-115">For more information about exception handling, see [Exceptions and Exception Handling](../../../csharp/programming-guide/exceptions/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8fd34-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="8fd34-116">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#4](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/exception_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="8fd34-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="8fd34-117">See Also</span></span>  
 [<span data-ttu-id="8fd34-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="8fd34-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8fd34-119">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="8fd34-119">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
