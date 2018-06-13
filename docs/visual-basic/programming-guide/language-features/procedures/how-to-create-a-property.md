---
title: 'Postupy: Vytvoření vlastnosti (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, properties
- properties [Visual Basic]
ms.assetid: 4d229712-6be8-4c5c-bac5-06995ce9185a
ms.openlocfilehash: 6e3faed9880b6417f17ab8fe84bc5162e803c437
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656240"
---
# <a name="how-to-create-a-property-visual-basic"></a>Postupy: Vytvoření vlastnosti (Visual Basic)
Uzavřete definici vlastnosti mezi `Property` příkaz a `End Property` příkaz. V rámci této definici definujete `Get` postupu `Set` postup nebo obojí. Všechny vlastnosti kódu je v rámci těchto postupů.  
  
 `Get` Postup načte hodnotu vlastnosti a `Set` postup ukládá hodnotu. Pokud chcete vlastnost, která má mít přístup pro čtení a zápis, je nutné zadat oba procesy. Pro vlastnost jen pro čtení, můžete definovat jenom `Get`, a pro vlastnost jen pro zápis, můžete definovat jenom `Set`.  
  
### <a name="to-create-a-property"></a>K vytvoření vlastnosti  
  
1.  Mimo vlastnost nebo postup, použijte [Property – příkaz](../../../../visual-basic/language-reference/statements/property-statement.md), za nímž následují `End Property` příkaz.  
  
2.  Pokud vlastnost přijímá parametry, postupujte podle kroků `Property` – klíčové slovo s názvem postup, pak se seznam parametrů v závorkách.  
  
3.  Postupujte podle závorkách s `As` klauzule zadat datový typ hodnoty vlastnosti. Musíte zadat typ dat i pro vlastnost jen pro zápis.  
  
4.  Přidat `Get` a `Set` postupy, podle potřeby. Najdete v následujících pokynů.  
  
### <a name="to-create-a-get-procedure-that-retrieves-a-property-value"></a>Chcete-li vytvořit Get procedury, která načte hodnotu vlastnosti  
  
1.  Mezi `Property` a `End Property` příkazy, zápisu [získat příkaz](../../../../visual-basic/language-reference/statements/get-statement.md), za nímž následují `End Get` příkaz. Není nutné definovat všechny parametry `Get` postupu.  
  
2.  Umístěte příkazy kód pro načtení vlastnosti na hodnotu mezi `Get` a `End Get` příkazy. Tento kód mohou zahrnovat jiné výpočty a manipulace dat kromě generování a vrací hodnotu vlastnosti.  
  
3.  Použití `Return` příkaz vrátit hodnotu vlastnosti volání kódu.  
  
 Musíte napsat `Get` postup pro vlastnost pro čtení a zápis a pro vlastnost jen pro čtení. Nesmí definovat `Get` postup pro vlastnost jen pro zápis.  
  
### <a name="to-create-a-set-procedure-that-writes-a-propertys-value"></a>K vytvoření procedury Set, vlastnosti na hodnotu zapíše  
  
1.  Mezi `Property` a `End Property` příkazy, zápisu [příkaz Set](../../../../visual-basic/language-reference/statements/set-statement.md), za nímž následují `End Set` příkaz.  
  
2.  V `Set` prohlášení, postupujte podle `Set` – klíčové slovo s seznam parametrů v závorkách. Tento seznam parametr musí obsahovat alespoň hodnotu parametru pro hodnotu předaná volající kód. Výchozí název pro tento parametr hodnotu je `Value`, ale podle potřeby můžete použít jiný název. Parametr musí mít stejný datový typ. jako samotné vlastnosti.  
  
3.  Umístěte příkazy kód pro ukládání hodnot ve vlastnosti mezi `Set` a `End Set` příkazy. Tento kód mohou zahrnovat jiné výpočty a manipulace dat kromě ověření a ukládání hodnotu vlastnosti.  
  
4.  Použijte parametr hodnotu tak, aby přijímal hodnota zadaná volání kódem. Můžete buď uložení této hodnoty přímo v příkazu přiřazení nebo použít ve výrazu k výpočtu interní hodnota, která má být uložen.  
  
 Musíte napsat `Set` postup pro vlastnost pro čtení a zápis a pro vlastnost jen pro zápis. Nesmí definovat `Set` postup pro vlastnost jen pro čtení.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří vlastnost pro čtení a zápis, která ukládá jméno a příjmení jako dvě základní názvy, křestní jméno a příjmení. Při volání kód čte `fullName`, `Get` postup kombinuje dva základní názvy a vrátí úplný název. Při volání kód přiřadí nový úplný název, `Set` postup pokusí rozdělit na dvě základní názvy. Pokud nenajde mezeru, uloží jej všechny jako křestní jméno.  
  
 [!code-vb[VbVbcnProcedures#8](./codesnippet/VisualBasic/how-to-create-a-property_1.vb)]  
  
 Následující příklad ukazuje typické volání procedury vlastnosti z `fullName`. První volání nastaví hodnotu vlastnosti a obnoví druhé volání.  
  
 [!code-vb[VbVbcnProcedures#9](./codesnippet/VisualBasic/how-to-create-a-property_2.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Procedury](./index.md)  
 [Procedury vlastnosti](./property-procedures.md)  
 [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)  
 [Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic](./differences-between-properties-and-variables.md)  
 [Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [Postupy: Volání procedury vlastnosti](./how-to-call-a-property-procedure.md)  
 [Postupy: deklarace a volání výchozí vlastnosti v jazyce Visual Basic](./how-to-declare-and-call-a-default-property.md)  
 [Postupy: Vložení hodnoty do vlastnosti](./how-to-put-a-value-in-a-property.md)  
 [Postupy: Získání hodnoty z vlastnosti](./how-to-get-a-value-from-a-property.md)
