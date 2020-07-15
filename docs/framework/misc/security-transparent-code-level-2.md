---
title: Transparentní kód pro zabezpečení, úroveň 2
description: Pochopení transparentního kódu úrovně 2 Podívejte se na příklady a chování použití, přepište vzory, pravidla dědičnosti a další.
ms.date: 03/30/2017
helpviewer_keywords:
- transparency
- level 2 transparency
- security-transparent code
- security-critical code
ms.assetid: 4d05610a-0da6-4f08-acea-d54c9d6143c0
ms.openlocfilehash: 3b87a48ac3f9925fd868be9e58d5904014ca6c09
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309206"
---
# <a name="security-transparent-code-level-2"></a><span data-ttu-id="ab3d4-104">Transparentní kód pro zabezpečení, úroveň 2</span><span class="sxs-lookup"><span data-stu-id="ab3d4-104">Security-Transparent Code, Level 2</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="ab3d4-105">Transparentnost úrovně 2 byla představena v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-105">Level 2 transparency was introduced in the .NET Framework 4.</span></span> <span data-ttu-id="ab3d4-106">Tři principy tohoto modelu jsou transparentní kód, bezpečný a kritický kód pro zabezpečení a kód kritický pro zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-106">The three tenets of this model are transparent code, security-safe-critical code, and security-critical code.</span></span>

- <span data-ttu-id="ab3d4-107">Transparentní kód, včetně kódu, který je spuštěn jako úplný vztah důvěryhodnosti, může volat jiný transparentní kód nebo pouze bezpečný kód kritický pro zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-107">Transparent code, including code that is running as full trust, can call other transparent code or security-safe-critical code only.</span></span> <span data-ttu-id="ab3d4-108">Může provádět jenom akce, které povoluje sada oprávnění částečné důvěryhodnosti domény (pokud existuje).</span><span class="sxs-lookup"><span data-stu-id="ab3d4-108">It can only perform actions allowed by the domain’s partial trust permission set (if one exists).</span></span> <span data-ttu-id="ab3d4-109">Transparentní kód nemůže provádět následující:</span><span class="sxs-lookup"><span data-stu-id="ab3d4-109">Transparent code cannot do the following:</span></span>

  - <span data-ttu-id="ab3d4-110">Provedení <xref:System.Security.CodeAccessPermission.Assert%2A> nebo zvýšení oprávnění.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-110">Perform an <xref:System.Security.CodeAccessPermission.Assert%2A> or elevation of privilege.</span></span>

  - <span data-ttu-id="ab3d4-111">Obsahuje nezabezpečený nebo neověřitelný kód.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-111">Contain unsafe or unverifiable code.</span></span>

  - <span data-ttu-id="ab3d4-112">Přímo zavolejte kritický kód.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-112">Directly call critical code.</span></span>

  - <span data-ttu-id="ab3d4-113">Volejte nativní kód nebo kód s <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atributem.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-113">Call native code or code with the <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attribute.</span></span>

  - <span data-ttu-id="ab3d4-114">Zavolejte člen, který je chráněn pomocí <xref:System.Security.Permissions.SecurityAction.LinkDemand> .</span><span class="sxs-lookup"><span data-stu-id="ab3d4-114">Call a member that is protected by a <xref:System.Security.Permissions.SecurityAction.LinkDemand>.</span></span>

  - <span data-ttu-id="ab3d4-115">Dědí z kritických typů.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-115">Inherit from critical types.</span></span>

  <span data-ttu-id="ab3d4-116">Transparentní metody navíc nemohou přepsat kritické virtuální metody nebo implementovat kritické metody rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-116">In addition, transparent methods cannot override critical virtual methods or implement critical interface methods.</span></span>

- <span data-ttu-id="ab3d4-117">Bezpečný a kritický kód je plně důvěryhodný, ale je volat transparentním kódem.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-117">Safe-critical code is fully trusted but is callable by transparent code.</span></span> <span data-ttu-id="ab3d4-118">Zveřejňuje omezený plošný prostor s plně důvěryhodným kódem; k ověření správnosti a zabezpečení dochází v kódu bezpečného kritického.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-118">It exposes a limited surface area of full-trust code; correctness and security verifications happen in safe-critical code.</span></span>

- <span data-ttu-id="ab3d4-119">Kód kritický pro zabezpečení může volat jakýkoli kód a je plně důvěryhodný, ale nemůže být volán transparentním kódem.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-119">Security-critical code can call any code and is fully trusted, but it cannot be called by transparent code.</span></span>

## <a name="usage-examples-and-behaviors"></a><span data-ttu-id="ab3d4-120">Příklady využití a chování</span><span class="sxs-lookup"><span data-stu-id="ab3d4-120">Usage Examples and Behaviors</span></span>

<span data-ttu-id="ab3d4-121">Chcete-li zadat pravidla .NET Framework 4 (transparentnost úrovně 2), použijte následující anotaci pro sestavení:</span><span class="sxs-lookup"><span data-stu-id="ab3d4-121">To specify .NET Framework 4 rules (level 2 transparency), use the following annotation for an assembly:</span></span>

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level2)]
```

<span data-ttu-id="ab3d4-122">Chcete-li zamknout pravidla .NET Framework 2,0 (transparentnost první úrovně), použijte následující poznámku:</span><span class="sxs-lookup"><span data-stu-id="ab3d4-122">To lock into the .NET Framework 2.0 rules (level 1 transparency), use the following annotation:</span></span>

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level1)]
```

<span data-ttu-id="ab3d4-123">Pokud do sestavení nechcete přidat poznámku, použijí se ve výchozím nastavení pravidla .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-123">If you do not annotate an assembly, the .NET Framework 4 rules are used by default.</span></span> <span data-ttu-id="ab3d4-124">Doporučený osvědčený postup je však použít <xref:System.Security.SecurityRulesAttribute> atribut místo v závislosti na výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-124">However, the recommended best practice is to use the <xref:System.Security.SecurityRulesAttribute> attribute instead of depending on the default.</span></span>

### <a name="assembly-wide-annotation"></a><span data-ttu-id="ab3d4-125">Poznámka na úrovni sestavení</span><span class="sxs-lookup"><span data-stu-id="ab3d4-125">Assembly-wide Annotation</span></span>

<span data-ttu-id="ab3d4-126">Následující pravidla platí pro použití atributů na úrovni sestavení:</span><span class="sxs-lookup"><span data-stu-id="ab3d4-126">The following rules apply to the use of attributes at the assembly level:</span></span>

- <span data-ttu-id="ab3d4-127">Bez atributů: modul runtime interpretuje veškerý kód jako kritické pro zabezpečení, s výjimkou případů, kdy je kritické zabezpečení v rozporu s pravidlem dědičnosti (například při přepsání nebo implementaci transparentní virtuální nebo metody rozhraní).</span><span class="sxs-lookup"><span data-stu-id="ab3d4-127">No attributes: If you do not specify any attributes, the runtime interprets all code as security-critical, except where being security-critical violates an inheritance rule (for example, when overriding or implementing a transparent virtual or interface method).</span></span> <span data-ttu-id="ab3d4-128">V těchto případech jsou metody kritické.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-128">In those cases, the methods are safe-critical.</span></span> <span data-ttu-id="ab3d4-129">Zadání žádného atributu způsobí, že modul CLR (Common Language Runtime) určí pravidla transparentnosti.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-129">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span>

- <span data-ttu-id="ab3d4-130">`SecurityTransparent`: Veškerý kód je transparentní; celé sestavení neprovede žádné privilegované nebo nezabezpečené.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-130">`SecurityTransparent`: All code is transparent; the entire assembly will not do anything privileged or unsafe.</span></span>

- <span data-ttu-id="ab3d4-131">`SecurityCritical`: Všechny kódy, které jsou představeny typy v tomto sestavení, jsou kritické; všechny ostatní kódy jsou transparentní.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-131">`SecurityCritical`: All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="ab3d4-132">Tento scénář je podobný jako při zadávání jakýchkoli atributů; modul CLR (Common Language Runtime) ale neurčuje automaticky pravidla transparentnosti.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-132">This scenario is similar to not specifying any attributes; however, the common language runtime does not automatically determine the transparency rules.</span></span> <span data-ttu-id="ab3d4-133">Například pokud přepíšete virtuální nebo abstraktní metodu nebo implementujete metodu rozhraní, je tato metoda ve výchozím nastavení průhledná.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-133">For example, if you override a virtual or abstract method or implement an interface method, by default, that method is transparent.</span></span> <span data-ttu-id="ab3d4-134">Metodu musíte explicitně opatřit poznámkami jako `SecurityCritical` nebo `SecuritySafeCritical` . v opačném případě <xref:System.TypeLoadException> dojde k vyvolání v době načítání.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-134">You must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`; otherwise, a <xref:System.TypeLoadException> will be thrown at load time.</span></span> <span data-ttu-id="ab3d4-135">Toto pravidlo platí také v případě, že je základní třída i odvozená třída ve stejném sestavení.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-135">This rule also applies when both the base class and the derived class are in the same assembly.</span></span>

- <span data-ttu-id="ab3d4-136">`AllowPartiallyTrustedCallers`(pouze úroveň 2): výchozí hodnota je transparentní pro všechny kódy.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-136">`AllowPartiallyTrustedCallers` (level 2 only): All code defaults to transparent.</span></span> <span data-ttu-id="ab3d4-137">Jednotlivé typy a členy však mohou mít jiné atributy.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-137">However, individual types and members can have other attributes.</span></span>

<span data-ttu-id="ab3d4-138">Následující tabulka porovnává chování na úrovni sestavení pro úroveň 2 s úrovní 1.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-138">The following table compares the assembly level behavior for Level 2 with Level 1.</span></span>

|<span data-ttu-id="ab3d4-139">Atribut Assembly</span><span class="sxs-lookup"><span data-stu-id="ab3d4-139">Assembly attribute</span></span>|<span data-ttu-id="ab3d4-140">Level 2</span><span class="sxs-lookup"><span data-stu-id="ab3d4-140">Level 2</span></span>|<span data-ttu-id="ab3d4-141">úroveň 1</span><span class="sxs-lookup"><span data-stu-id="ab3d4-141">Level 1</span></span>|
|------------------------|-------------|-------------|
|<span data-ttu-id="ab3d4-142">Žádný atribut v částečně důvěryhodném sestavení</span><span class="sxs-lookup"><span data-stu-id="ab3d4-142">No attribute on a partially trusted assembly</span></span>|<span data-ttu-id="ab3d4-143">Typy a členy jsou ve výchozím nastavení transparentní, ale mohou být kritické pro zabezpečení nebo bezpečné – kritické.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-143">Types and members are by default transparent, but can be security-critical or security-safe-critical.</span></span>|<span data-ttu-id="ab3d4-144">Všechny typy a členy jsou transparentní.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-144">All types and members are transparent.</span></span>|
|<span data-ttu-id="ab3d4-145">Žádný atribut</span><span class="sxs-lookup"><span data-stu-id="ab3d4-145">No attribute</span></span>|<span data-ttu-id="ab3d4-146">Zadání žádného atributu způsobí, že modul CLR (Common Language Runtime) určí pravidla transparentnosti.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-146">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span> <span data-ttu-id="ab3d4-147">Všechny typy a členy jsou kritické pro zabezpečení, s výjimkou případů, kdy kritické zabezpečení porušují pravidlo dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-147">All types and members are security-critical, except where being security-critical violates an inheritance rule.</span></span>|<span data-ttu-id="ab3d4-148">V plně důvěryhodném sestavení (v globální mezipaměti sestavení (GAC) nebo identifikovaný jako úplný vztah důvěryhodnosti v rámci `AppDomain` ) jsou všechny typy transparentní a všechny členy jsou bezpečné – kritické.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-148">On a fully trusted assembly (in the global assembly cache or identified as full trust in the `AppDomain`) all types are transparent and all members are security-safe-critical.</span></span>|
|`SecurityTransparent`|<span data-ttu-id="ab3d4-149">Všechny typy a členy jsou transparentní.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-149">All types and members are transparent.</span></span>|<span data-ttu-id="ab3d4-150">Všechny typy a členy jsou transparentní.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-150">All types and members are transparent.</span></span>|
|`SecurityCritical(SecurityCriticalScope.Everything)`|<span data-ttu-id="ab3d4-151">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-151">Not applicable.</span></span>|<span data-ttu-id="ab3d4-152">Všechny typy a členy jsou kritické pro zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-152">All types and members are security-critical.</span></span>|
|`SecurityCritical`|<span data-ttu-id="ab3d4-153">Všechny kódy, které jsou představeny typy v tomto sestavení jsou kritické; všechny ostatní kódy jsou transparentní.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-153">All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="ab3d4-154">Pokud přepíšete virtuální nebo abstraktní metodu nebo implementujete metodu rozhraní, je nutné explicitně opatřit poznámkami metodu jako `SecurityCritical` nebo `SecuritySafeCritical` .</span><span class="sxs-lookup"><span data-stu-id="ab3d4-154">If you override a virtual or abstract method or implement an interface method, you must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`.</span></span>|<span data-ttu-id="ab3d4-155">Veškerý kód je standardně transparentní.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-155">All code defaults to transparent.</span></span> <span data-ttu-id="ab3d4-156">Jednotlivé typy a členy však mohou mít jiné atributy.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-156">However, individual types and members can have other attributes.</span></span>|

### <a name="type-and-member-annotation"></a><span data-ttu-id="ab3d4-157">Typ a Poznámka člena</span><span class="sxs-lookup"><span data-stu-id="ab3d4-157">Type and Member Annotation</span></span>

<span data-ttu-id="ab3d4-158">Atributy zabezpečení použité pro typ platí také pro členy, které jsou zavedeny typem.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-158">The security attributes that are applied to a type also apply to the members that are introduced by the type.</span></span> <span data-ttu-id="ab3d4-159">Neplatí však pro virtuální nebo abstraktní přepsání implementace základní třídy nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-159">However, they do not apply to virtual or abstract overrides of the base class or interface implementations.</span></span> <span data-ttu-id="ab3d4-160">Následující pravidla platí pro použití atributů na úrovni typu a člena:</span><span class="sxs-lookup"><span data-stu-id="ab3d4-160">The following rules apply to the use of attributes at the type and member level:</span></span>

- <span data-ttu-id="ab3d4-161">`SecurityCritical`: Typ nebo člen je kritický a může být volán pouze pomocí plně důvěryhodného kódu.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-161">`SecurityCritical`: The type or member is critical and can be called only by full-trust code.</span></span> <span data-ttu-id="ab3d4-162">Metody, které jsou představeny v typu kritickém pro zabezpečení, jsou kritické.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-162">Methods that are introduced in a security-critical type are critical.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="ab3d4-163">Virtuální a abstraktní metody, které jsou představeny v základních třídách nebo rozhraních a jsou přepsány nebo implementovány ve třídě kritické pro zabezpečení, jsou standardně transparentní.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-163">Virtual and abstract methods that are introduced in base classes or interfaces, and overridden or implemented in a security-critical class are transparent by default.</span></span> <span data-ttu-id="ab3d4-164">Musí být identifikovány buď `SecuritySafeCritical` nebo `SecurityCritical` .</span><span class="sxs-lookup"><span data-stu-id="ab3d4-164">They must be identified as either `SecuritySafeCritical` or `SecurityCritical`.</span></span>

- <span data-ttu-id="ab3d4-165">`SecuritySafeCritical`: Typ nebo člen je v kritickém stavu.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-165">`SecuritySafeCritical`: The type or member is safe-critical.</span></span> <span data-ttu-id="ab3d4-166">Typ nebo člen je však možné volat z transparentního (částečně důvěryhodného) kódu a je stejně schopný jako jakýkoliv jiný kritický kód.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-166">However, the type or member can be called from transparent (partially trusted) code and is as capable as any other critical code.</span></span> <span data-ttu-id="ab3d4-167">Kód musí být auditován z důvodu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-167">The code must be audited for security.</span></span>

## <a name="override-patterns"></a><span data-ttu-id="ab3d4-168">Vzory přepsání</span><span class="sxs-lookup"><span data-stu-id="ab3d4-168">Override Patterns</span></span>

<span data-ttu-id="ab3d4-169">Následující tabulka ukazuje přepsání metody povolené pro transparentnost úrovně 2.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-169">The following table shows the method overrides allowed for level 2 transparency.</span></span>

|<span data-ttu-id="ab3d4-170">Základní člen virtuálního/rozhraní</span><span class="sxs-lookup"><span data-stu-id="ab3d4-170">Base virtual/interface member</span></span>|<span data-ttu-id="ab3d4-171">Přepsat/rozhraní</span><span class="sxs-lookup"><span data-stu-id="ab3d4-171">Override/interface</span></span>|
|------------------------------------|-------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

## <a name="inheritance-rules"></a><span data-ttu-id="ab3d4-172">Pravidla dědičnosti</span><span class="sxs-lookup"><span data-stu-id="ab3d4-172">Inheritance Rules</span></span>

<span data-ttu-id="ab3d4-173">V této části je následující pořadí přiřazeno k `Transparent` kódu, `Critical` a na `SafeCritical` základě přístupu a možností:</span><span class="sxs-lookup"><span data-stu-id="ab3d4-173">In this section, the following order is assigned to `Transparent`, `Critical`, and `SafeCritical` code based on access and capabilities:</span></span>

`Transparent` < `SafeCritical` < `Critical`

- <span data-ttu-id="ab3d4-174">Pravidla pro typy: Přejít zleva doprava a přístup se bude více omezující.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-174">Rules for types: Going from left to right, access becomes more restrictive.</span></span> <span data-ttu-id="ab3d4-175">Odvozené typy musí být alespoň tak omezující jako základní typ.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-175">Derived types must be at least as restrictive as the base type.</span></span>

- <span data-ttu-id="ab3d4-176">Pravidla pro metody: odvozené metody nemohou změnit přístupnost ze základní metody.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-176">Rules for methods: Derived methods cannot change accessibility from the base method.</span></span> <span data-ttu-id="ab3d4-177">Pro výchozí chování jsou všechny odvozené metody, které nejsou opatřeny poznámkami `Transparent` .</span><span class="sxs-lookup"><span data-stu-id="ab3d4-177">For default behavior, all derived methods that are not annotated are `Transparent`.</span></span> <span data-ttu-id="ab3d4-178">Deriváty kritických typů způsobují výjimku, pokud přepsaná metoda není explicitně označena jako `SecurityCritical` .</span><span class="sxs-lookup"><span data-stu-id="ab3d4-178">Derivatives of critical types cause an exception to be thrown if the overridden method is not explicitly annotated as `SecurityCritical`.</span></span>

<span data-ttu-id="ab3d4-179">Následující tabulka uvádí povolené vzory dědičnosti typů.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-179">The following table shows the allowed type inheritance patterns.</span></span>

|<span data-ttu-id="ab3d4-180">Základní třída</span><span class="sxs-lookup"><span data-stu-id="ab3d4-180">Base class</span></span>|<span data-ttu-id="ab3d4-181">Odvozená třída může být</span><span class="sxs-lookup"><span data-stu-id="ab3d4-181">Derived class can be</span></span>|
|----------------|--------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`Transparent`|`Critical`|
|`SafeCritical`|`SafeCritical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Critical`|

<span data-ttu-id="ab3d4-182">V následující tabulce jsou uvedeny nepovolené vzory dědičnosti typů.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-182">The following table shows the disallowed type inheritance patterns.</span></span>

|<span data-ttu-id="ab3d4-183">Základní třída</span><span class="sxs-lookup"><span data-stu-id="ab3d4-183">Base class</span></span>|<span data-ttu-id="ab3d4-184">Odvozená třída nemůže být</span><span class="sxs-lookup"><span data-stu-id="ab3d4-184">Derived class cannot be</span></span>|
|----------------|-----------------------------|
|`SafeCritical`|`Transparent`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

<span data-ttu-id="ab3d4-185">Následující tabulka uvádí povolené vzory dědičnosti metod.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-185">The following table shows the allowed method inheritance patterns.</span></span>

|<span data-ttu-id="ab3d4-186">Základní metoda</span><span class="sxs-lookup"><span data-stu-id="ab3d4-186">Base method</span></span>|<span data-ttu-id="ab3d4-187">Odvozená metoda může být</span><span class="sxs-lookup"><span data-stu-id="ab3d4-187">Derived method can be</span></span>|
|-----------------|---------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

<span data-ttu-id="ab3d4-188">V následující tabulce jsou uvedeny nepovolené vzory dědičnosti metod.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-188">The following table shows the disallowed method inheritance patterns.</span></span>

|<span data-ttu-id="ab3d4-189">Základní metoda</span><span class="sxs-lookup"><span data-stu-id="ab3d4-189">Base method</span></span>|<span data-ttu-id="ab3d4-190">Odvozená metoda nemůže být</span><span class="sxs-lookup"><span data-stu-id="ab3d4-190">Derived method cannot be</span></span>|
|-----------------|------------------------------|
|`Transparent`|`Critical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

> [!NOTE]
> <span data-ttu-id="ab3d4-191">Tato pravidla dědičnosti platí pro typy a členy úrovně 2.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-191">These inheritance rules apply to level 2 types and members.</span></span> <span data-ttu-id="ab3d4-192">Typy v sestaveních úrovně 1 mohou dědit z typů a členů kritických pro zabezpečení úrovně 2.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-192">Types in level 1 assemblies can inherit from level 2 security-critical types and members.</span></span> <span data-ttu-id="ab3d4-193">Typy a členy úrovně 2 proto musí mít samostatné požadavky dědičnosti pro dědice úrovně 1.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-193">Therefore, level 2 types and members must have separate inheritance demands for level 1 inheritors.</span></span>

## <a name="additional-information-and-rules"></a><span data-ttu-id="ab3d4-194">Další informace a pravidla</span><span class="sxs-lookup"><span data-stu-id="ab3d4-194">Additional Information and Rules</span></span>

### <a name="linkdemand-support"></a><span data-ttu-id="ab3d4-195">Podpora LinkDemand</span><span class="sxs-lookup"><span data-stu-id="ab3d4-195">LinkDemand Support</span></span>

<span data-ttu-id="ab3d4-196">Model transparentnosti úrovně 2 nahrazuje <xref:System.Security.Permissions.SecurityAction.LinkDemand> <xref:System.Security.SecurityCriticalAttribute> Atribut atributem.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-196">The level 2 transparency model replaces the <xref:System.Security.Permissions.SecurityAction.LinkDemand> with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="ab3d4-197">Ve starší verzi (úroveň 1) <xref:System.Security.Permissions.SecurityAction.LinkDemand> je automaticky považován za <xref:System.Security.Permissions.SecurityAction.Demand> .</span><span class="sxs-lookup"><span data-stu-id="ab3d4-197">In legacy (level 1) code, a <xref:System.Security.Permissions.SecurityAction.LinkDemand> is automatically treated as a <xref:System.Security.Permissions.SecurityAction.Demand>.</span></span>

### <a name="reflection"></a><span data-ttu-id="ab3d4-198">Reflexe</span><span class="sxs-lookup"><span data-stu-id="ab3d4-198">Reflection</span></span>

<span data-ttu-id="ab3d4-199">Vyvolání kritické metody nebo čtení kritického pole aktivuje požadavek na úplný vztah důvěryhodnosti (stejně jako v případě, že jste vyvolali soukromou metodu nebo pole).</span><span class="sxs-lookup"><span data-stu-id="ab3d4-199">Invoking a critical method or reading a critical field triggers a demand for full trust (just as if you were invoking a private method or field).</span></span> <span data-ttu-id="ab3d4-200">Proto kód s úplným vztahem důvěryhodnosti může vyvolat kritickou metodu, zatímco kód částečného vztahu důvěryhodnosti nemůže.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-200">Therefore, full-trust code can invoke a critical method, whereas partial-trust code cannot.</span></span>

<span data-ttu-id="ab3d4-201">Následující vlastnosti byly přidány do <xref:System.Reflection> oboru názvů, aby bylo možné určit, zda typ, metoda nebo pole jsou `SecurityCritical` , `SecuritySafeCritical` nebo `SecurityTransparent` : <xref:System.Type.IsSecurityCritical%2A> , <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A> , a <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A> .</span><span class="sxs-lookup"><span data-stu-id="ab3d4-201">The following properties have been added to the <xref:System.Reflection> namespace to determine whether the type, method, or field is `SecurityCritical`, `SecuritySafeCritical`, or `SecurityTransparent`:  <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, and <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>.</span></span> <span data-ttu-id="ab3d4-202">Pomocí těchto vlastností lze určit průhlednost pomocí reflexe namísto kontroly přítomnosti atributu.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-202">Use these properties to determine transparency by using reflection instead of checking for the presence of the attribute.</span></span> <span data-ttu-id="ab3d4-203">Pravidla transparentnosti jsou složitá a kontrola atributu nemusí být dostačující.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-203">The transparency rules are complex, and checking for the attribute may not be sufficient.</span></span>

> [!NOTE]
> <span data-ttu-id="ab3d4-204">`SafeCritical`Metoda vrátí `true` pro obojí <xref:System.Type.IsSecurityCritical%2A> a <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A> , protože `SafeCritical` je skutečně kritická (má stejné možnosti jako kritický kód, ale může být volána z transparentního kódu).</span><span class="sxs-lookup"><span data-stu-id="ab3d4-204">A `SafeCritical` method returns `true` for both <xref:System.Type.IsSecurityCritical%2A> and <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, because `SafeCritical` is indeed critical (it has the same capabilities as critical code, but it can be called from transparent code).</span></span>

<span data-ttu-id="ab3d4-205">Dynamické metody dědí průhlednost modulů, ke kterým jsou připojené; nedědí průhlednost typu (pokud jsou připojeny k typu).</span><span class="sxs-lookup"><span data-stu-id="ab3d4-205">Dynamic methods inherit the transparency of the modules they are attached to; they do not inherit the transparency of the type (if they are attached to a type).</span></span>

### <a name="skip-verification-in-full-trust"></a><span data-ttu-id="ab3d4-206">Přeskočit ověřování v úplném vztahu důvěryhodnosti</span><span class="sxs-lookup"><span data-stu-id="ab3d4-206">Skip Verification in Full Trust</span></span>

<span data-ttu-id="ab3d4-207">Můžete přeskočit ověření pro plně důvěryhodná transparentní sestavení nastavením <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> vlastnosti na hodnotu `true` v <xref:System.Security.SecurityRulesAttribute> atributu:</span><span class="sxs-lookup"><span data-stu-id="ab3d4-207">You can skip verification for fully trusted transparent assemblies by setting the <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property to `true` in the <xref:System.Security.SecurityRulesAttribute> attribute:</span></span>

`[assembly: SecurityRules(SecurityRuleSet.Level2, SkipVerificationInFullTrust = true)]`

<span data-ttu-id="ab3d4-208"><xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A>Vlastnost je `false` ve výchozím nastavení, takže vlastnost musí být nastavena na hodnotu `true` pro přeskočení ověření.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-208">The <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property is `false` by default, so the property must be set to `true` to skip verification.</span></span> <span data-ttu-id="ab3d4-209">Tato operace by se měla provádět jenom pro účely optimalizace.</span><span class="sxs-lookup"><span data-stu-id="ab3d4-209">This should be done for optimization purposes only.</span></span> <span data-ttu-id="ab3d4-210">Je nutné zajistit, aby transparentní kód v sestavení byl ověřen pomocí `transparent` Možnosti v [nástroji Nástroj PEVerify](../tools/peverify-exe-peverify-tool.md).</span><span class="sxs-lookup"><span data-stu-id="ab3d4-210">You should ensure that the transparent code in the assembly is verifiable by using the `transparent` option in the [PEVerify tool](../tools/peverify-exe-peverify-tool.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ab3d4-211">Viz také</span><span class="sxs-lookup"><span data-stu-id="ab3d4-211">See also</span></span>

- [<span data-ttu-id="ab3d4-212">Kód transparentní pro zabezpečení, úroveň 1</span><span class="sxs-lookup"><span data-stu-id="ab3d4-212">Security-Transparent Code, Level 1</span></span>](security-transparent-code-level-1.md)
- [<span data-ttu-id="ab3d4-213">Změny zabezpečení</span><span class="sxs-lookup"><span data-stu-id="ab3d4-213">Security Changes</span></span>](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes)
