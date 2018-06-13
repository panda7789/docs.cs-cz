---
title: Příkaz Sub nebo funkce není definována (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
ms.openlocfilehash: 58e90d769d5a7f2d88b5c27d1ec7d0d28c8d7b03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593698"
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
 [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)
