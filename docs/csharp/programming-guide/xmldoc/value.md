---
title: '&lt;Hodnota&gt; - C# Průvodce programováním pro službu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 28c07331931450f41f8c93d24e119f8a981ae9ae
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54500600"
---
# <a name="ltvaluegt-c-programming-guide"></a><span data-ttu-id="7638f-102">&lt;Hodnota&gt; (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="7638f-102">&lt;value&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="7638f-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7638f-103">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7638f-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="7638f-104">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="7638f-105">Popis pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7638f-105">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7638f-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7638f-106">Remarks</span></span>  
 <span data-ttu-id="7638f-107">\<Hodnota > značky umožňuje popisují hodnotu, která představuje vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7638f-107">The \<value> tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="7638f-108">Všimněte si, že při přidání vlastnosti prostřednictvím Průvodce kódem ve vývojovém prostředí sady Visual Studio .NET, přidá [ \<summary >](../../../csharp/programming-guide/xmldoc/summary.md) značky pro novou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7638f-108">Note that when you add a property via code wizard in the Visual Studio .NET development environment, it will add a [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="7638f-109">Měli byste pak ručně přidat \<hodnota > značka, které popisují hodnotu, která představuje vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7638f-109">You should then manually add a \<value> tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="7638f-110">Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="7638f-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7638f-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="7638f-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#14](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/value_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="7638f-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7638f-112">See also</span></span>

- [<span data-ttu-id="7638f-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="7638f-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="7638f-114">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="7638f-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
