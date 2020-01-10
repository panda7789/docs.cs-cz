---
title: <seealso> – C# Průvodce programováním
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
ms.openlocfilehash: 600affdfd8cb524a7fba479d3a68ad8b3e40098c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75694917"
---
# <a name="seealso-c-programming-guide"></a><span data-ttu-id="8327a-102">\<SeeAlso > (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="8327a-102">\<seealso> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="8327a-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8327a-103">Syntax</span></span>  
  
```xml  
<seealso cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="8327a-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="8327a-104">Parameters</span></span>  
 <span data-ttu-id="8327a-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="8327a-105">cref = " `member`"</span></span>  
 <span data-ttu-id="8327a-106">Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="8327a-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="8327a-107">Kompilátor kontroluje, zda daný prvek kódu existuje a zda předává `member` do názvu prvku ve výstupním souboru XML.`member`</span><span class="sxs-lookup"><span data-stu-id="8327a-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.`member`</span></span> <span data-ttu-id="8327a-108">v uvozovkách ("") se musí vyskytovat.</span><span class="sxs-lookup"><span data-stu-id="8327a-108">must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="8327a-109">Informace o tom, jak vytvořit odkaz cref na obecný typ, najdete v tématu [\<](./see.md).</span><span class="sxs-lookup"><span data-stu-id="8327a-109">For information on how to create a cref reference to a generic type, see [\<see>](./see.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8327a-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8327a-110">Remarks</span></span>  
 <span data-ttu-id="8327a-111">Značka > \<SeeAlso umožňuje určit text, který se může objevit v části Viz také.</span><span class="sxs-lookup"><span data-stu-id="8327a-111">The \<seealso> tag lets you specify the text that you might want to appear in a See Also section.</span></span> <span data-ttu-id="8327a-112">Použijte [\<v části >](./see.md) určete odkaz z textu.</span><span class="sxs-lookup"><span data-stu-id="8327a-112">Use [\<see>](./see.md) to specify a link from within text.</span></span>  
  
 <span data-ttu-id="8327a-113">Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="8327a-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8327a-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="8327a-114">Example</span></span>  
 <span data-ttu-id="8327a-115">Příklad použití \<SeeAlso > najdete v článku [> souhrnu\<](./summary.md) .</span><span class="sxs-lookup"><span data-stu-id="8327a-115">See [\<summary>](./summary.md) for an example of using \<seealso>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8327a-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8327a-116">See also</span></span>

- [<span data-ttu-id="8327a-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="8327a-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8327a-118">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="8327a-118">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
