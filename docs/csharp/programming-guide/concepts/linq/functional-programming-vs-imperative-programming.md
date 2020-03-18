---
title: Funkční programování vs. imperativní programování (C#)
ms.date: 07/20/2015
ms.assetid: 5e35c5a0-c949-422a-873b-fca6b2254f57
ms.openlocfilehash: a163a62912ed2a44d6ea8cad5bc536f03343f15c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69594311"
---
# <a name="functional-programming-vs-imperative-programming-c"></a>Funkční programování vs. imperativní programování (C#)
Toto téma porovnává a kontrastuje funkční programování s více tradiční imperativní (procedurální) programování.  
  
## <a name="functional-programming-vs-imperative-programming"></a>Funkční programování vs. imperativní programování  
 Funkční *programovací* paradigma bylo explicitně vytvořeno pro podporu čistě funkčního přístupu k řešení problémů. Funkční programování je formou *deklarativního programování*. Naproti tomu většina běžných jazyků, včetně jazyky objektově orientovaného programování (OOP), jako je C#, Visual Basic, C++ a Java, byla navržena především tak, aby podporovala *imperativní* (procedurální) programování.  
  
 S imperativní přístup, vývojář zapíše kód, který podrobně popisuje kroky, které musí počítač provést k dosažení cíle. To se někdy označuje jako *algoritmické* programování. Naproti tomu funkční přístup zahrnuje skládání problému jako sadu funkcí, které mají být provedeny. Pečlivě definujete vstup pro každou funkci a co jednotlivé funkce vrátí. Následující tabulka popisuje některé obecné rozdíly mezi těmito dvěma přístupy.  
  
|Charakteristika|Imperativní přístup|Funkční přístup|  
|--------------------|-------------------------|-------------------------|  
|Zaměření programátora|Jak provádět úkoly (algoritmy) a jak sledovat změny ve stavu.|Jaké informace jsou žádoucí a jaké transformace jsou požadovány.|  
|Změny stavu|Důležité.|Neexistující.|  
|Pořadí exekuce|Důležité.|Nízká důležitost.|  
|Primární řízení průtoku|Smyčky, podmíněné a volání funkce (metody).|Funkční volání, včetně rekurze.|  
|Primární manipulační jednotka|Instance struktur nebo tříd.|Funguje jako prvotřídní objekty a kolekce dat.|  
  
 Ačkoli většina jazyků byla navržena tak, aby podporovala konkrétní programovací paradigma, mnoho obecných jazyků je dostatečně flexibilních, aby podporovaly více paradigmat. Například většina jazyků, které obsahují ukazatele funkce lze věrohodně podporovat funkční programování. Kromě toho C# obsahuje explicitní rozšíření jazyka pro podporu funkční programování, včetně lambda výrazy a odvození typu. TECHNOLOGIE LINQ je formou deklarativního funkčního programování.  
  
## <a name="functional-programming-using-xslt"></a>Funkční programování pomocí XSLT  
 Mnoho vývojářů XSLT je obeznámeno s čistě funkčním přístupem. Nejúčinnějším způsobem, jak vytvořit šablonu stylů XSLT, je považovat každou šablonu za izolovanou a kompozitní transformaci. Pořadí provedení je zcela de-zdůraznil. XSLT neumožňuje vedlejší účinky (s výjimkou, že uvození mechanismy pro provádění procedurální kód může zavést vedlejší účinky, které mají za následek funkční nečistoty). Ačkoli xslt je účinný nástroj, některé jeho vlastnosti nejsou optimální. Například vyjádření programovací chod v JAZYCE XML umožňuje relativně podrobné kóda a proto je obtížné jej udržovat. Také těžké spoléhání se na rekurzi pro řízení toku může mít za následek kód, který je těžko čitelný. Další informace o XSLT naleznete v tématu [Transformace XSLT](../../../../standard/data/xml/xslt-transformations.md).  
  
 XSLT však prokázalhodnotu použití čistě funkční přístup pro transformaci XML z jednoho obrazce do druhého. Čisté funkční programování s LINQ na XML je v mnoha ohledech podobné XSLT. Však programovací konstrukce zavedené LINQ do XML a C# umožňují psát čistě funkční transformace, které jsou čitelnější a udržovatelné než XSLT.  
  
## <a name="advantages-of-pure-functions"></a>Výhody čistých funkcí  
 Hlavním důvodem pro implementaci funkční transformace jako čisté funkce je, že čisté funkce jsou kompozitovatelné: to znamená, že samostatné a bezstavové. Tyto vlastnosti přinášejí řadu výhod, včetně následujících:  
  
- Zvýšená čitelnost a udržovatelnost. Důvodem je, že každá funkce je navržena tak, aby splnila určitý úkol vzhledem k jeho argumentům. Funkce nespoléhá na žádný externí stav.  
  
- Snadnější reiterativní vývoj. Vzhledem k tomu, že kód je jednodušší refaktorovat, změny návrhu jsou často jednodušší implementovat. Předpokládejme například, že napíšete složitou transformaci a pak si uvědomíte, že některé kód se opakuje několikrát v transformaci. Máte-li refaktorovat prostřednictvím čisté metody, můžete volat svou čistou metodu podle vůle bez obav o vedlejší účinky.  
  
- Snadnější testování a ladění. Vzhledem k tomu, že čisté funkce lze snadněji testovat izolovaně, můžete napsat testovací kód, který volá čistou funkci s typickými hodnotami, platnými hraničními případy a neplatnými hraničními případy.  
  
## <a name="transitioning-for-oop-developers"></a>Přechod pro vývojáře OOP  
 V tradičním objektově orientovaném programování (OOP) je většina vývojářů zvyklá na programování v imperatickém/procedurálním stylu. Chcete-li přejít na rozvoj v čistém funkčním stylu, musí provést přechod ve svém myšlení a jejich přístup k rozvoji.  
  
 Chcete-li vyřešit problémy, vývojáři OOP navrhují hierarchie tříd, zaměřují se na správné zapouzdření a přemýšlejí z hlediska smluv třídy. Chování a stav typů objektů jsou prvořadé a jazykové funkce, jako jsou třídy, rozhraní, dědičnost a polymorfismus, jsou k dispozici k řešení těchto problémů.  
  
 Naproti tomu funkční programování přistupuje k výpočetním problémům jako cvičení při hodnocení čistě funkčních transformací sběru dat. Funkční programování zabraňuje stavu a proměnlivá data a místo toho klade důraz na použití funkcí.  
  
 Naštěstí C# nevyžaduje úplný skok na funkční programování, protože podporuje imperativní a funkční programovací přístupy. Vývojář si může vybrat, který přístup je nejvhodnější pro konkrétní scénář. Ve skutečnosti programy často kombinují oba přístupy.  
  
## <a name="see-also"></a>Viz také

- [Úvod do čistě funkčních transformací (C#)](./introduction-to-pure-functional-transformations.md)
- [Transformace XSLT](../../../../standard/data/xml/xslt-transformations.md)
- [Refaktoring do čistých funkcí (C#)](./refactoring-into-pure-functions.md)
