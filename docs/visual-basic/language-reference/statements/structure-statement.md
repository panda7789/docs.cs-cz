---
title: Structure – příkaz
ms.date: 05/12/2018
f1_keywords:
- vb.Structure
- Structure
helpviewer_keywords:
- user-defined types [Visual Basic], Structure statement
- compound data types [Visual Basic]
- Structure keyword [Visual Basic]
- Structure statement [Visual Basic]
- UDT (user-defined types)
- types [Visual Basic], user-defined
ms.assetid: 9bd1deea-2a89-4cdc-812c-6dcbb947c391
ms.openlocfilehash: 120f836b9d49c00e9c53af0d1fc832e22c8cbbb8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346461"
---
# <a name="structure-statement"></a>Structure – příkaz

Deklaruje název struktury a zavádí definici proměnných, vlastností, událostí a procedur, které struktura zahrnuje.

## <a name="syntax"></a>Syntaxe

```vb
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Partial ] _
Structure name [ ( Of typelist ) ]
    [ Implements interfacenames ]
    [ datamemberdeclarations ]
    [ methodmemberdeclarations ]
End Structure
```

## <a name="parts"></a>Součásti

|Termín|Definice|
|---|---|
|`attributelist`|Volitelná. Viz [seznam atributů](attribute-list.md).|
|`accessmodifier`|Volitelná. Může být jedna z následujících akcí:<br /><br /> -   [veřejné](../modifiers/public.md)<br />-   [chráněno](../modifiers/protected.md)<br />-   [přítel](../modifiers/friend.md)<br />-   [privátní](../modifiers/private.md)<br />[přítel chráněný](../modifiers/protected-friend.md) - <br/>- [Private Protected](../modifiers/private-protected.md) <br /><br /> Podívejte [se na úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).|
|`Shadows`|Volitelná. Viz [Shadows](../modifiers/shadows.md).|
|`Partial`|Volitelná. Označuje částečnou definici struktury. Zobrazit [částečné](../modifiers/partial.md).|
|`name`|Požadováno. Název této struktury Viz [deklarované názvy elementů](../../programming-guide/language-features/declared-elements/declared-element-names.md).|
|`Of`|Volitelná. Určuje, že se jedná o obecnou strukturu.|
|`typelist`|Povinné, pokud použijete klíčové slovo [of](of-clause.md) . Seznam parametrů typu pro tuto strukturu Viz [seznam typů](type-list.md).|
|`Implements`|Volitelná. Označuje, že tato struktura implementuje členy jednoho nebo více rozhraní. Viz [příkaz Implements](implements-statement.md).|
|`interfacenames`|Vyžaduje se, pokud použijete příkaz `Implements`. Názvy rozhraní, které tato struktura implementuje.|
|`datamemberdeclarations`|Požadováno. Nula nebo více `Const`, `Dim`, `Enum`nebo `Event` příkazy pro deklaraci *datových členů* struktury.|
|`methodmemberdeclarations`|Volitelná. Nula nebo více deklarací `Function`, `Operator`, `Property`nebo `Sub` procedur, které slouží jako *Členové metody* struktury.|
|`End Structure`|Požadováno. Ukončí definici `Structure`.|

## <a name="remarks"></a>Poznámky

Příkaz `Structure` definuje typ složené hodnoty, kterou můžete přizpůsobit. *Struktura* je generalizace uživatelsky definovaného typu (UDT) předchozích verzí Visual Basic. Další informace najdete v tématu [struktury](../../programming-guide/language-features/data-types/structures.md).

Struktury podporují mnoho stejných funkcí jako třídy. Například struktury mohou mít vlastnosti a postupy, mohou implementovat rozhraní a mohou mít parametrizované konstruktory. Existují však významné rozdíly mezi strukturami a třídami v oblastech, jako jsou dědičnost, deklarace a použití. Třídy jsou také typy odkazů a struktury jsou typy hodnot. Další informace naleznete v tématu [struktury a třídy](../../programming-guide/language-features/data-types/structures-and-classes.md).

`Structure` můžete použít jenom na úrovni oboru názvů nebo modulu. To znamená, že *kontext deklarace* struktury musí být zdrojový soubor, obor názvů, třída, struktura, modul nebo rozhraní a nemůže být procedura nebo blok. Další informace najdete v tématu [deklarace kontextů a výchozích úrovní přístupu](declaration-contexts-and-default-access-levels.md).

Struktury se ve výchozím nastavení přistupují k [příteli](../modifiers/friend.md) . Můžete upravit jejich úrovně přístupu modifikátory přístupu. Další informace najdete v tématu [úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).

## <a name="rules"></a>Pravidla

- **Vnoření.** Můžete definovat jednu strukturu v rámci jiné. Vnější struktura se nazývá *obsažená struktura*a vnitřní struktura se nazývá *vnořená struktura*. Nemůžete ale přistupovat k členům vnořené struktury prostřednictvím obsahující struktury. Místo toho je nutné deklarovat proměnnou datového typu vnořené struktury.

- **Deklarace člena** Musíte deklarovat každého člena struktury. Člen struktury nemůže být [chráněný](../modifiers/protected.md) ani `Protected Friend`, protože nic nemůže dědit ze struktury. Samotnou strukturu však lze `Protected` nebo `Protected Friend`.
  
     V rámci struktury můžete deklarovat nula nebo více nesdílených proměnných nebo nesdílených nevlastních událostí. Nemůžete mít jenom konstanty, vlastnosti a postupy, i když některé z nich nejsou sdílené.

- **Operace.** V rámci deklarace nelze inicializovat hodnotu žádného nesdíleného datového členu struktury. Takový datový člen musíte buď inicializovat pomocí parametrizovaného konstruktoru ve struktuře, nebo přiřadit hodnotu členu po vytvoření instance struktury.

- **Dědičnost.** Struktura nemůže dědit z jiného typu než <xref:System.ValueType>, ze kterého všechny struktury dědí. Konkrétně jedna struktura nemůže dědit od druhé.

     [Příkaz Inherits](inherits-statement.md) nelze použít v definici struktury, ani pro určení <xref:System.ValueType>.

- **Provádění.** Pokud struktura používá [příkaz Implements](implements-statement.md), je nutné implementovat každého člena definovaného každým rozhraním, které zadáte v `interfacenames`.

- **Výchozí vlastnost.** Struktura může určovat maximálně jednu vlastnost jako *výchozí vlastnost*pomocí [výchozího](../modifiers/default.md) modifikátoru. Další informace najdete v tématu [výchozí](../modifiers/default.md).

## <a name="behavior"></a>Chování

- **Úroveň přístupu.** V rámci struktury můžete deklarovat každého člena s vlastní úrovní přístupu. Všechny členy struktury jsou ve výchozím nastavení [veřejným](../modifiers/public.md) přístupem. Všimněte si, že pokud má struktura vlastní více úrovní přístupu, automaticky se tím omezí přístup k jejím členům, i když upravíte jejich úrovně přístupu modifikátory přístupu.

- **Oboru.** Struktura je v oboru, který obsahuje obor názvů, třídu, strukturu nebo modul.

     Rozsah každého člena struktury je celá struktura.

- **Platné.** Struktura sama o sobě nemá život. Místo toho má každá instance struktury životnost nezávisle na všech ostatních instancích.

     Doba životnosti instance začíná, když je vytvořena [novou klauzulí operátoru](../operators/new-operator.md) . Končí v případě, že skončí životnost proměnné, která ho obsahuje.

     Nemůžete roztáhnout dobu života instance struktury. Modul nabízí sbližování funkcí statické struktury. Další informace naleznete v tématu [příkaz Module](module-statement.md).

     Členové struktury mají životnost v závislosti na tom, jak a kde jsou deklarovány. Další informace naleznete v části "doba života" v [příkazu třídy](class-statement.md).

- **Vydal.** Kód mimo strukturu musí kvalifikovat název člena s názvem této struktury.

     Pokud kód uvnitř vnořené struktury vytvoří nekvalifikovaný odkaz na prvek programování, Visual Basic vyhledá prvek nejprve ve vnořené struktuře, poté v jeho obsahující struktuře a tak dále k vnějšímu nadřazenému prvku. Další informace naleznete v tématu [odkazy na deklarované elementy](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).

- **Spotřeba paměti.** Stejně jako u všech složených datových typů nemůžete bezpečně vypočítat celkovou spotřebu paměti struktury tím, že přidáváte dohromady jmenovité přidělení úložiště jeho členů. Navíc nemůžete bezpečně předpokládat, že pořadí úložiště v paměti je stejné jako vaše pořadí deklarace. Pokud potřebujete řídit rozložení úložiště struktury, můžete použít atribut <xref:System.Runtime.InteropServices.StructLayoutAttribute> u příkazu `Structure`.

## <a name="example"></a>Příklad

Následující příklad používá příkaz `Structure` k definování sady souvisejících dat pro zaměstnance. Zobrazuje použití `Public`, `Friend`a `Private` členů, aby odrážela citlivost datových položek. Také ukazuje proceduru, vlastnost a členy události.

[!code-vb[VbVbalrStatements#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#57)]

Další informace o použití `Structure`s naleznete v tématu Structure- [Variable](../../programming-guide/language-features/data-types/structure-variables.md).

## <a name="see-also"></a>Viz také:

- [Příkaz Class](class-statement.md)
- [Příkaz Interface](interface-statement.md)
- [Příkaz Module](module-statement.md)
- [Příkaz Dim](dim-statement.md)
- [Příkaz Const](const-statement.md)
- [Příkaz Enum](enum-statement.md)
- [Příkaz Event](event-statement.md)
- [Příkaz Operator](operator-statement.md)
- [Příkaz Property](property-statement.md)
- [Struktury a třídy](../../programming-guide/language-features/data-types/structures-and-classes.md)
