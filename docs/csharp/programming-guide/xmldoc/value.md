---
title: '&lt;Hodnota&gt; (C# Průvodce programováním)'
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 22de15560d6db6e8a70cea744dd9d85359336306
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33356428"
---
# <a name="ltvaluegt-c-programming-guide"></a><span data-ttu-id="4b27a-102">&lt;Hodnota&gt; (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="4b27a-102">&lt;value&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="4b27a-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b27a-103">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4b27a-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="4b27a-104">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="4b27a-105">Popis pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4b27a-105">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b27a-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4b27a-106">Remarks</span></span>  
 <span data-ttu-id="4b27a-107">\<Hodnotu > značka umožňuje popisují hodnotu, která představuje vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4b27a-107">The \<value> tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="4b27a-108">Všimněte si, že pokud přidáte vlastnost prostřednictvím Průvodce kódu ve vývojovém prostředí sady Visual Studio .NET, přidá [ \<souhrnné >](../../../csharp/programming-guide/xmldoc/summary.md) značky pro novou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4b27a-108">Note that when you add a property via code wizard in the Visual Studio .NET development environment, it will add a [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="4b27a-109">Měli byste pak přidat ručně \<hodnotu > značka, které popisují hodnotu, která představuje vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4b27a-109">You should then manually add a \<value> tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="4b27a-110">Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="4b27a-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b27a-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="4b27a-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#14](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/value_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="4b27a-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="4b27a-112">See Also</span></span>  
 [<span data-ttu-id="4b27a-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="4b27a-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4b27a-114">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="4b27a-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
