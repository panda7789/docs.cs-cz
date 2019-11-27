---
title: Příkaz Sub nebo funkce nejsou definované.
ms.date: 07/20/2015
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
ms.openlocfilehash: 8b81460eccb6be8baa2ea7bc68d0f80c9d16398e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349579"
---
# <a name="sub-or-function-not-defined-visual-basic"></a>Příkaz Sub nebo funkce není definována (Visual Basic)
Aby bylo možné volat `Sub`, musí být definován nebo `Function`. Mezi možné příčiny této chyby patří:  
  
- Název procedury je chybný.  
  
- Pokus o volání procedury z jiného projektu, aniž by bylo nutné explicitně přidat odkaz na tento projekt v dialogovém okně **odkazy** .  
  
- Určení procedury, která není viditelná pro volající proceduru.  
  
- Deklarace rutiny DLL (Dynamic-Link Library) systému Windows nebo rutiny kódu systému Macintosh, která není v určeném prostředku knihovny nebo kódu.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Ujistěte se, že je název procedury zadán správně.  
  
2. Vyhledejte název projektu, který obsahuje proceduru, kterou chcete volat, v dialogovém okně **odkazy** . Pokud se nezobrazí, klikněte na tlačítko **Procházet** a vyhledejte ho. Zaškrtněte políčko nalevo od názvu projektu a pak klikněte na tlačítko **OK**.  
  
3. Kontrola názvu rutiny.  
  
## <a name="see-also"></a>Viz také:

- [Typy chyb](../../../visual-basic/programming-guide/language-features/error-types.md)
- [Správa odkazů v projektu](/visualstudio/ide/managing-references-in-a-project)
- [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)
