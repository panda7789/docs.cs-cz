---
title: <permission> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
ms.openlocfilehash: d8fe70445b2a2500f99a0156604238665b7bbd1c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57473497"
---
# <a name="permission-visual-basic"></a><span data-ttu-id="a96d3-102">\<oprávnění > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a96d3-102">\<permission> (Visual Basic)</span></span>
<span data-ttu-id="a96d3-103">Určuje požadované oprávnění pro tohoto člena.</span><span class="sxs-lookup"><span data-stu-id="a96d3-103">Specifies a required permission for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a96d3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a96d3-104">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
## <a name="parameters"></a><span data-ttu-id="a96d3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a96d3-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="a96d3-106">Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="a96d3-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="a96d3-107">Kompilátor kontroluje, zda daný prvek kódu existuje a přeloží `member` k názvu canonical prvku ve výstupním souboru XML.</span><span class="sxs-lookup"><span data-stu-id="a96d3-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="a96d3-108">Uzavřete `member` do uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="a96d3-108">Enclose `member` in quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="a96d3-109">Popis přístup ke členu.</span><span class="sxs-lookup"><span data-stu-id="a96d3-109">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a96d3-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a96d3-110">Remarks</span></span>  
 <span data-ttu-id="a96d3-111">Použití `<permission>` značku k dokumentu přístup člena.</span><span class="sxs-lookup"><span data-stu-id="a96d3-111">Use the `<permission>` tag to document the access of a member.</span></span> <span data-ttu-id="a96d3-112">Použití <xref:System.Security.PermissionSet> tak, aby určovala přístup ke členu.</span><span class="sxs-lookup"><span data-stu-id="a96d3-112">Use the <xref:System.Security.PermissionSet> class to specify access to a member.</span></span>  
  
 <span data-ttu-id="a96d3-113">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="a96d3-113">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a96d3-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="a96d3-114">Example</span></span>  
 <span data-ttu-id="a96d3-115">Tento příklad používá `<permission>` značka, které popisují, které <xref:System.Security.Permissions.FileIOPermission> vyžaduje `ReadFile` metody.</span><span class="sxs-lookup"><span data-stu-id="a96d3-115">This example uses the `<permission>` tag to describe that the <xref:System.Security.Permissions.FileIOPermission> is required by the `ReadFile` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="a96d3-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a96d3-116">See also</span></span>
- [<span data-ttu-id="a96d3-117">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="a96d3-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
