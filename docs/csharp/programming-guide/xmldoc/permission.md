---
title: "&lt;oprávnění&gt; (C# Průvodce programováním)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 37bb37ea14edc1f91225f9b04b18b354d99579b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltpermissiongt-c-programming-guide"></a><span data-ttu-id="ec3aa-102">&lt;oprávnění&gt; (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="ec3aa-102">&lt;permission&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="ec3aa-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec3aa-103">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ec3aa-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="ec3aa-104">Parameters</span></span>  
 <span data-ttu-id="ec3aa-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="ec3aa-105">cref = " `member`"</span></span>  
 <span data-ttu-id="ec3aa-106">Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="ec3aa-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="ec3aa-107">Kompilátor zkontroluje, zda existuje element daného kódu a překládá `member` na element kanonický název ve výstupu XML.</span><span class="sxs-lookup"><span data-stu-id="ec3aa-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="ec3aa-108">*člen* musí být v rámci dvojitých uvozovek nahoře ("").</span><span class="sxs-lookup"><span data-stu-id="ec3aa-108">*member* must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="ec3aa-109">Informace o tom, jak vytvořit cref odkaz na obecného typu najdete v tématu [ \<najdete v části >](../../../csharp/programming-guide/xmldoc/see.md).</span><span class="sxs-lookup"><span data-stu-id="ec3aa-109">For information on how to create a cref reference to a generic type, see [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span></span>  
  
 `description`  
 <span data-ttu-id="ec3aa-110">Popis přístup ke členu.</span><span class="sxs-lookup"><span data-stu-id="ec3aa-110">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec3aa-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ec3aa-111">Remarks</span></span>  
 <span data-ttu-id="ec3aa-112">\<Oprávnění > značka umožňuje dokumentu přístup člena.</span><span class="sxs-lookup"><span data-stu-id="ec3aa-112">The \<permission> tag lets you document the access of a member.</span></span> <span data-ttu-id="ec3aa-113"><xref:System.Security.PermissionSet> Třída umožňuje určit přístup k členem.</span><span class="sxs-lookup"><span data-stu-id="ec3aa-113">The <xref:System.Security.PermissionSet> class lets you specify access to a member.</span></span>  
  
 <span data-ttu-id="ec3aa-114">Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="ec3aa-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec3aa-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="ec3aa-115">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#8](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/permission_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="ec3aa-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="ec3aa-116">See Also</span></span>  
 [<span data-ttu-id="ec3aa-117">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="ec3aa-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ec3aa-118">Doporučené značky pro dokumentační komentáře</span><span class="sxs-lookup"><span data-stu-id="ec3aa-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
