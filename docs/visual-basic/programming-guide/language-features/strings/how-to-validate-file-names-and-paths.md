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
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a>Postupy: Ověření názvů a cest souborů v jazyce Visual Basic
Tento příklad vrátí `Boolean` hodnotu, která označuje, zda řetězec představuje název souboru nebo cestu. Ověření kontroluje, zda název obsahuje znaky, které nejsou povoleny systémem souborů.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbcnRegEx#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#4)]  
  
 Tento příklad nekontroluje, zda má název nesprávně umístěné dvojtečky nebo adresáře bez názvu, nebo pokud délka názvu překračuje maximální délku definovanou systémem. Nekontroluje také, jestli má aplikace oprávnění pro přístup k prostředku systému souborů se zadaným názvem.  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO.Path.GetInvalidPathChars%2A>
- [Ověřování řetězců v jazyce Visual Basic](validating-strings.md)
