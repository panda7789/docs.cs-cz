---
title: "Transparentní kód pro zabezpečení, úroveň 2"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transparency
- level 2 transparency
- security-transparent code
- security-critical code
ms.assetid: 4d05610a-0da6-4f08-acea-d54c9d6143c0
caps.latest.revision: "37"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ba7b6bca4618b8de7c1b5ce2ef45b8455ee71c5c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="security-transparent-code-level-2"></a><span data-ttu-id="3e577-102">Transparentní kód pro zabezpečení, úroveň 2</span><span class="sxs-lookup"><span data-stu-id="3e577-102">Security-Transparent Code, Level 2</span></span>
<a name="top"></a>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="3e577-103">Průhlednost úrovně 2 byla zavedena v [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3e577-103">Level 2 transparency was introduced in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="3e577-104">Tři zásady tohoto modelu jsou transparentní kód, bezpečné a kritické pro zabezpečení kód a kód kritický pro zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="3e577-104">The three tenets of this model are transparent code, security-safe-critical code, and security-critical code.</span></span>  
  
-   <span data-ttu-id="3e577-105">Transparentní kód, včetně kódu, který je spuštěný jako úplný vztah důvěryhodnosti, můžete volat jiný transparentní kód nebo pouze bezpečné a kritické pro zabezpečení kód.</span><span class="sxs-lookup"><span data-stu-id="3e577-105">Transparent code, including code that is running as full trust, can call other transparent code or security-safe-critical code only.</span></span> <span data-ttu-id="3e577-106">Může provádět jenom akce povolené oprávnění částečné důvěryhodnosti domény nastavené (pokud existuje).</span><span class="sxs-lookup"><span data-stu-id="3e577-106">It can only perform actions allowed by the domain’s partial trust permission set (if one exists).</span></span> <span data-ttu-id="3e577-107">Kód transparentní nelze provést následující akce:</span><span class="sxs-lookup"><span data-stu-id="3e577-107">Transparent code cannot do the following:</span></span>  
  
    -   <span data-ttu-id="3e577-108">Provést <xref:System.Security.CodeAccessPermission.Assert%2A> nebo zvýšení úrovně oprávnění.</span><span class="sxs-lookup"><span data-stu-id="3e577-108">Perform an <xref:System.Security.CodeAccessPermission.Assert%2A> or elevation of privilege.</span></span>  
  
    -   <span data-ttu-id="3e577-109">Obsahovat nebezpečný nebo neověřitelný kód.</span><span class="sxs-lookup"><span data-stu-id="3e577-109">Contain unsafe or unverifiable code.</span></span>  
  
    -   <span data-ttu-id="3e577-110">Kód kritický pro volejte přímo.</span><span class="sxs-lookup"><span data-stu-id="3e577-110">Directly call critical code.</span></span>  
  
    -   <span data-ttu-id="3e577-111">Volání nativního kódu nebo kód s <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="3e577-111">Call native code or code with the <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attribute.</span></span>  
  
    -   <span data-ttu-id="3e577-112">Volání člena, který je chráněn <xref:System.Security.Permissions.SecurityAction.LinkDemand>.</span><span class="sxs-lookup"><span data-stu-id="3e577-112">Call a member that is protected by a <xref:System.Security.Permissions.SecurityAction.LinkDemand>.</span></span>  
  
    -   <span data-ttu-id="3e577-113">Typy kritické dědí.</span><span class="sxs-lookup"><span data-stu-id="3e577-113">Inherit from critical types.</span></span>  
  
     <span data-ttu-id="3e577-114">Kromě toho transparentní metody nelze přepsat kritické virtuální metody nebo implementovat kritické metody rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3e577-114">In addition, transparent methods cannot override critical virtual methods or implement critical interface methods.</span></span>  
  
-   <span data-ttu-id="3e577-115">Kritická kód je plně důvěryhodný, ale je volatelné transparentní kód.</span><span class="sxs-lookup"><span data-stu-id="3e577-115">Safe-critical code is fully trusted but is callable by transparent code.</span></span> <span data-ttu-id="3e577-116">Zpřístupňuje omezenou oblast povrchu plné důvěryhodnosti kódu; dojde k ověření správnosti a zabezpečení v kritickém kódu.</span><span class="sxs-lookup"><span data-stu-id="3e577-116">It exposes a limited surface area of full-trust code; correctness and security verifications happen in safe-critical code.</span></span>  
  
-   <span data-ttu-id="3e577-117">Kód kritický pro zabezpečení můžete volat žádný kód a je plně důvěryhodný, ale ji nelze volat kód transparentní.</span><span class="sxs-lookup"><span data-stu-id="3e577-117">Security-critical code can call any code and is fully trusted, but it cannot be called by transparent code.</span></span>  
  
 <span data-ttu-id="3e577-118">Toto téma obsahuje následující oddíly:</span><span class="sxs-lookup"><span data-stu-id="3e577-118">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="3e577-119">Příklady použití a chování</span><span class="sxs-lookup"><span data-stu-id="3e577-119">Usage Examples and Behaviors</span></span>](#examples)  
  
-   [<span data-ttu-id="3e577-120">Vzory přepsání</span><span class="sxs-lookup"><span data-stu-id="3e577-120">Override Patterns</span></span>](#override)  
  
-   [<span data-ttu-id="3e577-121">Pravidla dědičnosti</span><span class="sxs-lookup"><span data-stu-id="3e577-121">Inheritance Rules</span></span>](#inheritance)  
  
-   [<span data-ttu-id="3e577-122">Další informace a pravidla</span><span class="sxs-lookup"><span data-stu-id="3e577-122">Additional Information and Rules</span></span>](#additional)  
  
<a name="examples"></a>   
## <a name="usage-examples-and-behaviors"></a><span data-ttu-id="3e577-123">Příklady použití a chování</span><span class="sxs-lookup"><span data-stu-id="3e577-123">Usage Examples and Behaviors</span></span>  
 <span data-ttu-id="3e577-124">Chcete-li určit [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] pravidla (průhlednost úrovně 2), použijte následující anotaci pro sestavení:</span><span class="sxs-lookup"><span data-stu-id="3e577-124">To specify [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] rules (level 2 transparency), use the following annotation for an assembly:</span></span>  
  
```  
[assembly: SecurityRules(SecurityRuleSet.Level2)]  
```  
  
 <span data-ttu-id="3e577-125">Pokud chcete uzamknout na rozhraní .NET Framework 2.0 pravidla (úroveň 1 průhlednost), použijte následující poznámky:</span><span class="sxs-lookup"><span data-stu-id="3e577-125">To lock into the .NET Framework 2.0 rules (level 1 transparency), use the following annotation:</span></span>  
  
```  
[assembly: SecurityRules(SecurityRuleSet.Level1)]  
```  
  
 <span data-ttu-id="3e577-126">Pokud není opatřit poznámkami sestavení, [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] pravidla se používají ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="3e577-126">If you do not annotate an assembly, the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] rules are used by default.</span></span> <span data-ttu-id="3e577-127">Doporučený osvědčený postup je však používat <xref:System.Security.SecurityRulesAttribute> atribut místo v závislosti na výchozí.</span><span class="sxs-lookup"><span data-stu-id="3e577-127">However, the recommended best practice is to use the <xref:System.Security.SecurityRulesAttribute> attribute instead of depending on the default.</span></span>  
  
### <a name="assembly-wide-annotation"></a><span data-ttu-id="3e577-128">Sestavení celou poznámky</span><span class="sxs-lookup"><span data-stu-id="3e577-128">Assembly-wide Annotation</span></span>  
 <span data-ttu-id="3e577-129">Následující pravidla platí při použití atributů na úrovni sestavení:</span><span class="sxs-lookup"><span data-stu-id="3e577-129">The following rules apply to the use of attributes at the assembly level:</span></span>  
  
-   <span data-ttu-id="3e577-130">Žádné atributy: Pokud nezadáte žádné atributy, modul runtime interpretuje všechny kód jako kritické pro zabezpečení, s výjimkou případů, kdy se kritický pro zabezpečení porušuje pravidlo dědičnosti (například v případě, že přepsání nebo implementace transparentní virtuální nebo rozhraní – metoda ).</span><span class="sxs-lookup"><span data-stu-id="3e577-130">No attributes: If you do not specify any attributes, the runtime interprets all code as security-critical, except where being security-critical violates an inheritance rule (for example, when overriding or implementing a transparent virtual or interface method).</span></span> <span data-ttu-id="3e577-131">V takových případech jsou kritická metody.</span><span class="sxs-lookup"><span data-stu-id="3e577-131">In those cases, the methods are safe-critical.</span></span> <span data-ttu-id="3e577-132">Určení žádný atribut způsobí, že modul common language runtime k určení pravidel průhlednost.</span><span class="sxs-lookup"><span data-stu-id="3e577-132">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span>  
  
-   <span data-ttu-id="3e577-133">`SecurityTransparent`: Všechna kód je transparentní; celé sestavení nebude dělat nic privilegovaného nebo unsafe.</span><span class="sxs-lookup"><span data-stu-id="3e577-133">`SecurityTransparent`: All code is transparent; the entire assembly will not do anything privileged or unsafe.</span></span>  
  
-   <span data-ttu-id="3e577-134">`SecurityCritical`: Všechna kód, který je zavedený typy v tomto sestavení je velmi důležité; všechny ostatní kód je transparentní.</span><span class="sxs-lookup"><span data-stu-id="3e577-134">`SecurityCritical`: All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="3e577-135">Tento scénář je podobná nespecifikuje žádné atributy; však modul common language runtime automaticky neurčuje pravidla průhlednost.</span><span class="sxs-lookup"><span data-stu-id="3e577-135">This scenario is similar to not specifying any attributes; however, the common language runtime does not automatically determine the transparency rules.</span></span> <span data-ttu-id="3e577-136">Například pokud přepíšete metodu virtuální nebo abstraktní nebo implementovat metodu rozhraní, ve výchozím nastavení, že metoda je transparentní.</span><span class="sxs-lookup"><span data-stu-id="3e577-136">For example, if you override a virtual or abstract method or implement an interface method, by default, that method is transparent.</span></span> <span data-ttu-id="3e577-137">Musíte explicitně označit jako metodu `SecurityCritical` nebo `SecuritySafeCritical`, jinak hodnota <xref:System.TypeLoadException> při načítání, bude vyvolána.</span><span class="sxs-lookup"><span data-stu-id="3e577-137">You must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`; otherwise, a <xref:System.TypeLoadException> will be thrown at load time.</span></span> <span data-ttu-id="3e577-138">Toto pravidlo platí i v případě základní třída a odvozené třídy jsou ve stejném sestavení.</span><span class="sxs-lookup"><span data-stu-id="3e577-138">This rule also applies when both the base class and the derived class are in the same assembly.</span></span>  
  
-   <span data-ttu-id="3e577-139">`AllowPartiallyTrustedCallers`(úroveň 2 pouze): všechny code automaticky transparentní.</span><span class="sxs-lookup"><span data-stu-id="3e577-139">`AllowPartiallyTrustedCallers` (level 2 only): All code defaults to transparent.</span></span> <span data-ttu-id="3e577-140">Jednotlivé typy a členy však mohou mít jiné atributy.</span><span class="sxs-lookup"><span data-stu-id="3e577-140">However, individual types and members can have other attributes.</span></span>  
  
 <span data-ttu-id="3e577-141">Následující tabulka porovnává chování úrovně sestavení úroveň 2 s úrovně 1.</span><span class="sxs-lookup"><span data-stu-id="3e577-141">The following table compares the assembly level behavior for Level 2 with Level 1 .</span></span>  
  
|<span data-ttu-id="3e577-142">Atribut sestavení</span><span class="sxs-lookup"><span data-stu-id="3e577-142">Assembly attribute</span></span>|<span data-ttu-id="3e577-143">Úroveň 2</span><span class="sxs-lookup"><span data-stu-id="3e577-143">Level 2</span></span>|<span data-ttu-id="3e577-144">úroveň 1</span><span class="sxs-lookup"><span data-stu-id="3e577-144">Level 1</span></span>|  
|------------------------|-------------|-------------|  
|<span data-ttu-id="3e577-145">Žádný atribut v částečně důvěryhodné sestavení</span><span class="sxs-lookup"><span data-stu-id="3e577-145">No attribute on a partially trusted assembly</span></span>|<span data-ttu-id="3e577-146">Typy a členové jsou ve výchozím nastavení transparentní, ale může být kritické pro zabezpečení nebo bezpečné a kritické pro zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="3e577-146">Types and members are by default transparent, but can be security-critical or security-safe-critical.</span></span>|<span data-ttu-id="3e577-147">Všechny typy a členy jsou transparentní.</span><span class="sxs-lookup"><span data-stu-id="3e577-147">All types and members are transparent.</span></span>|  
|<span data-ttu-id="3e577-148">Žádný atribut</span><span class="sxs-lookup"><span data-stu-id="3e577-148">No attribute</span></span>|<span data-ttu-id="3e577-149">Určení žádný atribut způsobí, že modul common language runtime k určení pravidel průhlednost.</span><span class="sxs-lookup"><span data-stu-id="3e577-149">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span> <span data-ttu-id="3e577-150">Všechny typy a členy jsou kritické pro zabezpečení, s výjimkou případů, kdy se kritický pro zabezpečení porušuje pravidlo dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="3e577-150">All types and members are security-critical, except where being security-critical violates an inheritance rule.</span></span>|<span data-ttu-id="3e577-151">Ve plně důvěryhodný pro sestavení (v globální mezipaměti sestavení nebo identifikován jako úplný vztah důvěryhodnosti v `AppDomain`) jsou všechny typy transparentní a bezpečné a kritické pro zabezpečení se všichni její členové.</span><span class="sxs-lookup"><span data-stu-id="3e577-151">On a fully trusted assembly (in the global assembly cache or identified as full trust in the `AppDomain`) all types are transparent and all members are security-safe-critical.</span></span>|  
|`SecurityTransparent`|<span data-ttu-id="3e577-152">Všechny typy a členy jsou transparentní.</span><span class="sxs-lookup"><span data-stu-id="3e577-152">All types and members are transparent.</span></span>|<span data-ttu-id="3e577-153">Všechny typy a členy jsou transparentní.</span><span class="sxs-lookup"><span data-stu-id="3e577-153">All types and members are transparent.</span></span>|  
|`SecurityCritical(SecurityCriticalScope.Everything)`|<span data-ttu-id="3e577-154">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="3e577-154">Not applicable.</span></span>|<span data-ttu-id="3e577-155">Všechny typy a členy jsou kritické pro zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="3e577-155">All types and members are security-critical.</span></span>|  
|`SecurityCritical`|<span data-ttu-id="3e577-156">Všechny kód, který je zavedený typy v tomto sestavení je velmi důležité; všechny ostatní kód je transparentní.</span><span class="sxs-lookup"><span data-stu-id="3e577-156">All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="3e577-157">Pokud přepíšete metodu virtuální nebo abstraktní nebo implementovat metodu rozhraní, musíte explicitně označit jako metodu `SecurityCritical` nebo `SecuritySafeCritical`.</span><span class="sxs-lookup"><span data-stu-id="3e577-157">If you override a virtual or abstract method or implement an interface method, you must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`.</span></span>|<span data-ttu-id="3e577-158">Všechny kódu automaticky transparentní.</span><span class="sxs-lookup"><span data-stu-id="3e577-158">All code defaults to transparent.</span></span> <span data-ttu-id="3e577-159">Jednotlivé typy a členy však mohou mít jiné atributy.</span><span class="sxs-lookup"><span data-stu-id="3e577-159">However, individual types and members can have other attributes.</span></span>|  
  
### <a name="type-and-member-annotation"></a><span data-ttu-id="3e577-160">Typ a člen poznámky</span><span class="sxs-lookup"><span data-stu-id="3e577-160">Type and Member Annotation</span></span>  
 <span data-ttu-id="3e577-161">Atributy zabezpečení, které se použijí na typ platí také pro členy, které jsou zavedené podle typu.</span><span class="sxs-lookup"><span data-stu-id="3e577-161">The security attributes that are applied to a type also apply to the members that are introduced by the type.</span></span> <span data-ttu-id="3e577-162">Ale nelze je použít na virtuální nebo přepsání abstraktní základní implementace třídy nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3e577-162">However, they do not apply to virtual or abstract overrides of the base class or interface implementations.</span></span> <span data-ttu-id="3e577-163">Následující pravidla platí při použití atributů na úrovni typu a členu:</span><span class="sxs-lookup"><span data-stu-id="3e577-163">The following rules apply to the use of attributes at the type and member level:</span></span>  
  
-   <span data-ttu-id="3e577-164">`SecurityCritical`: Typ nebo člen je velmi důležité a lze volat pouze ve plně důvěryhodný kód.</span><span class="sxs-lookup"><span data-stu-id="3e577-164">`SecurityCritical`: The type or member is critical and can be called only by full-trust code.</span></span> <span data-ttu-id="3e577-165">Metody, které jsou zavedené v kritické pro zabezpečení typu jsou důležité.</span><span class="sxs-lookup"><span data-stu-id="3e577-165">Methods that are introduced in a security-critical type are critical.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="3e577-166">Virtuální a abstraktní metody, které jsou zavedené v rozhraní nebo základní třídy a přepsat nebo implementována ve třídě kritické pro zabezpečení jsou transparentní ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="3e577-166">Virtual and abstract methods that are introduced in base classes or interfaces, and overridden or implemented in a security-critical class are transparent by default.</span></span> <span data-ttu-id="3e577-167">Musí být identifikovány jako `SecuritySafeCritical` nebo `SecurityCritical`.</span><span class="sxs-lookup"><span data-stu-id="3e577-167">They must be identified as either `SecuritySafeCritical` or `SecurityCritical`.</span></span>  
  
-   <span data-ttu-id="3e577-168">`SecuritySafeCritical`: Typ nebo člen je kritický.</span><span class="sxs-lookup"><span data-stu-id="3e577-168">`SecuritySafeCritical`: The type or member is safe-critical.</span></span> <span data-ttu-id="3e577-169">Typ nebo člen lze volat z kódu transparentní (částečně důvěryhodné) a je umožňující jako jakýkoli jiný kód, kritické.</span><span class="sxs-lookup"><span data-stu-id="3e577-169">However, the type or member can be called from transparent (partially trusted) code and is as capable as any other critical code.</span></span> <span data-ttu-id="3e577-170">Kód musí být auditován pro zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="3e577-170">The code must be audited for security.</span></span>  
  
 [<span data-ttu-id="3e577-171">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="3e577-171">Back to top</span></span>](#top)  
  
<a name="override"></a>   
## <a name="override-patterns"></a><span data-ttu-id="3e577-172">Vzory přepsání</span><span class="sxs-lookup"><span data-stu-id="3e577-172">Override Patterns</span></span>  
 <span data-ttu-id="3e577-173">V následující tabulce jsou uvedeny přepsání metody povolené pro průhlednost úrovně 2.</span><span class="sxs-lookup"><span data-stu-id="3e577-173">The following table shows the method overrides allowed for level 2 transparency.</span></span>  
  
|<span data-ttu-id="3e577-174">Základní virtuální/rozhraní člen</span><span class="sxs-lookup"><span data-stu-id="3e577-174">Base virtual/interface member</span></span>|<span data-ttu-id="3e577-175">Přepsání/rozhraní</span><span class="sxs-lookup"><span data-stu-id="3e577-175">Override/interface</span></span>|  
|------------------------------------|-------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`SafeCritical`|`Transparent`|  
|`SafeCritical`|`SafeCritical`|  
|`Critical`|`Critical`|  
  
 [<span data-ttu-id="3e577-176">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="3e577-176">Back to top</span></span>](#top)  
  
<a name="inheritance"></a>   
## <a name="inheritance-rules"></a><span data-ttu-id="3e577-177">Pravidla dědičnosti</span><span class="sxs-lookup"><span data-stu-id="3e577-177">Inheritance Rules</span></span>  
 <span data-ttu-id="3e577-178">V této části je přiřazená následující pořadí `Transparent`, `Critical`, a `SafeCritical` kódu na základě přístupu a možnosti:</span><span class="sxs-lookup"><span data-stu-id="3e577-178">In this section, the following order is assigned to `Transparent`, `Critical`, and `SafeCritical` code based on access and capabilities:</span></span>  
  
 `Transparent` < `SafeCritical` < `Critical`  
  
-   <span data-ttu-id="3e577-179">Pravidla pro typy: přejdete zleva doprava, bude přístup k více omezující.</span><span class="sxs-lookup"><span data-stu-id="3e577-179">Rules for types: Going from left to right, access becomes more restrictive.</span></span> <span data-ttu-id="3e577-180">Odvozené typy musí být nejméně omezující jako základního typu.</span><span class="sxs-lookup"><span data-stu-id="3e577-180">Derived types must be at least as restrictive as the base type.</span></span>  
  
-   <span data-ttu-id="3e577-181">Pravidla pro metody: odvozené metody nelze změnit usnadnění ze základní metody.</span><span class="sxs-lookup"><span data-stu-id="3e577-181">Rules for methods: Derived methods cannot change accessibility from the base method.</span></span> <span data-ttu-id="3e577-182">Výchozí chování, jsou všechny odvozené metody, které nejsou poznámkou `Transparent`.</span><span class="sxs-lookup"><span data-stu-id="3e577-182">For default behavior, all derived methods that are not annotated are `Transparent`.</span></span> <span data-ttu-id="3e577-183">Odvozené typy kritické způsobují výjimku, která je vyvolána, pokud přepsaná metoda není explicitně označena jako `SecurityCritical`.</span><span class="sxs-lookup"><span data-stu-id="3e577-183">Derivatives of critical types cause an exception to be thrown if the overridden method is not explicitly annotated as `SecurityCritical`.</span></span>  
  
 <span data-ttu-id="3e577-184">Následující tabulka zobrazuje typ povolené vzory dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="3e577-184">The following table shows the allowed type inheritance patterns.</span></span>  
  
|<span data-ttu-id="3e577-185">Base – třída</span><span class="sxs-lookup"><span data-stu-id="3e577-185">Base class</span></span>|<span data-ttu-id="3e577-186">Odvozená třída může být</span><span class="sxs-lookup"><span data-stu-id="3e577-186">Derived class can be</span></span>|  
|----------------|--------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`Transparent`|`Critical`|  
|`SafeCritical`|`SafeCritical`|  
|`SafeCritical`|`Critical`|  
|`Critical`|`Critical`|  
  
 <span data-ttu-id="3e577-187">Následující tabulka zobrazuje typ nepovoleném vzory dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="3e577-187">The following table shows the disallowed type inheritance patterns.</span></span>  
  
|<span data-ttu-id="3e577-188">Base – třída</span><span class="sxs-lookup"><span data-stu-id="3e577-188">Base class</span></span>|<span data-ttu-id="3e577-189">Nemůže být odvozené třídy</span><span class="sxs-lookup"><span data-stu-id="3e577-189">Derived class cannot be</span></span>|  
|----------------|-----------------------------|  
|`SafeCritical`|`Transparent`|  
|`Critical`|`Transparent`|  
|`Critical`|`SafeCritical`|  
  
 <span data-ttu-id="3e577-190">Následující tabulka zobrazuje povolené metoda vzory dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="3e577-190">The following table shows the allowed method inheritance patterns.</span></span>  
  
|<span data-ttu-id="3e577-191">Base – metoda</span><span class="sxs-lookup"><span data-stu-id="3e577-191">Base method</span></span>|<span data-ttu-id="3e577-192">Může být odvozené – metoda</span><span class="sxs-lookup"><span data-stu-id="3e577-192">Derived method can be</span></span>|  
|-----------------|---------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`SafeCritical`|`Transparent`|  
|`SafeCritical`|`SafeCritical`|  
|`Critical`|`Critical`|  
  
 <span data-ttu-id="3e577-193">Následující tabulka zobrazuje metodu nepovoleném vzory dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="3e577-193">The following table shows the disallowed method inheritance patterns.</span></span>  
  
|<span data-ttu-id="3e577-194">Base – metoda</span><span class="sxs-lookup"><span data-stu-id="3e577-194">Base method</span></span>|<span data-ttu-id="3e577-195">Nemůže být odvozené – metoda</span><span class="sxs-lookup"><span data-stu-id="3e577-195">Derived method cannot be</span></span>|  
|-----------------|------------------------------|  
|`Transparent`|`Critical`|  
|`SafeCritical`|`Critical`|  
|`Critical`|`Transparent`|  
|`Critical`|`SafeCritical`|  
  
> [!NOTE]
>  <span data-ttu-id="3e577-196">Tato pravidla dědičnosti se vztahují na úroveň 2 typy a členy.</span><span class="sxs-lookup"><span data-stu-id="3e577-196">These inheritance rules apply to level 2 types and members.</span></span> <span data-ttu-id="3e577-197">Typy v sestavení úroveň 1 může dědit vlastnosti z typy kritické pro zabezpečení na úrovni 2 a členy.</span><span class="sxs-lookup"><span data-stu-id="3e577-197">Types in level 1 assemblies can inherit from level 2 security-critical types and members.</span></span> <span data-ttu-id="3e577-198">Typy na úrovni 2 a členy proto musí mít samostatné dědičnost požadavků pro dědice úroveň 1.</span><span class="sxs-lookup"><span data-stu-id="3e577-198">Therefore, level 2 types and members must have separate inheritance demands for level 1 inheritors.</span></span>  
  
 [<span data-ttu-id="3e577-199">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="3e577-199">Back to top</span></span>](#top)  
  
<a name="additional"></a>   
## <a name="additional-information-and-rules"></a><span data-ttu-id="3e577-200">Další informace a pravidla</span><span class="sxs-lookup"><span data-stu-id="3e577-200">Additional Information and Rules</span></span>  
  
### <a name="linkdemand-support"></a><span data-ttu-id="3e577-201">Podpora LinkDemand</span><span class="sxs-lookup"><span data-stu-id="3e577-201">LinkDemand Support</span></span>  
 <span data-ttu-id="3e577-202">Nahradí model průhlednost úrovně 2 <xref:System.Security.Permissions.SecurityAction.LinkDemand> s <xref:System.Security.SecurityCriticalAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="3e577-202">The level 2 transparency model replaces the <xref:System.Security.Permissions.SecurityAction.LinkDemand> with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="3e577-203">V kódu starší verze (úroveň 1) <xref:System.Security.Permissions.SecurityAction.LinkDemand> automaticky považován za <xref:System.Security.Permissions.SecurityAction.Demand>.</span><span class="sxs-lookup"><span data-stu-id="3e577-203">In legacy (level 1) code, a <xref:System.Security.Permissions.SecurityAction.LinkDemand> is automatically treated as a <xref:System.Security.Permissions.SecurityAction.Demand>.</span></span>  
  
### <a name="reflection"></a><span data-ttu-id="3e577-204">Reflexe</span><span class="sxs-lookup"><span data-stu-id="3e577-204">Reflection</span></span>  
 <span data-ttu-id="3e577-205">Vyvolání kritické metody nebo čtení kritické položky spustí požadavek na úplný vztah důvěryhodnosti (stejně, jako kdyby byly vyvolání soukromá metoda nebo pole).</span><span class="sxs-lookup"><span data-stu-id="3e577-205">Invoking a critical method or reading a critical field triggers a demand for full trust (just as if you were invoking a private method or field).</span></span> <span data-ttu-id="3e577-206">Kód plné důvěryhodnosti tedy můžete vyvolat kritickou metodu, zatímco nelze částečně důvěryhodný kód.</span><span class="sxs-lookup"><span data-stu-id="3e577-206">Therefore, full-trust code can invoke a critical method, whereas partial-trust code cannot.</span></span>  
  
 <span data-ttu-id="3e577-207">Následující vlastnosti jsou přidané do <xref:System.Reflection> oboru názvů určete, zda je typ, metoda nebo pole `SecurityCritical`, `SecuritySafeCritical`, nebo `SecurityTransparent`: <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, a <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>.</span><span class="sxs-lookup"><span data-stu-id="3e577-207">The following properties have been added to the <xref:System.Reflection> namespace to determine whether the type, method, or field is `SecurityCritical`, `SecuritySafeCritical`, or `SecurityTransparent`:  <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, and <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>.</span></span> <span data-ttu-id="3e577-208">Použijte tyto vlastnosti k určení transparentnosti pomocí reflexe místo kontroly na přítomnost atribut.</span><span class="sxs-lookup"><span data-stu-id="3e577-208">Use these properties to determine transparency by using reflection instead of checking for the presence of the attribute.</span></span> <span data-ttu-id="3e577-209">Pravidla transparentnosti jsou komplexní a kontrola atributu nemusí být plně dostačující.</span><span class="sxs-lookup"><span data-stu-id="3e577-209">The transparency rules are complex, and checking for the attribute may not be sufficient.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3e577-210">A `SafeCritical` metoda vrátí `true` pro obě <xref:System.Type.IsSecurityCritical%2A> a <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, protože `SafeCritical` je skutečně kritická (má stejné schopnosti jako kód kritický pro, ale může být volána z transparentní kód).</span><span class="sxs-lookup"><span data-stu-id="3e577-210">A `SafeCritical` method returns `true` for both <xref:System.Type.IsSecurityCritical%2A> and <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, because `SafeCritical` is indeed critical (it has the same capabilities as critical code, but it can be called from transparent code).</span></span>  
  
 <span data-ttu-id="3e577-211">Dynamické metody dědí transparentnost modulů, které jsou připojené k; nedědí transparentnost typu (pokud jsou připojené k typu).</span><span class="sxs-lookup"><span data-stu-id="3e577-211">Dynamic methods inherit the transparency of the modules they are attached to; they do not inherit the transparency of the type (if they are attached to a type).</span></span>  
  
### <a name="skip-verification-in-full-trust"></a><span data-ttu-id="3e577-212">Přeskočit ověření v režimu plné důvěryhodnosti</span><span class="sxs-lookup"><span data-stu-id="3e577-212">Skip Verification in Full Trust</span></span>  
 <span data-ttu-id="3e577-213">Můžete přeskočit ověření pro plně důvěryhodná transparentní sestavení pomocí nastavení <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> vlastnost `true` v <xref:System.Security.SecurityRulesAttribute> atribut:</span><span class="sxs-lookup"><span data-stu-id="3e577-213">You can skip verification for fully trusted transparent assemblies by setting the <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property to `true` in the <xref:System.Security.SecurityRulesAttribute> attribute:</span></span>  
  
 `[assembly: SecurityRules(SecurityRuleSet.Level2, SkipVerificationInFullTrust = true)]`  
  
 <span data-ttu-id="3e577-214"><xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> Vlastnost je `false` ve výchozím nastavení, takže vlastnost musí být nastavená `true` pro přeskočení ověření.</span><span class="sxs-lookup"><span data-stu-id="3e577-214">The <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property is `false` by default, so the property must be set to `true` to skip verification.</span></span> <span data-ttu-id="3e577-215">To by mělo být provedeno pouze pro účely optimalizace.</span><span class="sxs-lookup"><span data-stu-id="3e577-215">This should be done for optimization purposes only.</span></span> <span data-ttu-id="3e577-216">Měli byste zajistit, že transparentní kód v sestavení je ověřitelný pomocí `transparent` možnost [Nástroj PEVerify](../../../docs/framework/tools/peverify-exe-peverify-tool.md).</span><span class="sxs-lookup"><span data-stu-id="3e577-216">You should ensure that the transparent code in the assembly is verifiable by using the `transparent` option in the [PEVerify tool](../../../docs/framework/tools/peverify-exe-peverify-tool.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e577-217">Viz také</span><span class="sxs-lookup"><span data-stu-id="3e577-217">See Also</span></span>  
 [<span data-ttu-id="3e577-218">Kód transparentní pro zabezpečení, úroveň 1</span><span class="sxs-lookup"><span data-stu-id="3e577-218">Security-Transparent Code, Level 1</span></span>](../../../docs/framework/misc/security-transparent-code-level-1.md)  
 [<span data-ttu-id="3e577-219">Změny zabezpečení</span><span class="sxs-lookup"><span data-stu-id="3e577-219">Security Changes</span></span>](../../../docs/framework/security/security-changes.md)
