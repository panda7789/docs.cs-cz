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
ms.openlocfilehash: a0a73494c3573973d88823a7b5a5a83d2672e7d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656084"
---
# <a name="property-procedures-visual-basic"></a>Procedury vlastnosti (Visual Basic)
Procedury vlastnosti je řada příkazů jazyka Visual Basic, které pracují s vlastní vlastnost na modul, třídu nebo strukturu. Procedury vlastností se také označují jako *přístupové objekty vlastnosti*.  
  
 Visual Basic poskytuje následující postupy vlastnost:  
  
-   A `Get` postup vrátí hodnotu vlastnosti. Je volána při přístupu k vlastnosti ve výrazu.  
  
-   A `Set` postup nastaví vlastnost na hodnotu, včetně odkaz na objekt. Je volána při přiřazení hodnotu pro vlastnost.  
  
 Obvykle definovat procedury vlastností v párech, a pomocí `Get` a `Set` příkazy, ale můžete definovat buď postup samostatně, pokud vlastnost je jen pro čtení ([získat příkaz](../../../../visual-basic/language-reference/statements/get-statement.md)) nebo pouze pro zápis ([nastavit Příkaz](../../../../visual-basic/language-reference/statements/set-statement.md)).  
  
 Můžete vynechat `Get` a `Set` procedury při použití ve automaticky implementované vlastnosti. Další informace najdete v tématu [Auto-Implemented vlastnosti](./auto-implemented-properties.md).  
  
 V tříd, struktur a moduly můžete definovat vlastnosti. Vlastnosti jsou `Public` ve výchozím nastavení, což znamená, můžete je volat z libovolného místa v aplikaci, které můžete přístup k vlastnosti kontejneru.  
  
 Porovnání vlastností a proměnných najdete v tématu [rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic](./differences-between-properties-and-variables.md).  
  
## <a name="declaration-syntax"></a>Syntaxe deklarace  
 Samotné vlastnosti je definována blok kódu v rámci uzavřené [Property – příkaz](../../../../visual-basic/language-reference/statements/property-statement.md) a `End Property` příkaz. V tomto bloku každý procedury vlastnosti se zobrazí jako interní bloku uzavřené v rámci příkazu deklarace (`Get` nebo `Set`) a vyhledávání shody `End` deklarace.  
  
 Syntaxe deklarace vlastnost a její postupy vypadá takto:  
  
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
  
 `Modifiers` Můžete zadat úroveň přístupu a informací o přetížení, přepsání, sdílení a stínový provoz, stejně jako jestli vlastnost je jen pro čtení nebo jen pro zápis. `AccessLevel` Na `Get` nebo `Set` postupu může být všechny úrovně, který je více omezující než úroveň přístupu, zadaná pro vlastnost sám sebe. Další informace najdete v tématu [Property – příkaz](../../../../visual-basic/language-reference/statements/property-statement.md).  
  
### <a name="data-type"></a>Datový typ  
 Datový typ vlastnost a úroveň hlavní přístupu jsou definovány v `Property` příkaz není v procedury vlastností. Vlastnost může mít pouze jednoho datového typu. Například nelze definovat vlastnosti, které chcete uložit `Decimal` hodnotu, ale načíst `Double` hodnotu.  
  
### <a name="access-level"></a>Úroveň přístupu  
 Můžete však definovat úroveň hlavní přístup pro vlastnost a dál omezit úroveň přístupu v jednom z jeho procedury vlastností. Například můžete definovat `Public` vlastnost a potom zadejte `Private Set` postupu. `Get` Postup zůstane `Public`. Můžete změnit úroveň přístupu v pouze jeden z postupů vlastnost a pouze jej lze vytvořit více omezující než úroveň hlavní přístupu. Další informace najdete v tématu [postupy: deklarace vlastnosti se smíšené úrovně přístupu](./how-to-declare-a-property-with-mixed-access-levels.md).  
  
## <a name="parameter-declaration"></a>Deklarace parametru  
 Deklarovat každý parametr stejným způsobem jako u [Sub – procedury](./sub-procedures.md)kromě toho, že musí být tento mechanismus předávání `ByVal`.  
  
 Syntaxe pro každý parametr v seznamu parametrů je následující:  
  
 `[Optional] ByVal [ParamArray] parametername As datatype`  
  
 Pokud se jedná o volitelný parametr, musíte také zadat výchozí hodnotu v rámci jeho deklaraci. Syntaxe pro určení výchozí hodnota je následující:  
  
 `Optional ByVal parametername As datatype = defaultvalue`  
  
## <a name="property-value"></a>Hodnota vlastnosti  
 V `Get` poskytnutý postupu návratovou hodnotu volání výrazu jako hodnotu vlastnosti.  
  
 V `Set` postup, nová hodnota vlastnosti je předaný parametr `Set` příkaz. Pokud je výslovně deklarovat parametr, je třeba deklarovat s stejný datový typ jako vlastnost. Pokud parametr nedeklarujte, kompilátor použije implicitní parametr `Value` představují nová hodnota pro přiřazení k vlastnosti.  
  
## <a name="calling-syntax"></a>Syntaxe volání  
 Vyvolání procedury vlastnosti implicitně tím, že odkaz na vlastnost. Pomocí názvu vlastnosti stejným způsobem, jako byste použili název proměnné, s tím rozdílem, že je nutné zadat hodnoty pro všechny argumenty, které nejsou volitelné a seznam argumentů je nutné uzavřít do závorek. Pokud jsou zadány žádné argumenty, můžete volitelně vynechat závorkách.  
  
 Syntaxe pro implicitní volání `Set` postup je následující:  
  
 `propertyname[(argumentlist)] = expression`  
  
 Syntaxe pro implicitní volání `Get` postup je následující:  
  
 `lvalue = propertyname[(argumentlist)]`  
  
 `Do While (propertyname[(argumentlist)] > expression)`  
  
### <a name="illustration-of-declaration-and-call"></a>Obrázek deklarace a volání  
 Následující vlastnosti se ukládají jméno a příjmení jako dvě základní názvy, křestní jméno a příjmení. Při volání kód čte `fullName`, `Get` postup kombinuje dva základní názvy a vrátí úplný název. Při volání kód přiřadí nový úplný název, `Set` postup pokusí rozdělit na dvě základní názvy. Pokud nenajde mezeru, uloží jej všechny jako křestní jméno.  
  
 [!code-vb[VbVbcnProcedures#8](./codesnippet/VisualBasic/property-procedures_1.vb)]  
  
 Následující příklad ukazuje typické volání procedury vlastnosti z `fullName`.  
  
 [!code-vb[VbVbcnProcedures#9](./codesnippet/VisualBasic/property-procedures_2.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Procedury](./index.md)  
 [Procedury funkce](./function-procedures.md)  
 [Procedury operátoru](./operator-procedures.md)  
 [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)  
 [Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic](./differences-between-properties-and-variables.md)  
 [Postupy: Vytvoření vlastnosti](./how-to-create-a-property.md)  
 [Postupy: Volání procedury vlastnosti](./how-to-call-a-property-procedure.md)  
 [Postupy: deklarace a volání výchozí vlastnosti v jazyce Visual Basic](./how-to-declare-and-call-a-default-property.md)  
 [Postupy: Vložení hodnoty do vlastnosti](./how-to-put-a-value-in-a-property.md)  
 [Postupy: Získání hodnoty z vlastnosti](./how-to-get-a-value-from-a-property.md)
