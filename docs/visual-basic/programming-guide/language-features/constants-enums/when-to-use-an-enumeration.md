---
title: Kdy použít výčet
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
ms.openlocfilehash: ba69249e16b8c0ee06d57d06d192874a283b295e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403534"
---
# <a name="when-to-use-an-enumeration-visual-basic"></a>Kdy použít výčet (Visual Basic)
Výčty představují snadný způsob, jak pracovat se sadami souvisejících konstant. Výčet nebo `Enum` je symbolický název pro sadu hodnot. Výčty jsou považovány za datové typy a lze je použít k vytvoření sady konstant pro použití s proměnnými a vlastnostmi.  
  
## <a name="when-to-use-an-enumeration"></a>Kdy použít výčet  
 Pokaždé, když procedura přijme omezené sady proměnných, zvažte použití výčtu. Výčty vycházejí z jasných a čitelnějších kódů, zejména v případě, že se používají smysluplné názvy.  
  
 Mezi výhody používání výčtů patří:  
  
- Snižuje chyby způsobené přetypováním nebo nesprávným zadáním čísel.  
  
- V budoucnu usnadňuje změnu hodnot.  
  
- Usnadňuje čtení kódu, což znamená, že je méně pravděpodobný, že se na něj chyby ponárůstí.  
  
- Zajišťuje dopředné kompatibility. V případě výčtů je váš kód méně pravděpodobný, pokud v budoucnu někdo změní hodnoty odpovídající názvům členů.  
  
## <a name="naming-enumerations"></a>Vytváření názvů výčtů  
 Použijte zásady vytváření názvů pro členy výčtu. Když Visual Basic narazí na název člena výčtu, může být vyvolána výjimka, pokud jiné odkazované knihovny typů obsahují stejný název. Použijte jedinečnou předponu, která identifikuje hodnoty z vaší aplikace nebo komponenty.  
  
 Při odkazování na člena výčtu je nutné kvalifikovat název člena s názvem výčtu nebo jinak použít `Imports` příkaz. Další informace naleznete v tématu [výčty a kvalifikace názvu](enumerations-and-name-qualification.md).  
  
## <a name="predefined-enumerations"></a>Předdefinované výčty  
 Visual Basic poskytuje řadu předdefinovaných výčtů, jako jsou `FirstDayOfWeek` a `MsgBoxResult` , pro usnadnění kódu. Seznam těchto naleznete v tématu [konstanty a výčty](../../../language-reference/constants-and-enumerations.md).  
  
## <a name="see-also"></a>Viz také

- [Postupy: deklarace výčtu](how-to-declare-enumerations.md)
- [Postupy: Odkazování na člena výčtu](how-to-refer-to-an-enumeration-member.md)
- [Výčty a kvalifikace názvu](enumerations-and-name-qualification.md)
- [Postupy: Iterace ve výčtu jazyka Visual Basic](how-to-iterate-through-an-enumeration.md)
- [Postupy: Určení řetězce spojeného s hodnotou výčtu](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Enum – příkaz](../../../language-reference/statements/enum-statement.md)
- [Konstanty a výčty](../../../language-reference/constants-and-enumerations.md)
