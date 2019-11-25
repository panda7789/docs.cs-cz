---
title: 'How to: Validate File Names and Paths'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: cc4d275d469860aa19c45ca0fe0401b709b42d82
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344368"
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a><span data-ttu-id="ecbdd-102">Postupy: Ověření názvů a cest souborů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ecbdd-102">How to: Validate File Names and Paths in Visual Basic</span></span>
<span data-ttu-id="ecbdd-103">This example returns a `Boolean` value that indicates whether a string represents a file name or path.</span><span class="sxs-lookup"><span data-stu-id="ecbdd-103">This example returns a `Boolean` value that indicates whether a string represents a file name or path.</span></span> <span data-ttu-id="ecbdd-104">The validation checks if the name contains characters that are not allowed by the file system.</span><span class="sxs-lookup"><span data-stu-id="ecbdd-104">The validation checks if the name contains characters that are not allowed by the file system.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ecbdd-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="ecbdd-105">Example</span></span>  
 [!code-vb[VbVbcnRegEx#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#4)]  
  
 <span data-ttu-id="ecbdd-106">This example does not check if the name has incorrectly placed colons, or directories with no name, or if the length of the name exceeds the system-defined maximum length.</span><span class="sxs-lookup"><span data-stu-id="ecbdd-106">This example does not check if the name has incorrectly placed colons, or directories with no name, or if the length of the name exceeds the system-defined maximum length.</span></span> <span data-ttu-id="ecbdd-107">It also does not check if the application has permission to access the file-system resource with the specified name.</span><span class="sxs-lookup"><span data-stu-id="ecbdd-107">It also does not check if the application has permission to access the file-system resource with the specified name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecbdd-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ecbdd-108">See also</span></span>

- <xref:System.IO.Path.GetInvalidPathChars%2A>
- [<span data-ttu-id="ecbdd-109">Validating Strings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ecbdd-109">Validating Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
