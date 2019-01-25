---
title: '&lt;oprávnění&gt; - C# Průvodce programováním pro službu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: 5d78261807ab06bd5f89b5438648c5eb0dc56ad9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54739456"
---
# <a name="ltpermissiongt-c-programming-guide"></a><span data-ttu-id="492e9-102">&lt;oprávnění&gt; (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="492e9-102">&lt;permission&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="492e9-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="492e9-103">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="492e9-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="492e9-104">Parameters</span></span>  
 <span data-ttu-id="492e9-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="492e9-105">cref = " `member`"</span></span>  
 <span data-ttu-id="492e9-106">Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="492e9-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="492e9-107">Kompilátor kontroluje, zda daný prvek kódu existuje a přeloží `member` k názvu canonical prvku ve výstupním souboru XML.</span><span class="sxs-lookup"><span data-stu-id="492e9-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="492e9-108">*člen* musí být uvedena v uvozovkách ("").</span><span class="sxs-lookup"><span data-stu-id="492e9-108">*member* must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="492e9-109">Informace o tom, jak vytvořit cref odkaz na obecný typ, naleznete v tématu [ \<naleznete v tématu >](../../../csharp/programming-guide/xmldoc/see.md).</span><span class="sxs-lookup"><span data-stu-id="492e9-109">For information on how to create a cref reference to a generic type, see [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span></span>  
  
 `description`  
 <span data-ttu-id="492e9-110">Popis přístup ke členu.</span><span class="sxs-lookup"><span data-stu-id="492e9-110">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="492e9-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="492e9-111">Remarks</span></span>  
 <span data-ttu-id="492e9-112">\<Oprávnění > značky umožňuje dokumentu přístup člena.</span><span class="sxs-lookup"><span data-stu-id="492e9-112">The \<permission> tag lets you document the access of a member.</span></span> <span data-ttu-id="492e9-113"><xref:System.Security.PermissionSet> Třída umožňuje určit přístup ke členu.</span><span class="sxs-lookup"><span data-stu-id="492e9-113">The <xref:System.Security.PermissionSet> class lets you specify access to a member.</span></span>  
  
 <span data-ttu-id="492e9-114">Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="492e9-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="492e9-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="492e9-115">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#8](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/permission_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="492e9-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="492e9-116">See also</span></span>

- [<span data-ttu-id="492e9-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="492e9-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="492e9-118">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="492e9-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
