---
title: Delegáti (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- delegates [Visual Basic]
- Visual Basic code, delegates
ms.assetid: 410b60dc-5e60-4ec0-bfae-426755a2ee28
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fe21d8c0dcefaea35d9f96cd2ecbff92a1c83d36
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="delegates-visual-basic"></a>Delegáti (Visual Basic)
Delegáti jsou objekty, které odkazují na metody. V některých případech jsou popsány jako *ukazatelů na funkce zajišťující bezpečnost typů* vzhledem k tomu, že jsou podobná ukazatelů na funkce používán jinými programovací jazyky. Ale na rozdíl od ukazatelů na funkce [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Delegáti jsou typu odkazu na základě třídy <xref:System.Delegate?displayProperty=nameWithType>. Delegáti odkazovat oba sdílené metody – metody, které může být volána bez konkrétní instanci třídy – a instanci metody.  
  
## <a name="delegates-and-events"></a>Delegáti a události  
 Delegáti jsou užitečné v situacích, kde je nutné zprostředkovatel mezi volání procedury a postup volána. Například můžete objekt, který vyvolává události, abyste mohli volání obslužné rutiny různých událostí za různých okolností. Bohužel objekt vyvolání události nemůže vědět předem, které obslužná rutina události zpracovává konkrétní události. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]umožňuje dynamicky přidružení obslužné rutiny s událostmi vytvořením delegáta pro vás při použití `AddHandler` příkaz. V době běhu předává delegát volání obslužné rutiny příslušné události.  
  
 I když můžete vytvořit vlastní delegáty ve většině případů [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] vytvoří delegáta a podrobnosti postará za vás. Například `Event` příkaz implicitně definuje delegát třídy s názvem `<EventName>EventHandler` jako vnořenou třídu třída obsahující `Event` příkaz a se stejným podpisem jako událost. `AddressOf` Implicitně vytvoří instanci delegáta, který odkazuje na zvláštní postup. Následující dva řádky kódu jsou ekvivalentní. V prvním řádku, uvidíte explicitní vytvoření instance `Eventhandler`, s odkazem na metoda `Button1_Click` odeslán jako argumentem. Druhý řádek je pohodlnější způsob, jak stejnou věc udělat.  
  
 [!code-vb[VbVbalrDelegates#6](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegates_1.vb)]  
  
 Můžete použít zkrácený způsob vytváření delegátů kdekoli kompilátor můžete určit typ delegáta podle kontextu.  
  
## <a name="declaring-events-that-use-an-existing-delegate-type"></a>Deklarující události, které použijte existující typ delegáta  
 V některých situacích můžete událost chcete použít existující typ delegáta jako jeho základní delegáta deklarovat. Následující syntaxe ukazuje, jak:  
  
 [!code-vb[VbVbalrDelegates#7](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegates_2.vb)]  
  
 To je užitečné, pokud chcete směrovat více událostí do stejné obslužné rutiny.  
  
## <a name="delegate-variables-and-parameters"></a>Parametry a proměnné delegáta  
 Delegáti můžete použít pro ostatní, událostmi související úlohy, jako je například volných vláken nebo s postupy, které je třeba volat různé verze funkcí v době běhu.  
  
 Předpokládejme například, že máte aplikaci klasifikované ad, která obsahuje seznam s názvy automobilů. Reklamy jsou seřazené podle název, který je obvykle značku Auto. Pokud některé aut obsahovat rok car před značku dojde k potížím, které může být vystaven. Problém je, že funkce integrované řazení pole se seznamem seřadí pouze podle kódy znaků; umístí všechny reklamy nejprve spustit s daty, za nímž následuje reklamy počínaje značku.  
  
 Problém odstraníte tak, můžete vytvořit proceduru řazení ve třídě, která používá standardní abecedním řazení na seznamy většina, ale je moci v době běhu na vlastní řazení postup car reklamy. K tomu, předáte vlastní řazení postup k třídě řazení v době běhu použití delegátů.  
  
## <a name="addressof-and-lambda-expressions"></a>AddressOf a výrazy Lambda  
 Každá třída delegáta definuje konstruktor, který je předán specifikace metodu objektu. Argument pro konstruktor delegáta musí být odkaz na metodu nebo výrazu lambda.  
  
 Pokud chcete zadat odkaz na metodu, použijte následující syntaxi:  
  
 `AddressOf` [`expression`.]`methodName`  
  
 Typ kompilaci `expression` musí být název třídy nebo rozhraní, které obsahuje metodu pro zadaný název, jejichž podpis odpovídá podpis delegát třídy. `methodName` Může být buď sdílené metody nebo metodu instance. `methodName` Je povinný, i v případě, že vytvoříte delegáta pro metodu výchozí třídy.  
  
 Pokud chcete zadat výrazu lambda, použijte následující syntaxi:  
  
 `Function`([`parm` Jako `type`, `parm2` jako `type2`,...])`expression`  
  
 Následující příklad ukazuje, jak `AddressOf` a slouží k zadání odkazu pro delegáta výrazy lambda.  
  
 [!code-vb[VbVbalrDelegates#15](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegates_3.vb)]  
  
 Podpis funkce musí odpovídat typu delegáta. Další informace o výrazy lambda najdete v tématu [výrazy Lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md). Další příklady výrazů lambda a `AddressOf` přiřazení delegáti, najdete v části [volný převod delegáta](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Postupy: volání metody delegáta](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)|Poskytuje příklad, který ukazuje, jak přidružit metody delegáta a pak volání této metody prostřednictvím delegáta.|  
|[Postupy: předání procedur jiné proceduře v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)|Demonstruje způsob používání delegátů předat jeden procedur jiné proceduře.|  
|[Volný převod delegáta](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)|Popisuje, jak můžete přiřadit předplatných a funkce na delegáty nebo obslužné rutiny i v případě, že jejich podpisy nejsou identické|  
|[Události](../../../../visual-basic/programming-guide/language-features/events/index.md)|Obsahuje přehled událostí v jazyce Visual Basic.|
