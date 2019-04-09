---
title: Transparentní kód pro zabezpečení, úroveň 2
ms.date: 03/30/2017
helpviewer_keywords:
- transparency
- level 2 transparency
- security-transparent code
- security-critical code
ms.assetid: 4d05610a-0da6-4f08-acea-d54c9d6143c0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 62c25b14fa7b3867bbdbcb2f1e08cc16ce349e72
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59156075"
---
# <a name="security-transparent-code-level-2"></a><span data-ttu-id="09e67-102">Transparentní kód pro zabezpečení, úroveň 2</span><span class="sxs-lookup"><span data-stu-id="09e67-102">Security-Transparent Code, Level 2</span></span>
<a name="top"></a>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="09e67-103">Průhlednost úrovně 2 byla zavedena v [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="09e67-103">Level 2 transparency was introduced in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="09e67-104">Tři zásady tohoto modelu jsou transparentní kód, bezpečný a kritický pro zabezpečení kód a kód kritický pro zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="09e67-104">The three tenets of this model are transparent code, security-safe-critical code, and security-critical code.</span></span>  
  
-   <span data-ttu-id="09e67-105">Transparentní kód, včetně kód, který je spuštěn při úplném vztahu důvěryhodnosti, můžete volat jiný transparentní kód nebo bezpečný a kritický pro zabezpečení pouze kód.</span><span class="sxs-lookup"><span data-stu-id="09e67-105">Transparent code, including code that is running as full trust, can call other transparent code or security-safe-critical code only.</span></span> <span data-ttu-id="09e67-106">Může pouze provádět akce povolené oprávnění částečným vztahem důvěryhodnosti domény nastavení (pokud existuje).</span><span class="sxs-lookup"><span data-stu-id="09e67-106">It can only perform actions allowed by the domain’s partial trust permission set (if one exists).</span></span> <span data-ttu-id="09e67-107">Transparentní kód nemůže provádět následující:</span><span class="sxs-lookup"><span data-stu-id="09e67-107">Transparent code cannot do the following:</span></span>  
  
    -   <span data-ttu-id="09e67-108">Provést <xref:System.Security.CodeAccessPermission.Assert%2A> nebo zvýšení oprávnění.</span><span class="sxs-lookup"><span data-stu-id="09e67-108">Perform an <xref:System.Security.CodeAccessPermission.Assert%2A> or elevation of privilege.</span></span>  
  
    -   <span data-ttu-id="09e67-109">Obsahovat nebezpečný nebo neověřitelný kód.</span><span class="sxs-lookup"><span data-stu-id="09e67-109">Contain unsafe or unverifiable code.</span></span>  
  
    -   <span data-ttu-id="09e67-110">Přímo volejte kritický kód.</span><span class="sxs-lookup"><span data-stu-id="09e67-110">Directly call critical code.</span></span>  
  
    -   <span data-ttu-id="09e67-111">Volat nativní kód nebo kód s <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="09e67-111">Call native code or code with the <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attribute.</span></span>  
  
    -   <span data-ttu-id="09e67-112">Volat člen, který je chráněn <xref:System.Security.Permissions.SecurityAction.LinkDemand>.</span><span class="sxs-lookup"><span data-stu-id="09e67-112">Call a member that is protected by a <xref:System.Security.Permissions.SecurityAction.LinkDemand>.</span></span>  
  
    -   <span data-ttu-id="09e67-113">Dědit z kritických typů.</span><span class="sxs-lookup"><span data-stu-id="09e67-113">Inherit from critical types.</span></span>  
  
     <span data-ttu-id="09e67-114">Kromě toho transparentní metody nelze přepsat kritické virtuální metody nebo implementovat kritické metody rozhraní.</span><span class="sxs-lookup"><span data-stu-id="09e67-114">In addition, transparent methods cannot override critical virtual methods or implement critical interface methods.</span></span>  
  
-   <span data-ttu-id="09e67-115">Bezpečný a kritický kód je plně důvěryhodný, ale je volatelný transparentním kódem.</span><span class="sxs-lookup"><span data-stu-id="09e67-115">Safe-critical code is fully trusted but is callable by transparent code.</span></span> <span data-ttu-id="09e67-116">Zpřístupňuje omezenou oblast povrchu plně důvěryhodného kódu; ověření správnosti a zabezpečení dojde v bezpečný a kritický kód.</span><span class="sxs-lookup"><span data-stu-id="09e67-116">It exposes a limited surface area of full-trust code; correctness and security verifications happen in safe-critical code.</span></span>  
  
-   <span data-ttu-id="09e67-117">Kód kritický pro zabezpečení může volat libovolný kód a je plně důvěryhodný, ale nemůže být volán transparentním kódem.</span><span class="sxs-lookup"><span data-stu-id="09e67-117">Security-critical code can call any code and is fully trusted, but it cannot be called by transparent code.</span></span>  
  
 <span data-ttu-id="09e67-118">Toto téma obsahuje následující oddíly:</span><span class="sxs-lookup"><span data-stu-id="09e67-118">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="09e67-119">Příklady použití a chování</span><span class="sxs-lookup"><span data-stu-id="09e67-119">Usage Examples and Behaviors</span></span>](#examples)  
  
-   [<span data-ttu-id="09e67-120">Vzory přepsání</span><span class="sxs-lookup"><span data-stu-id="09e67-120">Override Patterns</span></span>](#override)  
  
-   [<span data-ttu-id="09e67-121">Pravidla dědičnosti</span><span class="sxs-lookup"><span data-stu-id="09e67-121">Inheritance Rules</span></span>](#inheritance)  
  
-   [<span data-ttu-id="09e67-122">Další informace a pravidla</span><span class="sxs-lookup"><span data-stu-id="09e67-122">Additional Information and Rules</span></span>](#additional)  
  
<a name="examples"></a>   
## <a name="usage-examples-and-behaviors"></a><span data-ttu-id="09e67-123">Příklady použití a chování</span><span class="sxs-lookup"><span data-stu-id="09e67-123">Usage Examples and Behaviors</span></span>  
 <span data-ttu-id="09e67-124">Chcete-li určit [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] pravidla (transparentnosti úrovně 2), použijte následující poznámce pro sestavení:</span><span class="sxs-lookup"><span data-stu-id="09e67-124">To specify [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] rules (level 2 transparency), use the following annotation for an assembly:</span></span>  
  
```  
[assembly: SecurityRules(SecurityRuleSet.Level2)]  
```  
  
 <span data-ttu-id="09e67-125">Uzavřít se do pravidel rozhraní .NET Framework 2.0 (transparentnosti úrovně 1), použijte následující poznámky:</span><span class="sxs-lookup"><span data-stu-id="09e67-125">To lock into the .NET Framework 2.0 rules (level 1 transparency), use the following annotation:</span></span>  
  
```  
[assembly: SecurityRules(SecurityRuleSet.Level1)]  
```  
  
 <span data-ttu-id="09e67-126">Pokud není opatřit poznámkami sestavení, [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] ve výchozím nastavení jsou použita pravidla.</span><span class="sxs-lookup"><span data-stu-id="09e67-126">If you do not annotate an assembly, the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] rules are used by default.</span></span> <span data-ttu-id="09e67-127">Nicméně doporučený osvědčeným postupem je použít <xref:System.Security.SecurityRulesAttribute> atribut místo v závislosti na výchozí.</span><span class="sxs-lookup"><span data-stu-id="09e67-127">However, the recommended best practice is to use the <xref:System.Security.SecurityRulesAttribute> attribute instead of depending on the default.</span></span>  
  
### <a name="assembly-wide-annotation"></a><span data-ttu-id="09e67-128">Celé sestavení poznámky</span><span class="sxs-lookup"><span data-stu-id="09e67-128">Assembly-wide Annotation</span></span>  
 <span data-ttu-id="09e67-129">Použití atributů na úrovni sestavení platí následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="09e67-129">The following rules apply to the use of attributes at the assembly level:</span></span>  
  
-   <span data-ttu-id="09e67-130">Žádné atributy: Pokud nezadáte žádné atributy, modul runtime interpretuje celý kód jako kritické pro zabezpečení, s výjimkou případů, kde jsou kritické pro zabezpečení porušuje pravidlo dědičnosti (například když přepisuje nebo implementuje transparentní metoda rozhraní nebo virtuální).</span><span class="sxs-lookup"><span data-stu-id="09e67-130">No attributes: If you do not specify any attributes, the runtime interprets all code as security-critical, except where being security-critical violates an inheritance rule (for example, when overriding or implementing a transparent virtual or interface method).</span></span> <span data-ttu-id="09e67-131">V takových případech metody jsou bezpečné a kritické.</span><span class="sxs-lookup"><span data-stu-id="09e67-131">In those cases, the methods are safe-critical.</span></span> <span data-ttu-id="09e67-132">Určení žádný atribut způsobí, že modul common language runtime k určení pravidla transparentnosti za vás.</span><span class="sxs-lookup"><span data-stu-id="09e67-132">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span>  
  
-   `SecurityTransparent`<span data-ttu-id="09e67-133">: Všechny kódy jsou transparentní; celé sestavení nespustí žádnou akci privilegovaných nebo unsafe.</span><span class="sxs-lookup"><span data-stu-id="09e67-133">: All code is transparent; the entire assembly will not do anything privileged or unsafe.</span></span>  
  
-   `SecurityCritical`<span data-ttu-id="09e67-134">: Veškerý kód, který je zavedený typy v tomto sestavení je velmi důležité; všechny ostatní kód je transparentní.</span><span class="sxs-lookup"><span data-stu-id="09e67-134">: All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="09e67-135">Tento scénář je podobný bez zadání jakékoli atributů Nicméně modul common language runtime automaticky nezjišťuje pravidla transparentnosti.</span><span class="sxs-lookup"><span data-stu-id="09e67-135">This scenario is similar to not specifying any attributes; however, the common language runtime does not automatically determine the transparency rules.</span></span> <span data-ttu-id="09e67-136">Například pokud přepsat virtuální nebo abstraktní metody nebo implementaci metody rozhraní, ve výchozím nastavení tato metoda je transparentní.</span><span class="sxs-lookup"><span data-stu-id="09e67-136">For example, if you override a virtual or abstract method or implement an interface method, by default, that method is transparent.</span></span> <span data-ttu-id="09e67-137">Musíte explicitně označit metody jako `SecurityCritical` nebo `SecuritySafeCritical`; v opačném případě <xref:System.TypeLoadException> bude vyvolána v okamžiku načtení.</span><span class="sxs-lookup"><span data-stu-id="09e67-137">You must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`; otherwise, a <xref:System.TypeLoadException> will be thrown at load time.</span></span> <span data-ttu-id="09e67-138">Toto pravidlo platí také, pokud základní třída a odvozené třídy jsou ve stejném sestavení.</span><span class="sxs-lookup"><span data-stu-id="09e67-138">This rule also applies when both the base class and the derived class are in the same assembly.</span></span>  
  
-   `AllowPartiallyTrustedCallers` <span data-ttu-id="09e67-139">(pouze pro úroveň 2): Všechny výchozí hodnoty pro transparentní kód.</span><span class="sxs-lookup"><span data-stu-id="09e67-139">(level 2 only): All code defaults to transparent.</span></span> <span data-ttu-id="09e67-140">Nicméně jednotlivé typy a členy mohou mít jiné atributy.</span><span class="sxs-lookup"><span data-stu-id="09e67-140">However, individual types and members can have other attributes.</span></span>  
  
 <span data-ttu-id="09e67-141">Následující tabulka porovnává chování úrovně sestavení pro úrovně 2 s 1. úrovně.</span><span class="sxs-lookup"><span data-stu-id="09e67-141">The following table compares the assembly level behavior for Level 2 with Level 1.</span></span>  
  
|<span data-ttu-id="09e67-142">Atribut sestavení</span><span class="sxs-lookup"><span data-stu-id="09e67-142">Assembly attribute</span></span>|<span data-ttu-id="09e67-143">Úroveň 2</span><span class="sxs-lookup"><span data-stu-id="09e67-143">Level 2</span></span>|<span data-ttu-id="09e67-144">úroveň 1</span><span class="sxs-lookup"><span data-stu-id="09e67-144">Level 1</span></span>|  
|------------------------|-------------|-------------|  
|<span data-ttu-id="09e67-145">Žádný atribut pro částečně důvěryhodná sestavení</span><span class="sxs-lookup"><span data-stu-id="09e67-145">No attribute on a partially trusted assembly</span></span>|<span data-ttu-id="09e67-146">Typy a členy jsou ve výchozím nastavení transparentní, ale může být kritické pro zabezpečení nebo bezpečný a kritický pro zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="09e67-146">Types and members are by default transparent, but can be security-critical or security-safe-critical.</span></span>|<span data-ttu-id="09e67-147">Všechny typy a členy jsou transparentní.</span><span class="sxs-lookup"><span data-stu-id="09e67-147">All types and members are transparent.</span></span>|  
|<span data-ttu-id="09e67-148">Žádný atribut</span><span class="sxs-lookup"><span data-stu-id="09e67-148">No attribute</span></span>|<span data-ttu-id="09e67-149">Určení žádný atribut způsobí, že modul common language runtime k určení pravidla transparentnosti za vás.</span><span class="sxs-lookup"><span data-stu-id="09e67-149">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span> <span data-ttu-id="09e67-150">Všechny typy a členy jsou kritické pro zabezpečení, s výjimkou případů, kde jsou kritické pro zabezpečení porušuje pravidlo dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="09e67-150">All types and members are security-critical, except where being security-critical violates an inheritance rule.</span></span>|<span data-ttu-id="09e67-151">Pro plně důvěryhodná sestavení (v globální mezipaměti sestavení nebo označen jako úplný vztah důvěryhodnosti v `AppDomain`) jsou všechny typy transparentní a všichni členové jsou bezpečné a kritické pro zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="09e67-151">On a fully trusted assembly (in the global assembly cache or identified as full trust in the `AppDomain`) all types are transparent and all members are security-safe-critical.</span></span>|  
|`SecurityTransparent`|<span data-ttu-id="09e67-152">Všechny typy a členy jsou transparentní.</span><span class="sxs-lookup"><span data-stu-id="09e67-152">All types and members are transparent.</span></span>|<span data-ttu-id="09e67-153">Všechny typy a členy jsou transparentní.</span><span class="sxs-lookup"><span data-stu-id="09e67-153">All types and members are transparent.</span></span>|  
|`SecurityCritical(SecurityCriticalScope.Everything)`|<span data-ttu-id="09e67-154">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="09e67-154">Not applicable.</span></span>|<span data-ttu-id="09e67-155">Všechny typy a členy jsou kritické pro zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="09e67-155">All types and members are security-critical.</span></span>|  
|`SecurityCritical`|<span data-ttu-id="09e67-156">Veškerý kód, který je zavedený typy v tomto sestavení je velmi důležité; všechny ostatní kód je transparentní.</span><span class="sxs-lookup"><span data-stu-id="09e67-156">All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="09e67-157">Je-li přepsat virtuální nebo abstraktní metody nebo implementovat metodu rozhraní, musíte explicitně označit metody jako `SecurityCritical` nebo `SecuritySafeCritical`.</span><span class="sxs-lookup"><span data-stu-id="09e67-157">If you override a virtual or abstract method or implement an interface method, you must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`.</span></span>|<span data-ttu-id="09e67-158">Všechny výchozí hodnoty pro transparentní kód.</span><span class="sxs-lookup"><span data-stu-id="09e67-158">All code defaults to transparent.</span></span> <span data-ttu-id="09e67-159">Nicméně jednotlivé typy a členy mohou mít jiné atributy.</span><span class="sxs-lookup"><span data-stu-id="09e67-159">However, individual types and members can have other attributes.</span></span>|  
  
### <a name="type-and-member-annotation"></a><span data-ttu-id="09e67-160">Typ a člen poznámek</span><span class="sxs-lookup"><span data-stu-id="09e67-160">Type and Member Annotation</span></span>  
 <span data-ttu-id="09e67-161">Atributy zabezpečení, které se použijí na typ. platí také pro členy, které vznikají zavlečením typu.</span><span class="sxs-lookup"><span data-stu-id="09e67-161">The security attributes that are applied to a type also apply to the members that are introduced by the type.</span></span> <span data-ttu-id="09e67-162">Nicméně se nevztahují na virtuální nebo abstraktní přepíše z implementací základní třídy nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="09e67-162">However, they do not apply to virtual or abstract overrides of the base class or interface implementations.</span></span> <span data-ttu-id="09e67-163">Použití atributů na úrovni typů a členů platí následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="09e67-163">The following rules apply to the use of attributes at the type and member level:</span></span>  
  
-   `SecurityCritical`<span data-ttu-id="09e67-164">: Tento typ nebo člen je velmi důležité a může být volána pouze pomocí plně důvěryhodného kódu.</span><span class="sxs-lookup"><span data-stu-id="09e67-164">: The type or member is critical and can be called only by full-trust code.</span></span> <span data-ttu-id="09e67-165">Metody, které jsou součástí typu kritické pro zabezpečení jsou kritické.</span><span class="sxs-lookup"><span data-stu-id="09e67-165">Methods that are introduced in a security-critical type are critical.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="09e67-166">Virtuální a abstraktní metody, které jsou součástí základní třídy nebo rozhraní a přepsat nebo implementována ve třídě kritické z hlediska zabezpečení je ve výchozím nastavení transparentní.</span><span class="sxs-lookup"><span data-stu-id="09e67-166">Virtual and abstract methods that are introduced in base classes or interfaces, and overridden or implemented in a security-critical class are transparent by default.</span></span> <span data-ttu-id="09e67-167">Musí být určen buď `SecuritySafeCritical` nebo `SecurityCritical`.</span><span class="sxs-lookup"><span data-stu-id="09e67-167">They must be identified as either `SecuritySafeCritical` or `SecurityCritical`.</span></span>  
  
-   `SecuritySafeCritical`<span data-ttu-id="09e67-168">: Tento typ nebo člen je kritický.</span><span class="sxs-lookup"><span data-stu-id="09e67-168">: The type or member is safe-critical.</span></span> <span data-ttu-id="09e67-169">Tento typ nebo člen lze volat z transparentního kódu (částečně důvěryhodným) a je možností, jako jakýkoli jiný kritický kód.</span><span class="sxs-lookup"><span data-stu-id="09e67-169">However, the type or member can be called from transparent (partially trusted) code and is as capable as any other critical code.</span></span> <span data-ttu-id="09e67-170">Musí být auditován kód pro zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="09e67-170">The code must be audited for security.</span></span>  
  
 [<span data-ttu-id="09e67-171">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="09e67-171">Back to top</span></span>](#top)  
  
<a name="override"></a>   
## <a name="override-patterns"></a><span data-ttu-id="09e67-172">Vzory přepsání</span><span class="sxs-lookup"><span data-stu-id="09e67-172">Override Patterns</span></span>  
 <span data-ttu-id="09e67-173">V následující tabulce jsou uvedeny přepsání metody, které jsou povolené pro transparentnosti úrovně 2.</span><span class="sxs-lookup"><span data-stu-id="09e67-173">The following table shows the method overrides allowed for level 2 transparency.</span></span>  
  
|<span data-ttu-id="09e67-174">Základní virtuálního člena/člena rozhraní</span><span class="sxs-lookup"><span data-stu-id="09e67-174">Base virtual/interface member</span></span>|<span data-ttu-id="09e67-175">Přepsání a interface</span><span class="sxs-lookup"><span data-stu-id="09e67-175">Override/interface</span></span>|  
|------------------------------------|-------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`SafeCritical`|`Transparent`|  
|`SafeCritical`|`SafeCritical`|  
|`Critical`|`Critical`|  
  
 [<span data-ttu-id="09e67-176">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="09e67-176">Back to top</span></span>](#top)  
  
<a name="inheritance"></a>   
## <a name="inheritance-rules"></a><span data-ttu-id="09e67-177">Pravidla dědičnosti</span><span class="sxs-lookup"><span data-stu-id="09e67-177">Inheritance Rules</span></span>  
 <span data-ttu-id="09e67-178">V této části je přiřazená následující pořadí `Transparent`, `Critical`, a `SafeCritical` kódu na základě přístupu a možnosti:</span><span class="sxs-lookup"><span data-stu-id="09e67-178">In this section, the following order is assigned to `Transparent`, `Critical`, and `SafeCritical` code based on access and capabilities:</span></span>  
  
 `Transparent` < `SafeCritical` < `Critical`  
  
-   <span data-ttu-id="09e67-179">Pravidla pro typy: Přechod zleva doprava, bude přístup více omezující.</span><span class="sxs-lookup"><span data-stu-id="09e67-179">Rules for types: Going from left to right, access becomes more restrictive.</span></span> <span data-ttu-id="09e67-180">Odvozené typy musí být alespoň tak omezující jako základního typu.</span><span class="sxs-lookup"><span data-stu-id="09e67-180">Derived types must be at least as restrictive as the base type.</span></span>  
  
-   <span data-ttu-id="09e67-181">Pravidla pro metody: Odvozené metody nemůže změnit přístupnost ze základní metody.</span><span class="sxs-lookup"><span data-stu-id="09e67-181">Rules for methods: Derived methods cannot change accessibility from the base method.</span></span> <span data-ttu-id="09e67-182">Pro výchozí chování, jsou všechny odvozené metody, která nejsou označena `Transparent`.</span><span class="sxs-lookup"><span data-stu-id="09e67-182">For default behavior, all derived methods that are not annotated are `Transparent`.</span></span> <span data-ttu-id="09e67-183">Odvozené typy kritických typů způsobit výjimku, která je vyvolána, pokud přepsané metody není explicitně označena jako `SecurityCritical`.</span><span class="sxs-lookup"><span data-stu-id="09e67-183">Derivatives of critical types cause an exception to be thrown if the overridden method is not explicitly annotated as `SecurityCritical`.</span></span>  
  
 <span data-ttu-id="09e67-184">V následující tabulce jsou uvedeny povolený typ vzory dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="09e67-184">The following table shows the allowed type inheritance patterns.</span></span>  
  
|<span data-ttu-id="09e67-185">Základní třída</span><span class="sxs-lookup"><span data-stu-id="09e67-185">Base class</span></span>|<span data-ttu-id="09e67-186">Odvozená třída může být</span><span class="sxs-lookup"><span data-stu-id="09e67-186">Derived class can be</span></span>|  
|----------------|--------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`Transparent`|`Critical`|  
|`SafeCritical`|`SafeCritical`|  
|`SafeCritical`|`Critical`|  
|`Critical`|`Critical`|  
  
 <span data-ttu-id="09e67-187">Následující tabulka ukazuje zakázaného typ vzory dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="09e67-187">The following table shows the disallowed type inheritance patterns.</span></span>  
  
|<span data-ttu-id="09e67-188">Základní třída</span><span class="sxs-lookup"><span data-stu-id="09e67-188">Base class</span></span>|<span data-ttu-id="09e67-189">Odvozená třída nemůže být</span><span class="sxs-lookup"><span data-stu-id="09e67-189">Derived class cannot be</span></span>|  
|----------------|-----------------------------|  
|`SafeCritical`|`Transparent`|  
|`Critical`|`Transparent`|  
|`Critical`|`SafeCritical`|  
  
 <span data-ttu-id="09e67-190">V následující tabulce jsou uvedeny povolené metody vzory dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="09e67-190">The following table shows the allowed method inheritance patterns.</span></span>  
  
|<span data-ttu-id="09e67-191">Base – metoda</span><span class="sxs-lookup"><span data-stu-id="09e67-191">Base method</span></span>|<span data-ttu-id="09e67-192">Může být Odvozená metoda</span><span class="sxs-lookup"><span data-stu-id="09e67-192">Derived method can be</span></span>|  
|-----------------|---------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`SafeCritical`|`Transparent`|  
|`SafeCritical`|`SafeCritical`|  
|`Critical`|`Critical`|  
  
 <span data-ttu-id="09e67-193">Následující tabulka ukazuje zakázaného metodu vzory dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="09e67-193">The following table shows the disallowed method inheritance patterns.</span></span>  
  
|<span data-ttu-id="09e67-194">Base – metoda</span><span class="sxs-lookup"><span data-stu-id="09e67-194">Base method</span></span>|<span data-ttu-id="09e67-195">Nemůže být Odvozená metoda</span><span class="sxs-lookup"><span data-stu-id="09e67-195">Derived method cannot be</span></span>|  
|-----------------|------------------------------|  
|`Transparent`|`Critical`|  
|`SafeCritical`|`Critical`|  
|`Critical`|`Transparent`|  
|`Critical`|`SafeCritical`|  
  
> [!NOTE]
>  <span data-ttu-id="09e67-196">Tato pravidla dědičnosti se vztahují na typy a členy úrovně 2.</span><span class="sxs-lookup"><span data-stu-id="09e67-196">These inheritance rules apply to level 2 types and members.</span></span> <span data-ttu-id="09e67-197">Typy v sestaveních úroveň 1 může dědit z typy kritické pro zabezpečení úrovně 2 a členy.</span><span class="sxs-lookup"><span data-stu-id="09e67-197">Types in level 1 assemblies can inherit from level 2 security-critical types and members.</span></span> <span data-ttu-id="09e67-198">Typy a členy úrovně 2 proto musí mít samostatné dědičnost požadavků pro dědice úrovně 1.</span><span class="sxs-lookup"><span data-stu-id="09e67-198">Therefore, level 2 types and members must have separate inheritance demands for level 1 inheritors.</span></span>  
  
 [<span data-ttu-id="09e67-199">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="09e67-199">Back to top</span></span>](#top)  
  
<a name="additional"></a>   
## <a name="additional-information-and-rules"></a><span data-ttu-id="09e67-200">Další informace a pravidla</span><span class="sxs-lookup"><span data-stu-id="09e67-200">Additional Information and Rules</span></span>  
  
### <a name="linkdemand-support"></a><span data-ttu-id="09e67-201">Podpora LinkDemand</span><span class="sxs-lookup"><span data-stu-id="09e67-201">LinkDemand Support</span></span>  
 <span data-ttu-id="09e67-202">Nahradí modelu transparentnosti úrovně 2 <xref:System.Security.Permissions.SecurityAction.LinkDemand> s <xref:System.Security.SecurityCriticalAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="09e67-202">The level 2 transparency model replaces the <xref:System.Security.Permissions.SecurityAction.LinkDemand> with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="09e67-203">V kódu starší verze (úroveň 1) <xref:System.Security.Permissions.SecurityAction.LinkDemand> je automaticky považováno za <xref:System.Security.Permissions.SecurityAction.Demand>.</span><span class="sxs-lookup"><span data-stu-id="09e67-203">In legacy (level 1) code, a <xref:System.Security.Permissions.SecurityAction.LinkDemand> is automatically treated as a <xref:System.Security.Permissions.SecurityAction.Demand>.</span></span>  
  
### <a name="reflection"></a><span data-ttu-id="09e67-204">Reflexe</span><span class="sxs-lookup"><span data-stu-id="09e67-204">Reflection</span></span>  
 <span data-ttu-id="09e67-205">Vyvolání kritické metody nebo čtení kritickému poli spustí požadavek pro úplný vztah důvěryhodnosti (tak, jako kdyby byly vyvolání soukromou metodu nebo pole).</span><span class="sxs-lookup"><span data-stu-id="09e67-205">Invoking a critical method or reading a critical field triggers a demand for full trust (just as if you were invoking a private method or field).</span></span> <span data-ttu-id="09e67-206">Proto plně důvěryhodného kódu můžete vyvolat na kritickou metodu, že nelze částečně důvěryhodného kódu.</span><span class="sxs-lookup"><span data-stu-id="09e67-206">Therefore, full-trust code can invoke a critical method, whereas partial-trust code cannot.</span></span>  
  
 <span data-ttu-id="09e67-207">Následující vlastnosti byly přidány do <xref:System.Reflection> obor názvů pro určení, zda je typ, metodu nebo pole `SecurityCritical`, `SecuritySafeCritical`, nebo `SecurityTransparent`: <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, a <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>.</span><span class="sxs-lookup"><span data-stu-id="09e67-207">The following properties have been added to the <xref:System.Reflection> namespace to determine whether the type, method, or field is `SecurityCritical`, `SecuritySafeCritical`, or `SecurityTransparent`:  <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, and <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>.</span></span> <span data-ttu-id="09e67-208">Tyto vlastnosti lze použijte k určení transparentnosti pomocí reflexe namísto kontroly na přítomnost atributu.</span><span class="sxs-lookup"><span data-stu-id="09e67-208">Use these properties to determine transparency by using reflection instead of checking for the presence of the attribute.</span></span> <span data-ttu-id="09e67-209">Pravidla transparentnosti jsou komplexní a kontrola pro atribut nemusí být dostatečné.</span><span class="sxs-lookup"><span data-stu-id="09e67-209">The transparency rules are complex, and checking for the attribute may not be sufficient.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="09e67-210">A `SafeCritical` vrátí metoda `true` pro obě <xref:System.Type.IsSecurityCritical%2A> a <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, protože `SafeCritical` je skutečně důležité (má stejné funkce jako kritický kód, ale mohou být volány transparentní kód).</span><span class="sxs-lookup"><span data-stu-id="09e67-210">A `SafeCritical` method returns `true` for both <xref:System.Type.IsSecurityCritical%2A> and <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, because `SafeCritical` is indeed critical (it has the same capabilities as critical code, but it can be called from transparent code).</span></span>  
  
 <span data-ttu-id="09e67-211">Průhlednost modulů, které jsou připojeny k; dědit dynamických metod nedědí průhlednost typu (pokud jsou připojeny k typu).</span><span class="sxs-lookup"><span data-stu-id="09e67-211">Dynamic methods inherit the transparency of the modules they are attached to; they do not inherit the transparency of the type (if they are attached to a type).</span></span>  
  
### <a name="skip-verification-in-full-trust"></a><span data-ttu-id="09e67-212">Přeskočit ověřování v režimu plné důvěryhodnosti</span><span class="sxs-lookup"><span data-stu-id="09e67-212">Skip Verification in Full Trust</span></span>  
 <span data-ttu-id="09e67-213">Můžete přeskočit ověření pro plně důvěryhodná transparentní sestavení tak, že nastavíte <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> vlastnost `true` v <xref:System.Security.SecurityRulesAttribute> atribut:</span><span class="sxs-lookup"><span data-stu-id="09e67-213">You can skip verification for fully trusted transparent assemblies by setting the <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property to `true` in the <xref:System.Security.SecurityRulesAttribute> attribute:</span></span>  
  
 `[assembly: SecurityRules(SecurityRuleSet.Level2, SkipVerificationInFullTrust = true)]`  
  
 <span data-ttu-id="09e67-214"><xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> Vlastnost `false` ve výchozím nastavení, tak vlastnost musí být nastavena na `true` pro přeskočení ověření.</span><span class="sxs-lookup"><span data-stu-id="09e67-214">The <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property is `false` by default, so the property must be set to `true` to skip verification.</span></span> <span data-ttu-id="09e67-215">To by mělo být provedeno za účelem optimalizace pouze.</span><span class="sxs-lookup"><span data-stu-id="09e67-215">This should be done for optimization purposes only.</span></span> <span data-ttu-id="09e67-216">Měli byste zajistit, že transparentní kód v sestavení je ověřit pomocí `transparent` možnost [Nástroj PEVerify](../../../docs/framework/tools/peverify-exe-peverify-tool.md).</span><span class="sxs-lookup"><span data-stu-id="09e67-216">You should ensure that the transparent code in the assembly is verifiable by using the `transparent` option in the [PEVerify tool](../../../docs/framework/tools/peverify-exe-peverify-tool.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09e67-217">Viz také:</span><span class="sxs-lookup"><span data-stu-id="09e67-217">See also</span></span>

- [<span data-ttu-id="09e67-218">Kód transparentní pro zabezpečení, úroveň 1</span><span class="sxs-lookup"><span data-stu-id="09e67-218">Security-Transparent Code, Level 1</span></span>](../../../docs/framework/misc/security-transparent-code-level-1.md)
- [<span data-ttu-id="09e67-219">Změny zabezpečení</span><span class="sxs-lookup"><span data-stu-id="09e67-219">Security Changes</span></span>](../../../docs/framework/security/security-changes.md)
