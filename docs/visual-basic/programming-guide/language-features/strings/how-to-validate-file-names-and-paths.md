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
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a>Postupy: Ověření názvů a cest souborů v jazyce Visual Basic
Tento příklad vrací `Boolean` hodnotu, která určuje, zda řetězec reprezentuje název souboru nebo cestu. Ověření kontroluje, zda název obsahuje znaky, které nejsou povoleny systému souborů.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbcnRegEx#4](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-file-names-and-paths_1.vb)]  
  
 Tento příklad nekontroluje, pokud název obsahuje nesprávně umístěný dvojtečky nebo adresáře bez názvu nebo délka názvu překračuje maximální délka definovaná systémem. Také nekontroluje Pokud aplikace má oprávnění pro přístup k prostředku systému souborů se zadaným názvem.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IO.Path.GetInvalidPathChars%2A>  
 [Ověřování řetězců v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
