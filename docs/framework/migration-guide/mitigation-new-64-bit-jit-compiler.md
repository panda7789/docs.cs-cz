---
title: 'Omezení rizik: Nový kompilátor JIT 64-bit'
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compiler, 64-bit
- JIT compilation, 64-bit
- RyuJIT compiler
ms.assetid: 0332dabc-72c5-4bdc-8975-20d717802b17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f3177ae53d8b932a52dccf11b12d44fd07ec1c4f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61871459"
---
# <a name="mitigation-new-64-bit-jit-compiler"></a><span data-ttu-id="19a97-102">Omezení rizik: Nový kompilátor JIT 64-bit</span><span class="sxs-lookup"><span data-stu-id="19a97-102">Mitigation: New 64-bit JIT Compiler</span></span>
<span data-ttu-id="19a97-103">Od verze rozhraní .NET Framework 4.6, modul runtime obsahuje nové 64-bit kompilátor JIT kompilace just-in-time.</span><span class="sxs-lookup"><span data-stu-id="19a97-103">Starting with the .NET Framework 4.6, the runtime includes a new 64-bit JIT compiler for just-in-time compilation.</span></span> <span data-ttu-id="19a97-104">Tato změna neovlivní kompilace s kompilátorem JIT 32-bit.</span><span class="sxs-lookup"><span data-stu-id="19a97-104">This change does not affect compilation with the  32-bit JIT compiler.</span></span>  
  
## <a name="unexpected-behavior-or-exceptions"></a><span data-ttu-id="19a97-105">Neočekávané chování nebo výjimky</span><span class="sxs-lookup"><span data-stu-id="19a97-105">Unexpected behavior or exceptions</span></span>  
 <span data-ttu-id="19a97-106">V některých případech se výsledky kompilace pomocí nového 64bitového kompilátoru JIT v výjimku při běhu nebo chování, které není dodržena při provádění kódu, které jsou kompilovány pomocí kompilátoru JIT starší 64-bit.</span><span class="sxs-lookup"><span data-stu-id="19a97-106">In some cases, compilation with the new 64-bit JIT compiler results in a runtime exception or in behavior that is not observed when executing code compiled by the older 64-bit JIT compiler.</span></span> <span data-ttu-id="19a97-107">Známé rozdíly patří následující:</span><span class="sxs-lookup"><span data-stu-id="19a97-107">The known differences include the following:</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="19a97-108">Vyřeší všechny tyto známé problémy v nového 64bitového kompilátoru vydané s použitím rozhraní .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="19a97-108">All of these known issues have been addressed in the new 64-bit compiler released with the .NET Framework 4.6.2.</span></span> <span data-ttu-id="19a97-109">Většina také vyřeší služba verze rozhraní .NET Framework 4.6 a 4.6.1, které jsou součástí Windows Update.</span><span class="sxs-lookup"><span data-stu-id="19a97-109">Most have also been addressed in service releases of the .NET Framework 4.6 and 4.6.1 that are included with Windows Update.</span></span> <span data-ttu-id="19a97-110">Můžete vyloučit tyto problémy tím, že zajišťuje, které vaši verzi systému Windows je aktuální, nebo po upgradu na rozhraní .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="19a97-110">You can eliminate these issues by ensuring that your version of Windows is up to date, or by upgrading to the .NET Framework 4.6.2.</span></span>  
  
- <span data-ttu-id="19a97-111">Za určitých podmínek může vyvolat operace rozbalení <xref:System.NullReferenceException> v sestaveních pro vydání s optimalizací zapnuté.</span><span class="sxs-lookup"><span data-stu-id="19a97-111">Under certain conditions, an unboxing operation may throw a <xref:System.NullReferenceException> in Release builds with optimization turned on.</span></span>  
  
- <span data-ttu-id="19a97-112">V některých případech se může vyvolat provádění kódu v těle metody velké <xref:System.StackOverflowException>.</span><span class="sxs-lookup"><span data-stu-id="19a97-112">In some cases, execution of production code in a large method body may throw a <xref:System.StackOverflowException>.</span></span>  
  
- <span data-ttu-id="19a97-113">Za určitých podmínek struktury předáno metodě, jsou považovány za typy odkazů spíše než typy hodnot ve verzi sestavení.</span><span class="sxs-lookup"><span data-stu-id="19a97-113">Under certain conditions, structures passed to a method are treated as reference types rather than value types in Release builds.</span></span> <span data-ttu-id="19a97-114">Jedním z projevy tento problém je, že jednotlivé položky v kolekci se zobrazí v neočekávaném pořadí.</span><span class="sxs-lookup"><span data-stu-id="19a97-114">One of the manifestations of this issue is that the individual items in a collection appear in an unexpected order.</span></span>  
  
- <span data-ttu-id="19a97-115">Za určitých podmínek, porovnání <xref:System.UInt16> hodnoty s jejich rozšířené nastavení je nesprávné v případě, že je povolena optimalizace.</span><span class="sxs-lookup"><span data-stu-id="19a97-115">Under certain conditions, the comparison of <xref:System.UInt16> values with their high bit set is incorrect if optimization is enabled.</span></span>  
  
- <span data-ttu-id="19a97-116">Za určitých podmínek, zejména při inicializaci pole hodnot, inicializace paměti <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> instrukce IL může inicializovat paměť s nesprávnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="19a97-116">Under certain conditions, particularly when initializing array values, memory initialization by the <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> IL instruction may initialize memory with an incorrect value.</span></span> <span data-ttu-id="19a97-117">To může vést neošetřené výjimce nebo nesprávný výstup.</span><span class="sxs-lookup"><span data-stu-id="19a97-117">This can result either in an unhandled exception or incorrect output.</span></span>  
  
- <span data-ttu-id="19a97-118">Za určitých podmínek výjimečných bit podmíněný test může vrátit nesprávná <xref:System.Boolean> hodnotu nebo vyvolat výjimku, pokud jsou povolené optimalizace kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="19a97-118">Under certain rare conditions, a conditional bit test can return the incorrect <xref:System.Boolean> value or throw an exception if compiler optimizations are enabled.</span></span>  
  
- <span data-ttu-id="19a97-119">Za určitých podmínek Pokud `if` příkaz slouží k otestování pro podmínku před vstupem `try` bloku a ve výstupu z `try` bloku a stejná podmínka je vyhodnocena v `catch` nebo `finally` bloku, nové Odebere 64bitového JIT kompilátoru `if` podmínky z `catch` nebo `finally` blokovat, pokud optimalizuje kód.</span><span class="sxs-lookup"><span data-stu-id="19a97-119">Under certain conditions, if an `if` statement is used to test for a condition before entering  a `try` block and in the exit from the `try` block, and the same condition is evaluated in the `catch` or `finally` block, the new 64-bit JIT compiler removes the `if` condition from the `catch` or `finally` block when it optimizes code.</span></span> <span data-ttu-id="19a97-120">V důsledku toho kód `if` příkaz v `catch` nebo `finally` bloku je bezpodmínečně provedeny.</span><span class="sxs-lookup"><span data-stu-id="19a97-120">As a result, code inside the `if` statement in the `catch` or `finally` block is executed unconditionally.</span></span>  
  
<a name="General"></a>   
## <a name="mitigation-of-known-issues"></a><span data-ttu-id="19a97-121">Zmírnění dopadů známých problémů</span><span class="sxs-lookup"><span data-stu-id="19a97-121">Mitigation of known issues</span></span>  
 <span data-ttu-id="19a97-122">Pokud narazíte na problémy uvedené výše, abyste mohli vyřešit pomocí některého z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="19a97-122">If you encounter the issues listed above, you can address them by doing any of the following:</span></span>  
  
- <span data-ttu-id="19a97-123">Upgrade na rozhraní .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="19a97-123">Upgrade to the .NET Framework 4.6.2.</span></span> <span data-ttu-id="19a97-124">Nový 64bitový kompilátor rozhraní .NET Framework 4.6.2 je součástí adresy každé z těchto známých problémů.</span><span class="sxs-lookup"><span data-stu-id="19a97-124">The new 64-bit compiler included with the .NET Framework 4.6.2 addresses each of these known issues.</span></span>  
  
- <span data-ttu-id="19a97-125">Ujistěte se, že je vaše verze Windows aktuální spuštěním aktualizace Windows.</span><span class="sxs-lookup"><span data-stu-id="19a97-125">Ensure that your version of Windows is up to date by running Windows Update.</span></span> <span data-ttu-id="19a97-126">Aktualizace služeb rozhraní .NET Framework 4.6 a 4.6.1 se vztahují na všechny tyto problémy s výjimkou <xref:System.NullReferenceException> v operace rozbalení.</span><span class="sxs-lookup"><span data-stu-id="19a97-126">Service updates to the .NET Framework 4.6 and 4.6.1 address each of these issues except the <xref:System.NullReferenceException> in an unboxing operation.</span></span>  
  
- <span data-ttu-id="19a97-127">Kompilovat s starší 64bitovým kompilátorem JIT.</span><span class="sxs-lookup"><span data-stu-id="19a97-127">Compile with the older 64-bit JIT compiler.</span></span> <span data-ttu-id="19a97-128">Zobrazit [zmírnění problémů s jinými problémy](#Other) části Další informace o tom, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="19a97-128">See the [Mitigation of other issues](#Other) section for more information on how to do this.</span></span>  
  
<a name="Other"></a>   
## <a name="mitigation-of-other-issues"></a><span data-ttu-id="19a97-129">Zmírnění problémů s jinými problémy</span><span class="sxs-lookup"><span data-stu-id="19a97-129">Mitigation of other issues</span></span>  
 <span data-ttu-id="19a97-130">Pokud narazíte na jakékoli další rozdíl v chování mezi kód zkompilovaný s starší 64bitovým kompilátorem a nového 64bitového kompilátoru JIT, nebo ladění a verze vydání aplikace, které jsou kompilovány pomocí nového 64bitového kompilátoru JIT, vám pomůžou následující aplikace s využitím starší 64bitového kompilátoru JIT kompilace:</span><span class="sxs-lookup"><span data-stu-id="19a97-130">If you encounter any other difference in behavior between code compiled with the older 64-bit compiler and the new 64-bit JIT compiler, or between the debug and release versions of your app that are both compiled with the new 64-bit JIT compiler, you can do the following to compile your app with the older 64-bit JIT compiler:</span></span>  
  
- <span data-ttu-id="19a97-131">Na základě jednotlivých aplikací, můžete přidat [ \<useLegacyJit >](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md) prvku do konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="19a97-131">On a per-application basis, you can add the [\<useLegacyJit>](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md) element to your application's configuration file.</span></span> <span data-ttu-id="19a97-132">Následující zakazuje kompilaci pomocí nového 64bitového kompilátoru JIT a místo toho používá starší verzi 64bitového kompilátoru JIT.</span><span class="sxs-lookup"><span data-stu-id="19a97-132">The following disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
    ```xml  
    <?xml version ="1.0"?>  
    <configuration>  
        <runtime>  
           <useLegacyJit enabled="1" />  
        </runtime>  
    </configuration>  
    ```  
  
- <span data-ttu-id="19a97-133">Na základě jednotlivých uživatelů můžete přidat `REG_DWORD` hodnotu s názvem `useLegacyJit` k `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` klíče registru.</span><span class="sxs-lookup"><span data-stu-id="19a97-133">On a per-user basis, you can add a `REG_DWORD` value named `useLegacyJit` to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key of the registry.</span></span> <span data-ttu-id="19a97-134">Hodnota 1 povolí starší verzi kompilátoru JIT 64-bit; Hodnota 0 zakáže a umožňuje nové 64bitovým kompilátorem JIT.</span><span class="sxs-lookup"><span data-stu-id="19a97-134">A value of 1 enables the legacy 64-bit JIT compiler; a value of 0 disables it and enables the new 64-bit JIT compiler.</span></span>  
  
- <span data-ttu-id="19a97-135">Na základě vázaná na počítač, můžete přidat `REG_DWORD` hodnotu s názvem `useLegacyJit` k `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` klíče registru.</span><span class="sxs-lookup"><span data-stu-id="19a97-135">On a per-machine basis, you can add a `REG_DWORD` value named `useLegacyJit` to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key of the registry.</span></span> <span data-ttu-id="19a97-136">Hodnota 1 povolí starší verzi kompilátoru JIT 64-bit; Hodnota 0 zakáže a umožňuje nové 64bitovým kompilátorem JIT.</span><span class="sxs-lookup"><span data-stu-id="19a97-136">A value of 1 enables the legacy 64-bit JIT compiler; a value of 0 disables it and enables the new 64-bit JIT compiler.</span></span>  
  
 <span data-ttu-id="19a97-137">Vám může také dejte nám vědět o problému pomocí hlášení chyby na [Microsoft Connect](https://connect.microsoft.com/VisualStudio).</span><span class="sxs-lookup"><span data-stu-id="19a97-137">You can also let us know about the problem by reporting a bug on [Microsoft Connect](https://connect.microsoft.com/VisualStudio).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19a97-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="19a97-138">See also</span></span>

- [<span data-ttu-id="19a97-139">Změny v modulu runtime</span><span class="sxs-lookup"><span data-stu-id="19a97-139">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
- [<span data-ttu-id="19a97-140">\<useLegacyJit> Element</span><span class="sxs-lookup"><span data-stu-id="19a97-140">\<useLegacyJit> Element</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md)
