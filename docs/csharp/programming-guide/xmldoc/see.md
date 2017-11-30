---
title: "&lt;v tématu&gt; (C# Průvodce programováním)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- <see>
- see
helpviewer_keywords:
- cref [C#], <see> tag
- <see> C# XML tag
- cross-references [C#]
- see C# XML tag
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 065c85ba411794858c8c4d70de0ac1467da1fe56
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltseegt-c-programming-guide"></a><span data-ttu-id="cfbcb-102">&lt;v tématu&gt; (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="cfbcb-102">&lt;see&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="cfbcb-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cfbcb-103">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cfbcb-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="cfbcb-104">Parameters</span></span>  
 <span data-ttu-id="cfbcb-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="cfbcb-105">cref = " `member`"</span></span>  
 <span data-ttu-id="cfbcb-106">Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="cfbcb-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="cfbcb-107">Kompilátor ověří, že element daného kódu existuje a předá `member` k názvu elementu ve výstupu XML. Místní *člen* v rámci dvojitých uvozovek nahoře ("").</span><span class="sxs-lookup"><span data-stu-id="cfbcb-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.Place *member* within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cfbcb-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cfbcb-108">Remarks</span></span>  
 <span data-ttu-id="cfbcb-109">\<Najdete v části > značka umožňuje zadat odkaz z v textu.</span><span class="sxs-lookup"><span data-stu-id="cfbcb-109">The \<see> tag lets you specify a link from within text.</span></span> <span data-ttu-id="cfbcb-110">Použití [ \<seealso >](../../../csharp/programming-guide/xmldoc/seealso.md) indikující, že text mají být umístěny v části Viz také.</span><span class="sxs-lookup"><span data-stu-id="cfbcb-110">Use [\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md) to indicate that text should be placed in a See Also section.</span></span> <span data-ttu-id="cfbcb-111">Použití [cref – atribut](../../../csharp/programming-guide/xmldoc/cref-attribute.md) k vytvoření interní hypertextové odkazy na stránky dokumentace pro elementy kódu.</span><span class="sxs-lookup"><span data-stu-id="cfbcb-111">Use the [cref Attribute](../../../csharp/programming-guide/xmldoc/cref-attribute.md) to create internal hyperlinks to documentation pages for code elements.</span></span>  
  
 <span data-ttu-id="cfbcb-112">Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="cfbcb-112">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
 <span data-ttu-id="cfbcb-113">Následující příklad ukazuje \<najdete v části > v části Souhrn značku.</span><span class="sxs-lookup"><span data-stu-id="cfbcb-113">The following example shows a \<see> tag within a summary section.</span></span>  
  
 [!code-csharp[csProgGuideDocComments#12](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/see_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="cfbcb-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="cfbcb-114">See Also</span></span>  
 [<span data-ttu-id="cfbcb-115">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="cfbcb-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="cfbcb-116">Doporučené značky pro dokumentační komentáře</span><span class="sxs-lookup"><span data-stu-id="cfbcb-116">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
