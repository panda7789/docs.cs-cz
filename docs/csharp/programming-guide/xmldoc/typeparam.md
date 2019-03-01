---
title: <typeparam> - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: 9150ab3e29eaa6b692e2ab2be90bb0e87ba54941
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978643"
---
# <a name="typeparam-c-programming-guide"></a><span data-ttu-id="ba677-102">\<typeparam > (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="ba677-102">\<typeparam> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="ba677-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba677-103">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ba677-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="ba677-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="ba677-105">Název parametru typu.</span><span class="sxs-lookup"><span data-stu-id="ba677-105">The name of the type parameter.</span></span> <span data-ttu-id="ba677-106">Název uzavřete do dvojitých uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="ba677-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="ba677-107">Popis pro parametr typu.</span><span class="sxs-lookup"><span data-stu-id="ba677-107">A description for the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba677-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ba677-108">Remarks</span></span>  
 <span data-ttu-id="ba677-109">`<typeparam>` Značky byste měli použít ve komentář pro obecný typ nebo metoda prohlášení k popisu parametr typu.</span><span class="sxs-lookup"><span data-stu-id="ba677-109">The `<typeparam>` tag should be used in the comment for a generic type or method declaration to describe a type parameter.</span></span> <span data-ttu-id="ba677-110">Přidáte značku pro každý typ parametru obecného typu nebo metody.</span><span class="sxs-lookup"><span data-stu-id="ba677-110">Add a tag for each type parameter of the generic type or method.</span></span>  
  
 <span data-ttu-id="ba677-111">Další informace najdete v tématu [obecných typů](../../../csharp/programming-guide/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="ba677-111">For more information, see [Generics](../../../csharp/programming-guide/generics/index.md).</span></span>  
  
 <span data-ttu-id="ba677-112">Text `<typeparam>` značky se zobrazí v IntelliSense, [okno prohlížeče objektů](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) kódu komentář webové sestavy.</span><span class="sxs-lookup"><span data-stu-id="ba677-112">The text for the `<typeparam>` tag will be displayed in IntelliSense, the [Object Browser Window](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) code comment web report.</span></span>  
  
 <span data-ttu-id="ba677-113">Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="ba677-113">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba677-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="ba677-114">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]  
  
## <a name="see-also"></a><span data-ttu-id="ba677-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ba677-115">See also</span></span>

- [<span data-ttu-id="ba677-116">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ba677-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="ba677-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="ba677-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="ba677-118">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="ba677-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
