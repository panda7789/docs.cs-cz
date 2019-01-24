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
author: KrzysztofCwalina
ms.openlocfilehash: 441dc2777cd8d221300c526b6b31a647af60ca71
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646575"
---
# <a name="operator-overloads"></a>Přetížení operátoru
Přetížení operátoru povolit rozhraní framework typy zobrazení, jako kdyby byly integrované primitivní.  
  
 I když je povolený a v některých situacích užitečné, je třeba přetížení operátoru použít opatrně. Jsou většinou v operátoru přetížení má byla zneužít, jako je například při spuštění návrháře framework použití operátorů pro operace, které by měly být jednoduché metody. Následující pokyny vám by měly pomoci při rozhodování, kdy a jak použití přetížení operátoru.  
  
 **X AVOID** definování přetížení operátoru v typy, které by měl působí jako primitivní typy (Předdefinované).  
  
 **✓ CONSIDER** definování přetížení operátoru v typu, který by měl působí jako primitivního typu.  
  
 Například <xref:System.String?displayProperty=nameWithType> má `operator==` a `operator!=` definované.  
  
 **✓ DO** v struktury, která představují čísla definovat přetížení operátoru (například <xref:System.Decimal?displayProperty=nameWithType>).  
  
 **X DO NOT** být cute při definování přetížení operátoru.  
  
 Přetížení operátoru je užitečné v případech, ve kterých je okamžitě zřejmý co se bude výsledek operace. Například smysl mít odečíst jeden <xref:System.DateTime> z jiného `DateTime` a získat <xref:System.TimeSpan>. Není však vhodné pomocí logického operátoru sjednocení pro sjednocení dvou databázové dotazy nebo operátor posunutí slouží k zápisu do datového proudu.  
  
 **X DO NOT** zadejte operátor přetížení pokud alespoň jeden z operandy typu definování přetížení.  
  
 **✓ DO** přetížení operátory symetrický způsobem.  
  
 Například, pokud přetížíte `operator==`, byste měli také přetížit `operator!=`. Podobně pokud přetížíte `operator<`, byste měli také přetížit `operator>`, a tak dále.  
  
 **✓ CONSIDER** poskytování metody popisné názvy, které odpovídají každé přetížené operátor.  
  
 Řadu jiných jazyků nepodporují přetížení operátoru. Z tohoto důvodu se doporučuje, typy, které přetěžují operátory zahrnují sekundární metodu s vhodný název specifického pro doménu, která obsahuje ekvivalentní funkce.  
  
 Následující tabulka obsahuje seznam operátorů a odpovídající názvy metod popisný.  
  
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
 Přetížení `operator ==` je poměrně složitý. Sémantika operátoru musí být kompatibilní s několika jinými členy jako <xref:System.Object.Equals%2A?displayProperty=nameWithType>.  
  
### <a name="conversion-operators"></a>Operátory převodu  
 Operátory převodu jsou unární operátory, které umožňují převod jednoho typu na jiný. Operátory musí být definovány jako statické členy v operandu nebo návratového typu. Existují dva typy operátorů převodu: implicitní a explicitní.  
  
 **X DO NOT** operátora převodu může poskytovat, pokud takový převod neočekává jasně koncoví uživatelé.  
  
 **X DO NOT** definovat operátory převodu mimo typ domény.  
  
 Například <xref:System.Int32>, <xref:System.Double>, a <xref:System.Decimal> jsou všechny číselné typy, zatímco <xref:System.DateTime> není. Proto by měl existovat žádný operátor převodu k převedení `Double(long)` k `DateTime`. V takovém případě se upřednostňuje konstruktor.  
  
 **X DO NOT** zadat operátor implicitní převod, pokud převod potenciálně míru ztrát.  
  
 Například by neměla existovat implicitní převod z `Double` k `Int32` protože `Double` má širší rozsah než `Int32`. Explicitní operátor převodu lze zadat i v případě, že převod je potenciálně míru ztrát.  
  
 **X DO NOT** vyvolat výjimky z implicitní přetypování.  
  
 Je velmi obtížné pochopit, co se děje, protože jejich se nemusíte být vědomi, že převod probíhat koncovým uživatelům.  
  
 **✓ DO** throw <xref:System.InvalidCastException?displayProperty=nameWithType> Pokud volání operátor přetypování výsledkem míru ztrát převod a kontrakt operátoru neumožňuje míru ztrát převody.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu člena](../../../docs/standard/design-guidelines/member.md)
- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
