---
title: Debugging – rozhraní
ms.date: 02/07/2019
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d939063aaefb00d4db3de604df0dbd1b2175bf95
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981605"
---
# <a name="debugging-interfaces"></a><span data-ttu-id="7c1eb-102">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7c1eb-102">Debugging Interfaces</span></span>
<span data-ttu-id="7c1eb-103">Tato část popisuje nespravovaná rozhraní, která zpracovávají ladění programu, který je spouštěn v modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-103">This section describes the unmanaged interfaces that handle the debugging of a program that is executing in the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7c1eb-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="7c1eb-104">In This Section</span></span>  
 <span data-ttu-id="7c1eb-105">[ICLRDataEnumMemoryRegions Interface](iclrdataenummemoryregions-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-105">[ICLRDataEnumMemoryRegions Interface](iclrdataenummemoryregions-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-106">Představuje způsob, jak vytvořit výčet oblastí paměti zadaných volajícími.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-106">Provides a method to enumerate regions of memory that are specified by callers.</span></span>  
  
 <span data-ttu-id="7c1eb-107">[ICLRDataEnumMemoryRegionsCallback Interface](iclrdataenummemoryregionscallback-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-107">[ICLRDataEnumMemoryRegionsCallback Interface](iclrdataenummemoryregionscallback-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-108">Poskytuje metodu zpětného volání pro `EnumMemoryRegions` k poskytnutí zprávy ladicímu programu, výsledek pokusu o výčet určité oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-108">Provides a callback method for `EnumMemoryRegions` to report to the debugger, the result of an attempt to enumerate a specified region of memory.</span></span>  
  
 <span data-ttu-id="7c1eb-109">[Iclrdatatarget – rozhraní](iclrdatatarget-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-109">[ICLRDataTarget Interface](iclrdatatarget-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-110">Poskytuje metody pro interakci s cílovým procesem CLR.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-110">Provides methods for interaction with a target CLR process.</span></span>  
  
 <span data-ttu-id="7c1eb-111">[ICLRDataTarget2 Interface](iclrdatatarget2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-111">[ICLRDataTarget2 Interface](iclrdatatarget2-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-112">Podtřída `ICLRDataTarget` vrstvou služeb přístupu k data, která se používá k manipulaci s oblastmi virtuální paměti v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-112">A subclass of `ICLRDataTarget` that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
 <span data-ttu-id="7c1eb-113">[ICLRDataTarget3 Interface](iclrdatatarget3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-113">[ICLRDataTarget3 Interface](iclrdatatarget3-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-114">Podtřída [iclrdatatarget2 –](iclrdatatarget2-interface.md) , která poskytuje přístup k informacím o výjimce.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-114">A subclass of [ICLRDataTarget2](iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
 <span data-ttu-id="7c1eb-115">[Iclrdebugging – rozhraní](iclrdebugging-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-115">[ICLRDebugging Interface](iclrdebugging-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-116">Poskytuje metody, které zpracovávají načítání a uvolňování modulů pro ladění.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-116">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
 <span data-ttu-id="7c1eb-117">[Iclrdebugginglibraryprovider – rozhraní](iclrdebugginglibraryprovider-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-117">[ICLRDebuggingLibraryProvider Interface](iclrdebugginglibraryprovider-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-118">Zahrnuje [ProvideLibrary – metoda](iclrdebugginglibraryprovider-providelibrary-method.md) metodu, která získá rozhraní zpětného volání, které umožňuje knihovnám ladění specifickým pro verzi modulu runtime k vyhledání a načtení na požádání zprostředkovatele knihovny.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-118">Includes the [ProvideLibrary Method](iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
 <span data-ttu-id="7c1eb-119">[ICLRMetadataLocator Interface](iclrmetadatalocator-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-119">[ICLRMetadataLocator Interface](iclrmetadatalocator-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-120">Rozhraní používané vrstvou služeb přístupu k datům k vyhledání metadat sestavení v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-120">Interface used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
 <span data-ttu-id="7c1eb-121">[Icordebug – rozhraní](icordebug-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-121">[ICorDebug Interface](icordebug-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-122">Poskytuje metody, které umožňují vývojářům ladit aplikace v prostředí CLR.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-122">Provides methods that allow developers to debug applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="7c1eb-123">[ICorDebugAppDomain Interface](icordebugappdomain-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-123">[ICorDebugAppDomain Interface](icordebugappdomain-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-124">Poskytuje metody pro ladění domén aplikace.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-124">Provides methods for debugging application domains.</span></span>  
  
 <span data-ttu-id="7c1eb-125">[ICorDebugAppDomain2 Interface](icordebugappdomain2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-125">[ICorDebugAppDomain2 Interface](icordebugappdomain2-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-126">Poskytuje metody pro práci s poli, ukazateli, ukazateli na funkci a typy ByRef.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-126">Provides methods to work with arrays, pointers, function pointers, and ByRef types.</span></span> <span data-ttu-id="7c1eb-127">Toto rozhraní je rozšířením `ICorDebugAppDomain` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-127">This interface is an extension of the `ICorDebugAppDomain` interface.</span></span>  
  
 <span data-ttu-id="7c1eb-128">[ICorDebugAppDomain3 Interface](icordebugappdomain3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-128">[ICorDebugAppDomain3 Interface](icordebugappdomain3-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-129">Poskytuje metody pro práci s [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typy v aplikační doméně.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-129">Provides methods to work with the [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types in an application domain.</span></span> <span data-ttu-id="7c1eb-130">Toto rozhraní je rozšířením `ICorDebugAppDomain` a `ICorDebugAppDomain2` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-130">This interface is an extension of the `ICorDebugAppDomain` and `ICorDebugAppDomain2` interfaces.</span></span>  
  
 <span data-ttu-id="7c1eb-131">[ICorDebugAppDomain4 Interface](icordebugappdomain4-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-131">[ICorDebugAppDomain4 Interface](icordebugappdomain4-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-132">Logicky rozšiřuje [ICorDebugAppDomain](icordebugappdomain-interface.md) získat objekt spravovaného z obálka volatelná aplikacemi COM rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-132">Logically extends the [ICorDebugAppDomain](icordebugappdomain-interface.md) interface to get a managed object from a COM callable wrapper.</span></span>  
  
 <span data-ttu-id="7c1eb-133">[ICorDebugAppDomainEnum Interface](icordebugappdomainenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-133">[ICorDebugAppDomainEnum Interface](icordebugappdomainenum-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-134">Poskytuje metodu, která vrací zadaný počet `ICorDebugAppDomain` hodnot počínaje na dalším místě ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-134">Provides a method that returns a specified number of `ICorDebugAppDomain` values starting at the next location in the enumeration.</span></span>  
  
 <span data-ttu-id="7c1eb-135">[ICorDebugArrayValue Interface](icordebugarrayvalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-135">[ICorDebugArrayValue Interface](icordebugarrayvalue-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-136">Podtřída `ICorDebugHeapValue` , která představuje jednorozměrné nebo vícedimenzionální pole.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-136">A subclass of `ICorDebugHeapValue` that represents a single-dimensional or multi-dimensional array.</span></span>  
  
 <span data-ttu-id="7c1eb-137">[Icordebugassembly – rozhraní](icordebugassembly-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-137">[ICorDebugAssembly Interface](icordebugassembly-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-138">Představuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-138">Represents an assembly.</span></span>  
  
 <span data-ttu-id="7c1eb-139">[Icordebugassembly2 – rozhraní](icordebugassembly2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-139">[ICorDebugAssembly2 Interface](icordebugassembly2-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-140">Představuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-140">Represents an assembly.</span></span> <span data-ttu-id="7c1eb-141">Toto rozhraní je rozšířením `ICorDebugAssembly` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-141">This interface is an extension of the `ICorDebugAssembly` interface.</span></span>  
  
 <span data-ttu-id="7c1eb-142">[Icordebugassembly3 – rozhraní](icordebugassembly3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-142">[ICorDebugAssembly3 Interface](icordebugassembly3-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-143">Logicky rozšiřuje [ICorDebugAssembly](icordebugassembly-interface.md) rozhraní k poskytování podpory pro sestavení kontejneru a jejich obsažené sestavení.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-143">Logically extends the [ICorDebugAssembly](icordebugassembly-interface.md) interface to provide support for container assemblies and their contained assemblies.</span></span> <span data-ttu-id="7c1eb-144">**K dispozici na pouze .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="7c1eb-144">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="7c1eb-145">[Icordebugassemblyenum – rozhraní](icordebugassemblyenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-145">[ICorDebugAssemblyEnum Interface](icordebugassemblyenum-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-146">Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugAssembly` pole.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-146">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugAssembly` arrays.</span></span>  
  
 <span data-ttu-id="7c1eb-147">[Icordebugblockingobjectenum – rozhraní](icordebugblockingobjectenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-147">[ICorDebugBlockingObjectEnum Interface](icordebugblockingobjectenum-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-148">Poskytuje enumerátor pro seznam [CorDebugBlockingObject](cordebugblockingobject-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-148">Provides an enumerator for a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
 <span data-ttu-id="7c1eb-149">[Icordebugboxvalue – rozhraní](icordebugboxvalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-149">[ICorDebugBoxValue Interface](icordebugboxvalue-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-150">Podtřída `ICorDebugHeapValue` představující objektu třídy zabalených hodnot.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-150">A subclass of `ICorDebugHeapValue` that represents a boxed value class object.</span></span>  
  
 <span data-ttu-id="7c1eb-151">[Icordebugbreakpoint – rozhraní](icordebugbreakpoint-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-151">[ICorDebugBreakpoint Interface](icordebugbreakpoint-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-152">Představuje zarážku ve funkci nebo bod sledování na hodnotě.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-152">Represents a breakpoint in a function or a watch point on a value.</span></span>  
  
 <span data-ttu-id="7c1eb-153">[Icordebugbreakpointenum – rozhraní](icordebugbreakpointenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-153">[ICorDebugBreakpointEnum Interface](icordebugbreakpointenum-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-154">Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugBreakpoint` pole.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-154">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugBreakpoint` arrays.</span></span>  
  
 <span data-ttu-id="7c1eb-155">[Icordebugchain – rozhraní](icordebugchain-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-155">[ICorDebugChain Interface](icordebugchain-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-156">Představuje segment fyzického nebo logického zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-156">Represents a segment of a physical or logical call stack.</span></span>  
  
 <span data-ttu-id="7c1eb-157">[Icordebugchainenum – rozhraní](icordebugchainenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-157">[ICorDebugChainEnum Interface](icordebugchainenum-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-158">Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugChain` pole.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-158">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugChain` arrays.</span></span>  
  
 <span data-ttu-id="7c1eb-159">[Icordebugclass – rozhraní](icordebugclass-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-159">[ICorDebugClass Interface](icordebugclass-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-160">Představuje typ, který může být základní nebo komplexní (tj. definovaný uživatelem).</span><span class="sxs-lookup"><span data-stu-id="7c1eb-160">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="7c1eb-161">Pokud je typ obecný, `ICorDebugClass` představuje obecný typ bez instancí.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-161">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
 <span data-ttu-id="7c1eb-162">[Icordebugclass2 – rozhraní](icordebugclass2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-162">[ICorDebugClass2 Interface](icordebugclass2-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-163">Představuje obecnou třídu nebo třídu s parametrem metody typu <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-163">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="7c1eb-164">Toto rozhraní rozšiřuje `ICorDebugClass`.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-164">This interface extends `ICorDebugClass`.</span></span>  
  
 <span data-ttu-id="7c1eb-165">[Icordebugcode – rozhraní](icordebugcode-interface1.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-165">[ICorDebugCode Interface](icordebugcode-interface1.md)\\</span></span>
 <span data-ttu-id="7c1eb-166">Představuje segment kódu jazyka MSIL nebo nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-166">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
 <span data-ttu-id="7c1eb-167">[Icordebugcode2 – rozhraní](icordebugcode2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-167">[ICorDebugCode2 Interface](icordebugcode2-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-168">Poskytuje metody, které rozšiřují možnosti `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-168">Provides methods that extend the capabilities of `ICorDebugCode`.</span></span>  
  
 <span data-ttu-id="7c1eb-169">[Icordebugcode3 – rozhraní](icordebugcode3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-169">[ICorDebugCode3 Interface](icordebugcode3-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-170">Poskytuje metodu, která rozšiřuje [ICorDebugCode](icordebugcode-interface1.md) a [ICorDebugCode2](icordebugcode2-interface.md) zadání informací o spravované návratové hodnotě.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-170">Provides a method that extends [ICorDebugCode](icordebugcode-interface1.md) and [ICorDebugCode2](icordebugcode2-interface.md) to provide information about a managed return value.</span></span>  
  
 <span data-ttu-id="7c1eb-171">[Icordebugcode4 – rozhraní](icordebugcode4-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-171">[ICorDebugCode4 Interface](icordebugcode4-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-172">Poskytuje metodu, která umožňuje ladicí program, který výčet lokálních proměnných a argumentů funkce.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-172">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="7c1eb-173">[Icordebugcodeenum – rozhraní](icordebugcodeenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-173">[ICorDebugCodeEnum Interface](icordebugcodeenum-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-174">Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugCode` pole.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-174">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugCode` arrays.</span></span>  
  
 <span data-ttu-id="7c1eb-175">[ICorDebugComObjectValue Interface](icordebugcomobjectvalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-175">[ICorDebugComObjectValue Interface](icordebugcomobjectvalue-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-176">Poskytuje metody pro načtení objektů z mezipaměti rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-176">Provides methods to retrieve cached interface objects.</span></span>  
  
 <span data-ttu-id="7c1eb-177">[ICorDebugContext Interface](icordebugcontext-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-177">[ICorDebugContext Interface](icordebugcontext-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-178">Představuje objekt kontextu.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-178">Represents a context object.</span></span> <span data-ttu-id="7c1eb-179">Toto rozhraní zatím nebylo implementováno.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-179">This interface has not been implemented yet.</span></span>  
  
 <span data-ttu-id="7c1eb-180">[Icordebugcontroller – rozhraní](icordebugcontroller-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-180">[ICorDebugController Interface](icordebugcontroller-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-181">Představuje rozsah buď <xref:System.Diagnostics.Process> nebo <xref:System.AppDomain>, ve které provádění kódu lze ovládat kontext.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-181">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
 <span data-ttu-id="7c1eb-182">[Icordebugdatatarget – rozhraní](icordebugdatatarget-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-182">[ICorDebugDataTarget Interface](icordebugdatatarget-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-183">Poskytuje rozhraní zpětného volání, které poskytuje přístup ke konkrétnímu cílovému procesu.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-183">Provides a callback interface that provides access to a particular target process.</span></span>  
  
 <span data-ttu-id="7c1eb-184">[ICorDebugDataTarget2 Interface](icordebugdatatarget2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-184">[ICorDebugDataTarget2 Interface](icordebugdatatarget2-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-185">Logicky rozšiřuje [icordebugdatatarget –](icordebugdatatarget-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-185">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="7c1eb-186">**K dispozici na pouze .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="7c1eb-186">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="7c1eb-187">[ICorDebugDataTarget3 Interface](icordebugdatatarget3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-187">[ICorDebugDataTarget3 Interface](icordebugdatatarget3-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-188">Logicky rozšiřuje [icordebugdatatarget –](icordebugdatatarget-interface.md) rozhraní pro zadání informací o načtené moduly.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-188">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span> <span data-ttu-id="7c1eb-189">**K dispozici na pouze .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="7c1eb-189">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="7c1eb-190">[Icordebugdebugevent – rozhraní](icordebugdebugevent-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-190">[ICorDebugDebugEvent Interface](icordebugdebugevent-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-191">Definuje základní rozhraní, ze kterého jsou všechny `ICorDebug` výjimky ladění jsou odvozeny.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-191">Defines the base interface from which all `ICorDebug` debug events derive.</span></span> <span data-ttu-id="7c1eb-192">**K dispozici na pouze .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="7c1eb-192">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="7c1eb-193">[ICorDebugEditAndContinueErrorInfo Interface](icordebugeditandcontinueerrorinfo-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-193">[ICorDebugEditAndContinueErrorInfo Interface](icordebugeditandcontinueerrorinfo-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-194">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-194">Obsolete.</span></span> <span data-ttu-id="7c1eb-195">Toto rozhraní nepoužívejte.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-195">Do not use this interface.</span></span>  
  
 <span data-ttu-id="7c1eb-196">[ICorDebugEditAndContinueSnapshot Interface](icordebugeditandcontinuesnapshot-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-196">[ICorDebugEditAndContinueSnapshot Interface](icordebugeditandcontinuesnapshot-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-197">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-197">Obsolete.</span></span> <span data-ttu-id="7c1eb-198">Toto rozhraní nepoužívejte.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-198">Do not use this interface.</span></span>  
  
 <span data-ttu-id="7c1eb-199">[Icordebugenum – rozhraní](icordebugenum-interface1.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-199">[ICorDebugEnum Interface](icordebugenum-interface1.md)\\</span></span>
 <span data-ttu-id="7c1eb-200">Slouží jako abstraktní základní rozhraní pro enumerátory ladění.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-200">Serves as the abstract base interface for debugging enumerators.</span></span>  
  
 <span data-ttu-id="7c1eb-201">[Icordebugerrorinfoenum – rozhraní](icordebugerrorinfoenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-201">[ICorDebugErrorInfoEnum Interface](icordebugerrorinfoenum-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-202">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-202">Obsolete.</span></span> <span data-ttu-id="7c1eb-203">Toto rozhraní nepoužívejte.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-203">Do not use this interface.</span></span>  
  
 <span data-ttu-id="7c1eb-204">[Icordebugeval – rozhraní](icordebugeval-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-204">[ICorDebugEval Interface](icordebugeval-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-205">Poskytuje metody povolující ladicímu programu spouštět kód v kontextu laděného kódu.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-205">Provides methods to enable the debugger to execute code within the context of the code being debugged.</span></span>  
  
 <span data-ttu-id="7c1eb-206">[Icordebugeval2 – rozhraní](icordebugeval2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-206">[ICorDebugEval2 Interface](icordebugeval2-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-207">Rozšiřuje `ICorDebugEval` k poskytování podpory pro obecné typy.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-207">Extends `ICorDebugEval` to provide support for generic types.</span></span>  
  
 <span data-ttu-id="7c1eb-208">[Icordebugexceptiondebugevent – rozhraní](icordebugexceptiondebugevent-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-208">[ICorDebugExceptionDebugEvent Interface](icordebugexceptiondebugevent-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-209">Rozšiřuje [ICorDebugDebugEvent](icordebugdebugevent-interface.md) rozhraní pro podporu události výjimky.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-209">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support exception events.</span></span> <span data-ttu-id="7c1eb-210">**K dispozici na pouze .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="7c1eb-210">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="7c1eb-211">[Icordebugexceptionobjectcallstackenum – rozhraní](icordebugexceptionobjectcallstackenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-211">[ICorDebugExceptionObjectCallStackEnum Interface](icordebugexceptionobjectcallstackenum-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-212">Poskytuje enumerátor pro informace zásobníku volání, který je vložený v objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-212">Provides an enumerator for call stack information that is embedded in an exception object.</span></span>  
  
 <span data-ttu-id="7c1eb-213">[ICorDebugExceptionObjectValue Interface](icordebugexceptionobjectvalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-213">[ICorDebugExceptionObjectValue Interface](icordebugexceptionobjectvalue-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-214">Rozšiřuje [ICorDebugObjectValue](icordebugobjectvalue-interface.md) rozhraní pro poskytnutí informací o trasování zásobníku z objektu spravované výjimky.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-214">Extends the [ICorDebugObjectValue](icordebugobjectvalue-interface.md) interface to provide stack trace information from a managed exception object.</span></span>  
  
 <span data-ttu-id="7c1eb-215">[Icordebugframe – rozhraní](icordebugframe-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-215">[ICorDebugFrame Interface](icordebugframe-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-216">Představuje snímek aktuálního zásobníku.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-216">Represents a frame on the current stack.</span></span>  
  
 <span data-ttu-id="7c1eb-217">[Icordebugframeenum – rozhraní](icordebugframeenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-217">[ICorDebugFrameEnum Interface](icordebugframeenum-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-218">Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugFrame` pole.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-218">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugFrame` arrays.</span></span>  
  
 <span data-ttu-id="7c1eb-219">[Icordebugfunction – rozhraní](icordebugfunction-interface1.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-219">[ICorDebugFunction Interface](icordebugfunction-interface1.md)\\</span></span>
 <span data-ttu-id="7c1eb-220">Představuje spravovanou funkci nebo metodu.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-220">Represents a managed function or method.</span></span>  
  
 <span data-ttu-id="7c1eb-221">[Icordebugfunction2 – rozhraní](icordebugfunction2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-221">[ICorDebugFunction2 Interface](icordebugfunction2-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-222">Logicky rozšiřuje `ICorDebugFunction` a poskytuje podporu pro funkce pouze můj kód krokové ladění.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-222">Logically extends `ICorDebugFunction` to provide support for Just My Code step-through debugging.</span></span>  
  
 <span data-ttu-id="7c1eb-223">[Icordebugfunction3 – rozhraní](icordebugfunction3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-223">[ICorDebugFunction3 Interface](icordebugfunction3-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-224">Logicky rozšiřuje [ICorDebugFunction](icordebugfunction-interface1.md) rozhraní pro žádost o ReJIT poskytují přístup ke kódu.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-224">Logically extends the [ICorDebugFunction](icordebugfunction-interface1.md) interface to provide access to code from a ReJIT request.</span></span>  
  
 <span data-ttu-id="7c1eb-225">[Icordebugfunctionbreakpoint – rozhraní](icordebugfunctionbreakpoint-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-225">[ICorDebugFunctionBreakpoint Interface](icordebugfunctionbreakpoint-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-226">Rozšiřuje `ICorDebugBreakpoint` pro podporu zarážek v rámci funkcí.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-226">Extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
 <span data-ttu-id="7c1eb-227">[Icordebuggcreferenceenum – rozhraní](icordebuggcreferenceenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-227">[ICorDebugGCReferenceEnum Interface](icordebuggcreferenceenum-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-228">Poskytuje enumerátor pro objekty, které budou uvolněny z paměti.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-228">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
 <span data-ttu-id="7c1eb-229">[Icordebuggenericvalue – rozhraní](icordebuggenericvalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-229">[ICorDebugGenericValue Interface](icordebuggenericvalue-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-230">Podtřída `ICorDebugValue` , která platí pro všechny hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-230">A subclass of `ICorDebugValue` that applies to all values.</span></span> <span data-ttu-id="7c1eb-231">Toto rozhraní poskytuje metody Get a Set pro hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-231">This interface provides Get and Set methods for the value.</span></span>  
  
 <span data-ttu-id="7c1eb-232">[Icordebugguidtotypeenum – rozhraní](icordebugguidtotypeenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-232">[ICorDebugGuidToTypeEnum Interface](icordebugguidtotypeenum-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-233">Poskytuje enumerátor pro objekt, který mapuje identifikátory GUID a odpovídající `ICorDebugType` objekty.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-233">Provides an enumerator for an object that maps GUIDs and their corresponding `ICorDebugType` objects.</span></span>  
  
 <span data-ttu-id="7c1eb-234">[Icordebughandlevalue – rozhraní](icordebughandlevalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-234">[ICorDebugHandleValue Interface](icordebughandlevalue-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-235">Podtřída `ICorDebugReferenceValue` , která představuje referenční hodnotu, do které ladicí program vytvořil popisovač pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-235">A subclass of `ICorDebugReferenceValue` that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
 <span data-ttu-id="7c1eb-236">[Icordebugheapenum – rozhraní](icordebugheapenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-236">[ICorDebugHeapEnum Interface](icordebugheapenum-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-237">Poskytuje enumerátor pro objekty na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-237">Provides an enumerator for objects on the managed heap.</span></span>  
  
 <span data-ttu-id="7c1eb-238">[Icordebugheapsegmentenum – rozhraní](icordebugheapsegmentenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-238">[ICorDebugHeapSegmentEnum Interface](icordebugheapsegmentenum-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-239">Poskytuje enumerátor pro oblasti paměti spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-239">Provides an enumerator for the memory regions of the managed heap.</span></span>  
  
 <span data-ttu-id="7c1eb-240">[Icordebugheapvalue – rozhraní](icordebugheapvalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-240">[ICorDebugHeapValue Interface](icordebugheapvalue-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-241">Podtřída `ICorDebugValue` , který představuje objekt, který byl shromážděn uvolňováním CLR.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-241">A subclass of `ICorDebugValue` that represents an object that has been collected by the CLR garbage collector.</span></span>  
  
 <span data-ttu-id="7c1eb-242">[ICorDebugHeapValue2 Interface](icordebugheapvalue2-interface1.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-242">[ICorDebugHeapValue2 Interface](icordebugheapvalue2-interface1.md)\\</span></span>
 <span data-ttu-id="7c1eb-243">Rozšíření `ICorDebugHeapValue` , která poskytuje podporu pro popisovače modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-243">An extension of `ICorDebugHeapValue` that provides support for runtime handles.</span></span>  
  
 <span data-ttu-id="7c1eb-244">[ICorDebugHeapValue3 Interface](icordebugheapvalue3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-244">[ICorDebugHeapValue3 Interface](icordebugheapvalue3-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-245">Zpřístupní vlastnosti uzamčení sledování objektů.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-245">Exposes the monitor lock properties of objects.</span></span>  
  
 <span data-ttu-id="7c1eb-246">[Icordebugilcode – rozhraní](icordebugilcode-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-246">[ICorDebugILCode Interface](icordebugilcode-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-247">Představuje segment kódu (IL intermediate language).</span><span class="sxs-lookup"><span data-stu-id="7c1eb-247">Represents a segment of intermediate language (IL) code.</span></span>  
  
 <span data-ttu-id="7c1eb-248">[Icordebugilcode2 – rozhraní](icordebugilcode2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-248">[ICorDebugILCode2 Interface](icordebugilcode2-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-249">Logicky rozšiřuje [ICorDebugILCode](icordebugilcode-interface.md) rozhraní poskytuje metody, které vracejí token pro místní proměnné podpis funkce a, která mapují profiler instrumentované (IL intermediate language) kompenzuje původní metody IL posuny.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-249">Logically extends the [ICorDebugILCode](icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
 <span data-ttu-id="7c1eb-250">[Icordebugilframe – rozhraní](icordebugilframe-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-250">[ICorDebugILFrame Interface](icordebugilframe-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-251">Představuje rámec zásobníku kódu MSIL.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-251">Represents a stack frame of MSIL code.</span></span>  
  
 <span data-ttu-id="7c1eb-252">[Icordebugilframe2 – rozhraní](icordebugilframe2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-252">[ICorDebugILFrame2 Interface](icordebugilframe2-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-253">Logické rozšíření `ICorDebugILFrame`.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-253">A logical extension of `ICorDebugILFrame`.</span></span>  
  
 <span data-ttu-id="7c1eb-254">[Icordebugilframe3 – rozhraní](icordebugilframe3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-254">[ICorDebugILFrame3 Interface](icordebugilframe3-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-255">Poskytuje metodu, která zapouzdřuje vrácenou hodnotu funkce.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-255">Provides a method that encapsulates the return value of a function.</span></span>  
  
 <span data-ttu-id="7c1eb-256">[Icordebugilframe4 – rozhraní](icordebugilframe4-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-256">[ICorDebugILFrame4 Interface](icordebugilframe4-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-257">Poskytuje metody, které umožňují přístup k místní proměnné a kód v bloku zásobníku kódu (IL intermediate language).</span><span class="sxs-lookup"><span data-stu-id="7c1eb-257">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="7c1eb-258">Parametr určuje, zda ladicí program má přístup k proměnné a kód přidaný v profileru ReJIT instrumentace.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-258">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
 <span data-ttu-id="7c1eb-259">[ICorDebugInstanceFieldSymbol Interface](icordebuginstancefieldsymbol-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-259">[ICorDebugInstanceFieldSymbol Interface](icordebuginstancefieldsymbol-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-260">Představuje informací symbolů ladění pro pole instance.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-260">Represents the debug symbol information for an instance field.</span></span> <span data-ttu-id="7c1eb-261">**K dispozici na pouze .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="7c1eb-261">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="7c1eb-262">[Icordebuginternalframe – rozhraní](icordebuginternalframe-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-262">[ICorDebugInternalFrame Interface](icordebuginternalframe-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-263">Určuje typy rámců pro ladicí program.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-263">Identifies frame types for the debugger.</span></span>  
  
 <span data-ttu-id="7c1eb-264">[Icordebuginternalframe2 – rozhraní](icordebuginternalframe2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-264">[ICorDebugInternalFrame2 Interface](icordebuginternalframe2-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-265">Poskytuje informace o vnitřních rámcích, včetně adresy zásobníku a pozice ve vztahu k [ICorDebugFrame](icordebugframe-interface.md) objekty.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-265">Provides information about internal frames, including stack address and position in relation to [ICorDebugFrame](icordebugframe-interface.md) objects.</span></span>  
  
 <span data-ttu-id="7c1eb-266">[Icordebugloadedmodule – rozhraní](icordebugloadedmodule-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-266">[ICorDebugLoadedModule Interface](icordebugloadedmodule-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-267">Poskytuje informace o u načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-267">Provides information about a loaded module.</span></span> <span data-ttu-id="7c1eb-268">**K dispozici na pouze .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="7c1eb-268">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="7c1eb-269">[ICorDebugManagedCallback Interface](icordebugmanagedcallback-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-269">[ICorDebugManagedCallback Interface](icordebugmanagedcallback-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-270">Poskytuje metody pro zpětná volání procesu ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-270">Provides methods to process debugger callbacks.</span></span>  
  
 <span data-ttu-id="7c1eb-271">[ICorDebugManagedCallback2 Interface](icordebugmanagedcallback2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-271">[ICorDebugManagedCallback2 Interface](icordebugmanagedcallback2-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-272">Poskytuje metody pro podporu zpracování výjimek ladicího programu a spravované pomocníky ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="7c1eb-272">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="7c1eb-273">`ICorDebugManagedCallback2` je logickým rozšířením `ICorDebugManagedCallback`.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-273">`ICorDebugManagedCallback2` is a logical extension of `ICorDebugManagedCallback`.</span></span>  
  
 <span data-ttu-id="7c1eb-274">[ICorDebugManagedCallback3 Interface](icordebugmanagedcallback3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-274">[ICorDebugManagedCallback3 Interface](icordebugmanagedcallback3-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-275">Poskytuje metodu zpětného volání, která určuje, že povolené vlastní oznámení ladicího programu bylo vyvoláno.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-275">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
 <span data-ttu-id="7c1eb-276">[Icordebugmda – rozhraní](icordebugmda-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-276">[ICorDebugMDA Interface](icordebugmda-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-277">Představuje zprávu pomocníka spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="7c1eb-277">Represents a managed debugging assistant (MDA) message.</span></span>  
  
 <span data-ttu-id="7c1eb-278">[ICorDebugMemoryBuffer Interface](icordebugmemorybuffer-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-278">[ICorDebugMemoryBuffer Interface](icordebugmemorybuffer-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-279">Představuje vyrovnávací paměť v paměti.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-279">Represents an in-memory buffer.</span></span> <span data-ttu-id="7c1eb-280">**K dispozici na pouze .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="7c1eb-280">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="7c1eb-281">[Icordebugmergedassemblyrecord – rozhraní](icordebugmergedassemblyrecord-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-281">[ICorDebugMergedAssemblyRecord Interface](icordebugmergedassemblyrecord-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-282">Poskytuje informace o sloučené sestavení.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-282">Provides information about a merged assembly.</span></span> <span data-ttu-id="7c1eb-283">**K dispozici na pouze .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="7c1eb-283">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="7c1eb-284">[ICorDebugMetaDataLocator Interface](icordebugmetadatalocator-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-284">[ICorDebugMetaDataLocator Interface](icordebugmetadatalocator-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-285">Poskytuje informace metadat k ladicímu programu.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-285">Provides metadata information to the debugger.</span></span>  
  
 <span data-ttu-id="7c1eb-286">[ICorDebugModule Interface](icordebugmodule-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-286">[ICorDebugModule Interface](icordebugmodule-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-287">Představuje modul CLR, který je spustitelný soubor nebo dynamická knihovna (DLL).</span><span class="sxs-lookup"><span data-stu-id="7c1eb-287">Represents a CLR module, which is either an executable or a dynamic-link library (DLL).</span></span>  
  
 <span data-ttu-id="7c1eb-288">[ICorDebugModule2 Interface](icordebugmodule2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-288">[ICorDebugModule2 Interface](icordebugmodule2-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-289">Slouží jako logické rozšíření pro `ICorDebugModule`.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-289">Serves as a logical extension to `ICorDebugModule`.</span></span>  
  
 <span data-ttu-id="7c1eb-290">[ICorDebugModule3 Interface](icordebugmodule3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-290">[ICorDebugModule3 Interface](icordebugmodule3-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-291">Vytvoří čtečku symbolů pro dynamický modul.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-291">Creates a symbol reader for a dynamic module.</span></span>  
  
 <span data-ttu-id="7c1eb-292">[ICorDebugModuleBreakpoint Interface](icordebugmodulebreakpoint-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-292">[ICorDebugModuleBreakpoint Interface](icordebugmodulebreakpoint-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-293">Rozšiřuje `ICorDebugBreakpoint` a zajistit tak přístup k určitým modulům.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-293">Extends `ICorDebugBreakpoint` to provide access to specific modules.</span></span>  
  
 <span data-ttu-id="7c1eb-294">[Icordebugmoduledebugevent – rozhraní](icordebugmoduledebugevent-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-294">[ICorDebugModuleDebugEvent Interface](icordebugmoduledebugevent-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-295">Rozšiřuje [ICorDebugDebugEvent](icordebugdebugevent-interface.md) rozhraní pro podporu událostí na úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-295">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support module-level events.</span></span> <span data-ttu-id="7c1eb-296">**K dispozici na pouze .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="7c1eb-296">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="7c1eb-297">[Icordebugmoduleenum – rozhraní](icordebugmoduleenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-297">[ICorDebugModuleEnum Interface](icordebugmoduleenum-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-298">Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugModule` pole.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-298">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugModule` arrays.</span></span>  
  
 <span data-ttu-id="7c1eb-299">[ICorDebugMutableDataTarget Interface](icordebugmutabledatatarget-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-299">[ICorDebugMutableDataTarget Interface](icordebugmutabledatatarget-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-300">Rozšiřuje [icordebugdatatarget –](icordebugdatatarget-interface.md) rozhraní pro podporu proměnlivé datové cíle.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-300">Extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
 <span data-ttu-id="7c1eb-301">[Icordebugnativeframe – rozhraní](icordebugnativeframe-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-301">[ICorDebugNativeFrame Interface](icordebugnativeframe-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-302">Specializovaná implementace `ICorDebugFrame` pro nativní snímky.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-302">A specialized implementation of `ICorDebugFrame` used for native frames.</span></span>  
  
 <span data-ttu-id="7c1eb-303">[Icordebugnativeframe2 – rozhraní](icordebugnativeframe2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-303">[ICorDebugNativeFrame2 Interface](icordebugnativeframe2-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-304">Poskytuje metody, které testují podřízené a nadřazené vztahy rámce.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-304">Provides methods that test for child and parent frame relationships.</span></span>  
  
 <span data-ttu-id="7c1eb-305">[Icordebugobjectenum – rozhraní](icordebugobjectenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-305">[ICorDebugObjectEnum Interface](icordebugobjectenum-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-306">Implementuje `ICorDebugEnum` metody a vytváří výčet polí objektů podle jejich relativních virtuálních adres (RVA).</span><span class="sxs-lookup"><span data-stu-id="7c1eb-306">Implements `ICorDebugEnum` methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
 <span data-ttu-id="7c1eb-307">[Icordebugobjectvalue – rozhraní](icordebugobjectvalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-307">[ICorDebugObjectValue Interface](icordebugobjectvalue-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-308">Podtřída `ICorDebugValue` , která představuje hodnotu, která obsahuje objekt.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-308">A subclass of `ICorDebugValue` that represents a value that contains an object.</span></span>  
  
 <span data-ttu-id="7c1eb-309">[Icordebugobjectvalue2 – rozhraní](icordebugobjectvalue2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-309">[ICorDebugObjectValue2 Interface](icordebugobjectvalue2-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-310">Rozšiřuje `ICorDebugObjectValue` pro podporu dědičnosti a přepsání.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-310">Extends `ICorDebugObjectValue` to support inheritance and overrides.</span></span>  
  
 <span data-ttu-id="7c1eb-311">[Icordebugprocess – rozhraní](icordebugprocess-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-311">[ICorDebugProcess Interface](icordebugprocess-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-312">Představuje proces, který spouští spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-312">Represents a process that is executing managed code.</span></span>  
  
 <span data-ttu-id="7c1eb-313">[Icordebugprocess2 – rozhraní](icordebugprocess2-interface1.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-313">[ICorDebugProcess2 Interface](icordebugprocess2-interface1.md)\\</span></span>
 <span data-ttu-id="7c1eb-314">Logické rozšíření `ICorDebugProcess`.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-314">A logical extension of `ICorDebugProcess`.</span></span>  
  
 <span data-ttu-id="7c1eb-315">[Icordebugprocess3 – rozhraní](icordebugprocess3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-315">[ICorDebugProcess3 Interface](icordebugprocess3-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-316">Řídí vlastní oznámení ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-316">Controls custom debugger notifications.</span></span>

 <span data-ttu-id="7c1eb-317">[ICorDebugProcess4 rozhraní](icordebugprocess4-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-317">[ICorDebugProcess4 Interface](icordebugprocess4-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-318">Poskytuje podporu pro mimo proces řízení provádění.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-318">Provides support for out of process execution control.</span></span>
  
 <span data-ttu-id="7c1eb-319">[Icordebugprocess5 – rozhraní](icordebugprocess5-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-319">[ICorDebugProcess5 Interface](icordebugprocess5-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-320">Rozšiřuje [ICorDebugProcess](icordebugprocess-interface.md) rozhraní pro podporu přístupu ke spravované haldě, k poskytování informací o uvolnění paměti spravovaných objektů a určení, zda ladicí program načítá obrázky z aplikace v místním mezipaměti nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-320">Extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application's local native image cache.</span></span>  
  
 <span data-ttu-id="7c1eb-321">[Icordebugprocess6 – rozhraní](icordebugprocess6-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-321">[ICorDebugProcess6 Interface](icordebugprocess6-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-322">Logicky rozšiřuje [ICorDebugProcess](icordebugprocess-interface.md) rozhraní k povolení funkcí, jako je například dekódování spravované ladění události, které jsou zakódovány nativní výjimka ladění událostí a rozdělení virtuální modulu.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-322">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span> <span data-ttu-id="7c1eb-323">**K dispozici na pouze .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="7c1eb-323">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="7c1eb-324">[Icordebugprocess7 – rozhraní](icordebugprocess7-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-324">[ICorDebugProcess7 Interface](icordebugprocess7-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-325">Poskytuje metodu, která nakonfiguruje ladicího programu pro zpracování aktualizace metadat v paměti v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-325">Provides a method that configures the debugger to handle in-memory metadata updates in the target process.</span></span>  
  
 <span data-ttu-id="7c1eb-326">[Icordebugprocess8 – rozhraní](icordebugprocess8-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-326">[ICorDebugProcess8 Interface](icordebugprocess8-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-327">Logicky rozšiřuje [ICorDebugProcess](icordebugprocess-interface.md) rozhraní pro povolení nebo zakázání určitých typů [icordebugmanagedcallback2 –](icordebugmanagedcallback2-interface.md) zpětných volání výjimky.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-327">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable or disable certain types of [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
 <span data-ttu-id="7c1eb-328">[Icordebugprocessenum – rozhraní](icordebugprocessenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-328">[ICorDebugProcessEnum Interface](icordebugprocessenum-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-329">Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugProcess` pole.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-329">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugProcess` arrays.</span></span>  
  
 <span data-ttu-id="7c1eb-330">[Icordebugreferencevalue – rozhraní](icordebugreferencevalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-330">[ICorDebugReferenceValue Interface](icordebugreferencevalue-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-331">Podtřída `ICorDebugValue` podporující referenční typy.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-331">A subclass of `ICorDebugValue` that supports reference types.</span></span>  
  
 <span data-ttu-id="7c1eb-332">[Icordebugregisterset – rozhraní](icordebugregisterset-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-332">[ICorDebugRegisterSet Interface](icordebugregisterset-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-333">Představuje sadu registrů, které jsou k dispozici v počítači, který aktuálně spouští kód.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-333">Represents the set of registers available on the machine that is currently executing code.</span></span>  
  
 <span data-ttu-id="7c1eb-334">[Icordebugregisterset2 – rozhraní](icordebugregisterset2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-334">[ICorDebugRegisterSet2 Interface](icordebugregisterset2-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-335">Rozšiřuje možnosti `ICorDebugRegisterSet` pro hardwarové platformy, které mají více než 64 registrů.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-335">Extends the capabilities of `ICorDebugRegisterSet` for hardware platforms that have more than 64 registers.</span></span>  
  
 <span data-ttu-id="7c1eb-336">[Icordebugremote – rozhraní](icordebugremote-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-336">[ICorDebugRemote Interface](icordebugremote-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-337">Umožňuje spustit nebo připojit spravovaný ladicí program ke vzdálenému cílovému procesu.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-337">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
 <span data-ttu-id="7c1eb-338">[Icordebugremotetarget – rozhraní](icordebugremotetarget-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-338">[ICorDebugRemoteTarget Interface](icordebugremotetarget-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-339">Poskytuje metody umožňující ladit aplikace programu Silverlight v prostředí CLR.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-339">Provides methods that enable you to debug Silverlight-based applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="7c1eb-340">[ICorDebugRuntimeUnwindableFrame Interface](icordebugruntimeunwindableframe-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-340">[ICorDebugRuntimeUnwindableFrame Interface](icordebugruntimeunwindableframe-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-341">Poskytuje podporu pro nespravované metody, které vyžadují modul CLR k uvolnění rámce.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-341">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
 <span data-ttu-id="7c1eb-342">[Icordebugstackwalk – rozhraní](icordebugstackwalk-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-342">[ICorDebugStackWalk Interface](icordebugstackwalk-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-343">Poskytuje metody pro získání spravovaných metod nebo rámců v zásobníku vlákna.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-343">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
 <span data-ttu-id="7c1eb-344">[Icordebugstaticfieldsymbol – rozhraní](icordebugstaticfieldsymbol-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-344">[ICorDebugStaticFieldSymbol Interface](icordebugstaticfieldsymbol-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-345">Představuje informací symbolů ladění pro statické pole.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-345">Represents the debug symbol information for a static field.</span></span> <span data-ttu-id="7c1eb-346">**K dispozici na pouze .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="7c1eb-346">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="7c1eb-347">[Icordebugstepper – rozhraní](icordebugstepper-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-347">[ICorDebugStepper Interface](icordebugstepper-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-348">Představuje krok ve spuštění kódu, který je prováděn pomocí ladicího programu, slouží jako identifikátor mezi vydáním a dokončením příkazu a umožňuje krok zrušit.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-348">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
 <span data-ttu-id="7c1eb-349">[Icordebugstepper2 – rozhraní](icordebugstepper2-interface1.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-349">[ICorDebugStepper2 Interface](icordebugstepper2-interface1.md)\\</span></span>
 <span data-ttu-id="7c1eb-350">Poskytuje podporu ladění Pouze můj kód (JMC).</span><span class="sxs-lookup"><span data-stu-id="7c1eb-350">Provides support for Just My Code (JMC) debugging.</span></span>  
  
 <span data-ttu-id="7c1eb-351">[Icordebugstepperenum – rozhraní](icordebugstepperenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-351">[ICorDebugStepperEnum Interface](icordebugstepperenum-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-352">Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugStepper` pole.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-352">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugStepper` arrays.</span></span>  
  
 <span data-ttu-id="7c1eb-353">[ICorDebugStringValue Interface](icordebugstringvalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-353">[ICorDebugStringValue Interface](icordebugstringvalue-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-354">Podtřída `ICorDebugHeapValue` aplikovaná na řetězcové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-354">A subclass of `ICorDebugHeapValue` that applies to string values.</span></span>  
  
 <span data-ttu-id="7c1eb-355">[Icordebugsymbolprovider – rozhraní](icordebugsymbolprovider-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-355">[ICorDebugSymbolProvider Interface](icordebugsymbolprovider-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-356">Poskytuje metody, které slouží k načtení informací symbolů ladění.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-356">Provides methods that can be used to retrieve debug symbol information.</span></span> <span data-ttu-id="7c1eb-357">**K dispozici na pouze .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="7c1eb-357">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="7c1eb-358">[Icordebugsymbolprovider2 – rozhraní](icordebugsymbolprovider2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-358">[ICorDebugSymbolProvider2 Interface](icordebugsymbolprovider2-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-359">Logicky rozšiřuje [icordebugsymbolprovider –](icordebugsymbolprovider-interface.md) rozhraní pro načtení informací o symbolu další ladění.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-359">Logically extends the [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span> <span data-ttu-id="7c1eb-360">**K dispozici na pouze .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="7c1eb-360">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="7c1eb-361">[Icordebugthread – rozhraní](icordebugthread-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-361">[ICorDebugThread Interface](icordebugthread-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-362">Představuje vlákno v procesu.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-362">Represents a thread in a process.</span></span> <span data-ttu-id="7c1eb-363">Životnost `ICorDebugThread` instance je stejná jako životnost vlákna, které představuje.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-363">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
 <span data-ttu-id="7c1eb-364">[Icordebugthread2 – rozhraní](icordebugthread2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-364">[ICorDebugThread2 Interface](icordebugthread2-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-365">Slouží jako logické rozšíření pro `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-365">Serves as a logical extension to `ICorDebugThread`.</span></span>  
  
 <span data-ttu-id="7c1eb-366">[Icordebugthread3 – rozhraní](icordebugthread3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-366">[ICorDebugThread3 Interface](icordebugthread3-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-367">Poskytuje vstupní bod, který [ICorDebugStackWalk](icordebugstackwalk-interface.md) a odpovídající rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-367">Provides the entry point to the [ICorDebugStackWalk](icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
 <span data-ttu-id="7c1eb-368">[Icordebugthread4 – rozhraní](icordebugthread4-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-368">[ICorDebugThread4 Interface](icordebugthread4-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-369">Poskytuje informace o blokování vlákna.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-369">Provides thread blocking information.</span></span>  
  
 <span data-ttu-id="7c1eb-370">[Icordebugthreadenum – rozhraní](icordebugthreadenum-interface1.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-370">[ICorDebugThreadEnum Interface](icordebugthreadenum-interface1.md)\\</span></span>
 <span data-ttu-id="7c1eb-371">Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugThread` pole.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-371">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugThread` arrays.</span></span>  
  
 <span data-ttu-id="7c1eb-372">[Icordebugtype – rozhraní](icordebugtype-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-372">[ICorDebugType Interface](icordebugtype-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-373">Představuje typ, který může být základní nebo komplexní (tj. definovaný uživatelem).</span><span class="sxs-lookup"><span data-stu-id="7c1eb-373">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="7c1eb-374">Pokud je typ obecný, `ICorDebugType` představuje obecný typ s instancemi.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-374">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
 <span data-ttu-id="7c1eb-375">[Icordebugtype2 – rozhraní](icordebugtype2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-375">[ICorDebugType2 Interface](icordebugtype2-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-376">Rozšiřuje [ICorDebugType](icordebugtype-interface.md) rozhraní načtete identifikátor typu základního typu nebo komplexní typ (definovaný uživatelem).</span><span class="sxs-lookup"><span data-stu-id="7c1eb-376">Extends the [ICorDebugType](icordebugtype-interface.md) interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
 <span data-ttu-id="7c1eb-377">[Icordebugtypeenum – rozhraní](icordebugtypeenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-377">[ICorDebugTypeEnum Interface](icordebugtypeenum-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-378">Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugType` pole.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-378">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugType` arrays.</span></span>  
  
 <span data-ttu-id="7c1eb-379">[ICorDebugUnmanagedCallback Interface](icordebugunmanagedcallback-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-379">[ICorDebugUnmanagedCallback Interface](icordebugunmanagedcallback-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-380">Poskytuje oznámení nativních událostí, které přímo nesouvisejí s CLR.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-380">Provides notification of native events that are not directly related to the CLR.</span></span>  
  
 <span data-ttu-id="7c1eb-381">[ICorDebugValue](icordebugvalue-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-381">[ICorDebugValue](icordebugvalue-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-382">Představuje hodnotu pro čtení nebo zápis v laděném procesu.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-382">Represents a read or write value in the process being debugged.</span></span>  
  
 <span data-ttu-id="7c1eb-383">[ICorDebugValue2](icordebugvalue2-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-383">[ICorDebugValue2](icordebugvalue2-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-384">Rozšiřuje `ICorDebugValue` k poskytování podpory pro `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-384">Extends `ICorDebugValue` to provide support for `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="7c1eb-385">[Icordebugvalue3 – rozhraní](icordebugvalue3-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-385">[ICorDebugValue3 Interface](icordebugvalue3-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-386">Rozšiřuje rozhraní "ICorDebugValue" a "ICorDebugValue2" k poskytování podpory pro pole, která jsou větší než 2 GB.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-386">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
 <span data-ttu-id="7c1eb-387">[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-387">[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-388">Rozšiřuje `ICorDebugBreakpoint` a zajistit tak přístup k určitým hodnotám.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-388">Extends `ICorDebugBreakpoint` to provide access to specific values.</span></span>  
  
 <span data-ttu-id="7c1eb-389">[Icordebugvalueenum –](icordebugvalueenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-389">[ICorDebugValueEnum](icordebugvalueenum-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-390">Implementuje `ICorDebugEnum` metody a vytváří výčet `ICorDebugValue` pole.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-390">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugValue` arrays.</span></span>  
  
 <span data-ttu-id="7c1eb-391">[Icordebugvariablehome – rozhraní](icordebugvariablehome-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-391">[ICorDebugVariableHome Interface](icordebugvariablehome-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-392">Představuje místní proměnné nebo argumentu funkce.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-392">Represents a local variable or argument of a function.</span></span>  
  
 <span data-ttu-id="7c1eb-393">[Icordebugvariablehomeenum – rozhraní](icordebugvariablehomeenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-393">[ICorDebugVariableHomeEnum Interface](icordebugvariablehomeenum-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-394">Poskytuje enumerátor pro místní proměnné a argumenty ve funkci.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-394">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="7c1eb-395">[ICorDebugVariableSymbol Interface](icordebugvariablesymbol-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-395">[ICorDebugVariableSymbol Interface](icordebugvariablesymbol-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-396">Načte informace o symbolu ladění pro proměnnou.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-396">Retrieves the debug symbol information for a variable.</span></span> <span data-ttu-id="7c1eb-397">**K dispozici na pouze .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="7c1eb-397">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="7c1eb-398">[Icordebugvirtualunwinder – rozhraní](icordebugvirtualunwinder-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-398">[ICorDebugVirtualUnwinder Interface](icordebugvirtualunwinder-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-399">Poskytuje metody, které vám pomůžou odvíjení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-399">Provides methods to help in stack unwinding.</span></span> <span data-ttu-id="7c1eb-400">**K dispozici na pouze .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="7c1eb-400">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="7c1eb-401">[Icorpublish – rozhraní](icorpublish-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-401">[ICorPublish Interface](icorpublish-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-402">Slouží jako obecné rozhraní pro procesy publikování.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-402">Serves as the general interface for the publishing processes.</span></span>  
  
 <span data-ttu-id="7c1eb-403">[Icorpublishappdomain – rozhraní](icorpublishappdomain-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-403">[ICorPublishAppDomain Interface](icorpublishappdomain-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-404">Představuje a poskytuje informace o aplikační doméně.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-404">Represents and provides information about an application domain.</span></span>  
  
 <span data-ttu-id="7c1eb-405">[Icorpublishappdomainenum – rozhraní](icorpublishappdomainenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-405">[ICorPublishAppDomainEnum Interface](icorpublishappdomainenum-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-406">Poskytuje metody, které procházejí kolekci `ICorPublishAppDomain` objekty, které momentálně existují v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-406">Provides methods that traverse a collection of `ICorPublishAppDomain` objects that currently exist within a process.</span></span>  
  
 <span data-ttu-id="7c1eb-407">[Icorpublishenum – rozhraní](icorpublishenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-407">[ICorPublishEnum Interface](icorpublishenum-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-408">Slouží jako abstraktní základ pro enumerátory publikování.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-408">Serves as the abstract base for publishing enumerators.</span></span>  
  
 <span data-ttu-id="7c1eb-409">[Icorpublishprocess – rozhraní](icorpublishprocess-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-409">[ICorPublishProcess Interface](icorpublishprocess-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-410">Poskytuje metody, které přistupují k informacím o procesu.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-410">Provides methods that access information about a process.</span></span>  
  
 <span data-ttu-id="7c1eb-411">[Icorpublishprocessenum – rozhraní](icorpublishprocessenum-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-411">[ICorPublishProcessEnum Interface](icorpublishprocessenum-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-412">Poskytuje metody, které procházejí kolekci `ICorPublishProcess` objekty.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-412">Provides methods that traverse a collection of `ICorPublishProcess` objects.</span></span>  

 <span data-ttu-id="7c1eb-413">[ISOSDacInterface rozhraní](isosdacinterface-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-413">[ISOSDacInterface Interface](isosdacinterface-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-414">Poskytuje pomocné metody pro přístup k datům z `SOS`.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-414">Provides helper methods to access data from `SOS`.</span></span>

 <span data-ttu-id="7c1eb-415">[IXCLRDataMethodDefinition rozhraní](ixclrdatamethoddefinition-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-415">[IXCLRDataMethodDefinition Interface](ixclrdatamethoddefinition-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-416">Poskytuje metody pro dotazování na informace o definici metody.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-416">Provides methods for querying information about a method definition.</span></span>
 
 <span data-ttu-id="7c1eb-417">[IXCLRDataMethodInstance Interface](ixclrdatamethodinstance-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-417">[IXCLRDataMethodInstance Interface](ixclrdatamethodinstance-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-418">Poskytuje metody pro dotazování na informace o metodu instance.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-418">Provides methods for querying information about a method instance.</span></span>
 
 <span data-ttu-id="7c1eb-419">[IXCLRDataModule Interface](ixclrdatamodule-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-419">[IXCLRDataModule Interface](ixclrdatamodule-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-420">Poskytuje metody pro dotazování na informace o u načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-420">Provides methods for querying information about a loaded module.</span></span>
 
 <span data-ttu-id="7c1eb-421">[IXCLRDataProcess Interface](ixclrdataprocess-interface.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-421">[IXCLRDataProcess Interface](ixclrdataprocess-interface.md)\\</span></span>
 <span data-ttu-id="7c1eb-422">Poskytuje metody pro dotazování na informace o procesu.</span><span class="sxs-lookup"><span data-stu-id="7c1eb-422">Provides methods for querying information about a process.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="7c1eb-423">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="7c1eb-423">Related Sections</span></span>  
 <span data-ttu-id="7c1eb-424">[Ladění tříd typu coclass](debugging-coclasses.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-424">[Debugging Coclasses](debugging-coclasses.md)\\</span></span>
 <span data-ttu-id="7c1eb-425">[Globální statické funkce ladění](debugging-global-static-functions.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-425">[Debugging Global Static Functions](debugging-global-static-functions.md)\\</span></span>
 <span data-ttu-id="7c1eb-426">[Výčty pro ladění](debugging-enumerations.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-426">[Debugging Enumerations](debugging-enumerations.md)\\</span></span>
 <span data-ttu-id="7c1eb-427">[Struktury pro ladění](debugging-structures.md)\\</span><span class="sxs-lookup"><span data-stu-id="7c1eb-427">[Debugging Structures](debugging-structures.md)\\</span></span>
