---
title: Přetížení operátoru
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- operators [.NET Framework], overloads
- names [.NET Framework], overloaded operators
- member design guidelines, operators
- overloaded operators
ms.assetid: 37585bf2-4c27-4dee-849a-af70e3338cc1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 747fc21aceae60e362c72391ae265e45d6f8445f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579304"
---
# <a name="operator-overloads"></a>Přetížení operátoru
Přetížení operátoru povolit framework typy zobrazí, jako by byly primitiv předdefinované jazyka.  
  
 I když je povolené a užitečné v některých situacích Ano, je třeba přetížení operátoru použít opatrně. Existují mnoho případy, ve které operátor přetížení má byla zneužít, například při spuštění framework návrhářů, chcete-li používat pro operace, které by měly být jednoduché metody. Následující pokyny by měly pomoci při rozhodování, kdy a jak použití přetížení operátoru.  
  
 **X nepoužívejte** definování přetížení operátoru v typy, které by měl působí jako primitivní typy (Předdefinované).  
  
 **✓ ZVAŽTE** definování přetížení operátoru v typu, který by měl působí jako primitivního typu.  
  
 Například <xref:System.String?displayProperty=nameWithType> má `operator==` a `operator!=` definované.  
  
 **PROVEĎTE ✓** v struktury, která představují čísla definovat přetížení operátoru (například <xref:System.Decimal?displayProperty=nameWithType>).  
  
 **X nesmí** být cute při definování přetížení operátoru.  
  
 Přetížení operátoru je užitečné v případech, ve kterých je hned zjevné co bude výsledek operace. Například má smysl moct odečtena jeden <xref:System.DateTime> z jiné `DateTime` a získat <xref:System.TimeSpan>. Však není vhodné používat logický operátor union, union dotazy dvě databáze nebo použít operátor posunutí k zápisu do datového proudu.  
  
 **X nesmí** zadejte operátor přetížení pokud alespoň jeden z operandy typu definování přetížení.  
  
 **PROVEĎTE ✓** přetížení operátory symetrický způsobem.  
  
 Například, pokud jste přetížení `operator==`, by také přetížení `operator!=`. Podobně pokud jste přetížení `operator<`, by také přetížení `operator>`a tak dále.  
  
 **✓ ZVAŽTE** poskytování metody popisné názvy, které odpovídají každé přetížené operátor.  
  
 Mnoho jazyků nepodporují přetížení operátoru. Z tohoto důvodu se doporučuje, aby typy, které přetížení operátory o sekundární metodu s názvem příslušné specifické pro doménu, která poskytuje ekvivalentní funkci.  
  
 Následující tabulka obsahuje seznam operátory a odpovídající metoda popisné názvy.  
  
|Symbol operátoru jazyka C#|Název metadat|Popisný název|  
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
  
### <a name="overloading-operator-"></a>Přetížení operátoru ==  
 Přetížení `operator ==` je poměrně složitá. Sémantika operátor musí být kompatibilní s několika jinými členy, jako například <xref:System.Object.Equals%2A?displayProperty=nameWithType>.  
  
### <a name="conversion-operators"></a>Operátory převodu  
 Operátory převodu jsou unární operátory, které umožňují převod z jednoho typu. Operátory musí být definován jako statické členy na operand nebo návratový typ. Existují dva typy operátory převodu: implicitní a explicitní.  
  
 **X nesmí** operátora převodu může poskytovat, pokud takový převod neočekává jasně koncoví uživatelé.  
  
 **X nesmí** definovat operátory převodu mimo typ domény.  
  
 Například <xref:System.Int32>, <xref:System.Double>, a <xref:System.Decimal> jsou všechny číselné typy, zatímco <xref:System.DateTime> není. Proto, měla by existovat žádné operátor převodu převést `Double(long)` k `DateTime`. V takovém případě je upřednostňovaný konstruktor.  
  
 **X nesmí** zadat operátor implicitní převod, pokud převod potenciálně míru ztrát.  
  
 Například by nemělo být ke implicitní převod z `Double` k `Int32` protože `Double` má více typů než `Int32`. Explicitní převod operátor lze zadat, i když je převod potenciálně míru ztrát.  
  
 **X nesmí** vyvolat výjimky z implicitní přetypování.  
  
 Je velmi obtížné koncovým uživatelům pochopit, co se děje, protože mohou být vědět, Probíhá převod.  
  
 **PROVEĎTE ✓** throw <xref:System.InvalidCastException?displayProperty=nameWithType> Pokud volání operátor přetypování výsledkem míru ztrát převod a kontrakt operátoru neumožňuje míru ztrát převody.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Pokyny k návrhu člena](../../../docs/standard/design-guidelines/member.md)  
 [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
