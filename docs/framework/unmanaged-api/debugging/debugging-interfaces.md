---
title: Debugging – rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8b6d00d17615769a5d03d58e0eda5af62ca58368
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415959"
---
# <a name="debugging-interfaces"></a><span data-ttu-id="74566-102">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-102">Debugging Interfaces</span></span>
<span data-ttu-id="74566-103">Tato část popisuje nespravovaná rozhraní, která zpracovávají ladění programu, který je spouštěn v modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="74566-103">This section describes the unmanaged interfaces that handle the debugging of a program that is executing in the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="74566-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="74566-104">In This Section</span></span>  
 [<span data-ttu-id="74566-105">ICLRDataEnumMemoryRegions – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-105">ICLRDataEnumMemoryRegions Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)  
 <span data-ttu-id="74566-106">Představuje způsob, jak vytvořit výčet oblastí paměti zadaných volajícími.</span><span class="sxs-lookup"><span data-stu-id="74566-106">Provides a method to enumerate regions of memory that are specified by callers.</span></span>  
  
 [<span data-ttu-id="74566-107">ICLRDataEnumMemoryRegionsCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-107">ICLRDataEnumMemoryRegionsCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)  
 <span data-ttu-id="74566-108">Poskytuje metodu zpětného volání pro `EnumMemoryRegions` k poskytnutí zprávy ladicímu programu, výsledek pokusu o výčet určité oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="74566-108">Provides a callback method for `EnumMemoryRegions` to report to the debugger, the result of an attempt to enumerate a specified region of memory.</span></span>  
  
 [<span data-ttu-id="74566-109">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-109">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 <span data-ttu-id="74566-110">Poskytuje metody pro interakci s cílovým procesem CLR.</span><span class="sxs-lookup"><span data-stu-id="74566-110">Provides methods for interaction with a target CLR process.</span></span>  
  
 [<span data-ttu-id="74566-111">ICLRDataTarget2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-111">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 <span data-ttu-id="74566-112">Podtřída `ICLRDataTarget` vrstvou služeb přístupu k data, která se používá k manipulaci s oblastmi virtuální paměti v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="74566-112">A subclass of `ICLRDataTarget` that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
 [<span data-ttu-id="74566-113">ICLRDataTarget3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-113">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 <span data-ttu-id="74566-114">Podtřída [iclrdatatarget2 –](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) , která poskytuje přístup k informacím o výjimce.</span><span class="sxs-lookup"><span data-stu-id="74566-114">A subclass of [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
 [<span data-ttu-id="74566-115">ICLRDebugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-115">ICLRDebugging Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md)  
 <span data-ttu-id="74566-116">Poskytuje metody, které zpracovávají načítání a uvolňování modulů pro ladění.</span><span class="sxs-lookup"><span data-stu-id="74566-116">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
 [<span data-ttu-id="74566-117">ICLRDebuggingLibraryProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-117">ICLRDebuggingLibraryProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md)  
 <span data-ttu-id="74566-118">Zahrnuje [ProvideLibrary – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) metodu, která získá rozhraní zpětného volání, které umožňuje knihovnám ladění specifickým pro verzi modulu runtime k vyhledání a načtení na požádání zprostředkovatele knihovny.</span><span class="sxs-lookup"><span data-stu-id="74566-118">Includes the [ProvideLibrary Method](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
 [<span data-ttu-id="74566-119">ICLRMetadataLocator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-119">ICLRMetadataLocator Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-interface.md)  
 <span data-ttu-id="74566-120">Rozhraní používané vrstvou služeb přístupu k datům k vyhledání metadat sestavení v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="74566-120">Interface used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
 [<span data-ttu-id="74566-121">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-121">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 <span data-ttu-id="74566-122">Poskytuje metody, které umožňují vývojářům ladit aplikace v prostředí CLR.</span><span class="sxs-lookup"><span data-stu-id="74566-122">Provides methods that allow developers to debug applications in the CLR environment.</span></span>  
  
 [<span data-ttu-id="74566-123">ICorDebugAppDomain – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-123">ICorDebugAppDomain Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md)  
 <span data-ttu-id="74566-124">Poskytuje metody pro ladění domén aplikace.</span><span class="sxs-lookup"><span data-stu-id="74566-124">Provides methods for debugging application domains.</span></span>  
  
 [<span data-ttu-id="74566-125">ICorDebugAppDomain2 – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-125">ICorDebugAppDomain2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-interface.md)  
 <span data-ttu-id="74566-126">Poskytuje metody pro práci s poli, ukazateli, ukazateli na funkci a typy ByRef.</span><span class="sxs-lookup"><span data-stu-id="74566-126">Provides methods to work with arrays, pointers, function pointers, and ByRef types.</span></span> <span data-ttu-id="74566-127">Toto rozhraní je rozšířením `ICorDebugAppDomain` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="74566-127">This interface is an extension of the `ICorDebugAppDomain` interface.</span></span>  
  
 [<span data-ttu-id="74566-128">ICorDebugAppDomain3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-128">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)  
 <span data-ttu-id="74566-129">Poskytuje metody pro práci s [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typy v aplikační doméně.</span><span class="sxs-lookup"><span data-stu-id="74566-129">Provides methods to work with the [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types in an application domain.</span></span> <span data-ttu-id="74566-130">Toto rozhraní je rozšířením `ICorDebugAppDomain` a `ICorDebugAppDomain2` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="74566-130">This interface is an extension of the `ICorDebugAppDomain` and `ICorDebugAppDomain2` interfaces.</span></span>  
  
 [<span data-ttu-id="74566-131">ICorDebugAppDomain4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-131">ICorDebugAppDomain4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)  
 <span data-ttu-id="74566-132">Logicky rozšiřuje [ICorDebugAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md) získat objekt spravovaného z obálka volatelná aplikacemi COM rozhraní.</span><span class="sxs-lookup"><span data-stu-id="74566-132">Logically extends the [ICorDebugAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md) interface to get a managed object from a COM callable wrapper.</span></span>  
  
 [<span data-ttu-id="74566-133">ICorDebugAppDomainEnum – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-133">ICorDebugAppDomainEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md)  
 <span data-ttu-id="74566-134">Poskytuje metodu, která vrací zadaný počet `ICorDebugAppDomain` hodnot počínaje na dalším místě ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="74566-134">Provides a method that returns a specified number of `ICorDebugAppDomain` values starting at the next location in the enumeration.</span></span>  
  
 [<span data-ttu-id="74566-135">ICorDebugArrayValue – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-135">ICorDebugArrayValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-interface.md)  
 <span data-ttu-id="74566-136">Podtřída `ICorDebugHeapValue` , která představuje jednorozměrné nebo vícedimenzionální pole.</span><span class="sxs-lookup"><span data-stu-id="74566-136">A subclass of `ICorDebugHeapValue` that represents a single-dimensional or multi-dimensional array.</span></span>  
  
 [<span data-ttu-id="74566-137">ICorDebugAssembly – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-137">ICorDebugAssembly Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md)  
 <span data-ttu-id="74566-138">Představuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="74566-138">Represents an assembly.</span></span>  
  
 [<span data-ttu-id="74566-139">ICorDebugAssembly2 – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-139">ICorDebugAssembly2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly2-interface.md)  
 <span data-ttu-id="74566-140">Představuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="74566-140">Represents an assembly.</span></span> <span data-ttu-id="74566-141">Toto rozhraní je rozšířením `ICorDebugAssembly` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="74566-141">This interface is an extension of the `ICorDebugAssembly` interface.</span></span>  
  
 [<span data-ttu-id="74566-142">ICorDebugAssembly3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-142">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 <span data-ttu-id="74566-143">Logicky rozšiřuje [ICorDebugAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md) rozhraní k poskytování podpory pro sestavení kontejneru a jejich obsažené sestavení.</span><span class="sxs-lookup"><span data-stu-id="74566-143">Logically extends the [ICorDebugAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md) interface to provide support for container assemblies and their contained assemblies.</span></span> <span data-ttu-id="74566-144">**K dispozici na pouze .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="74566-144">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="74566-145">ICorDebugAssemblyEnum – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-145">ICorDebugAssemblyEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassemblyenum-interface.md)  
 <span data-ttu-id="74566-146">Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugAssembly` pole.</span><span class="sxs-lookup"><span data-stu-id="74566-146">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugAssembly` arrays.</span></span>  
  
 [<span data-ttu-id="74566-147">ICorDebugBlockingObjectEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-147">ICorDebugBlockingObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
 <span data-ttu-id="74566-148">Poskytuje enumerátor pro seznam [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="74566-148">Provides an enumerator for a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>  
  
 [<span data-ttu-id="74566-149">ICorDebugBoxValue – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-149">ICorDebugBoxValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugboxvalue-interface.md)  
 <span data-ttu-id="74566-150">Podtřída `ICorDebugHeapValue` představující objektu třídy zabalených hodnot.</span><span class="sxs-lookup"><span data-stu-id="74566-150">A subclass of `ICorDebugHeapValue` that represents a boxed value class object.</span></span>  
  
 [<span data-ttu-id="74566-151">ICorDebugBreakpoint – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-151">ICorDebugBreakpoint Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-interface.md)  
 <span data-ttu-id="74566-152">Představuje zarážku ve funkci nebo bod sledování na hodnotě.</span><span class="sxs-lookup"><span data-stu-id="74566-152">Represents a breakpoint in a function or a watch point on a value.</span></span>  
  
 [<span data-ttu-id="74566-153">ICorDebugBreakpointEnum – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-153">ICorDebugBreakpointEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-interface.md)  
 <span data-ttu-id="74566-154">Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugBreakpoint` pole.</span><span class="sxs-lookup"><span data-stu-id="74566-154">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugBreakpoint` arrays.</span></span>  
  
 [<span data-ttu-id="74566-155">ICorDebugChain – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-155">ICorDebugChain Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md)  
 <span data-ttu-id="74566-156">Představuje segment fyzického nebo logického zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="74566-156">Represents a segment of a physical or logical call stack.</span></span>  
  
 [<span data-ttu-id="74566-157">ICorDebugChainEnum – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-157">ICorDebugChainEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchainenum-interface.md)  
 <span data-ttu-id="74566-158">Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugChain` pole.</span><span class="sxs-lookup"><span data-stu-id="74566-158">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugChain` arrays.</span></span>  
  
 [<span data-ttu-id="74566-159">ICorDebugClass – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-159">ICorDebugClass Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)  
 <span data-ttu-id="74566-160">Představuje typ, který může být základní nebo komplexní (tj. definovaný uživatelem).</span><span class="sxs-lookup"><span data-stu-id="74566-160">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="74566-161">Pokud je typ obecný, `ICorDebugClass` představuje obecný typ bez instancí.</span><span class="sxs-lookup"><span data-stu-id="74566-161">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
 [<span data-ttu-id="74566-162">ICorDebugClass2 – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-162">ICorDebugClass2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-interface.md)  
 <span data-ttu-id="74566-163">Představuje obecnou třídu nebo třídu s parametrem metody typu <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="74566-163">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="74566-164">Toto rozhraní rozšiřuje `ICorDebugClass`.</span><span class="sxs-lookup"><span data-stu-id="74566-164">This interface extends `ICorDebugClass`.</span></span>  
  
 [<span data-ttu-id="74566-165">ICorDebugCode – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-165">ICorDebugCode Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)  
 <span data-ttu-id="74566-166">Představuje segment kódu jazyka MSIL nebo nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="74566-166">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
 [<span data-ttu-id="74566-167">ICorDebugCode2 – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-167">ICorDebugCode2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md)  
 <span data-ttu-id="74566-168">Poskytuje metody, které rozšiřují možnosti `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="74566-168">Provides methods that extend the capabilities of `ICorDebugCode`.</span></span>  
  
 [<span data-ttu-id="74566-169">ICorDebugCode3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-169">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 <span data-ttu-id="74566-170">Poskytuje metodu, která rozšiřuje [ICorDebugCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md) a [ICorDebugCode2](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md) zadání informací o spravované návratové hodnotě.</span><span class="sxs-lookup"><span data-stu-id="74566-170">Provides a method that extends [ICorDebugCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md) and [ICorDebugCode2](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md) to provide information about a managed return value.</span></span>  
  
 [<span data-ttu-id="74566-171">ICorDebugCode4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-171">ICorDebugCode4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)  
 <span data-ttu-id="74566-172">Poskytuje metodu, která umožňuje ladicí program, který výčet lokálních proměnných a argumentů funkce.</span><span class="sxs-lookup"><span data-stu-id="74566-172">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
 [<span data-ttu-id="74566-173">ICorDebugCodeEnum – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-173">ICorDebugCodeEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcodeenum-interface.md)  
 <span data-ttu-id="74566-174">Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugCode` pole.</span><span class="sxs-lookup"><span data-stu-id="74566-174">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugCode` arrays.</span></span>  
  
 [<span data-ttu-id="74566-175">ICorDebugComObjectValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-175">ICorDebugComObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)  
 <span data-ttu-id="74566-176">Poskytuje metody pro načtení objektů z mezipaměti rozhraní.</span><span class="sxs-lookup"><span data-stu-id="74566-176">Provides methods to retrieve cached interface objects.</span></span>  
  
 [<span data-ttu-id="74566-177">ICorDebugContext – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-177">ICorDebugContext Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontext-interface.md)  
 <span data-ttu-id="74566-178">Představuje objekt kontextu.</span><span class="sxs-lookup"><span data-stu-id="74566-178">Represents a context object.</span></span> <span data-ttu-id="74566-179">Toto rozhraní zatím nebylo implementováno.</span><span class="sxs-lookup"><span data-stu-id="74566-179">This interface has not been implemented yet.</span></span>  
  
 [<span data-ttu-id="74566-180">ICorDebugController – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-180">ICorDebugController Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-interface.md)  
 <span data-ttu-id="74566-181">Představuje rozsah buď <xref:System.Diagnostics.Process> nebo <xref:System.AppDomain>, ve které provádění kódu lze ovládat kontext.</span><span class="sxs-lookup"><span data-stu-id="74566-181">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
 [<span data-ttu-id="74566-182">ICorDebugDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-182">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 <span data-ttu-id="74566-183">Poskytuje rozhraní zpětného volání, které poskytuje přístup ke konkrétnímu cílovému procesu.</span><span class="sxs-lookup"><span data-stu-id="74566-183">Provides a callback interface that provides access to a particular target process.</span></span>  
  
 [<span data-ttu-id="74566-184">ICorDebugDataTarget2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-184">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 <span data-ttu-id="74566-185">Logicky rozšiřuje [icordebugdatatarget –](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="74566-185">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="74566-186">**K dispozici na pouze .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="74566-186">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="74566-187">ICorDebugDataTarget3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-187">ICorDebugDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-interface.md)  
 <span data-ttu-id="74566-188">Logicky rozšiřuje [icordebugdatatarget –](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) rozhraní pro zadání informací o načtené moduly.</span><span class="sxs-lookup"><span data-stu-id="74566-188">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span> <span data-ttu-id="74566-189">**K dispozici na pouze .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="74566-189">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="74566-190">ICorDebugDebugEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-190">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 <span data-ttu-id="74566-191">Definuje základní rozhraní, ze kterého jsou všechny `ICorDebug` výjimky ladění jsou odvozeny.</span><span class="sxs-lookup"><span data-stu-id="74566-191">Defines the base interface from which all `ICorDebug` debug events derive.</span></span> <span data-ttu-id="74566-192">**K dispozici na pouze .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="74566-192">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="74566-193">ICorDebugEditAndContinueErrorInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-193">ICorDebugEditAndContinueErrorInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinueerrorinfo-interface.md)  
 <span data-ttu-id="74566-194">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="74566-194">Obsolete.</span></span> <span data-ttu-id="74566-195">Toto rozhraní nepoužívejte.</span><span class="sxs-lookup"><span data-stu-id="74566-195">Do not use this interface.</span></span>  
  
 [<span data-ttu-id="74566-196">ICorDebugEditAndContinueSnapshot – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-196">ICorDebugEditAndContinueSnapshot Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinuesnapshot-interface.md)  
 <span data-ttu-id="74566-197">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="74566-197">Obsolete.</span></span> <span data-ttu-id="74566-198">Toto rozhraní nepoužívejte.</span><span class="sxs-lookup"><span data-stu-id="74566-198">Do not use this interface.</span></span>  
  
 [<span data-ttu-id="74566-199">ICorDebugEnum – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-199">ICorDebugEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-interface1.md)  
 <span data-ttu-id="74566-200">Slouží jako abstraktní základní rozhraní pro enumerátory ladění.</span><span class="sxs-lookup"><span data-stu-id="74566-200">Serves as the abstract base interface for debugging enumerators.</span></span>  
  
 [<span data-ttu-id="74566-201">ICorDebugErrorInfoEnum – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-201">ICorDebugErrorInfoEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugerrorinfoenum-interface.md)  
 <span data-ttu-id="74566-202">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="74566-202">Obsolete.</span></span> <span data-ttu-id="74566-203">Toto rozhraní nepoužívejte.</span><span class="sxs-lookup"><span data-stu-id="74566-203">Do not use this interface.</span></span>  
  
 [<span data-ttu-id="74566-204">ICorDebugEval – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-204">ICorDebugEval Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-interface.md)  
 <span data-ttu-id="74566-205">Poskytuje metody povolující ladicímu programu spouštět kód v kontextu laděného kódu.</span><span class="sxs-lookup"><span data-stu-id="74566-205">Provides methods to enable the debugger to execute code within the context of the code being debugged.</span></span>  
  
 [<span data-ttu-id="74566-206">ICorDebugEval2 – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-206">ICorDebugEval2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-interface.md)  
 <span data-ttu-id="74566-207">Rozšiřuje `ICorDebugEval` k poskytování podpory pro obecné typy.</span><span class="sxs-lookup"><span data-stu-id="74566-207">Extends `ICorDebugEval` to provide support for generic types.</span></span>  
  
 [<span data-ttu-id="74566-208">ICorDebugExceptionDebugEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-208">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 <span data-ttu-id="74566-209">Rozšiřuje [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) rozhraní pro podporu události výjimky.</span><span class="sxs-lookup"><span data-stu-id="74566-209">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support exception events.</span></span> <span data-ttu-id="74566-210">**K dispozici na pouze .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="74566-210">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="74566-211">ICorDebugExceptionObjectCallStackEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-211">ICorDebugExceptionObjectCallStackEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
 <span data-ttu-id="74566-212">Poskytuje enumerátor pro informace zásobníku volání, který je vložený v objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="74566-212">Provides an enumerator for call stack information that is embedded in an exception object.</span></span>  
  
 [<span data-ttu-id="74566-213">ICorDebugExceptionObjectValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-213">ICorDebugExceptionObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-interface.md)  
 <span data-ttu-id="74566-214">Rozšiřuje [ICorDebugObjectValue](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md) rozhraní pro poskytnutí informací o trasování zásobníku z objektu spravované výjimky.</span><span class="sxs-lookup"><span data-stu-id="74566-214">Extends the [ICorDebugObjectValue](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md) interface to provide stack trace information from a managed exception object.</span></span>  
  
 [<span data-ttu-id="74566-215">ICorDebugFrame – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-215">ICorDebugFrame Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md)  
 <span data-ttu-id="74566-216">Představuje snímek aktuálního zásobníku.</span><span class="sxs-lookup"><span data-stu-id="74566-216">Represents a frame on the current stack.</span></span>  
  
 [<span data-ttu-id="74566-217">ICorDebugFrameEnum – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-217">ICorDebugFrameEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframeenum-interface.md)  
 <span data-ttu-id="74566-218">Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugFrame` pole.</span><span class="sxs-lookup"><span data-stu-id="74566-218">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugFrame` arrays.</span></span>  
  
 [<span data-ttu-id="74566-219">ICorDebugFunction – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-219">ICorDebugFunction Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md)  
 <span data-ttu-id="74566-220">Představuje spravovanou funkci nebo metodu.</span><span class="sxs-lookup"><span data-stu-id="74566-220">Represents a managed function or method.</span></span>  
  
 [<span data-ttu-id="74566-221">ICorDebugFunction2 – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-221">ICorDebugFunction2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-interface.md)  
 <span data-ttu-id="74566-222">Logicky rozšiřuje `ICorDebugFunction` a poskytuje podporu pro funkce pouze můj kód krokové ladění.</span><span class="sxs-lookup"><span data-stu-id="74566-222">Logically extends `ICorDebugFunction` to provide support for Just My Code step-through debugging.</span></span>  
  
 [<span data-ttu-id="74566-223">ICorDebugFunction3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-223">ICorDebugFunction3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-interface.md)  
 <span data-ttu-id="74566-224">Logicky rozšiřuje [ICorDebugFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md) rozhraní pro žádost o ReJIT poskytují přístup ke kódu.</span><span class="sxs-lookup"><span data-stu-id="74566-224">Logically extends the [ICorDebugFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md) interface to provide access to code from a ReJIT request.</span></span>  
  
 [<span data-ttu-id="74566-225">ICorDebugFunctionBreakpoint – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-225">ICorDebugFunctionBreakpoint Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-interface.md)  
 <span data-ttu-id="74566-226">Rozšiřuje `ICorDebugBreakpoint` pro podporu zarážek v rámci funkcí.</span><span class="sxs-lookup"><span data-stu-id="74566-226">Extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
 [<span data-ttu-id="74566-227">ICorDebugGCReferenceEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-227">ICorDebugGCReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
 <span data-ttu-id="74566-228">Poskytuje enumerátor pro objekty, které budou uvolněny z paměti.</span><span class="sxs-lookup"><span data-stu-id="74566-228">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
 [<span data-ttu-id="74566-229">ICorDebugGenericValue – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-229">ICorDebugGenericValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-interface.md)  
 <span data-ttu-id="74566-230">Podtřída `ICorDebugValue` , která platí pro všechny hodnoty.</span><span class="sxs-lookup"><span data-stu-id="74566-230">A subclass of `ICorDebugValue` that applies to all values.</span></span> <span data-ttu-id="74566-231">Toto rozhraní poskytuje metody Get a Set pro hodnotu.</span><span class="sxs-lookup"><span data-stu-id="74566-231">This interface provides Get and Set methods for the value.</span></span>  
  
 [<span data-ttu-id="74566-232">ICorDebugGuidToTypeEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-232">ICorDebugGuidToTypeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
 <span data-ttu-id="74566-233">Poskytuje enumerátor pro objekt, který mapuje identifikátory GUID a odpovídající `ICorDebugType` objekty.</span><span class="sxs-lookup"><span data-stu-id="74566-233">Provides an enumerator for an object that maps GUIDs and their corresponding `ICorDebugType` objects.</span></span>  
  
 [<span data-ttu-id="74566-234">ICorDebugHandleValue – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-234">ICorDebugHandleValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-interface.md)  
 <span data-ttu-id="74566-235">Podtřída `ICorDebugReferenceValue` , která představuje referenční hodnotu, do které ladicí program vytvořil popisovač pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="74566-235">A subclass of `ICorDebugReferenceValue` that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
 [<span data-ttu-id="74566-236">ICorDebugHeapEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-236">ICorDebugHeapEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
 <span data-ttu-id="74566-237">Poskytuje enumerátor pro objekty na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="74566-237">Provides an enumerator for objects on the managed heap.</span></span>  
  
 [<span data-ttu-id="74566-238">ICorDebugHeapSegmentEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-238">ICorDebugHeapSegmentEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
 <span data-ttu-id="74566-239">Poskytuje enumerátor pro oblasti paměti spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="74566-239">Provides an enumerator for the memory regions of the managed heap.</span></span>  
  
 [<span data-ttu-id="74566-240">ICorDebugHeapValue – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-240">ICorDebugHeapValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-interface.md)  
 <span data-ttu-id="74566-241">Podtřída `ICorDebugValue` , který představuje objekt, který byl shromážděn uvolňováním CLR.</span><span class="sxs-lookup"><span data-stu-id="74566-241">A subclass of `ICorDebugValue` that represents an object that has been collected by the CLR garbage collector.</span></span>  
  
 [<span data-ttu-id="74566-242">ICorDebugHeapValue2 – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-242">ICorDebugHeapValue2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue2-interface1.md)  
 <span data-ttu-id="74566-243">Rozšíření `ICorDebugHeapValue` , která poskytuje podporu pro popisovače modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="74566-243">An extension of `ICorDebugHeapValue` that provides support for runtime handles.</span></span>  
  
 [<span data-ttu-id="74566-244">ICorDebugHeapValue3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-244">ICorDebugHeapValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md)  
 <span data-ttu-id="74566-245">Zpřístupní vlastnosti uzamčení sledování objektů.</span><span class="sxs-lookup"><span data-stu-id="74566-245">Exposes the monitor lock properties of objects.</span></span>  
  
 [<span data-ttu-id="74566-246">ICorDebugILCode – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-246">ICorDebugILCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)  
 <span data-ttu-id="74566-247">Představuje segment kódu (IL intermediate language).</span><span class="sxs-lookup"><span data-stu-id="74566-247">Represents a segment of intermediate language (IL) code.</span></span>  
  
 [<span data-ttu-id="74566-248">ICorDebugILCode2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-248">ICorDebugILCode2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)  
 <span data-ttu-id="74566-249">Logicky rozšiřuje [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) rozhraní poskytuje metody, které vracejí token pro místní proměnné podpis funkce a, která mapují profiler instrumentované (IL intermediate language) kompenzuje původní metody IL posuny.</span><span class="sxs-lookup"><span data-stu-id="74566-249">Logically extends the [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
 [<span data-ttu-id="74566-250">ICorDebugILFrame – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-250">ICorDebugILFrame Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-interface.md)  
 <span data-ttu-id="74566-251">Představuje rámec zásobníku kódu MSIL.</span><span class="sxs-lookup"><span data-stu-id="74566-251">Represents a stack frame of MSIL code.</span></span>  
  
 [<span data-ttu-id="74566-252">ICorDebugILFrame2 – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-252">ICorDebugILFrame2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-interface.md)  
 <span data-ttu-id="74566-253">Logické rozšíření `ICorDebugILFrame`.</span><span class="sxs-lookup"><span data-stu-id="74566-253">A logical extension of `ICorDebugILFrame`.</span></span>  
  
 [<span data-ttu-id="74566-254">ICorDebugILFrame3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-254">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)  
 <span data-ttu-id="74566-255">Poskytuje metodu, která zapouzdřuje vrácenou hodnotu funkce.</span><span class="sxs-lookup"><span data-stu-id="74566-255">Provides a method that encapsulates the return value of a function.</span></span>  
  
 [<span data-ttu-id="74566-256">ICorDebugILFrame4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-256">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 <span data-ttu-id="74566-257">Poskytuje metody, které umožňují přístup k místní proměnné a kód v bloku zásobníku kódu (IL intermediate language).</span><span class="sxs-lookup"><span data-stu-id="74566-257">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="74566-258">Parametr určuje, zda ladicí program má přístup k proměnné a kód přidaný v profileru ReJIT instrumentace.</span><span class="sxs-lookup"><span data-stu-id="74566-258">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
 [<span data-ttu-id="74566-259">ICorDebugInstanceFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-259">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 <span data-ttu-id="74566-260">Představuje informací symbolů ladění pro pole instance.</span><span class="sxs-lookup"><span data-stu-id="74566-260">Represents the debug symbol information for an instance field.</span></span> <span data-ttu-id="74566-261">**K dispozici na pouze .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="74566-261">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="74566-262">ICorDebugInternalFrame – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-262">ICorDebugInternalFrame Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-interface.md)  
 <span data-ttu-id="74566-263">Určuje typy rámců pro ladicí program.</span><span class="sxs-lookup"><span data-stu-id="74566-263">Identifies frame types for the debugger.</span></span>  
  
 [<span data-ttu-id="74566-264">ICorDebugInternalFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-264">ICorDebugInternalFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)  
 <span data-ttu-id="74566-265">Poskytuje informace o vnitřních rámcích, včetně adresy zásobníku a pozice ve vztahu k [ICorDebugFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md) objekty.</span><span class="sxs-lookup"><span data-stu-id="74566-265">Provides information about internal frames, including stack address and position in relation to [ICorDebugFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md) objects.</span></span>  
  
 [<span data-ttu-id="74566-266">ICorDebugLoadedModule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-266">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 <span data-ttu-id="74566-267">Poskytuje informace o u načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="74566-267">Provides information about a loaded module.</span></span> <span data-ttu-id="74566-268">**K dispozici na pouze .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="74566-268">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="74566-269">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-269">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)  
 <span data-ttu-id="74566-270">Poskytuje metody pro zpětná volání procesu ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="74566-270">Provides methods to process debugger callbacks.</span></span>  
  
 [<span data-ttu-id="74566-271">ICorDebugManagedCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-271">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 <span data-ttu-id="74566-272">Poskytuje metody pro podporu zpracování výjimek ladicího programu a spravované pomocníky ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="74566-272">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="74566-273">`ICorDebugManagedCallback2` je logickým rozšířením `ICorDebugManagedCallback`.</span><span class="sxs-lookup"><span data-stu-id="74566-273">`ICorDebugManagedCallback2` is a logical extension of `ICorDebugManagedCallback`.</span></span>  
  
 [<span data-ttu-id="74566-274">ICorDebugManagedCallback3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-274">ICorDebugManagedCallback3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-interface.md)  
 <span data-ttu-id="74566-275">Poskytuje metodu zpětného volání, která určuje, že povolené vlastní oznámení ladicího programu bylo vyvoláno.</span><span class="sxs-lookup"><span data-stu-id="74566-275">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
 [<span data-ttu-id="74566-276">ICorDebugMDA – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-276">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 <span data-ttu-id="74566-277">Představuje zprávu pomocníka spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="74566-277">Represents a managed debugging assistant (MDA) message.</span></span>  
  
 [<span data-ttu-id="74566-278">ICorDebugMemoryBuffer – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-278">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 <span data-ttu-id="74566-279">Představuje vyrovnávací paměť v paměti.</span><span class="sxs-lookup"><span data-stu-id="74566-279">Represents an in-memory buffer.</span></span> <span data-ttu-id="74566-280">**K dispozici na pouze .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="74566-280">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="74566-281">ICorDebugMergedAssemblyRecord – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-281">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 <span data-ttu-id="74566-282">Poskytuje informace o sloučené sestavení.</span><span class="sxs-lookup"><span data-stu-id="74566-282">Provides information about a merged assembly.</span></span> <span data-ttu-id="74566-283">**K dispozici na pouze .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="74566-283">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="74566-284">ICorDebugMetaDataLocator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-284">ICorDebugMetaDataLocator Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmetadatalocator-interface.md)  
 <span data-ttu-id="74566-285">Poskytuje informace metadat k ladicímu programu.</span><span class="sxs-lookup"><span data-stu-id="74566-285">Provides metadata information to the debugger.</span></span>  
  
 [<span data-ttu-id="74566-286">ICorDebugModule – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-286">ICorDebugModule Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-interface.md)  
 <span data-ttu-id="74566-287">Představuje modul CLR, který je spustitelný soubor nebo dynamická knihovna (DLL).</span><span class="sxs-lookup"><span data-stu-id="74566-287">Represents a CLR module, which is either an executable or a dynamic-link library (DLL).</span></span>  
  
 [<span data-ttu-id="74566-288">ICorDebugModule2 – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-288">ICorDebugModule2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-interface.md)  
 <span data-ttu-id="74566-289">Slouží jako logické rozšíření pro `ICorDebugModule`.</span><span class="sxs-lookup"><span data-stu-id="74566-289">Serves as a logical extension to `ICorDebugModule`.</span></span>  
  
 [<span data-ttu-id="74566-290">ICorDebugModule3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-290">ICorDebugModule3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule3-interface.md)  
 <span data-ttu-id="74566-291">Vytvoří čtečku symbolů pro dynamický modul.</span><span class="sxs-lookup"><span data-stu-id="74566-291">Creates a symbol reader for a dynamic module.</span></span>  
  
 [<span data-ttu-id="74566-292">ICorDebugModuleBreakpoint – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-292">ICorDebugModuleBreakpoint Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-interface.md)  
 <span data-ttu-id="74566-293">Rozšiřuje `ICorDebugBreakpoint` a zajistit tak přístup k určitým modulům.</span><span class="sxs-lookup"><span data-stu-id="74566-293">Extends `ICorDebugBreakpoint` to provide access to specific modules.</span></span>  
  
 [<span data-ttu-id="74566-294">ICorDebugModuleDebugEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-294">ICorDebugModuleDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
 <span data-ttu-id="74566-295">Rozšiřuje [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) rozhraní pro podporu událostí na úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="74566-295">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support module-level events.</span></span> <span data-ttu-id="74566-296">**K dispozici na pouze .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="74566-296">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="74566-297">ICorDebugModuleEnum – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-297">ICorDebugModuleEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-interface.md)  
 <span data-ttu-id="74566-298">Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugModule` pole.</span><span class="sxs-lookup"><span data-stu-id="74566-298">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugModule` arrays.</span></span>  
  
 [<span data-ttu-id="74566-299">ICorDebugMutableDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-299">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 <span data-ttu-id="74566-300">Rozšiřuje [icordebugdatatarget –](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) rozhraní pro podporu proměnlivé datové cíle.</span><span class="sxs-lookup"><span data-stu-id="74566-300">Extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
 [<span data-ttu-id="74566-301">ICorDebugNativeFrame – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-301">ICorDebugNativeFrame Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-interface.md)  
 <span data-ttu-id="74566-302">Specializovaná implementace `ICorDebugFrame` pro nativní snímky.</span><span class="sxs-lookup"><span data-stu-id="74566-302">A specialized implementation of `ICorDebugFrame` used for native frames.</span></span>  
  
 [<span data-ttu-id="74566-303">ICorDebugNativeFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-303">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 <span data-ttu-id="74566-304">Poskytuje metody, které testují podřízené a nadřazené vztahy rámce.</span><span class="sxs-lookup"><span data-stu-id="74566-304">Provides methods that test for child and parent frame relationships.</span></span>  
  
 [<span data-ttu-id="74566-305">ICorDebugObjectEnum – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-305">ICorDebugObjectEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-interface.md)  
 <span data-ttu-id="74566-306">Implementuje `ICorDebugEnum` metody a vytváří výčet polí objektů podle jejich relativních virtuálních adres (RVA).</span><span class="sxs-lookup"><span data-stu-id="74566-306">Implements `ICorDebugEnum` methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
 [<span data-ttu-id="74566-307">ICorDebugObjectValue – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-307">ICorDebugObjectValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md)  
 <span data-ttu-id="74566-308">Podtřída `ICorDebugValue` , která představuje hodnotu, která obsahuje objekt.</span><span class="sxs-lookup"><span data-stu-id="74566-308">A subclass of `ICorDebugValue` that represents a value that contains an object.</span></span>  
  
 [<span data-ttu-id="74566-309">ICorDebugObjectValue2 – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-309">ICorDebugObjectValue2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue2-interface.md)  
 <span data-ttu-id="74566-310">Rozšiřuje `ICorDebugObjectValue` pro podporu dědičnosti a přepsání.</span><span class="sxs-lookup"><span data-stu-id="74566-310">Extends `ICorDebugObjectValue` to support inheritance and overrides.</span></span>  
  
 [<span data-ttu-id="74566-311">ICorDebugProcess – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-311">ICorDebugProcess Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md)  
 <span data-ttu-id="74566-312">Představuje proces, který spouští spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="74566-312">Represents a process that is executing managed code.</span></span>  
  
 [<span data-ttu-id="74566-313">ICorDebugProcess2 – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-313">ICorDebugProcess2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-interface1.md)  
 <span data-ttu-id="74566-314">Logické rozšíření `ICorDebugProcess`.</span><span class="sxs-lookup"><span data-stu-id="74566-314">A logical extension of `ICorDebugProcess`.</span></span>  
  
 [<span data-ttu-id="74566-315">ICorDebugProcess3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-315">ICorDebugProcess3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)  
 <span data-ttu-id="74566-316">Řídí vlastní oznámení ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="74566-316">Controls custom debugger notifications.</span></span>  
  
 [<span data-ttu-id="74566-317">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-317">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 <span data-ttu-id="74566-318">Rozšiřuje [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) rozhraní pro podporu přístupu ke spravované haldě, k poskytování informací o uvolnění paměti spravovaných objektů a určení, zda ladicí program načítá obrázky z aplikace v místním mezipaměti nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="74566-318">Extends the [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application's local native image cache.</span></span>  
  
 [<span data-ttu-id="74566-319">ICorDebugProcess6 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-319">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 <span data-ttu-id="74566-320">Logicky rozšiřuje [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) rozhraní k povolení funkcí, jako je například dekódování spravované ladění události, které jsou zakódovány nativní výjimka ladění událostí a rozdělení virtuální modulu.</span><span class="sxs-lookup"><span data-stu-id="74566-320">Logically extends the [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span> <span data-ttu-id="74566-321">**K dispozici na pouze .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="74566-321">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="74566-322">ICorDebugProcess7 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-322">ICorDebugProcess7 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-interface.md)  
 <span data-ttu-id="74566-323">Poskytuje metodu, která nakonfiguruje ladicího programu pro zpracování aktualizace metadat v paměti v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="74566-323">Provides a method that configures the debugger to handle in-memory metadata updates in the target process.</span></span>  
  
 [<span data-ttu-id="74566-324">ICorDebugProcess8 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-324">ICorDebugProcess8 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)  
 <span data-ttu-id="74566-325">Logicky rozšiřuje [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) rozhraní pro povolení nebo zakázání určitých typů [icordebugmanagedcallback2 –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) zpětných volání výjimky.</span><span class="sxs-lookup"><span data-stu-id="74566-325">Logically extends the [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interface to enable or disable certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
 [<span data-ttu-id="74566-326">ICorDebugProcessEnum – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-326">ICorDebugProcessEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocessenum-interface.md)  
 <span data-ttu-id="74566-327">Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugProcess` pole.</span><span class="sxs-lookup"><span data-stu-id="74566-327">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugProcess` arrays.</span></span>  
  
 [<span data-ttu-id="74566-328">ICorDebugReferenceValue – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-328">ICorDebugReferenceValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-interface.md)  
 <span data-ttu-id="74566-329">Podtřída `ICorDebugValue` podporující referenční typy.</span><span class="sxs-lookup"><span data-stu-id="74566-329">A subclass of `ICorDebugValue` that supports reference types.</span></span>  
  
 [<span data-ttu-id="74566-330">ICorDebugRegisterSet – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-330">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 <span data-ttu-id="74566-331">Představuje sadu registrů, které jsou k dispozici v počítači, který aktuálně spouští kód.</span><span class="sxs-lookup"><span data-stu-id="74566-331">Represents the set of registers available on the machine that is currently executing code.</span></span>  
  
 [<span data-ttu-id="74566-332">ICorDebugRegisterSet2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-332">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 <span data-ttu-id="74566-333">Rozšiřuje možnosti `ICorDebugRegisterSet` pro hardwarové platformy, které mají více než 64 registrů.</span><span class="sxs-lookup"><span data-stu-id="74566-333">Extends the capabilities of `ICorDebugRegisterSet` for hardware platforms that have more than 64 registers.</span></span>  
  
 [<span data-ttu-id="74566-334">ICorDebugRemote – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-334">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 <span data-ttu-id="74566-335">Umožňuje spustit nebo připojit spravovaný ladicí program ke vzdálenému cílovému procesu.</span><span class="sxs-lookup"><span data-stu-id="74566-335">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
 [<span data-ttu-id="74566-336">ICorDebugRemoteTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-336">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 <span data-ttu-id="74566-337">Poskytuje metody umožňující ladit aplikace programu Silverlight v prostředí CLR.</span><span class="sxs-lookup"><span data-stu-id="74566-337">Provides methods that enable you to debug Silverlight-based applications in the CLR environment.</span></span>  
  
 [<span data-ttu-id="74566-338">ICorDebugRuntimeUnwindableFrame – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-338">ICorDebugRuntimeUnwindableFrame Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugruntimeunwindableframe-interface.md)  
 <span data-ttu-id="74566-339">Poskytuje podporu pro nespravované metody, které vyžadují modul CLR k uvolnění rámce.</span><span class="sxs-lookup"><span data-stu-id="74566-339">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
 [<span data-ttu-id="74566-340">ICorDebugStackWalk – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-340">ICorDebugStackWalk Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)  
 <span data-ttu-id="74566-341">Poskytuje metody pro získání spravovaných metod nebo rámců v zásobníku vlákna.</span><span class="sxs-lookup"><span data-stu-id="74566-341">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
 [<span data-ttu-id="74566-342">ICorDebugStaticFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-342">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 <span data-ttu-id="74566-343">Představuje informací symbolů ladění pro statické pole.</span><span class="sxs-lookup"><span data-stu-id="74566-343">Represents the debug symbol information for a static field.</span></span> <span data-ttu-id="74566-344">**K dispozici na pouze .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="74566-344">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="74566-345">ICorDebugStepper – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-345">ICorDebugStepper Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-interface.md)  
 <span data-ttu-id="74566-346">Představuje krok ve spuštění kódu, který je prováděn pomocí ladicího programu, slouží jako identifikátor mezi vydáním a dokončením příkazu a umožňuje krok zrušit.</span><span class="sxs-lookup"><span data-stu-id="74566-346">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
 [<span data-ttu-id="74566-347">ICorDebugStepper2 – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-347">ICorDebugStepper2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-interface1.md)  
 <span data-ttu-id="74566-348">Poskytuje podporu ladění Pouze můj kód (JMC).</span><span class="sxs-lookup"><span data-stu-id="74566-348">Provides support for Just My Code (JMC) debugging.</span></span>  
  
 [<span data-ttu-id="74566-349">ICorDebugStepperEnum – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-349">ICorDebugStepperEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepperenum-interface.md)  
 <span data-ttu-id="74566-350">Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugStepper` pole.</span><span class="sxs-lookup"><span data-stu-id="74566-350">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugStepper` arrays.</span></span>  
  
 [<span data-ttu-id="74566-351">ICorDebugStringValue – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-351">ICorDebugStringValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-interface.md)  
 <span data-ttu-id="74566-352">Podtřída `ICorDebugHeapValue` aplikovaná na řetězcové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="74566-352">A subclass of `ICorDebugHeapValue` that applies to string values.</span></span>  
  
 [<span data-ttu-id="74566-353">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-353">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 <span data-ttu-id="74566-354">Poskytuje metody, které slouží k načtení informací symbolů ladění.</span><span class="sxs-lookup"><span data-stu-id="74566-354">Provides methods that can be used to retrieve debug symbol information.</span></span> <span data-ttu-id="74566-355">**K dispozici na pouze .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="74566-355">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="74566-356">ICorDebugSymbolProvider2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-356">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 <span data-ttu-id="74566-357">Logicky rozšiřuje [icordebugsymbolprovider –](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) rozhraní pro načtení informací o symbolu další ladění.</span><span class="sxs-lookup"><span data-stu-id="74566-357">Logically extends the [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span> <span data-ttu-id="74566-358">**K dispozici na pouze .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="74566-358">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="74566-359">ICorDebugThread – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-359">ICorDebugThread Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-interface.md)  
 <span data-ttu-id="74566-360">Představuje vlákno v procesu.</span><span class="sxs-lookup"><span data-stu-id="74566-360">Represents a thread in a process.</span></span> <span data-ttu-id="74566-361">Životnost `ICorDebugThread` instance je stejná jako životnost vlákna, které představuje.</span><span class="sxs-lookup"><span data-stu-id="74566-361">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
 [<span data-ttu-id="74566-362">ICorDebugThread2 – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-362">ICorDebugThread2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interface.md)  
 <span data-ttu-id="74566-363">Slouží jako logické rozšíření pro `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="74566-363">Serves as a logical extension to `ICorDebugThread`.</span></span>  
  
 [<span data-ttu-id="74566-364">ICorDebugThread3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-364">ICorDebugThread3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md)  
 <span data-ttu-id="74566-365">Poskytuje vstupní bod, který [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) a odpovídající rozhraní.</span><span class="sxs-lookup"><span data-stu-id="74566-365">Provides the entry point to the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
 [<span data-ttu-id="74566-366">ICorDebugThread4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-366">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 <span data-ttu-id="74566-367">Poskytuje informace o blokování vlákna.</span><span class="sxs-lookup"><span data-stu-id="74566-367">Provides thread blocking information.</span></span>  
  
 [<span data-ttu-id="74566-368">ICorDebugThreadEnum – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-368">ICorDebugThreadEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthreadenum-interface1.md)  
 <span data-ttu-id="74566-369">Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugThread` pole.</span><span class="sxs-lookup"><span data-stu-id="74566-369">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugThread` arrays.</span></span>  
  
 [<span data-ttu-id="74566-370">ICorDebugType – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-370">ICorDebugType Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md)  
 <span data-ttu-id="74566-371">Představuje typ, který může být základní nebo komplexní (tj. definovaný uživatelem).</span><span class="sxs-lookup"><span data-stu-id="74566-371">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="74566-372">Pokud je typ obecný, `ICorDebugType` představuje obecný typ s instancemi.</span><span class="sxs-lookup"><span data-stu-id="74566-372">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
 [<span data-ttu-id="74566-373">ICorDebugType2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-373">ICorDebugType2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)  
 <span data-ttu-id="74566-374">Rozšiřuje [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) rozhraní načtete identifikátor typu základního typu nebo komplexní typ (definovaný uživatelem).</span><span class="sxs-lookup"><span data-stu-id="74566-374">Extends the [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
 [<span data-ttu-id="74566-375">ICorDebugTypeEnum – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="74566-375">ICorDebugTypeEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtypeenum-interface.md)  
 <span data-ttu-id="74566-376">Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugType` pole.</span><span class="sxs-lookup"><span data-stu-id="74566-376">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugType` arrays.</span></span>  
  
 [<span data-ttu-id="74566-377">ICorDebugUnmanagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-377">ICorDebugUnmanagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)  
 <span data-ttu-id="74566-378">Poskytuje oznámení nativních událostí, které přímo nesouvisejí s CLR.</span><span class="sxs-lookup"><span data-stu-id="74566-378">Provides notification of native events that are not directly related to the CLR.</span></span>  
  
 <span data-ttu-id="74566-379">"ICorDebugValue"</span><span class="sxs-lookup"><span data-stu-id="74566-379">"ICorDebugValue"</span></span>  
 <span data-ttu-id="74566-380">Představuje hodnotu pro čtení nebo zápis v laděném procesu.</span><span class="sxs-lookup"><span data-stu-id="74566-380">Represents a read or write value in the process being debugged.</span></span>  
  
 <span data-ttu-id="74566-381">Icordebugvalue2 "–"</span><span class="sxs-lookup"><span data-stu-id="74566-381">"ICorDebugValue2"</span></span>  
 <span data-ttu-id="74566-382">Rozšiřuje `ICorDebugValue` k poskytování podpory pro `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="74566-382">Extends `ICorDebugValue` to provide support for `ICorDebugType`.</span></span>  
  
 [<span data-ttu-id="74566-383">ICorDebugValue3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-383">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)  
 <span data-ttu-id="74566-384">Rozšiřuje rozhraní "ICorDebugValue" a "ICorDebugValue2" k poskytování podpory pro pole, která jsou větší než 2 GB.</span><span class="sxs-lookup"><span data-stu-id="74566-384">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
 <span data-ttu-id="74566-385">Icordebugvaluebreakpoint "–"</span><span class="sxs-lookup"><span data-stu-id="74566-385">"ICorDebugValueBreakpoint"</span></span>  
 <span data-ttu-id="74566-386">Rozšiřuje `ICorDebugBreakpoint` a zajistit tak přístup k určitým hodnotám.</span><span class="sxs-lookup"><span data-stu-id="74566-386">Extends `ICorDebugBreakpoint` to provide access to specific values.</span></span>  
  
 <span data-ttu-id="74566-387">Icordebugvalueenum "–"</span><span class="sxs-lookup"><span data-stu-id="74566-387">"ICorDebugValueEnum"</span></span>  
 <span data-ttu-id="74566-388">Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugValue` pole.</span><span class="sxs-lookup"><span data-stu-id="74566-388">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugValue` arrays.</span></span>  
  
 [<span data-ttu-id="74566-389">ICorDebugVariableHome – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-389">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)  
 <span data-ttu-id="74566-390">Představuje místní proměnné nebo argumentu funkce.</span><span class="sxs-lookup"><span data-stu-id="74566-390">Represents a local variable or argument of a function.</span></span>  
  
 [<span data-ttu-id="74566-391">ICorDebugVariableHomeEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-391">ICorDebugVariableHomeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
 <span data-ttu-id="74566-392">Poskytuje enumerátor pro místní proměnné a argumenty ve funkci.</span><span class="sxs-lookup"><span data-stu-id="74566-392">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
 [<span data-ttu-id="74566-393">ICorDebugVariableSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-393">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 <span data-ttu-id="74566-394">Načte informace o symbolu ladění pro proměnnou.</span><span class="sxs-lookup"><span data-stu-id="74566-394">Retrieves the debug symbol information for a variable.</span></span> <span data-ttu-id="74566-395">**K dispozici na pouze .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="74566-395">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="74566-396">ICorDebugVirtualUnwinder – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-396">ICorDebugVirtualUnwinder Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-interface.md)  
 <span data-ttu-id="74566-397">Poskytuje metody, které vám pomůžou odvíjení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="74566-397">Provides methods to help in stack unwinding.</span></span> <span data-ttu-id="74566-398">**K dispozici na pouze .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="74566-398">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="74566-399">ICorPublish – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-399">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)  
 <span data-ttu-id="74566-400">Slouží jako obecné rozhraní pro procesy publikování.</span><span class="sxs-lookup"><span data-stu-id="74566-400">Serves as the general interface for the publishing processes.</span></span>  
  
 [<span data-ttu-id="74566-401">ICorPublishAppDomain – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-401">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)  
 <span data-ttu-id="74566-402">Představuje a poskytuje informace o aplikační doméně.</span><span class="sxs-lookup"><span data-stu-id="74566-402">Represents and provides information about an application domain.</span></span>  
  
 [<span data-ttu-id="74566-403">ICorPublishAppDomainEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-403">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
 <span data-ttu-id="74566-404">Poskytuje metody, které procházejí kolekci `ICorPublishAppDomain` objekty, které momentálně existují v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="74566-404">Provides methods that traverse a collection of `ICorPublishAppDomain` objects that currently exist within a process.</span></span>  
  
 [<span data-ttu-id="74566-405">ICorPublishEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-405">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)  
 <span data-ttu-id="74566-406">Slouží jako abstraktní základ pro enumerátory publikování.</span><span class="sxs-lookup"><span data-stu-id="74566-406">Serves as the abstract base for publishing enumerators.</span></span>  
  
 [<span data-ttu-id="74566-407">ICorPublishProcess – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-407">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)  
 <span data-ttu-id="74566-408">Poskytuje metody, které přistupují k informacím o procesu.</span><span class="sxs-lookup"><span data-stu-id="74566-408">Provides methods that access information about a process.</span></span>  
  
 [<span data-ttu-id="74566-409">ICorPublishProcessEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74566-409">ICorPublishProcessEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
 <span data-ttu-id="74566-410">Poskytuje metody, které procházejí kolekci `ICorPublishProcess` objekty.</span><span class="sxs-lookup"><span data-stu-id="74566-410">Provides methods that traverse a collection of `ICorPublishProcess` objects.</span></span>  

 <span data-ttu-id="74566-411">[Rozhraní ISOSDacInterface](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-interface.md) poskytuje pomocné metody pro přístup k datům z `SOS`.</span><span class="sxs-lookup"><span data-stu-id="74566-411">[ISOSDacInterface Interface](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-interface.md) Provides helper methods to access data from `SOS`.</span></span>

 <span data-ttu-id="74566-412">[Rozhraní IXCLRDataMethodDefinition](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md) poskytuje metody pro dotazování na informace o definici metody.</span><span class="sxs-lookup"><span data-stu-id="74566-412">[IXCLRDataMethodDefinition Interface](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md) Provides methods for querying information about a method definition.</span></span>
 
 <span data-ttu-id="74566-413">[Rozhraní IXCLRDataMethodInstance](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-interface.md) poskytuje metody pro dotazování na informace o metodu instance.</span><span class="sxs-lookup"><span data-stu-id="74566-413">[IXCLRDataMethodInstance Interface](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-interface.md) Provides methods for querying information about a method instance.</span></span>
 
 <span data-ttu-id="74566-414">[Rozhraní IXCLRDataModule](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-interface.md) poskytuje metody pro dotazování na informace o u načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="74566-414">[IXCLRDataModule Interface](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-interface.md) Provides methods for querying information about a loaded module.</span></span>
 
 <span data-ttu-id="74566-415">[Rozhraní IXCLRDataProcess](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md) poskytuje metody pro dotazování na informace o procesu.</span><span class="sxs-lookup"><span data-stu-id="74566-415">[IXCLRDataProcess Interface](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md) Provides methods for querying information about a process.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="74566-416">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="74566-416">Related Sections</span></span>  
 [<span data-ttu-id="74566-417">Třídy typu coclass pro ladění</span><span class="sxs-lookup"><span data-stu-id="74566-417">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="74566-418">Globální statické funkce pro ladění</span><span class="sxs-lookup"><span data-stu-id="74566-418">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [<span data-ttu-id="74566-419">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="74566-419">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [<span data-ttu-id="74566-420">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="74566-420">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
