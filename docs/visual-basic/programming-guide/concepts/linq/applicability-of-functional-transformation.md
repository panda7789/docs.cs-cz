---
title: Použitelnost funkční transformace (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 3b74e134-e19b-44bc-8d06-e26c48305040
ms.openlocfilehash: 01ebc25e77e7098d0aad5ec612e57d7f6b078d4f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54699399"
---
# <a name="applicability-of-functional-transformation-visual-basic"></a>Použitelnost funkční transformace (Visual Basic)
Čistě funkční transformace se dají použít v nejrůznějších situacích.  
  
 Funkční transformace přístup je ideální pro dotazování a zpracování strukturovaných dat; proto souladu s technologií LINQ. Funkční transformace však má mnohem širší použitelnost než LINQ. Jakýkoli proces, kde je hlavní fokus na transformaci dat z jednoho formuláře do jiného pravděpodobně být zařazena mezi kandidáty pro funkční transformace.  
  
 Tento přístup se vztahuje na mnoho problémů, které nemusí být kandidát na první pohled zobrazit. Používá ve spojení s nebo samostatně z technologie LINQ, funkční transformace by měl být v následujících oblastech:  
  
-   Dokumenty XML. Ve správném formátu data z libovolné dialekt XML lze snadno ovládat pomocí funkční transformace. Další informace najdete v tématu [funkční transformace XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-transformation-of-xml.md).  
  
-   Ostatní formáty souborů structured. Většina souborů ze souborů Windows.ini do prostého textu, dokumentů, mají některé struktura, která slouží k analýze a transformace.  
  
-   Protokoly streamování dat. Data kódování a dekódování dat z komunikační protokoly můžete často reprezentované pomocí jednoduchého funkční transformace.  
  
-   Relační databázový systém a OODBMS data. Relační a objektově orientované databáze, stejně jako XML, jsou široce používaný strukturovaných datových zdrojů.  
  
-   Řešení matematických, statistiky a vědy. Tato pole mají tendenci k práci s velkými datovými sadami, aby pomáhaly při vizualizaci, odhad, nebo ve skutečnosti řešení potíží, které nejsou v netriviálních uživatele.  
  
 Jak je popsáno v [refaktoring do čistých funkcí (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/refactoring-into-pure-functions.md), pomocí čisté funkce je příkladem funkčního programování. V další okamžitě přináší výhody použití čistě funkce poskytuje cenné zkušenosti zamyslíme nad problémy z hlediska funkční transformace. Tento přístup také může mít významný vliv na návrh aplikace a třídy. To platí zejména při problém slouží k transformaci řešení data, jak je popsáno výše.  
  
 I když jsou nad rámec tohoto kurzu, návrhů, které jsou ovlivněny funkční transformace perspektivy mají tendenci center procesů více než u objektů jako objekty actor a výsledné řešení obvykle možné implementovat jako řadu ve velkém měřítku transformace, spíše než změní stav jednotlivých objektů.  
  
 Znovu nezapomeňte, že jazyka Visual Basic podporuje imperativní a funkční přístupy, tak optimální pro vaši aplikaci může obsahovat prvky obou.  
  
## <a name="see-also"></a>Viz také:
- [Úvod k čistě funkčním transformacím (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
- [Funkční transformace XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-transformation-of-xml.md)
- [Refaktoring do čistých funkcí (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/refactoring-into-pure-functions.md)
