---
title: <value> – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 09577d931c6b1f571cd4112c788da38bab85bf42
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523276"
---
# <a name="value-c-programming-guide"></a><span data-ttu-id="d49f3-102">> \<value (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="d49f3-102">\<value> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="d49f3-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d49f3-103">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a><span data-ttu-id="d49f3-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="d49f3-104">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="d49f3-105">Popis vlastnosti</span><span class="sxs-lookup"><span data-stu-id="d49f3-105">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d49f3-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d49f3-106">Remarks</span></span>  
 <span data-ttu-id="d49f3-107">Značka > \<value umožňuje popsat hodnotu, kterou vlastnost představuje.</span><span class="sxs-lookup"><span data-stu-id="d49f3-107">The \<value> tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="d49f3-108">Všimněte si, že při přidání vlastnosti prostřednictvím průvodce kódem ve vývojovém prostředí sady Visual Studio .NET bude přidána značka [\<summary >](./summary.md) pro novou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d49f3-108">Note that when you add a property via code wizard in the Visual Studio .NET development environment, it will add a [\<summary>](./summary.md) tag for the new property.</span></span> <span data-ttu-id="d49f3-109">Měli byste potom ručně přidat značku > \<value k popisu hodnoty, kterou vlastnost představuje.</span><span class="sxs-lookup"><span data-stu-id="d49f3-109">You should then manually add a \<value> tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="d49f3-110">Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="d49f3-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d49f3-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="d49f3-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]  
  
## <a name="see-also"></a><span data-ttu-id="d49f3-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d49f3-112">See also</span></span>

- [<span data-ttu-id="d49f3-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="d49f3-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d49f3-114">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="d49f3-114">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
