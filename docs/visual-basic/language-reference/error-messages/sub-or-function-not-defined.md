---
title: Příkaz Sub nebo funkce nejsou definované.
ms.date: 07/20/2015
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
ms.openlocfilehash: 9eb13d943f9f1cffc984847f7339111e06f5aa6b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373924"
---
# <a name="sub-or-function-not-defined-visual-basic"></a>Příkaz Sub nebo funkce není definována (Visual Basic)
`Sub` `Function` Musí být definován, aby mohl být volán. Mezi možné příčiny této chyby patří:  
  
- Název procedury je chybný.  
  
- Pokus o volání procedury z jiného projektu, aniž by bylo nutné explicitně přidat odkaz na tento projekt v dialogovém okně **odkazy** .  
  
- Určení procedury, která není viditelná pro volající proceduru.  
  
- Deklarace rutiny DLL (Dynamic-Link Library) systému Windows nebo rutiny kódu systému Macintosh, která není v určeném prostředku knihovny nebo kódu.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Ujistěte se, že je název procedury zadán správně.  
  
2. Vyhledejte název projektu, který obsahuje proceduru, kterou chcete volat, v dialogovém okně **odkazy** . Pokud se nezobrazí, klikněte na tlačítko **Procházet** a vyhledejte ho. Zaškrtněte políčko nalevo od názvu projektu a pak klikněte na tlačítko **OK**.  
  
3. Kontrola názvu rutiny.  
  
## <a name="see-also"></a>Viz také

- [Typy chyb](../../programming-guide/language-features/error-types.md)
- [Správa odkazů v projektu](/visualstudio/ide/managing-references-in-a-project)
- [Sub – příkaz](../statements/sub-statement.md)
- [Function – příkaz](../statements/function-statement.md)
