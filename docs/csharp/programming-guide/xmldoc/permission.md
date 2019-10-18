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
ms.openlocfilehash: 454928d5dfd023639bc68f194f2f5ec9e2d7dc22
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523391"
---
# <a name="permission-c-programming-guide"></a><span data-ttu-id="5bd39-102">> \<permission (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="5bd39-102">\<permission> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="5bd39-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5bd39-103">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
## <a name="parameters"></a><span data-ttu-id="5bd39-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="5bd39-104">Parameters</span></span>  
 <span data-ttu-id="5bd39-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="5bd39-105">cref = " `member`"</span></span>  
 <span data-ttu-id="5bd39-106">Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="5bd39-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="5bd39-107">Kompilátor kontroluje, zda daný prvek kódu existuje, a překládá `member` na název kanonického prvku ve výstupním souboru XML.</span><span class="sxs-lookup"><span data-stu-id="5bd39-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="5bd39-108">*člen* musí být v uvozovkách ("").</span><span class="sxs-lookup"><span data-stu-id="5bd39-108">*member* must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="5bd39-109">Informace o tom, jak vytvořit odkaz cref na obecný typ, naleznete v tématu [\<see >](./see.md).</span><span class="sxs-lookup"><span data-stu-id="5bd39-109">For information on how to create a cref reference to a generic type, see [\<see>](./see.md).</span></span>  
  
 `description`  
 <span data-ttu-id="5bd39-110">Popis přístupu ke členovi.</span><span class="sxs-lookup"><span data-stu-id="5bd39-110">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5bd39-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5bd39-111">Remarks</span></span>  
 <span data-ttu-id="5bd39-112">Značka > \<permission umožňuje dokumentovat přístup člena.</span><span class="sxs-lookup"><span data-stu-id="5bd39-112">The \<permission> tag lets you document the access of a member.</span></span> <span data-ttu-id="5bd39-113">Třída <xref:System.Security.PermissionSet> umožňuje zadat přístup ke členu.</span><span class="sxs-lookup"><span data-stu-id="5bd39-113">The <xref:System.Security.PermissionSet> class lets you specify access to a member.</span></span>  
  
 <span data-ttu-id="5bd39-114">Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="5bd39-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5bd39-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="5bd39-115">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]  
  
## <a name="see-also"></a><span data-ttu-id="5bd39-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5bd39-116">See also</span></span>

- [<span data-ttu-id="5bd39-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="5bd39-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5bd39-118">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="5bd39-118">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
