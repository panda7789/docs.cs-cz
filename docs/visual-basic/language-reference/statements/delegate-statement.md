---
title: Delegate – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Delegate
helpviewer_keywords:
- delegate keyword [Visual Basic]
- Delegate statement [Visual Basic]
ms.assetid: f799c518-0817-40cc-ad0b-4da846fdba57
ms.openlocfilehash: 4718c0a6e332d644a7f54c79246df95f841058d0
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2018
ms.locfileid: "43258480"
---
# <a name="delegate-statement"></a>Delegate – příkaz
Slouží k deklaraci delegáta. Delegát je typ odkazu, který odkazuje `Shared` metodu typu nebo metodě instance objektu. Všechny procedury s parametry a návratovým typem odpovídajícím lze použít k vytvoření instance této třídy delegáta. Postup lze poté později vyvolat prostřednictvím instance delegátu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ <attrlist> ] [ accessmodifier ] _  
[ Shadows ] Delegate [ Sub | Function ] name [( Of typeparamlist )] [([ parameterlist ])] [ As type ]  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`attrlist`|Volitelné. Seznam atributů, které platí pro tohoto delegáta. Více atributů jsou odděleny čárkami. Je nutné uzavřít [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md) v lomených závorkách ("`<`"a"`>`").|  
|`accessmodifier`|Volitelné. Určuje, jaký kód může přistupovat k delegáta. Může být jedna z následujících akcí:<br /><br /> - [Veřejné](../../../visual-basic/language-reference/modifiers/public.md). Veškerý kód, který může přistupovat k elementu, který deklaruje delegáta k němu přístup.<br />-   [Chráněné](../../../visual-basic/language-reference/modifiers/protected.md). Pouze kód uvnitř třídy delegáta nebo odvozené třídy k němu přístup.<br />-   [Friend –](../../../visual-basic/language-reference/modifiers/friend.md). Pouze kód v rámci stejného sestavení můžete přistupovat k delegátu.<br />- [Privátní](../../../visual-basic/language-reference/modifiers/private.md). Pouze kód v rámci elementu, který deklaruje delegáta k němu přístup.<br /><br /> - [Protected Friend](../../language-reference/modifiers/protected-friend.md) pouze kód uvnitř třídy delegáta, odvozené třídy nebo stejného sestavení můžete přistupovat k delegáta. <br />- [Privátní chráněné](../../language-reference/modifiers/private-protected.md) pouze kód v rámci třídy delegáta nebo v odvozené třídě ve stejném sestavení můžete přistupovat k delegátu. |  
|`Shadows`|Volitelné. Označuje, že tento delegát znovu deklaruje a skryje identicky pojmenovanou programovací prvek, nebo sadu přetížených elementů v základní třídě. Můžete stínové jakýkoli druh element deklarovaný pomocí jakéhokoli druhu.<br /><br /> Stínovaný element je k dispozici v rámci odvozené třídy, která zastiňuje, s výjimkou z kde stínového provozu prvek je přístupný. Například pokud `Private` element zastiňuje prvek základní třídy, kód, který nemá oprávnění k přístupu `Private` element má přístup k elementu základní třídy místo toho.|  
|`Sub`|Volitelné, ale buď `Sub` nebo `Function` musí být uvedena. Deklaruje tento postup jako delegát `Sub` proceduru, která nevrací hodnotu.|  
|`Function`|Volitelné, ale buď `Sub` nebo `Function` musí být uvedena. Deklaruje tento postup jako delegát `Function` proceduru, která vrací hodnotu.|  
|`name`|Požadováno. Název typu delegáta; splňuje standardní zásady vytváření názvů proměnných.|  
|`typeparamlist`|Volitelné. Seznam parametrů typu pro tohoto delegáta. Více typy parametrů jsou odděleny čárkami. Volitelně můžete každý parametr typu lze deklarovat typ variant pomocí `In` a `Out` obecných parametrů. Je nutné uzavřít [seznam typů](../../../visual-basic/language-reference/statements/type-list.md) v závorkách a zavést ji `Of` – klíčové slovo.|  
|`parameterlist`|Volitelné. Seznam parametrů, které jsou předány na postup, když je volána. Je nutné uzavřít [seznam parametrů](../../../visual-basic/language-reference/statements/parameter-list.md) v závorkách.|  
|`type`|Povinné, pokud zadáte `Function` postup. Datový typ vrácené hodnoty.|  
  
## <a name="remarks"></a>Poznámky  
 `Delegate` Prohlášení definuje parametry a návratovým typem třídy delegáta. Všechny procedury s odpovídající parametry a návratové typy lze použít k vytvoření instance této třídy delegáta. Postup lze poté později vyvolat prostřednictvím instance delegátu po zavolání delegáta `Invoke` metody.  
  
 Delegáty lze deklarovat v oboru názvů, modulu, třídy nebo struktury úroveň, ale ne v rámci procedury.  
  
 Každá třída delegáta je definován konstruktor, který je předán specifikace metodu objektu. Argument pro konstruktor delegate musí být odkaz na metodu nebo výraz lambda.  
  
 Pokud chcete zadat odkaz na metodu, použijte následující syntaxi:  
  
 `AddressOf` [`expression`.]`methodname`  
  
 Typ kompilace `expression` musí být názvem třídy nebo rozhraní, které obsahuje metodu se zadaným názvem, jehož předpis shoduje se signaturou třídy delegáta. `methodname` Může být buď sdílené metody nebo metodu instance. `methodname` Není volitelný, i v případě vytvoření delegáta pro výchozí metodu třídy.  
  
 Pokud chcete zadat výraz lambda, použijte následující syntaxi:  
  
 `Function` ([`parm` Jako `type`, `parm2` jako `type2`;...]) `expression`  
  
 Signatura funkce musí odpovídat typu delegátu. Další informace o výrazech lambda naleznete v tématu [výrazy Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 Další informace o delegátech naleznete v tématu [delegáti](../../../visual-basic/programming-guide/language-features/delegates/index.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Delegate` příkaz deklarovat delegáta pro účely provozování na dvou čísel a vrátí číslo. `DelegateTest` Metoda použije instanci tohoto typu delegáta a použije ho k pracovat s páry čísel.  
  
 [!code-vb[VbVbalrDelegates#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegate-statement_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Operátor AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [z](../../../visual-basic/language-reference/statements/of-clause.md)  
 [Delegáti](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Postupy: Použití obecné třídy](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [Obecné typy v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md)  
 [V](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)  
 [navýšení kapacity](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
