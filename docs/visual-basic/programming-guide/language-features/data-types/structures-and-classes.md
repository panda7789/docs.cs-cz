---
title: Struktury a třídy
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], vs. structures
- structures [Visual Basic]
- classes [Visual Basic]
- structures [Visual Basic], compared to classes
- structures [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: a221e74a-ffcf-4bdc-a0f6-a088a9bf26cc
ms.openlocfilehash: d252d9216a9b825ad0663a5779d7ce7f81fa9011
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393569"
---
# <a name="structures-and-classes-visual-basic"></a>Struktury a třídy (Visual Basic)
Visual Basic sjednocuje syntaxi pro struktury a třídy s výsledkem, že obě entity podporují většinu stejných funkcí. Existují však i důležité rozdíly mezi strukturami a třídami.  
  
 Třídy mají výhodu typů odkazů – předání odkazu je efektivnější než předání proměnné struktury se všemi daty. Na druhé straně struktury nevyžadují přidělení paměti v globální haldě.  
  
 Vzhledem k tomu, že nemůžete dědit ze struktury, měly by být struktury používány pouze pro objekty, které není nutné rozšiřovat. Použijte struktury, pokud objekt, který chcete vytvořit, má malou velikost instance a vezme v úvahu výkonnostní charakteristiky tříd versus struktur.  
  
## <a name="similarities"></a>Podobnosti  
 Struktury a třídy jsou podobné v následujících ohledech:  
  
- Oba jsou typy *kontejnerů* , což znamená, že obsahují jiné typy jako členy.  
  
- Oba mají členy, které mohou zahrnovat konstruktory, metody, vlastnosti, pole, konstanty, výčty, události a obslužné rutiny událostí. Nepleťte si však tyto členy s deklarovanými *prvky* struktury.  
  
- Členové obou můžou mít individuální úrovně přístupu. Například jeden člen může být deklarován `Public` a druhý `Private` .  
  
- Oba můžou implementovat rozhraní.  
  
- Oba můžou mít sdílené konstruktory s parametry nebo bez.  
  
- Oba můžou vystavit *výchozí vlastnost*za předpokladu, že vlastnost přebírá aspoň jeden parametr.  
  
- Obě můžou deklarovat a vyvolat události a obě můžou deklarovat delegáty.  
  
## <a name="differences"></a>Rozdíly  
 Struktury a třídy se liší v následujících údajích:  
  
- Struktury jsou *typy hodnot*; třídy jsou *odkazové typy*. Proměnná typu struktury obsahuje data struktury místo toho, aby obsahovala odkaz na data jako typ třídy.  
  
- Struktury používají alokaci zásobníku; třídy používají přidělení haldy.  
  
- Všechny prvky struktury jsou `Public` ve výchozím nastavení. proměnné třídy a konstanty jsou `Private` ve výchozím nastavení, zatímco jiné členy třídy jsou `Public` ve výchozím nastavení. Toto chování pro členy třídy zajišťuje kompatibilitu s výchozím systémem Visual Basic 6,0.  
  
- Struktura musí mít alespoň jednu nesdílenou proměnnou nebo nevlastní nesdílenou, nevlastní prvek události; Třída může být zcela prázdná.  
  
- Prvky struktury nelze deklarovat jako `Protected` ; Členové třídy mohou.  
  
- Procedura struktury může zpracovávat události pouze v případě, že se jedná o [sdílenou](../../../language-reference/modifiers/shared.md) `Sub` proceduru, a to pouze pomocí [příkazu AddHandler](../../../language-reference/statements/addhandler-statement.md); jakákoli procedura třídy může zpracovávat události pomocí klíčového slova [Handles](../../../language-reference/statements/handles-clause.md) nebo `AddHandler` příkazu. Další informace najdete v tématu [události](../events/index.md).  
  
- Deklarace proměnných struktury nemůžou určovat Inicializátory ani počáteční velikosti polí. deklarace proměnných třídy mohou.  
  
- Struktury implicitně dědí z <xref:System.ValueType?displayProperty=nameWithType> třídy a nemůžou dědit z žádného jiného typu; třídy mohou dědit z jakékoliv třídy nebo třídy kromě <xref:System.ValueType?displayProperty=nameWithType> .  
  
- Struktury nejsou dědičné; třídy jsou.  
  
- Struktury nejsou nikdy ukončeny, takže modul CLR (Common Language Runtime) nikdy nevolá <xref:System.Object.Finalize%2A> metodu v žádné struktuře. třídy jsou ukončeny systémem uvolňování paměti (GC), který volá <xref:System.Object.Finalize%2A> třídu, když zjistí, že neexistují žádné aktivní odkazy.  
  
- Struktura nevyžaduje konstruktor. Třída dělá.  
  
- Struktury mohou mít nesdílené konstruktory pouze v případě, že převezmou parametry; třídy mohou mít s parametry nebo bez nich.  
  
 Každá struktura má implicitní veřejný konstruktor bez parametrů. Tento konstruktor inicializuje všechny prvky dat struktury na jejich výchozí hodnoty. Toto chování nelze předefinovat.  
  
## <a name="instances-and-variables"></a>Instance a proměnné  
 Vzhledem k tomu, že struktury jsou typy hodnot, každá proměnná struktury je trvale svázána s instancí jednotlivé struktury. Ale třídy jsou odkazové typy a proměnná objektu může odkazovat na různé instance třídy v různých časech. Toto rozlišení má vliv na využití struktur a tříd následujícími způsoby:  
  
- **Operace.** Proměnná struktury implicitně obsahuje inicializaci elementů pomocí konstruktoru bez parametrů struktury. Proto `Dim s As struct1` je ekvivalentem `Dim s As struct1 = New struct1()` .  
  
- **Přiřazují se proměnné.** Když přiřadíte jednu proměnnou struktury k druhé nebo předáte instanci struktury do argumentu procedury, aktuální hodnoty všech prvků proměnné se zkopírují do nové struktury. Když přiřadíte jednu proměnnou objektu k druhé nebo předáte proměnnou objektu proceduře, je zkopírován pouze odkazový ukazatel.  
  
- **Nepřiřazuje se nic.** Proměnné struktury můžete přiřadit hodnotu [Nothing](../../../language-reference/nothing.md) , ale instance bude nadále přidružena k proměnné. Můžete i nadále volat své metody a přistupovat k jejím datovým prvkům, i když jsou proměnné prvky opětovně inicializovány přiřazením.  
  
     Naproti tomu, pokud nastavíte proměnnou objektu na `Nothing` , oddělíte ji z jakékoli instance třídy a nebudete mít přístup k žádným členům přes proměnnou, dokud k ní nepřiřadíte jinou instanci.  
  
- **Více instancí.** K objektové proměnné může být přiřazena jiná instance třídy v různých časech a několik proměnných objektu může ve stejnou dobu odkazovat na stejnou instanci třídy. Změny, které provedete v hodnotách členů třídy, ovlivňují tyto členy při zpřístupnění prostřednictvím jiné proměnné odkazující na stejnou instanci.  
  
     Prvky struktury jsou však izolované v rámci své vlastní instance. Změny jejich hodnot se neprojeví v žádné jiné proměnné struktury, ani v jiných instancích stejné `Structure` deklarace.  
  
- **Porovnávání.** Testování rovnosti dvou struktur musí být provedeno pomocí testu elementu po prvku. Dvě objektové proměnné lze porovnat pomocí <xref:System.Object.Equals%2A> metody. <xref:System.Object.Equals%2A>Určuje, zda dvě proměnné odkazují na stejnou instanci.  
  
## <a name="see-also"></a>Viz také

- [Datové typy](index.md)
- [Složené datové typy](composite-data-types.md)
- [Typy hodnot a typy odkazu](value-types-and-reference-types.md)
- [Struktury](structures.md)
- [Řešení potíží s datovými typy](troubleshooting-data-types.md)
- [Struktury a ostatní programovací elementy](structures-and-other-programming-elements.md)
- [Objekty a třídy](../objects-and-classes/index.md)
