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
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743685"
---
# <a name="operator-overloads"></a><span data-ttu-id="ec603-102">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="ec603-102">Operator Overloads</span></span>
<span data-ttu-id="ec603-103">Přetížení operátorů umožňují, aby se typy rozhraní zobrazovaly, jako kdyby byly předdefinované jazykové primitivy.</span><span class="sxs-lookup"><span data-stu-id="ec603-103">Operator overloads allow framework types to appear as if they were built-in language primitives.</span></span>

 <span data-ttu-id="ec603-104">I když je v některých situacích povolená a užitečná, je nutné přetížení operátorů používat obezřetně.</span><span class="sxs-lookup"><span data-stu-id="ec603-104">Although allowed and useful in some situations, operator overloads should be used cautiously.</span></span> <span data-ttu-id="ec603-105">Existuje mnoho případů, ve kterých je přetížení operátoru zneužití, například když návrháři architektury začali používat operátory pro operace, které by měly být jednoduché metody.</span><span class="sxs-lookup"><span data-stu-id="ec603-105">There are many cases in which operator overloading has been abused, such as when framework designers started to use operators for operations that should be simple methods.</span></span> <span data-ttu-id="ec603-106">Následující pokyny by vám měly pomáhat při rozhodování, kdy a jak používat přetížení operátoru.</span><span class="sxs-lookup"><span data-stu-id="ec603-106">The following guidelines should help you decide when and how to use operator overloading.</span></span>

 <span data-ttu-id="ec603-107">❌ Vyhněte se definování přetížení operátoru, s výjimkou typů, které by se měly cítit jako primitivní (předdefinované) typy.</span><span class="sxs-lookup"><span data-stu-id="ec603-107">❌ AVOID defining operator overloads, except in types that should feel like primitive (built-in) types.</span></span>

 <span data-ttu-id="ec603-108">✔️ Zvažte definování přetížení operátoru v typu, který by se měl cítit jako primitivní typ.</span><span class="sxs-lookup"><span data-stu-id="ec603-108">✔️ CONSIDER defining operator overloads in a type that should feel like a primitive type.</span></span>

 <span data-ttu-id="ec603-109">Například <xref:System.String?displayProperty=nameWithType> má definováno `operator==` a `operator!=`.</span><span class="sxs-lookup"><span data-stu-id="ec603-109">For example, <xref:System.String?displayProperty=nameWithType> has `operator==` and `operator!=` defined.</span></span>

 <span data-ttu-id="ec603-110">✔️ definovat přetížení operátoru ve strukturách, které reprezentují čísla (například <xref:System.Decimal?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="ec603-110">✔️ DO define operator overloads in structs that represent numbers (such as <xref:System.Decimal?displayProperty=nameWithType>).</span></span>

 <span data-ttu-id="ec603-111">❌ roztomilá při definování přetížení operátoru.</span><span class="sxs-lookup"><span data-stu-id="ec603-111">❌ DO NOT be cute when defining operator overloads.</span></span>

 <span data-ttu-id="ec603-112">Přetížení operátoru je užitečné v případech, kdy je okamžitě zřejmé, jaký výsledek operace bude.</span><span class="sxs-lookup"><span data-stu-id="ec603-112">Operator overloading is useful in cases in which it is immediately obvious what the result of the operation will be.</span></span> <span data-ttu-id="ec603-113">Je například vhodné, aby bylo možné odečíst jednu <xref:System.DateTime> z jiného `DateTime` a získat <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="ec603-113">For example, it makes sense to be able to subtract one <xref:System.DateTime> from another `DateTime` and get a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="ec603-114">Není však vhodné použít operátor logického sjednocení pro sjednocení dvou databázových dotazů nebo k zápisu do datového proudu pomocí operátoru Shift.</span><span class="sxs-lookup"><span data-stu-id="ec603-114">However, it is not appropriate to use the logical union operator to union two database queries, or to use the shift operator to write to a stream.</span></span>

 <span data-ttu-id="ec603-115">❌ neposkytují přetížení operátorů, pokud alespoň jeden z operandů není typu definujícího přetížení.</span><span class="sxs-lookup"><span data-stu-id="ec603-115">❌ DO NOT provide operator overloads unless at least one of the operands is of the type defining the overload.</span></span>

 <span data-ttu-id="ec603-116">✔️ operátory přetížení způsobem symetricky.</span><span class="sxs-lookup"><span data-stu-id="ec603-116">✔️ DO overload operators in a symmetric fashion.</span></span>

 <span data-ttu-id="ec603-117">Například Pokud převedete `operator==`, měli byste také přetížit `operator!=`.</span><span class="sxs-lookup"><span data-stu-id="ec603-117">For example, if you overload the `operator==`, you should also overload the `operator!=`.</span></span> <span data-ttu-id="ec603-118">Podobně pokud převedete `operator<`, měli byste také přetížit `operator>`a tak dále.</span><span class="sxs-lookup"><span data-stu-id="ec603-118">Similarly, if you overload the `operator<`, you should also overload the `operator>`, and so on.</span></span>

 <span data-ttu-id="ec603-119">✔️ Zvažte poskytnutí metod s popisnými názvy, které odpovídají každému přetíženému operátoru.</span><span class="sxs-lookup"><span data-stu-id="ec603-119">✔️ CONSIDER providing methods with friendly names that correspond to each overloaded operator.</span></span>

 <span data-ttu-id="ec603-120">Mnoho jazyků nepodporuje přetížení operátorů.</span><span class="sxs-lookup"><span data-stu-id="ec603-120">Many languages do not support operator overloading.</span></span> <span data-ttu-id="ec603-121">Z tohoto důvodu se doporučuje, aby typy, které přetěžují operátory obsahují sekundární metodu s vhodným názvem domény, který poskytuje ekvivalentní funkce.</span><span class="sxs-lookup"><span data-stu-id="ec603-121">For this reason, it is recommended that types that overload operators include a secondary method with an appropriate domain-specific name that provides equivalent functionality.</span></span>

 <span data-ttu-id="ec603-122">Následující tabulka obsahuje seznam operátorů a odpovídající popisné názvy metod.</span><span class="sxs-lookup"><span data-stu-id="ec603-122">The following table contains a list of operators and the corresponding friendly method names.</span></span>

|<span data-ttu-id="ec603-123">C#Symbol operátoru</span><span class="sxs-lookup"><span data-stu-id="ec603-123">C# Operator Symbol</span></span>|<span data-ttu-id="ec603-124">Název metadat</span><span class="sxs-lookup"><span data-stu-id="ec603-124">Metadata Name</span></span>|<span data-ttu-id="ec603-125">Popisný název</span><span class="sxs-lookup"><span data-stu-id="ec603-125">Friendly Name</span></span>|
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

### <a name="overloading-operator-"></a><span data-ttu-id="ec603-126">Operátor přetížení = =</span><span class="sxs-lookup"><span data-stu-id="ec603-126">Overloading Operator ==</span></span>
 <span data-ttu-id="ec603-127">Přetížení `operator ==` je poměrně komplikované.</span><span class="sxs-lookup"><span data-stu-id="ec603-127">Overloading `operator ==` is quite complicated.</span></span> <span data-ttu-id="ec603-128">Sémantika operátoru musí být kompatibilní s několika ostatními členy, například <xref:System.Object.Equals%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ec603-128">The semantics of the operator need to be compatible with several other members, such as <xref:System.Object.Equals%2A?displayProperty=nameWithType>.</span></span>

### <a name="conversion-operators"></a><span data-ttu-id="ec603-129">Operátory převodu</span><span class="sxs-lookup"><span data-stu-id="ec603-129">Conversion Operators</span></span>
 <span data-ttu-id="ec603-130">Operátory převodu jsou unární operátory, které umožňují převod z jednoho typu na jiný.</span><span class="sxs-lookup"><span data-stu-id="ec603-130">Conversion operators are unary operators that allow conversion from one type to another.</span></span> <span data-ttu-id="ec603-131">Operátory musí být definovány jako statické členy buď na operandu, nebo na návratový typ.</span><span class="sxs-lookup"><span data-stu-id="ec603-131">The operators must be defined as static members on either the operand or the return type.</span></span> <span data-ttu-id="ec603-132">Existují dva typy operátorů převodu: implicitní a explicitní.</span><span class="sxs-lookup"><span data-stu-id="ec603-132">There are two types of conversion operators: implicit and explicit.</span></span>

 <span data-ttu-id="ec603-133">❌ neposkytují operátor převodu, Pokud koncoví uživatelé tyto převody jasně neočekávají.</span><span class="sxs-lookup"><span data-stu-id="ec603-133">❌ DO NOT provide a conversion operator if such conversion is not clearly expected by the end users.</span></span>

 <span data-ttu-id="ec603-134">❌ nedefinovat operátory převodu mimo doménu typu.</span><span class="sxs-lookup"><span data-stu-id="ec603-134">❌ DO NOT define conversion operators outside of a type’s domain.</span></span>

 <span data-ttu-id="ec603-135">Například <xref:System.Int32>, <xref:System.Double>a <xref:System.Decimal> jsou všechny číselné typy, zatímco <xref:System.DateTime> ne.</span><span class="sxs-lookup"><span data-stu-id="ec603-135">For example, <xref:System.Int32>, <xref:System.Double>, and <xref:System.Decimal> are all numeric types, whereas <xref:System.DateTime> is not.</span></span> <span data-ttu-id="ec603-136">Proto by neměl existovat žádný operátor převodu k převedení `Double(long)` na `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="ec603-136">Therefore, there should be no conversion operator to convert a `Double(long)` to a `DateTime`.</span></span> <span data-ttu-id="ec603-137">V takovém případě je upřednostňován konstruktor.</span><span class="sxs-lookup"><span data-stu-id="ec603-137">A constructor is preferred in such a case.</span></span>

 <span data-ttu-id="ec603-138">❌ neposkytují implicitní operátor převodu, pokud je převod potenciálně ztrátný.</span><span class="sxs-lookup"><span data-stu-id="ec603-138">❌ DO NOT provide an implicit conversion operator if the conversion is potentially lossy.</span></span>

 <span data-ttu-id="ec603-139">Například by neměl být implicitní převod z `Double` na `Int32`, protože `Double` má širší rozsah než `Int32`.</span><span class="sxs-lookup"><span data-stu-id="ec603-139">For example, there should not be an implicit conversion from `Double` to `Int32` because `Double` has a wider range than `Int32`.</span></span> <span data-ttu-id="ec603-140">Explicitní operátor převodu lze zadat i v případě, že je převod potenciálně ztrátný.</span><span class="sxs-lookup"><span data-stu-id="ec603-140">An explicit conversion operator can be provided even if the conversion is potentially lossy.</span></span>

 <span data-ttu-id="ec603-141">❌ nevyvolávat výjimky z implicitních přetypování.</span><span class="sxs-lookup"><span data-stu-id="ec603-141">❌ DO NOT throw exceptions from implicit casts.</span></span>

 <span data-ttu-id="ec603-142">Koncovým uživatelům je velmi obtížné pochopit, co se děje, protože nemusí vědět, že probíhá převod.</span><span class="sxs-lookup"><span data-stu-id="ec603-142">It is very difficult for end users to understand what is happening, because they might not be aware that a conversion is taking place.</span></span>

 <span data-ttu-id="ec603-143">✔️ vyvolat <xref:System.InvalidCastException?displayProperty=nameWithType>, pokud volání operátoru přetypování má za následek ztrátový převod a kontrakt operátora nepovoluje ztrátové převody.</span><span class="sxs-lookup"><span data-stu-id="ec603-143">✔️ DO throw <xref:System.InvalidCastException?displayProperty=nameWithType> if a call to a cast operator results in a lossy conversion and the contract of the operator does not allow lossy conversions.</span></span>

 <span data-ttu-id="ec603-144">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="ec603-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="ec603-145">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="ec603-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="ec603-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="ec603-146">See also</span></span>

- [<span data-ttu-id="ec603-147">Pokyny k návrhu člena</span><span class="sxs-lookup"><span data-stu-id="ec603-147">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="ec603-148">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="ec603-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
