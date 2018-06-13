---
title: 'Postupy: Ověření názvů a cest souborů v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: ab3df335bc5bba21d386bb69b12d840990e629fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647801"
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a><span data-ttu-id="c4eb2-102">Postupy: Ověření názvů a cest souborů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c4eb2-102">How to: Validate File Names and Paths in Visual Basic</span></span>
<span data-ttu-id="c4eb2-103">Tento příklad vrací `Boolean` hodnotu, která určuje, zda řetězec reprezentuje název souboru nebo cestu.</span><span class="sxs-lookup"><span data-stu-id="c4eb2-103">This example returns a `Boolean` value that indicates whether a string represents a file name or path.</span></span> <span data-ttu-id="c4eb2-104">Ověření kontroluje, zda název obsahuje znaky, které nejsou povoleny systému souborů.</span><span class="sxs-lookup"><span data-stu-id="c4eb2-104">The validation checks if the name contains characters that are not allowed by the file system.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4eb2-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="c4eb2-105">Example</span></span>  
 [!code-vb[VbVbcnRegEx#4](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-file-names-and-paths_1.vb)]  
  
 <span data-ttu-id="c4eb2-106">Tento příklad nekontroluje, pokud název obsahuje nesprávně umístěný dvojtečky nebo adresáře bez názvu nebo délka názvu překračuje maximální délka definovaná systémem.</span><span class="sxs-lookup"><span data-stu-id="c4eb2-106">This example does not check if the name has incorrectly placed colons, or directories with no name, or if the length of the name exceeds the system-defined maximum length.</span></span> <span data-ttu-id="c4eb2-107">Také nekontroluje Pokud aplikace má oprávnění pro přístup k prostředku systému souborů se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="c4eb2-107">It also does not check if the application has permission to access the file-system resource with the specified name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4eb2-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="c4eb2-108">See Also</span></span>  
 <xref:System.IO.Path.GetInvalidPathChars%2A>  
 [<span data-ttu-id="c4eb2-109">Ověřování řetězců v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c4eb2-109">Validating Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
