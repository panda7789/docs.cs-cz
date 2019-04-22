---
title: Procedury vlastnosti (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Set statement [Visual Basic], Property procedures
- Visual Basic code, procedures
- return values [Visual Basic], Property procedures
- syntax [Visual Basic], Property procedures
- procedures [Visual Basic], property
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], custom
- property procedures
- Get statement [Visual Basic], property procedures
ms.assetid: 46a98379-e1a2-45dd-a48c-b51213f5ab07
ms.openlocfilehash: 47e93ee17f160ce5cd701fd0a12ec16b3997ce9b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58828340"
---
# <a name="property-procedures-visual-basic"></a>Procedury vlastnosti (Visual Basic)
Procedury vlastnosti je řadu příkazů jazyka Visual Basic, které pracují s vlastní vlastnost v modulu, třídy nebo struktury. Procedury vlastnosti jsou známé také jako *přistupující objekty vlastnosti*.  
  
 Visual Basic poskytuje pokyny pro následující vlastnost:  
  
-   A `Get` postup vrátí hodnotu vlastnosti. Je volána při přístupu k vlastnosti ve výrazu.  
  
-   A `Set` postup nastaví vlastnost na hodnotu, včetně odkazu na objekt. Je volána při přiřazení hodnoty k vlastnosti.  
  
 Obvykle definovat ve dvojicích, pomocí procedury vlastnosti `Get` a `Set` příkazy, ale můžete definovat těchto postupech samostatně, pokud je vlastnost jen pro čtení ([získat příkaz](../../../../visual-basic/language-reference/statements/get-statement.md)) nebo pouze pro zápis ([nastavení Příkaz](../../../../visual-basic/language-reference/statements/set-statement.md)).  
  
 Můžete vynechat `Get` a `Set` procedury při použití automaticky implementované vlastnosti. Další informace najdete v tématu [implemented Properties](./auto-implemented-properties.md).  
  
 Definujte vlastnosti do třídy, struktury a moduly. Vlastnosti jsou `Public` ve výchozím nastavení, což znamená, že je můžete volat z libovolného místa v aplikaci s přístupem k vlastnosti kontejneru.  
  
 Porovnání vlastnostmi a proměnnými, naleznete v tématu [rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic](./differences-between-properties-and-variables.md).  
  
## <a name="declaration-syntax"></a>Syntaxe deklarace  
 Samotné vlastnosti je definován bloku kódu uzavřený do složených závorek [Property – příkaz](../../../../visual-basic/language-reference/statements/property-statement.md) a `End Property` příkazu. V tomto bloku se každá procedura property zobrazí jako z vnitřního bloku uzavřeny v příkazu deklarace (`Get` nebo `Set`) a odpovídající `End` deklarace.  
  
 Syntaxe pro deklaraci vlastnosti a její postupy je následující:  
  
```  
[Default] [Modifiers] Property PropertyName[(ParameterList)] [As DataType]  
    [AccessLevel] Get  
        ' Statements of the Get procedure.  
        ' The following statement returns an expression as the property's value.  
        Return Expression  
    End Get  
    [AccessLevel] Set[(ByVal NewValue As DataType)]  
        ' Statements of the Set procedure.  
        ' The following statement assigns newvalue as the property's value.  
        LValue = NewValue  
    End Set  
End Property  
- or -  
[Default] [Modifiers] Property PropertyName [(ParameterList)] [As DataType]  
```  
  
 `Modifiers` Můžete určit úroveň přístupu a informace týkající se přetížení, přepsání, sdílení a stínování, stejně jako Určuje, zda je vlastnost jen pro čtení nebo jen pro zápis. `AccessLevel` Na `Get` nebo `Set` postupu může být libovolné úrovni, která je více omezující než úroveň přístupu, zadaná pro vlastnost samotný. Další informace najdete v tématu [Property – příkaz](../../../../visual-basic/language-reference/statements/property-statement.md).  
  
### <a name="data-type"></a>Datový typ  
 Typ dat vlastnosti a úroveň přístupu objektu zabezpečení jsou definovány v `Property` příkaz není v procedury vlastností. Vlastnost může mít pouze jednoho datového typu. Například nelze definovat vlastnost k ukládání `Decimal` hodnotu, ale načíst `Double` hodnotu.  
  
### <a name="access-level"></a>Úroveň přístupu  
 Ale můžete definovat úroveň zabezpečení přístupu pro vlastnost a dál omezit úroveň přístupu v jednom z jeho procedury vlastností. Například můžete definovat `Public` vlastnost a potom definovat, `Private Set` postup. `Get` Postup zůstane `Public`. Můžete změnit úroveň přístupu pouze v jednom z vlastnosti postupů a můžete pouze si je více omezující než úroveň přístupu instančního objektu. Další informace najdete v tématu [jak: Deklarace vlastnosti se smíšenými úrovněmi přístupu](./how-to-declare-a-property-with-mixed-access-levels.md).  
  
## <a name="parameter-declaration"></a>Deklarace parametru  
 Deklarujete každý parametr stejným způsobem jako u [Sub – procedury](./sub-procedures.md), s tím rozdílem, že musí být mechanismus předávání `ByVal`.  
  
 Syntaxe pro každý parametr v seznamu parametrů je následující:  
  
 `[Optional] ByVal [ParamArray] parametername As datatype`  
  
 Pokud se jedná o volitelný parametr, musíte také zadat výchozí hodnotu jako součást její deklarace. Syntaxe pro určení výchozí hodnota je následujícím způsobem:  
  
 `Optional ByVal parametername As datatype = defaultvalue`  
  
## <a name="property-value"></a>Hodnota vlastnosti  
 V `Get` procedury, vrácená hodnota je zadaný pro volání výrazu jako hodnotu vlastnosti.  
  
 V `Set` postupu hodnota nové vlastnosti je předán jako parametr `Set` příkazu. Pokud explicitně deklarujete parametr, musíte ji deklarovat s typem dat jako vlastnost. Pokud parametr nedeklaruje, kompilátor používá implicitní parametr `Value` představující nová hodnota pro přiřazení k vlastnosti.  
  
## <a name="calling-syntax"></a>Syntaxe volání  
 Vyvolání procedury vlastnosti implicitně tím, že odkaz na vlastnost. Můžete použít název vlastnosti stejným způsobem použijete název proměnné, s tím rozdílem, že je nutné zadat hodnoty pro všechny argumenty, které nejsou nepovinné a je nutné uzavřít do závorek seznamu argumentů. Pokud nejsou dodány žádné argumenty, můžete volitelně vynechejte závorky.  
  
 Syntaxe pro implicitní volání `Set` postup je následující:  
  
 `propertyname[(argumentlist)] = expression`  
  
 Syntaxe pro implicitní volání `Get` postup je následující:  
  
 `lvalue = propertyname[(argumentlist)]`  
  
 `Do While (propertyname[(argumentlist)] > expression)`  
  
### <a name="illustration-of-declaration-and-call"></a>Obrázek deklarace a volání  
 Následující vlastnosti se ukládají úplný název jako dva základní názvy, křestní jméno a příjmení. Když volající kód čte `fullName`, `Get` postup kombinuje dva základní názvy a vrátí úplný název. Pokud volající kód přiřadí nový úplný název, `Set` postup pokusy o jeho rozdělení na dva základní názvy. Pokud nelze najít mezeru, uloží jej jako křestní jméno.  
  
 [!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]  
  
 Následující příklad ukazuje typické volání procedury vlastnosti z `fullName`.  
  
 [!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Viz také:

- [Procedury](./index.md)
- [Procedury funkce](./function-procedures.md)
- [Procedury operátoru](./operator-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic](./differences-between-properties-and-variables.md)
- [Postupy: Vytvoření vlastnosti](./how-to-create-a-property.md)
- [Postupy: Volání procedury vlastnosti](./how-to-call-a-property-procedure.md)
- [Postupy: Deklarace a volání výchozí vlastnosti v jazyce Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Postupy: Vložení hodnoty do vlastnosti](./how-to-put-a-value-in-a-property.md)
- [Postupy: Získání hodnoty z vlastnosti](./how-to-get-a-value-from-a-property.md)
