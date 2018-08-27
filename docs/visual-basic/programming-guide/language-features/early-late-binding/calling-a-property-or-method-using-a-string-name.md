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
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2018
ms.locfileid: "42911643"
---
# <a name="calling-a-property-or-method-using-a-string-name-visual-basic"></a>Volání vlastnosti nebo metody pomocí názvu řetězce (Visual Basic)
Ve většině případů můžete zjistit vlastnosti a metody objektu v době návrhu a napsat kód pro jejich zpracování. Ale v některých případech nemusí o vlastnostech a metodách objektu předem znáte, nebo budete chtít právě flexibilitu povolení koncového uživatele k zadání vlastností nebo provádění metod v době běhu.  
  
## <a name="callbyname-function"></a>CallByName – funkce  
 Zvažte například klientská aplikace, která vyhodnotí výrazy zadané uživatelem předáním operátor komponenty modelu COM. Předpokládejme, že jsou neustále přidává nové funkce do komponenty, které vyžadují nové operátory. Při použití techniky přístupu k objektu standardní musíte znovu zkompilovat a znovu distribuovat klientská aplikace, než může využívat nových operátorů. Abyste tomu předešli, můžete použít `CallByName` funkce k předání nových operátorů jako řetězce, beze změny aplikace.  
  
 `CallByName` Funkce umožňuje používat řetězce k určení vlastnosti nebo metody v době běhu. Podpis pro `CallByName` funkce vypadá takto:  
  
 *Výsledek* = `CallByName`(*objekt*, *Název_procedury*, *CallType*, *argumenty*())  
  
 První argument *objekt*, přebírá název objektu, který má k provedení akce. *Název_procedury* přebírá argument řetězec obsahující název metody nebo vlastnosti postup má být volána. *CallType* konstantu, která představuje typ postup, který má být vyvolán přebírá argument: metody (`Microsoft.VisualBasic.CallType.Method`), číst vlastnosti (`Microsoft.VisualBasic.CallType.Get`), nebo určitá vlastnost nastavila (`Microsoft.VisualBasic.CallType.Set`). *Argumenty* přebírá argument, který je volitelný, pole typu `Object` , která obsahuje všechny argumenty do procedury.  
  
 Můžete použít `CallByName` s třídami v aktuálním řešení, ale se nejčastěji používá pro přístup k objektům modelu COM nebo objekty z [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sestavení.  
  
 Předpokládejme, že přidáte odkaz na sestavení, které obsahuje třídu s názvem `MathClass`, který má novou funkci s názvem `SquareRoot`, jak je znázorněno v následujícím kódu:  
  
 [!code-vb[VbVbalrOOP#53](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_1.vb)]  
  
 Vaše aplikace může používat ovládací prvky textové pole ovládacího prvku, která metoda bude volána a argumentů. Například pokud `TextBox1` obsahuje výraz, který se má vyhodnotit, a `TextBox2` je použít k zadání názvu funkce, můžete použít následující kód k vyvolání `SquareRoot` funkci na výrazu v `TextBox1`:  
  
 [!code-vb[VbVbalrOOP#54](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_2.vb)]  
  
 Pokud zadáte "64" do `TextBox1`, "SquareRoot" v `TextBox2`a následně zavolat `CallMath` procedury, druhou odmocninu čísla v `TextBox1` vyhodnocena. Vyvolá kódem v příkladu `SquareRoot` funkci (desetinný řetězec, který obsahuje výraz, který má být vyhodnocen jako povinný argument) a vrátí "8" v `TextBox1` (odmocninu 64). Samozřejmě, pokud uživatel zadá neplatný řetězec v `TextBox2`, pokud řetězec obsahuje název vlastnosti namísto metody nebo pokud metoda další požadovaný argument, dojde k chybě za běhu. Je třeba přidat robustní kód pro zpracování chyb při použití `CallByName` předvídat těchto nebo jiné chyby.  
  
> [!NOTE]
>  Zatímco `CallByName` funkce může být užitečné v některých případech, třeba zvažte jeho užitečnost proti vliv na výkon – pomocí `CallByName` k vyvolání procedury je o něco pomalejší než volání s pozdní vazbou. Pokud jsou volání funkce, která se nazývá opakovaně, například jako uvnitř smyčky, `CallByName` může mít vážné vliv na výkon.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Interaction.CallByName%2A>  
 [Určení typu objektu](../../../../visual-basic/programming-guide/language-features/early-late-binding/determining-object-type.md)
