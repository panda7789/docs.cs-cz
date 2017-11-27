---
title: "Ověřování složitosti hesla (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: String data type [Visual Basic], validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bdbe5f385c6b7a0898c4907b0d8afabdaed06fa0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a>Návod: Ověření, že hesla jsou složitá (Visual Basic).
Tato metoda zkontroluje některé vlastnosti silného hesla a aktualizace parametr řetězce s informacemi o tom, které kontroluje heslo selže.  
  
 Hesla lze v zabezpečeném systému k autorizaci uživatele. Hesla musí být ale těžko neoprávnění uživatelé tak snadno uhodnout. Útočníci mohou používat *slovníkové útoky* program, který iteruje v rámci všech slova ve slovníku (nebo více slovník v různých jazycích) a kontroluje, zda některé z slova fungovat jako heslo uživatele. Slabé heslo, například "Určitý fotbalový tým" nebo "Mustang" můžete snadno uhodnout. Silnější hesla, jako například "? Můžete seL1N3vaFiNdMeyeP@sSWerd! ", jsou mnohem méně pravděpodobné, že uhodnout. Systém chráněný heslem se ujistěte, že uživatelé vybrat silná hesla.  
  
 Silné heslo je komplexní (obsahující směs velká písmena, malá písmena, číselné a speciální znaky) a není slova. Tento příklad ukazuje, jak ověřit složitost.  
  
## <a name="example"></a>Příklad  
  
### <a name="code"></a>Kód  
 [!code-vb[VbVbcnRegEx#1](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/walkthrough-validating-that-passwords-are-complex_1.vb)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tuto metodu volejte předáním řetězec, který obsahuje toto heslo.  
  
 Tento příklad vyžaduje:  
  
-   Přístup k členům <xref:System.Text.RegularExpressions> oboru názvů. Přidat `Imports` příkaz, pokud jste nejsou kvalifikující plně názvy členů v kódu. Další informace najdete v tématu [příkaz Imports (Namespace .NET a typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="security"></a>Zabezpečení  
 Pokud přesouváte hesla přes síť, budete muset použít bezpečnou metodu pro přenášení dat. Další informace najdete v tématu [zabezpečení webové aplikace ASP.NET](https://msdn.microsoft.com/library/330a99hc).  
  
 Můžete zvýšit jeho přesnost `ValidatePassword` funkce přidáním další složitosti kontroly:  
  
-   Porovnejte heslo a jeho dílčích řetězců proti jméno uživatele, identifikátor uživatele a slovníku definované aplikací. Kromě toho považovat za vizuálně podobné znaky ekvivalentní při provádění porovnání. Například považovat za písmena "l" a "e" ekvivalentní číslice "1" a "3".  
  
-   Pokud je jenom jedno velké písmeno, ujistěte se, že se nejedná o první znak hesla.  
  
-   Zajistěte, aby poslední dva znaky hesla byla písmeno znaků.  
  
-   Nepovolit hesla, ve kterých jsou všechny symboly vstup z klávesnice na horní řádek.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Text.RegularExpressions.Regex>  
 [Zabezpečení webové aplikace ASP.NET](https://msdn.microsoft.com/library/330a99hc)
