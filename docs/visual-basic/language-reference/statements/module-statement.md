---
title: Module – příkaz
ms.date: 07/20/2015
f1_keywords:
- Module
- vb.Module
helpviewer_keywords:
- modules, classes
- modules
- Module statement [Visual Basic]
- modules, declaring
- standard modules
- classes [Visual Basic], vs. modules
- declarations [Visual Basic], modules
ms.assetid: a1243afc-14a5-45df-95d5-51118aeac362
ms.openlocfilehash: 24a27ba41f5ac889f2f2725a2852368a4292a6fb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404448"
---
# <a name="module-statement"></a>Module – příkaz

Deklaruje název modulu a zavádí definici proměnných, vlastností, událostí a procedur, které modul zahrnuje.

## <a name="syntax"></a>Syntaxe

```vb
[ <attributelist> ] [ accessmodifier ]  Module name
    [ statements ]
End Module
```

## <a name="parts"></a>Součásti

`attributelist`  
Nepovinný parametr. Viz [seznam atributů](attribute-list.md).

`accessmodifier`  
Nepovinný parametr. Může to být jedna z následujících:

- [Republik](../modifiers/public.md)

- [Friend](../modifiers/friend.md)

Podívejte [se na úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).

`name`  
Povinná hodnota. Název tohoto modulu Viz [deklarované názvy elementů](../../programming-guide/language-features/declared-elements/declared-element-names.md).

`statements`  
Nepovinný parametr. Příkazy definující proměnné, vlastnosti, události, procedury a vnořené typy tohoto modulu.

`End Module`  
Ukončí `Module` definici.

## <a name="remarks"></a>Poznámky

`Module`Příkaz definuje typ odkazu dostupný v celém svém oboru názvů. *Modul* (někdy označovaný jako *Standardní modul*) je podobný třídě, ale s některými důležitými odlišnostmi. Každý modul obsahuje přesně jednu instanci a není nutné jej vytvářet ani přiřazovat proměnné. Moduly nepodporují dědičnost ani implementují rozhraní. Všimněte si, že modul není *typu* v tom smyslu, že třída nebo struktura je – nelze deklarovat programový prvek tak, aby měl datový typ modulu.

Můžete použít `Module` pouze na úrovni oboru názvů. To znamená, že *kontext deklarace* pro modul musí být zdrojový soubor nebo obor názvů a nemůže být třída, struktura, modul, rozhraní, procedura nebo blok. Nemůžete vnořovat modul v jiném modulu nebo v žádném typu. Další informace najdete v tématu [deklarace kontextů a výchozích úrovní přístupu](declaration-contexts-and-default-access-levels.md).

Modul má stejnou životnost jako váš program. Vzhledem k tomu, že se jedná o všechny členy `Shared` , mají také životní cyklus stejné jako u programu.

Moduly jako výchozí mají přístup [typu Friend](../modifiers/friend.md) . Můžete upravit jejich úrovně přístupu modifikátory přístupu. Další informace najdete v tématu [úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).

Všichni členové modulu jsou implicitně `Shared` .

## <a name="classes-and-modules"></a>Třídy a moduly

Tyto prvky mají hodně podobnosti, ale existují i některé důležité rozdíly.

- **Vede.** Předchozí verze Visual Basic rozpoznávají dva typy modulů: *moduly tříd* (soubory. CLS) a *standardní moduly* (soubory. bas). Aktuální verze volá tyto *třídy* a *moduly*, v uvedeném pořadí.

- **Sdílené členy.** Můžete určit, zda je člen třídy sdíleným členem nebo členem instance.

- **Orientace objektu.** Třídy jsou objektově orientované, ale moduly nejsou. Takže pouze třídy mohou být vytvořeny jako objekty. Další informace naleznete v tématu [objekty a třídy](../../programming-guide/language-features/objects-and-classes/index.md).

## <a name="rules"></a>Pravidla

- **Modifikátory.** Všechny členy modulů jsou implicitně [sdíleny](../modifiers/shared.md). Klíčové slovo nelze použít `Shared` při deklaraci člena a nelze změnit sdílený stav žádného člena.

- **Dědičnost.** Modul nemůže dědit z jiného typu než <xref:System.Object> , ze kterého všechny moduly dědí. Konkrétně jeden modul nemůže dědit z jiného modulu.

  [Příkaz Inherits](inherits-statement.md) nelze použít v definici modulu, ani když zadáte <xref:System.Object> .

- **Výchozí vlastnost.** V modulu nelze definovat žádné výchozí vlastnosti. Další informace najdete v tématu [výchozí](../modifiers/default.md).

## <a name="behavior"></a>Chování

- **Úroveň přístupu.** V rámci modulu můžete deklarovat každého člena s vlastní úrovní přístupu. Členy modulu jsou ve výchozím nastavení [veřejný](../modifiers/public.md) přístup, s výjimkou proměnných a konstant, které jsou ve výchozím nastavení [privátním](../modifiers/private.md) přístupem. Pokud má modul více omezený přístup než jeden z jeho členů, má zadaná úroveň přístupu k modulu přednost.

- **Oboru.** Modul je v rozsahu celého oboru názvů.

  Rozsah každého člena modulu je celý modul. Všimněte si, že všichni členové přecházejí na *povýšení typu*, což způsobí, že jejich obor bude povýšen na obor názvů obsahující modul. Další informace najdete v tématu o [typu propagace](../../programming-guide/language-features/declared-elements/type-promotion.md).

- **Vydal.** V projektu může být více modulů a můžete deklarovat členy se stejným názvem ve dvou nebo více modulech. Pokud je však odkaz z vnějšku tohoto modulu, musíte kvalifikovat jakýkoliv odkaz na takový člen s odpovídajícím názvem modulu. Další informace naleznete v tématu [odkazy na deklarované elementy](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).

## <a name="example"></a>Příklad

[!code-vb[VbVbalrStatements#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#69)]

## <a name="see-also"></a>Viz také

- [Class – příkaz](class-statement.md)
- [Namespace – příkaz](namespace-statement.md)
- [Structure – příkaz](structure-statement.md)
- [Interface – příkaz](interface-statement.md)
- [Property – příkaz](property-statement.md)
- [Propagace typu](../../programming-guide/language-features/declared-elements/type-promotion.md)
