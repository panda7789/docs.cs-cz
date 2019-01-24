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
# <a name="operator-overloads"></a><span data-ttu-id="6e485-102">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="6e485-102">Operator Overloads</span></span>
<span data-ttu-id="6e485-103">Přetížení operátoru povolit rozhraní framework typy zobrazení, jako kdyby byly integrované primitivní.</span><span class="sxs-lookup"><span data-stu-id="6e485-103">Operator overloads allow framework types to appear as if they were built-in language primitives.</span></span>  
  
 <span data-ttu-id="6e485-104">I když je povolený a v některých situacích užitečné, je třeba přetížení operátoru použít opatrně.</span><span class="sxs-lookup"><span data-stu-id="6e485-104">Although allowed and useful in some situations, operator overloads should be used cautiously.</span></span> <span data-ttu-id="6e485-105">Jsou většinou v operátoru přetížení má byla zneužít, jako je například při spuštění návrháře framework použití operátorů pro operace, které by měly být jednoduché metody.</span><span class="sxs-lookup"><span data-stu-id="6e485-105">There are many cases in which operator overloading has been abused, such as when framework designers started to use operators for operations that should be simple methods.</span></span> <span data-ttu-id="6e485-106">Následující pokyny vám by měly pomoci při rozhodování, kdy a jak použití přetížení operátoru.</span><span class="sxs-lookup"><span data-stu-id="6e485-106">The following guidelines should help you decide when and how to use operator overloading.</span></span>  
  
 <span data-ttu-id="6e485-107">**X AVOID** definování přetížení operátoru v typy, které by měl působí jako primitivní typy (Předdefinované).</span><span class="sxs-lookup"><span data-stu-id="6e485-107">**X AVOID** defining operator overloads, except in types that should feel like primitive (built-in) types.</span></span>  
  
 <span data-ttu-id="6e485-108">**✓ CONSIDER** definování přetížení operátoru v typu, který by měl působí jako primitivního typu.</span><span class="sxs-lookup"><span data-stu-id="6e485-108">**✓ CONSIDER** defining operator overloads in a type that should feel like a primitive type.</span></span>  
  
 <span data-ttu-id="6e485-109">Například <xref:System.String?displayProperty=nameWithType> má `operator==` a `operator!=` definované.</span><span class="sxs-lookup"><span data-stu-id="6e485-109">For example, <xref:System.String?displayProperty=nameWithType> has `operator==` and `operator!=` defined.</span></span>  
  
 <span data-ttu-id="6e485-110">**✓ DO** v struktury, která představují čísla definovat přetížení operátoru (například <xref:System.Decimal?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="6e485-110">**✓ DO** define operator overloads in structs that represent numbers (such as <xref:System.Decimal?displayProperty=nameWithType>).</span></span>  
  
 <span data-ttu-id="6e485-111">**X DO NOT** být cute při definování přetížení operátoru.</span><span class="sxs-lookup"><span data-stu-id="6e485-111">**X DO NOT** be cute when defining operator overloads.</span></span>  
  
 <span data-ttu-id="6e485-112">Přetížení operátoru je užitečné v případech, ve kterých je okamžitě zřejmý co se bude výsledek operace.</span><span class="sxs-lookup"><span data-stu-id="6e485-112">Operator overloading is useful in cases in which it is immediately obvious what the result of the operation will be.</span></span> <span data-ttu-id="6e485-113">Například smysl mít odečíst jeden <xref:System.DateTime> z jiného `DateTime` a získat <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="6e485-113">For example, it makes sense to be able to subtract one <xref:System.DateTime> from another `DateTime` and get a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="6e485-114">Není však vhodné pomocí logického operátoru sjednocení pro sjednocení dvou databázové dotazy nebo operátor posunutí slouží k zápisu do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="6e485-114">However, it is not appropriate to use the logical union operator to union two database queries, or to use the shift operator to write to a stream.</span></span>  
  
 <span data-ttu-id="6e485-115">**X DO NOT** zadejte operátor přetížení pokud alespoň jeden z operandy typu definování přetížení.</span><span class="sxs-lookup"><span data-stu-id="6e485-115">**X DO NOT** provide operator overloads unless at least one of the operands is of the type defining the overload.</span></span>  
  
 <span data-ttu-id="6e485-116">**✓ DO** přetížení operátory symetrický způsobem.</span><span class="sxs-lookup"><span data-stu-id="6e485-116">**✓ DO** overload operators in a symmetric fashion.</span></span>  
  
 <span data-ttu-id="6e485-117">Například, pokud přetížíte `operator==`, byste měli také přetížit `operator!=`.</span><span class="sxs-lookup"><span data-stu-id="6e485-117">For example, if you overload the `operator==`, you should also overload the `operator!=`.</span></span> <span data-ttu-id="6e485-118">Podobně pokud přetížíte `operator<`, byste měli také přetížit `operator>`, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="6e485-118">Similarly, if you overload the `operator<`, you should also overload the `operator>`, and so on.</span></span>  
  
 <span data-ttu-id="6e485-119">**✓ CONSIDER** poskytování metody popisné názvy, které odpovídají každé přetížené operátor.</span><span class="sxs-lookup"><span data-stu-id="6e485-119">**✓ CONSIDER** providing methods with friendly names that correspond to each overloaded operator.</span></span>  
  
 <span data-ttu-id="6e485-120">Řadu jiných jazyků nepodporují přetížení operátoru.</span><span class="sxs-lookup"><span data-stu-id="6e485-120">Many languages do not support operator overloading.</span></span> <span data-ttu-id="6e485-121">Z tohoto důvodu se doporučuje, typy, které přetěžují operátory zahrnují sekundární metodu s vhodný název specifického pro doménu, která obsahuje ekvivalentní funkce.</span><span class="sxs-lookup"><span data-stu-id="6e485-121">For this reason, it is recommended that types that overload operators include a secondary method with an appropriate domain-specific name that provides equivalent functionality.</span></span>  
  
 <span data-ttu-id="6e485-122">Následující tabulka obsahuje seznam operátorů a odpovídající názvy metod popisný.</span><span class="sxs-lookup"><span data-stu-id="6e485-122">The following table contains a list of operators and the corresponding friendly method names.</span></span>  
  
|<span data-ttu-id="6e485-123">Symbol operátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6e485-123">C# Operator Symbol</span></span>|<span data-ttu-id="6e485-124">Název metadat</span><span class="sxs-lookup"><span data-stu-id="6e485-124">Metadata Name</span></span>|<span data-ttu-id="6e485-125">Popisný název</span><span class="sxs-lookup"><span data-stu-id="6e485-125">Friendly Name</span></span>|  
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
  
### <a name="overloading-operator-"></a><span data-ttu-id="6e485-126">Přetížení operátoru ==</span><span class="sxs-lookup"><span data-stu-id="6e485-126">Overloading Operator ==</span></span>  
 <span data-ttu-id="6e485-127">Přetížení `operator ==` je poměrně složitý.</span><span class="sxs-lookup"><span data-stu-id="6e485-127">Overloading `operator ==` is quite complicated.</span></span> <span data-ttu-id="6e485-128">Sémantika operátoru musí být kompatibilní s několika jinými členy jako <xref:System.Object.Equals%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6e485-128">The semantics of the operator need to be compatible with several other members, such as <xref:System.Object.Equals%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="conversion-operators"></a><span data-ttu-id="6e485-129">Operátory převodu</span><span class="sxs-lookup"><span data-stu-id="6e485-129">Conversion Operators</span></span>  
 <span data-ttu-id="6e485-130">Operátory převodu jsou unární operátory, které umožňují převod jednoho typu na jiný.</span><span class="sxs-lookup"><span data-stu-id="6e485-130">Conversion operators are unary operators that allow conversion from one type to another.</span></span> <span data-ttu-id="6e485-131">Operátory musí být definovány jako statické členy v operandu nebo návratového typu.</span><span class="sxs-lookup"><span data-stu-id="6e485-131">The operators must be defined as static members on either the operand or the return type.</span></span> <span data-ttu-id="6e485-132">Existují dva typy operátorů převodu: implicitní a explicitní.</span><span class="sxs-lookup"><span data-stu-id="6e485-132">There are two types of conversion operators: implicit and explicit.</span></span>  
  
 <span data-ttu-id="6e485-133">**X DO NOT** operátora převodu může poskytovat, pokud takový převod neočekává jasně koncoví uživatelé.</span><span class="sxs-lookup"><span data-stu-id="6e485-133">**X DO NOT** provide a conversion operator if such conversion is not clearly expected by the end users.</span></span>  
  
 <span data-ttu-id="6e485-134">**X DO NOT** definovat operátory převodu mimo typ domény.</span><span class="sxs-lookup"><span data-stu-id="6e485-134">**X DO NOT** define conversion operators outside of a type’s domain.</span></span>  
  
 <span data-ttu-id="6e485-135">Například <xref:System.Int32>, <xref:System.Double>, a <xref:System.Decimal> jsou všechny číselné typy, zatímco <xref:System.DateTime> není.</span><span class="sxs-lookup"><span data-stu-id="6e485-135">For example, <xref:System.Int32>, <xref:System.Double>, and <xref:System.Decimal> are all numeric types, whereas <xref:System.DateTime> is not.</span></span> <span data-ttu-id="6e485-136">Proto by měl existovat žádný operátor převodu k převedení `Double(long)` k `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="6e485-136">Therefore, there should be no conversion operator to convert a `Double(long)` to a `DateTime`.</span></span> <span data-ttu-id="6e485-137">V takovém případě se upřednostňuje konstruktor.</span><span class="sxs-lookup"><span data-stu-id="6e485-137">A constructor is preferred in such a case.</span></span>  
  
 <span data-ttu-id="6e485-138">**X DO NOT** zadat operátor implicitní převod, pokud převod potenciálně míru ztrát.</span><span class="sxs-lookup"><span data-stu-id="6e485-138">**X DO NOT** provide an implicit conversion operator if the conversion is potentially lossy.</span></span>  
  
 <span data-ttu-id="6e485-139">Například by neměla existovat implicitní převod z `Double` k `Int32` protože `Double` má širší rozsah než `Int32`.</span><span class="sxs-lookup"><span data-stu-id="6e485-139">For example, there should not be an implicit conversion from `Double` to `Int32` because `Double` has a wider range than `Int32`.</span></span> <span data-ttu-id="6e485-140">Explicitní operátor převodu lze zadat i v případě, že převod je potenciálně míru ztrát.</span><span class="sxs-lookup"><span data-stu-id="6e485-140">An explicit conversion operator can be provided even if the conversion is potentially lossy.</span></span>  
  
 <span data-ttu-id="6e485-141">**X DO NOT** vyvolat výjimky z implicitní přetypování.</span><span class="sxs-lookup"><span data-stu-id="6e485-141">**X DO NOT** throw exceptions from implicit casts.</span></span>  
  
 <span data-ttu-id="6e485-142">Je velmi obtížné pochopit, co se děje, protože jejich se nemusíte být vědomi, že převod probíhat koncovým uživatelům.</span><span class="sxs-lookup"><span data-stu-id="6e485-142">It is very difficult for end users to understand what is happening, because they might not be aware that a conversion is taking place.</span></span>  
  
 <span data-ttu-id="6e485-143">**✓ DO** throw <xref:System.InvalidCastException?displayProperty=nameWithType> Pokud volání operátor přetypování výsledkem míru ztrát převod a kontrakt operátoru neumožňuje míru ztrát převody.</span><span class="sxs-lookup"><span data-stu-id="6e485-143">**✓ DO** throw <xref:System.InvalidCastException?displayProperty=nameWithType> if a call to a cast operator results in a lossy conversion and the contract of the operator does not allow lossy conversions.</span></span>  
  
 <span data-ttu-id="6e485-144">*Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="6e485-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="6e485-145">*Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="6e485-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e485-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6e485-146">See also</span></span>

- [<span data-ttu-id="6e485-147">Pokyny k návrhu člena</span><span class="sxs-lookup"><span data-stu-id="6e485-147">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="6e485-148">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="6e485-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
