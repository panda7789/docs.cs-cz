---
title: 'Zmírnění: nový 64 kompilátor JIT'
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compiler, 64-bit
- JIT compilation, 64-bit
- RyuJIT compiler
ms.assetid: 0332dabc-72c5-4bdc-8975-20d717802b17
ms.openlocfilehash: dd8c2c6b3cfa919970f68f2faae2044568f6c9ac
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457914"
---
# <a name="mitigation-new-64-bit-jit-compiler"></a><span data-ttu-id="b7be2-102">Zmírnění: nový 64 kompilátor JIT</span><span class="sxs-lookup"><span data-stu-id="b7be2-102">Mitigation: New 64-bit JIT Compiler</span></span>
<span data-ttu-id="b7be2-103">Počínaje .NET Framework 4,6 obsahuje modul runtime nový 64 kompilátor JIT pro kompilaci za běhu.</span><span class="sxs-lookup"><span data-stu-id="b7be2-103">Starting with the .NET Framework 4.6, the runtime includes a new 64-bit JIT compiler for just-in-time compilation.</span></span> <span data-ttu-id="b7be2-104">Tato změna nemá vliv na kompilaci s 32 kompilátorem JIT.</span><span class="sxs-lookup"><span data-stu-id="b7be2-104">This change does not affect compilation with the  32-bit JIT compiler.</span></span>  
  
## <a name="unexpected-behavior-or-exceptions"></a><span data-ttu-id="b7be2-105">Neočekávané chování nebo výjimky</span><span class="sxs-lookup"><span data-stu-id="b7be2-105">Unexpected behavior or exceptions</span></span>  
 <span data-ttu-id="b7be2-106">V některých případech kompilace s novým 64 kompilátorem JIT má za následek výjimku za běhu nebo v chování, které není pozorováno při provádění kódu zkompilovaného starším 64 kompilátorem JIT.</span><span class="sxs-lookup"><span data-stu-id="b7be2-106">In some cases, compilation with the new 64-bit JIT compiler results in a runtime exception or in behavior that is not observed when executing code compiled by the older 64-bit JIT compiler.</span></span> <span data-ttu-id="b7be2-107">Mezi známé rozdíly patří následující:</span><span class="sxs-lookup"><span data-stu-id="b7be2-107">The known differences include the following:</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b7be2-108">Všechny tyto známé problémy byly vyřešeny v novém 64 kompilátoru, který byl vydán s .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="b7be2-108">All of these known issues have been addressed in the new 64-bit compiler released with the .NET Framework 4.6.2.</span></span> <span data-ttu-id="b7be2-109">K dispozici jsou také nejnovější verze .NET Framework 4,6 a 4.6.1, které jsou součástí web Windows Update.</span><span class="sxs-lookup"><span data-stu-id="b7be2-109">Most have also been addressed in service releases of the .NET Framework 4.6 and 4.6.1 that are included with Windows Update.</span></span> <span data-ttu-id="b7be2-110">Tyto problémy můžete eliminovat tím, že zajistíte aktuálnost vaší verze Windows nebo upgradem na .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="b7be2-110">You can eliminate these issues by ensuring that your version of Windows is up to date, or by upgrading to the .NET Framework 4.6.2.</span></span>  
  
- <span data-ttu-id="b7be2-111">Za určitých podmínek může rozbalení operace vyvolat <xref:System.NullReferenceException> v sestavení vydaných verzí s zapnutou optimalizací.</span><span class="sxs-lookup"><span data-stu-id="b7be2-111">Under certain conditions, an unboxing operation may throw a <xref:System.NullReferenceException> in Release builds with optimization turned on.</span></span>  
  
- <span data-ttu-id="b7be2-112">V některých případech může provádění produkčního kódu v těle velké metody vyvolat <xref:System.StackOverflowException>.</span><span class="sxs-lookup"><span data-stu-id="b7be2-112">In some cases, execution of production code in a large method body may throw a <xref:System.StackOverflowException>.</span></span>  
  
- <span data-ttu-id="b7be2-113">Za určitých podmínek se struktury předané metodě považují jako typy odkazů spíše než typy hodnot v sestaveních vydaných verzí.</span><span class="sxs-lookup"><span data-stu-id="b7be2-113">Under certain conditions, structures passed to a method are treated as reference types rather than value types in Release builds.</span></span> <span data-ttu-id="b7be2-114">Jedním z manifestů tohoto problému je, že jednotlivé položky v kolekci se zobrazí v neočekávaném pořadí.</span><span class="sxs-lookup"><span data-stu-id="b7be2-114">One of the manifestations of this issue is that the individual items in a collection appear in an unexpected order.</span></span>  
  
- <span data-ttu-id="b7be2-115">Za určitých podmínek je porovnání hodnot <xref:System.UInt16> s jejich vysokou bitovou sadou nesprávné, pokud je povolena optimalizace.</span><span class="sxs-lookup"><span data-stu-id="b7be2-115">Under certain conditions, the comparison of <xref:System.UInt16> values with their high bit set is incorrect if optimization is enabled.</span></span>  
  
- <span data-ttu-id="b7be2-116">Za určitých podmínek, zejména při inicializaci hodnot pole, může inicializace paměti pomocí instrukcí <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> IL inicializovat paměť s nesprávnou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="b7be2-116">Under certain conditions, particularly when initializing array values, memory initialization by the <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> IL instruction may initialize memory with an incorrect value.</span></span> <span data-ttu-id="b7be2-117">Výsledkem může být Neošetřená výjimka nebo nesprávný výstup.</span><span class="sxs-lookup"><span data-stu-id="b7be2-117">This can result either in an unhandled exception or incorrect output.</span></span>  
  
- <span data-ttu-id="b7be2-118">Za určitých vzácných podmínek může podmíněný bit test vracet nesprávnou <xref:System.Boolean> hodnotu nebo vyvolat výjimku, pokud jsou povoleny optimalizace kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="b7be2-118">Under certain rare conditions, a conditional bit test can return the incorrect <xref:System.Boolean> value or throw an exception if compiler optimizations are enabled.</span></span>  
  
- <span data-ttu-id="b7be2-119">Za určitých podmínek platí, že pokud se k otestování podmínky používá příkaz `if`, před vstupem do bloku `try` a při ukončení z bloku `try` se tato podmínka vyhodnocuje v `catch` nebo `finally` bloku. , nový 64 kompilátor JIT při optimalizaci kódu odstraní podmínku `if` z bloku `catch` nebo `finally`.</span><span class="sxs-lookup"><span data-stu-id="b7be2-119">Under certain conditions, if an `if` statement is used to test for a condition before entering  a `try` block and in the exit from the `try` block, and the same condition is evaluated in the `catch` or `finally` block, the new 64-bit JIT compiler removes the `if` condition from the `catch` or `finally` block when it optimizes code.</span></span> <span data-ttu-id="b7be2-120">V důsledku toho je kód v příkazu `if` v bloku `catch` nebo `finally` prováděn nepodmíněně.</span><span class="sxs-lookup"><span data-stu-id="b7be2-120">As a result, code inside the `if` statement in the `catch` or `finally` block is executed unconditionally.</span></span>  
  
<a name="General"></a>   
## <a name="mitigation-of-known-issues"></a><span data-ttu-id="b7be2-121">Zmírnění známých problémů</span><span class="sxs-lookup"><span data-stu-id="b7be2-121">Mitigation of known issues</span></span>  
 <span data-ttu-id="b7be2-122">Pokud narazíte na výše uvedené problémy, můžete je vyřešit provedením následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="b7be2-122">If you encounter the issues listed above, you can address them by doing any of the following:</span></span>  
  
- <span data-ttu-id="b7be2-123">Upgradujte na .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="b7be2-123">Upgrade to the .NET Framework 4.6.2.</span></span> <span data-ttu-id="b7be2-124">Nový 64 kompilátor zahrnutý do .NET Framework 4.6.2 řeší všechny tyto známé problémy.</span><span class="sxs-lookup"><span data-stu-id="b7be2-124">The new 64-bit compiler included with the .NET Framework 4.6.2 addresses each of these known issues.</span></span>  
  
- <span data-ttu-id="b7be2-125">Zajistěte, aby byla verze Windows aktuální, a to spuštěním web Windows Update.</span><span class="sxs-lookup"><span data-stu-id="b7be2-125">Ensure that your version of Windows is up to date by running Windows Update.</span></span> <span data-ttu-id="b7be2-126">Aktualizace služby .NET Framework 4,6 a 4.6.1 řeší každý z těchto problémů s výjimkou <xref:System.NullReferenceException> v operaci rozbalení.</span><span class="sxs-lookup"><span data-stu-id="b7be2-126">Service updates to the .NET Framework 4.6 and 4.6.1 address each of these issues except the <xref:System.NullReferenceException> in an unboxing operation.</span></span>  
  
- <span data-ttu-id="b7be2-127">Zkompiluje se starším 64 kompilátorem JIT.</span><span class="sxs-lookup"><span data-stu-id="b7be2-127">Compile with the older 64-bit JIT compiler.</span></span> <span data-ttu-id="b7be2-128">Další informace o tom, jak to udělat, najdete v části [zmírnění problémů s dalšími problémy](#Other) .</span><span class="sxs-lookup"><span data-stu-id="b7be2-128">See the [Mitigation of other issues](#Other) section for more information on how to do this.</span></span>  
  
<a name="Other"></a>   
## <a name="mitigation-of-other-issues"></a><span data-ttu-id="b7be2-129">Zmírnění jiných problémů</span><span class="sxs-lookup"><span data-stu-id="b7be2-129">Mitigation of other issues</span></span>  
 <span data-ttu-id="b7be2-130">Pokud narazíte na jiné rozdíly v chování mezi kódem kompilovaným se starším 64 kompilátorem a novým 64 kompilátorem JIT, nebo mezi verzemi ladění a vydání vaší aplikace, které jsou zkompilovány pomocí nového 64-bitového kompilátoru JIT, můžete provést následující akce: pro zkompilování aplikace se starším 64 kompilátorem JIT:</span><span class="sxs-lookup"><span data-stu-id="b7be2-130">If you encounter any other difference in behavior between code compiled with the older 64-bit compiler and the new 64-bit JIT compiler, or between the debug and release versions of your app that are both compiled with the new 64-bit JIT compiler, you can do the following to compile your app with the older 64-bit JIT compiler:</span></span>  
  
- <span data-ttu-id="b7be2-131">Na základě jednotlivých aplikací můžete do konfiguračního souboru aplikace přidat [\<useLegacyJit >](../configure-apps/file-schema/runtime/uselegacyjit-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="b7be2-131">On a per-application basis, you can add the [\<useLegacyJit>](../configure-apps/file-schema/runtime/uselegacyjit-element.md) element to your application's configuration file.</span></span> <span data-ttu-id="b7be2-132">Následující zakáže kompilaci s novým 64 kompilátorem JIT a místo toho používá starší 64 kompilátor JIT.</span><span class="sxs-lookup"><span data-stu-id="b7be2-132">The following disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
    ```xml  
    <?xml version ="1.0"?>  
    <configuration>  
        <runtime>  
           <useLegacyJit enabled="1" />  
        </runtime>  
    </configuration>  
    ```  
  
- <span data-ttu-id="b7be2-133">Na základě jednotlivých uživatelů můžete do `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` klíče registru přidat `REG_DWORD`ovou hodnotu s názvem `useLegacyJit`.</span><span class="sxs-lookup"><span data-stu-id="b7be2-133">On a per-user basis, you can add a `REG_DWORD` value named `useLegacyJit` to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key of the registry.</span></span> <span data-ttu-id="b7be2-134">Hodnota 1 povolí starší 64 kompilátor JIT; hodnota 0 ji zakáže a povolí nový 64 kompilátor JIT.</span><span class="sxs-lookup"><span data-stu-id="b7be2-134">A value of 1 enables the legacy 64-bit JIT compiler; a value of 0 disables it and enables the new 64-bit JIT compiler.</span></span>  
  
- <span data-ttu-id="b7be2-135">Na základě jednotlivých počítačů můžete do `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` klíče registru přidat `REG_DWORD`ovou hodnotu s názvem `useLegacyJit`.</span><span class="sxs-lookup"><span data-stu-id="b7be2-135">On a per-machine basis, you can add a `REG_DWORD` value named `useLegacyJit` to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key of the registry.</span></span> <span data-ttu-id="b7be2-136">Hodnota 1 povolí starší 64 kompilátor JIT; hodnota 0 ji zakáže a povolí nový 64 kompilátor JIT.</span><span class="sxs-lookup"><span data-stu-id="b7be2-136">A value of 1 enables the legacy 64-bit JIT compiler; a value of 0 disables it and enables the new 64-bit JIT compiler.</span></span>  
  
 <span data-ttu-id="b7be2-137">Můžete nám taky informovat o problému tím, že nahlásíte chybu na [Microsoft Connect](https://connect.microsoft.com/VisualStudio).</span><span class="sxs-lookup"><span data-stu-id="b7be2-137">You can also let us know about the problem by reporting a bug on [Microsoft Connect](https://connect.microsoft.com/VisualStudio).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7be2-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b7be2-138">See also</span></span>

- [<span data-ttu-id="b7be2-139">Kompatibilita aplikací</span><span class="sxs-lookup"><span data-stu-id="b7be2-139">Application compatibility</span></span>](application-compatibility.md)
- [<span data-ttu-id="b7be2-140">\<element > useLegacyJit</span><span class="sxs-lookup"><span data-stu-id="b7be2-140">\<useLegacyJit> Element</span></span>](../configure-apps/file-schema/runtime/uselegacyjit-element.md)
