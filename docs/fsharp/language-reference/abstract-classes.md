---
title: Abstraktní třídy
description: Přečtěte F# si o abstraktních třídách, které ponechávají některé nebo všechny členy neimplementované a nepředstavují společné funkce pro různé typy objektů.
ms.date: 05/16/2016
ms.openlocfilehash: d7fc87178cff7c5c824992c97198b49f87025f00
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082951"
---
# <a name="abstract-classes"></a>Abstraktní třídy

*Abstraktní třídy* jsou třídy, které ponechávají některé nebo všechny členy neimplementované, takže implementace mohou být poskytnuty odvozenými třídami.

## <a name="syntax"></a>Syntaxe

```fsharp
// Abstract class syntax.
[<AbstractClass>]
type [ accessibility-modifier ] abstract-class-name =
[ inherit base-class-or-interface-name ]
[ abstract-member-declarations-and-member-definitions ]

// Abstract member syntax.
abstract member member-name : type-signature
```

## <a name="remarks"></a>Poznámky

V objektově orientovaném programování je abstraktní třída použita jako základní třída hierarchie a představuje společné funkce pro různé typy objektů. Jak naznačuje název "Abstract", abstraktní třídy často neodpovídají přímo na konkrétní entity v doméně problému. Představují ale společné množství různých konkrétních entit.

Abstraktní třídy musí mít `AbstractClass` atribut. Můžou mít implementované a neimplementované členy. Použití termínu *abstract* při použití na třídu je stejné jako v jiných jazycích .NET. použití termínu *abstract* při použití na metody (a vlastnosti) se ale trochu liší F# od použití v jiných jazycích .NET. V F#, je-li metoda označena `abstract` klíčovým slovem, znamená to, že člen má položku, která je známá jako *virtuální slot pro expedici*, ve vnitřní tabulce virtuálních funkcí pro daný typ. Jinými slovy, metoda je virtuální, i když `virtual` se klíčové slovo nepoužívá v F# jazyce. Klíčové slovo `abstract` se používá na virtuálních metodách bez ohledu na to, jestli je metoda implementovaná. Deklarace virtuálního slotu pro odesílání je oddělená od definice metody pro tuto slot pro expedici. Proto F# ekvivalent deklarace virtuální metody a definice v jiném jazyce .NET je kombinací deklarace abstraktní metody i samostatné definice s `default` klíčovým slovem nebo `override` klíčovým slovem. Další informace a příklady naleznete v tématu [metody](./members/methods.md).

Třída je považována za abstraktní pouze v případě, že existují abstraktní metody, které jsou deklarovány, ale nejsou definovány. Proto třídy, které mají abstraktní metody, nejsou nutně abstraktní třídy. Pokud třída neobsahuje nedefinované abstraktní metody, nepoužívejte atribut **AbstractClass** .

V předchozí syntaxi může `public`být *Modifikátor přístupnosti* , `private` nebo `internal`. Další informace najdete v tématu [Access Control](access-control.md).

Stejně jako u jiných typů abstraktní třídy mohou mít základní třídu a jedno nebo více základních rozhraní. Každá základní třída nebo rozhraní se zobrazí na samostatném řádku spolu s `inherit` klíčovým slovem.

Definice typu abstraktní třídy může obsahovat plně definované členy, ale může obsahovat také abstraktní členy. Syntaxe pro abstraktní členy je uvedena samostatně v předchozí syntaxi. V této syntaxi je *podpis typu* člena seznam, který obsahuje typy parametrů v pořadí a návratové typy oddělené `->` `*` tokeny nebo tokeny, které jsou vhodné pro curryfikované a řazené kolekce členů. Syntaxe pro signatury abstraktních typů členů je stejná jako ta, která se používá v souborech signatur a která je znázorněna IntelliSense v editoru Visual Studio Code.

Následující kód ilustruje prvek abstraktní třídy, který má dvě neabstraktní odvozené třídy, čtverc a Circle. Příklad ukazuje, jak používat abstraktní třídy, metody a vlastnosti. V příkladu prvek abstraktní třídy představuje společné prvky konkrétního kruhu a čtverce v konkrétní entitě. Společné funkce všech tvarů (v dvojrozměrném systémovém systému souřadnic) jsou abstraktní do třídy Shape: pozice v mřížce, úhel natočení a vlastnost oblasti a hraničního režimu. Ty mohou být přepsány, s výjimkou pozice, chování jednotlivých tvarů, které nelze změnit.

Metoda rotace může být přepsána jako ve třídě Circle, což je invariantní rotace z důvodu jejího symetrie. Takže ve třídě Circle je metoda otáčení nahrazena metodou, která nedělá nic.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2901.fs)]

**Výstup:**

```console
Perimeter of square with side length 10.000000 is 40.000000
Circumference of circle with radius 5.000000 is 31.415927
Area of Square: 100.000000
Area of Circle: 78.539816
```

## <a name="see-also"></a>Viz také:

- [Třídy](classes.md)
- [Členové](./members/index.md)
- [Metody](./members/methods.md)
- [Vlastnosti](./members/Properties.md)
