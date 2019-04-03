---
title: 'Postupy: Ověření názvy souborů a cest v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: c8e01a0f5a3f99fdbc424d6cd7d224367c7bad08
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58835801"
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a><span data-ttu-id="a0c50-102">Postupy: Ověření názvy souborů a cest v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a0c50-102">How to: Validate File Names and Paths in Visual Basic</span></span>
<span data-ttu-id="a0c50-103">V tomto příkladu vrátí `Boolean` hodnotu, která určuje, zda řetězec reprezentuje název souboru nebo cesta.</span><span class="sxs-lookup"><span data-stu-id="a0c50-103">This example returns a `Boolean` value that indicates whether a string represents a file name or path.</span></span> <span data-ttu-id="a0c50-104">Pokud název obsahuje znaky, které nejsou povoleny v systému souborů kontroly ověření.</span><span class="sxs-lookup"><span data-stu-id="a0c50-104">The validation checks if the name contains characters that are not allowed by the file system.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0c50-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="a0c50-105">Example</span></span>  
 [!code-vb[VbVbcnRegEx#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#4)]  
  
 <span data-ttu-id="a0c50-106">V tomto příkladu nekontroluje, pokud název byl nesprávně umístěn dvojtečkou nebo adresáře bez názvu, nebo pokud délka názvu překračuje maximální délka definovaná systémem.</span><span class="sxs-lookup"><span data-stu-id="a0c50-106">This example does not check if the name has incorrectly placed colons, or directories with no name, or if the length of the name exceeds the system-defined maximum length.</span></span> <span data-ttu-id="a0c50-107">Také nekontroluje Pokud aplikace nemá oprávnění pro přístup k systému souborů prostředků se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="a0c50-107">It also does not check if the application has permission to access the file-system resource with the specified name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0c50-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a0c50-108">See also</span></span>

- <xref:System.IO.Path.GetInvalidPathChars%2A>
- [<span data-ttu-id="a0c50-109">Ověřování řetězců v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a0c50-109">Validating Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
