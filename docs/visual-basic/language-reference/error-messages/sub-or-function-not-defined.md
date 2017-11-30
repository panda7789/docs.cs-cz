---
title: "Příkaz Sub nebo funkce není definována (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6237ca26b06bdffa06499607e634b3222725c189
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="sub-or-function-not-defined-visual-basic"></a>Příkaz Sub nebo funkce není definována (Visual Basic)
A `Sub` nebo `Function` musí být definován, aby bylo možné volat. Možné příčiny této chyby patří:  
  
-   Chyba v pravopisu název procedury.  
  
-   Při pokusu o volání procedury z jiného projektu bez explicitně přidat odkaz na tohoto projektu v **odkazy** dialogové okno.  
  
-   Zadání procedury, která není viditelná pro volání procedury.  
  
-   Deklarování Windows dynamická knihovna (DLL) rutina nebo rutiny Macintosh kód prostředků, který není v zadaný prostředek knihovny nebo kód.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Ujistěte se, že název postupu je napsán správně.  
  
2.  Najít název projektu, který obsahuje postup, který chcete použít **odkazy** dialogové okno. Pokud se nezobrazí, klikněte **Procházet** tlačítko ji najít. Zaškrtněte políčko nalevo od názvu projektu a pak klikněte na **OK**.  
  
3.  Zkontrolujte název rutiny.  
  
## <a name="see-also"></a>Viz také  
 [Typy chyb](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [Správa odkazů v projektu](/visualstudio/ide/managing-references-in-a-project)  
 [Sub – příkaz](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Function – příkaz](../../../visual-basic/language-reference/statements/function-statement.md)
