---
title: "Postupy: Ověření názvů a cest souborů v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9c50d09dd7160992ffd95ececeff623a8aa93d2d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a>Postupy: Ověření názvů a cest souborů v jazyce Visual Basic
Tento příklad vrací `Boolean` hodnotu, která určuje, zda řetězec reprezentuje název souboru nebo cestu. Ověření kontroluje, zda název obsahuje znaky, které nejsou povoleny systému souborů.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbcnRegEx#4](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-file-names-and-paths_1.vb)]  
  
 Tento příklad nekontroluje, pokud název obsahuje nesprávně umístěný dvojtečky nebo adresáře bez názvu nebo délka názvu překračuje maximální délka definovaná systémem. Také nekontroluje Pokud aplikace má oprávnění pro přístup k prostředku systému souborů se zadaným názvem.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IO.Path.GetInvalidPathChars%2A>  
 [Ověřování řetězců v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
