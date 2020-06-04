---
title: Volání vlastnosti nebo metody pomocí názvu řetězce
ms.date: 07/20/2015
helpviewer_keywords:
- passing operators [Visual Basic]
- strings [Visual Basic], passing new operators as
- objects [Visual Basic], setting properties
- setting properties, object properties at run time
- method calls [Visual Basic], strings
- methods [Visual Basic], calling with string names
- calling methods [Visual Basic], string names
- properties [Visual Basic], setting at run time
- CallByName function
ms.assetid: 79a7b8b4-b8c7-4ad8-aca8-12a9a2b32f03
ms.openlocfilehash: 29072479db36f9f8a81ffd7f3f5b10208ebaa984
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410654"
---
# <a name="calling-a-property-or-method-using-a-string-name-visual-basic"></a>Volání vlastnosti nebo metody pomocí názvu řetězce (Visual Basic)
Ve většině případů můžete zjistit vlastnosti a metody objektu v době návrhu a napsat kód, který je zpracovává. V některých případech však nemusíte znát informace o vlastnostech a metodách objektu předem nebo můžete chtít flexibilitu povolit koncovému uživateli, aby v době běhu určili vlastnosti nebo metody spouštění.  
  
## <a name="callbyname-function"></a>CallByName – funkce  
 Vezměte v úvahu například klientskou aplikaci, která vyhodnotí výrazy zadané uživatelem předáním operátoru komponentě COM. Předpokládejme, že neustále přidáváte nové funkce do komponenty, která vyžaduje nové operátory. Použijete-li standardní techniky přístupu k objektům, je nutné znovu zkompilovat a distribuovat klientskou aplikaci předtím, než bude možné použít nové operátory. Aby k tomu nedošlo, můžete `CallByName` funkci použít k předání nových operátorů jako řetězců bez změny aplikace.  
  
 `CallByName`Funkce umožňuje použít řetězec k určení vlastnosti nebo metody v době běhu. Signatura `CallByName` funkce vypadá takto:  
  
 *Result*  =  Výsledek `CallByName` (*Object*, *Procedure*, *CallType*, *argumenty*())  
  
 První argument *objektu*, přebírá název objektu, na kterém chcete pracovat. Argument *procedury* má řetězec, který obsahuje název metody nebo procedury vlastnosti, která má být vyvolána. Argument *CallType* má konstantu, která představuje typ procedury, která se má vyvolat: metoda ( `Microsoft.VisualBasic.CallType.Method` ), vlastnost Read ( `Microsoft.VisualBasic.CallType.Get` ) nebo sadu vlastností ( `Microsoft.VisualBasic.CallType.Set` ). Argument *argumenty* , který je nepovinný, přebírá pole typu `Object` , které obsahuje všechny argumenty procedury.  
  
 Můžete použít `CallByName` s třídami v aktuálním řešení, ale nejčastěji se používá pro přístup k objektům COM nebo objektům z .NET Framework sestavení.  
  
 Předpokládejme, že přidáte odkaz na sestavení, které obsahuje třídu s názvem `MathClass` , která má novou funkci s názvem `SquareRoot` , jak je znázorněno v následujícím kódu:  
  
 [!code-vb[VbVbalrOOP#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#53)]  
  
 Vaše aplikace by mohla používat ovládací prvky textového pole k řízení, která metoda bude volána a její argumenty. Například pokud `TextBox1` obsahuje výraz, který má být vyhodnocen a který `TextBox2` slouží k zadání názvu funkce, můžete použít následující kód k vyvolání `SquareRoot` funkce ve výrazu v `TextBox1` :  
  
 [!code-vb[VbVbalrOOP#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#54)]  
  
 Pokud zadáte "64" v `TextBox1` "SquareRoot" v " `TextBox2` a potom zavoláte `CallMath` proceduru, bude vyhodnocena druhá odmocnina čísla v `TextBox1` . Kód v příkladu vyvolá `SquareRoot` funkci (která přijímá řetězec, který obsahuje výraz, který má být vyhodnocen jako požadovaný argument) a vrátí "8" v (druhá odmocnina `TextBox1` 64). Samozřejmě, pokud uživatel zadá neplatný řetězec v `TextBox2` , pokud řetězec obsahuje název vlastnosti namísto metody, nebo pokud má metoda další požadovaný argument, dojde k chybě za běhu. Je nutné přidat robustní kód pro zpracování chyb, když použijete `CallByName` k předvídání těchto nebo jakýchkoli jiných chyb.  
  
> [!NOTE]
> I když `CallByName` funkce může být užitečná v některých případech, je nutné zvážit její užitečnost proti vlivu na výkon – použití `CallByName` pro vyvolání procedury je mírně pomalejší než volání s pozdní vazbou. Pokud vyvoláte funkci, která je volána opakovaně, například uvnitř smyčky, `CallByName` může mít vážný vliv na výkon.  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Interaction.CallByName%2A>
- [Určení typu objektu](determining-object-type.md)
