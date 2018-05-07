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
ms.openlocfilehash: e64b54b93463845dd9afd0c0efd0e39f20cab1ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="structures-and-classes-visual-basic"></a>Struktury a třídy (Visual Basic)
Visual Basic kombinuje syntaxe struktury a třídy, s tím výsledkem, že obě entity podporují většinu stejné funkce. Existují však také důležité rozdíly mezi struktury a třídy.  
  
 Výhodou se odkazové typy jsou třídy – předáním odkazu na je efektivnější než předávání proměnná struktura s jeho data. Na druhé straně struktury nevyžadují přidělení paměti v haldě globální.  
  
 Protože nelze dědí strukturou, struktury slouží pouze pro objekty, které není potřeba rozšířit. Struktury použijte, pokud má velikost malých instance objektu, který chcete vytvořit a vezměte v úvahu charakteristiky výkonu už třídy a struktury.  
  
## <a name="similarities"></a>Podobnosti  
 Struktury a třídy jsou podobné v těchto ohledech:  
  
-   Jsou obě *kontejneru* typy, což znamená, že obsahují jiné typy jako členy.  
  
-   Mají obě členy, které mohou zahrnovat konstruktory, metody, vlastnosti, pole, konstanty, výčty, události a obslužné rutiny událostí. Nezaměňujte však tito členové s deklarovaný *elementy* struktury.  
  
-   Členové těchto dvou možností můžete své úrovně přístupu. Například lze deklarovat jednoho člena `Public` a jiné `Private`.  
  
-   Jak můžete implementovat rozhraní.  
  
-   Jak může mít sdílené konstruktory, s nebo bez parametrů.  
  
-   Jak můžou zpřístupnit *výchozí vlastnost*, za předpokladu, že má vlastnost minimálně jeden parametr.  
  
-   Obě deklarace a vyvolávání událostí a obě můžou deklarovat delegáti.  
  
## <a name="differences"></a>Rozdíly  
 Struktury a třídy se liší v tyto údaje:  
  
-   Struktury jsou *typů hodnot*; třídy jsou *odkazové typy*. Proměnné typu struktura obsahuje data struktura, nikoli obsahující odkaz na data jako typ třídy nemá.  
  
-   Struktury použijte přidělení zásobníku; třídy pomocí přidělení haldy.  
  
-   Všechny prvky struktura jsou `Public` ve výchozím nastavení; třídy proměnných a konstant jsou `Private` ve výchozím nastavení jsou členy jiné třídy `Public` ve výchozím nastavení. Toto chování pro členy třídy zajišťuje kompatibilitu s Visual Basic 6.0 systému výchozí hodnoty.  
  
-   Struktury musí mít alespoň jeden sdíleném proměnnou nebo sdíleném, noncustom event element; Třída může být zcela prázdný.  
  
-   Elementy struktury nelze deklarovat jako `Protected`; můžete členy třídy.  
  
-   Struktura postupu můžete zpracování událostí, pouze pokud je [sdílené](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub` postupu a pouze pomocí Řešitele [AddHandler – příkaz](../../../../visual-basic/language-reference/statements/addhandler-statement.md); všechny třídy postupu dokáže zpracovat události, s použitím buď [ Zpracovává](../../../../visual-basic/language-reference/statements/handles-clause.md) – klíčové slovo nebo `AddHandler` příkaz. Další informace najdete v tématu [události](../../../../visual-basic/programming-guide/language-features/events/index.md).  
  
-   Deklarace proměnných struktura nelze zadat inicializátory nebo počáteční velikosti pole; deklarace proměnných třídy můžete.  
  
-   Struktury implicitně dědí <xref:System.ValueType?displayProperty=nameWithType> třídy a nemůže Zdědit z libovolného typu; třídy můžete dědí všechny třídy nebo třídy jiné než <xref:System.ValueType?displayProperty=nameWithType>.  
  
-   Struktury nejsou zděditelné; třídy jsou.  
  
-   Struktury se nikdy ukončeno, takže modul CLR (CLR) nikdy nevolá <xref:System.Object.Finalize%2A> metodu na všechny struktura; třídy jsou ukončena modulem garbage collector (GC), který volá <xref:System.Object.Finalize%2A> na třídu, když zjistí neexistují žádné aktivní odkazy Zbývající.  
  
-   Struktury nevyžaduje konstruktor; Třída nepodporuje.  
  
-   Může mít struktury sdíleném konstruktory pouze v případě, že jejich trvat parametry; třídy lze nastavit s nebo bez parametrů.  
  
 Každý struktura má implicitní veřejný konstruktor bez parametrů. Tento konstruktor inicializuje všechna struktura datové prvky na výchozí hodnoty. Toto chování nelze znovu definovat.  
  
## <a name="instances-and-variables"></a>Instance a proměnné  
 Protože struktury jsou typy hodnot, každá proměnná struktura je trvale vázána instance jednotlivých struktura. Ale třídy jsou odkazové typy a proměnné objektu mohou odkazovat na různých instancí třídy v různých časech. Tento rozdíl ovlivní vaše použití třídy a struktury následujícími způsoby:  
  
-   **Inicializace.** Proměnné struktury zahrnuje implicitně inicializaci elementů pomocí struktura konstruktor bez parametrů. Proto `Dim s As struct1` je ekvivalentní `Dim s As struct1 = New struct1()`.  
  
-   **Přiřazení proměnné.** Pokud přiřadit jednu proměnnou struktura do jiné nebo struktura instance předat argumentu procedury, aktuálních hodnot všech proměnných elementů se zkopírují do nové struktury. Když přiřadit jednu proměnnou objekt do jiné nebo předání proceduře proměnné objektu, se zkopírují pouze odkaz na ukazatel.  
  
-   **Nic přiřazení.** Můžete přiřadit hodnotu [nic](../../../../visual-basic/language-reference/nothing.md) pro strukturu proměnné, ale instance nadále přidružená k proměnné. Můžete volat jeho metody a přístup k jeho datové prvky, i když proměnné elementy jsou opětovně inicializovány podle přiřazení.  
  
     Pokud nastavíte proměnné objektu na oproti tomu `Nothing`, zrušíte přidružení z jakékoli instance třídy a prostřednictvím proměnnou nelze přístup žádné členy, dokud přiřadit jiná instance.  
  
-   **Více instancí.** Objektová proměnná může mít jinou třídu instance přiřazen v různou dobu a několik objektové proměnné mohou odkazovat na stejnou instanci třídy ve stejnou dobu. Změny provedené na hodnoty členů tříd ovlivňují těmto členům přistupováno pomocí jiné proměnné odkazující na stejnou instanci.  
  
     Elementy struktury, ale jsou izolovány. v rámci své vlastní instanci. Změny jejich hodnoty se neprojeví v žádné jiné proměnné struktury, i v jiných instance stejné `Structure` deklarace.  
  
-   **Rovnosti.** Testování rovnosti dvou struktur musí provést test pomocí elementu. Dvě proměnné objektu je možné porovnávat pomocí <xref:System.Object.Equals%2A> metoda. <xref:System.Object.Equals%2A> Označuje, zda dvě proměnné, které bodu na stejnou instanci.  
  
## <a name="see-also"></a>Viz také  
 [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Složené datové typy](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Řešení potíží s datovými typy](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Struktury a ostatní programovací elementy](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)  
 [Objekty a třídy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
