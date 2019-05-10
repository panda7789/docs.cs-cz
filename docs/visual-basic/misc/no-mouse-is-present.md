---
title: Není připojena myš
ms.date: 07/20/2015
f1_keywords:
- vbrMouse_NoMouseIsPresent
ms.assetid: 4472fd57-4217-4463-9d3c-dc4a8fe88f1b
ms.openlocfilehash: 5493cea8c87a40b0c9663aaa7f36ce6cb423d346
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624862"
---
# <a name="no-mouse-is-present"></a>Není připojena myš
Jedna z vlastností objektu `My.Computer.Mouse` byla volána objektu, ale počítač nemá žádné myši a portem myši nainstalované.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Přidat `Try...Catch` blok po volání na vlastnost `My.Computer.Mouse` objektu.  
  
     – nebo –  
  
- Nainstalujte do počítače myši.  
  
## <a name="see-also"></a>Viz také:

- [My.Computer.Mouse](xref:Microsoft.VisualBasic.Devices.Mouse)
- [Zpracování a vyvolání výjimek v rozhraní .NET](../../standard/exceptions/index.md)
- [Příkaz Try...Catch...Finally](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
