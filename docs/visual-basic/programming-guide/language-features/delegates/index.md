---
title: Delegáti (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
  - 'delegates [Visual Basic]'
  - 'Visual Basic code, delegates'
ms.assetid: 410b60dc-5e60-4ec0-bfae-426755a2ee28
---

# <a name="delegates-visual-basic"></a>Delegáti (Visual Basic)

Delegáti jsou objekty, které odkazují na metody. Se někdy označuje jako *ukazatele na funkci bezpečnosti typů* protože jsou podobní ukazatelům na funkci použít v jiných programovacích jazycích. Ale na rozdíl od ukazatelů na funkce, Visual Basic Delegáti jsou typem odkazu na základě třídy <xref:System.Delegate?displayProperty=nameWithType>. Delegáty lze odkazovat na obě sdílené metody, metody, které může být volána bez konkrétní instanci třídy – a instanci metody.

## <a name="delegates-and-events"></a>Delegáti a události

Delegáti jsou užitečné v situacích, kdy potřebujete prostředník mezi volání procedury a procedura volána. Můžete například objekt, který vyvolává události, které mají být schopny volat jiné obslužné za různých okolností. Objekt vyvolání události nemůže vědět předem, které obslužná rutina události je bohužel zpracování určité události. Visual Basic umožňuje obslužné rutiny událostí dynamicky přidružit s událostmi vytvořením delegáta pro vás při použití `AddHandler` příkazu. V době běhu delegát předává volání obslužné rutiny příslušné události.

I když můžete vytvořit vlastní delegáty, ve většině případů vytvoří delegát jazyka Visual Basic a za vás postará o podrobnosti. Například `Event` příkaz implicitně definuje třídu delegáta s názvem `<EventName>EventHandler` jako vnořené třídy z třídy obsahující `Event` příkaz a se stejnou signaturou jako události. `AddressOf` Příkaz implicitně vytvoří instanci delegáta, který odkazuje na konkrétní postup. Následující dva řádky kódu jsou ekvivalentní. V prvním řádku, uvidíte explicitní vytvoření instance `EventHandler`, s odkazem na metodu `Button1_Click` odeslán jako argument. Druhý řádek je pohodlnější způsob, jak to samé udělá.

[!code-vb[VbVbalrDelegates#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#6)]

Můžete použít zkrácený způsob vytváření delegátů kdekoli kompilátor může určit typ delegáta podle kontextu.

## <a name="declaring-events-that-use-an-existing-delegate-type"></a>Typ delegáta deklarovaného události, které používají existující

V některých případech můžete chtít událost použít existující typ delegáta jako jeho základní delegáta deklarovat. Následující syntaxe ukazuje, jak:

[!code-vb[VbVbalrDelegates#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#7)]

To je užitečné, pokud chcete směrovat více událostí na stejnou obslužnou rutinu.

## <a name="delegate-variables-and-parameters"></a>Delegát proměnné a parametry

Lze použít delegáty pro ostatní, cokoli jiného než událost související s úkoly, jako je například volných vláken nebo s postupy, které je potřeba volat jiné verze funkcí v době běhu.

Například předpokládejme, že budete mít aplikaci klasifikované ad, který obsahuje seznam s názvy aut. Reklamy jsou seřazeny podle názvu, který je obvykle zkontrolujte Auto. Pokud některé auta obsahovat rok car před značku, dojde k potížím, které mohou nastat. Problém je, že funkce integrované řazení pole se seznamem seřadí pouze podle kódy znaků; umístí všechny reklamy spuštění s datem, nejprve, za nímž následuje reklamy, spouští se s bylo možné vytvořit.

To pokud chcete napravit, můžete vytvořit proceduru řazení ve třídě, která používá standardní abecední řazení na většině pole se seznamem, ale je možné přepínat v době běhu k postupu vlastní řazení pro car reklamy. K tomuto účelu předáte postup vlastní řazení na třídu řazení v době běhu, použití delegátů.

## <a name="addressof-and-lambda-expressions"></a>Výrazy Lambda a AddressOf

Každá třída delegáta je definován konstruktor, který je předán specifikace metodu objektu. Argument pro konstruktor delegate musí být odkaz na metodu nebo výraz lambda.

Pokud chcete zadat odkaz na metodu, použijte následující syntaxi:

`AddressOf` [`expression`.]`methodName`

Typ kompilace `expression` musí být názvem třídy nebo rozhraní, které obsahuje metodu se zadaným názvem, jehož předpis shoduje se signaturou třídy delegáta. `methodName` Může být buď sdílené metody nebo metodu instance. `methodName` Není volitelný, i v případě vytvoření delegáta pro výchozí metodu třídy.

Pokud chcete zadat výraz lambda, použijte následující syntaxi:

`Function` ([`parm` Jako `type`, `parm2` jako `type2`;...]) `expression`

Následující příklad ukazuje, jak `AddressOf` a výrazy lambda umožňují zadat odkaz pro delegáta.

[!code-vb[VbVbalrDelegates#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class2.vb#15)]

Signatura funkce musí odpovídat typu delegátu. Další informace o výrazech lambda naleznete v tématu [výrazy Lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md). Další příklady výrazů lambda a `AddressOf` přiřazení na delegáty, naleznete v tématu [volný převod delegáta](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Postupy: Volání metody delegáta](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)|Poskytuje příklad, který ukazuje, jak přidružit metodu delegáta a poté vyvolat tuto metodu prostřednictvím delegáta.|
|[Postupy: Předání procedur jiné proceduře v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)|Ukazuje, jak mají být předány jiné proceduře jeden postup používání delegátů.|
|[Volný převod delegáta](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)|Popisuje, jak můžete přiřadit typu Sub a funkce na delegáty nebo obslužné rutiny i v případě, že jejich podpisy nejsou stejné|
|[Události](../../../../visual-basic/programming-guide/language-features/events/index.md)|Poskytuje přehled o události v jazyce Visual Basic.|
