---
title: <value> – C# Průvodce programováním
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: a30435c40ad31e026b9cb1952086984548f0cdb6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75694540"
---
# <a name="value-c-programming-guide"></a><span data-ttu-id="c645a-102">> hodnota \<(C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="c645a-102">\<value> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="c645a-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c645a-103">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a><span data-ttu-id="c645a-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="c645a-104">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="c645a-105">Popis vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c645a-105">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c645a-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c645a-106">Remarks</span></span>  
 <span data-ttu-id="c645a-107">Hodnota \<> tag umožňuje popsat hodnotu, kterou vlastnost představuje.</span><span class="sxs-lookup"><span data-stu-id="c645a-107">The \<value> tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="c645a-108">Všimněte si, že při přidání vlastnosti přes průvodce kódem ve vývojovém prostředí sady Visual Studio .NET bude přidána značka [\<summary >](./summary.md) pro novou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c645a-108">Note that when you add a property via code wizard in the Visual Studio .NET development environment, it will add a [\<summary>](./summary.md) tag for the new property.</span></span> <span data-ttu-id="c645a-109">Měli byste pak ručně přidat \<Value > tag k popisu hodnoty, kterou vlastnost představuje.</span><span class="sxs-lookup"><span data-stu-id="c645a-109">You should then manually add a \<value> tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="c645a-110">Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="c645a-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c645a-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="c645a-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]  
  
## <a name="see-also"></a><span data-ttu-id="c645a-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c645a-112">See also</span></span>

- [<span data-ttu-id="c645a-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="c645a-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c645a-114">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="c645a-114">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
