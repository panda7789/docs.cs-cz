---
title: Funkční programování vs. Imperativní programování (C#)
ms.date: 07/20/2015
ms.assetid: 5e35c5a0-c949-422a-873b-fca6b2254f57
ms.openlocfilehash: a163a62912ed2a44d6ea8cad5bc536f03343f15c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594311"
---
# <a name="functional-programming-vs-imperative-programming-c"></a>Funkční programování vs. Imperativní programování (C#)
Toto téma porovnává a kontrastuje funkční programování s více tradičními imperativních (procedurální) programování.  
  
## <a name="functional-programming-vs-imperative-programming"></a>Funkční programování vs. imperativní programování  
 *Funkce programovacího programování* byla explicitně vytvořena pro podporu čistě funkčního přístupu k řešení problémů. Funkční programování je forma deklarativního *programování*. Naopak většina běžných jazyků, včetně objektově orientovaného programování (OOP), jako C#jsou například Visual Basic, C++a Java, byla navržena tak, aby primárně podporovala *imperativní* (procedurální) programování.  
  
 V případě imperativního přístupu Vývojář zapíše kód, který popisuje přesný popis kroků, které musí počítač provést k dosažení cíle. Tento postup se někdy označuje jako *algoritmy* programování. Kromě toho funkční přístup zahrnuje vytvoření problému jako sady funkcí, které mají být provedeny. Nadefinujete pečlivě vstup na jednotlivé funkce a funkci, kterou vrátí každá funkce. Následující tabulka popisuje některé z obecných rozdílů mezi těmito dvěma přístupy.  
  
|Charakteristiku|Imperativní přístup|Funkční přístup|  
|--------------------|-------------------------|-------------------------|  
|Programátorské zaměření|Jak provádět úlohy (algoritmy) a jak sledovat změny ve stavu.|Jaké informace jsou požadovány a jaké transformace jsou vyžadovány.|  
|Změny stavu|Významná.|Neexistující.|  
|Pořadí spouštění|Významná.|Nízká důležitost.|  
|Primární řízení toku|Cykly, podmíněné funkce a volání funkcí (metoda).|Volání funkcí, včetně rekurze.|  
|Primární manipulační jednotka|Instance struktur nebo tříd.|Funguje jako objekty a kolekce dat první třídy.|  
  
 I když většina jazyků byla navržena pro podporu konkrétního programovacího paradigmata, mnoho obecných jazyků je dostatečně flexibilní, aby podporovalo více paradigmat. Například většina jazyků, které obsahují ukazatele na funkce, může být použita k crediblyí podpory funkčního programování. Kromě toho C# obsahuje explicitní jazyková rozšíření pro podporu funkčního programování, včetně výrazů lambda a odvození typu. Technologie LINQ je forma deklarativního funkčního programování.  
  
## <a name="functional-programming-using-xslt"></a>Funkční programování pomocí XSLT  
 Mnoho vývojářů XSLT je obeznámené s čistě funkčním přístupem. Nejúčinnější způsob, jak vytvořit šablonu stylů XSLT, je zacházet s každou šablonou jako s izolovanou a sestavitelnou transformací. Pořadí spuštění je zcela zvýrazněné. XSLT nepovoluje vedlejší účinky (s výjimkou, že řídicí mechanismy pro spuštění procedurálního kódu mohou představovat vedlejší účinky, které mají za následek funkční nečistotu). I když je jazyk XSLT účinným nástrojem, některé z jeho vlastností nejsou optimální. Například vyjadřující programovací konstrukce v XML zjednodušují kód poměrně podrobné, a proto je obtížné ho udržovat. Velmi náročné na rekurzi pro řízení toku může mít za následek těžko čitelný kód. Další informace o XSLT naleznete v tématu [transformace XSLT](../../../../standard/data/xml/xslt-transformations.md).  
  
 XSLT však ukázala hodnotu použití čistě funkčního přístupu pro transformaci XML z jednoho obrazce na jiný. Čistě funkční programování s LINQ to XML je podobně v mnoha způsobech transformace XSLT. Nicméně programovací konstrukce zavedené LINQ to XML a C# umožňují psát čistě funkční transformace, které jsou čitelnější a udržovatelnější než XSLT.  
  
## <a name="advantages-of-pure-functions"></a>Výhody čistě funkcí  
 Hlavním důvodem pro implementaci funkční transformace jako čistě funkcí je, že čistě funkce jsou sestavitelné: to znamená, že jsou samostatné a bezstavové. Tyto charakteristiky přinášejí řadu výhod, včetně následujících:  
  
- Zvýšení čitelnosti a udržovatelnosti. Je to proto, že každá funkce je navržena k provedení konkrétního úkolu, který je dán argumenty. Funkce nespoléhá na žádný externí stav.  
  
- Jednodušší vývoj. Vzhledem k tomu, že kód je snazší Refaktorovat, je často snazší implementovat změny návrhu. Předpokládejme například, že píšete složitou transformaci a pak si myslíte, že je nějaký kód několikrát opakován v transformaci. Pokud provádíte refaktorování čistě metody, můžete zavolat metodu Pure na, aniž byste se museli starat o vedlejší účinky.  
  
- Jednodušší testování a ladění. Vzhledem k tomu, že čisté funkce lze snáze testovat v izolaci, můžete napsat testovací kód, který volá funkci Pure s typickými hodnotami, platnými okraji a neplatnými hraničními případy.  
  
## <a name="transitioning-for-oop-developers"></a>Přechod pro vývojáře OOP  
 V tradičním objektově orientovaném programování (OOP) je většina vývojářů zvykla na programování ve stylu imperativního/procedurálního. Chcete-li přepnout do vývoje čistě funkčního stylu, musí provést přechod v jejich přemýšlejce a jejich přístupu k vývoji.  
  
 Chcete-li vyřešit problémy, vývojáři OOP navrhují hierarchie tříd, soustředit se na správné zapouzdření a vzít v úvahu pojem smlouvy. Chování a stav typů objektů jsou nejdůležitější a jazykové funkce, jako jsou třídy, rozhraní, dědičnost a polymorfismu, jsou poskytnuty k vyřešení těchto otázek.  
  
 Naproti tomu funkční programování přistupuje k výpočetním problémům jako cvičení při vyhodnocování čistě funkčních transformací kolekcí dat. Funkční programování zabraňuje stavovým a proměnlivým datům a místo toho zvýrazní použití funkcí.  
  
 Naštěstí, C# nevyžaduje úplný odkaz na funkční programování, protože podporuje jak imperativně, tak i funkční programovací postupy. Vývojář si může vybrat, který přístup je nejvhodnější pro konkrétní scénář. V některých případech programy často kombinují obě přístupy.  
  
## <a name="see-also"></a>Viz také:

- [Úvod do čistě funkční transformace (C#)](./introduction-to-pure-functional-transformations.md)
- [Transformace XSLT](../../../../standard/data/xml/xslt-transformations.md)
- [Refaktoring do čistě funkcí (C#)](./refactoring-into-pure-functions.md)
