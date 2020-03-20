---
title: 'Zmírnění: Nový 64bitový kompilátor JIT'
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compiler, 64-bit
- JIT compilation, 64-bit
- RyuJIT compiler
ms.assetid: 0332dabc-72c5-4bdc-8975-20d717802b17
ms.openlocfilehash: 883aaf032bde632b08f965d3450cfbea4feb8e65
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181255"
---
# <a name="mitigation-new-64-bit-jit-compiler"></a><span data-ttu-id="289d9-102">Zmírnění: Nový 64bitový kompilátor JIT</span><span class="sxs-lookup"><span data-stu-id="289d9-102">Mitigation: New 64-bit JIT Compiler</span></span>
<span data-ttu-id="289d9-103">Počínaje rozhraním .NET Framework 4.6 obsahuje runtime nový 64bitový kompilátor JIT pro kompilaci just-in-time.</span><span class="sxs-lookup"><span data-stu-id="289d9-103">Starting with the .NET Framework 4.6, the runtime includes a new 64-bit JIT compiler for just-in-time compilation.</span></span> <span data-ttu-id="289d9-104">Tato změna nemá vliv na kompilaci s 32bitovým kompilátorem JIT.</span><span class="sxs-lookup"><span data-stu-id="289d9-104">This change does not affect compilation with the  32-bit JIT compiler.</span></span>  
  
## <a name="unexpected-behavior-or-exceptions"></a><span data-ttu-id="289d9-105">Neočekávané chování nebo výjimky</span><span class="sxs-lookup"><span data-stu-id="289d9-105">Unexpected behavior or exceptions</span></span>  
 <span data-ttu-id="289d9-106">V některých případech kompilace s novým 64bitový kompilátor JIT výsledky v modulu runtime výjimku nebo v chování, které není pozorováno při provádění kódu zkompilovaného starší 64bitový kompilátor JIT.</span><span class="sxs-lookup"><span data-stu-id="289d9-106">In some cases, compilation with the new 64-bit JIT compiler results in a runtime exception or in behavior that is not observed when executing code compiled by the older 64-bit JIT compiler.</span></span> <span data-ttu-id="289d9-107">Známé rozdíly zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="289d9-107">The known differences include the following:</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="289d9-108">Všechny tyto známé problémy byly vyřešeny v novém 64bitovém kompilátoru vydaném s rozhraním .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="289d9-108">All of these known issues have been addressed in the new 64-bit compiler released with the .NET Framework 4.6.2.</span></span> <span data-ttu-id="289d9-109">Většina z nich byla také řešena ve verzích služby .NET Framework 4.6 a 4.6.1, které jsou součástí služby Windows Update.</span><span class="sxs-lookup"><span data-stu-id="289d9-109">Most have also been addressed in service releases of the .NET Framework 4.6 and 4.6.1 that are included with Windows Update.</span></span> <span data-ttu-id="289d9-110">Tyto problémy můžete odstranit zajištěním, že vaše verze systému Windows je aktuální, nebo upgradem na rozhraní .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="289d9-110">You can eliminate these issues by ensuring that your version of Windows is up to date, or by upgrading to the .NET Framework 4.6.2.</span></span>  
  
- <span data-ttu-id="289d9-111">Za určitých podmínek může operace <xref:System.NullReferenceException> rozbalení vyvolat sestavení v verzi se zapnutou optimalizací.</span><span class="sxs-lookup"><span data-stu-id="289d9-111">Under certain conditions, an unboxing operation may throw a <xref:System.NullReferenceException> in Release builds with optimization turned on.</span></span>  
  
- <span data-ttu-id="289d9-112">V některých případech provádění výrobního kódu v těle <xref:System.StackOverflowException>velké metody může vyvolat .</span><span class="sxs-lookup"><span data-stu-id="289d9-112">In some cases, execution of production code in a large method body may throw a <xref:System.StackOverflowException>.</span></span>  
  
- <span data-ttu-id="289d9-113">Za určitých podmínek struktury předané metodě jsou považovány za typy odkazů, nikoli jako typy hodnot v sestaveních release.</span><span class="sxs-lookup"><span data-stu-id="289d9-113">Under certain conditions, structures passed to a method are treated as reference types rather than value types in Release builds.</span></span> <span data-ttu-id="289d9-114">Jedním z projevů tohoto problému je, že jednotlivé položky v kolekci se zobrazí v neočekávaném pořadí.</span><span class="sxs-lookup"><span data-stu-id="289d9-114">One of the manifestations of this issue is that the individual items in a collection appear in an unexpected order.</span></span>  
  
- <span data-ttu-id="289d9-115">Za určitých <xref:System.UInt16> podmínek porovnání hodnot s jejich vysokou bitovou sadou je nesprávné, pokud je povolena optimalizace.</span><span class="sxs-lookup"><span data-stu-id="289d9-115">Under certain conditions, the comparison of <xref:System.UInt16> values with their high bit set is incorrect if optimization is enabled.</span></span>  
  
- <span data-ttu-id="289d9-116">Za určitých podmínek, zejména při inicializaci hodnot pole, může inicializace paměti inicializací <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> il inicializace s nesprávnou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="289d9-116">Under certain conditions, particularly when initializing array values, memory initialization by the <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> IL instruction may initialize memory with an incorrect value.</span></span> <span data-ttu-id="289d9-117">To může mít za následek neošetřené výjimky nebo nesprávný výstup.</span><span class="sxs-lookup"><span data-stu-id="289d9-117">This can result either in an unhandled exception or incorrect output.</span></span>  
  
- <span data-ttu-id="289d9-118">Za určitých výjimečných podmínek podmíněný <xref:System.Boolean> bitový test může vrátit nesprávnou hodnotu nebo vyvolat výjimku, pokud jsou povoleny optimalizace kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="289d9-118">Under certain rare conditions, a conditional bit test can return the incorrect <xref:System.Boolean> value or throw an exception if compiler optimizations are enabled.</span></span>  
  
- <span data-ttu-id="289d9-119">Za určitých podmínek, `if` pokud příkaz se používá `try` k testování podmínky před `try` zadáním bloku a výstupu `catch` z `finally` bloku a stejné podmínky je vyhodnocena `if` v `catch` nebo `finally` bloku, nový 64bitový kompilátor JIT odebere podmínku z nebo bloku při optimalizaci kódu.</span><span class="sxs-lookup"><span data-stu-id="289d9-119">Under certain conditions, if an `if` statement is used to test for a condition before entering  a `try` block and in the exit from the `try` block, and the same condition is evaluated in the `catch` or `finally` block, the new 64-bit JIT compiler removes the `if` condition from the `catch` or `finally` block when it optimizes code.</span></span> <span data-ttu-id="289d9-120">V důsledku toho je `if` kód `catch` uvnitř `finally` příkazu v bloku nebo proveden bezpodmínečně.</span><span class="sxs-lookup"><span data-stu-id="289d9-120">As a result, code inside the `if` statement in the `catch` or `finally` block is executed unconditionally.</span></span>  
  
<a name="General"></a>
## <a name="mitigation-of-known-issues"></a><span data-ttu-id="289d9-121">Zmírnění známých problémů</span><span class="sxs-lookup"><span data-stu-id="289d9-121">Mitigation of known issues</span></span>  
 <span data-ttu-id="289d9-122">Pokud narazíte na výše uvedené problémy, můžete je řešit některou z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="289d9-122">If you encounter the issues listed above, you can address them by doing any of the following:</span></span>  
  
- <span data-ttu-id="289d9-123">Upgrade na rozhraní .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="289d9-123">Upgrade to the .NET Framework 4.6.2.</span></span> <span data-ttu-id="289d9-124">Nový 64bitový kompilátor, který je součástí rozhraní .NET Framework 4.6.2, řeší každý z těchto známých problémů.</span><span class="sxs-lookup"><span data-stu-id="289d9-124">The new 64-bit compiler included with the .NET Framework 4.6.2 addresses each of these known issues.</span></span>  
  
- <span data-ttu-id="289d9-125">Spuštěním služby Windows Update zajistíte aktuálnost vaší verze systému Windows.</span><span class="sxs-lookup"><span data-stu-id="289d9-125">Ensure that your version of Windows is up to date by running Windows Update.</span></span> <span data-ttu-id="289d9-126">Aktualizace služby rozhraní .NET Framework 4.6 a 4.6.1 <xref:System.NullReferenceException> řeší každý z těchto problémů s výjimkou operace rozbalení.</span><span class="sxs-lookup"><span data-stu-id="289d9-126">Service updates to the .NET Framework 4.6 and 4.6.1 address each of these issues except the <xref:System.NullReferenceException> in an unboxing operation.</span></span>  
  
- <span data-ttu-id="289d9-127">Kompilujte se starším 64bitovým kompilátorem JIT.</span><span class="sxs-lookup"><span data-stu-id="289d9-127">Compile with the older 64-bit JIT compiler.</span></span> <span data-ttu-id="289d9-128">Další informace o tom, jak to provést, naleznete v části [Zmírnění dalších problémů.](#Other)</span><span class="sxs-lookup"><span data-stu-id="289d9-128">See the [Mitigation of other issues](#Other) section for more information on how to do this.</span></span>  
  
<a name="Other"></a>
## <a name="mitigation-of-other-issues"></a><span data-ttu-id="289d9-129">Zmírnění dalších problémů</span><span class="sxs-lookup"><span data-stu-id="289d9-129">Mitigation of other issues</span></span>  
 <span data-ttu-id="289d9-130">Pokud narazíte na jiný rozdíl v chování mezi kódem kompilovaným se starším 64bitovým kompilátorem a novým 64bitovým kompilátorem JIT nebo mezi ladicí mi a verzí aplikace, které jsou zkompilovány s novým 64bitovým kompilátorem JIT, můžete provést následující postup kompilace aplikace se starším 64bitovým kompilátorem JIT:</span><span class="sxs-lookup"><span data-stu-id="289d9-130">If you encounter any other difference in behavior between code compiled with the older 64-bit compiler and the new 64-bit JIT compiler, or between the debug and release versions of your app that are both compiled with the new 64-bit JIT compiler, you can do the following to compile your app with the older 64-bit JIT compiler:</span></span>  
  
- <span data-ttu-id="289d9-131">Na základě pro aplikaci, můžete přidat [ \<useLegacyJit>](../configure-apps/file-schema/runtime/uselegacyjit-element.md) prvek do konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="289d9-131">On a per-application basis, you can add the [\<useLegacyJit>](../configure-apps/file-schema/runtime/uselegacyjit-element.md) element to your application's configuration file.</span></span> <span data-ttu-id="289d9-132">Následující zakáže kompilaci s novým 64bitovým kompilátorem JIT a místo toho používá starší 64bitový kompilátor JIT.</span><span class="sxs-lookup"><span data-stu-id="289d9-132">The following disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
    ```xml  
    <?xml version ="1.0"?>  
    <configuration>  
        <runtime>  
           <useLegacyJit enabled="1" />  
        </runtime>  
    </configuration>  
    ```  
  
- <span data-ttu-id="289d9-133">Na základě pro jednotlivé uživatele můžete `REG_DWORD` přidat `useLegacyJit` hodnotu pojmenovanou `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` do klíče registru.</span><span class="sxs-lookup"><span data-stu-id="289d9-133">On a per-user basis, you can add a `REG_DWORD` value named `useLegacyJit` to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key of the registry.</span></span> <span data-ttu-id="289d9-134">Hodnota 1 umožňuje starší 64bitový kompilátor JIT; hodnota 0 zakáže a povolí nový 64bitový kompilátor JIT.</span><span class="sxs-lookup"><span data-stu-id="289d9-134">A value of 1 enables the legacy 64-bit JIT compiler; a value of 0 disables it and enables the new 64-bit JIT compiler.</span></span>  
  
- <span data-ttu-id="289d9-135">Na základě pro počítač můžete přidat `REG_DWORD` hodnotu `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` pojmenovanou `useLegacyJit` do klíče registru.</span><span class="sxs-lookup"><span data-stu-id="289d9-135">On a per-machine basis, you can add a `REG_DWORD` value named `useLegacyJit` to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key of the registry.</span></span> <span data-ttu-id="289d9-136">Hodnota 1 umožňuje starší 64bitový kompilátor JIT; hodnota 0 zakáže a povolí nový 64bitový kompilátor JIT.</span><span class="sxs-lookup"><span data-stu-id="289d9-136">A value of 1 enables the legacy 64-bit JIT compiler; a value of 0 disables it and enables the new 64-bit JIT compiler.</span></span>  
  
 <span data-ttu-id="289d9-137">Můžete nám také dát vědět o problému nahlášením chyby na [Microsoft Connect](https://connect.microsoft.com/VisualStudio).</span><span class="sxs-lookup"><span data-stu-id="289d9-137">You can also let us know about the problem by reporting a bug on [Microsoft Connect](https://connect.microsoft.com/VisualStudio).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="289d9-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="289d9-138">See also</span></span>

- [<span data-ttu-id="289d9-139">Kompatibilita aplikací</span><span class="sxs-lookup"><span data-stu-id="289d9-139">Application compatibility</span></span>](application-compatibility.md)
- [<span data-ttu-id="289d9-140">\<useLegacyJit> Element</span><span class="sxs-lookup"><span data-stu-id="289d9-140">\<useLegacyJit> Element</span></span>](../configure-apps/file-schema/runtime/uselegacyjit-element.md)
