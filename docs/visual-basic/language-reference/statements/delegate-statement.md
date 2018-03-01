---
title: "Delegate – příkaz"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Delegate
helpviewer_keywords:
- delegate keyword [Visual Basic]
- Delegate statement [Visual Basic]
ms.assetid: f799c518-0817-40cc-ad0b-4da846fdba57
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7e79a261f74cbc7aa067af63629e31bedf65d163
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="delegate-statement"></a>Delegate – příkaz
Používá k deklaraci delegáta. Delegát je odkaz na typ, který odkazuje `Shared` metoda typu nebo metodu instance objektu. Všechny postup s odpovídajícími typy parametrů a vraťte se může použít k vytvoření instance této třídy delegáta. Postup lze poté později vyvolat prostřednictvím instanci delegáta.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ <attrlist> ] [ accessmodifier ] _  
[ Shadows ] Delegate [ Sub | Function ] name [( Of typeparamlist )] [([ parameterlist ])] [ As type ]  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`attrlist`|Volitelné. Seznam atributů, které platí pro tohoto delegáta. Více atributů jsou oddělené čárkami. Je nutné uzavřít [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md) v lomených závorkách ("`<`"a"`>`").|  
|`accessmodifier`|Volitelné. Určuje, jaký kód můžete přístup delegáta. Může být jedna z následujících akcí:<br /><br /> -   [Veřejné](../../../visual-basic/language-reference/modifiers/public.md). Kód, který můžete získat přístup k elementu, který deklaruje delegáta k němu přístup.<br />-   [Chráněné](../../../visual-basic/language-reference/modifiers/protected.md). Pouze kódu v rámci tohoto delegáta nebo odvozená třída k němu přístup.<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md). Pouze kód v rámci stejného sestavení může přistupovat delegát.<br />-   [Privátní](../../../visual-basic/language-reference/modifiers/private.md). Jenom kód v rámci elementu, který deklaruje delegáta k němu přístup.<br /><br /> Můžete zadat `Protected Friend` pro povolení přístupu z kódu v rámci tohoto delegáta třídu, odvozené třídě nebo do stejného sestavení.|  
|`Shadows`|Volitelné. Označuje, že tento delegát redeclares a skryje stejně jako s názvem programovací prvek, nebo sadu přetížené elementů v základní třídě. Můžete stínové jakýkoli druh deklarovaný element s jakéhokoli jiného typu.<br /><br /> Element stíněné je k dispozici v rámci odvozené třídy, stín, s výjimkou z kde element stínového provozu je nedostupná. Například pokud `Private` element shadows prvku základní třídy, kód, který nemá oprávnění k přístupu `Private` element přistupuje k prvku základní třídy místo.|  
|`Sub`|Volitelné, ale buď `Sub` nebo `Function` musí zobrazit. Tento postup jako delegáta deklaruje `Sub` procedury, která nevrátí hodnotu.|  
|`Function`|Volitelné, ale buď `Sub` nebo `Function` musí zobrazit. Tento postup jako delegáta deklaruje `Function` procedury, která vrátí hodnotu.|  
|`name`|Požadováno. Název typu delegáta; dodržovat standardní zásady vytváření názvů proměnných.|  
|`typeparamlist`|Volitelné. Seznam parametrů typu pro tohoto delegáta. Několik parametrů typu jsou oddělené čárkami. Volitelně můžete každý parametr typu lze deklarovat variant pomocí `In` a `Out` obecné modifikátory. Je nutné uzavřít [seznam typů](../../../visual-basic/language-reference/statements/type-list.md) v závorkách a její znamenat `Of` – klíčové slovo.|  
|`parameterlist`|Volitelné. Seznam parametrů, které se budou předávat procesu při jejím volání. Je nutné uzavřít [seznam parametrů](../../../visual-basic/language-reference/statements/parameter-list.md) v závorkách.|  
|`type`|Pokud zadáte požadované `Function` postupu. Datový typ vrácené hodnoty.|  
  
## <a name="remarks"></a>Poznámky  
 `Delegate` Příkaz definuje parametr a návratové typy delegát třídy. Libovolná procedura s odpovídající parametry a návratové typy slouží k vytvoření instance této třídy delegáta. Postup můžete pak později vyvolat prostřednictvím instanci delegáta volání metody delegáta `Invoke` metoda.  
  
 Delegáti lze deklarovat na obor názvů, modulu, třídu nebo strukturu úroveň, ale není v rámci procedury.  
  
 Každá třída delegáta definuje konstruktor, který je předán specifikace metodu objektu. Argument pro konstruktor delegáta musí být odkaz na metodu nebo výrazu lambda.  
  
 Pokud chcete zadat odkaz na metodu, použijte následující syntaxi:  
  
 `AddressOf` [`expression`.]`methodname`  
  
 Typ kompilaci `expression` musí být název třídy nebo rozhraní, které obsahuje metodu pro zadaný název, jejichž podpis odpovídá podpis delegát třídy. `methodname` Může být buď sdílené metody nebo metodu instance. `methodname` Je povinný, i v případě, že vytvoříte delegáta pro metodu výchozí třídy.  
  
 Pokud chcete zadat výrazu lambda, použijte následující syntaxi:  
  
 `Function`([`parm` Jako `type`, `parm2` jako `type2`,...])`expression`  
  
 Podpis funkce musí odpovídat typu delegáta. Další informace o výrazy lambda najdete v tématu [výrazy Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 Další informace o delegáti najdete v tématu [delegáti](../../../visual-basic/programming-guide/language-features/delegates/index.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Delegate` příkaz deklarovat delegáta pro provoz na dvou čísel a vrátí číslo. `DelegateTest` Metoda přebírá instanci delegáta tohoto typu a používá ho k provozu na páry čísel.  
  
 [!code-vb[VbVbalrDelegates#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegate-statement_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [AddressOf – operátor](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Z](../../../visual-basic/language-reference/statements/of-clause.md)  
 [Delegáti](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Postupy: použití obecné třídy](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [Obecné typy v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md)  
 [V](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)  
 [Na více systémů](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
