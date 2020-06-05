---
title: Procedury vlastnosti
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
ms.openlocfilehash: cb5b0e12512e476b7c96bbfb19f8e4f470f6b498
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363730"
---
# <a name="property-procedures-visual-basic"></a>Procedury vlastnosti (Visual Basic)

Procedura vlastnosti je řada příkazů Visual Basic, které pracují s vlastní vlastností v modulu, třídě nebo struktuře. Procedury vlastnosti jsou také známé jako *přistupující objekty vlastností*.

Visual Basic poskytuje následující procedury vlastností:

- `Get`Procedura vrátí hodnotu vlastnosti. Je volána při přístupu k vlastnosti ve výrazu.
- `Set`Procedura nastaví vlastnost na hodnotu, včetně odkazu na objekt. Je volána, když přiřadíte hodnotu k vlastnosti.

Procedury vlastností ve dvojicích obvykle definujete pomocí `Get` příkazů a `Set` , ale můžete definovat buď samostatně, pokud je vlastnost jen pro čtení ([příkaz Get](../../../language-reference/statements/get-statement.md)) nebo pouze pro zápis ([příkaz set](../../../language-reference/statements/set-statement.md)).

Můžete vynechat `Get` `Set` proceduru a při použití automaticky implementované vlastnosti. Další informace najdete v tématu věnovaném [automaticky implementovaným vlastnostem](./auto-implemented-properties.md).

Můžete definovat vlastnosti v třídách, strukturách a modulech. `Public`Ve výchozím nastavení jsou vlastnosti, což znamená, že je můžete volat odkudkoli v aplikaci, která má přístup k kontejneru vlastnosti.

Porovnání vlastností a proměnných naleznete [v tématu rozdíly mezi vlastnostmi a proměnnými v Visual Basic](differences-between-properties-and-variables.md).

## <a name="declaration-syntax"></a>Syntaxe deklarace

Samotná vlastnost je definována blokem kódu uzavřeným v rámci [příkazu Property](../../../language-reference/statements/property-statement.md) a `End Property` příkazu. V rámci tohoto bloku se každá procedura Vlastnosti zobrazuje jako vnitřní blok uzavřený v příkazu deklarace ( `Get` nebo `Set` ) a v rámci `End` deklarace v porovnání.

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
' - or -
[Default] [Modifiers] Property PropertyName [(ParameterList)] [As DataType]
```

`Modifiers`Může určit úroveň přístupu a informace týkající se přetížení, přepsání, sdílení a stínování a také zda je vlastnost jen pro čtení nebo jen pro zápis. `AccessLevel`V `Get` `Set` proceduře nebo může být libovolná úroveň, která je více omezující než úroveň přístupu zadaná pro samotnou vlastnost. Další informace naleznete v tématu [příkaz Vlastnosti](../../../language-reference/statements/property-statement.md).

### <a name="data-type"></a>Typ dat

Datový typ vlastnosti a úroveň přístupu zabezpečení jsou definovány v `Property` příkazu, nikoli v procedurách vlastnosti. Vlastnost může mít pouze jeden datový typ. Například nelze definovat vlastnost pro uložení `Decimal` hodnoty, ale načtení `Double` hodnoty.

### <a name="access-level"></a>Úroveň přístupu

Můžete však definovat hlavní úroveň přístupu pro vlastnost a dále omezit úroveň přístupu v jednom z jeho procedur vlastností. Můžete například definovat `Public` vlastnost a pak definovat `Private Set` proceduru. `Get`Postup zůstane `Public` . Úroveň přístupu můžete změnit jenom v jednom z procedur vlastnosti a můžete ji omezit jenom na úroveň přístupu zabezpečení. Další informace najdete v tématu [Postupy: deklarace vlastnosti se smíšenými úrovněmi přístupu](how-to-declare-a-property-with-mixed-access-levels.md).

## <a name="parameter-declaration"></a>Deklarace parametru

Každý parametr deklarujete stejným způsobem jako u [procedur sub](sub-procedures.md), s tím rozdílem, že mechanismus předávání musí být `ByVal` .

Syntaxe pro každý parametr v seznamu parametrů je následující:

```vb
[Optional] ByVal [ParamArray] parametername As datatype
```

Pokud je parametr volitelný, musíte také zadat výchozí hodnotu jako součást její deklarace. Syntaxe pro určení výchozí hodnoty je následující:

```vb
Optional ByVal parametername As datatype = defaultvalue
```

## <a name="property-value"></a>Hodnota vlastnosti

V `Get` proceduře je vrácená hodnota dodána volajícímu výrazu jako hodnota vlastnosti.

V `Set` proceduře je nová hodnota vlastnosti předána parametru `Set` příkazu. Pokud explicitně deklarujete parametr, je nutné jej deklarovat se stejným datovým typem jako vlastnost. Pokud parametr nedeklarujete, kompilátor použije implicitní parametr `Value` pro reprezentaci nové hodnoty, která má být přiřazena vlastnosti.

## <a name="calling-syntax"></a>Syntaxe volání

Proceduru vlastnosti můžete implicitně vyvolat tak, že vytvoříte odkaz na vlastnost. Název vlastnosti použijete stejným způsobem jako název proměnné, s výjimkou toho, že je nutné zadat hodnoty pro všechny argumenty, které nejsou volitelné, a je třeba uzavřít seznam argumentů v závorkách. Pokud nejsou zadány žádné argumenty, můžete volitelně vynechat závorky.

Syntaxe implicitního volání `Set` procedury je následující:

```vb
propertyname[(argumentlist)] = expression
```

Syntaxe implicitního volání `Get` procedury je následující:

```vb
lvalue = propertyname[(argumentlist)]
Do While (propertyname[(argumentlist)] > expression)
```

### <a name="illustration-of-declaration-and-call"></a>Ilustrace deklarace a volání

Následující vlastnost uchovává úplný název jako dva názvy prvků, křestní jméno a příjmení. Když volající kód přečte `fullName` , `Get` procedura Zkombinuje dva názvy prvků a vrátí úplný název. Když volající kód přiřadí nový úplný název, procedura se `Set` pokusí ho rozdělit do dvou názvů prvků. Pokud nenalezne žádné místo, uloží ho jako křestní jméno.

[!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]

Následující příklad ukazuje typická volání procedur vlastností `fullName` :

[!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]

## <a name="see-also"></a>Viz také

- [Procedury](index.md)
- [Procedury funkcí](function-procedures.md)
- [Procedury operátoru](operator-procedures.md)
- [Parametry a argumenty procedury](procedure-parameters-and-arguments.md)
- [Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic](differences-between-properties-and-variables.md)
- [Postupy: Vytvoření vlastnosti](how-to-create-a-property.md)
- [Postupy: Volání procedury vlastnosti](how-to-call-a-property-procedure.md)
- [Postupy: Deklarace a volání výchozí vlastnosti v jazyce Visual Basic](how-to-declare-and-call-a-default-property.md)
- [Postupy: Vložení hodnoty do vlastnosti](how-to-put-a-value-in-a-property.md)
- [Postupy: Získání hodnoty z vlastnosti](how-to-get-a-value-from-a-property.md)
