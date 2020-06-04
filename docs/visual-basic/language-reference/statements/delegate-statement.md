---
title: Delegate – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.Delegate
helpviewer_keywords:
- delegate keyword [Visual Basic]
- Delegate statement [Visual Basic]
ms.assetid: f799c518-0817-40cc-ad0b-4da846fdba57
ms.openlocfilehash: 8dec28620b0409f05007b2c0b1c1fd4494c2d7c8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404755"
---
# <a name="delegate-statement"></a>Delegate – příkaz
Slouží k deklaraci delegáta. Delegát je odkazový typ, který odkazuje na `Shared` metodu typu nebo na metodu instance objektu. Pro vytvoření instance této třídy delegáta lze použít jakýkoli postup se shodnými typy parametrů a návratových typů. Postup může být později vyvolán prostřednictvím instance delegáta.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
[ <attrlist> ] [ accessmodifier ] _  
[ Shadows ] Delegate [ Sub | Function ] name [( Of typeparamlist )] [([ parameterlist ])] [ As type ]  
```  
  
## <a name="parts"></a>Součásti  
  
|Pojem|Definice|  
|---|---|  
|`attrlist`|Nepovinný parametr. Seznam atributů, které se vztahují na tohoto delegáta. Více atributů je odděleno čárkami. [Seznam atributů](attribute-list.md) musíte uzavřít do lomených závorek (" `<` " a " `>` ").|  
|`accessmodifier`|Nepovinný parametr. Určuje, který kód má přístup k delegátovi. Může to být jedna z následujících:<br /><br /> - [Veřejné](../modifiers/public.md). Jakýkoli kód, který má přístup k prvku, který deklaruje delegáta, má k němu přístup.<br />-   [Chráněno](../modifiers/protected.md). K němu má přístup pouze kód v rámci třídy delegáta nebo odvozené třídy.<br />-   [Přítel](../modifiers/friend.md). K delegátovi může přistupovat pouze kód v rámci stejného sestavení.<br />- [Soukromá](../modifiers/private.md). K němu má přístup pouze kód v rámci elementu, který deklaruje delegáta.<br /><br /> - [Chráněný přítel](../modifiers/protected-friend.md) K delegátovi mají přístup pouze kód v rámci třídy delegáta, odvozená třída nebo stejné sestavení. <br />- [Soukromé chráněné](../modifiers/private-protected.md) Pouze kód v rámci třídy delegáta nebo v odvozené třídě ve stejném sestavení má přístup k delegátovi. |  
|`Shadows`|Nepovinný parametr. Označuje, že tento delegát předeklaruje a skryje identicky pojmenovaný prvek programování nebo sadu přetížených prvků v základní třídě. Můžete vystínovat jakýkoliv druh deklarovaného prvku s jakýmkoli jiným druhem.<br /><br /> Stínovaný element není k dispozici v odvozené třídě, která ho nastínuje, s výjimkou, kde není k dispozici stínový element. Například pokud `Private` prvek vystínuje element základní třídy, kód, který nemá oprávnění pro přístup k `Private` elementu, přistupuje k elementu základní třídy.|  
|`Sub`|Volitelné, ale `Sub` `Function` musí být buď nebo. Deklaruje tuto proceduru jako delegovanou `Sub` proceduru, která nevrací hodnotu.|  
|`Function`|Volitelné, ale `Sub` `Function` musí být buď nebo. Deklaruje tuto proceduru jako delegovanou `Function` proceduru, která vrací hodnotu.|  
|`name`|Povinná hodnota. Název typu delegáta; Následují standardní zásady vytváření názvů proměnných.|  
|`typeparamlist`|Nepovinný parametr. Seznam parametrů typu pro tohoto delegáta. Vícenásobné parametry typu jsou odděleny čárkami. Volitelně lze každý parametr typu deklarovat jako variant pomocí `In` a `Out` obecných modifikátorů. [Seznam typů](type-list.md) je nutné uzavřít do závorek a uvést ho pomocí `Of` klíčového slova.|  
|`parameterlist`|Nepovinný parametr. Seznam parametrů, které jsou předány proceduře při volání. [Seznam parametrů](parameter-list.md) musí být uzavřen v závorkách.|  
|`type`|Vyžaduje se, pokud zadáte `Function` proceduru. Datový typ návratové hodnoty|  
  
## <a name="remarks"></a>Poznámky  
 `Delegate`Příkaz definuje parametry a návratové typy třídy delegáta. K vytvoření instance této třídy delegáta lze použít jakýkoli postup se shodnými parametry a návratovým typem. Postup lze později vyvolat prostřednictvím instance delegáta voláním metody delegáta `Invoke` .  
  
 Delegáty lze deklarovat na úrovni oboru názvů, modulu, třídy nebo struktury, ale ne v rámci procedury.  
  
 Každá třída delegáta definuje konstruktor, který je předán specifikaci metody objektu. Argument konstruktoru delegáta musí být odkazem na metodu nebo výraz lambda.  
  
 Chcete-li zadat odkaz na metodu, použijte následující syntaxi:  
  
 `AddressOf` [`expression`.]`methodname`  
  
 Typ doby kompilace `expression` musí být název třídy nebo rozhraní, které obsahuje metodu zadaného názvu, jejíž signatura odpovídá signatuře třídy delegáta. `methodname`Může se jednat o sdílenou metodu nebo metodu instance. `methodname`Není volitelná, i když vytvoříte delegáta pro výchozí metodu třídy.  
  
 Chcete-li zadat výraz lambda, použijte následující syntaxi:  
  
 `Function`([ `parm` As `type` , `parm2` as `type2` ,...])`expression`  
  
 Signatura funkce musí odpovídat typu delegáta. Další informace o výrazech lambda naleznete v tématu [lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).  
  
 Další informace o delegátech naleznete v tématu [Delegates](../../programming-guide/language-features/delegates/index.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Delegate` příkaz k deklaraci delegáta pro provoz na dvou číslech a vrácení čísla. `DelegateTest`Metoda přebírá instanci delegáta tohoto typu a používá ho k provozování párů čísel.  
  
 [!code-vb[VbVbalrDelegates#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>Viz také

- [AddressOf – operátor](../operators/addressof-operator.md)
- [Tohoto](of-clause.md)
- [Delegáti](../../programming-guide/language-features/delegates/index.md)
- [Postupy: Použití obecné třídy](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Obecné typy v Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [Kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md)
- [V](../modifiers/in-generic-modifier.md)
- [Mimo](../modifiers/out-generic-modifier.md)
