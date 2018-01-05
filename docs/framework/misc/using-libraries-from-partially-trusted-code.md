---
title: "Používání knihoven z částečně důvěryhodného kódu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [.NET Framework], partially trusted code
- partially trusted code
- partial trust
- AllowPartiallyTrustedCallersAttribute attribute
- code access security, partially trusted code
- APTCA
ms.assetid: dd66cd4c-b087-415f-9c3e-94e3a1835f74
caps.latest.revision: "25"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 00f532e4e93936dbd719f2b8a0c060e54e16425b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="using-libraries-from-partially-trusted-code"></a><span data-ttu-id="7c2ee-102">Používání knihoven z částečně důvěryhodného kódu</span><span class="sxs-lookup"><span data-stu-id="7c2ee-102">Using Libraries from Partially Trusted Code</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
> [!NOTE]
>  <span data-ttu-id="7c2ee-103">Toto téma řeší chování sestavení se silným názvem a platí jenom pro [úrovně 1](../../../docs/framework/misc/security-transparent-code-level-1.md) sestavení.</span><span class="sxs-lookup"><span data-stu-id="7c2ee-103">This topic addresses the behavior of strong-named assemblies and applies only to [Level 1](../../../docs/framework/misc/security-transparent-code-level-1.md) assemblies.</span></span> <span data-ttu-id="7c2ee-104">[Kód transparentní pro zabezpečení, úroveň 2](../../../docs/framework/misc/security-transparent-code-level-2.md) sestavení v [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] nebo později nemá vliv silné názvy.</span><span class="sxs-lookup"><span data-stu-id="7c2ee-104">[Security-Transparent Code, Level 2](../../../docs/framework/misc/security-transparent-code-level-2.md) assemblies in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] or later are not affected by strong names.</span></span> <span data-ttu-id="7c2ee-105">Další informace o změnách systému zabezpečení najdete v tématu [změny zabezpečení](../../../docs/framework/security/security-changes.md).</span><span class="sxs-lookup"><span data-stu-id="7c2ee-105">For more information about changes to the security system, see [Security Changes](../../../docs/framework/security/security-changes.md).</span></span>  
  
 <span data-ttu-id="7c2ee-106">Aplikace, které přijímají menší než úplný vztah důvěryhodnosti z jeho hostitele nebo izolovaného prostoru není povoleno volat sdílené spravované knihovny zapisovače knihovny specificky umožňují jim prostřednictvím <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="7c2ee-106">Applications that receive less than full trust from their host or sandbox are not allowed to call shared managed libraries unless the library writer specifically allows them to through the use of the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute.</span></span> <span data-ttu-id="7c2ee-107">Autoři aplikace musí být tedy vědět, že některé knihovny nebudete mít k dispozici k nim z částečně důvěryhodného kontextu.</span><span class="sxs-lookup"><span data-stu-id="7c2ee-107">Therefore, application writers must be aware that some libraries will not be available to them from a partially trusted context.</span></span> <span data-ttu-id="7c2ee-108">Ve výchozím nastavení, všechny kódu, která se spouští v částečné důvěryhodnosti [izolovaného prostoru](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md) a není v seznamu plné důvěryhodnosti sestavení je částečně důvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="7c2ee-108">By default, all code that executes in a partial-trust [sandbox](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md) and is not in the list of full-trust assemblies is partially trusted.</span></span> <span data-ttu-id="7c2ee-109">Pokud neočekáváte kódu spouštění z částečně důvěryhodného kontextu nebo má být volána částečně důvěryhodným kódem, nemáte starat o informace v této části.</span><span class="sxs-lookup"><span data-stu-id="7c2ee-109">If you do not expect your code to be executed from a partially trusted context or to be called by partially trusted code, you do not have to be concerned about the information in this section.</span></span> <span data-ttu-id="7c2ee-110">Však můžete psát kód, který musí komunikovat s částečně důvěryhodným kódem nebo pracovat z částečně důvěryhodného kontextu, je třeba zvážit následující faktory:</span><span class="sxs-lookup"><span data-stu-id="7c2ee-110">However, if you write code that must interact with partially trusted code or operate from a partially trusted context, you should consider the following factors:</span></span>  
  
-   <span data-ttu-id="7c2ee-111">Knihovny musí být podepsané se silným názvem, aby bylo možné sdílet mezi více aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="7c2ee-111">Libraries must be signed with a strong name in order to be shared by multiple applications.</span></span> <span data-ttu-id="7c2ee-112">Silné názvy povolit kódu být umístěny v globální mezipaměti sestavení nebo přidat do seznamu plné důvěryhodnosti sandboxing <xref:System.AppDomain>, a povolit příjemcům ověřit, že konkrétním mobilního kódu ve skutečnosti pocházejí od vás.</span><span class="sxs-lookup"><span data-stu-id="7c2ee-112">Strong names allow your code to be placed in the global assembly cache or added to the full-trust list of a sandboxing <xref:System.AppDomain>, and allow consumers to verify that a particular piece of mobile code actually originates from you.</span></span>  
  
-   <span data-ttu-id="7c2ee-113">Ve výchozím nastavení, silným názvem [úrovně 1](../../../docs/framework/misc/security-transparent-code-level-1.md) sdílené knihovny provést implicitní [LinkDemand](../../../docs/framework/misc/link-demands.md) pro úplné důvěryhodnosti automaticky, aniž by museli něco dělat zapisovač knihovny.</span><span class="sxs-lookup"><span data-stu-id="7c2ee-113">By default, strong-named [Level 1](../../../docs/framework/misc/security-transparent-code-level-1.md) shared libraries perform an implicit [LinkDemand](../../../docs/framework/misc/link-demands.md) for full trust automatically, without the library writer having to do anything.</span></span>  
  
-   <span data-ttu-id="7c2ee-114">Pokud volající nemá úplný vztah důvěryhodnosti, ale pořád se pokouší volat tuto knihovnu, modul runtime vyvolá <xref:System.Security.SecurityException> a volající není povoleno propojení do knihovny.</span><span class="sxs-lookup"><span data-stu-id="7c2ee-114">If a caller does not have full trust but still tries to call such a library, the runtime throws a <xref:System.Security.SecurityException> and the caller is not allowed to link to the library.</span></span>  
  
-   <span data-ttu-id="7c2ee-115">Aby bylo možné zakázat automatické **LinkDemand** a zabránit vyvolání výjimky, můžete umístit **AllowPartiallyTrustedCallersAttribute** atribut na sestavení rozsahu sdílenou Knihovna.</span><span class="sxs-lookup"><span data-stu-id="7c2ee-115">In order to disable the automatic **LinkDemand** and prevent the exception from being thrown, you can place the **AllowPartiallyTrustedCallersAttribute** attribute on the assembly scope of a shared library.</span></span> <span data-ttu-id="7c2ee-116">Tento atribut umožňuje vašich knihovnách, která se má volat z částečně důvěryhodného spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="7c2ee-116">This attribute allows your libraries to be called from partially trusted managed code.</span></span>  
  
-   <span data-ttu-id="7c2ee-117">Částečně důvěryhodný kód, který je udělen přístup k tomuto atributu do knihovny, je stále podléhá další omezení, které jsou definované <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="7c2ee-117">Partially trusted code that is granted access to a library with this attribute is still subject to further restrictions defined by the <xref:System.AppDomain>.</span></span>  
  
-   <span data-ttu-id="7c2ee-118">Neexistuje žádný programový způsob pro částečně důvěryhodného kódu pro volání knihovny, který nemá **AllowPartiallyTrustedCallersAttribute** atribut.</span><span class="sxs-lookup"><span data-stu-id="7c2ee-118">There is no programmatic way for partially trusted code to call a library that does not have the **AllowPartiallyTrustedCallersAttribute** attribute.</span></span>  
  
 <span data-ttu-id="7c2ee-119">Knihovny, které jsou privátní na konkrétní aplikaci nevyžadují silný název nebo **AllowPartiallyTrustedCallersAttribute** atribut a nemůže být odkazován potenciálně škodlivého kódu, mimo aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7c2ee-119">Libraries that are private to a specific application do not require a strong name or the **AllowPartiallyTrustedCallersAttribute** attribute and cannot be referenced by potentially malicious code outside the application.</span></span> <span data-ttu-id="7c2ee-120">Takový kód je chráněna proti zneužití úmyslnému i neúmyslnému částečně důvěryhodného kódu mobilní bez vývojář si museli dělat žádné další.</span><span class="sxs-lookup"><span data-stu-id="7c2ee-120">Such code is protected against intentional or unintentional misuse by partially trusted mobile code without the developer having to do anything extra.</span></span>  
  
 <span data-ttu-id="7c2ee-121">Je třeba zvážit explicitní povolení používání částečně důvěryhodného kódu pro následující typy kódu:</span><span class="sxs-lookup"><span data-stu-id="7c2ee-121">You should consider explicitly enabling use by partially trusted code for the following types of code:</span></span>  
  
-   <span data-ttu-id="7c2ee-122">Kód, který byl usilovně testován pro chyby zabezpečení a je v souladu se zásadami popsanými v [pokyny zabezpečení kódování](../../../docs/standard/security/secure-coding-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="7c2ee-122">Code that has been diligently tested for security vulnerabilities and is in compliance with the guidelines described in [Secure Coding Guidelines](../../../docs/standard/security/secure-coding-guidelines.md).</span></span>  
  
-   <span data-ttu-id="7c2ee-123">Knihovny kódu se silným názvem, které jsou napsané konkrétně pro částečně důvěryhodné scénáře.</span><span class="sxs-lookup"><span data-stu-id="7c2ee-123">Strong-named code libraries that are specifically written for partially trusted scenarios.</span></span>  
  
-   <span data-ttu-id="7c2ee-124">Všechny součásti (jestli částečně nebo zcela důvěryhodné) podepsáno silným názvem, který bude volán kódem, který byl stažen z Internetu.</span><span class="sxs-lookup"><span data-stu-id="7c2ee-124">Any components (whether partially or fully trusted) signed with a strong name that will be called by code that is downloaded from the Internet.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7c2ee-125">Některé třídy v knihovně tříd rozhraní .NET Framework nemají **AllowPartiallyTrustedCallersAttribute** atribut a nedají se volat částečně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="7c2ee-125">Some classes in the .NET Framework class library do not have the **AllowPartiallyTrustedCallersAttribute** attribute and cannot be called by partially trusted code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c2ee-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="7c2ee-126">See Also</span></span>  
 [<span data-ttu-id="7c2ee-127">Zabezpečení přístupu kódu</span><span class="sxs-lookup"><span data-stu-id="7c2ee-127">Code Access Security</span></span>](../../../docs/framework/misc/code-access-security.md)
