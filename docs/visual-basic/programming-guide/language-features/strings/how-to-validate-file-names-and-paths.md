---
title: 'Postupy: Ověření názvy souborů a cest v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: d29553071d68319d754406b3104da6e096f908fd
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975521"
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a>Postupy: Ověření názvy souborů a cest v jazyce Visual Basic
V tomto příkladu vrátí `Boolean` hodnotu, která určuje, zda řetězec reprezentuje název souboru nebo cesta. Pokud název obsahuje znaky, které nejsou povoleny v systému souborů kontroly ověření.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbcnRegEx#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#4)]  
  
 V tomto příkladu nekontroluje, pokud název byl nesprávně umístěn dvojtečkou nebo adresáře bez názvu, nebo pokud délka názvu překračuje maximální délka definovaná systémem. Také nekontroluje Pokud aplikace nemá oprávnění pro přístup k systému souborů prostředků se zadaným názvem.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.IO.Path.GetInvalidPathChars%2A>
- [Ověřování řetězců v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
