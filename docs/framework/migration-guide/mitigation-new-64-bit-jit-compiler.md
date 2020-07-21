---
title: 'Zmírnění: nový 64 kompilátor JIT'
description: Seznamte se s novým 64 kompilátorem JIT, který je součástí .NET Framework 4,6 a neočekávané chování nebo výjimky, které mohou nastat během kompilace.
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compiler, 64-bit
- JIT compilation, 64-bit
- RyuJIT compiler
ms.assetid: 0332dabc-72c5-4bdc-8975-20d717802b17
ms.openlocfilehash: f059cbdd3b2a66ac8a668b7b8a80d9ad1551fa64
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475226"
---
# <a name="mitigation-new-64-bit-jit-compiler"></a><span data-ttu-id="e471e-103">Zmírnění: nový 64 kompilátor JIT</span><span class="sxs-lookup"><span data-stu-id="e471e-103">Mitigation: New 64-bit JIT Compiler</span></span>
<span data-ttu-id="e471e-104">Počínaje .NET Framework 4,6 obsahuje modul runtime nový 64 kompilátor JIT pro kompilaci za běhu.</span><span class="sxs-lookup"><span data-stu-id="e471e-104">Starting with .NET Framework 4.6, the runtime includes a new 64-bit JIT compiler for just-in-time compilation.</span></span> <span data-ttu-id="e471e-105">Tato změna nemá vliv na kompilaci s 32 kompilátorem JIT.</span><span class="sxs-lookup"><span data-stu-id="e471e-105">This change does not affect compilation with the 32-bit JIT compiler.</span></span>  
  
## <a name="unexpected-behavior-or-exceptions"></a><span data-ttu-id="e471e-106">Neočekávané chování nebo výjimky</span><span class="sxs-lookup"><span data-stu-id="e471e-106">Unexpected behavior or exceptions</span></span>  
 <span data-ttu-id="e471e-107">V některých případech kompilace s novým 64 kompilátorem JIT má za následek výjimku za běhu nebo v chování, které není pozorováno při provádění kódu zkompilovaného starším 64 kompilátorem JIT.</span><span class="sxs-lookup"><span data-stu-id="e471e-107">In some cases, compilation with the new 64-bit JIT compiler results in a runtime exception or in behavior that is not observed when executing code compiled by the older 64-bit JIT compiler.</span></span> <span data-ttu-id="e471e-108">Mezi známé rozdíly patří následující:</span><span class="sxs-lookup"><span data-stu-id="e471e-108">The known differences include the following:</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e471e-109">Všechny tyto známé problémy byly vyřešeny v novém 64 kompilátoru, který byl vydán s .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="e471e-109">All of these known issues have been addressed in the new 64-bit compiler released with the .NET Framework 4.6.2.</span></span> <span data-ttu-id="e471e-110">K dispozici jsou také nejnovější verze .NET Framework 4,6 a 4.6.1, které jsou součástí web Windows Update.</span><span class="sxs-lookup"><span data-stu-id="e471e-110">Most have also been addressed in service releases of the .NET Framework 4.6 and 4.6.1 that are included with Windows Update.</span></span> <span data-ttu-id="e471e-111">Tyto problémy můžete eliminovat tím, že zajistíte aktuálnost vaší verze Windows nebo upgradem na .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="e471e-111">You can eliminate these issues by ensuring that your version of Windows is up to date, or by upgrading to the .NET Framework 4.6.2.</span></span>  
  
- <span data-ttu-id="e471e-112">Za určitých podmínek může rozbalení operace vyvolat v sestavení vydaných <xref:System.NullReferenceException> verzí s zapnutou optimalizací.</span><span class="sxs-lookup"><span data-stu-id="e471e-112">Under certain conditions, an unboxing operation may throw a <xref:System.NullReferenceException> in Release builds with optimization turned on.</span></span>  
  
- <span data-ttu-id="e471e-113">V některých případech může provedení produkčního kódu v těle metody vyvolat výjimku <xref:System.StackOverflowException> .</span><span class="sxs-lookup"><span data-stu-id="e471e-113">In some cases, execution of production code in a large method body may throw a <xref:System.StackOverflowException>.</span></span>  
  
- <span data-ttu-id="e471e-114">Za určitých podmínek se struktury předané metodě považují jako typy odkazů spíše než typy hodnot v sestaveních vydaných verzí.</span><span class="sxs-lookup"><span data-stu-id="e471e-114">Under certain conditions, structures passed to a method are treated as reference types rather than value types in Release builds.</span></span> <span data-ttu-id="e471e-115">Jedním z manifestů tohoto problému je, že jednotlivé položky v kolekci se zobrazí v neočekávaném pořadí.</span><span class="sxs-lookup"><span data-stu-id="e471e-115">One of the manifestations of this issue is that the individual items in a collection appear in an unexpected order.</span></span>  
  
- <span data-ttu-id="e471e-116">Za určitých podmínek <xref:System.UInt16> je porovnání hodnot s jejich vysokou bitovou sadou nesprávné, pokud je povolena optimalizace.</span><span class="sxs-lookup"><span data-stu-id="e471e-116">Under certain conditions, the comparison of <xref:System.UInt16> values with their high bit set is incorrect if optimization is enabled.</span></span>  
  
- <span data-ttu-id="e471e-117">Za určitých podmínek, zejména při inicializaci hodnot pole, může inicializace paměti pomocí <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> instrukcí Il inicializovat paměť s nesprávnou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="e471e-117">Under certain conditions, particularly when initializing array values, memory initialization by the <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> IL instruction may initialize memory with an incorrect value.</span></span> <span data-ttu-id="e471e-118">Výsledkem může být Neošetřená výjimka nebo nesprávný výstup.</span><span class="sxs-lookup"><span data-stu-id="e471e-118">This can result either in an unhandled exception or incorrect output.</span></span>  
  
- <span data-ttu-id="e471e-119">Za určitých vzácných podmínek může podmíněný bit test vracet nesprávnou <xref:System.Boolean> hodnotu nebo vyvolat výjimku, pokud jsou povoleny optimalizace kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="e471e-119">Under certain rare conditions, a conditional bit test can return the incorrect <xref:System.Boolean> value or throw an exception if compiler optimizations are enabled.</span></span>  
  
- <span data-ttu-id="e471e-120">Za určitých podmínek platí, že pokud `if` je příkaz použit k otestování podmínky před vstupem do `try` bloku a do ukončení z `try` bloku a stejná podmínka je vyhodnocena v `catch` bloku nebo `finally` , nový 64 kompilátor JIT `if` `catch` `finally` při optimalizaci kódu odstraní podmínku z bloku nebo.</span><span class="sxs-lookup"><span data-stu-id="e471e-120">Under certain conditions, if an `if` statement is used to test for a condition before entering  a `try` block and in the exit from the `try` block, and the same condition is evaluated in the `catch` or `finally` block, the new 64-bit JIT compiler removes the `if` condition from the `catch` or `finally` block when it optimizes code.</span></span> <span data-ttu-id="e471e-121">V důsledku toho je kód uvnitř `if` příkazu v `catch` `finally` bloku nebo proveden nepodmíněným způsobem.</span><span class="sxs-lookup"><span data-stu-id="e471e-121">As a result, code inside the `if` statement in the `catch` or `finally` block is executed unconditionally.</span></span>  
  
<a name="General"></a>
## <a name="mitigation-of-known-issues"></a><span data-ttu-id="e471e-122">Zmírnění známých problémů</span><span class="sxs-lookup"><span data-stu-id="e471e-122">Mitigation of known issues</span></span>  
 <span data-ttu-id="e471e-123">Pokud narazíte na výše uvedené problémy, můžete je vyřešit provedením následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="e471e-123">If you encounter the issues listed above, you can address them by doing any of the following:</span></span>  
  
- <span data-ttu-id="e471e-124">Upgradujte na .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="e471e-124">Upgrade to the .NET Framework 4.6.2.</span></span> <span data-ttu-id="e471e-125">Nový 64 kompilátor zahrnutý do .NET Framework 4.6.2 řeší všechny tyto známé problémy.</span><span class="sxs-lookup"><span data-stu-id="e471e-125">The new 64-bit compiler included with the .NET Framework 4.6.2 addresses each of these known issues.</span></span>  
  
- <span data-ttu-id="e471e-126">Zajistěte, aby byla verze Windows aktuální, a to spuštěním web Windows Update.</span><span class="sxs-lookup"><span data-stu-id="e471e-126">Ensure that your version of Windows is up to date by running Windows Update.</span></span> <span data-ttu-id="e471e-127">Aktualizace služby .NET Framework 4,6 a 4.6.1 řeší každý z těchto problémů s výjimkou <xref:System.NullReferenceException> operace rozbalení.</span><span class="sxs-lookup"><span data-stu-id="e471e-127">Service updates to the .NET Framework 4.6 and 4.6.1 address each of these issues except the <xref:System.NullReferenceException> in an unboxing operation.</span></span>  
  
- <span data-ttu-id="e471e-128">Zkompiluje se starším 64 kompilátorem JIT.</span><span class="sxs-lookup"><span data-stu-id="e471e-128">Compile with the older 64-bit JIT compiler.</span></span> <span data-ttu-id="e471e-129">Další informace o tom, jak to udělat, najdete v části [zmírnění problémů s dalšími problémy](#Other) .</span><span class="sxs-lookup"><span data-stu-id="e471e-129">See the [Mitigation of other issues](#Other) section for more information on how to do this.</span></span>  
  
<a name="Other"></a>
## <a name="mitigation-of-other-issues"></a><span data-ttu-id="e471e-130">Zmírnění jiných problémů</span><span class="sxs-lookup"><span data-stu-id="e471e-130">Mitigation of other issues</span></span>  
 <span data-ttu-id="e471e-131">Pokud narazíte na jiné rozdíly v chování mezi kódem kompilovaným se starším 64 kompilátorem a novým 64 kompilátorem JIT, nebo mezi verzemi ladění a vydání vaší aplikace, které jsou zkompilovány pomocí nového 64-bitového kompilátoru JIT, můžete provést následující postup pro zkompilování aplikace se 64 starším 32bitovým kompilátorem JIT. :</span><span class="sxs-lookup"><span data-stu-id="e471e-131">If you encounter any other difference in behavior between code compiled with the older 64-bit compiler and the new 64-bit JIT compiler, or between the debug and release versions of your app that are both compiled with the new 64-bit JIT compiler, you can do the following to compile your app with the older 64-bit JIT compiler:</span></span>  
  
- <span data-ttu-id="e471e-132">Na základě jednotlivých aplikací můžete přidat [\<useLegacyJit>](../configure-apps/file-schema/runtime/uselegacyjit-element.md) prvek do konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="e471e-132">On a per-application basis, you can add the [\<useLegacyJit>](../configure-apps/file-schema/runtime/uselegacyjit-element.md) element to your application's configuration file.</span></span> <span data-ttu-id="e471e-133">Následující zakáže kompilaci s novým 64 kompilátorem JIT a místo toho používá starší 64 kompilátor JIT.</span><span class="sxs-lookup"><span data-stu-id="e471e-133">The following disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
    ```xml  
    <?xml version ="1.0"?>  
    <configuration>  
        <runtime>  
           <useLegacyJit enabled="1" />  
        </runtime>  
    </configuration>  
    ```  
  
- <span data-ttu-id="e471e-134">Na základě jednotlivých uživatelů můžete do `REG_DWORD` klíče registru přidat hodnotu s názvem `useLegacyJit` `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` .</span><span class="sxs-lookup"><span data-stu-id="e471e-134">On a per-user basis, you can add a `REG_DWORD` value named `useLegacyJit` to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key of the registry.</span></span> <span data-ttu-id="e471e-135">Hodnota 1 povolí starší 64 kompilátor JIT; hodnota 0 ji zakáže a povolí nový 64 kompilátor JIT.</span><span class="sxs-lookup"><span data-stu-id="e471e-135">A value of 1 enables the legacy 64-bit JIT compiler; a value of 0 disables it and enables the new 64-bit JIT compiler.</span></span>  
  
- <span data-ttu-id="e471e-136">Na základě jednotlivých počítačů můžete do `REG_DWORD` klíče registru přidat hodnotu s názvem `useLegacyJit` `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` .</span><span class="sxs-lookup"><span data-stu-id="e471e-136">On a per-machine basis, you can add a `REG_DWORD` value named `useLegacyJit` to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key of the registry.</span></span> <span data-ttu-id="e471e-137">Hodnota 1 povolí starší 64 kompilátor JIT; hodnota 0 ji zakáže a povolí nový 64 kompilátor JIT.</span><span class="sxs-lookup"><span data-stu-id="e471e-137">A value of 1 enables the legacy 64-bit JIT compiler; a value of 0 disables it and enables the new 64-bit JIT compiler.</span></span>  
  
 <span data-ttu-id="e471e-138">Můžete nám taky informovat o problému tím, že nahlásíte chybu na [Microsoft Connect](https://connect.microsoft.com/VisualStudio).</span><span class="sxs-lookup"><span data-stu-id="e471e-138">You can also let us know about the problem by reporting a bug on [Microsoft Connect](https://connect.microsoft.com/VisualStudio).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e471e-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="e471e-139">See also</span></span>

- [<span data-ttu-id="e471e-140">Kompatibilita aplikací</span><span class="sxs-lookup"><span data-stu-id="e471e-140">Application compatibility</span></span>](application-compatibility.md)
- [<span data-ttu-id="e471e-141">\<useLegacyJit>Objekt</span><span class="sxs-lookup"><span data-stu-id="e471e-141">\<useLegacyJit> Element</span></span>](../configure-apps/file-schema/runtime/uselegacyjit-element.md)
