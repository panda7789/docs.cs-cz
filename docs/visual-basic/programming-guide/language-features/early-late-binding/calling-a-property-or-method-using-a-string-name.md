---
title: Volání vlastnosti nebo metody pomocí názvu řetězce (Visual Basic)
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
ms.openlocfilehash: 76be426049489bb58e50878822c03fa5cd5cca8e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649224"
---
# <a name="calling-a-property-or-method-using-a-string-name-visual-basic"></a>Volání vlastnosti nebo metody pomocí názvu řetězce (Visual Basic)
Ve většině případů můžete zjistit vlastnosti a metody objektu v době návrhu a napsat kód pro jejich zpracování. Ale v některých případech nemusí víte o vlastnosti a metody objektu předem, nebo chcete může jenom možnost povolení koncový uživatel zadat vlastnosti nebo metody provést v době běhu.  
  
## <a name="callbyname-function"></a>CallByName – funkce  
 Zvažte například klientskou aplikaci, která vyhodnotí výrazy zadané uživatelem pomocí předání operátor komponenty modelu COM. Předpokládejme, že neustále přidáváte nové funkce pro součásti, které vyžadují nové operátory. Při použití standardní objekt přístup techniky, musíte znovu zkompiluje a znovu distribuovat klientskou aplikaci, než by mohl použít novou operátory. Chcete-li předejít, můžete použít `CallByName` funkce k předání nových operátorů jako řetězce, aniž byste museli měnit aplikace.  
  
 `CallByName` Funkce vám umožní používat řetězec zadat vlastnosti nebo metody za běhu. Podpis pro `CallByName` funkce vypadá takto:  
  
 *Výsledek* = `CallByName`(*objekt*, *ProcedureName*, *Typ_volání*, *argumenty*())  
  
 První argument *objekt*, přebírá název objektu, kterou chcete pracovat. *ProcedureName* argument přebírá řetězec, který obsahuje název procedury metody nebo vlastnosti, které má být volána. *Typ_volání* argument trvá konstanta, která představuje typ postup vyvolání: metody (`Microsoft.VisualBasic.CallType.Method`), číst vlastnosti (`Microsoft.VisualBasic.CallType.Get`), nebo nastavte vlastnost (`Microsoft.VisualBasic.CallType.Set`). *Argumenty* argument, který je volitelný a přijímá pole typu `Object` obsahující všechny argumenty k postupu.  
  
 Můžete použít `CallByName` s třídami v aktuálním řešení, ale se nejčastěji používá pro přístup COM – objekty nebo objekty z [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sestavení.  
  
 Předpokládejme, že přidáte odkaz na sestavení obsahující třídu s názvem `MathClass`, která obsahuje novou funkci s názvem `SquareRoot`, jak je znázorněno v následujícím kódu:  
  
 [!code-vb[VbVbalrOOP#53](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_1.vb)]  
  
 Vaše aplikace může používat ovládací prvky text k řízení, která metoda bude volána a jeho argumenty. Například pokud `TextBox1` obsahuje výraz, který se má vyhodnotit, a `TextBox2` je použít k zadání názvu funkce, můžete použít následující kód k vyvolání `SquareRoot` funkce na výrazu v `TextBox1`:  
  
 [!code-vb[VbVbalrOOP#54](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_2.vb)]  
  
 Pokud zadáte "64" v `TextBox1`, "SquareRoot" v `TextBox2`a pak zavolají `CallMath` postup, druhou odmocninu čísla v `TextBox1` vyhodnotí. Vyvolá kód v ukázce `SquareRoot` funkce (což trvá řetězec, který obsahuje výraz, který má být vyhodnocen jako požadovaný argument) a vrátí "8" `TextBox1` (druhou odmocninu 64). Samozřejmě, pokud uživatel zadá neplatný řetězec v `TextBox2`, řetězec obsahuje název vlastnosti místo metodu nebo metodu měli další požadovaný argument, nastane chyba spuštění. Budete muset přidat robustní kód pro ošetření chyb při použití `CallByName` odhadnout tyto nebo jiné chyby.  
  
> [!NOTE]
>  Když `CallByName` funkce můžou být užitečné v některých případech se musí naváží jeho užitečnost proti vliv na výkon – pomocí `CallByName` vyvolat proceduru se nepatrně pomalejší v porovnání pozdní vazbou volání. Pokud jsou volání funkce, která je volána opakovaně, například jako uvnitř smyčku, `CallByName` může mít závažné vliv na výkon.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Interaction.CallByName%2A>  
 [Určení typu objektu](../../../../visual-basic/programming-guide/language-features/early-late-binding/determining-object-type.md)
