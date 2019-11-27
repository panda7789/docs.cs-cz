---
title: Delegate – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.Delegate
helpviewer_keywords:
- delegate keyword [Visual Basic]
- Delegate statement [Visual Basic]
ms.assetid: f799c518-0817-40cc-ad0b-4da846fdba57
ms.openlocfilehash: 662d2c3c0767adfe406e0a6f1b1e6dccd704e795
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354078"
---
# <a name="delegate-statement"></a>Delegate – příkaz
Slouží k deklaraci delegáta. Delegát je odkazový typ, který odkazuje na metodu `Shared` typu nebo na metodu instance objektu. Pro vytvoření instance této třídy delegáta lze použít jakýkoli postup se shodnými typy parametrů a návratových typů. Postup může být později vyvolán prostřednictvím instance delegáta.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
[ <attrlist> ] [ accessmodifier ] _  
[ Shadows ] Delegate [ Sub | Function ] name [( Of typeparamlist )] [([ parameterlist ])] [ As type ]  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`attrlist`|Volitelná. Seznam atributů, které se vztahují na tohoto delegáta. Více atributů je odděleno čárkami. [Seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md) je nutné uzavřít do lomených závorek ("`<`" a "`>`").|  
|`accessmodifier`|Volitelná. Určuje, který kód má přístup k delegátovi. Může být jedna z následujících akcí:<br /><br /> - [veřejné](../../../visual-basic/language-reference/modifiers/public.md). Jakýkoli kód, který má přístup k prvku, který deklaruje delegáta, má k němu přístup.<br />-   [chráněno](../../../visual-basic/language-reference/modifiers/protected.md). K němu má přístup pouze kód v rámci třídy delegáta nebo odvozené třídy.<br />-   [přítele](../../../visual-basic/language-reference/modifiers/friend.md). K delegátovi může přistupovat pouze kód v rámci stejného sestavení.<br />- [privátní](../../../visual-basic/language-reference/modifiers/private.md). K němu má přístup pouze kód v rámci elementu, který deklaruje delegáta.<br /><br /> k delegátovi mají přístup pouze kód, který je v rámci třídy delegáta - [chráněný](../../language-reference/modifiers/protected-friend.md) jenom v rámci odvozené třídy nebo stejného sestavení. <br />k delegátovi mají přístup pouze kód, který je v rámci třídy delegáta nebo v odvozené třídě ve stejném sestavení - pouze [soukromým chráněným](../../language-reference/modifiers/private-protected.md) kódem. |  
|`Shadows`|Volitelná. Označuje, že tento delegát předeklaruje a skryje identicky pojmenovaný prvek programování nebo sadu přetížených prvků v základní třídě. Můžete vystínovat jakýkoliv druh deklarovaného prvku s jakýmkoli jiným druhem.<br /><br /> Stínovaný element není k dispozici v odvozené třídě, která ho nastínuje, s výjimkou, kde není k dispozici stínový element. Například pokud `Private` element stínování elementu základní třídy, kód, který nemá oprávnění pro přístup k `Private` elementu, přistupuje k elementu základní třídy místo toho.|  
|`Sub`|Volitelné, ale musí se zobrazit buď `Sub`, nebo `Function`. Deklaruje tuto proceduru jako delegáta `Sub` proceduru, která nevrací hodnotu.|  
|`Function`|Volitelné, ale musí se zobrazit buď `Sub`, nebo `Function`. Deklaruje tuto proceduru jako delegáta `Function` proceduru, která vrací hodnotu.|  
|`name`|Požadováno. Název typu delegáta; Následují standardní zásady vytváření názvů proměnných.|  
|`typeparamlist`|Volitelná. Seznam parametrů typu pro tohoto delegáta. Vícenásobné parametry typu jsou odděleny čárkami. Volitelně lze každý parametr typu deklarovat jako typ variant pomocí `In` a `Out` obecných modifikátorů. [Seznam typů](../../../visual-basic/language-reference/statements/type-list.md) musíte uzavřít do závorek a vložit ho pomocí klíčového slova `Of`.|  
|`parameterlist`|Volitelná. Seznam parametrů, které jsou předány proceduře při volání. [Seznam parametrů](../../../visual-basic/language-reference/statements/parameter-list.md) musí být uzavřen v závorkách.|  
|`type`|Vyžaduje se, pokud zadáte proceduru `Function`. Datový typ návratové hodnoty|  
  
## <a name="remarks"></a>Poznámky  
 Příkaz `Delegate` definuje parametry a návratové typy třídy delegáta. K vytvoření instance této třídy delegáta lze použít jakýkoli postup se shodnými parametry a návratovým typem. Postup lze později vyvolat prostřednictvím instance delegáta voláním metody `Invoke` delegáta.  
  
 Delegáty lze deklarovat na úrovni oboru názvů, modulu, třídy nebo struktury, ale ne v rámci procedury.  
  
 Každá třída delegáta definuje konstruktor, který je předán specifikaci metody objektu. Argument konstruktoru delegáta musí být odkazem na metodu nebo výraz lambda.  
  
 Chcete-li zadat odkaz na metodu, použijte následující syntaxi:  
  
 `AddressOf` [`expression`.]`methodname`  
  
 Typ doby kompilace `expression` musí být název třídy nebo rozhraní, které obsahuje metodu zadaného názvu, jejíž signatura odpovídá signatuře třídy Delegate. `methodname` může být buď sdílená metoda, nebo metoda instance. `methodname` není volitelná, i když vytvoříte delegáta pro výchozí metodu třídy.  
  
 Chcete-li zadat výraz lambda, použijte následující syntaxi:  
  
 `Function` ([`parm` as `type``parm2` jako `type2`,...]) `expression`  
  
 Signatura funkce musí odpovídat typu delegáta. Další informace o výrazech lambda naleznete v tématu [lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 Další informace o delegátech naleznete v tématu [Delegates](../../../visual-basic/programming-guide/language-features/delegates/index.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá příkaz `Delegate` k deklaraci delegáta pro provoz na dvou číslech a vrácení čísla. Metoda `DelegateTest` přebírá instanci delegáta tohoto typu a používá ho k provozování párů čísel.  
  
 [!code-vb[VbVbalrDelegates#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>Viz také:

- [Operátor AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Tohoto](../../../visual-basic/language-reference/statements/of-clause.md)
- [Delegáti](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Postupy: Použití obecné třídy](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Obecné typy v Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md)
- [Pro](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [Mimo](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
