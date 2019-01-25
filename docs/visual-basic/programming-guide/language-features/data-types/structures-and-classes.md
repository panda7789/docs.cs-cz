---
title: Struktury a třídy (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], vs. structures
- structures [Visual Basic]
- classes [Visual Basic]
- structures [Visual Basic], compared to classes
- structures [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: a221e74a-ffcf-4bdc-a0f6-a088a9bf26cc
ms.openlocfilehash: 78c1d529053a10fc208ee5499b759623c227cb25
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54681807"
---
# <a name="structures-and-classes-visual-basic"></a>Struktury a třídy (Visual Basic)
Visual Basic sjednocuje syntaxe struktur a tříd, s tím, že obě entity podporuje většinu stejné funkce. Existují však i důležité rozdíly mezi strukturami a třídami.  
  
 Třídy mají výhodou odkazové typy – předáním odkazu je efektivnější než předání proměnnou struktury obsahující všechna jeho data. Na druhé straně struktury nevyžadují přidělení paměti v haldě globální.  
  
 Protože nemůže dědit ze struktury, struktury by měla sloužit pouze pro objekty, které není potřeba prodloužit. Struktury použijte, pokud objekt, který chcete vytvořit má velikost malých instancí a vezměte v úvahu charakteristiky výkonu třídy a struktury.  
  
## <a name="similarities"></a>Podobnosti  
 Třídy a struktury jsou podobné jako u těchto ohledech:  
  
-   Obě jsou *kontejneru* typy, což znamená, že sloupce obsahují další typy jako členy.  
  
-   Obě mají členy, které může obsahovat konstruktory, metody, vlastnosti, pole, konstanty, výčty, události a obslužné rutiny událostí. Nezaměňujte však tito členové s deklarovaný *prvky* struktury.  
  
-   Členy obou můžete své úrovně přístupu. Například lze deklarovat jeden člen `Public` a další `Private`.  
  
-   Jak můžete implementovat rozhraní.  
  
-   Obojí může mít sdílené konstruktory, s nebo bez parametrů.  
  
-   Jak můžete zveřejnit *výchozí vlastnost*za předpokladu, že vlastnost používá nejméně jeden parametr.  
  
-   Obě deklarace a vyvolávání událostí, a obě deklarování delegátů.  
  
## <a name="differences"></a>Rozdíly  
 Struktury a třídy se liší v následující údaje:  
  
-   Struktury jsou *typů hodnot*; třídy jsou *referenční typy*. Proměnné typu struktura obsahuje data struktury, spíše než obsahující odkaz na data jako typ třídy nemá.  
  
-   Struktury použijte přidělení zásobníku; třídy použijte přidělení haldy.  
  
-   Všechny prvky struktury jsou `Public` ve výchozím nastavení; třída proměnné a konstanty jsou `Private` ostatních členů třídy jsou standardně `Public` ve výchozím nastavení. Toto chování pro členy třídy zajišťuje kompatibilitu se systémem Visual Basic 6.0 výchozích hodnot.  
  
-   Struktura musí mít aspoň jeden nesdílené proměnné nebo nesdílené, noncustom element události. Třída může být úplně prázdná.  
  
-   Elementy struktury nelze deklarovat jako `Protected`; můžete členy třídy.  
  
-   Proceduru struktury můžete zpracovávat události, pouze pokud je [sdílené](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub` postupu a pouze pomocí Řešitele [AddHandler – příkaz](../../../../visual-basic/language-reference/statements/addhandler-statement.md); všechny třídy procedury můžete zpracovávat události, pomocí buď [ Zpracovává](../../../../visual-basic/language-reference/statements/handles-clause.md) – klíčové slovo nebo `AddHandler` příkazu. Další informace najdete v tématu [události](../../../../visual-basic/programming-guide/language-features/events/index.md).  
  
-   Deklarace proměnné struktury nelze zadat inicializátory nebo počáteční velikosti pole; deklarace proměnných třídy můžete.  
  
-   Struktury implicitně dědí z <xref:System.ValueType?displayProperty=nameWithType> třídu a nemůže dědit z žádného jiného typu; třídy mohou dědit z libovolné třídy nebo tříd jiných než <xref:System.ValueType?displayProperty=nameWithType>.  
  
-   Struktury nejsou odvoditelný; třídy jsou.  
  
-   Struktury jsou nikdy ukončena, takže nikdy nevolá common language runtime (CLR) <xref:System.Object.Finalize%2A> metody na jinou strukturu; třídy jsou ukončeny systému uvolňování paměti (GC), která volá <xref:System.Object.Finalize%2A> ve třídě, když zjistí, že neexistují žádné aktivní odkazy Zbývající.  
  
-   Struktura nevyžaduje konstruktor; Třída nemá.  
  
-   Struktury mohou mít nesdílené konstruktory pouze v případě, že přijímají parametry; třídy mohou mít je s nebo bez parametrů.  
  
 Každá konstrukce má implicitní veřejný konstruktor bez parametrů. Tento konstruktor inicializuje všechny struktury datové prvky, aby jejich výchozí hodnoty. Toto chování nelze předefinovat.  
  
## <a name="instances-and-variables"></a>Instance a proměnné  
 Protože struktury jsou typy hodnot, každou proměnnou struktury je trvale svázána s instancí jednotlivých struktury. Ale třídy jsou odkazové typy a proměnné objektu mohou odkazovat na různé instance třídy v různých časech. Toto rozlišení ovlivňuje využití struktury a třídy následujícími způsoby:  
  
-   **Inicializace.** Proměnné struktury implicitně obsahuje inicializaci prvků pomocí konstrukcí konstruktor bez parametrů. Proto `Dim s As struct1` je ekvivalentní `Dim s As struct1 = New struct1()`.  
  
-   **Přiřazení proměnné.** Při přiřazení jednu proměnnou struktury do jiné nebo předat instanci struktury argumentu procedury, aktuální hodnoty prvků všechny proměnné zkopírují do novou strukturu. Při přiřadit jednu proměnnou objekt do jiné nebo předání proměnné objektu proceduře, zkopíruje pouze odkaz na ukazatel.  
  
-   **Přiřazení žádnou akci.** Přiřadíte hodnotu [nic](../../../../visual-basic/language-reference/nothing.md) na strukturu proměnnou, ale instance nadále být spojen s proměnnou. Stále můžete volat jeho metody a přístup k jeho prvkům data, i když proměnné prvky jsou opětovně inicializovány pomocí přiřazení.  
  
     Naopak pokud nastavíte proměnné objektu na `Nothing`oddělit z libovolné instance třídy a žádné členy nelze přistupovat prostřednictvím proměnné dokud přiřadit jinou instancí.  
  
-   **Více instancí.** Objektová proměnná může mít jinou třídu instancí přiřazená v různou dobu a několik objektových proměnných mohou odkazovat na stejnou instanci třídy ve stejnou dobu. Změny provedené na hodnoty členů třídy. ovlivňují tyto členy, když přistupuje prostřednictvím jiné proměnné odkazující na stejné instanci.  
  
     Prvky struktury, ale jsou izolované v rámci své vlastní instance. Změny jejich hodnoty se neprojeví v jakékoli jiné proměnné struktury, dokonce i v dalších instancí stejného `Structure` deklarace.  
  
-   **Rovnost.** Testování rovnosti dvou struktur, je nutné provést s testu prvek po prvku. Dvě proměnné objektu lze porovnat pomocí <xref:System.Object.Equals%2A> metody. <xref:System.Object.Equals%2A> Určuje, zda dvě proměnné odkazovat na stejné instanci.  
  
## <a name="see-also"></a>Viz také:
- [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Složené datové typy](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Řešení potíží s datovými typy](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Struktury a ostatní programovací elementy](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [Objekty a třídy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
