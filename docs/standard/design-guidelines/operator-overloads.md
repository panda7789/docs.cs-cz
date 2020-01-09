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
ms.openlocfilehash: 4cea3c17de40a873d977223f36b6dcef4f2c2d78
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709137"
---
# <a name="operator-overloads"></a>Přetížení operátoru
Přetížení operátorů umožňují, aby se typy rozhraní zobrazovaly, jako kdyby byly předdefinované jazykové primitivy.  
  
 I když je v některých situacích povolená a užitečná, je nutné přetížení operátorů používat obezřetně. Existuje mnoho případů, ve kterých je přetížení operátoru zneužití, například když návrháři architektury začali používat operátory pro operace, které by měly být jednoduché metody. Následující pokyny by vám měly pomáhat při rozhodování, kdy a jak používat přetížení operátoru.  
  
 **X AVOID** definování přetížení operátoru v typy, které by měl působí jako primitivní typy (Předdefinované).  
  
 **✓ CONSIDER** definování přetížení operátoru v typu, který by měl působí jako primitivního typu.  
  
 Například <xref:System.String?displayProperty=nameWithType> má definováno `operator==` a `operator!=`.  
  
 **✓ DO** v struktury, která představují čísla definovat přetížení operátoru (například <xref:System.Decimal?displayProperty=nameWithType>).  
  
 **X DO NOT** být cute při definování přetížení operátoru.  
  
 Přetížení operátoru je užitečné v případech, kdy je okamžitě zřejmé, jaký výsledek operace bude. Je například vhodné, aby bylo možné odečíst jednu <xref:System.DateTime> z jiného `DateTime` a získat <xref:System.TimeSpan>. Není však vhodné použít operátor logického sjednocení pro sjednocení dvou databázových dotazů nebo k zápisu do datového proudu pomocí operátoru Shift.  
  
 **X DO NOT** zadejte operátor přetížení pokud alespoň jeden z operandy typu definování přetížení.  
  
 **✓ DO** přetížení operátory symetrický způsobem.  
  
 Například Pokud převedete `operator==`, měli byste také přetížit `operator!=`. Podobně pokud převedete `operator<`, měli byste také přetížit `operator>`a tak dále.  
  
 **✓ CONSIDER** poskytování metody popisné názvy, které odpovídají každé přetížené operátor.  
  
 Mnoho jazyků nepodporuje přetížení operátorů. Z tohoto důvodu se doporučuje, aby typy, které přetěžují operátory obsahují sekundární metodu s vhodným názvem domény, který poskytuje ekvivalentní funkce.  
  
 Následující tabulka obsahuje seznam operátorů a odpovídající popisné názvy metod.  
  
|C#Symbol operátoru|Název metadat|Popisný název|  
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
  
### <a name="overloading-operator-"></a>Operátor přetížení = =  
 Přetížení `operator ==` je poměrně komplikované. Sémantika operátoru musí být kompatibilní s několika ostatními členy, například <xref:System.Object.Equals%2A?displayProperty=nameWithType>.  
  
### <a name="conversion-operators"></a>Operátory převodu  
 Operátory převodu jsou unární operátory, které umožňují převod z jednoho typu na jiný. Operátory musí být definovány jako statické členy buď na operandu, nebo na návratový typ. Existují dva typy operátorů převodu: implicitní a explicitní.  
  
 **X DO NOT** operátora převodu může poskytovat, pokud takový převod neočekává jasně koncoví uživatelé.  
  
 **X DO NOT** definovat operátory převodu mimo typ domény.  
  
 Například <xref:System.Int32>, <xref:System.Double>a <xref:System.Decimal> jsou všechny číselné typy, zatímco <xref:System.DateTime> ne. Proto by neměl existovat žádný operátor převodu k převedení `Double(long)` na `DateTime`. V takovém případě je upřednostňován konstruktor.  
  
 **X DO NOT** zadat operátor implicitní převod, pokud převod potenciálně míru ztrát.  
  
 Například by neměl být implicitní převod z `Double` na `Int32`, protože `Double` má širší rozsah než `Int32`. Explicitní operátor převodu lze zadat i v případě, že je převod potenciálně ztrátný.  
  
 **X DO NOT** vyvolat výjimky z implicitní přetypování.  
  
 Koncovým uživatelům je velmi obtížné pochopit, co se děje, protože nemusí vědět, že probíhá převod.  
  
 **✓ DO** throw <xref:System.InvalidCastException?displayProperty=nameWithType> Pokud volání operátor přetypování výsledkem míru ztrát převod a kontrakt operátoru neumožňuje míru ztrát převody.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu člena](../../../docs/standard/design-guidelines/member.md)
- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
