---
title: Není připojena myš
ms.date: 07/20/2015
f1_keywords:
- vbrMouse_NoMouseIsPresent
ms.assetid: 4472fd57-4217-4463-9d3c-dc4a8fe88f1b
ms.openlocfilehash: f69371ea2db1aba5d3ad501ab41a9ea6e646ad3b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557874"
---
# <a name="no-mouse-is-present"></a>Není připojena myš
Jedna z vlastností objektu `My.Computer.Mouse` byla volána objektu, ale počítač nemá žádné myši a portem myši nainstalované.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Přidat `Try...Catch` blok po volání na vlastnost `My.Computer.Mouse` objektu.  
  
     – nebo –  
  
-   Nainstalujte do počítače myši.  
  
## <a name="see-also"></a>Viz také:
- [My.Computer.Mouse](xref:Microsoft.VisualBasic.Devices.Mouse)
- [Výjimky a zpracování chyb v jazyce Visual Basic](https://msdn.microsoft.com/library/3e351e73-cf23-40ab-8b60-05794160529e)
- [Příkaz Try...Catch...Finally](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
