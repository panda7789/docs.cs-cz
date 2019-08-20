---
title: <permission> – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: e9eb50394f01072a194d3f746577707f89ba65dd
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587878"
---
# <a name="permission-c-programming-guide"></a><span data-ttu-id="d278f-102">\<> oprávnění (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="d278f-102">\<permission> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="d278f-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d278f-103">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
## <a name="parameters"></a><span data-ttu-id="d278f-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="d278f-104">Parameters</span></span>  
 <span data-ttu-id="d278f-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="d278f-105">cref = " `member`"</span></span>  
 <span data-ttu-id="d278f-106">Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="d278f-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="d278f-107">Kompilátor kontroluje, zda daný prvek kódu existuje, a překládá `member` se na název kanonického prvku ve výstupním souboru XML.</span><span class="sxs-lookup"><span data-stu-id="d278f-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="d278f-108">*člen* musí být v uvozovkách ("").</span><span class="sxs-lookup"><span data-stu-id="d278f-108">*member* must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="d278f-109">Informace o tom, jak vytvořit odkaz cref na obecný typ, naleznete [ \<v tématu viz >](./see.md).</span><span class="sxs-lookup"><span data-stu-id="d278f-109">For information on how to create a cref reference to a generic type, see [\<see>](./see.md).</span></span>  
  
 `description`  
 <span data-ttu-id="d278f-110">Popis přístupu ke členovi.</span><span class="sxs-lookup"><span data-stu-id="d278f-110">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d278f-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d278f-111">Remarks</span></span>  
 <span data-ttu-id="d278f-112">Značka \<> oprávnění umožňuje dokumentovat přístup člena.</span><span class="sxs-lookup"><span data-stu-id="d278f-112">The \<permission> tag lets you document the access of a member.</span></span> <span data-ttu-id="d278f-113"><xref:System.Security.PermissionSet> Třída umožňuje zadat přístup ke členu.</span><span class="sxs-lookup"><span data-stu-id="d278f-113">The <xref:System.Security.PermissionSet> class lets you specify access to a member.</span></span>  
  
 <span data-ttu-id="d278f-114">Zkompilujte pomocí [/doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte dokumentační komentáře do souboru.</span><span class="sxs-lookup"><span data-stu-id="d278f-114">Compile with [/doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d278f-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="d278f-115">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]  
  
## <a name="see-also"></a><span data-ttu-id="d278f-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d278f-116">See also</span></span>

- [<span data-ttu-id="d278f-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="d278f-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d278f-118">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="d278f-118">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
