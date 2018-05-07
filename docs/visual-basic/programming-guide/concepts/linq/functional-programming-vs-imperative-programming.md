---
title: Funkční programování vs. Imperativní programování (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 6a1f3b57-00e6-447d-9906-74c7c4d5d85c
ms.openlocfilehash: 63d3801a393b242bce8b497e2c983534a6996c6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="functional-programming-vs-imperative-programming-visual-basic"></a>Funkční programování vs. Imperativní programování (Visual Basic)
Toto téma porovnává a výrazně liší od funkční programování s tradičnější imperativní programování (procedurální).  
  
## <a name="functional-programming-vs-imperative-programming"></a>Funkční programování vs. Imperativní programování  
 *Funkční programování* zlepší explicitně vytvořil pro podporu čistý funkční přístup k řešení problémů. Funkční programování je forma *deklarativní programování*. Na rozdíl od většiny všeobecně jazyků, včetně objektově orientované programovací jazyky (mimoprocesová aplikace VOLÁNA) například C#, Visual Basic, C++ a Java, byly navrženy pro podporu především *imperativní* programování (procedurální).  
  
 S imperativní přístup vývojář se zapisují kód, který popisuje přesnější podrobné kroky, které počítače musí provést k dosažení cíle. To se někdy označuje jako *algoritmické* programování. Naproti tomu funkční přístupu zahrnuje skládání problém jako sady funkcí, které by šlo spustit. Definujete pečlivě vstup pro jednotlivé funkce, a vrátí co jednotlivé funkce. Následující tabulka popisuje některé obecné rozdíly mezi těmito dvěma přístupy.  
  
|Vlastnosti|Imperativní přístup|Funkční přístup|  
|--------------------|-------------------------|-------------------------|  
|Fokus programátory|Jak provádět úlohy (algoritmy) a jak můžete sledovat změny ve stavu.|Jaké informace se požaduje a jaké transformace jsou povinné.|  
|Změny stavu|Důležité.|Neexistující jiného typu.|  
|Pořadí provádění|Důležité.|Nízkou důležitostí.|  
|Řízení toku na primární|Smyčky, podmínky a volání funkce (metoda).|Volání funkcí, včetně rekurze.|  
|Manipulace s primární jednotka|Instance třídy nebo struktury.|Funkce jako první třídy objektů a dat kolekce.|  
  
 I když většina jazyky byly navrženy pro podporu konkrétní programovací zlepší, mnoha jazycích Obecné jsou dostatečně flexibilní pro podporu více vzorů. Například většina jazyky, které obsahují ukazatele na funkce slouží k podpoře hrozit funkční programování. Visual Basic navíc obsahuje explicitní jazyková rozšíření a podporu funkční programování, včetně výrazy lambda odvození typu. Technologie LINQ je forma deklarativní, funkční programování.  
  
## <a name="functional-programming-using-xslt"></a>Funkční programování pomocí XSLT  
 Celá řada vývojářů XSLT se seznámíte s čistě funkční přístup. Co nejúčinnější způsob, jak vyvíjet šablony stylů XSLT je považovat za každé šabloně transformaci izolovaný, bez možnosti složení. Pořadí zpracování je zcela zrušte zvýrazněné. XSLT neumožňuje vedlejší efekty (s jedinou výjimkou uvozovací znaky mechanismy pro provádění kódu procesního můžou představovat vedlejší účinky, jejichž výsledkem funkční nečistot). I když XSLT je nástroj pro efektivní, některé jeho vlastnosti jsou však není optimální. Například vyjadřující programovací konstrukce v XML díky kód relativně podrobné a proto poměrně složitá. Navíc může způsobit velkou spoléhat na rekurze pro řízení toku kód, který je těžko čitelný. Další informace o XSLT najdete v tématu [transformace XSLT](../../../../standard/data/xml/xslt-transformations.md).  
  
 XSLT se ukázalo jako hodnota použití čistý funkční přístupu pro převod XML z jednoho obrazce do jiného. Čistý funkční programování s technologie LINQ to XML je podobné jako v mnoha způsoby XSLT. Programovací konstrukce zavedených v technologii LINQ to XML a Visual Basic však umožňují zápisu čistý funkční transformace, které jsou čitelnější a udržovatelný než XSLT.  
  
## <a name="advantages-of-pure-functions"></a>Výhody čistý funkcí  
 Hlavním důvodem pro implementaci funkční transformace jako čistý funkce je, že čistý funkce bez možnosti složení: tedy samostatné a bezstavové. Tyto charakteristiky přineste řadu výhod, včetně následujících:  
  
-   Zvýšená přehlednosti a jeho udržovatelnost. To je vzhledem k tomu, že jednotlivé funkce slouží k provedení určité úlohy uveden její argumenty. Funkce nevyžaduje žádné externí stavu.  
  
-   Snadnější reiterative vývoj. Protože kód je snazší refactor, jsou často usnadňují implementaci změny návrhu. Předpokládejme například, zapsat složitý transformace a pak Uvědomte si, že nějaký kód je opakovaně transformace. Pokud jste Refaktorovat čistý metodou, můžete volat čistý metodu na bude bez obav, vedlejší účinky.  
  
-   Jednodušší testování a ladění. Protože čistý funkce lze snadno testovat v izolaci, můžete napsat testovací kód, který volá funkci čistý s typické hodnoty, platný edge případů a případů neplatný okraj.  
  
## <a name="transitioning-for-oop-developers"></a>Přechod pro vývojáře mimoprocesová aplikace VOLÁNA  
 V tradiční objektově orientované programování (mimoprocesová aplikace VOLÁNA), jsou uzpůsobené pro programování v styl imperativní nebo procedurální Většina vývojářů. Přejděte na vývoj ve stylu čistý funkční, mají proveďte přechod v jejich přemýšlení a jejich přístup pro vývoj.  
  
 K řešení problémů, vývojáři mimoprocesová aplikace VOLÁNA návrh hierarchie tříd, zaměřit na správné zapouzdření a vezměte v úvahu z hlediska kontrakty třídy. Chování a stav typy objektů jsou prvořadý a jazykové funkce, jako jsou třídy, rozhraní, dědičnost a polymorfismus, jsou dostupné k těmto problémům.  
  
 Funkční programování naopak blíží výpočetní problémy jako cvičení při vyhodnocení čistý funkční transformace dat kolekcí. Funkční programování zabraňuje stavu a měnitelný dat a místo toho klade důraz použití funkce.  
  
 Naštěstí jazyka Visual Basic nevyžaduje úplnou přestupného do funkční programování, protože podporuje imperativní a funkční programovací přístupy. Vývojář rozhodnout, jaký přístup je nejvhodnější pro konkrétní scénář. Ve skutečnosti programy často kombinací obou přístupů.  
  
## <a name="see-also"></a>Viz také  
 [Úvod do čistého funkční transformace (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
 [Transformace XSLT](../../../../standard/data/xml/xslt-transformations.md)  
 [Refaktoring do čistého funkce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/refactoring-into-pure-functions.md)
