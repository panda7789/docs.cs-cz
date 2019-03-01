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
ms.openlocfilehash: 475e9ab5c59260544b0e413e165953c0b84449b5
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973896"
---
# <a name="permission-c-programming-guide"></a><span data-ttu-id="f4adb-102">\<oprávnění > (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="f4adb-102">\<permission> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="f4adb-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4adb-103">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f4adb-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="f4adb-104">Parameters</span></span>  
 <span data-ttu-id="f4adb-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="f4adb-105">cref = " `member`"</span></span>  
 <span data-ttu-id="f4adb-106">Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="f4adb-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="f4adb-107">Kompilátor kontroluje, zda daný prvek kódu existuje a přeloží `member` k názvu canonical prvku ve výstupním souboru XML.</span><span class="sxs-lookup"><span data-stu-id="f4adb-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="f4adb-108">*člen* musí být uvedena v uvozovkách ("").</span><span class="sxs-lookup"><span data-stu-id="f4adb-108">*member* must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="f4adb-109">Informace o tom, jak vytvořit cref odkaz na obecný typ, naleznete v tématu [ \<naleznete v tématu >](../../../csharp/programming-guide/xmldoc/see.md).</span><span class="sxs-lookup"><span data-stu-id="f4adb-109">For information on how to create a cref reference to a generic type, see [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span></span>  
  
 `description`  
 <span data-ttu-id="f4adb-110">Popis přístup ke členu.</span><span class="sxs-lookup"><span data-stu-id="f4adb-110">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4adb-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f4adb-111">Remarks</span></span>  
 <span data-ttu-id="f4adb-112">\<Oprávnění > značky umožňuje dokumentu přístup člena.</span><span class="sxs-lookup"><span data-stu-id="f4adb-112">The \<permission> tag lets you document the access of a member.</span></span> <span data-ttu-id="f4adb-113"><xref:System.Security.PermissionSet> Třída umožňuje určit přístup ke členu.</span><span class="sxs-lookup"><span data-stu-id="f4adb-113">The <xref:System.Security.PermissionSet> class lets you specify access to a member.</span></span>  
  
 <span data-ttu-id="f4adb-114">Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="f4adb-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4adb-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="f4adb-115">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]  
  
## <a name="see-also"></a><span data-ttu-id="f4adb-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f4adb-116">See also</span></span>

- [<span data-ttu-id="f4adb-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="f4adb-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="f4adb-118">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="f4adb-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
