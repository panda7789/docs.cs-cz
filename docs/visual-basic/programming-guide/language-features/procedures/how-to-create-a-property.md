---
title: 'Postupy: Vytvoření vlastnosti (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, properties
- properties [Visual Basic]
ms.assetid: 4d229712-6be8-4c5c-bac5-06995ce9185a
ms.openlocfilehash: 91f34de36e88724ccab21097bf54a4604f7eee37
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665777"
---
# <a name="how-to-create-a-property-visual-basic"></a>Postupy: Vytvoření vlastnosti (Visual Basic)
Použijte definici vlastnosti mezi `Property` příkazu a `End Property` příkazu. V rámci této definice můžete definovat `Get` postupu `Set` procedury nebo obojí. Všechny vlastnosti kódu je v rámci těchto postupů.  
  
 `Get` Načte hodnotu vlastnosti, procedury a `Set` postup uloží hodnotu. Pokud chcete vlastnost, která má mít přístup pro čtení a zápis, je nutné definovat oba postupy. Pro vlastnost jen pro čtení, můžete definovat pouze `Get`, a pro vlastnost jen pro zápis, můžete definovat pouze `Set`.  
  
### <a name="to-create-a-property"></a>Pro vytvoření vlastnosti  
  
1. Mimo vlastnost nebo procedura, použijte [Property – příkaz](../../../../visual-basic/language-reference/statements/property-statement.md)následovaný `End Property` příkazu.  
  
2. Pokud vlastnost přijímá parametry, postupujte `Property` – klíčové slovo s názvem podle postupu, pak se seznam parametrů v závorkách.  
  
3. Postupujte podle závorek s `As` klauzule zadejte datový typ hodnoty vlastnosti. Je třeba zadat typ dat i pro vlastnost jen pro zápis.  
  
4. Přidat `Get` a `Set` postupy, podle potřeby. Viz následující pokyny.  
  
### <a name="to-create-a-get-procedure-that-retrieves-a-property-value"></a>Chcete-li vytvořit procedury Get, která načte hodnotu vlastnosti  
  
1. Mezi `Property` a `End Property` psát příkazy, [získat příkaz](../../../../visual-basic/language-reference/statements/get-statement.md)následovaný `End Get` příkazu. Není potřeba definujte libovolné parametry pro `Get` postup.  
  
2. Umístit příkazy kódu k načtení hodnoty vlastnosti mezi `Get` a `End Get` příkazy. Tento kód může obsahovat další výpočty a manipulace dat kromě generování a vrací hodnotu vlastnosti.  
  
3. Použití `Return` příkazu vrátí hodnotu vlastnosti volajícímu kódu.  
  
 Je nutné napsat `Get` postup pro vlastnost pro čtení i zápis a pro vlastnost jen pro čtení. Nesmí definovat `Get` postup pro vlastnost jen pro zápis.  
  
### <a name="to-create-a-set-procedure-that-writes-a-propertys-value"></a>Vytvořte sadu proceduru, která zapíše hodnoty vlastnosti  
  
1. Mezi `Property` a `End Property` příkazy, zápis [nastavit příkaz](../../../../visual-basic/language-reference/statements/set-statement.md)následovaný `End Set` příkaz.  
  
2. V `Set` prohlášení, postupujte `Set` – klíčové slovo se seznamem parametrů v závorkách. Tento seznam parametrů musí obsahovat alespoň hodnotu parametru pro hodnotu předanou ve volajícím kódu. Je výchozí název pro tento parametr hodnotu `Value`, ale v případě potřeby můžete použít jiný název. Parametr value musí mít stejný datový typ jako samotné vlastnosti.  
  
3. Umístit příkazy kódu k uložení hodnoty do vlastnosti mezi `Set` a `End Set` příkazy. Tento kód může obsahovat další výpočty a manipulace dat kromě ověřování a uložení hodnoty vlastnosti.  
  
4. Použijte parametr hodnoty tak, aby přijímal hodnoty poskytnuté volajícím kódu. Můžete přímo v příkazu přiřazení uložte tuto hodnotu, nebo použít ve výrazu k výpočtu interní hodnota, která má být uložena.  
  
 Je nutné napsat `Set` postup pro vlastnost pro čtení i zápis a pro vlastnost jen pro zápis. Nesmí definovat `Set` postup pro vlastnost jen pro čtení.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří vlastnost pro čtení a zápis, která ukládá celé jméno, křestní jméno a příjmení dvě základní názvy jako. Když volající kód čte `fullName`, `Get` postup kombinuje dva základní názvy a vrátí úplný název. Pokud volající kód přiřadí nový úplný název, `Set` postup pokusy o jeho rozdělení na dva základní názvy. Pokud nelze najít mezeru, uloží jej jako křestní jméno.  
  
 [!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]  
  
 Následující příklad ukazuje typické volání procedury vlastnosti z `fullName`. První volání nastaví hodnotu vlastnosti a druhé volání obnoví.  
  
 [!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Viz také:

- [Procedury](./index.md)
- [Procedury vlastnosti](./property-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic](./differences-between-properties-and-variables.md)
- [Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Postupy: Volání procedury vlastnosti](./how-to-call-a-property-procedure.md)
- [Postupy: Deklarace a volání výchozí vlastnosti v jazyce Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Postupy: Vložení hodnoty do vlastnosti](./how-to-put-a-value-in-a-property.md)
- [Postupy: Získání hodnoty z vlastnosti](./how-to-get-a-value-from-a-property.md)
