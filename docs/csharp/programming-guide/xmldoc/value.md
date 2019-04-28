---
title: <value> - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 7f82008d000bf0316b505bfc5d40e9e64b2685a3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675796"
---
# <a name="value-c-programming-guide"></a><span data-ttu-id="84c1a-102">\<Hodnota > (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="84c1a-102">\<value> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="84c1a-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84c1a-103">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a><span data-ttu-id="84c1a-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="84c1a-104">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="84c1a-105">Popis pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="84c1a-105">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84c1a-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="84c1a-106">Remarks</span></span>  
 <span data-ttu-id="84c1a-107">\<Hodnota > značky umožňuje popisují hodnotu, která představuje vlastnost.</span><span class="sxs-lookup"><span data-stu-id="84c1a-107">The \<value> tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="84c1a-108">Všimněte si, že při přidání vlastnosti prostřednictvím Průvodce kódem ve vývojovém prostředí sady Visual Studio .NET, přidá [ \<summary >](../../../csharp/programming-guide/xmldoc/summary.md) značky pro novou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="84c1a-108">Note that when you add a property via code wizard in the Visual Studio .NET development environment, it will add a [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="84c1a-109">Měli byste pak ručně přidat \<hodnota > značka, které popisují hodnotu, která představuje vlastnost.</span><span class="sxs-lookup"><span data-stu-id="84c1a-109">You should then manually add a \<value> tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="84c1a-110">Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="84c1a-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84c1a-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="84c1a-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]  
  
## <a name="see-also"></a><span data-ttu-id="84c1a-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="84c1a-112">See also</span></span>

- [<span data-ttu-id="84c1a-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="84c1a-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="84c1a-114">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="84c1a-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
