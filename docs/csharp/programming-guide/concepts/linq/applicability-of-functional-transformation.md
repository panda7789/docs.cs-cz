---
title: Použitelnost funkční transformace (C#)
ms.date: 07/20/2015
ms.assetid: c78107bd-b006-4574-a3d4-bbf808388ff3
ms.openlocfilehash: baa3866c8c2c148a3080522d7c02e28e9d0fd945
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/15/2018
ms.locfileid: "45641258"
---
# <a name="applicability-of-functional-transformation-c"></a>Použitelnost funkční transformace (C#)
Čistě funkční transformace se dají použít v nejrůznějších situacích.  
  
 Funkční transformace přístup je ideální pro dotazování a zpracování strukturovaných dat; proto souladu s technologií LINQ. Funkční transformace však má mnohem širší použitelnost než LINQ. Jakýkoli proces, kde je hlavní fokus na transformaci dat z jednoho formuláře do jiného pravděpodobně být zařazena mezi kandidáty pro funkční transformace.  
  
 Tento přístup se vztahuje na mnoho problémů, které nemusí být kandidát na první pohled zobrazit. Používá ve spojení s nebo samostatně z technologie LINQ, funkční transformace by měl být v následujících oblastech:  
  
-   Dokumenty XML. Ve správném formátu data z libovolné dialekt XML lze snadno ovládat pomocí funkční transformace. Další informace najdete v tématu [funkční transformace XML (C#)](../../../../csharp/programming-guide/concepts/linq/functional-transformation-of-xml.md).  
  
-   Ostatní formáty souborů structured. Většina souborů ze souborů Windows.ini do prostého textu, dokumentů, mají některé struktura, která slouží k analýze a transformace.  
  
-   Protokoly streamování dat. Data kódování a dekódování dat z komunikační protokoly můžete často reprezentované pomocí jednoduchého funkční transformace.  
  
-   Relační databázový systém a OODBMS data. Relační a objektově orientované databáze, stejně jako XML, jsou široce používaný strukturovaných datových zdrojů.  
  
-   Řešení matematických, statistiky a vědy. Tato pole mají tendenci k práci s velkými datovými sadami, aby pomáhaly při vizualizaci, odhad, nebo ve skutečnosti řešení potíží, které nejsou v netriviálních uživatele.  
  
 Jak je popsáno v [refaktoring do čistých funkcí (C#)](../../../../csharp/programming-guide/concepts/linq/refactoring-into-pure-functions.md), pomocí čisté funkce je příkladem funkčního programování. V další okamžitě přináší výhody použití čistě funkce poskytuje cenné zkušenosti zamyslíme nad problémy z hlediska funkční transformace. Tento přístup také může mít významný vliv na návrh aplikace a třídy. To platí zejména při problém slouží k transformaci řešení data, jak je popsáno výše.  
  
 I když jsou nad rámec tohoto kurzu, návrhů, které jsou ovlivněny funkční transformace perspektivy mají tendenci center procesů více než u objektů jako objekty actor a výsledné řešení obvykle možné implementovat jako řadu ve velkém měřítku transformace, spíše než změní stav jednotlivých objektů.  
  
 Znovu nezapomeňte, že podporuje jazyk C# imperativní a funkční přístupy, takže nejvhodnější návrh pro vaši aplikaci může obsahovat prvky obou.  
  
## <a name="see-also"></a>Viz také

- [Úvod k čistě funkčním transformacím (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
- [Funkční transformace XML (C#)](../../../../csharp/programming-guide/concepts/linq/functional-transformation-of-xml.md)  
- [Refaktoring do čistých funkcí (C#)](../../../../csharp/programming-guide/concepts/linq/refactoring-into-pure-functions.md)
