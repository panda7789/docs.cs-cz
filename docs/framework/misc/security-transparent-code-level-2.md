---
title: Transparentní kód pro zabezpečení, úroveň 2
ms.date: 03/30/2017
helpviewer_keywords:
- transparency
- level 2 transparency
- security-transparent code
- security-critical code
ms.assetid: 4d05610a-0da6-4f08-acea-d54c9d6143c0
ms.openlocfilehash: 12e991e4977b0866343158c05681ddf4bd0c869b
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645734"
---
# <a name="security-transparent-code-level-2"></a><span data-ttu-id="cae69-102">Transparentní kód pro zabezpečení, úroveň 2</span><span class="sxs-lookup"><span data-stu-id="cae69-102">Security-Transparent Code, Level 2</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="cae69-103">Transparentnost úrovně 2 byla zavedena v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="cae69-103">Level 2 transparency was introduced in the .NET Framework 4.</span></span> <span data-ttu-id="cae69-104">Tři principy tohoto modelu jsou transparentní kód, bezpečný a kritický kód zabezpečení a kód kritický pro zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="cae69-104">The three tenets of this model are transparent code, security-safe-critical code, and security-critical code.</span></span>

- <span data-ttu-id="cae69-105">Transparentní kód, včetně kódu, který je spuštěn jako úplný vztah důvěryhodnosti, může volat pouze jiný transparentní kód nebo kód bezpečný a kritický pro zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="cae69-105">Transparent code, including code that is running as full trust, can call other transparent code or security-safe-critical code only.</span></span> <span data-ttu-id="cae69-106">Může provádět pouze akce povolené sadou oprávnění částečné důvěryhodnosti domény (pokud existuje).</span><span class="sxs-lookup"><span data-stu-id="cae69-106">It can only perform actions allowed by the domain’s partial trust permission set (if one exists).</span></span> <span data-ttu-id="cae69-107">Transparentní kód nemůže provést následující akce:</span><span class="sxs-lookup"><span data-stu-id="cae69-107">Transparent code cannot do the following:</span></span>

  - <span data-ttu-id="cae69-108">Proveďte <xref:System.Security.CodeAccessPermission.Assert%2A> zvýšení oprávnění nebo zvýšení oprávnění.</span><span class="sxs-lookup"><span data-stu-id="cae69-108">Perform an <xref:System.Security.CodeAccessPermission.Assert%2A> or elevation of privilege.</span></span>

  - <span data-ttu-id="cae69-109">Obsahují nebezpečný nebo neověřitelný kód.</span><span class="sxs-lookup"><span data-stu-id="cae69-109">Contain unsafe or unverifiable code.</span></span>

  - <span data-ttu-id="cae69-110">Přímo volejte kritický kód.</span><span class="sxs-lookup"><span data-stu-id="cae69-110">Directly call critical code.</span></span>

  - <span data-ttu-id="cae69-111">Volání nativního kódu <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> nebo kódu s atributem.</span><span class="sxs-lookup"><span data-stu-id="cae69-111">Call native code or code with the <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attribute.</span></span>

  - <span data-ttu-id="cae69-112">Volání člena, který je <xref:System.Security.Permissions.SecurityAction.LinkDemand>chráněn .</span><span class="sxs-lookup"><span data-stu-id="cae69-112">Call a member that is protected by a <xref:System.Security.Permissions.SecurityAction.LinkDemand>.</span></span>

  - <span data-ttu-id="cae69-113">Dědit z kritických typů.</span><span class="sxs-lookup"><span data-stu-id="cae69-113">Inherit from critical types.</span></span>

  <span data-ttu-id="cae69-114">Kromě toho transparentní metody nelze přepsat kritické virtuální metody nebo implementovat kritické metody rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cae69-114">In addition, transparent methods cannot override critical virtual methods or implement critical interface methods.</span></span>

- <span data-ttu-id="cae69-115">Bezpečný kritický kód je plně důvěryhodný, ale je volatelný transparentním kódem.</span><span class="sxs-lookup"><span data-stu-id="cae69-115">Safe-critical code is fully trusted but is callable by transparent code.</span></span> <span data-ttu-id="cae69-116">Poskytuje omezenou plochu plně důvěryhodného kódu; správnost a ověření bezpečnosti se děje v bezpečném kritickém kódu.</span><span class="sxs-lookup"><span data-stu-id="cae69-116">It exposes a limited surface area of full-trust code; correctness and security verifications happen in safe-critical code.</span></span>

- <span data-ttu-id="cae69-117">Kód kritický pro zabezpečení může volat libovolný kód a je plně důvěryhodný, ale nelze jej volat transparentním kódem.</span><span class="sxs-lookup"><span data-stu-id="cae69-117">Security-critical code can call any code and is fully trusted, but it cannot be called by transparent code.</span></span>

## <a name="usage-examples-and-behaviors"></a><span data-ttu-id="cae69-118">Příklady použití a chování</span><span class="sxs-lookup"><span data-stu-id="cae69-118">Usage Examples and Behaviors</span></span>

<span data-ttu-id="cae69-119">Chcete-li zadat pravidla rozhraní .NET Framework 4 (průhlednost úrovně 2), použijte pro sestavení následující poznámku:</span><span class="sxs-lookup"><span data-stu-id="cae69-119">To specify .NET Framework 4 rules (level 2 transparency), use the following annotation for an assembly:</span></span>

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level2)]
```

<span data-ttu-id="cae69-120">Chcete-li zamknout do pravidel rozhraní .NET Framework 2.0 (průhlednost úrovně 1), použijte následující poznámku:</span><span class="sxs-lookup"><span data-stu-id="cae69-120">To lock into the .NET Framework 2.0 rules (level 1 transparency), use the following annotation:</span></span>

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level1)]
```

<span data-ttu-id="cae69-121">Pokud neopatříte onotovat sestavení, pravidla rozhraní .NET Framework 4 se používají ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="cae69-121">If you do not annotate an assembly, the .NET Framework 4 rules are used by default.</span></span> <span data-ttu-id="cae69-122">Doporučeným osvědčeným postupem je <xref:System.Security.SecurityRulesAttribute> však použít atribut namísto v závislosti na výchozí.</span><span class="sxs-lookup"><span data-stu-id="cae69-122">However, the recommended best practice is to use the <xref:System.Security.SecurityRulesAttribute> attribute instead of depending on the default.</span></span>

### <a name="assembly-wide-annotation"></a><span data-ttu-id="cae69-123">Anotace pro celou sestavu</span><span class="sxs-lookup"><span data-stu-id="cae69-123">Assembly-wide Annotation</span></span>

<span data-ttu-id="cae69-124">Následující pravidla platí pro použití atributů na úrovni sestavení:</span><span class="sxs-lookup"><span data-stu-id="cae69-124">The following rules apply to the use of attributes at the assembly level:</span></span>

- <span data-ttu-id="cae69-125">Žádné atributy: Pokud nezadáte žádné atributy, modul runtime interpretuje veškerý kód jako kritický pro zabezpečení, s výjimkou případů, kdy kritické pro zabezpečení porušuje pravidlo dědičnosti (například při přepsání nebo implementaci transparentní virtuální metody nebo metody rozhraní).</span><span class="sxs-lookup"><span data-stu-id="cae69-125">No attributes: If you do not specify any attributes, the runtime interprets all code as security-critical, except where being security-critical violates an inheritance rule (for example, when overriding or implementing a transparent virtual or interface method).</span></span> <span data-ttu-id="cae69-126">V těchto případech jsou metody bezpečné kritické.</span><span class="sxs-lookup"><span data-stu-id="cae69-126">In those cases, the methods are safe-critical.</span></span> <span data-ttu-id="cae69-127">Zadání žádného atributu způsobí, že za vás určuje pravidla průhlednosti běžný jazyk.</span><span class="sxs-lookup"><span data-stu-id="cae69-127">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span>

- <span data-ttu-id="cae69-128">`SecurityTransparent`: Veškerý kód je transparentní; celé sestavení nebude dělat nic privilegovaného nebo nebezpečného.</span><span class="sxs-lookup"><span data-stu-id="cae69-128">`SecurityTransparent`: All code is transparent; the entire assembly will not do anything privileged or unsafe.</span></span>

- <span data-ttu-id="cae69-129">`SecurityCritical`: Veškerý kód, který je zaveden typy v tomto sestavení je kritická; všechny ostatní kódy jsou transparentní.</span><span class="sxs-lookup"><span data-stu-id="cae69-129">`SecurityCritical`: All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="cae69-130">Tento scénář je podobný nezadávejte žádné atributy; běžný jazyk runtime však automaticky neurčuje pravidla transparentnosti.</span><span class="sxs-lookup"><span data-stu-id="cae69-130">This scenario is similar to not specifying any attributes; however, the common language runtime does not automatically determine the transparency rules.</span></span> <span data-ttu-id="cae69-131">Například pokud přepsat virtuální nebo abstraktní metody nebo implementovat metodu rozhraní, ve výchozím nastavení, tato metoda je transparentní.</span><span class="sxs-lookup"><span data-stu-id="cae69-131">For example, if you override a virtual or abstract method or implement an interface method, by default, that method is transparent.</span></span> <span data-ttu-id="cae69-132">Je nutné explicitně anotovat `SecurityCritical` `SecuritySafeCritical`metodu jako nebo ; v opačném <xref:System.TypeLoadException> případě bude vyvolána v době načítání.</span><span class="sxs-lookup"><span data-stu-id="cae69-132">You must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`; otherwise, a <xref:System.TypeLoadException> will be thrown at load time.</span></span> <span data-ttu-id="cae69-133">Toto pravidlo platí také v případě, že základní třída a odvozené třídy jsou ve stejném sestavení.</span><span class="sxs-lookup"><span data-stu-id="cae69-133">This rule also applies when both the base class and the derived class are in the same assembly.</span></span>

- <span data-ttu-id="cae69-134">`AllowPartiallyTrustedCallers`(pouze úroveň 2): Všechny výchozí kódy jsou průhledné.</span><span class="sxs-lookup"><span data-stu-id="cae69-134">`AllowPartiallyTrustedCallers` (level 2 only): All code defaults to transparent.</span></span> <span data-ttu-id="cae69-135">Jednotlivé typy a členové však mohou mít jiné atributy.</span><span class="sxs-lookup"><span data-stu-id="cae69-135">However, individual types and members can have other attributes.</span></span>

<span data-ttu-id="cae69-136">Následující tabulka porovnává chování na úrovni sestavy pro úroveň 2 s úrovní 1.</span><span class="sxs-lookup"><span data-stu-id="cae69-136">The following table compares the assembly level behavior for Level 2 with Level 1.</span></span>

|<span data-ttu-id="cae69-137">Atribut sestavení</span><span class="sxs-lookup"><span data-stu-id="cae69-137">Assembly attribute</span></span>|<span data-ttu-id="cae69-138">Level 2</span><span class="sxs-lookup"><span data-stu-id="cae69-138">Level 2</span></span>|<span data-ttu-id="cae69-139">úroveň 1</span><span class="sxs-lookup"><span data-stu-id="cae69-139">Level 1</span></span>|
|------------------------|-------------|-------------|
|<span data-ttu-id="cae69-140">Žádný atribut v částečně důvěryhodném sestavení</span><span class="sxs-lookup"><span data-stu-id="cae69-140">No attribute on a partially trusted assembly</span></span>|<span data-ttu-id="cae69-141">Typy a členy jsou ve výchozím nastavení transparentní, ale mohou být kritické pro zabezpečení nebo bezpečné a kritické pro zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="cae69-141">Types and members are by default transparent, but can be security-critical or security-safe-critical.</span></span>|<span data-ttu-id="cae69-142">Všechny typy a členy jsou transparentní.</span><span class="sxs-lookup"><span data-stu-id="cae69-142">All types and members are transparent.</span></span>|
|<span data-ttu-id="cae69-143">Žádný atribut</span><span class="sxs-lookup"><span data-stu-id="cae69-143">No attribute</span></span>|<span data-ttu-id="cae69-144">Zadání žádného atributu způsobí, že za vás určuje pravidla průhlednosti běžný jazyk.</span><span class="sxs-lookup"><span data-stu-id="cae69-144">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span> <span data-ttu-id="cae69-145">Všechny typy a členy jsou kritické pro zabezpečení, s výjimkou případů, kdy je kritické pro zabezpečení porušuje pravidlo dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="cae69-145">All types and members are security-critical, except where being security-critical violates an inheritance rule.</span></span>|<span data-ttu-id="cae69-146">V plně důvěryhodném sestavení (v globální mezipaměti sestavení `AppDomain`nebo identifikované jako úplný vztah důvěryhodnosti v ) jsou všechny typy transparentní a všechny členy jsou kritické pro zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="cae69-146">On a fully trusted assembly (in the global assembly cache or identified as full trust in the `AppDomain`) all types are transparent and all members are security-safe-critical.</span></span>|
|`SecurityTransparent`|<span data-ttu-id="cae69-147">Všechny typy a členy jsou transparentní.</span><span class="sxs-lookup"><span data-stu-id="cae69-147">All types and members are transparent.</span></span>|<span data-ttu-id="cae69-148">Všechny typy a členy jsou transparentní.</span><span class="sxs-lookup"><span data-stu-id="cae69-148">All types and members are transparent.</span></span>|
|`SecurityCritical(SecurityCriticalScope.Everything)`|<span data-ttu-id="cae69-149">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="cae69-149">Not applicable.</span></span>|<span data-ttu-id="cae69-150">Všechny typy a členy jsou kritické pro zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="cae69-150">All types and members are security-critical.</span></span>|
|`SecurityCritical`|<span data-ttu-id="cae69-151">Veškerý kód, který je zaveden typy v tomto sestavení je kritická; všechny ostatní kódy jsou transparentní.</span><span class="sxs-lookup"><span data-stu-id="cae69-151">All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="cae69-152">Pokud přepíšete virtuální nebo abstraktní metodu nebo implementujete metodu `SecurityCritical` rozhraní, musíte metodu explicitně oznamovat jako nebo `SecuritySafeCritical`.</span><span class="sxs-lookup"><span data-stu-id="cae69-152">If you override a virtual or abstract method or implement an interface method, you must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`.</span></span>|<span data-ttu-id="cae69-153">Všechny kód výchozí transparentní.</span><span class="sxs-lookup"><span data-stu-id="cae69-153">All code defaults to transparent.</span></span> <span data-ttu-id="cae69-154">Jednotlivé typy a členové však mohou mít jiné atributy.</span><span class="sxs-lookup"><span data-stu-id="cae69-154">However, individual types and members can have other attributes.</span></span>|

### <a name="type-and-member-annotation"></a><span data-ttu-id="cae69-155">Typ a anotace členů</span><span class="sxs-lookup"><span data-stu-id="cae69-155">Type and Member Annotation</span></span>

<span data-ttu-id="cae69-156">Atributy zabezpečení, které jsou použity pro typ platí také pro členy, které jsou zavedeny typu.</span><span class="sxs-lookup"><span data-stu-id="cae69-156">The security attributes that are applied to a type also apply to the members that are introduced by the type.</span></span> <span data-ttu-id="cae69-157">Však se nevztahují na virtuální nebo abstraktní přepsání základní třídy nebo implementace rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cae69-157">However, they do not apply to virtual or abstract overrides of the base class or interface implementations.</span></span> <span data-ttu-id="cae69-158">Pro použití atributů na úrovni typu a člena platí následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="cae69-158">The following rules apply to the use of attributes at the type and member level:</span></span>

- <span data-ttu-id="cae69-159">`SecurityCritical`: Typ nebo člen je kritický a může být volán pouze úplným důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="cae69-159">`SecurityCritical`: The type or member is critical and can be called only by full-trust code.</span></span> <span data-ttu-id="cae69-160">Metody, které jsou zavedeny v typu kritické pro zabezpečení jsou kritické.</span><span class="sxs-lookup"><span data-stu-id="cae69-160">Methods that are introduced in a security-critical type are critical.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="cae69-161">Virtuální a abstraktní metody, které jsou zavedeny v základních třídách nebo rozhraních a přepsány nebo implementovány ve třídě kritické pro zabezpečení, jsou ve výchozím nastavení transparentní.</span><span class="sxs-lookup"><span data-stu-id="cae69-161">Virtual and abstract methods that are introduced in base classes or interfaces, and overridden or implemented in a security-critical class are transparent by default.</span></span> <span data-ttu-id="cae69-162">Musí být identifikovány `SecuritySafeCritical` `SecurityCritical`jako buď nebo .</span><span class="sxs-lookup"><span data-stu-id="cae69-162">They must be identified as either `SecuritySafeCritical` or `SecurityCritical`.</span></span>

- <span data-ttu-id="cae69-163">`SecuritySafeCritical`: Typ nebo člen je bezpečný kritický.</span><span class="sxs-lookup"><span data-stu-id="cae69-163">`SecuritySafeCritical`: The type or member is safe-critical.</span></span> <span data-ttu-id="cae69-164">Typ nebo člen však lze volat z transparentního (částečně důvěryhodného) kódu a je stejně schopný jako jakýkoli jiný kritický kód.</span><span class="sxs-lookup"><span data-stu-id="cae69-164">However, the type or member can be called from transparent (partially trusted) code and is as capable as any other critical code.</span></span> <span data-ttu-id="cae69-165">Kód musí být auditován z důvodu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="cae69-165">The code must be audited for security.</span></span>

## <a name="override-patterns"></a><span data-ttu-id="cae69-166">Přepsat vzorky</span><span class="sxs-lookup"><span data-stu-id="cae69-166">Override Patterns</span></span>

<span data-ttu-id="cae69-167">V následující tabulce jsou uvedeny přepsání metody povolené pro průhlednost úrovně 2.</span><span class="sxs-lookup"><span data-stu-id="cae69-167">The following table shows the method overrides allowed for level 2 transparency.</span></span>

|<span data-ttu-id="cae69-168">Základní člen virtuálního/rozhraní</span><span class="sxs-lookup"><span data-stu-id="cae69-168">Base virtual/interface member</span></span>|<span data-ttu-id="cae69-169">Přepsat/rozhraní</span><span class="sxs-lookup"><span data-stu-id="cae69-169">Override/interface</span></span>|
|------------------------------------|-------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

## <a name="inheritance-rules"></a><span data-ttu-id="cae69-170">Pravidla dědičnosti</span><span class="sxs-lookup"><span data-stu-id="cae69-170">Inheritance Rules</span></span>

<span data-ttu-id="cae69-171">V této části je přiřazena `Transparent` `Critical`následující `SafeCritical` objednávka , a kód založený na přístupu a možnostech:</span><span class="sxs-lookup"><span data-stu-id="cae69-171">In this section, the following order is assigned to `Transparent`, `Critical`, and `SafeCritical` code based on access and capabilities:</span></span>

`Transparent` < `SafeCritical` < `Critical`

- <span data-ttu-id="cae69-172">Pravidla pro typy: Chystáte se zleva doprava, přístup se stává více omezující.</span><span class="sxs-lookup"><span data-stu-id="cae69-172">Rules for types: Going from left to right, access becomes more restrictive.</span></span> <span data-ttu-id="cae69-173">Odvozené typy musí být alespoň stejně omezující jako základní typ.</span><span class="sxs-lookup"><span data-stu-id="cae69-173">Derived types must be at least as restrictive as the base type.</span></span>

- <span data-ttu-id="cae69-174">Pravidla pro metody: Odvozené metody nemohou změnit usnadnění přístupu ze základní metody.</span><span class="sxs-lookup"><span data-stu-id="cae69-174">Rules for methods: Derived methods cannot change accessibility from the base method.</span></span> <span data-ttu-id="cae69-175">Pro výchozí chování jsou `Transparent`všechny odvozené metody, které nejsou anotovány.</span><span class="sxs-lookup"><span data-stu-id="cae69-175">For default behavior, all derived methods that are not annotated are `Transparent`.</span></span> <span data-ttu-id="cae69-176">Derivace kritických typů způsobit výjimku vyvolat, pokud potlačené metody `SecurityCritical`není explicitně anotován jako .</span><span class="sxs-lookup"><span data-stu-id="cae69-176">Derivatives of critical types cause an exception to be thrown if the overridden method is not explicitly annotated as `SecurityCritical`.</span></span>

<span data-ttu-id="cae69-177">V následující tabulce jsou uvedeny vzorky dědičnosti povolených typů.</span><span class="sxs-lookup"><span data-stu-id="cae69-177">The following table shows the allowed type inheritance patterns.</span></span>

|<span data-ttu-id="cae69-178">Základní třída</span><span class="sxs-lookup"><span data-stu-id="cae69-178">Base class</span></span>|<span data-ttu-id="cae69-179">Odvozenou třídu lze</span><span class="sxs-lookup"><span data-stu-id="cae69-179">Derived class can be</span></span>|
|----------------|--------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`Transparent`|`Critical`|
|`SafeCritical`|`SafeCritical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Critical`|

<span data-ttu-id="cae69-180">V následující tabulce jsou uvedeny nepovolené vzory dědičnosti typu.</span><span class="sxs-lookup"><span data-stu-id="cae69-180">The following table shows the disallowed type inheritance patterns.</span></span>

|<span data-ttu-id="cae69-181">Základní třída</span><span class="sxs-lookup"><span data-stu-id="cae69-181">Base class</span></span>|<span data-ttu-id="cae69-182">Odvozenou třídu nelze</span><span class="sxs-lookup"><span data-stu-id="cae69-182">Derived class cannot be</span></span>|
|----------------|-----------------------------|
|`SafeCritical`|`Transparent`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

<span data-ttu-id="cae69-183">V následující tabulce jsou uvedeny vzory dědičnosti povolené metody.</span><span class="sxs-lookup"><span data-stu-id="cae69-183">The following table shows the allowed method inheritance patterns.</span></span>

|<span data-ttu-id="cae69-184">Základní metoda</span><span class="sxs-lookup"><span data-stu-id="cae69-184">Base method</span></span>|<span data-ttu-id="cae69-185">Odvozenou metodu lze</span><span class="sxs-lookup"><span data-stu-id="cae69-185">Derived method can be</span></span>|
|-----------------|---------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

<span data-ttu-id="cae69-186">V následující tabulce jsou uvedeny vzorky dědičnosti metody, která nejsou povolena.</span><span class="sxs-lookup"><span data-stu-id="cae69-186">The following table shows the disallowed method inheritance patterns.</span></span>

|<span data-ttu-id="cae69-187">Základní metoda</span><span class="sxs-lookup"><span data-stu-id="cae69-187">Base method</span></span>|<span data-ttu-id="cae69-188">Odvozenou metodu nelze</span><span class="sxs-lookup"><span data-stu-id="cae69-188">Derived method cannot be</span></span>|
|-----------------|------------------------------|
|`Transparent`|`Critical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

> [!NOTE]
> <span data-ttu-id="cae69-189">Tato pravidla dědičnosti platí pro typy a členy úrovně 2.</span><span class="sxs-lookup"><span data-stu-id="cae69-189">These inheritance rules apply to level 2 types and members.</span></span> <span data-ttu-id="cae69-190">Typy v sestaveních úrovně 1 mohou dědit z typů a členů kriticképro zabezpečení úrovně 2.</span><span class="sxs-lookup"><span data-stu-id="cae69-190">Types in level 1 assemblies can inherit from level 2 security-critical types and members.</span></span> <span data-ttu-id="cae69-191">Proto úroveň 2 typy a členy musí mít samostatné požadavky dědičnosti pro úroveň 1 dědiců.</span><span class="sxs-lookup"><span data-stu-id="cae69-191">Therefore, level 2 types and members must have separate inheritance demands for level 1 inheritors.</span></span>

## <a name="additional-information-and-rules"></a><span data-ttu-id="cae69-192">Další informace a pravidla</span><span class="sxs-lookup"><span data-stu-id="cae69-192">Additional Information and Rules</span></span>

### <a name="linkdemand-support"></a><span data-ttu-id="cae69-193">Podpora linkpoptávky</span><span class="sxs-lookup"><span data-stu-id="cae69-193">LinkDemand Support</span></span>

<span data-ttu-id="cae69-194">Model průhlednosti úrovně 2 <xref:System.Security.Permissions.SecurityAction.LinkDemand> nahradí <xref:System.Security.SecurityCriticalAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="cae69-194">The level 2 transparency model replaces the <xref:System.Security.Permissions.SecurityAction.LinkDemand> with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="cae69-195">Ve starším kódu (úroveň <xref:System.Security.Permissions.SecurityAction.LinkDemand> 1) je <xref:System.Security.Permissions.SecurityAction.Demand>a automaticky považována za .</span><span class="sxs-lookup"><span data-stu-id="cae69-195">In legacy (level 1) code, a <xref:System.Security.Permissions.SecurityAction.LinkDemand> is automatically treated as a <xref:System.Security.Permissions.SecurityAction.Demand>.</span></span>

### <a name="reflection"></a><span data-ttu-id="cae69-196">Reflexe</span><span class="sxs-lookup"><span data-stu-id="cae69-196">Reflection</span></span>

<span data-ttu-id="cae69-197">Vyvolání kritické metody nebo čtení kritického pole spustí požadavek na úplný vztah důvěryhodnosti (stejně jako byste vyvolávali soukromou metodu nebo pole).</span><span class="sxs-lookup"><span data-stu-id="cae69-197">Invoking a critical method or reading a critical field triggers a demand for full trust (just as if you were invoking a private method or field).</span></span> <span data-ttu-id="cae69-198">Proto plně důvěryhodný kód může vyvolat kritickou metodu, zatímco kód s částečnou důvěryhodností nemůže.</span><span class="sxs-lookup"><span data-stu-id="cae69-198">Therefore, full-trust code can invoke a critical method, whereas partial-trust code cannot.</span></span>

<span data-ttu-id="cae69-199">Do <xref:System.Reflection> oboru názvů byly přidány následující vlastnosti, které určují, `SecurityCritical`zda `SecuritySafeCritical`je `SecurityTransparent` <xref:System.Type.IsSecurityCritical%2A>typ, metoda nebo pole , , nebo : , <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, a <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>.</span><span class="sxs-lookup"><span data-stu-id="cae69-199">The following properties have been added to the <xref:System.Reflection> namespace to determine whether the type, method, or field is `SecurityCritical`, `SecuritySafeCritical`, or `SecurityTransparent`:  <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, and <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>.</span></span> <span data-ttu-id="cae69-200">Tyto vlastnosti slouží k určení průhlednosti pomocí odrazu namísto kontroly přítomnosti atributu.</span><span class="sxs-lookup"><span data-stu-id="cae69-200">Use these properties to determine transparency by using reflection instead of checking for the presence of the attribute.</span></span> <span data-ttu-id="cae69-201">Pravidla transparentnosti jsou složitá a kontrola atributu nemusí být dostatečná.</span><span class="sxs-lookup"><span data-stu-id="cae69-201">The transparency rules are complex, and checking for the attribute may not be sufficient.</span></span>

> [!NOTE]
> <span data-ttu-id="cae69-202">Metoda `SafeCritical` vrátí `true` pro <xref:System.Type.IsSecurityCritical%2A> <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>oba `SafeCritical` a , protože je skutečně důležité (má stejné možnosti jako kritický kód, ale může být volána z transparentní kód).</span><span class="sxs-lookup"><span data-stu-id="cae69-202">A `SafeCritical` method returns `true` for both <xref:System.Type.IsSecurityCritical%2A> and <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, because `SafeCritical` is indeed critical (it has the same capabilities as critical code, but it can be called from transparent code).</span></span>

<span data-ttu-id="cae69-203">Dynamické metody dědí průhlednost modulů, ke kterým jsou připojeny; nedědí průhlednost typu (pokud jsou připojeny k typu).</span><span class="sxs-lookup"><span data-stu-id="cae69-203">Dynamic methods inherit the transparency of the modules they are attached to; they do not inherit the transparency of the type (if they are attached to a type).</span></span>

### <a name="skip-verification-in-full-trust"></a><span data-ttu-id="cae69-204">Přeskočit ověření v plné důvěře</span><span class="sxs-lookup"><span data-stu-id="cae69-204">Skip Verification in Full Trust</span></span>

<span data-ttu-id="cae69-205">Ověření plně důvěryhodných průhledných sestavení můžete <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> přeskočit `true` nastavením vlastnosti v atributu: <xref:System.Security.SecurityRulesAttribute></span><span class="sxs-lookup"><span data-stu-id="cae69-205">You can skip verification for fully trusted transparent assemblies by setting the <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property to `true` in the <xref:System.Security.SecurityRulesAttribute> attribute:</span></span>

`[assembly: SecurityRules(SecurityRuleSet.Level2, SkipVerificationInFullTrust = true)]`

<span data-ttu-id="cae69-206">Vlastnost <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> je `false` ve výchozím nastavení, takže `true` vlastnost musí být nastavena na přeskočit ověření.</span><span class="sxs-lookup"><span data-stu-id="cae69-206">The <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property is `false` by default, so the property must be set to `true` to skip verification.</span></span> <span data-ttu-id="cae69-207">To by mělo být provedeno pouze pro účely optimalizace.</span><span class="sxs-lookup"><span data-stu-id="cae69-207">This should be done for optimization purposes only.</span></span> <span data-ttu-id="cae69-208">Měli byste zajistit, že transparentní kód v sestavení je `transparent` ověřitelný pomocí možnosti v [nástroji PEVerify](../tools/peverify-exe-peverify-tool.md).</span><span class="sxs-lookup"><span data-stu-id="cae69-208">You should ensure that the transparent code in the assembly is verifiable by using the `transparent` option in the [PEVerify tool](../tools/peverify-exe-peverify-tool.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cae69-209">Viz také</span><span class="sxs-lookup"><span data-stu-id="cae69-209">See also</span></span>

- [<span data-ttu-id="cae69-210">Transparentní kód zabezpečení, úroveň 1</span><span class="sxs-lookup"><span data-stu-id="cae69-210">Security-Transparent Code, Level 1</span></span>](security-transparent-code-level-1.md)
- [<span data-ttu-id="cae69-211">Změny zabezpečení</span><span class="sxs-lookup"><span data-stu-id="cae69-211">Security Changes</span></span>](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes)
