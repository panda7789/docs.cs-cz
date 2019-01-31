---
title: <permission> - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: 4725e82c6b085e220f63346a8c6838ecc288efa1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55263651"
---
# <a name="permission-c-programming-guide"></a><span data-ttu-id="a8bc2-102">\<oprávnění > (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="a8bc2-102">\<permission> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="a8bc2-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8bc2-103">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a8bc2-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="a8bc2-104">Parameters</span></span>  
 <span data-ttu-id="a8bc2-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="a8bc2-105">cref = " `member`"</span></span>  
 <span data-ttu-id="a8bc2-106">Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="a8bc2-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="a8bc2-107">Kompilátor kontroluje, zda daný prvek kódu existuje a přeloží `member` k názvu canonical prvku ve výstupním souboru XML.</span><span class="sxs-lookup"><span data-stu-id="a8bc2-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="a8bc2-108">*člen* musí být uvedena v uvozovkách ("").</span><span class="sxs-lookup"><span data-stu-id="a8bc2-108">*member* must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="a8bc2-109">Informace o tom, jak vytvořit cref odkaz na obecný typ, naleznete v tématu [ \<naleznete v tématu >](../../../csharp/programming-guide/xmldoc/see.md).</span><span class="sxs-lookup"><span data-stu-id="a8bc2-109">For information on how to create a cref reference to a generic type, see [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span></span>  
  
 `description`  
 <span data-ttu-id="a8bc2-110">Popis přístup ke členu.</span><span class="sxs-lookup"><span data-stu-id="a8bc2-110">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8bc2-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a8bc2-111">Remarks</span></span>  
 <span data-ttu-id="a8bc2-112">\<Oprávnění > značky umožňuje dokumentu přístup člena.</span><span class="sxs-lookup"><span data-stu-id="a8bc2-112">The \<permission> tag lets you document the access of a member.</span></span> <span data-ttu-id="a8bc2-113"><xref:System.Security.PermissionSet> Třída umožňuje určit přístup ke členu.</span><span class="sxs-lookup"><span data-stu-id="a8bc2-113">The <xref:System.Security.PermissionSet> class lets you specify access to a member.</span></span>  
  
 <span data-ttu-id="a8bc2-114">Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="a8bc2-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8bc2-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="a8bc2-115">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#8](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/permission_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="a8bc2-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a8bc2-116">See also</span></span>

- [<span data-ttu-id="a8bc2-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="a8bc2-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="a8bc2-118">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="a8bc2-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
