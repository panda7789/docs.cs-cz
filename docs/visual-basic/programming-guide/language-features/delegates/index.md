---
title: Delegáti
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [Visual Basic]
- Visual Basic code, delegates
ms.assetid: 410b60dc-5e60-4ec0-bfae-426755a2ee28
ms.openlocfilehash: 1f161248fa04f8fab0e5335413e69ca565732f71
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410680"
---
# <a name="delegates-visual-basic"></a>Delegáti (Visual Basic)

Delegáti jsou objekty, které odkazují na metody. Jsou někdy popsány jako *ukazatele funkce bezpečného typu* , protože jsou podobné ukazatelům funkcí použitým v jiných programovacích jazycích. Ale na rozdíl od ukazatelů na funkce Visual Basic Delegáti jsou odkazový typ založený na třídě <xref:System.Delegate?displayProperty=nameWithType> . Delegáti mohou odkazovat jak na sdílené metody – metody, které lze volat bez konkrétní instance třídy – a metody instance.

## <a name="delegates-and-events"></a>Delegáti a události

Delegáti jsou užitečné v situacích, kdy potřebujete prostředník mezi volající procedurou a procedurou, která je volána. Například může být vhodné, aby objekt, který vyvolává události, mohl volat různé obslužné rutiny událostí za různých okolností. Objekt, který vyvolává události, bohužel nemůže znát před časem, který obslužná rutina události zpracovává konkrétní událost. Visual Basic umožňuje dynamicky přidružit obslužné rutiny událostí s událostmi tím, že při použití příkazu vytvoří delegáta pro vás `AddHandler` . V době běhu delegát přesměruje volání příslušné obslužné rutiny události.

I když můžete vytvořit vlastní delegáty, ve většině případů Visual Basic vytvoří delegáta a postará o podrobnosti. Například `Event` příkaz implicitně definuje třídu delegáta s názvem `<EventName>EventHandler` jako vnořenou třídu třídy obsahující `Event` příkaz a se stejnou signaturou jako událost. `AddressOf`Příkaz implicitně vytvoří instanci delegáta, která odkazuje na konkrétní proceduru. Následující dva řádky kódu jsou ekvivalentní. Na prvním řádku se zobrazí explicitní vytvoření instance `EventHandler` s odkazem na metodu `Button1_Click` odeslanou jako argument. Druhým řádkem je pohodlnější způsob, jak to provést.

[!code-vb[VbVbalrDelegates#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#6)]

Můžete použít zkrácený způsob vytváření delegátů kdekoli, kde kompilátor může určit typ delegáta v kontextu.

## <a name="declaring-events-that-use-an-existing-delegate-type"></a>Deklarace událostí, které používají existující typ delegáta

V některých situacích může být vhodné deklarovat událost pro použití existujícího typu delegáta jako svého základního delegáta. Následující syntaxe ukazuje, jak:

[!code-vb[VbVbalrDelegates#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#7)]

To je užitečné, pokud chcete směrovat více událostí do stejné obslužné rutiny.

## <a name="delegate-variables-and-parameters"></a>Proměnné a parametry delegáta

Delegáty můžete použít pro jiné úlohy, které nesouvisí s událostmi, jako je například volné zřetězení nebo s postupy, které potřebují volat různé verze funkcí za běhu.

Předpokládejme například, že máte aplikaci klasifikovanou jako službu AD, která obsahuje seznam s názvy automobilů. Reklamy jsou seřazeny podle názvu, což je obvykle značka auto. Problém, ke kterému může dojít, když některá osobní automobily před sebou zahrnuje rok auta. Problémem je, že vestavěná funkce řazení v poli seznamu seřadí pouze kódy znaků; umístí všechny reklamy počínaje počátečními daty a potom reklamy začínající na.

Chcete-li tento problém vyřešit, můžete vytvořit proceduru řazení ve třídě, která používá standardní abecední řazení ve většině polí seznamu, ale může přepnout v době běhu do vlastního postupu řazení pro inzeráty na automobil. Chcete-li to provést, předejte vlastní proceduru řazení do třídy řazení za běhu pomocí delegátů.

## <a name="addressof-and-lambda-expressions"></a>AddressOf a lambda výrazy

Každá třída delegáta definuje konstruktor, který je předán specifikaci metody objektu. Argument konstruktoru delegáta musí být odkazem na metodu nebo výraz lambda.

Chcete-li zadat odkaz na metodu, použijte následující syntaxi:

`AddressOf` [`expression`.]`methodName`

Typ doby kompilace `expression` musí být název třídy nebo rozhraní, které obsahuje metodu zadaného názvu, jejíž signatura odpovídá signatuře třídy delegáta. `methodName`Může se jednat o sdílenou metodu nebo metodu instance. `methodName`Není volitelná, i když vytvoříte delegáta pro výchozí metodu třídy.

Chcete-li zadat výraz lambda, použijte následující syntaxi:

`Function`([ `parm` As `type` , `parm2` as `type2` ,...])`expression`

Následující příklad ukazuje jak `AddressOf` a lambda výrazy, které slouží k určení odkazu pro delegáta.

[!code-vb[VbVbalrDelegates#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class2.vb#15)]

Signatura funkce musí odpovídat typu delegáta. Další informace o výrazech lambda naleznete v tématu [lambda Expressions](../procedures/lambda-expressions.md). Další příklady výrazů lambda a `AddressOf` přiřazení delegátům naleznete v tématu [odlehčený převod delegáta](relaxed-delegate-conversion.md).

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Postupy: Volání metody delegáta](how-to-invoke-a-delegate-method.md)|Poskytuje příklad, který ukazuje, jak přidružit metodu k delegátovi a následně tuto metodu vyvolat prostřednictvím delegáta.|
|[Postupy: Předání procedur jiné proceduře v jazyce Visual Basic](how-to-pass-procedures-to-another-procedure.md)|Ukazuje, jak použít delegáty k předání jednoho postupu jinému postupu.|
|[Volný převod delegáta](relaxed-delegate-conversion.md)|Popisuje, jak můžete přiřadit vlastníky a funkce delegátům nebo obslužným rutinám, i když jejich signatury nejsou stejné.|
|[Události](../events/index.md)|Poskytuje přehled událostí v Visual Basic.|
