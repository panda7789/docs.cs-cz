---
title: Zmírnění Nový 64 kompilátor JIT
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compiler, 64-bit
- JIT compilation, 64-bit
- RyuJIT compiler
ms.assetid: 0332dabc-72c5-4bdc-8975-20d717802b17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6df750872e90572b00cdf427461b4a9782c47d63
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968524"
---
# <a name="mitigation-new-64-bit-jit-compiler"></a><span data-ttu-id="6105c-102">Zmírnění Nový 64 kompilátor JIT</span><span class="sxs-lookup"><span data-stu-id="6105c-102">Mitigation: New 64-bit JIT Compiler</span></span>
<span data-ttu-id="6105c-103">Počínaje .NET Framework 4,6 obsahuje modul runtime nový 64 kompilátor JIT pro kompilaci za běhu.</span><span class="sxs-lookup"><span data-stu-id="6105c-103">Starting with the .NET Framework 4.6, the runtime includes a new 64-bit JIT compiler for just-in-time compilation.</span></span> <span data-ttu-id="6105c-104">Tato změna nemá vliv na kompilaci s 32 kompilátorem JIT.</span><span class="sxs-lookup"><span data-stu-id="6105c-104">This change does not affect compilation with the  32-bit JIT compiler.</span></span>  
  
## <a name="unexpected-behavior-or-exceptions"></a><span data-ttu-id="6105c-105">Neočekávané chování nebo výjimky</span><span class="sxs-lookup"><span data-stu-id="6105c-105">Unexpected behavior or exceptions</span></span>  
 <span data-ttu-id="6105c-106">V některých případech kompilace s novým 64 kompilátorem JIT má za následek výjimku za běhu nebo v chování, které není pozorováno při provádění kódu zkompilovaného starším 64 kompilátorem JIT.</span><span class="sxs-lookup"><span data-stu-id="6105c-106">In some cases, compilation with the new 64-bit JIT compiler results in a runtime exception or in behavior that is not observed when executing code compiled by the older 64-bit JIT compiler.</span></span> <span data-ttu-id="6105c-107">Mezi známé rozdíly patří následující:</span><span class="sxs-lookup"><span data-stu-id="6105c-107">The known differences include the following:</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6105c-108">Všechny tyto známé problémy byly vyřešeny v novém 64 kompilátoru, který byl vydán s .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="6105c-108">All of these known issues have been addressed in the new 64-bit compiler released with the .NET Framework 4.6.2.</span></span> <span data-ttu-id="6105c-109">K dispozici jsou také nejnovější verze .NET Framework 4,6 a 4.6.1, které jsou součástí web Windows Update.</span><span class="sxs-lookup"><span data-stu-id="6105c-109">Most have also been addressed in service releases of the .NET Framework 4.6 and 4.6.1 that are included with Windows Update.</span></span> <span data-ttu-id="6105c-110">Tyto problémy můžete eliminovat tím, že zajistíte aktuálnost vaší verze Windows nebo upgradem na .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="6105c-110">You can eliminate these issues by ensuring that your version of Windows is up to date, or by upgrading to the .NET Framework 4.6.2.</span></span>  
  
- <span data-ttu-id="6105c-111">Za určitých podmínek může rozbalení operace vyvolat v sestavení vydaných <xref:System.NullReferenceException> verzí s zapnutou optimalizací.</span><span class="sxs-lookup"><span data-stu-id="6105c-111">Under certain conditions, an unboxing operation may throw a <xref:System.NullReferenceException> in Release builds with optimization turned on.</span></span>  
  
- <span data-ttu-id="6105c-112">V některých případech může provedení produkčního kódu v těle metody vyvolat výjimku <xref:System.StackOverflowException>.</span><span class="sxs-lookup"><span data-stu-id="6105c-112">In some cases, execution of production code in a large method body may throw a <xref:System.StackOverflowException>.</span></span>  
  
- <span data-ttu-id="6105c-113">Za určitých podmínek se struktury předané metodě považují jako typy odkazů spíše než typy hodnot v sestaveních vydaných verzí.</span><span class="sxs-lookup"><span data-stu-id="6105c-113">Under certain conditions, structures passed to a method are treated as reference types rather than value types in Release builds.</span></span> <span data-ttu-id="6105c-114">Jedním z manifestů tohoto problému je, že jednotlivé položky v kolekci se zobrazí v neočekávaném pořadí.</span><span class="sxs-lookup"><span data-stu-id="6105c-114">One of the manifestations of this issue is that the individual items in a collection appear in an unexpected order.</span></span>  
  
- <span data-ttu-id="6105c-115">Za určitých podmínek je porovnání <xref:System.UInt16> hodnot s jejich vysokou bitovou sadou nesprávné, pokud je povolena optimalizace.</span><span class="sxs-lookup"><span data-stu-id="6105c-115">Under certain conditions, the comparison of <xref:System.UInt16> values with their high bit set is incorrect if optimization is enabled.</span></span>  
  
- <span data-ttu-id="6105c-116">Za určitých podmínek, zejména při inicializaci hodnot pole, může inicializace paměti pomocí <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> instrukcí Il inicializovat paměť s nesprávnou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="6105c-116">Under certain conditions, particularly when initializing array values, memory initialization by the <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> IL instruction may initialize memory with an incorrect value.</span></span> <span data-ttu-id="6105c-117">Výsledkem může být Neošetřená výjimka nebo nesprávný výstup.</span><span class="sxs-lookup"><span data-stu-id="6105c-117">This can result either in an unhandled exception or incorrect output.</span></span>  
  
- <span data-ttu-id="6105c-118">Za určitých vzácných podmínek může podmíněný bit test vracet nesprávnou <xref:System.Boolean> hodnotu nebo vyvolat výjimku, pokud jsou povoleny optimalizace kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="6105c-118">Under certain rare conditions, a conditional bit test can return the incorrect <xref:System.Boolean> value or throw an exception if compiler optimizations are enabled.</span></span>  
  
- <span data-ttu-id="6105c-119">Za určitých podmínek platí, že `if` Pokud je příkaz použit k otestování podmínky před vstupem `try` do bloku a `try` v ukončení z bloku `catch` a stejná podmínka je vyhodnocena v bloku nebo `finally` , nový 64 kompilátor JIT při optimalizaci kódu odstraní `if` podmínku `catch` z bloku nebo `finally` .</span><span class="sxs-lookup"><span data-stu-id="6105c-119">Under certain conditions, if an `if` statement is used to test for a condition before entering  a `try` block and in the exit from the `try` block, and the same condition is evaluated in the `catch` or `finally` block, the new 64-bit JIT compiler removes the `if` condition from the `catch` or `finally` block when it optimizes code.</span></span> <span data-ttu-id="6105c-120">V důsledku toho je kód uvnitř `if` příkazu v bloku `finally`neboproveden nepodmíněným způsobem. `catch`</span><span class="sxs-lookup"><span data-stu-id="6105c-120">As a result, code inside the `if` statement in the `catch` or `finally` block is executed unconditionally.</span></span>  
  
<a name="General"></a>   
## <a name="mitigation-of-known-issues"></a><span data-ttu-id="6105c-121">Zmírnění známých problémů</span><span class="sxs-lookup"><span data-stu-id="6105c-121">Mitigation of known issues</span></span>  
 <span data-ttu-id="6105c-122">Pokud narazíte na výše uvedené problémy, můžete je vyřešit provedením následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="6105c-122">If you encounter the issues listed above, you can address them by doing any of the following:</span></span>  
  
- <span data-ttu-id="6105c-123">Upgradujte na .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="6105c-123">Upgrade to the .NET Framework 4.6.2.</span></span> <span data-ttu-id="6105c-124">Nový 64 kompilátor zahrnutý do .NET Framework 4.6.2 řeší všechny tyto známé problémy.</span><span class="sxs-lookup"><span data-stu-id="6105c-124">The new 64-bit compiler included with the .NET Framework 4.6.2 addresses each of these known issues.</span></span>  
  
- <span data-ttu-id="6105c-125">Zajistěte, aby byla verze Windows aktuální, a to spuštěním web Windows Update.</span><span class="sxs-lookup"><span data-stu-id="6105c-125">Ensure that your version of Windows is up to date by running Windows Update.</span></span> <span data-ttu-id="6105c-126">Aktualizace služby .NET Framework 4,6 a 4.6.1 řeší každý z těchto problémů s výjimkou <xref:System.NullReferenceException> operace rozbalení.</span><span class="sxs-lookup"><span data-stu-id="6105c-126">Service updates to the .NET Framework 4.6 and 4.6.1 address each of these issues except the <xref:System.NullReferenceException> in an unboxing operation.</span></span>  
  
- <span data-ttu-id="6105c-127">Zkompiluje se starším 64 kompilátorem JIT.</span><span class="sxs-lookup"><span data-stu-id="6105c-127">Compile with the older 64-bit JIT compiler.</span></span> <span data-ttu-id="6105c-128">Další informace o tom, jak to udělat, najdete v části [zmírnění problémů s dalšími problémy](#Other) .</span><span class="sxs-lookup"><span data-stu-id="6105c-128">See the [Mitigation of other issues](#Other) section for more information on how to do this.</span></span>  
  
<a name="Other"></a>   
## <a name="mitigation-of-other-issues"></a><span data-ttu-id="6105c-129">Zmírnění jiných problémů</span><span class="sxs-lookup"><span data-stu-id="6105c-129">Mitigation of other issues</span></span>  
 <span data-ttu-id="6105c-130">Pokud narazíte na jiné rozdíly v chování mezi kódem kompilovaným se starším 64 kompilátorem a novým 64 kompilátorem JIT, nebo mezi verzemi ladění a vydání vaší aplikace, které jsou zkompilovány pomocí nového 64-bitového kompilátoru JIT, můžete provést následující akce: pro zkompilování aplikace se starším 64 kompilátorem JIT:</span><span class="sxs-lookup"><span data-stu-id="6105c-130">If you encounter any other difference in behavior between code compiled with the older 64-bit compiler and the new 64-bit JIT compiler, or between the debug and release versions of your app that are both compiled with the new 64-bit JIT compiler, you can do the following to compile your app with the older 64-bit JIT compiler:</span></span>  
  
- <span data-ttu-id="6105c-131">Na základě jednotlivých aplikací můžete přidat [ \<prvek useLegacyJit >](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md) do konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="6105c-131">On a per-application basis, you can add the [\<useLegacyJit>](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md) element to your application's configuration file.</span></span> <span data-ttu-id="6105c-132">Následující zakáže kompilaci s novým 64 kompilátorem JIT a místo toho používá starší 64 kompilátor JIT.</span><span class="sxs-lookup"><span data-stu-id="6105c-132">The following disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
    ```xml  
    <?xml version ="1.0"?>  
    <configuration>  
        <runtime>  
           <useLegacyJit enabled="1" />  
        </runtime>  
    </configuration>  
    ```  
  
- <span data-ttu-id="6105c-133">Na základě jednotlivých uživatelů můžete do `REG_DWORD` `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` klíče registru přidat hodnotu s názvem `useLegacyJit` .</span><span class="sxs-lookup"><span data-stu-id="6105c-133">On a per-user basis, you can add a `REG_DWORD` value named `useLegacyJit` to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key of the registry.</span></span> <span data-ttu-id="6105c-134">Hodnota 1 povolí starší 64 kompilátor JIT; hodnota 0 ji zakáže a povolí nový 64 kompilátor JIT.</span><span class="sxs-lookup"><span data-stu-id="6105c-134">A value of 1 enables the legacy 64-bit JIT compiler; a value of 0 disables it and enables the new 64-bit JIT compiler.</span></span>  
  
- <span data-ttu-id="6105c-135">Na základě jednotlivých počítačů můžete do `REG_DWORD` `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` klíče registru přidat hodnotu s názvem `useLegacyJit` .</span><span class="sxs-lookup"><span data-stu-id="6105c-135">On a per-machine basis, you can add a `REG_DWORD` value named `useLegacyJit` to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key of the registry.</span></span> <span data-ttu-id="6105c-136">Hodnota 1 povolí starší 64 kompilátor JIT; hodnota 0 ji zakáže a povolí nový 64 kompilátor JIT.</span><span class="sxs-lookup"><span data-stu-id="6105c-136">A value of 1 enables the legacy 64-bit JIT compiler; a value of 0 disables it and enables the new 64-bit JIT compiler.</span></span>  
  
 <span data-ttu-id="6105c-137">Můžete nám taky informovat o problému tím, že nahlásíte chybu na [Microsoft Connect](https://connect.microsoft.com/VisualStudio).</span><span class="sxs-lookup"><span data-stu-id="6105c-137">You can also let us know about the problem by reporting a bug on [Microsoft Connect](https://connect.microsoft.com/VisualStudio).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6105c-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6105c-138">See also</span></span>

- [<span data-ttu-id="6105c-139">Změny v modulu runtime</span><span class="sxs-lookup"><span data-stu-id="6105c-139">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
- [<span data-ttu-id="6105c-140">\<useLegacyJit> Element</span><span class="sxs-lookup"><span data-stu-id="6105c-140">\<useLegacyJit> Element</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md)
