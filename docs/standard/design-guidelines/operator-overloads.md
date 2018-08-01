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
# <a name="operator-overloads"></a><span data-ttu-id="fc366-102">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="fc366-102">Operator Overloads</span></span>
<span data-ttu-id="fc366-103">Přetížení operátoru povolit framework typy zobrazí, jako by byly primitiv předdefinované jazyka.</span><span class="sxs-lookup"><span data-stu-id="fc366-103">Operator overloads allow framework types to appear as if they were built-in language primitives.</span></span>  
  
 <span data-ttu-id="fc366-104">I když je povolené a užitečné v některých situacích Ano, je třeba přetížení operátoru použít opatrně.</span><span class="sxs-lookup"><span data-stu-id="fc366-104">Although allowed and useful in some situations, operator overloads should be used cautiously.</span></span> <span data-ttu-id="fc366-105">Existují mnoho případy, ve které operátor přetížení má byla zneužít, například při spuštění framework návrhářů, chcete-li používat pro operace, které by měly být jednoduché metody.</span><span class="sxs-lookup"><span data-stu-id="fc366-105">There are many cases in which operator overloading has been abused, such as when framework designers started to use operators for operations that should be simple methods.</span></span> <span data-ttu-id="fc366-106">Následující pokyny by měly pomoci při rozhodování, kdy a jak použití přetížení operátoru.</span><span class="sxs-lookup"><span data-stu-id="fc366-106">The following guidelines should help you decide when and how to use operator overloading.</span></span>  
  
 <span data-ttu-id="fc366-107">**X AVOID** definování přetížení operátoru v typy, které by měl působí jako primitivní typy (Předdefinované).</span><span class="sxs-lookup"><span data-stu-id="fc366-107">**X AVOID** defining operator overloads, except in types that should feel like primitive (built-in) types.</span></span>  
  
 <span data-ttu-id="fc366-108">**✓ CONSIDER** definování přetížení operátoru v typu, který by měl působí jako primitivního typu.</span><span class="sxs-lookup"><span data-stu-id="fc366-108">**✓ CONSIDER** defining operator overloads in a type that should feel like a primitive type.</span></span>  
  
 <span data-ttu-id="fc366-109">Například <xref:System.String?displayProperty=nameWithType> má `operator==` a `operator!=` definované.</span><span class="sxs-lookup"><span data-stu-id="fc366-109">For example, <xref:System.String?displayProperty=nameWithType> has `operator==` and `operator!=` defined.</span></span>  
  
 <span data-ttu-id="fc366-110">**✓ DO** v struktury, která představují čísla definovat přetížení operátoru (například <xref:System.Decimal?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="fc366-110">**✓ DO** define operator overloads in structs that represent numbers (such as <xref:System.Decimal?displayProperty=nameWithType>).</span></span>  
  
 <span data-ttu-id="fc366-111">**X DO NOT** být cute při definování přetížení operátoru.</span><span class="sxs-lookup"><span data-stu-id="fc366-111">**X DO NOT** be cute when defining operator overloads.</span></span>  
  
 <span data-ttu-id="fc366-112">Přetížení operátoru je užitečné v případech, ve kterých je hned zjevné co bude výsledek operace.</span><span class="sxs-lookup"><span data-stu-id="fc366-112">Operator overloading is useful in cases in which it is immediately obvious what the result of the operation will be.</span></span> <span data-ttu-id="fc366-113">Například má smysl moct odečtena jeden <xref:System.DateTime> z jiné `DateTime` a získat <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="fc366-113">For example, it makes sense to be able to subtract one <xref:System.DateTime> from another `DateTime` and get a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="fc366-114">Však není vhodné používat logický operátor union, union dotazy dvě databáze nebo použít operátor posunutí k zápisu do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="fc366-114">However, it is not appropriate to use the logical union operator to union two database queries, or to use the shift operator to write to a stream.</span></span>  
  
 <span data-ttu-id="fc366-115">**X DO NOT** zadejte operátor přetížení pokud alespoň jeden z operandy typu definování přetížení.</span><span class="sxs-lookup"><span data-stu-id="fc366-115">**X DO NOT** provide operator overloads unless at least one of the operands is of the type defining the overload.</span></span>  
  
 <span data-ttu-id="fc366-116">**✓ DO** přetížení operátory symetrický způsobem.</span><span class="sxs-lookup"><span data-stu-id="fc366-116">**✓ DO** overload operators in a symmetric fashion.</span></span>  
  
 <span data-ttu-id="fc366-117">Například, pokud jste přetížení `operator==`, by také přetížení `operator!=`.</span><span class="sxs-lookup"><span data-stu-id="fc366-117">For example, if you overload the `operator==`, you should also overload the `operator!=`.</span></span> <span data-ttu-id="fc366-118">Podobně pokud jste přetížení `operator<`, by také přetížení `operator>`a tak dále.</span><span class="sxs-lookup"><span data-stu-id="fc366-118">Similarly, if you overload the `operator<`, you should also overload the `operator>`, and so on.</span></span>  
  
 <span data-ttu-id="fc366-119">**✓ CONSIDER** poskytování metody popisné názvy, které odpovídají každé přetížené operátor.</span><span class="sxs-lookup"><span data-stu-id="fc366-119">**✓ CONSIDER** providing methods with friendly names that correspond to each overloaded operator.</span></span>  
  
 <span data-ttu-id="fc366-120">Mnoho jazyků nepodporují přetížení operátoru.</span><span class="sxs-lookup"><span data-stu-id="fc366-120">Many languages do not support operator overloading.</span></span> <span data-ttu-id="fc366-121">Z tohoto důvodu se doporučuje, aby typy, které přetížení operátory o sekundární metodu s názvem příslušné specifické pro doménu, která poskytuje ekvivalentní funkci.</span><span class="sxs-lookup"><span data-stu-id="fc366-121">For this reason, it is recommended that types that overload operators include a secondary method with an appropriate domain-specific name that provides equivalent functionality.</span></span>  
  
 <span data-ttu-id="fc366-122">Následující tabulka obsahuje seznam operátory a odpovídající metoda popisné názvy.</span><span class="sxs-lookup"><span data-stu-id="fc366-122">The following table contains a list of operators and the corresponding friendly method names.</span></span>  
  
|<span data-ttu-id="fc366-123">Symbol operátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="fc366-123">C# Operator Symbol</span></span>|<span data-ttu-id="fc366-124">Název metadat</span><span class="sxs-lookup"><span data-stu-id="fc366-124">Metadata Name</span></span>|<span data-ttu-id="fc366-125">Popisný název</span><span class="sxs-lookup"><span data-stu-id="fc366-125">Friendly Name</span></span>|  
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
  
### <a name="overloading-operator-"></a><span data-ttu-id="fc366-126">Přetížení operátoru ==</span><span class="sxs-lookup"><span data-stu-id="fc366-126">Overloading Operator ==</span></span>  
 <span data-ttu-id="fc366-127">Přetížení `operator ==` je poměrně složitá.</span><span class="sxs-lookup"><span data-stu-id="fc366-127">Overloading `operator ==` is quite complicated.</span></span> <span data-ttu-id="fc366-128">Sémantika operátor musí být kompatibilní s několika jinými členy, jako například <xref:System.Object.Equals%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fc366-128">The semantics of the operator need to be compatible with several other members, such as <xref:System.Object.Equals%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="conversion-operators"></a><span data-ttu-id="fc366-129">Operátory převodu</span><span class="sxs-lookup"><span data-stu-id="fc366-129">Conversion Operators</span></span>  
 <span data-ttu-id="fc366-130">Operátory převodu jsou unární operátory, které umožňují převod z jednoho typu.</span><span class="sxs-lookup"><span data-stu-id="fc366-130">Conversion operators are unary operators that allow conversion from one type to another.</span></span> <span data-ttu-id="fc366-131">Operátory musí být definován jako statické členy na operand nebo návratový typ.</span><span class="sxs-lookup"><span data-stu-id="fc366-131">The operators must be defined as static members on either the operand or the return type.</span></span> <span data-ttu-id="fc366-132">Existují dva typy operátory převodu: implicitní a explicitní.</span><span class="sxs-lookup"><span data-stu-id="fc366-132">There are two types of conversion operators: implicit and explicit.</span></span>  
  
 <span data-ttu-id="fc366-133">**X DO NOT** operátora převodu může poskytovat, pokud takový převod neočekává jasně koncoví uživatelé.</span><span class="sxs-lookup"><span data-stu-id="fc366-133">**X DO NOT** provide a conversion operator if such conversion is not clearly expected by the end users.</span></span>  
  
 <span data-ttu-id="fc366-134">**X DO NOT** definovat operátory převodu mimo typ domény.</span><span class="sxs-lookup"><span data-stu-id="fc366-134">**X DO NOT** define conversion operators outside of a type’s domain.</span></span>  
  
 <span data-ttu-id="fc366-135">Například <xref:System.Int32>, <xref:System.Double>, a <xref:System.Decimal> jsou všechny číselné typy, zatímco <xref:System.DateTime> není.</span><span class="sxs-lookup"><span data-stu-id="fc366-135">For example, <xref:System.Int32>, <xref:System.Double>, and <xref:System.Decimal> are all numeric types, whereas <xref:System.DateTime> is not.</span></span> <span data-ttu-id="fc366-136">Proto, měla by existovat žádné operátor převodu převést `Double(long)` k `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="fc366-136">Therefore, there should be no conversion operator to convert a `Double(long)` to a `DateTime`.</span></span> <span data-ttu-id="fc366-137">V takovém případě je upřednostňovaný konstruktor.</span><span class="sxs-lookup"><span data-stu-id="fc366-137">A constructor is preferred in such a case.</span></span>  
  
 <span data-ttu-id="fc366-138">**X DO NOT** zadat operátor implicitní převod, pokud převod potenciálně míru ztrát.</span><span class="sxs-lookup"><span data-stu-id="fc366-138">**X DO NOT** provide an implicit conversion operator if the conversion is potentially lossy.</span></span>  
  
 <span data-ttu-id="fc366-139">Například by nemělo být ke implicitní převod z `Double` k `Int32` protože `Double` má více typů než `Int32`.</span><span class="sxs-lookup"><span data-stu-id="fc366-139">For example, there should not be an implicit conversion from `Double` to `Int32` because `Double` has a wider range than `Int32`.</span></span> <span data-ttu-id="fc366-140">Explicitní převod operátor lze zadat, i když je převod potenciálně míru ztrát.</span><span class="sxs-lookup"><span data-stu-id="fc366-140">An explicit conversion operator can be provided even if the conversion is potentially lossy.</span></span>  
  
 <span data-ttu-id="fc366-141">**X DO NOT** vyvolat výjimky z implicitní přetypování.</span><span class="sxs-lookup"><span data-stu-id="fc366-141">**X DO NOT** throw exceptions from implicit casts.</span></span>  
  
 <span data-ttu-id="fc366-142">Je velmi obtížné koncovým uživatelům pochopit, co se děje, protože mohou být vědět, Probíhá převod.</span><span class="sxs-lookup"><span data-stu-id="fc366-142">It is very difficult for end users to understand what is happening, because they might not be aware that a conversion is taking place.</span></span>  
  
 <span data-ttu-id="fc366-143">**✓ DO** throw <xref:System.InvalidCastException?displayProperty=nameWithType> Pokud volání operátor přetypování výsledkem míru ztrát převod a kontrakt operátoru neumožňuje míru ztrát převody.</span><span class="sxs-lookup"><span data-stu-id="fc366-143">**✓ DO** throw <xref:System.InvalidCastException?displayProperty=nameWithType> if a call to a cast operator results in a lossy conversion and the contract of the operator does not allow lossy conversions.</span></span>  
  
 <span data-ttu-id="fc366-144">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="fc366-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="fc366-145">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="fc366-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc366-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="fc366-146">See Also</span></span>  
 [<span data-ttu-id="fc366-147">Pokyny k návrhu člena</span><span class="sxs-lookup"><span data-stu-id="fc366-147">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 [<span data-ttu-id="fc366-148">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="fc366-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
