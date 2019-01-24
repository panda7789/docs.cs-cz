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
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a>Postupy: Ověření názvy souborů a cest v jazyce Visual Basic
V tomto příkladu vrátí `Boolean` hodnotu, která určuje, zda řetězec reprezentuje název souboru nebo cesta. Pokud název obsahuje znaky, které nejsou povoleny v systému souborů kontroly ověření.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbcnRegEx#4](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-file-names-and-paths_1.vb)]  
  
 V tomto příkladu nekontroluje, pokud název byl nesprávně umístěn dvojtečkou nebo adresáře bez názvu, nebo pokud délka názvu překračuje maximální délka definovaná systémem. Také nekontroluje Pokud aplikace nemá oprávnění pro přístup k systému souborů prostředků se zadaným názvem.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.IO.Path.GetInvalidPathChars%2A>
- [Ověřování řetězců v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
