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
ms.openlocfilehash: a4b8ac3e27348764f537ee9502ce1fbb165bb3ef
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352566"
---
# <a name="property-procedures-visual-basic"></a>Procedury vlastnosti (Visual Basic)

Procedura vlastnosti je řada příkazů Visual Basic, které pracují s vlastní vlastností v modulu, třídě nebo struktuře. Procedury vlastnosti jsou také známé jako *přistupující objekty vlastností*.

Visual Basic poskytuje následující procedury vlastností:

- `Get` procedura vrátí hodnotu vlastnosti. Je volána při přístupu k vlastnosti ve výrazu.
- Procedura `Set` nastaví vlastnost na hodnotu, včetně odkazu na objekt. Je volána, když přiřadíte hodnotu k vlastnosti.

Procedury vlastností ve dvojicích obvykle definujete pomocí příkazů `Get` a `Set`, ale můžete definovat buď samostatně, pokud je vlastnost jen pro čtení ([příkaz Get](../../../../visual-basic/language-reference/statements/get-statement.md)) nebo pouze pro zápis ([příkaz set](../../../../visual-basic/language-reference/statements/set-statement.md)).

Můžete vynechat `Get` a `Set` postup při použití automaticky implementované vlastnosti. Další informace najdete v tématu věnovaném [automaticky implementovaným vlastnostem](./auto-implemented-properties.md).

Můžete definovat vlastnosti v třídách, strukturách a modulech. Ve výchozím nastavení jsou vlastnosti `Public`, což znamená, že je můžete volat odkudkoli v aplikaci, která má přístup k kontejneru vlastnosti.

Porovnání vlastností a proměnných naleznete [v tématu rozdíly mezi vlastnostmi a proměnnými v Visual Basic](differences-between-properties-and-variables.md).

## <a name="declaration-syntax"></a>Syntaxe deklarace

Samotná vlastnost je definována blokem kódu uzavřeným v rámci [příkazu Property](../../../../visual-basic/language-reference/statements/property-statement.md) a příkazu `End Property`. V rámci tohoto bloku se každá procedura Vlastnosti zobrazuje jako vnitřní blok uzavřený v rámci příkazu deklarace (`Get` nebo `Set`) a deklarace `End`.

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

`Modifiers` může určovat úroveň přístupu a informace týkající se přetížení, přepsání, sdílení a stínování a také zda je vlastnost jen pro čtení nebo jen pro zápis. `AccessLevel` v proceduře `Get` nebo `Set` může být libovolná úroveň, která je více omezující než úroveň přístupu zadaná pro samotnou vlastnost. Další informace naleznete v tématu [příkaz Vlastnosti](../../../../visual-basic/language-reference/statements/property-statement.md).

### <a name="data-type"></a>Typ dat

Datový typ vlastnosti a úroveň přístupu zabezpečení jsou definovány v příkazu `Property`, nikoli v procedurách vlastnosti. Vlastnost může mít pouze jeden datový typ. Například nelze definovat vlastnost pro uložení `Decimal` hodnoty, ale načtení `Double` hodnoty.

### <a name="access-level"></a>Úroveň přístupu

Můžete však definovat hlavní úroveň přístupu pro vlastnost a dále omezit úroveň přístupu v jednom z jeho procedur vlastností. Můžete například definovat vlastnost `Public` a potom definovat `Private Set` proceduru. `Get` postup zůstane `Public`. Úroveň přístupu můžete změnit jenom v jednom z procedur vlastnosti a můžete ji omezit jenom na úroveň přístupu zabezpečení. Další informace najdete v tématu [Postupy: deklarace vlastnosti se smíšenými úrovněmi přístupu](how-to-declare-a-property-with-mixed-access-levels.md).

## <a name="parameter-declaration"></a>Deklarace parametru

Každý parametr deklarujete stejným způsobem jako u [dílčích procedur](sub-procedures.md), s tím rozdílem, že mechanismus předávání musí být `ByVal`.

Syntaxe pro každý parametr v seznamu parametrů je následující:

```vb
[Optional] ByVal [ParamArray] parametername As datatype
```

Pokud je parametr volitelný, musíte také zadat výchozí hodnotu jako součást její deklarace. Syntaxe pro určení výchozí hodnoty je následující:

```vb
Optional ByVal parametername As datatype = defaultvalue
```

## <a name="property-value"></a>Hodnota vlastnosti

V `Get` proceduře je návratovou hodnotou poskytnut výraz volání jako hodnota vlastnosti.

V `Set` proceduře je nová hodnota vlastnosti předána parametru příkazu `Set`. Pokud explicitně deklarujete parametr, je nutné jej deklarovat se stejným datovým typem jako vlastnost. Pokud parametr nedeklarujete, kompilátor použije implicitní parametr `Value` k reprezentaci nové hodnoty, která má být přiřazena vlastnosti.

## <a name="calling-syntax"></a>Syntaxe volání

Proceduru vlastnosti můžete implicitně vyvolat tak, že vytvoříte odkaz na vlastnost. Název vlastnosti použijete stejným způsobem jako název proměnné, s výjimkou toho, že je nutné zadat hodnoty pro všechny argumenty, které nejsou volitelné, a je třeba uzavřít seznam argumentů v závorkách. Pokud nejsou zadány žádné argumenty, můžete volitelně vynechat závorky.

Syntaxe pro implicitní volání procedury `Set` je následující:

```vb
propertyname[(argumentlist)] = expression
```

Syntaxe pro implicitní volání procedury `Get` je následující:

```vb
lvalue = propertyname[(argumentlist)]
Do While (propertyname[(argumentlist)] > expression)
```

### <a name="illustration-of-declaration-and-call"></a>Ilustrace deklarace a volání

Následující vlastnost uchovává úplný název jako dva názvy prvků, křestní jméno a příjmení. Když volající kód přečte `fullName`, procedura `Get` kombinuje dva názvy prvků a vrátí úplný název. Když volající kód přiřadí nový úplný název, `Set` postup se pokusí ho rozdělit do dvou názvů prvků. Pokud nenalezne žádné místo, uloží ho jako křestní jméno.

[!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]

Následující příklad ukazuje typická volání procedur vlastností `fullName`:

[!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]

## <a name="see-also"></a>Viz také:

- [Procedury](index.md)
- [Procedury funkce](function-procedures.md)
- [Procedury operátoru](operator-procedures.md)
- [Parametry a argumenty procedury](procedure-parameters-and-arguments.md)
- [Rozdíly mezi vlastnostmi a proměnnými v Visual Basic](differences-between-properties-and-variables.md)
- [Postupy: Vytvoření vlastnosti](how-to-create-a-property.md)
- [Postupy: Volání procedury vlastnosti](how-to-call-a-property-procedure.md)
- [Postupy: deklarace a volání výchozí vlastnosti v Visual Basic](how-to-declare-and-call-a-default-property.md)
- [Postupy: Vložení hodnoty do vlastnosti](how-to-put-a-value-in-a-property.md)
- [Postupy: Získání hodnoty z vlastnosti](how-to-get-a-value-from-a-property.md)
