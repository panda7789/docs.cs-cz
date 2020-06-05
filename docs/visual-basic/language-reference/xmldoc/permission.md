---
title: <permission>
ms.date: 07/20/2015
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
ms.openlocfilehash: b3acec04060367a0b9e54b19c0106644d028357b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400031"
---
# <a name="permission-visual-basic"></a><span data-ttu-id="c0acd-101">\<permission> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c0acd-101">\<permission> (Visual Basic)</span></span>
<span data-ttu-id="c0acd-102">Určuje požadované oprávnění pro člena.</span><span class="sxs-lookup"><span data-stu-id="c0acd-102">Specifies a required permission for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0acd-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0acd-103">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0acd-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="c0acd-104">Parameters</span></span>  
 `member`  
 <span data-ttu-id="c0acd-105">Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="c0acd-105">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="c0acd-106">Kompilátor kontroluje, zda daný prvek kódu existuje, a překládá se na `member` název kanonického prvku ve výstupním souboru XML.</span><span class="sxs-lookup"><span data-stu-id="c0acd-106">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="c0acd-107">Uzavřete `member` do uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="c0acd-107">Enclose `member` in quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="c0acd-108">Popis přístupu ke členovi.</span><span class="sxs-lookup"><span data-stu-id="c0acd-108">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c0acd-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c0acd-109">Remarks</span></span>  
 <span data-ttu-id="c0acd-110">Pomocí `<permission>` značky můžete zdokumentovat přístup člena.</span><span class="sxs-lookup"><span data-stu-id="c0acd-110">Use the `<permission>` tag to document the access of a member.</span></span> <span data-ttu-id="c0acd-111">Použijte <xref:System.Security.PermissionSet> třídu k určení přístupu ke členu.</span><span class="sxs-lookup"><span data-stu-id="c0acd-111">Use the <xref:System.Security.PermissionSet> class to specify access to a member.</span></span>  
  
 <span data-ttu-id="c0acd-112">Zkompilujte s [-doc](../../reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="c0acd-112">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0acd-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="c0acd-113">Example</span></span>  
 <span data-ttu-id="c0acd-114">Tento příklad používá `<permission>` značku k označení toho, že <xref:System.Security.Permissions.FileIOPermission> Metoda je vyžadována `ReadFile` metodou.</span><span class="sxs-lookup"><span data-stu-id="c0acd-114">This example uses the `<permission>` tag to describe that the <xref:System.Security.Permissions.FileIOPermission> is required by the `ReadFile` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="c0acd-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="c0acd-115">See also</span></span>

- [<span data-ttu-id="c0acd-116">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="c0acd-116">XML Comment Tags</span></span>](index.md)
