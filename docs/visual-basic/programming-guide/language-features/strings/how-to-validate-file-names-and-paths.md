---
title: 'Postupy: Ověření názvů a cest souborů'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: 3b4695dfbcaf05c73bd53af5be7a49d081eb8e47
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410577"
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a><span data-ttu-id="bded9-102">Postupy: Ověření názvů a cest souborů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bded9-102">How to: Validate File Names and Paths in Visual Basic</span></span>
<span data-ttu-id="bded9-103">Tento příklad vrátí `Boolean` hodnotu, která označuje, zda řetězec představuje název souboru nebo cestu.</span><span class="sxs-lookup"><span data-stu-id="bded9-103">This example returns a `Boolean` value that indicates whether a string represents a file name or path.</span></span> <span data-ttu-id="bded9-104">Ověření kontroluje, zda název obsahuje znaky, které nejsou povoleny systémem souborů.</span><span class="sxs-lookup"><span data-stu-id="bded9-104">The validation checks if the name contains characters that are not allowed by the file system.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bded9-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="bded9-105">Example</span></span>  
 [!code-vb[VbVbcnRegEx#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#4)]  
  
 <span data-ttu-id="bded9-106">Tento příklad nekontroluje, zda má název nesprávně umístěné dvojtečky nebo adresáře bez názvu, nebo pokud délka názvu překračuje maximální délku definovanou systémem.</span><span class="sxs-lookup"><span data-stu-id="bded9-106">This example does not check if the name has incorrectly placed colons, or directories with no name, or if the length of the name exceeds the system-defined maximum length.</span></span> <span data-ttu-id="bded9-107">Nekontroluje také, jestli má aplikace oprávnění pro přístup k prostředku systému souborů se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="bded9-107">It also does not check if the application has permission to access the file-system resource with the specified name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bded9-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="bded9-108">See also</span></span>

- <xref:System.IO.Path.GetInvalidPathChars%2A>
- [<span data-ttu-id="bded9-109">Ověřování řetězců v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bded9-109">Validating Strings in Visual Basic</span></span>](validating-strings.md)
