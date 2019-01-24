---
title: 'Postupy: Ověření názvy souborů a cest v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: c0d39ecbaf9ca23c72e45b8839d268fbc38fe48e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54648446"
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a><span data-ttu-id="b7299-102">Postupy: Ověření názvy souborů a cest v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b7299-102">How to: Validate File Names and Paths in Visual Basic</span></span>
<span data-ttu-id="b7299-103">V tomto příkladu vrátí `Boolean` hodnotu, která určuje, zda řetězec reprezentuje název souboru nebo cesta.</span><span class="sxs-lookup"><span data-stu-id="b7299-103">This example returns a `Boolean` value that indicates whether a string represents a file name or path.</span></span> <span data-ttu-id="b7299-104">Pokud název obsahuje znaky, které nejsou povoleny v systému souborů kontroly ověření.</span><span class="sxs-lookup"><span data-stu-id="b7299-104">The validation checks if the name contains characters that are not allowed by the file system.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7299-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="b7299-105">Example</span></span>  
 [!code-vb[VbVbcnRegEx#4](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-file-names-and-paths_1.vb)]  
  
 <span data-ttu-id="b7299-106">V tomto příkladu nekontroluje, pokud název byl nesprávně umístěn dvojtečkou nebo adresáře bez názvu, nebo pokud délka názvu překračuje maximální délka definovaná systémem.</span><span class="sxs-lookup"><span data-stu-id="b7299-106">This example does not check if the name has incorrectly placed colons, or directories with no name, or if the length of the name exceeds the system-defined maximum length.</span></span> <span data-ttu-id="b7299-107">Také nekontroluje Pokud aplikace nemá oprávnění pro přístup k systému souborů prostředků se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="b7299-107">It also does not check if the application has permission to access the file-system resource with the specified name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7299-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b7299-108">See also</span></span>
- <xref:System.IO.Path.GetInvalidPathChars%2A>
- [<span data-ttu-id="b7299-109">Ověřování řetězců v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b7299-109">Validating Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
