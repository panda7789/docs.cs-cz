---
title: Kdy použít výčet (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
ms.openlocfilehash: ff2d8c324aee8bbccef050c020e5392368b05b1c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825094"
---
# <a name="when-to-use-an-enumeration-visual-basic"></a>Kdy použít výčet (Visual Basic)
Výčty nabízí snadný způsob, jak pracovat se sadami související s konstantami. Což je výčet nebo `Enum`, je symbolický název pro sadu hodnot. Výčty jsou považovány za datových typů a můžete využít k vytvoření sady konstanty pro použití s proměnných a vlastností.  
  
## <a name="when-to-use-an-enumeration"></a>Kdy použít výčet  
 Pokaždé, když procedury přijímá omezenou sadu proměnných, zvažte možnost použít výčet. Výčty usnadňují srozumitelnější a čitelnější kód, zejména v případě, že používají smysluplné názvy.  
  
 Výhody používání výčtů patří:  
  
-   Snižuje chyby způsobené transpozice nebo chybným zadáním čísla.  
  
-   Umožňuje snadno ke změně hodnot v budoucnu.  
  
-   Díky kód lépe čitelný, což znamená, že je méně pravděpodobné, že se do něj ovládat chyby.  
  
-   Zajišťuje kompatibilitu. S výčty váš kód je méně pravděpodobné, že selhat, pokud v budoucnu někdo změní hodnoty odpovídající názvy členů.  
  
## <a name="naming-enumerations"></a>Názvy výčtů  
 Použijte zásady vytváření názvů pro členy výčtu. Pokud jazyka Visual Basic narazí název člena výčtu, může vyvolána výjimka, pokud obsahují další odkazované knihovny typů se stejným názvem. Použijte jedinečnou předponu, která identifikuje hodnoty z vaší aplikace nebo komponenty.  
  
 Při odkazování na člena výčtu, které musí kvalifikovat název člena s názvem výčtu jinak použít `Imports` příkazu. Další informace najdete v tématu [výčty a kvalifikace názvu](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
## <a name="predefined-enumerations"></a>Předdefinované výčty  
 Visual Basic nabízí celou řadu předdefinovaných výčty, jako například `FirstDayOfWeek` a `MsgBoxResult`, které usnadní váš kód. Jejich seznam naleznete v tématu [konstanty a výčty](../../../../visual-basic/language-reference/constants-and-enumerations.md).  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Deklarace výčtů](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Postupy: Odkazování na člena výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Výčty a kvalifikace názvu](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Postupy: Iterace ve výčtu v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [Postupy: Určení řetězce spojeného s hodnotou výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Příkaz Enum](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [Konstanty a výčty](../../../../visual-basic/language-reference/constants-and-enumerations.md)
