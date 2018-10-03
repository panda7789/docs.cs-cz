---
title: '&lt;typeparam&gt; (C# Programming Guide)'
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: ec19060008c1c06c54c89dbddee7d24001bcdebc
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48046234"
---
# <a name="lttypeparamgt-c-programming-guide"></a><span data-ttu-id="5b27f-102">&lt;typeparam&gt; (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="5b27f-102">&lt;typeparam&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="5b27f-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b27f-103">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5b27f-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="5b27f-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="5b27f-105">Název parametru typu.</span><span class="sxs-lookup"><span data-stu-id="5b27f-105">The name of the type parameter.</span></span> <span data-ttu-id="5b27f-106">Název uzavřete do dvojitých uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="5b27f-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="5b27f-107">Popis pro parametr typu.</span><span class="sxs-lookup"><span data-stu-id="5b27f-107">A description for the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b27f-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5b27f-108">Remarks</span></span>  
 <span data-ttu-id="5b27f-109">`<typeparam>` Značky byste měli použít ve komentář pro obecný typ nebo metoda prohlášení k popisu parametr typu.</span><span class="sxs-lookup"><span data-stu-id="5b27f-109">The `<typeparam>` tag should be used in the comment for a generic type or method declaration to describe a type parameter.</span></span> <span data-ttu-id="5b27f-110">Přidáte značku pro každý typ parametru obecného typu nebo metody.</span><span class="sxs-lookup"><span data-stu-id="5b27f-110">Add a tag for each type parameter of the generic type or method.</span></span>  
  
 <span data-ttu-id="5b27f-111">Další informace najdete v tématu [obecných typů](../../../csharp/programming-guide/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="5b27f-111">For more information, see [Generics](../../../csharp/programming-guide/generics/index.md).</span></span>  
  
 <span data-ttu-id="5b27f-112">Text `<typeparam>` značky se zobrazí v IntelliSense, [okno prohlížeče objektů](https://msdn.microsoft.com/library/3c7f1673-1f0d-41b1-94ca-a3dcfcb82cda) kódu komentář webové sestavy.</span><span class="sxs-lookup"><span data-stu-id="5b27f-112">The text for the `<typeparam>` tag will be displayed in IntelliSense, the [Object Browser Window](https://msdn.microsoft.com/library/3c7f1673-1f0d-41b1-94ca-a3dcfcb82cda) code comment web report.</span></span>  
  
 <span data-ttu-id="5b27f-113">Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="5b27f-113">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b27f-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="5b27f-114">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#13](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/typeparam_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="5b27f-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="5b27f-115">See Also</span></span>

- [<span data-ttu-id="5b27f-116">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5b27f-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="5b27f-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="5b27f-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="5b27f-118">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="5b27f-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
