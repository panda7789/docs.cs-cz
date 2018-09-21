---
title: Funkční programování vs. Imperativní programování (C#)
ms.date: 07/20/2015
ms.assetid: 5e35c5a0-c949-422a-873b-fca6b2254f57
ms.openlocfilehash: 01be2758147b84af3410709aab62a0ca89b0c9cf
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46532711"
---
# <a name="functional-programming-vs-imperative-programming-c"></a>Funkční programování vs. Imperativní programování (C#)
Toto téma porovnává a výrazně liší od tradičnější imperativního (procesního) programování s funkčního programování.  
  
## <a name="functional-programming-vs-imperative-programming"></a>Funkční programování vs. Imperativní programování  
 *Funkční programování* paradigma byla explicitně vytvořili za účelem podpory čistě funkční přístup k řešení problémů. Funkční programování je forma *programování deklarativních*. Naproti tomu byly navrženy většiny běžných jazyků, včetně objektově orientované programovací jazyky (OOP) jako je C#, Visual Basic, C++ a jazyka Java, především podpoře *imperativní* (procesního) programování.  
  
 S imperativní přístup vývojář píše kód, který popisuje v přesnější podrobností kroky, které počítače nutné provést k dosažení tohoto cíle. To se někdy označuje jako *vylepšením* programování. Naproti tomu funkční přístup zahrnuje vytváření problému jako sadu funkcí, které má být proveden. Můžete definovat důkladně vstup pro každou funkci a jaké každá funkce vrátí. Následující tabulka popisuje některé obecné rozdíly mezi těmito dvěma přístupy.  
  
|Vlastnost|Imperativní přístup|Funkční přístup|  
|--------------------|-------------------------|-------------------------|  
|Programátor fokus|Jak provádět úkoly (algoritmy) a jak sledovat změny stavu.|Jaké informace je požadován a jaké transformace jsou povinné.|  
|Změny stavu|Důležité.|Neexistující.|  
|Pořadí provádění|Důležité.|S nízkou důležitostí.|  
|Řízení toku na primární|Smyčky, podmíněné příkazy a volání funkcí (metoda).|Volání funkcí, včetně rekurze.|  
|Manipulace s primární částí|Instance struktur nebo tříd.|Funkce jako první třídy objektů a dat kolekce.|  
  
 I když většina jazyků byly navrženy pro podporu konkrétní programovacího paradigmatu, mnoho obecné jazyky jsou dostatečně flexibilní, aby podporovat více paradigmat. Většina jazyků, které obsahují ukazatele na funkce lze například hrozit podporu funkčního programování. Kromě toho C# obsahuje explicitní jazyková rozšíření pro podporu funkčního programování, včetně výrazů lambda a odvození typu. Technologie LINQ je forma deklarativní, funkční programování.  
  
## <a name="functional-programming-using-xslt"></a>Funkční programování pomocí XSLT  
 Mnoho vývojářů XSLT obeznámeni s čistě funkční přístup. Nejúčinnější způsob, jak vyvíjet šablony stylů XSLT je považovat za každou šablonu izolované, sestavitelný transformace. Pořadí provádění není úplně zruší zvýrazněné. XSLT nepovoluje vedlejší účinky (s výjimkou, že uvození mechanismy pro provádění kódu procedury může způsobovat vedlejší účinky, jejichž výsledkem funkční nečistot). Ale efektivní nástroj sice XSLT některé jeho vlastnosti nejsou optimální. Například vyjádření programovací konstrukce jazyka XML je kód relativně podrobné a proto obtížné udržovat. Navíc může způsobit náročné závislost na rekurze pro řízení toku kód, který je obtížné číst. Další informace o XSLT, naleznete v tématu [transformace XSLT](../../../../standard/data/xml/xslt-transformations.md).  
  
 XSLT se ukázalo jako hodnotu použití čistě funkční přístup pro transformaci XML z jednoho obrazce na jiný. Čistě funkční programování s LINQ to XML je podobná ve spoustě ohledů XSLT. Programovací konstrukce zavedených v technologii LINQ to XML a C# vám ale umožní k zápisu čistě funkční transformace, které jsou čitelnější a udržovatelný než XSLT.  
  
## <a name="advantages-of-pure-functions"></a>Výhody čisté funkce  
 Hlavním důvodem pro implementaci funkční transformace jako čistě funkce je, že čistě funkce sestavitelný: to znamená, samostatná a bezstavové. Tyto vlastnosti přinést řadu výhod, včetně následujících:  
  
-   Zvýšení přehlednosti a udržovatelnosti. Toto je vzhledem k tomu, že každá funkce je navržená k provedení určitého úkolu přiřazena svých argumentů. Funkce nevyžaduje žádné externího stavu.  
  
-   Snadnější reiterative vývoje. Vzhledem k tomu je snazší Refaktorovat kód, změny návrhu jsou často usnadnil. Předpokládejme například, můžete psát složitější transformace a potom dobré si uvědomit, že nějaký kód je několikrát opakovat v transformace. Pokud refaktorujete prostřednictvím čistě metody, může volat vaši čistě metodu kdykoli bez starostí o vedlejší účinky.  
  
-   Snazší testování a ladění. Protože čistě funkce můžete snadněji zkoušet v izolaci, můžete napsat kód testu, který volá funkci čistě s typické hodnoty platné hraniční případy a neplatný hraniční případy.  
  
## <a name="transitioning-for-oop-developers"></a>Přechod pro vývojáře OOP  
 V tradičních objektově orientované programování (OOP), jsou zvyklí na programování ve stylu dnešní/procedurální Většina vývojářů. Přepnout na vývoj ve stylu čistě funkční, musí provést přechod v jejich přemýšlení a jejich přístup k vývoji.  
  
 K řešení problémů, vývojáře OOP návrhu hierarchií tříd, zaměřte se na řádné zapouzdření a uvažují v rámci smluv třídy. Chování a stav typy objektů jsou prvořadá a jazykové funkce, jako jsou třídy, rozhraní, dědičnosti a polymorfismu, jsou k dispozici k těmto problémům.  
  
 Naproti tomu funkční programování blíží výpočetní problémy jako cvičení v pořadí vyhodnocování čistě funkční transformace dat kolekce. Funkční programování se vyhnete stavu a proměnlivé datové a místo toho klade důraz aplikaci funkcí.  
  
 Naštěstí C# nevyžaduje úplnou i pro funkční programování, protože podporuje imperativní a funkční programování přístupy. Vývojář můžete zvolit, jaký přístup je pro konkrétní scénář nejvhodnější. Ve skutečnosti programy často kombinací obou metod.  
  
## <a name="see-also"></a>Viz také

- [Úvod k čistě funkčním transformacím (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
- [Transformace XSLT](../../../../standard/data/xml/xslt-transformations.md)  
- [Refaktoring do čistých funkcí (C#)](../../../../csharp/programming-guide/concepts/linq/refactoring-into-pure-functions.md)
