---
title: <permission> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
ms.openlocfilehash: 904d573514bf35b773d47321b7fd3b6a86e90262
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524697"
---
# <a name="permission-visual-basic"></a><span data-ttu-id="2cd6e-102">\<permission > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2cd6e-102">\<permission> (Visual Basic)</span></span>
<span data-ttu-id="2cd6e-103">Určuje požadované oprávnění pro člena.</span><span class="sxs-lookup"><span data-stu-id="2cd6e-103">Specifies a required permission for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cd6e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2cd6e-104">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
## <a name="parameters"></a><span data-ttu-id="2cd6e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2cd6e-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="2cd6e-106">Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="2cd6e-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="2cd6e-107">Kompilátor kontroluje, zda daný prvek kódu existuje, a překládá `member` na název kanonického prvku ve výstupním souboru XML.</span><span class="sxs-lookup"><span data-stu-id="2cd6e-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="2cd6e-108">Uzavřete `member` do uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="2cd6e-108">Enclose `member` in quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="2cd6e-109">Popis přístupu ke členovi.</span><span class="sxs-lookup"><span data-stu-id="2cd6e-109">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2cd6e-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2cd6e-110">Remarks</span></span>  
 <span data-ttu-id="2cd6e-111">Pomocí značky `<permission>` můžete zdokumentovat přístup člena.</span><span class="sxs-lookup"><span data-stu-id="2cd6e-111">Use the `<permission>` tag to document the access of a member.</span></span> <span data-ttu-id="2cd6e-112">K určení přístupu ke členu použijte třídu <xref:System.Security.PermissionSet>.</span><span class="sxs-lookup"><span data-stu-id="2cd6e-112">Use the <xref:System.Security.PermissionSet> class to specify access to a member.</span></span>  
  
 <span data-ttu-id="2cd6e-113">Zkompilujte s [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="2cd6e-113">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2cd6e-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="2cd6e-114">Example</span></span>  
 <span data-ttu-id="2cd6e-115">V tomto příkladu se používá značka `<permission>` k označení toho, že metoda `ReadFile` vyžaduje <xref:System.Security.Permissions.FileIOPermission>.</span><span class="sxs-lookup"><span data-stu-id="2cd6e-115">This example uses the `<permission>` tag to describe that the <xref:System.Security.Permissions.FileIOPermission> is required by the `ReadFile` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="2cd6e-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2cd6e-116">See also</span></span>

- [<span data-ttu-id="2cd6e-117">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="2cd6e-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
