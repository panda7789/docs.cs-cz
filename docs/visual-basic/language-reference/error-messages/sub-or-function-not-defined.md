---
title: Příkaz Sub nebo funkce není definována (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
ms.openlocfilehash: 4627f8ddb979780481feadbef06225baf6a7c0ca
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54532172"
---
# <a name="sub-or-function-not-defined-visual-basic"></a>Příkaz Sub nebo funkce není definována (Visual Basic)
A `Sub` nebo `Function` musí být definován, aby bylo možné volat. Mezi možné příčiny této chyby patří:  
  
-   Chyba v pravopisu název procedury.  
  
-   Při pokusu o volání procedury z jiného projektu bez nutnosti explicitně přidávat odkaz na tento projekt v **odkazy** dialogové okno.  
  
-   Určení procedury, která není viditelná pro volání procedury.  
  
-   Deklarování rutiny Windows dynamická knihovna (DLL) nebo Macintosh kód prostředků rutiny, která není v zadané zdroje knihovny nebo kód.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Ujistěte se, jestli název procedury je napsaný správně.  
  
2.  Vyhledání názvu projektu, který obsahuje postup, chcete volat **odkazy** dialogové okno. Pokud se nezobrazí, klikněte na tlačítko **Procházet** tlačítko ji najít. Zaškrtněte políčko nalevo od názvu projektu a potom klikněte na tlačítko **OK**.  
  
3.  Zkontrolujte název rutiny.  
  
## <a name="see-also"></a>Viz také:
- [Typy chyb](../../../visual-basic/programming-guide/language-features/error-types.md)
- [Správa odkazů v projektu](/visualstudio/ide/managing-references-in-a-project)
- [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)
