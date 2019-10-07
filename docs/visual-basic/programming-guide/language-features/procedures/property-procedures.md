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
ms.openlocfilehash: f3b57ae45815fbd91cad17cddbed4d01037eb92f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002084"
---
# <a name="property-procedures-visual-basic"></a>Procedury vlastnosti (Visual Basic)
Procedura vlastnosti je řada příkazů Visual Basic, které pracují s vlastní vlastností v modulu, třídě nebo struktuře. Procedury vlastnosti jsou také známé jako *přistupující objekty vlastností*.  
  
 Visual Basic poskytuje následující procedury vlastností:  
  
- Procedura `Get` vrátí hodnotu vlastnosti. Je volána při přístupu k vlastnosti ve výrazu.  
  
- Procedura `Set` nastaví vlastnost na hodnotu, včetně odkazu na objekt. Je volána, když přiřadíte hodnotu k vlastnosti.  
  
 Procedury vlastností ve dvojicích obvykle definujete pomocí příkazů `Get` a `Set`, ale můžete definovat buď samostatně, pokud je vlastnost jen pro čtení ([příkaz Get](../../../../visual-basic/language-reference/statements/get-statement.md)) nebo pouze pro zápis ([příkaz set](../../../../visual-basic/language-reference/statements/set-statement.md)).  
  
 Při použití automaticky implementované vlastnosti můžete vynechat postup `Get` a `Set`. Další informace najdete v tématu věnovaném [automaticky implementovaným vlastnostem](./auto-implemented-properties.md).  
  
 Můžete definovat vlastnosti v třídách, strukturách a modulech. Ve výchozím nastavení jsou vlastnosti `Public`, což znamená, že je můžete volat odkudkoli v aplikaci, která má přístup k kontejneru vlastnosti.  
  
 Porovnání vlastností a proměnných naleznete [v tématu rozdíly mezi vlastnostmi a proměnnými v Visual Basic](./differences-between-properties-and-variables.md).  
  
## <a name="declaration-syntax"></a>Syntaxe deklarace  
 Samotná vlastnost je definována blokem kódu uzavřeným v rámci [příkazu Property](../../../../visual-basic/language-reference/statements/property-statement.md) a příkazu `End Property`. V rámci tohoto bloku se každá procedura Vlastnosti zobrazuje jako vnitřní blok uzavřený v rámci příkazu deklarace (`Get` nebo `Set`) a shoda deklarace `End`.  
  
 Syntaxe pro deklaraci vlastnosti a její postupy je následující:  
  
```vb  
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
  
 @No__t-0 může určovat úroveň přístupu a informace týkající se přetěžování, přepsání, sdílení a stínování a také zda je vlastnost jen pro čtení nebo jen pro zápis. @No__t-0 v proceduře `Get` nebo `Set` může být libovolná úroveň, která je více omezující než úroveň přístupu zadaná pro samotnou vlastnost. Další informace naleznete v tématu [příkaz Vlastnosti](../../../../visual-basic/language-reference/statements/property-statement.md).  
  
### <a name="data-type"></a>Datový typ  
 Datový typ a úroveň přístupu objektu vlastnosti jsou definovány v příkazu `Property`, nikoli v procedurách vlastnosti. Vlastnost může mít pouze jeden datový typ. Například nelze definovat vlastnost pro uložení hodnoty @no__t 0, ale načtení hodnoty `Double`.  
  
### <a name="access-level"></a>Úroveň přístupu  
 Můžete však definovat hlavní úroveň přístupu pro vlastnost a dále omezit úroveň přístupu v jednom z jeho procedur vlastností. Můžete například definovat vlastnost `Public` a pak definovat proceduru `Private Set`. Procedura `Get` zůstane `Public`. Úroveň přístupu můžete změnit jenom v jednom z procedur vlastnosti a můžete ji omezit jenom na úroveň přístupu zabezpečení. Další informace najdete v tématu [Postupy: deklarace vlastnosti se smíšenými úrovněmi přístupu](./how-to-declare-a-property-with-mixed-access-levels.md).  
  
## <a name="parameter-declaration"></a>Deklarace parametru  
 Každý parametr deklarujete stejným způsobem jako u [dílčích procedur](./sub-procedures.md), s tím rozdílem, že mechanismus předávání musí být `ByVal`.  
  
 Syntaxe pro každý parametr v seznamu parametrů je následující:  
  
 `[Optional] ByVal [ParamArray] parametername As datatype`  
  
 Pokud je parametr volitelný, musíte také zadat výchozí hodnotu jako součást její deklarace. Syntaxe pro určení výchozí hodnoty je následující:  
  
 `Optional ByVal parametername As datatype = defaultvalue`  
  
## <a name="property-value"></a>Hodnota vlastnosti  
 V proceduře `Get` je návratová hodnota zadána do volajícího výrazu jako hodnota vlastnosti.  
  
 V proceduře `Set` je nová hodnota vlastnosti předána parametru příkazu `Set`. Pokud explicitně deklarujete parametr, je nutné jej deklarovat se stejným datovým typem jako vlastnost. Pokud parametr nedeklarujete, kompilátor použije implicitní parametr `Value` pro reprezentaci nové hodnoty, která má být přiřazena vlastnosti.  
  
## <a name="calling-syntax"></a>Syntaxe volání  
 Proceduru vlastnosti můžete implicitně vyvolat tak, že vytvoříte odkaz na vlastnost. Název vlastnosti použijete stejným způsobem jako název proměnné, s výjimkou toho, že je nutné zadat hodnoty pro všechny argumenty, které nejsou volitelné, a je třeba uzavřít seznam argumentů v závorkách. Pokud nejsou zadány žádné argumenty, můžete volitelně vynechat závorky.  
  
 Syntaxe pro implicitní volání procedury `Set` je následující:  
  
 `propertyname[(argumentlist)] = expression`  
  
 Syntaxe pro implicitní volání procedury `Get` je následující:  
  
 `lvalue = propertyname[(argumentlist)]`  
  
 `Do While (propertyname[(argumentlist)] > expression)`  
  
### <a name="illustration-of-declaration-and-call"></a>Ilustrace deklarace a volání  
 Následující vlastnost uchovává úplný název jako dva názvy prvků, křestní jméno a příjmení. Když volající kód přečte `fullName`, procedura `Get` kombinuje dva názvy prvků a vrátí úplný název. Když volající kód přiřadí nový úplný název, procedura `Set` se pokusí ho rozdělit do dvou názvů prvků. Pokud nenalezne žádné místo, uloží ho jako křestní jméno.  
  
 [!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]  
  
 Následující příklad ukazuje typická volání procedur vlastností `fullName`.  
  
 [!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Viz také:

- [Procedury](./index.md)
- [Procedury funkce](./function-procedures.md)
- [Procedury operátoru](./operator-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Rozdíly mezi vlastnostmi a proměnnými v Visual Basic](./differences-between-properties-and-variables.md)
- [Postupy: Vytvoření vlastnosti](./how-to-create-a-property.md)
- [Postupy: Volání procedury vlastnosti](./how-to-call-a-property-procedure.md)
- [Postupy: deklarace a volání výchozí vlastnosti v Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Postupy: Vložení hodnoty do vlastnosti](./how-to-put-a-value-in-a-property.md)
- [Postupy: Získání hodnoty z vlastnosti](./how-to-get-a-value-from-a-property.md)
