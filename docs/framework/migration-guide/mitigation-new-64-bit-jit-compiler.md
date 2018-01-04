---
title: "Omezení rizik: Nové 64-bit JIT kompilátoru"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JIT compiler, 64-bit
- JIT compilation, 64-bit
- RyuJIT compiler
ms.assetid: 0332dabc-72c5-4bdc-8975-20d717802b17
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ea1f5a832e2db63590fe5cbc3425078e17d3825
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="mitigation-new-64-bit-jit-compiler"></a><span data-ttu-id="3acab-102">Omezení rizik: Nové 64-bit JIT kompilátoru</span><span class="sxs-lookup"><span data-stu-id="3acab-102">Mitigation: New 64-bit JIT Compiler</span></span>
<span data-ttu-id="3acab-103">Od verze rozhraní .NET Framework 4.6, modul runtime zahrnuje nové kompilátoru JIT 64-bit pro kompilaci za běhu.</span><span class="sxs-lookup"><span data-stu-id="3acab-103">Starting with the .NET Framework 4.6, the runtime includes a new 64-bit JIT compiler for just-in-time compilation.</span></span> <span data-ttu-id="3acab-104">Tato změna nemá vliv kompilace s 32-bit kompilátoru za běhu.</span><span class="sxs-lookup"><span data-stu-id="3acab-104">This change does not affect compilation with the  32-bit JIT compiler.</span></span>  
  
## <a name="unexpected-behavior-or-exceptions"></a><span data-ttu-id="3acab-105">Neočekávané chování nebo výjimky</span><span class="sxs-lookup"><span data-stu-id="3acab-105">Unexpected behavior or exceptions</span></span>  
 <span data-ttu-id="3acab-106">V některých případech výsledky kompilace pomocí nové 64bitový kompilátor JIT v výjimku modulu runtime nebo v chování, které není dodržen při provádění kódu starší 64bitový kompilátor JIT zkompilují.</span><span class="sxs-lookup"><span data-stu-id="3acab-106">In some cases, compilation with the new 64-bit JIT compiler results in a runtime exception or in behavior that is not observed when executing code compiled by the older 64-bit JIT compiler.</span></span> <span data-ttu-id="3acab-107">Známé rozdíly zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="3acab-107">The known differences include the following:</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3acab-108">Všechny tyto známé problémy mít byly řešeny v nové 64bitový kompilátor vydané s rozhraním .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="3acab-108">All of these known issues have been addressed in the new 64-bit compiler released with the .NET Framework 4.6.2.</span></span> <span data-ttu-id="3acab-109">Většina mít také vyřeší ve vydáních služby rozhraní .NET Framework 4.6 a 4.6.1, které jsou součástí služby Windows Update.</span><span class="sxs-lookup"><span data-stu-id="3acab-109">Most have also been addressed in service releases of the .NET Framework 4.6 and 4.6.1 that are included with Windows Update.</span></span> <span data-ttu-id="3acab-110">Můžete vyloučit tyto problémy zajištěním, které vaši verzi systému Windows je aktuální, nebo po upgradu na rozhraní .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="3acab-110">You can eliminate these issues by ensuring that your version of Windows is up to date, or by upgrading to the .NET Framework 4.6.2.</span></span>  
  
-   <span data-ttu-id="3acab-111">Za určitých podmínek může vyvolat operace rozbalení <xref:System.NullReferenceException> v sestavení pro vydání s optimalizací zapnutý.</span><span class="sxs-lookup"><span data-stu-id="3acab-111">Under certain conditions, an unboxing operation may throw a <xref:System.NullReferenceException> in Release builds with optimization turned on.</span></span>  
  
-   <span data-ttu-id="3acab-112">V některých případech může spuštění produkčním kódu v textu obsáhlou metodu throw <xref:System.StackOverflowException>.</span><span class="sxs-lookup"><span data-stu-id="3acab-112">In some cases, execution of production code in a large method body may throw a <xref:System.StackOverflowException>.</span></span>  
  
-   <span data-ttu-id="3acab-113">Za určitých podmínek struktury předána metodě, jsou považovány za odkazové typy místo typy hodnot v verzi sestavení.</span><span class="sxs-lookup"><span data-stu-id="3acab-113">Under certain conditions, structures passed to a method are treated as reference types rather than value types in Release builds.</span></span> <span data-ttu-id="3acab-114">Jedním z projevů tohoto problému je, že jednotlivé položky v kolekci se objeví v neočekávaném pořadí.</span><span class="sxs-lookup"><span data-stu-id="3acab-114">One of the manifestations of this issue is that the individual items in a collection appear in an unexpected order.</span></span>  
  
-   <span data-ttu-id="3acab-115">Za určitých podmínek, při porovnání <xref:System.UInt16> hodnoty sadou jejich rozšířené je nesprávný, pokud je povolená optimalizace.</span><span class="sxs-lookup"><span data-stu-id="3acab-115">Under certain conditions, the comparison of <xref:System.UInt16> values with their high bit set is incorrect if optimization is enabled.</span></span>  
  
-   <span data-ttu-id="3acab-116">Za určitých podmínek, zejména při inicializaci pole hodnot, inicializace paměti pomocí <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> IL instrukce může inicializovat paměť s nesprávnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3acab-116">Under certain conditions, particularly when initializing array values, memory initialization by the <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> IL instruction may initialize memory with an incorrect value.</span></span> <span data-ttu-id="3acab-117">To může způsobit buď v neošetřené výjimky nebo nesprávné výstup.</span><span class="sxs-lookup"><span data-stu-id="3acab-117">This can result either in an unhandled exception or incorrect output.</span></span>  
  
-   <span data-ttu-id="3acab-118">Za určitých výjimečných podmínek, může vrátit testu podmíněného bit nesprávném <xref:System.Boolean> hodnotu nebo vyvolána výjimka, pokud jsou povolené optimalizace kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="3acab-118">Under certain rare conditions, a conditional bit test can return the incorrect <xref:System.Boolean> value or throw an exception if compiler optimizations are enabled.</span></span>  
  
-   <span data-ttu-id="3acab-119">Za určitých podmínek Pokud `if` příkaz se používá k testování pro podmínku před vstupem `try` bloku a ve výstupu z `try` bloku a stejné podmínku vyhodnotí v `catch` nebo `finally` bloku, nové 64bitový kompilátor JIT odebere `if` podmínky z `catch` nebo `finally` blokovat, když optimalizuje kódu.</span><span class="sxs-lookup"><span data-stu-id="3acab-119">Under certain conditions, if an `if` statement is used to test for a condition before entering  a `try` block and in the exit from the `try` block, and the same condition is evaluated in the `catch` or `finally` block, the new 64-bit JIT compiler removes the `if` condition from the `catch` or `finally` block when it optimizes code.</span></span> <span data-ttu-id="3acab-120">V důsledku toho code uvnitř `if` příkaz v `catch` nebo `finally` bezpodmínečně vykonání bloku.</span><span class="sxs-lookup"><span data-stu-id="3acab-120">As a result, code inside the `if` statement in the `catch` or `finally` block is executed unconditionally.</span></span>  
  
<a name="General"></a>   
## <a name="mitigation-of-known-issues"></a><span data-ttu-id="3acab-121">Zmírnění dopadů známých problémů</span><span class="sxs-lookup"><span data-stu-id="3acab-121">Mitigation of known issues</span></span>  
 <span data-ttu-id="3acab-122">Pokud narazíte na problémy uvedené výše, můžete je vyřešit pomocí některého z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="3acab-122">If you encounter the issues listed above, you can address them by doing any of the following:</span></span>  
  
-   <span data-ttu-id="3acab-123">Upgrade na rozhraní .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="3acab-123">Upgrade to the .NET Framework 4.6.2.</span></span> <span data-ttu-id="3acab-124">Nové 64bitový kompilátor součástí rozhraní .NET Framework 4.6.2 řeší každý z těchto známých problémů.</span><span class="sxs-lookup"><span data-stu-id="3acab-124">The new 64-bit compiler included with the .NET Framework 4.6.2 addresses each of these known issues.</span></span>  
  
-   <span data-ttu-id="3acab-125">Zajistěte, aby byl vaši verzi systému Windows aktuální spuštěním služby Windows Update.</span><span class="sxs-lookup"><span data-stu-id="3acab-125">Ensure that your version of Windows is up to date by running Windows Update.</span></span> <span data-ttu-id="3acab-126">Aktualizace služby rozhraní .NET Framework 4.6 a 4.6.1 se vztahují na všechny tyto problémy s výjimkou <xref:System.NullReferenceException> v rozbalení operace.</span><span class="sxs-lookup"><span data-stu-id="3acab-126">Service updates to the .NET Framework 4.6 and 4.6.1 address each of these issues except the <xref:System.NullReferenceException> in an unboxing operation.</span></span>  
  
-   <span data-ttu-id="3acab-127">Kompilace s starší 64bitový kompilátor JIT.</span><span class="sxs-lookup"><span data-stu-id="3acab-127">Compile with the older 64-bit JIT compiler.</span></span> <span data-ttu-id="3acab-128">Najdete v článku [zmírnění další problémy](#Other) části Další informace o tom, jak to udělat.</span><span class="sxs-lookup"><span data-stu-id="3acab-128">See the [Mitigation of other issues](#Other) section for more information on how to do this.</span></span>  
  
<a name="Other"></a>   
## <a name="mitigation-of-other-issues"></a><span data-ttu-id="3acab-129">Zmírnění dopadů jiné problémy</span><span class="sxs-lookup"><span data-stu-id="3acab-129">Mitigation of other issues</span></span>  
 <span data-ttu-id="3acab-130">Pokud narazíte na žádné jiné rozdíl v chování mezi kódem kompilovat s starší 64bitový kompilátor a nové 64bitový kompilátor JIT, nebo mezi ladění a vydání verze aplikace, které jsou kompilovat s novou 64bitový kompilátor JIT, můžete provést následující sestavovat aplikace pomocí starší 64bitový kompilátor JIT:</span><span class="sxs-lookup"><span data-stu-id="3acab-130">If you encounter any other difference in behavior between code compiled with the older 64-bit compiler and the new 64-bit JIT compiler, or between the debug and release versions of your app that are both compiled with the new 64-bit JIT compiler, you can do the following to compile your app with the older 64-bit JIT compiler:</span></span>  
  
-   <span data-ttu-id="3acab-131">Na základě jednotlivých aplikací, můžete přidat [ \<useLegacyJit >](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md) element konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="3acab-131">On a per-application basis, you can add the [\<useLegacyJit>](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md) element to your application's configuration file.</span></span> <span data-ttu-id="3acab-132">Následující zakáže kompilaci s novou 64bitový kompilátor JIT a místo toho používá starší verze 64bitový kompilátor JIT.</span><span class="sxs-lookup"><span data-stu-id="3acab-132">The following disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
    ```xml  
    <?xml version ="1.0"?>  
    <configuration>  
        <runtime>  
           <useLegacyJit enabled="1" />  
        </runtime>  
    </configuration>  
    ```  
  
-   <span data-ttu-id="3acab-133">U každého uživatele zvlášť, můžete přidat `REG_DWORD` hodnotu s názvem `useLegacyJit` k `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` klíče registru.</span><span class="sxs-lookup"><span data-stu-id="3acab-133">On a per-user basis, you can add a `REG_DWORD` value named `useLegacyJit` to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key of the registry.</span></span> <span data-ttu-id="3acab-134">Hodnota 1 povolí starší verze kompilátoru JIT 64-bit; Hodnota 0 zakáže ho a umožňuje nové 64bitový kompilátor JIT.</span><span class="sxs-lookup"><span data-stu-id="3acab-134">A value of 1 enables the legacy 64-bit JIT compiler; a value of 0 disables it and enables the new 64-bit JIT compiler.</span></span>  
  
-   <span data-ttu-id="3acab-135">U jednotlivých počítačů, můžete přidat `REG_DWORD` hodnotu s názvem `useLegacyJit` k `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` klíče registru.</span><span class="sxs-lookup"><span data-stu-id="3acab-135">On a per-machine basis, you can add a `REG_DWORD` value named `useLegacyJit` to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key of the registry.</span></span> <span data-ttu-id="3acab-136">Hodnota 1 povolí starší verze kompilátoru JIT 64-bit; Hodnota 0 zakáže ho a umožňuje nové 64bitový kompilátor JIT.</span><span class="sxs-lookup"><span data-stu-id="3acab-136">A value of 1 enables the legacy 64-bit JIT compiler; a value of 0 disables it and enables the new 64-bit JIT compiler.</span></span>  
  
 <span data-ttu-id="3acab-137">Vám může také dejte nám vědět o problému pomocí hlášení chyby na [Microsoft Connect](https://connect.microsoft.com/VisualStudio).</span><span class="sxs-lookup"><span data-stu-id="3acab-137">You can also let us know about the problem by reporting a bug on [Microsoft Connect](https://connect.microsoft.com/VisualStudio).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3acab-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="3acab-138">See Also</span></span>  
 [<span data-ttu-id="3acab-139">Změny v modulu runtime</span><span class="sxs-lookup"><span data-stu-id="3acab-139">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)  
 [<span data-ttu-id="3acab-140">\<useLegacyJit > elementu</span><span class="sxs-lookup"><span data-stu-id="3acab-140">\<useLegacyJit> Element</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md)
