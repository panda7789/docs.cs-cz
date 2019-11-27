---
title: 'Postupy: ověření názvů souborů a cest'
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
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a>Postupy: Ověření názvů a cest souborů v jazyce Visual Basic
V tomto příkladu se vrátí hodnota `Boolean`, která indikuje, jestli řetězec představuje název souboru nebo cestu. Ověření kontroluje, zda název obsahuje znaky, které nejsou povoleny systémem souborů.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbcnRegEx#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#4)]  
  
 Tento příklad nekontroluje, zda má název nesprávně umístěné dvojtečky nebo adresáře bez názvu, nebo pokud délka názvu překračuje maximální délku definovanou systémem. Nekontroluje také, jestli má aplikace oprávnění pro přístup k prostředku systému souborů se zadaným názvem.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO.Path.GetInvalidPathChars%2A>
- [Ověřování řetězců v Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
