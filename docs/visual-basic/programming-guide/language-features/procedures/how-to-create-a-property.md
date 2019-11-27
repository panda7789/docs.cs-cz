---
title: 'Postupy: Vytvoření vlastnosti'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, properties
- properties [Visual Basic]
ms.assetid: 4d229712-6be8-4c5c-bac5-06995ce9185a
ms.openlocfilehash: ee5a9f687765ce064eb3c3f84218ed36eb916d9d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349701"
---
# <a name="how-to-create-a-property-visual-basic"></a>Postupy: Vytvoření vlastnosti (Visual Basic)
Definici vlastnosti můžete uzavřít mezi `Property` příkaz a příkaz `End Property`. V rámci této definice definujete proceduru `Get`, `Set` postup nebo obojí. Všechny kódy vlastností leží v rámci těchto postupů.  
  
 Procedura `Get` načte hodnotu vlastnosti a procedura `Set` ukládá hodnotu. Chcete-li, aby vlastnost měla přístup pro čtení a zápis, je nutné definovat oba postupy. U vlastnosti jen pro čtení definujete pouze `Get`a pro vlastnost pouze pro zápis definujete pouze `Set`.  
  
### <a name="to-create-a-property"></a>Vytvoření vlastnosti  
  
1. Mimo jakoukoliv vlastnost nebo proceduru použijte [příkaz Property](../../../../visual-basic/language-reference/statements/property-statement.md)následovaný příkazem `End Property`.  
  
2. Pokud vlastnost přebírá parametry, použijte klíčové slovo `Property` s názvem procedury a pak seznam parametrů v závorkách.  
  
3. Pomocí závorek s klauzulí `As` určete datový typ hodnoty vlastnosti. Je nutné zadat datový typ i pro vlastnost, která je jen pro zápis.  
  
4. Podle potřeby přidejte `Get` a `Set` postupy. Přečtěte si následující pokyny.  
  
### <a name="to-create-a-get-procedure-that-retrieves-a-property-value"></a>Vytvoření procedury Get, která načte hodnotu vlastnosti  
  
1. Mezi příkazy `Property` a `End Property` zapište [příkaz Get](../../../../visual-basic/language-reference/statements/get-statement.md)následovaný příkazem `End Get`. Pro `Get` postup nemusíte definovat žádné parametry.  
  
2. Umístěte příkazy kódu pro načtení hodnoty vlastnosti mezi příkazy `Get` a `End Get`. Tento kód může kromě generování a vracení hodnoty vlastnosti zahrnovat i jiné výpočty a manipulace s daty.  
  
3. Použijte příkaz `Return` pro vrácení hodnoty vlastnosti na volající kód.  
  
 Je nutné zapsat `Get` proceduru pro vlastnost pro čtení i zápis a pro vlastnost určenou jen pro čtení. Pro vlastnost, která je jen pro zápis, nesmíte definovat `Get` proceduru.  
  
### <a name="to-create-a-set-procedure-that-writes-a-propertys-value"></a>Vytvoření procedury nastavení, která zapíše hodnotu vlastnosti  
  
1. Mezi příkazy `Property` a `End Property` zapište [příkaz set](../../../../visual-basic/language-reference/statements/set-statement.md)následovaný příkazem `End Set`.  
  
2. V příkazu `Set` postupujte podle klíčového slova `Set` se seznamem parametrů v závorkách. Tento seznam parametrů musí obsahovat alespoň parametr hodnoty pro hodnotu předanou volajícím kódem. Výchozí název tohoto parametru hodnoty je `Value`, ale v případě potřeby můžete použít jiný název. Parametr value musí mít stejný datový typ jako vlastnost samotnou.  
  
3. Umístěte příkazy kódu k uložení hodnoty ve vlastnosti mezi příkazy `Set` a `End Set`. Tento kód může kromě ověřování a ukládání hodnoty vlastnosti zahrnovat i jiné výpočty a manipulace s daty.  
  
4. Pomocí parametru value přijměte hodnotu poskytnutou volajícím kódem. Tuto hodnotu můžete buď uložit přímo do příkazu přiřazení, nebo ji použít ve výrazu k výpočtu interní hodnoty, která se má uložit.  
  
 Je nutné zapsat `Set` proceduru pro vlastnost pro čtení i zápis a pro vlastnost určenou jen pro zápis. Pro vlastnost určenou jen pro čtení není nutné definovat `Set` proceduru.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří vlastnost pro čtení a zápis, která uloží úplný název jako dva názvy prvků, křestní jméno a příjmení. Když volající kód přečte `fullName`, procedura `Get` kombinuje dva názvy prvků a vrátí úplný název. Když volající kód přiřadí nový úplný název, `Set` postup se pokusí ho rozdělit do dvou názvů prvků. Pokud nenalezne žádné místo, uloží ho jako křestní jméno.  
  
 [!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]  
  
 Následující příklad ukazuje typická volání procedur vlastností `fullName`. První volání nastaví hodnotu vlastnosti a druhé volání ji načte.  
  
 [!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Viz také:

- [Procedury](./index.md)
- [Procedury vlastnosti](./property-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Rozdíly mezi vlastnostmi a proměnnými v Visual Basic](./differences-between-properties-and-variables.md)
- [Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Postupy: Volání procedury vlastnosti](./how-to-call-a-property-procedure.md)
- [Postupy: deklarace a volání výchozí vlastnosti v Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Postupy: Vložení hodnoty do vlastnosti](./how-to-put-a-value-in-a-property.md)
- [Postupy: Získání hodnoty z vlastnosti](./how-to-get-a-value-from-a-property.md)
