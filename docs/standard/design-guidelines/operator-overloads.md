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
# <a name="operator-overloads"></a><span data-ttu-id="70003-102">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="70003-102">Operator Overloads</span></span>
<span data-ttu-id="70003-103">Přetížení operátorů umožňují, aby se typy architektury zobrazovaly, jako by byly předdefinované jazykové primitivy.</span><span class="sxs-lookup"><span data-stu-id="70003-103">Operator overloads allow framework types to appear as if they were built-in language primitives.</span></span>

 <span data-ttu-id="70003-104">Ačkoli povolené a užitečné v některých situacích, přetížení operátoru by měly být používány opatrně.</span><span class="sxs-lookup"><span data-stu-id="70003-104">Although allowed and useful in some situations, operator overloads should be used cautiously.</span></span> <span data-ttu-id="70003-105">Existuje mnoho případů, ve kterých bylo zneužito přetížení operátoru, například když návrháři architektury začali používat operátory pro operace, které by měly být jednoduché metody.</span><span class="sxs-lookup"><span data-stu-id="70003-105">There are many cases in which operator overloading has been abused, such as when framework designers started to use operators for operations that should be simple methods.</span></span> <span data-ttu-id="70003-106">Následující pokyny by vám měly pomoci rozhodnout, kdy a jak používat přetížení operátoru.</span><span class="sxs-lookup"><span data-stu-id="70003-106">The following guidelines should help you decide when and how to use operator overloading.</span></span>

 <span data-ttu-id="70003-107">❌Vyhněte se definování přetížení operátoru, s výjimkou typů, které by se měly cítit jako primitivní (vestavěné) typy.</span><span class="sxs-lookup"><span data-stu-id="70003-107">❌ AVOID defining operator overloads, except in types that should feel like primitive (built-in) types.</span></span>

 <span data-ttu-id="70003-108">✔️ zvážit definování přetížení operátoru v typu, který by se měl cítit jako primitivní typ.</span><span class="sxs-lookup"><span data-stu-id="70003-108">✔️ CONSIDER defining operator overloads in a type that should feel like a primitive type.</span></span>

 <span data-ttu-id="70003-109">Například <xref:System.String?displayProperty=nameWithType> má `operator==` `operator!=` a definována.</span><span class="sxs-lookup"><span data-stu-id="70003-109">For example, <xref:System.String?displayProperty=nameWithType> has `operator==` and `operator!=` defined.</span></span>

 <span data-ttu-id="70003-110">✔️ do definovat přetížení operátoru ve strukturách, <xref:System.Decimal?displayProperty=nameWithType>které představují čísla (například ).</span><span class="sxs-lookup"><span data-stu-id="70003-110">✔️ DO define operator overloads in structs that represent numbers (such as <xref:System.Decimal?displayProperty=nameWithType>).</span></span>

 <span data-ttu-id="70003-111">❌Nebuďte roztomilí při definování přetížení operátoru.</span><span class="sxs-lookup"><span data-stu-id="70003-111">❌ DO NOT be cute when defining operator overloads.</span></span>

 <span data-ttu-id="70003-112">Přetížení operátoru je užitečné v případech, kdy je okamžitě zřejmé, jaký bude výsledek operace.</span><span class="sxs-lookup"><span data-stu-id="70003-112">Operator overloading is useful in cases in which it is immediately obvious what the result of the operation will be.</span></span> <span data-ttu-id="70003-113">Například má smysl, aby bylo možné <xref:System.DateTime> odečíst jeden od druhého `DateTime` a získat <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="70003-113">For example, it makes sense to be able to subtract one <xref:System.DateTime> from another `DateTime` and get a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="70003-114">Není však vhodné použít operátor logického sjednocení k sjednocení dvou databázových dotazů nebo k zápisu do datového proudu pomocí operátoru shift.</span><span class="sxs-lookup"><span data-stu-id="70003-114">However, it is not appropriate to use the logical union operator to union two database queries, or to use the shift operator to write to a stream.</span></span>

 <span data-ttu-id="70003-115">❌NEPOSKYTUJÍ operátor přetížení, pokud alespoň jeden z operandů je typu definující přetížení.</span><span class="sxs-lookup"><span data-stu-id="70003-115">❌ DO NOT provide operator overloads unless at least one of the operands is of the type defining the overload.</span></span>

 <span data-ttu-id="70003-116">✔️ operátory přetížení do symetrickým způsobem.</span><span class="sxs-lookup"><span data-stu-id="70003-116">✔️ DO overload operators in a symmetric fashion.</span></span>

 <span data-ttu-id="70003-117">Například pokud přetížení `operator==`, měli byste `operator!=`také přetížení .</span><span class="sxs-lookup"><span data-stu-id="70003-117">For example, if you overload the `operator==`, you should also overload the `operator!=`.</span></span> <span data-ttu-id="70003-118">Podobně pokud přetížení `operator<`, měli byste také `operator>`přetížení , a tak dále.</span><span class="sxs-lookup"><span data-stu-id="70003-118">Similarly, if you overload the `operator<`, you should also overload the `operator>`, and so on.</span></span>

 <span data-ttu-id="70003-119">✔️ zvažte poskytování metod s popisnými názvy, které odpovídají každému přetíženému operátoru.</span><span class="sxs-lookup"><span data-stu-id="70003-119">✔️ CONSIDER providing methods with friendly names that correspond to each overloaded operator.</span></span>

 <span data-ttu-id="70003-120">Mnoho jazyků nepodporuje přetížení operátoru.</span><span class="sxs-lookup"><span data-stu-id="70003-120">Many languages do not support operator overloading.</span></span> <span data-ttu-id="70003-121">Z tohoto důvodu se doporučuje, aby typy operátorů přetížení obsahovat sekundární metodu s odpovídající název specifické pro doménu, který poskytuje ekvivalentní funkce.</span><span class="sxs-lookup"><span data-stu-id="70003-121">For this reason, it is recommended that types that overload operators include a secondary method with an appropriate domain-specific name that provides equivalent functionality.</span></span>

 <span data-ttu-id="70003-122">Následující tabulka obsahuje seznam operátorů a odpovídající popisné názvy metod.</span><span class="sxs-lookup"><span data-stu-id="70003-122">The following table contains a list of operators and the corresponding friendly method names.</span></span>

|<span data-ttu-id="70003-123">Symbol operátora Jazyka C#</span><span class="sxs-lookup"><span data-stu-id="70003-123">C# Operator Symbol</span></span>|<span data-ttu-id="70003-124">Název metadat</span><span class="sxs-lookup"><span data-stu-id="70003-124">Metadata Name</span></span>|<span data-ttu-id="70003-125">Popisný název</span><span class="sxs-lookup"><span data-stu-id="70003-125">Friendly Name</span></span>|
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

### <a name="overloading-operator-"></a><span data-ttu-id="70003-126">Operátor přetížení ==</span><span class="sxs-lookup"><span data-stu-id="70003-126">Overloading Operator ==</span></span>
 <span data-ttu-id="70003-127">Přetížení `operator ==` je poměrně komplikované.</span><span class="sxs-lookup"><span data-stu-id="70003-127">Overloading `operator ==` is quite complicated.</span></span> <span data-ttu-id="70003-128">Sémantiku operátora musí být kompatibilní s několika <xref:System.Object.Equals%2A?displayProperty=nameWithType>dalšími členy, například .</span><span class="sxs-lookup"><span data-stu-id="70003-128">The semantics of the operator need to be compatible with several other members, such as <xref:System.Object.Equals%2A?displayProperty=nameWithType>.</span></span>

### <a name="conversion-operators"></a><span data-ttu-id="70003-129">Operátory převodu</span><span class="sxs-lookup"><span data-stu-id="70003-129">Conversion Operators</span></span>
 <span data-ttu-id="70003-130">Operátory převodu jsou unární operátory, které umožňují převod z jednoho typu na jiný.</span><span class="sxs-lookup"><span data-stu-id="70003-130">Conversion operators are unary operators that allow conversion from one type to another.</span></span> <span data-ttu-id="70003-131">Operátory musí být definovány jako statické členy na operandu nebo návratového typu.</span><span class="sxs-lookup"><span data-stu-id="70003-131">The operators must be defined as static members on either the operand or the return type.</span></span> <span data-ttu-id="70003-132">Existují dva typy operátorů převodu: implicitní a explicitní.</span><span class="sxs-lookup"><span data-stu-id="70003-132">There are two types of conversion operators: implicit and explicit.</span></span>

 <span data-ttu-id="70003-133">❌Neposkytujte operátor převodu, pokud takový převod není jasně očekáván koncovými uživateli.</span><span class="sxs-lookup"><span data-stu-id="70003-133">❌ DO NOT provide a conversion operator if such conversion is not clearly expected by the end users.</span></span>

 <span data-ttu-id="70003-134">❌NEDEFINUJTE operátory převodu mimo doménu typu.</span><span class="sxs-lookup"><span data-stu-id="70003-134">❌ DO NOT define conversion operators outside of a type’s domain.</span></span>

 <span data-ttu-id="70003-135">Například <xref:System.Int32>, <xref:System.Double>, <xref:System.Decimal> a jsou všechny <xref:System.DateTime> číselné typy, vzhledem k tomu, že není.</span><span class="sxs-lookup"><span data-stu-id="70003-135">For example, <xref:System.Int32>, <xref:System.Double>, and <xref:System.Decimal> are all numeric types, whereas <xref:System.DateTime> is not.</span></span> <span data-ttu-id="70003-136">Proto by měl být žádný operátor `Double(long)` převodu převést na `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="70003-136">Therefore, there should be no conversion operator to convert a `Double(long)` to a `DateTime`.</span></span> <span data-ttu-id="70003-137">Konstruktor je upřednostňován v takovém případě.</span><span class="sxs-lookup"><span data-stu-id="70003-137">A constructor is preferred in such a case.</span></span>

 <span data-ttu-id="70003-138">❌NEPOSKYTUJÍ implicitní operátor převodu, pokud převod je potenciálně ztrátové.</span><span class="sxs-lookup"><span data-stu-id="70003-138">❌ DO NOT provide an implicit conversion operator if the conversion is potentially lossy.</span></span>

 <span data-ttu-id="70003-139">Například by neměl být implicitní `Double` `Int32` převod `Double` z do, `Int32`protože má širší rozsah než .</span><span class="sxs-lookup"><span data-stu-id="70003-139">For example, there should not be an implicit conversion from `Double` to `Int32` because `Double` has a wider range than `Int32`.</span></span> <span data-ttu-id="70003-140">Explicitní operátor převodu může být poskytnuta i v případě, že převod je potenciálně ztrátové.</span><span class="sxs-lookup"><span data-stu-id="70003-140">An explicit conversion operator can be provided even if the conversion is potentially lossy.</span></span>

 <span data-ttu-id="70003-141">❌NEVYVOLÁVAT výjimky z implicitní přetypáže.</span><span class="sxs-lookup"><span data-stu-id="70003-141">❌ DO NOT throw exceptions from implicit casts.</span></span>

 <span data-ttu-id="70003-142">Pro koncové uživatele je velmi obtížné pochopit, co se děje, protože si nemusí být vědomi, že probíhá převod.</span><span class="sxs-lookup"><span data-stu-id="70003-142">It is very difficult for end users to understand what is happening, because they might not be aware that a conversion is taking place.</span></span>

 <span data-ttu-id="70003-143">✔️ DO <xref:System.InvalidCastException?displayProperty=nameWithType> throw, pokud volání operátoru přetypovacího vysílání vede ke ztrátovému převodu a smlouva operátoru neumožňuje ztrátové převody.</span><span class="sxs-lookup"><span data-stu-id="70003-143">✔️ DO throw <xref:System.InvalidCastException?displayProperty=nameWithType> if a call to a cast operator results in a lossy conversion and the contract of the operator does not allow lossy conversions.</span></span>

 <span data-ttu-id="70003-144">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="70003-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="70003-145">*Přetištěno se svolením Pearson Education, Inc. z [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="70003-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="70003-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="70003-146">See also</span></span>

- [<span data-ttu-id="70003-147">Pokyny k návrhu člena</span><span class="sxs-lookup"><span data-stu-id="70003-147">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="70003-148">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="70003-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
