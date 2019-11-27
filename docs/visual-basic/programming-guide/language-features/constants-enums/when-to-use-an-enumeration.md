---
title: Kdy použít výčet
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
ms.openlocfilehash: 5daae8d487ddfe079a54e305e59e32e8ded8f65e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353961"
---
# <a name="when-to-use-an-enumeration-visual-basic"></a>Kdy použít výčet (Visual Basic)
Výčty představují snadný způsob, jak pracovat se sadami souvisejících konstant. Výčet nebo `Enum`je symbolického názvu pro sadu hodnot. Výčty jsou považovány za datové typy a lze je použít k vytvoření sady konstant pro použití s proměnnými a vlastnostmi.  
  
## <a name="when-to-use-an-enumeration"></a>Kdy použít výčet  
 Pokaždé, když procedura přijme omezené sady proměnných, zvažte použití výčtu. Výčty vycházejí z jasných a čitelnějších kódů, zejména v případě, že se používají smysluplné názvy.  
  
 Mezi výhody používání výčtů patří:  
  
- Snižuje chyby způsobené přetypováním nebo nesprávným zadáním čísel.  
  
- V budoucnu usnadňuje změnu hodnot.  
  
- Usnadňuje čtení kódu, což znamená, že je méně pravděpodobný, že se na něj chyby ponárůstí.  
  
- Zajišťuje dopředné kompatibility. V případě výčtů je váš kód méně pravděpodobný, pokud v budoucnu někdo změní hodnoty odpovídající názvům členů.  
  
## <a name="naming-enumerations"></a>Vytváření názvů výčtů  
 Použijte zásady vytváření názvů pro členy výčtu. Když Visual Basic narazí na název člena výčtu, může být vyvolána výjimka, pokud jiné odkazované knihovny typů obsahují stejný název. Použijte jedinečnou předponu, která identifikuje hodnoty z vaší aplikace nebo komponenty.  
  
 Při odkazování na člena výčtu je nutné kvalifikovat název člena s názvem výčtu nebo jinak použít příkaz `Imports`. Další informace naleznete v tématu [výčty a kvalifikace názvu](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
## <a name="predefined-enumerations"></a>Předdefinované výčty  
 Visual Basic poskytuje řadu předdefinovaných výčtů, jako je například `FirstDayOfWeek` a `MsgBoxResult`, pro usnadnění kódu. Seznam těchto naleznete v tématu [konstanty a výčty](../../../../visual-basic/language-reference/constants-and-enumerations.md).  
  
## <a name="see-also"></a>Viz také:

- [Postupy: deklarace výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Postupy: Odkazování na člena výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Výčty a kvalifikace názvu](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Postupy: iterace prostřednictvím výčtu v Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [Postupy: Určení řetězce spojeného s hodnotou výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Příkaz Enum](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [Konstanty a výčty](../../../../visual-basic/language-reference/constants-and-enumerations.md)
