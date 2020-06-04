---
title: 'Postupy: Vytvoření vlastnosti'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, properties
- properties [Visual Basic]
ms.assetid: 4d229712-6be8-4c5c-bac5-06995ce9185a
ms.openlocfilehash: fa220998d12206e620c242b9b39df3dc1b639d29
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388255"
---
# <a name="how-to-create-a-property-visual-basic"></a>Postupy: Vytvoření vlastnosti (Visual Basic)
Definici vlastnosti můžete uzavřít mezi `Property` příkazem a `End Property` příkazem. V rámci této definice definujete `Get` proceduru, `Set` proceduru nebo obojí. Všechny kódy vlastností leží v rámci těchto postupů.  
  
 `Get`Procedura načte hodnotu vlastnosti a `Set` procedura ukládá hodnotu. Chcete-li, aby vlastnost měla přístup pro čtení a zápis, je nutné definovat oba postupy. Pro vlastnost, která je jen pro čtení, můžete definovat pouze `Get` a pro vlastnost pouze pro zápis pouze definovat `Set` .  
  
### <a name="to-create-a-property"></a>Vytvoření vlastnosti  
  
1. Mimo jakoukoliv vlastnost nebo proceduru použijte [příkaz Property](../../../language-reference/statements/property-statement.md)následovaný `End Property` příkazem.  
  
2. Pokud vlastnost přebírá parametry, postupujte podle `Property` klíčového slova s názvem procedury a potom seznamem parametrů v závorkách.  
  
3. Pomocí závorek s `As` klauzulí určete datový typ hodnoty vlastnosti. Je nutné zadat datový typ i pro vlastnost, která je jen pro zápis.  
  
4. `Get` `Set` Podle potřeby přidejte a procedury. Přečtěte si následující pokyny.  
  
### <a name="to-create-a-get-procedure-that-retrieves-a-property-value"></a>Vytvoření procedury Get, která načte hodnotu vlastnosti  
  
1. Mezi `Property` příkazy a `End Property` napište [příkaz Get](../../../language-reference/statements/get-statement.md)následovaný `End Get` příkazem. Pro proceduru nemusíte definovat žádné parametry `Get` .  
  
2. Umístěte příkazy kódu pro načtení hodnoty vlastnosti mezi `Get` `End Get` příkazy a. Tento kód může kromě generování a vracení hodnoty vlastnosti zahrnovat i jiné výpočty a manipulace s daty.  
  
3. Použijte `Return` příkaz pro vrácení hodnoty vlastnosti na volající kód.  
  
 Je nutné napsat `Get` proceduru pro vlastnost pro čtení i zápis a pro vlastnost určenou jen pro čtení. Pro vlastnost, která je `Get` jen pro zápis, nesmíte definovat proceduru.  
  
### <a name="to-create-a-set-procedure-that-writes-a-propertys-value"></a>Vytvoření procedury nastavení, která zapíše hodnotu vlastnosti  
  
1. Mezi `Property` příkazy a `End Property` napište [příkaz set](../../../language-reference/statements/set-statement.md)následovaný `End Set` příkazem.  
  
2. V `Set` příkazu použijte `Set` klíčové slovo s seznamem parametrů v závorkách. Tento seznam parametrů musí obsahovat alespoň parametr hodnoty pro hodnotu předanou volajícím kódem. Výchozí název tohoto parametru hodnoty je `Value` , ale v případě potřeby můžete použít jiný název. Parametr value musí mít stejný datový typ jako vlastnost samotnou.  
  
3. Umístěte příkazy kódu k uložení hodnoty ve vlastnosti mezi `Set` `End Set` příkazy a. Tento kód může kromě ověřování a ukládání hodnoty vlastnosti zahrnovat i jiné výpočty a manipulace s daty.  
  
4. Pomocí parametru value přijměte hodnotu poskytnutou volajícím kódem. Tuto hodnotu můžete buď uložit přímo do příkazu přiřazení, nebo ji použít ve výrazu k výpočtu interní hodnoty, která se má uložit.  
  
 Musíte napsat `Set` proceduru pro vlastnost pro čtení i zápis a pro vlastnost určenou jen pro zápis. `Set`Pro vlastnost určenou jen pro čtení nesmíte definovat proceduru.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří vlastnost pro čtení a zápis, která uloží úplný název jako dva názvy prvků, křestní jméno a příjmení. Když volající kód přečte `fullName` , `Get` procedura Zkombinuje dva názvy prvků a vrátí úplný název. Když volající kód přiřadí nový úplný název, procedura se `Set` pokusí ho rozdělit do dvou názvů prvků. Pokud nenalezne žádné místo, uloží ho jako křestní jméno.  
  
 [!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]  
  
 Následující příklad ukazuje typická volání procedur vlastností třídy `fullName` . První volání nastaví hodnotu vlastnosti a druhé volání ji načte.  
  
 [!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Viz také

- [Procedury](./index.md)
- [Procedury vlastnosti](./property-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic](./differences-between-properties-and-variables.md)
- [Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Postupy: Volání procedury vlastnosti](./how-to-call-a-property-procedure.md)
- [Postupy: Deklarace a volání výchozí vlastnosti v jazyce Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Postupy: Vložení hodnoty do vlastnosti](./how-to-put-a-value-in-a-property.md)
- [Postupy: Získání hodnoty z vlastnosti](./how-to-get-a-value-from-a-property.md)
