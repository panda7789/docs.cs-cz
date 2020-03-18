---
title: Přetížení operátoru
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- operators [.NET Framework], overloads
- names [.NET Framework], overloaded operators
- member design guidelines, operators
- overloaded operators
ms.assetid: 37585bf2-4c27-4dee-849a-af70e3338cc1
ms.openlocfilehash: 0999e94c8d77396b237522e89c51206ce1226718
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400566"
---
# <a name="operator-overloads"></a>Přetížení operátoru
Přetížení operátorů umožňují, aby se typy architektury zobrazovaly, jako by byly předdefinované jazykové primitivy.

 Ačkoli povolené a užitečné v některých situacích, přetížení operátoru by měly být používány opatrně. Existuje mnoho případů, ve kterých bylo zneužito přetížení operátoru, například když návrháři architektury začali používat operátory pro operace, které by měly být jednoduché metody. Následující pokyny by vám měly pomoci rozhodnout, kdy a jak používat přetížení operátoru.

 ❌Vyhněte se definování přetížení operátoru, s výjimkou typů, které by se měly cítit jako primitivní (vestavěné) typy.

 ✔️ zvážit definování přetížení operátoru v typu, který by se měl cítit jako primitivní typ.

 Například <xref:System.String?displayProperty=nameWithType> má `operator==` `operator!=` a definována.

 ✔️ do definovat přetížení operátoru ve strukturách, <xref:System.Decimal?displayProperty=nameWithType>které představují čísla (například ).

 ❌Nebuďte roztomilí při definování přetížení operátoru.

 Přetížení operátoru je užitečné v případech, kdy je okamžitě zřejmé, jaký bude výsledek operace. Například má smysl, aby bylo možné <xref:System.DateTime> odečíst jeden od druhého `DateTime` a získat <xref:System.TimeSpan>. Není však vhodné použít operátor logického sjednocení k sjednocení dvou databázových dotazů nebo k zápisu do datového proudu pomocí operátoru shift.

 ❌NEPOSKYTUJÍ operátor přetížení, pokud alespoň jeden z operandů je typu definující přetížení.

 ✔️ operátory přetížení do symetrickým způsobem.

 Například pokud přetížení `operator==`, měli byste `operator!=`také přetížení . Podobně pokud přetížení `operator<`, měli byste také `operator>`přetížení , a tak dále.

 ✔️ zvažte poskytování metod s popisnými názvy, které odpovídají každému přetíženému operátoru.

 Mnoho jazyků nepodporuje přetížení operátoru. Z tohoto důvodu se doporučuje, aby typy operátorů přetížení obsahovat sekundární metodu s odpovídající název specifické pro doménu, který poskytuje ekvivalentní funkce.

 Následující tabulka obsahuje seznam operátorů a odpovídající popisné názvy metod.

|Symbol operátora Jazyka C#|Název metadat|Popisný název|
|-------------------------|-------------------|-------------------|
|`N/A`|`op_Implicit`|`To<TypeName>/From<TypeName>`|
|`N/A`|`op_Explicit`|`To<TypeName>/From<TypeName>`|
|`+ (binary)`|`op_Addition`|`Add`|
|`- (binary)`|`op_Subtraction`|`Subtract`|
|`* (binary)`|`op_Multiply`|`Multiply`|
|`/`|`op_Division`|`Divide`|
|`%`|`op_Modulus`|`Mod or Remainder`|
|`^`|`op_ExclusiveOr`|`Xor`|
|`& (binary)`|`op_BitwiseAnd`|`BitwiseAnd`|
|<code>&#124;</code>|`op_BitwiseOr`|`BitwiseOr`|
|`&&`|`op_LogicalAnd`|`And`|
|<code>&#124;&#124;</code>|`op_LogicalOr`|`Or`|
|`=`|`op_Assign`|`Assign`|
|`<<`|`op_LeftShift`|`LeftShift`|
|`>>`|`op_RightShift`|`RightShift`|
|`N/A`|`op_SignedRightShift`|`SignedRightShift`|
|`N/A`|`op_UnsignedRightShift`|`UnsignedRightShift`|
|`==`|`op_Equality`|`Equals`|
|`!=`|`op_Inequality`|`Equals`|
|`>`|`op_GreaterThan`|`CompareTo`|
|`<`|`op_LessThan`|`CompareTo`|
|`>=`|`op_GreaterThanOrEqual`|`CompareTo`|
|`<=`|`op_LessThanOrEqual`|`CompareTo`|
|`*=`|`op_MultiplicationAssignment`|`Multiply`|
|`-=`|`op_SubtractionAssignment`|`Subtract`|
|`^=`|`op_ExclusiveOrAssignment`|`Xor`|
|`<<=`|`op_LeftShiftAssignment`|`LeftShift`|
|`%=`|`op_ModulusAssignment`|`Mod`|
|`+=`|`op_AdditionAssignment`|`Add`|
|`&=`|`op_BitwiseAndAssignment`|`BitwiseAnd`|
|<code>&#124;=</code>|`op_BitwiseOrAssignment`|`BitwiseOr`|
|`,`|`op_Comma`|`Comma`|
|`/=`|`op_DivisionAssignment`|`Divide`|
|`--`|`op_Decrement`|`Decrement`|
|`++`|`op_Increment`|`Increment`|
|`- (unary)`|`op_UnaryNegation`|`Negate`|
|`+ (unary)`|`op_UnaryPlus`|`Plus`|
|`~`|`op_OnesComplement`|`OnesComplement`|

### <a name="overloading-operator-"></a>Operátor přetížení ==
 Přetížení `operator ==` je poměrně komplikované. Sémantiku operátora musí být kompatibilní s několika <xref:System.Object.Equals%2A?displayProperty=nameWithType>dalšími členy, například .

### <a name="conversion-operators"></a>Operátory převodu
 Operátory převodu jsou unární operátory, které umožňují převod z jednoho typu na jiný. Operátory musí být definovány jako statické členy na operandu nebo návratového typu. Existují dva typy operátorů převodu: implicitní a explicitní.

 ❌Neposkytujte operátor převodu, pokud takový převod není jasně očekáván koncovými uživateli.

 ❌NEDEFINUJTE operátory převodu mimo doménu typu.

 Například <xref:System.Int32>, <xref:System.Double>, <xref:System.Decimal> a jsou všechny <xref:System.DateTime> číselné typy, vzhledem k tomu, že není. Proto by měl být žádný operátor `Double(long)` převodu převést na `DateTime`. Konstruktor je upřednostňován v takovém případě.

 ❌NEPOSKYTUJÍ implicitní operátor převodu, pokud převod je potenciálně ztrátové.

 Například by neměl být implicitní `Double` `Int32` převod `Double` z do, `Int32`protože má širší rozsah než . Explicitní operátor převodu může být poskytnuta i v případě, že převod je potenciálně ztrátové.

 ❌NEVYVOLÁVAT výjimky z implicitní přetypáže.

 Pro koncové uživatele je velmi obtížné pochopit, co se děje, protože si nemusí být vědomi, že probíhá převod.

 ✔️ DO <xref:System.InvalidCastException?displayProperty=nameWithType> throw, pokud volání operátoru přetypovacího vysílání vede ke ztrátovému převodu a smlouva operátoru neumožňuje ztrátové převody.

 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

 *Přetištěno se svolením Pearson Education, Inc. z [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také

- [Pokyny k návrhu člena](../../../docs/standard/design-guidelines/member.md)
- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
