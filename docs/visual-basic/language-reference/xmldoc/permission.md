---
title: '&lt;oprávnění&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
ms.openlocfilehash: bcec5d968f5d0c5400c28e772df151b164888a47
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46323295"
---
# <a name="ltpermissiongt-visual-basic"></a><span data-ttu-id="2080c-102">&lt;oprávnění&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2080c-102">&lt;permission&gt; (Visual Basic)</span></span>
<span data-ttu-id="2080c-103">Určuje požadované oprávnění pro tohoto člena.</span><span class="sxs-lookup"><span data-stu-id="2080c-103">Specifies a required permission for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2080c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2080c-104">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2080c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2080c-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="2080c-106">Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="2080c-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="2080c-107">Kompilátor kontroluje, zda daný prvek kódu existuje a přeloží `member` k názvu canonical prvku ve výstupním souboru XML.</span><span class="sxs-lookup"><span data-stu-id="2080c-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="2080c-108">Uzavřete `member` do uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="2080c-108">Enclose `member` in quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="2080c-109">Popis přístup ke členu.</span><span class="sxs-lookup"><span data-stu-id="2080c-109">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2080c-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2080c-110">Remarks</span></span>  
 <span data-ttu-id="2080c-111">Použití `<permission>` značku k dokumentu přístup člena.</span><span class="sxs-lookup"><span data-stu-id="2080c-111">Use the `<permission>` tag to document the access of a member.</span></span> <span data-ttu-id="2080c-112">Použití <xref:System.Security.PermissionSet> tak, aby určovala přístup ke členu.</span><span class="sxs-lookup"><span data-stu-id="2080c-112">Use the <xref:System.Security.PermissionSet> class to specify access to a member.</span></span>  
  
 <span data-ttu-id="2080c-113">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="2080c-113">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2080c-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="2080c-114">Example</span></span>  
 <span data-ttu-id="2080c-115">Tento příklad používá `<permission>` značka, které popisují, které <xref:System.Security.Permissions.FileIOPermission> vyžaduje `ReadFile` metody.</span><span class="sxs-lookup"><span data-stu-id="2080c-115">This example uses the `<permission>` tag to describe that the <xref:System.Security.Permissions.FileIOPermission> is required by the `ReadFile` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#7](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/permission_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="2080c-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="2080c-116">See Also</span></span>  
 [<span data-ttu-id="2080c-117">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="2080c-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
