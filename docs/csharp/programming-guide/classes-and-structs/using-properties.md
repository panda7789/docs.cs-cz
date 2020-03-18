---
title: Použití průvodce vlastnostmi – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- set accessor [C#]
- get accessor [C#]
- properties [C#], about properties
ms.assetid: f7f67b05-0983-4cdb-96af-1855d24c967c
ms.openlocfilehash: d873f626b660bb6bd94710add4543e21e11823d6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77452016"
---
# <a name="using-properties-c-programming-guide"></a>Použití vlastností (Průvodce programováním v C#)

Vlastnosti kombinují aspekty polí i metod. Uživateli objektu se vlastnost jeví jako pole, přístup k vlastnosti vyžaduje stejnou syntaxi. Pro implementátor třídy je vlastnost jeden nebo dva bloky kódu, představující [přístupový](../../language-reference/keywords/get.md) objekt get a/nebo [přistupující objekt set.](../../language-reference/keywords/set.md) Blok kódu pro `get` přistupující objekt je proveden při čtení vlastnosti; blok kódu pro `set` přistupující objekt je proveden, když je vlastnost přiřazena nová hodnota. Vlastnost bez `set` přistupujícího objektu je považována za jen pro čtení. Vlastnost bez `get` přistupujícího objektu je považována za pouze pro zápis. Vlastnost, která má oba přistupující objekty je čtení a zápis.

Na rozdíl od polí nejsou vlastnosti klasifikovány jako proměnné. Proto nelze předat vlastnost jako [ref](../../language-reference/keywords/ref.md) nebo [out](../../language-reference/keywords/out-parameter-modifier.md) parametr.

Vlastnosti mají mnoho použití: mohou ověřit data před povolením změny; mohou transparentně vystavit data ve třídě, kde jsou tato data skutečně načtena z jiného zdroje, například z databáze; mohou provést akci při změně dat, například vyvolání události nebo změně hodnoty jiných polí.

Vlastnosti jsou deklarovány v bloku třídy zadáním úrovně přístupu pole, následovaný matný typ vlastnosti, následovaný názvem `get`vlastnosti a následuje `set` blok kódu, který deklaruje -accessor a/nebo přistupujícího objektu. Například:

[!code-csharp[csProgGuideProperties#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#7)]

V tomto `Month` příkladu je deklarována jako vlastnost tak, aby `set` přistupující objekt můžete ujistěte se, že `Month` hodnota je nastavena mezi 1 a 12. Vlastnost `Month` používá soukromé pole ke sledování skutečné hodnoty. Skutečné umístění dat vlastnosti se často označuje jako "záložní úložiště vlastnosti". Je běžné, že vlastnosti používají privátní pole jako záložní úložiště. Pole je označeno jako soukromé, aby bylo zajištěno, že může být změněno pouze voláním do služby. Další informace o omezeních veřejného a soukromého přístupu naleznete [v tématu Modifikátory přístupu](./access-modifiers.md).

Automaticky implementované vlastnosti poskytují zjednodušenou syntaxi pro jednoduché deklarace vlastností. Další informace naleznete [v tématu Auto-Implemented Properties](auto-implemented-properties.md).

## <a name="the-get-accessor"></a>The get Accessor

Tělo přistupujícího `get` subjektu se podobá metodě. Musí vrátit hodnotu typu vlastnosti. Provádění přistupujícího `get` pole je ekvivalentní čtení hodnoty pole. Například při vrácení soukromé proměnné z `get` přistupujícího objektů a optimalizace `get` jsou povoleny, volání přístupového zařízení metoda je vložena kompilátoru, takže neexistuje žádná režie volání metody. Metoda virtuálního `get` přistupujícího objektu však nemůže být vložena, protože kompilátor neví v době kompilace, která metoda může být skutečně volána za běhu. Následuje přistupující `get` pole, které vrací `_name`hodnotu soukromého pole :

[!code-csharp[csProgGuideProperties#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#8)]

Při odkazování na vlastnost, s výjimkou jako `get` cíl přiřazení, přistupující objekt je vyvolána ke čtení hodnoty vlastnosti. Například:

[!code-csharp[csProgGuideProperties#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#9)]

Přistupující `get` objekt musí končit [příkazem return](../../language-reference/keywords/return.md) nebo [throw](../../language-reference/keywords/throw.md) a ovládací prvek nemůže odtékat z těla přistupujícího objektu.

Je špatný styl programování změnit stav objektu pomocí `get` přistupujícího objektu. Například následující přistupující objekt vytváří vedlejší účinek změny stavu `_number` objektu při každém přístupu k poli.

[!code-csharp[csProgGuideProperties#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#10)]

Přistupující `get` ho lze použít k vrácení hodnoty pole nebo k jeho výpočtu a vrácení. Například:

[!code-csharp[csProgGuideProperties#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#11)]

Pokud v předchozím segmentu kódu nepřiřadíte `Name` vlastnosti hodnotu, `NA`vrátí hodnotu .

## <a name="the-set-accessor"></a>Přistupující člen souboru

Přistupující `set` odkaz se podobá metodě, jejíž návratový typ je [void](../../language-reference/builtin-types/void.md). Používá implicitní parametr `value`s názvem , jehož typ je typ vlastnosti. V následujícím příkladu `set` je do vlastnosti `Name` přidán přistupující objekt:

[!code-csharp[csProgGuideProperties#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#12)]

Při přiřazení hodnoty vlastnosti `set` je vyvolán apřistit u objektu, který poskytuje novou hodnotu. Například:

[!code-csharp[csProgGuideProperties#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#13)]

Je chyba použít implicitní název `value`parametru , pro deklaraci místní proměnné v přistupujícím objektu. `set`

## <a name="remarks"></a>Poznámky

Vlastnosti lze `public`označit `private` `protected`jako `internal` `protected internal` , `private protected`, , nebo . Tyto modifikátory přístupu definují, jak mohou uživatelé třídy přistupovat k vlastnosti. A `get` `set` přístupové objekty pro stejnou vlastnost mohou mít různé modifikátory přístupu. Například `get` může být `public` povolit přístup jen pro čtení z `set` mimo `private` `protected`typ a může být nebo . Další informace naleznete [v tématu Access Modifiers](./access-modifiers.md).

Vlastnost může být deklarována `static` jako statická vlastnost pomocí klíčového slova. Tím se vlastnost k dispozici volajícím kdykoli, i v případě, že neexistuje žádná instance třídy. Další informace naleznete [v tématu Statické třídy a statické členy třídy](./static-classes-and-static-class-members.md).

Vlastnost může být označena jako virtuální vlastnost pomocí [virtuálního](../../language-reference/keywords/virtual.md) klíčového slova. To umožňuje odvozené třídy přepsat chování vlastností pomocí klíčového slova [přepsat.](../../language-reference/keywords/override.md) Další informace o těchto možnostech naleznete v [tématu Dědičnost](inheritance.md).

Vlastnost přepsání virtuální vlastnosti může být také [zapečetěna](../../language-reference/keywords/sealed.md), určující, že pro odvozené třídy již není virtuální. Nakonec vlastnost může být deklarována [abstraktní](../../language-reference/keywords/abstract.md). To znamená, že neexistuje žádná implementace ve třídě a odvozené třídy musí psát vlastní implementaci. Další informace o těchto možnostech naleznete [v tématu Abstract and Sealed Classes and Class Members](abstract-and-sealed-classes-and-class-members.md).
  
> [!NOTE]
> Je chyba použít [virtuální](../../language-reference/keywords/virtual.md), [abstraktní](../../language-reference/keywords/abstract.md)nebo [přepsat](../../language-reference/keywords/override.md) modifikátor na přistupující objekt [statické](../../language-reference/keywords/static.md) vlastnosti.

## <a name="example"></a>Příklad

Tento příklad ukazuje vlastnosti instance, statické a jen pro čtení. Přijme jméno zaměstnance z klávesnice, přírůstky `NumberOfEmployees` o 1 a zobrazí jméno a číslo zaměstnance.

[!code-csharp[csProgGuideProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#2)]

## <a name="example"></a>Příklad

Tento příklad ukazuje, jak získat přístup k vlastnosti v základní třídě, která je skryta jinou vlastností, která má stejný název v odvozené třídě:

[!code-csharp[csProgGuideProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#3)]

Následující body jsou důležité v předchozím příkladu:

- Vlastnost `Name` v odvozené třídě skryje vlastnost `Name` v základní třídě. V takovém případě `new` modifikátor se používá v deklaraci vlastnosti v odvozené třídě:

     [!code-csharp[csProgGuideProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#4)]  

- Přetypované přetypádky `(Employee)` se používají pro přístup ke skryté vlastnosti v základní třídě:

     [!code-csharp[csProgGuideProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#5)]

     Další informace o skrytí členů naleznete v [novém modifikátoru](../../language-reference/keywords/new-modifier.md).

## <a name="example"></a>Příklad

V tomto příkladu `Cube` dvě `Square`třídy a `Shape`, implementovat abstraktní `Area` třídy , a přepsat jeho abstraktní vlastnost. Všimněte si použití modifikátoru [přepsání](../../language-reference/keywords/override.md) vlastností. Program přijme stranu jako vstup a vypočítá oblasti pro čtverec a krychli. Také přijímá oblast jako vstup a vypočítá odpovídající stranu pro čtverec a krychli.

[!code-csharp[csProgGuideProperties#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#6)]

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Vlastnosti](properties.md)
- [Vlastnosti rozhraní](interface-properties.md)
- [Automaticky implementované vlastnosti](auto-implemented-properties.md)
