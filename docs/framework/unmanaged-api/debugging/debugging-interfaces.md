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
ms.openlocfilehash: 991e333c53101a2be2a8a19d3960c3d0879619be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33409929"
---
# <a name="debugging-interfaces"></a><span data-ttu-id="fb44f-102">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-102">Debugging Interfaces</span></span>
<span data-ttu-id="fb44f-103">Tato část popisuje nespravovaná rozhraní, která zpracovávají ladění programu, který je spouštěn v modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="fb44f-103">This section describes the unmanaged interfaces that handle the debugging of a program that is executing in the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fb44f-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="fb44f-104">In This Section</span></span>  
 [<span data-ttu-id="fb44f-105">ICLRDataEnumMemoryRegions – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-105">ICLRDataEnumMemoryRegions Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)  
 <span data-ttu-id="fb44f-106">Představuje způsob, jak vytvořit výčet oblastí paměti zadaných volajícími.</span><span class="sxs-lookup"><span data-stu-id="fb44f-106">Provides a method to enumerate regions of memory that are specified by callers.</span></span>  
  
 [<span data-ttu-id="fb44f-107">ICLRDataEnumMemoryRegionsCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-107">ICLRDataEnumMemoryRegionsCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)  
 <span data-ttu-id="fb44f-108">Poskytuje metody zpětného volání pro `EnumMemoryRegions` tak, aby odesílaly ladicí program, výsledek pokusu o zobrazení výčtu zadané oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="fb44f-108">Provides a callback method for `EnumMemoryRegions` to report to the debugger, the result of an attempt to enumerate a specified region of memory.</span></span>  
  
 [<span data-ttu-id="fb44f-109">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-109">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 <span data-ttu-id="fb44f-110">Poskytuje metody pro interakci s cílovým procesem CLR.</span><span class="sxs-lookup"><span data-stu-id="fb44f-110">Provides methods for interaction with a target CLR process.</span></span>  
  
 [<span data-ttu-id="fb44f-111">ICLRDataTarget2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-111">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 <span data-ttu-id="fb44f-112">Podtřídou třídy `ICLRDataTarget` vrstvy služby přístupu k datům jsou používány k manipulaci s oblastí virtuální paměti v tento cílový proces.</span><span class="sxs-lookup"><span data-stu-id="fb44f-112">A subclass of `ICLRDataTarget` that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
 [<span data-ttu-id="fb44f-113">ICLRDataTarget3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-113">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 <span data-ttu-id="fb44f-114">Podtřídou třídy [iclrdatatarget2 –](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) , který poskytuje přístup k informacím o výjimce.</span><span class="sxs-lookup"><span data-stu-id="fb44f-114">A subclass of [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
 [<span data-ttu-id="fb44f-115">ICLRDebugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-115">ICLRDebugging Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md)  
 <span data-ttu-id="fb44f-116">Poskytuje metody, které zpracovávají načítání a uvolňování modulů pro ladění.</span><span class="sxs-lookup"><span data-stu-id="fb44f-116">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
 [<span data-ttu-id="fb44f-117">ICLRDebuggingLibraryProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-117">ICLRDebuggingLibraryProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md)  
 <span data-ttu-id="fb44f-118">Zahrnuje [providelibrary – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) metodu, která získá knihovny poskytovatele rozhraní zpětné volání, které umožňuje common language runtime specifické pro verzi ladění lze knihoven najít a načíst na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="fb44f-118">Includes the [ProvideLibrary Method](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
 [<span data-ttu-id="fb44f-119">ICLRMetadataLocator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-119">ICLRMetadataLocator Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-interface.md)  
 <span data-ttu-id="fb44f-120">Rozhraní používané vrstvou služeb přístupu k datům k vyhledání metadat sestavení v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="fb44f-120">Interface used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
 [<span data-ttu-id="fb44f-121">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-121">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 <span data-ttu-id="fb44f-122">Poskytuje metody, které umožňují vývojářům ladit aplikace v prostředí CLR.</span><span class="sxs-lookup"><span data-stu-id="fb44f-122">Provides methods that allow developers to debug applications in the CLR environment.</span></span>  
  
 [<span data-ttu-id="fb44f-123">ICorDebugAppDomain – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-123">ICorDebugAppDomain Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md)  
 <span data-ttu-id="fb44f-124">Poskytuje metody pro ladění domén aplikace.</span><span class="sxs-lookup"><span data-stu-id="fb44f-124">Provides methods for debugging application domains.</span></span>  
  
 [<span data-ttu-id="fb44f-125">ICorDebugAppDomain2 – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-125">ICorDebugAppDomain2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-interface.md)  
 <span data-ttu-id="fb44f-126">Poskytuje metody pro práci s poli, ukazateli, ukazateli na funkci a typy ByRef.</span><span class="sxs-lookup"><span data-stu-id="fb44f-126">Provides methods to work with arrays, pointers, function pointers, and ByRef types.</span></span> <span data-ttu-id="fb44f-127">Toto rozhraní je rozšířením `ICorDebugAppDomain` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fb44f-127">This interface is an extension of the `ICorDebugAppDomain` interface.</span></span>  
  
 [<span data-ttu-id="fb44f-128">ICorDebugAppDomain3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-128">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)  
 <span data-ttu-id="fb44f-129">Poskytuje metody pro práci s [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typy v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="fb44f-129">Provides methods to work with the [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types in an application domain.</span></span> <span data-ttu-id="fb44f-130">Toto rozhraní je rozšířením `ICorDebugAppDomain` a `ICorDebugAppDomain2` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fb44f-130">This interface is an extension of the `ICorDebugAppDomain` and `ICorDebugAppDomain2` interfaces.</span></span>  
  
 [<span data-ttu-id="fb44f-131">ICorDebugAppDomain4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-131">ICorDebugAppDomain4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)  
 <span data-ttu-id="fb44f-132">Logicky rozšiřuje [ICorDebugAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md) rozhraní, jak získat objekt spravovaného z obálka volatelná aplikacemi COM.</span><span class="sxs-lookup"><span data-stu-id="fb44f-132">Logically extends the [ICorDebugAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md) interface to get a managed object from a COM callable wrapper.</span></span>  
  
 [<span data-ttu-id="fb44f-133">ICorDebugAppDomainEnum – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-133">ICorDebugAppDomainEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md)  
 <span data-ttu-id="fb44f-134">Poskytne metodu, která vrací zadaný počet `ICorDebugAppDomain` hodnot počínaje na další umístění ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="fb44f-134">Provides a method that returns a specified number of `ICorDebugAppDomain` values starting at the next location in the enumeration.</span></span>  
  
 [<span data-ttu-id="fb44f-135">ICorDebugArrayValue – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-135">ICorDebugArrayValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-interface.md)  
 <span data-ttu-id="fb44f-136">Podtřídou třídy `ICorDebugHeapValue` představující jednorozměrná nebo multidimenzionální pole.</span><span class="sxs-lookup"><span data-stu-id="fb44f-136">A subclass of `ICorDebugHeapValue` that represents a single-dimensional or multi-dimensional array.</span></span>  
  
 [<span data-ttu-id="fb44f-137">ICorDebugAssembly – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-137">ICorDebugAssembly Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md)  
 <span data-ttu-id="fb44f-138">Představuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="fb44f-138">Represents an assembly.</span></span>  
  
 [<span data-ttu-id="fb44f-139">ICorDebugAssembly2 – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-139">ICorDebugAssembly2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly2-interface.md)  
 <span data-ttu-id="fb44f-140">Představuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="fb44f-140">Represents an assembly.</span></span> <span data-ttu-id="fb44f-141">Toto rozhraní je rozšířením `ICorDebugAssembly` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fb44f-141">This interface is an extension of the `ICorDebugAssembly` interface.</span></span>  
  
 [<span data-ttu-id="fb44f-142">ICorDebugAssembly3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-142">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 <span data-ttu-id="fb44f-143">Logicky rozšiřuje [ICorDebugAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md) rozhraní kvůli zajištění podpory pro kontejner sestavení a jejich omezením sestavení.</span><span class="sxs-lookup"><span data-stu-id="fb44f-143">Logically extends the [ICorDebugAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md) interface to provide support for container assemblies and their contained assemblies.</span></span> <span data-ttu-id="fb44f-144">**K dispozici v jenom .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="fb44f-144">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="fb44f-145">ICorDebugAssemblyEnum – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-145">ICorDebugAssemblyEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassemblyenum-interface.md)  
 <span data-ttu-id="fb44f-146">Implementuje `ICorDebugEnum` metody a vytvoří výčet `ICorDebugAssembly` pole.</span><span class="sxs-lookup"><span data-stu-id="fb44f-146">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugAssembly` arrays.</span></span>  
  
 [<span data-ttu-id="fb44f-147">ICorDebugBlockingObjectEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-147">ICorDebugBlockingObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
 <span data-ttu-id="fb44f-148">Poskytuje enumerátor pro seznam [cordebugblockingobject –](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="fb44f-148">Provides an enumerator for a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>  
  
 [<span data-ttu-id="fb44f-149">ICorDebugBoxValue – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-149">ICorDebugBoxValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugboxvalue-interface.md)  
 <span data-ttu-id="fb44f-150">Podtřídou třídy `ICorDebugHeapValue` představující objekt třídy zabalené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="fb44f-150">A subclass of `ICorDebugHeapValue` that represents a boxed value class object.</span></span>  
  
 [<span data-ttu-id="fb44f-151">ICorDebugBreakpoint – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-151">ICorDebugBreakpoint Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-interface.md)  
 <span data-ttu-id="fb44f-152">Představuje zarážku ve funkci nebo bod sledování na hodnotě.</span><span class="sxs-lookup"><span data-stu-id="fb44f-152">Represents a breakpoint in a function or a watch point on a value.</span></span>  
  
 [<span data-ttu-id="fb44f-153">ICorDebugBreakpointEnum – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-153">ICorDebugBreakpointEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-interface.md)  
 <span data-ttu-id="fb44f-154">Implementuje `ICorDebugEnum` metody a vytvoří výčet `ICorDebugBreakpoint` pole.</span><span class="sxs-lookup"><span data-stu-id="fb44f-154">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugBreakpoint` arrays.</span></span>  
  
 [<span data-ttu-id="fb44f-155">ICorDebugChain – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-155">ICorDebugChain Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md)  
 <span data-ttu-id="fb44f-156">Představuje segment fyzického nebo logického zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="fb44f-156">Represents a segment of a physical or logical call stack.</span></span>  
  
 [<span data-ttu-id="fb44f-157">ICorDebugChainEnum – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-157">ICorDebugChainEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchainenum-interface.md)  
 <span data-ttu-id="fb44f-158">Implementuje `ICorDebugEnum` metody a vytvoří výčet `ICorDebugChain` pole.</span><span class="sxs-lookup"><span data-stu-id="fb44f-158">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugChain` arrays.</span></span>  
  
 [<span data-ttu-id="fb44f-159">ICorDebugClass – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-159">ICorDebugClass Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)  
 <span data-ttu-id="fb44f-160">Představuje typ, který může být základní nebo komplexní (tj. definovaný uživatelem).</span><span class="sxs-lookup"><span data-stu-id="fb44f-160">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="fb44f-161">Pokud je typ Obecné, `ICorDebugClass` představuje bez instancí obecného typu.</span><span class="sxs-lookup"><span data-stu-id="fb44f-161">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
 [<span data-ttu-id="fb44f-162">ICorDebugClass2 – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-162">ICorDebugClass2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-interface.md)  
 <span data-ttu-id="fb44f-163">Představuje obecné třídy nebo typu třídu pomocí parametru metody <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="fb44f-163">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="fb44f-164">Toto rozhraní rozšiřuje `ICorDebugClass`.</span><span class="sxs-lookup"><span data-stu-id="fb44f-164">This interface extends `ICorDebugClass`.</span></span>  
  
 [<span data-ttu-id="fb44f-165">ICorDebugCode – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-165">ICorDebugCode Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)  
 <span data-ttu-id="fb44f-166">Představuje segment kódu jazyka MSIL nebo nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="fb44f-166">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
 [<span data-ttu-id="fb44f-167">ICorDebugCode2 – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-167">ICorDebugCode2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md)  
 <span data-ttu-id="fb44f-168">Poskytuje metody, které rozšiřují možnosti `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="fb44f-168">Provides methods that extend the capabilities of `ICorDebugCode`.</span></span>  
  
 [<span data-ttu-id="fb44f-169">ICorDebugCode3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-169">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 <span data-ttu-id="fb44f-170">Poskytne metodu, která rozšiřuje [ICorDebugCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md) a [icordebugcode2 –](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md) k zadání informací o spravovaných návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="fb44f-170">Provides a method that extends [ICorDebugCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md) and [ICorDebugCode2](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md) to provide information about a managed return value.</span></span>  
  
 [<span data-ttu-id="fb44f-171">ICorDebugCode4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-171">ICorDebugCode4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)  
 <span data-ttu-id="fb44f-172">Poskytne metodu, která umožňuje ladicí program výčet místní proměnné a argumenty ve funkci.</span><span class="sxs-lookup"><span data-stu-id="fb44f-172">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
 [<span data-ttu-id="fb44f-173">ICorDebugCodeEnum – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-173">ICorDebugCodeEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcodeenum-interface.md)  
 <span data-ttu-id="fb44f-174">Implementuje `ICorDebugEnum` metody a vytvoří výčet `ICorDebugCode` pole.</span><span class="sxs-lookup"><span data-stu-id="fb44f-174">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugCode` arrays.</span></span>  
  
 [<span data-ttu-id="fb44f-175">ICorDebugComObjectValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-175">ICorDebugComObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)  
 <span data-ttu-id="fb44f-176">Poskytuje metody pro načtení objektů z mezipaměti rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fb44f-176">Provides methods to retrieve cached interface objects.</span></span>  
  
 [<span data-ttu-id="fb44f-177">ICorDebugContext – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-177">ICorDebugContext Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontext-interface.md)  
 <span data-ttu-id="fb44f-178">Představuje objekt kontextu.</span><span class="sxs-lookup"><span data-stu-id="fb44f-178">Represents a context object.</span></span> <span data-ttu-id="fb44f-179">Toto rozhraní zatím nebylo implementováno.</span><span class="sxs-lookup"><span data-stu-id="fb44f-179">This interface has not been implemented yet.</span></span>  
  
 [<span data-ttu-id="fb44f-180">ICorDebugController – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-180">ICorDebugController Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-interface.md)  
 <span data-ttu-id="fb44f-181">Představuje obor, buď <xref:System.Diagnostics.Process> nebo <xref:System.AppDomain>, ve které provádění kódu se dá řídit kontextu.</span><span class="sxs-lookup"><span data-stu-id="fb44f-181">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
 [<span data-ttu-id="fb44f-182">ICorDebugDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-182">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 <span data-ttu-id="fb44f-183">Poskytuje rozhraní zpětného volání, které poskytuje přístup ke konkrétnímu cílovému procesu.</span><span class="sxs-lookup"><span data-stu-id="fb44f-183">Provides a callback interface that provides access to a particular target process.</span></span>  
  
 [<span data-ttu-id="fb44f-184">ICorDebugDataTarget2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-184">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 <span data-ttu-id="fb44f-185">Logicky rozšiřuje [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fb44f-185">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="fb44f-186">**K dispozici v jenom .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="fb44f-186">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="fb44f-187">ICorDebugDataTarget3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-187">ICorDebugDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-interface.md)  
 <span data-ttu-id="fb44f-188">Logicky rozšiřuje [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) rozhraní k zadání informací o načíst moduly.</span><span class="sxs-lookup"><span data-stu-id="fb44f-188">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span> <span data-ttu-id="fb44f-189">**K dispozici v jenom .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="fb44f-189">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="fb44f-190">ICorDebugDebugEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-190">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 <span data-ttu-id="fb44f-191">Definuje základní rozhraní, ze kterého jsou všechny `ICorDebug` odvozena ladění událostí.</span><span class="sxs-lookup"><span data-stu-id="fb44f-191">Defines the base interface from which all `ICorDebug` debug events derive.</span></span> <span data-ttu-id="fb44f-192">**K dispozici v jenom .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="fb44f-192">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="fb44f-193">ICorDebugEditAndContinueErrorInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-193">ICorDebugEditAndContinueErrorInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinueerrorinfo-interface.md)  
 <span data-ttu-id="fb44f-194">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="fb44f-194">Obsolete.</span></span> <span data-ttu-id="fb44f-195">Toto rozhraní nepoužívejte.</span><span class="sxs-lookup"><span data-stu-id="fb44f-195">Do not use this interface.</span></span>  
  
 [<span data-ttu-id="fb44f-196">ICorDebugEditAndContinueSnapshot – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-196">ICorDebugEditAndContinueSnapshot Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinuesnapshot-interface.md)  
 <span data-ttu-id="fb44f-197">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="fb44f-197">Obsolete.</span></span> <span data-ttu-id="fb44f-198">Toto rozhraní nepoužívejte.</span><span class="sxs-lookup"><span data-stu-id="fb44f-198">Do not use this interface.</span></span>  
  
 [<span data-ttu-id="fb44f-199">ICorDebugEnum – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-199">ICorDebugEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-interface1.md)  
 <span data-ttu-id="fb44f-200">Slouží jako abstraktní základní rozhraní pro enumerátory ladění.</span><span class="sxs-lookup"><span data-stu-id="fb44f-200">Serves as the abstract base interface for debugging enumerators.</span></span>  
  
 [<span data-ttu-id="fb44f-201">ICorDebugErrorInfoEnum – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-201">ICorDebugErrorInfoEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugerrorinfoenum-interface.md)  
 <span data-ttu-id="fb44f-202">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="fb44f-202">Obsolete.</span></span> <span data-ttu-id="fb44f-203">Toto rozhraní nepoužívejte.</span><span class="sxs-lookup"><span data-stu-id="fb44f-203">Do not use this interface.</span></span>  
  
 [<span data-ttu-id="fb44f-204">ICorDebugEval – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-204">ICorDebugEval Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-interface.md)  
 <span data-ttu-id="fb44f-205">Poskytuje metody povolující ladicímu programu spouštět kód v kontextu laděného kódu.</span><span class="sxs-lookup"><span data-stu-id="fb44f-205">Provides methods to enable the debugger to execute code within the context of the code being debugged.</span></span>  
  
 [<span data-ttu-id="fb44f-206">ICorDebugEval2 – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-206">ICorDebugEval2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-interface.md)  
 <span data-ttu-id="fb44f-207">Rozšiřuje `ICorDebugEval` kvůli zajištění podpory pro obecné typy.</span><span class="sxs-lookup"><span data-stu-id="fb44f-207">Extends `ICorDebugEval` to provide support for generic types.</span></span>  
  
 [<span data-ttu-id="fb44f-208">ICorDebugExceptionDebugEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-208">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 <span data-ttu-id="fb44f-209">Rozšiřuje [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) rozhraní pro podporu událostí výjimky.</span><span class="sxs-lookup"><span data-stu-id="fb44f-209">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support exception events.</span></span> <span data-ttu-id="fb44f-210">**K dispozici v jenom .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="fb44f-210">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="fb44f-211">ICorDebugExceptionObjectCallStackEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-211">ICorDebugExceptionObjectCallStackEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
 <span data-ttu-id="fb44f-212">Poskytuje enumerátor pro informace zásobníku volání, který je vložený v objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="fb44f-212">Provides an enumerator for call stack information that is embedded in an exception object.</span></span>  
  
 [<span data-ttu-id="fb44f-213">ICorDebugExceptionObjectValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-213">ICorDebugExceptionObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-interface.md)  
 <span data-ttu-id="fb44f-214">Rozšiřuje [ICorDebugObjectValue](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md) rozhraní poskytnout informace trasování zásobníku z objektu spravovaného výjimka.</span><span class="sxs-lookup"><span data-stu-id="fb44f-214">Extends the [ICorDebugObjectValue](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md) interface to provide stack trace information from a managed exception object.</span></span>  
  
 [<span data-ttu-id="fb44f-215">ICorDebugFrame – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-215">ICorDebugFrame Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md)  
 <span data-ttu-id="fb44f-216">Představuje snímek aktuálního zásobníku.</span><span class="sxs-lookup"><span data-stu-id="fb44f-216">Represents a frame on the current stack.</span></span>  
  
 [<span data-ttu-id="fb44f-217">ICorDebugFrameEnum – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-217">ICorDebugFrameEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframeenum-interface.md)  
 <span data-ttu-id="fb44f-218">Implementuje `ICorDebugEnum` metody a vytvoří výčet `ICorDebugFrame` pole.</span><span class="sxs-lookup"><span data-stu-id="fb44f-218">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugFrame` arrays.</span></span>  
  
 [<span data-ttu-id="fb44f-219">ICorDebugFunction – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-219">ICorDebugFunction Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md)  
 <span data-ttu-id="fb44f-220">Představuje spravovanou funkci nebo metodu.</span><span class="sxs-lookup"><span data-stu-id="fb44f-220">Represents a managed function or method.</span></span>  
  
 [<span data-ttu-id="fb44f-221">ICorDebugFunction2 – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-221">ICorDebugFunction2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-interface.md)  
 <span data-ttu-id="fb44f-222">Logicky rozšiřuje `ICorDebugFunction` poskytovat podporu pro pouze můj kód procházení po kroku ladění.</span><span class="sxs-lookup"><span data-stu-id="fb44f-222">Logically extends `ICorDebugFunction` to provide support for Just My Code step-through debugging.</span></span>  
  
 [<span data-ttu-id="fb44f-223">ICorDebugFunction3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-223">ICorDebugFunction3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-interface.md)  
 <span data-ttu-id="fb44f-224">Logicky rozšiřuje [ICorDebugFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md) rozhraní k poskytování přístupu ke kódu z ReJIT požadavku.</span><span class="sxs-lookup"><span data-stu-id="fb44f-224">Logically extends the [ICorDebugFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md) interface to provide access to code from a ReJIT request.</span></span>  
  
 [<span data-ttu-id="fb44f-225">ICorDebugFunctionBreakpoint – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-225">ICorDebugFunctionBreakpoint Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-interface.md)  
 <span data-ttu-id="fb44f-226">Rozšiřuje `ICorDebugBreakpoint` pro podporu zarážky v rámci funkcí.</span><span class="sxs-lookup"><span data-stu-id="fb44f-226">Extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
 [<span data-ttu-id="fb44f-227">ICorDebugGCReferenceEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-227">ICorDebugGCReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
 <span data-ttu-id="fb44f-228">Poskytuje enumerátor pro objekty, které budou uvolněny z paměti.</span><span class="sxs-lookup"><span data-stu-id="fb44f-228">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
 [<span data-ttu-id="fb44f-229">ICorDebugGenericValue – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-229">ICorDebugGenericValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-interface.md)  
 <span data-ttu-id="fb44f-230">Podtřídou třídy `ICorDebugValue` , platí pro všechny hodnoty.</span><span class="sxs-lookup"><span data-stu-id="fb44f-230">A subclass of `ICorDebugValue` that applies to all values.</span></span> <span data-ttu-id="fb44f-231">Toto rozhraní poskytuje metody Get a Set pro hodnotu.</span><span class="sxs-lookup"><span data-stu-id="fb44f-231">This interface provides Get and Set methods for the value.</span></span>  
  
 [<span data-ttu-id="fb44f-232">ICorDebugGuidToTypeEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-232">ICorDebugGuidToTypeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
 <span data-ttu-id="fb44f-233">Poskytuje enumerátor pro objekt, který mapuje identifikátory GUID a jejich odpovídajících `ICorDebugType` objekty.</span><span class="sxs-lookup"><span data-stu-id="fb44f-233">Provides an enumerator for an object that maps GUIDs and their corresponding `ICorDebugType` objects.</span></span>  
  
 [<span data-ttu-id="fb44f-234">ICorDebugHandleValue – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-234">ICorDebugHandleValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-interface.md)  
 <span data-ttu-id="fb44f-235">Podtřídou třídy `ICorDebugReferenceValue` představující hodnotu odkaz, ke kterému ladicí program vytvořil popisovač pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="fb44f-235">A subclass of `ICorDebugReferenceValue` that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
 [<span data-ttu-id="fb44f-236">ICorDebugHeapEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-236">ICorDebugHeapEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
 <span data-ttu-id="fb44f-237">Poskytuje enumerátor pro objekty na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="fb44f-237">Provides an enumerator for objects on the managed heap.</span></span>  
  
 [<span data-ttu-id="fb44f-238">ICorDebugHeapSegmentEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-238">ICorDebugHeapSegmentEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
 <span data-ttu-id="fb44f-239">Poskytuje enumerátor pro oblasti paměti spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="fb44f-239">Provides an enumerator for the memory regions of the managed heap.</span></span>  
  
 [<span data-ttu-id="fb44f-240">ICorDebugHeapValue – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-240">ICorDebugHeapValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-interface.md)  
 <span data-ttu-id="fb44f-241">Podtřídou třídy `ICorDebugValue` představující objekt, který shromážděných modulem garbage collector v CLR.</span><span class="sxs-lookup"><span data-stu-id="fb44f-241">A subclass of `ICorDebugValue` that represents an object that has been collected by the CLR garbage collector.</span></span>  
  
 [<span data-ttu-id="fb44f-242">ICorDebugHeapValue2 – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-242">ICorDebugHeapValue2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue2-interface1.md)  
 <span data-ttu-id="fb44f-243">Rozšíření `ICorDebugHeapValue` , poskytuje podporu pro obslužné rutiny modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="fb44f-243">An extension of `ICorDebugHeapValue` that provides support for runtime handles.</span></span>  
  
 [<span data-ttu-id="fb44f-244">ICorDebugHeapValue3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-244">ICorDebugHeapValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md)  
 <span data-ttu-id="fb44f-245">Zpřístupní vlastnosti uzamčení sledování objektů.</span><span class="sxs-lookup"><span data-stu-id="fb44f-245">Exposes the monitor lock properties of objects.</span></span>  
  
 [<span data-ttu-id="fb44f-246">ICorDebugILCode – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-246">ICorDebugILCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)  
 <span data-ttu-id="fb44f-247">Představuje segment kód intermediate language (IL).</span><span class="sxs-lookup"><span data-stu-id="fb44f-247">Represents a segment of intermediate language (IL) code.</span></span>  
  
 [<span data-ttu-id="fb44f-248">ICorDebugILCode2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-248">ICorDebugILCode2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)  
 <span data-ttu-id="fb44f-249">Logicky rozšiřuje [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) rozhraní poskytují metody, které vracejí token pro podpis místní proměnné funkce a která mapování profileru instrumentovaného převodní jazyk (IL) posune metodě původní IL Posune.</span><span class="sxs-lookup"><span data-stu-id="fb44f-249">Logically extends the [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
 [<span data-ttu-id="fb44f-250">ICorDebugILFrame – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-250">ICorDebugILFrame Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-interface.md)  
 <span data-ttu-id="fb44f-251">Představuje rámec zásobníku kódu MSIL.</span><span class="sxs-lookup"><span data-stu-id="fb44f-251">Represents a stack frame of MSIL code.</span></span>  
  
 [<span data-ttu-id="fb44f-252">ICorDebugILFrame2 – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-252">ICorDebugILFrame2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-interface.md)  
 <span data-ttu-id="fb44f-253">Logické rozšíření `ICorDebugILFrame`.</span><span class="sxs-lookup"><span data-stu-id="fb44f-253">A logical extension of `ICorDebugILFrame`.</span></span>  
  
 [<span data-ttu-id="fb44f-254">ICorDebugILFrame3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-254">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)  
 <span data-ttu-id="fb44f-255">Poskytuje metodu, která zapouzdřuje vrácenou hodnotu funkce.</span><span class="sxs-lookup"><span data-stu-id="fb44f-255">Provides a method that encapsulates the return value of a function.</span></span>  
  
 [<span data-ttu-id="fb44f-256">ICorDebugILFrame4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-256">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 <span data-ttu-id="fb44f-257">Poskytuje metody, které vám umožní přístup k místní proměnné a kódu v zásobníku kódu převodní jazyk (IL).</span><span class="sxs-lookup"><span data-stu-id="fb44f-257">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="fb44f-258">Parametr určuje, zda ladicí program má přístup k proměnné a kódu přidaném v ReJIT instrumentace profileru.</span><span class="sxs-lookup"><span data-stu-id="fb44f-258">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
 [<span data-ttu-id="fb44f-259">ICorDebugInstanceFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-259">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 <span data-ttu-id="fb44f-260">Představuje informace o ladění symbol pro pole instance.</span><span class="sxs-lookup"><span data-stu-id="fb44f-260">Represents the debug symbol information for an instance field.</span></span> <span data-ttu-id="fb44f-261">**K dispozici v jenom .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="fb44f-261">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="fb44f-262">ICorDebugInternalFrame – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-262">ICorDebugInternalFrame Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-interface.md)  
 <span data-ttu-id="fb44f-263">Určuje typy rámců pro ladicí program.</span><span class="sxs-lookup"><span data-stu-id="fb44f-263">Identifies frame types for the debugger.</span></span>  
  
 [<span data-ttu-id="fb44f-264">ICorDebugInternalFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-264">ICorDebugInternalFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)  
 <span data-ttu-id="fb44f-265">Poskytuje informace o interní rámce, včetně adres zásobníku a pozice v souvislosti s [ICorDebugFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md) objekty.</span><span class="sxs-lookup"><span data-stu-id="fb44f-265">Provides information about internal frames, including stack address and position in relation to [ICorDebugFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md) objects.</span></span>  
  
 [<span data-ttu-id="fb44f-266">ICorDebugLoadedModule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-266">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 <span data-ttu-id="fb44f-267">Poskytuje informace o načíst modul.</span><span class="sxs-lookup"><span data-stu-id="fb44f-267">Provides information about a loaded module.</span></span> <span data-ttu-id="fb44f-268">**K dispozici v jenom .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="fb44f-268">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="fb44f-269">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-269">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)  
 <span data-ttu-id="fb44f-270">Poskytuje metody pro zpětná volání procesu ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="fb44f-270">Provides methods to process debugger callbacks.</span></span>  
  
 [<span data-ttu-id="fb44f-271">ICorDebugManagedCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-271">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 <span data-ttu-id="fb44f-272">Poskytuje metody pro podporu zpracování výjimek ladicího programu a spravované pomocníky ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="fb44f-272">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="fb44f-273">`ICorDebugManagedCallback2` je logické rozšíření `ICorDebugManagedCallback`.</span><span class="sxs-lookup"><span data-stu-id="fb44f-273">`ICorDebugManagedCallback2` is a logical extension of `ICorDebugManagedCallback`.</span></span>  
  
 [<span data-ttu-id="fb44f-274">ICorDebugManagedCallback3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-274">ICorDebugManagedCallback3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-interface.md)  
 <span data-ttu-id="fb44f-275">Poskytuje metodu zpětného volání, která určuje, že povolené vlastní oznámení ladicího programu bylo vyvoláno.</span><span class="sxs-lookup"><span data-stu-id="fb44f-275">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
 [<span data-ttu-id="fb44f-276">ICorDebugMDA – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-276">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 <span data-ttu-id="fb44f-277">Představuje zprávu pomocníka spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="fb44f-277">Represents a managed debugging assistant (MDA) message.</span></span>  
  
 [<span data-ttu-id="fb44f-278">ICorDebugMemoryBuffer – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-278">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 <span data-ttu-id="fb44f-279">Představuje vyrovnávací paměť v paměti.</span><span class="sxs-lookup"><span data-stu-id="fb44f-279">Represents an in-memory buffer.</span></span> <span data-ttu-id="fb44f-280">**K dispozici v jenom .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="fb44f-280">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="fb44f-281">ICorDebugMergedAssemblyRecord – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-281">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 <span data-ttu-id="fb44f-282">Poskytuje informace o sloučené sestavení.</span><span class="sxs-lookup"><span data-stu-id="fb44f-282">Provides information about a merged assembly.</span></span> <span data-ttu-id="fb44f-283">**K dispozici v jenom .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="fb44f-283">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="fb44f-284">ICorDebugMetaDataLocator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-284">ICorDebugMetaDataLocator Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmetadatalocator-interface.md)  
 <span data-ttu-id="fb44f-285">Poskytuje informace metadat k ladicímu programu.</span><span class="sxs-lookup"><span data-stu-id="fb44f-285">Provides metadata information to the debugger.</span></span>  
  
 [<span data-ttu-id="fb44f-286">ICorDebugModule – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-286">ICorDebugModule Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-interface.md)  
 <span data-ttu-id="fb44f-287">Představuje modul CLR, který je spustitelný soubor nebo dynamická knihovna (DLL).</span><span class="sxs-lookup"><span data-stu-id="fb44f-287">Represents a CLR module, which is either an executable or a dynamic-link library (DLL).</span></span>  
  
 [<span data-ttu-id="fb44f-288">ICorDebugModule2 – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-288">ICorDebugModule2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-interface.md)  
 <span data-ttu-id="fb44f-289">Slouží jako logické rozšíření pro `ICorDebugModule`.</span><span class="sxs-lookup"><span data-stu-id="fb44f-289">Serves as a logical extension to `ICorDebugModule`.</span></span>  
  
 [<span data-ttu-id="fb44f-290">ICorDebugModule3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-290">ICorDebugModule3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule3-interface.md)  
 <span data-ttu-id="fb44f-291">Vytvoří čtečku symbolů pro dynamický modul.</span><span class="sxs-lookup"><span data-stu-id="fb44f-291">Creates a symbol reader for a dynamic module.</span></span>  
  
 [<span data-ttu-id="fb44f-292">ICorDebugModuleBreakpoint – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-292">ICorDebugModuleBreakpoint Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-interface.md)  
 <span data-ttu-id="fb44f-293">Rozšiřuje `ICorDebugBreakpoint` poskytnout přístup k určité moduly.</span><span class="sxs-lookup"><span data-stu-id="fb44f-293">Extends `ICorDebugBreakpoint` to provide access to specific modules.</span></span>  
  
 [<span data-ttu-id="fb44f-294">ICorDebugModuleDebugEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-294">ICorDebugModuleDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
 <span data-ttu-id="fb44f-295">Rozšiřuje [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) rozhraní pro podporu událostí na úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="fb44f-295">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support module-level events.</span></span> <span data-ttu-id="fb44f-296">**K dispozici v jenom .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="fb44f-296">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="fb44f-297">ICorDebugModuleEnum – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-297">ICorDebugModuleEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-interface.md)  
 <span data-ttu-id="fb44f-298">Implementuje `ICorDebugEnum` metody a vytvoří výčet `ICorDebugModule` pole.</span><span class="sxs-lookup"><span data-stu-id="fb44f-298">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugModule` arrays.</span></span>  
  
 [<span data-ttu-id="fb44f-299">ICorDebugMutableDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-299">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 <span data-ttu-id="fb44f-300">Rozšiřuje [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) rozhraní pro podporu měnitelný datový cíle.</span><span class="sxs-lookup"><span data-stu-id="fb44f-300">Extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
 [<span data-ttu-id="fb44f-301">ICorDebugNativeFrame – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-301">ICorDebugNativeFrame Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-interface.md)  
 <span data-ttu-id="fb44f-302">Specializovaná implementace `ICorDebugFrame` používá pro nativní rámce.</span><span class="sxs-lookup"><span data-stu-id="fb44f-302">A specialized implementation of `ICorDebugFrame` used for native frames.</span></span>  
  
 [<span data-ttu-id="fb44f-303">ICorDebugNativeFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-303">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 <span data-ttu-id="fb44f-304">Poskytuje metody, které testují podřízené a nadřazené vztahy rámce.</span><span class="sxs-lookup"><span data-stu-id="fb44f-304">Provides methods that test for child and parent frame relationships.</span></span>  
  
 [<span data-ttu-id="fb44f-305">ICorDebugObjectEnum – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-305">ICorDebugObjectEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-interface.md)  
 <span data-ttu-id="fb44f-306">Implementuje `ICorDebugEnum` metody a zobrazí pole objektů podle jejich relativní virtuální adresy (RVAs).</span><span class="sxs-lookup"><span data-stu-id="fb44f-306">Implements `ICorDebugEnum` methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
 [<span data-ttu-id="fb44f-307">ICorDebugObjectValue – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-307">ICorDebugObjectValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md)  
 <span data-ttu-id="fb44f-308">Podtřídou třídy `ICorDebugValue` představující hodnotu, která obsahuje objekt.</span><span class="sxs-lookup"><span data-stu-id="fb44f-308">A subclass of `ICorDebugValue` that represents a value that contains an object.</span></span>  
  
 [<span data-ttu-id="fb44f-309">ICorDebugObjectValue2 – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-309">ICorDebugObjectValue2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue2-interface.md)  
 <span data-ttu-id="fb44f-310">Rozšiřuje `ICorDebugObjectValue` pro podporu dědičnosti a přepsání.</span><span class="sxs-lookup"><span data-stu-id="fb44f-310">Extends `ICorDebugObjectValue` to support inheritance and overrides.</span></span>  
  
 [<span data-ttu-id="fb44f-311">ICorDebugProcess – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-311">ICorDebugProcess Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md)  
 <span data-ttu-id="fb44f-312">Představuje proces, který spouští spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="fb44f-312">Represents a process that is executing managed code.</span></span>  
  
 [<span data-ttu-id="fb44f-313">ICorDebugProcess2 – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-313">ICorDebugProcess2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-interface1.md)  
 <span data-ttu-id="fb44f-314">Logické rozšíření `ICorDebugProcess`.</span><span class="sxs-lookup"><span data-stu-id="fb44f-314">A logical extension of `ICorDebugProcess`.</span></span>  
  
 [<span data-ttu-id="fb44f-315">ICorDebugProcess3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-315">ICorDebugProcess3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)  
 <span data-ttu-id="fb44f-316">Řídí vlastní oznámení ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="fb44f-316">Controls custom debugger notifications.</span></span>  
  
 [<span data-ttu-id="fb44f-317">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-317">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 <span data-ttu-id="fb44f-318">Rozšiřuje [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) je místní rozhraní pro podporu přístupu k spravovaná halda k zadání informací o uvolňování paměti spravovaných objektů a k určení, zda ladicí program načte bitové kopie z aplikace mezipaměť nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="fb44f-318">Extends the [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application's local native image cache.</span></span>  
  
 [<span data-ttu-id="fb44f-319">ICorDebugProcess6 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-319">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 <span data-ttu-id="fb44f-320">Logicky rozšiřuje [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) rozhraní k povolení funkcí, jako je například dekódování spravované ladění události, které jsou v událostí výjimek na nativní ladění a rozdělení virtuální modulu kódování.</span><span class="sxs-lookup"><span data-stu-id="fb44f-320">Logically extends the [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span> <span data-ttu-id="fb44f-321">**K dispozici v jenom .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="fb44f-321">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="fb44f-322">ICorDebugProcess7 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-322">ICorDebugProcess7 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-interface.md)  
 <span data-ttu-id="fb44f-323">Poskytne metodu, která nakonfiguruje ladicího programu pro zpracování v paměti metadata aktualizací v tento cílový proces.</span><span class="sxs-lookup"><span data-stu-id="fb44f-323">Provides a method that configures the debugger to handle in-memory metadata updates in the target process.</span></span>  
  
 [<span data-ttu-id="fb44f-324">ICorDebugProcess8 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-324">ICorDebugProcess8 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)  
 <span data-ttu-id="fb44f-325">Logicky rozšiřuje [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) rozhraní k povolení nebo zakázání určitých typů [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) zpětná volání výjimek.</span><span class="sxs-lookup"><span data-stu-id="fb44f-325">Logically extends the [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interface to enable or disable certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
 [<span data-ttu-id="fb44f-326">ICorDebugProcessEnum – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-326">ICorDebugProcessEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocessenum-interface.md)  
 <span data-ttu-id="fb44f-327">Implementuje `ICorDebugEnum` metody a vytvoří výčet `ICorDebugProcess` pole.</span><span class="sxs-lookup"><span data-stu-id="fb44f-327">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugProcess` arrays.</span></span>  
  
 [<span data-ttu-id="fb44f-328">ICorDebugReferenceValue – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-328">ICorDebugReferenceValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-interface.md)  
 <span data-ttu-id="fb44f-329">Podtřídou třídy `ICorDebugValue` , podporuje odkazové typy.</span><span class="sxs-lookup"><span data-stu-id="fb44f-329">A subclass of `ICorDebugValue` that supports reference types.</span></span>  
  
 [<span data-ttu-id="fb44f-330">ICorDebugRegisterSet – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-330">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 <span data-ttu-id="fb44f-331">Představuje sadu registrů, které jsou k dispozici v počítači, který aktuálně spouští kód.</span><span class="sxs-lookup"><span data-stu-id="fb44f-331">Represents the set of registers available on the machine that is currently executing code.</span></span>  
  
 [<span data-ttu-id="fb44f-332">ICorDebugRegisterSet2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-332">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 <span data-ttu-id="fb44f-333">Rozšiřuje možnosti `ICorDebugRegisterSet` pro hardware platformy, které mají víc než 64 Registry.</span><span class="sxs-lookup"><span data-stu-id="fb44f-333">Extends the capabilities of `ICorDebugRegisterSet` for hardware platforms that have more than 64 registers.</span></span>  
  
 [<span data-ttu-id="fb44f-334">ICorDebugRemote – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-334">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 <span data-ttu-id="fb44f-335">Umožňuje spustit nebo připojit spravovaný ladicí program ke vzdálenému cílovému procesu.</span><span class="sxs-lookup"><span data-stu-id="fb44f-335">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
 [<span data-ttu-id="fb44f-336">ICorDebugRemoteTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-336">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 <span data-ttu-id="fb44f-337">Poskytuje metody umožňující ladit aplikace programu Silverlight v prostředí CLR.</span><span class="sxs-lookup"><span data-stu-id="fb44f-337">Provides methods that enable you to debug Silverlight-based applications in the CLR environment.</span></span>  
  
 [<span data-ttu-id="fb44f-338">ICorDebugRuntimeUnwindableFrame – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-338">ICorDebugRuntimeUnwindableFrame Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugruntimeunwindableframe-interface.md)  
 <span data-ttu-id="fb44f-339">Poskytuje podporu pro nespravované metody, které vyžadují modul CLR k uvolnění rámce.</span><span class="sxs-lookup"><span data-stu-id="fb44f-339">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
 [<span data-ttu-id="fb44f-340">ICorDebugStackWalk – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-340">ICorDebugStackWalk Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)  
 <span data-ttu-id="fb44f-341">Poskytuje metody pro získání spravovaných metod nebo rámců v zásobníku vlákna.</span><span class="sxs-lookup"><span data-stu-id="fb44f-341">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
 [<span data-ttu-id="fb44f-342">ICorDebugStaticFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-342">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 <span data-ttu-id="fb44f-343">Představuje informace o ladění symbol pro statické pole.</span><span class="sxs-lookup"><span data-stu-id="fb44f-343">Represents the debug symbol information for a static field.</span></span> <span data-ttu-id="fb44f-344">**K dispozici v jenom .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="fb44f-344">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="fb44f-345">ICorDebugStepper – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-345">ICorDebugStepper Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-interface.md)  
 <span data-ttu-id="fb44f-346">Představuje krok ve spuštění kódu, který je prováděn pomocí ladicího programu, slouží jako identifikátor mezi vydáním a dokončením příkazu a umožňuje krok zrušit.</span><span class="sxs-lookup"><span data-stu-id="fb44f-346">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
 [<span data-ttu-id="fb44f-347">ICorDebugStepper2 – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-347">ICorDebugStepper2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-interface1.md)  
 <span data-ttu-id="fb44f-348">Poskytuje podporu ladění Pouze můj kód (JMC).</span><span class="sxs-lookup"><span data-stu-id="fb44f-348">Provides support for Just My Code (JMC) debugging.</span></span>  
  
 [<span data-ttu-id="fb44f-349">ICorDebugStepperEnum – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-349">ICorDebugStepperEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepperenum-interface.md)  
 <span data-ttu-id="fb44f-350">Implementuje `ICorDebugEnum` metody a vytvoří výčet `ICorDebugStepper` pole.</span><span class="sxs-lookup"><span data-stu-id="fb44f-350">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugStepper` arrays.</span></span>  
  
 [<span data-ttu-id="fb44f-351">ICorDebugStringValue – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-351">ICorDebugStringValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-interface.md)  
 <span data-ttu-id="fb44f-352">Podtřídou třídy `ICorDebugHeapValue` , platí pro řetězcové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="fb44f-352">A subclass of `ICorDebugHeapValue` that applies to string values.</span></span>  
  
 [<span data-ttu-id="fb44f-353">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-353">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 <span data-ttu-id="fb44f-354">Poskytuje metody, které lze použít k načtení informací o symbolu ladění.</span><span class="sxs-lookup"><span data-stu-id="fb44f-354">Provides methods that can be used to retrieve debug symbol information.</span></span> <span data-ttu-id="fb44f-355">**K dispozici v jenom .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="fb44f-355">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="fb44f-356">ICorDebugSymbolProvider2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-356">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 <span data-ttu-id="fb44f-357">Logicky rozšiřuje [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) rozhraní k načtení informací o symbolu další ladění.</span><span class="sxs-lookup"><span data-stu-id="fb44f-357">Logically extends the [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span> <span data-ttu-id="fb44f-358">**K dispozici v jenom .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="fb44f-358">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="fb44f-359">ICorDebugThread – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-359">ICorDebugThread Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-interface.md)  
 <span data-ttu-id="fb44f-360">Představuje vlákno v procesu.</span><span class="sxs-lookup"><span data-stu-id="fb44f-360">Represents a thread in a process.</span></span> <span data-ttu-id="fb44f-361">Životnost `ICorDebugThread` instance je stejný jako životnost vlákno reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="fb44f-361">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
 [<span data-ttu-id="fb44f-362">ICorDebugThread2 – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-362">ICorDebugThread2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interface.md)  
 <span data-ttu-id="fb44f-363">Slouží jako logické rozšíření pro `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="fb44f-363">Serves as a logical extension to `ICorDebugThread`.</span></span>  
  
 [<span data-ttu-id="fb44f-364">ICorDebugThread3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-364">ICorDebugThread3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md)  
 <span data-ttu-id="fb44f-365">Představuje vstupní bod do [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) a odpovídající rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fb44f-365">Provides the entry point to the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
 [<span data-ttu-id="fb44f-366">ICorDebugThread4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-366">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 <span data-ttu-id="fb44f-367">Poskytuje informace o blokování vlákna.</span><span class="sxs-lookup"><span data-stu-id="fb44f-367">Provides thread blocking information.</span></span>  
  
 [<span data-ttu-id="fb44f-368">ICorDebugThreadEnum – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-368">ICorDebugThreadEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthreadenum-interface1.md)  
 <span data-ttu-id="fb44f-369">Implementuje `ICorDebugEnum` metody a vytvoří výčet `ICorDebugThread` pole.</span><span class="sxs-lookup"><span data-stu-id="fb44f-369">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugThread` arrays.</span></span>  
  
 [<span data-ttu-id="fb44f-370">ICorDebugType – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-370">ICorDebugType Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md)  
 <span data-ttu-id="fb44f-371">Představuje typ, který může být základní nebo komplexní (tj. definovaný uživatelem).</span><span class="sxs-lookup"><span data-stu-id="fb44f-371">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="fb44f-372">Pokud je typ Obecné, `ICorDebugType` představuje instanci obecného typu.</span><span class="sxs-lookup"><span data-stu-id="fb44f-372">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
 [<span data-ttu-id="fb44f-373">ICorDebugType2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-373">ICorDebugType2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)  
 <span data-ttu-id="fb44f-374">Rozšiřuje [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) rozhraní k načtení identifikátor typu základní typ nebo komplexní typ (definovaný uživatelem).</span><span class="sxs-lookup"><span data-stu-id="fb44f-374">Extends the [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
 [<span data-ttu-id="fb44f-375">ICorDebugTypeEnum – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="fb44f-375">ICorDebugTypeEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtypeenum-interface.md)  
 <span data-ttu-id="fb44f-376">Implementuje `ICorDebugEnum` metody a vytvoří výčet `ICorDebugType` pole.</span><span class="sxs-lookup"><span data-stu-id="fb44f-376">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugType` arrays.</span></span>  
  
 [<span data-ttu-id="fb44f-377">ICorDebugUnmanagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-377">ICorDebugUnmanagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)  
 <span data-ttu-id="fb44f-378">Poskytuje oznámení nativních událostí, které přímo nesouvisejí s CLR.</span><span class="sxs-lookup"><span data-stu-id="fb44f-378">Provides notification of native events that are not directly related to the CLR.</span></span>  
  
 <span data-ttu-id="fb44f-379">"ICorDebugValue"</span><span class="sxs-lookup"><span data-stu-id="fb44f-379">"ICorDebugValue"</span></span>  
 <span data-ttu-id="fb44f-380">Představuje hodnotu pro čtení nebo zápis v laděném procesu.</span><span class="sxs-lookup"><span data-stu-id="fb44f-380">Represents a read or write value in the process being debugged.</span></span>  
  
 <span data-ttu-id="fb44f-381">Icordebugvalue2 "–"</span><span class="sxs-lookup"><span data-stu-id="fb44f-381">"ICorDebugValue2"</span></span>  
 <span data-ttu-id="fb44f-382">Rozšiřuje `ICorDebugValue` poskytovat podporu pro `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="fb44f-382">Extends `ICorDebugValue` to provide support for `ICorDebugType`.</span></span>  
  
 [<span data-ttu-id="fb44f-383">ICorDebugValue3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-383">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)  
 <span data-ttu-id="fb44f-384">Rozšiřuje rozhraní "ICorDebugValue" a "Icordebugvalue2 –" poskytovat podporu pro pole, které jsou větší než 2 GB.</span><span class="sxs-lookup"><span data-stu-id="fb44f-384">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
 <span data-ttu-id="fb44f-385">"ICorDebugValueBreakpoint"</span><span class="sxs-lookup"><span data-stu-id="fb44f-385">"ICorDebugValueBreakpoint"</span></span>  
 <span data-ttu-id="fb44f-386">Rozšiřuje `ICorDebugBreakpoint` k poskytování přístupu k konkrétní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="fb44f-386">Extends `ICorDebugBreakpoint` to provide access to specific values.</span></span>  
  
 <span data-ttu-id="fb44f-387">"ICorDebugValueEnum"</span><span class="sxs-lookup"><span data-stu-id="fb44f-387">"ICorDebugValueEnum"</span></span>  
 <span data-ttu-id="fb44f-388">Implementuje `ICorDebugEnum` metody a vytvoří výčet `ICorDebugValue` pole.</span><span class="sxs-lookup"><span data-stu-id="fb44f-388">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugValue` arrays.</span></span>  
  
 [<span data-ttu-id="fb44f-389">ICorDebugVariableHome – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-389">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)  
 <span data-ttu-id="fb44f-390">Představuje místní proměnné nebo argument funkce.</span><span class="sxs-lookup"><span data-stu-id="fb44f-390">Represents a local variable or argument of a function.</span></span>  
  
 [<span data-ttu-id="fb44f-391">ICorDebugVariableHomeEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-391">ICorDebugVariableHomeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
 <span data-ttu-id="fb44f-392">Poskytuje enumerátor pro místní proměnné a argumenty ve funkci.</span><span class="sxs-lookup"><span data-stu-id="fb44f-392">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
 [<span data-ttu-id="fb44f-393">ICorDebugVariableSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-393">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 <span data-ttu-id="fb44f-394">Načte informace o ladění symbol pro proměnnou.</span><span class="sxs-lookup"><span data-stu-id="fb44f-394">Retrieves the debug symbol information for a variable.</span></span> <span data-ttu-id="fb44f-395">**K dispozici v jenom .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="fb44f-395">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="fb44f-396">ICorDebugVirtualUnwinder – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-396">ICorDebugVirtualUnwinder Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-interface.md)  
 <span data-ttu-id="fb44f-397">Poskytuje metody, které pomohou v uvolnění zásobníku.</span><span class="sxs-lookup"><span data-stu-id="fb44f-397">Provides methods to help in stack unwinding.</span></span> <span data-ttu-id="fb44f-398">**K dispozici v jenom .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="fb44f-398">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="fb44f-399">ICorPublish – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-399">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)  
 <span data-ttu-id="fb44f-400">Slouží jako obecné rozhraní pro procesy publikování.</span><span class="sxs-lookup"><span data-stu-id="fb44f-400">Serves as the general interface for the publishing processes.</span></span>  
  
 [<span data-ttu-id="fb44f-401">ICorPublishAppDomain – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-401">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)  
 <span data-ttu-id="fb44f-402">Představuje a poskytuje informace o aplikační doméně.</span><span class="sxs-lookup"><span data-stu-id="fb44f-402">Represents and provides information about an application domain.</span></span>  
  
 [<span data-ttu-id="fb44f-403">ICorPublishAppDomainEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-403">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
 <span data-ttu-id="fb44f-404">Poskytuje metody, které překračují kolekce `ICorPublishAppDomain` objekty, které aktuálně existovat v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="fb44f-404">Provides methods that traverse a collection of `ICorPublishAppDomain` objects that currently exist within a process.</span></span>  
  
 [<span data-ttu-id="fb44f-405">ICorPublishEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-405">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)  
 <span data-ttu-id="fb44f-406">Slouží jako abstraktní základ pro enumerátory publikování.</span><span class="sxs-lookup"><span data-stu-id="fb44f-406">Serves as the abstract base for publishing enumerators.</span></span>  
  
 [<span data-ttu-id="fb44f-407">ICorPublishProcess – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-407">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)  
 <span data-ttu-id="fb44f-408">Poskytuje metody, které přistupují k informacím o procesu.</span><span class="sxs-lookup"><span data-stu-id="fb44f-408">Provides methods that access information about a process.</span></span>  
  
 [<span data-ttu-id="fb44f-409">ICorPublishProcessEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb44f-409">ICorPublishProcessEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
 <span data-ttu-id="fb44f-410">Poskytuje metody, které překračují kolekce `ICorPublishProcess` objekty.</span><span class="sxs-lookup"><span data-stu-id="fb44f-410">Provides methods that traverse a collection of `ICorPublishProcess` objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="fb44f-411">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="fb44f-411">Related Sections</span></span>  
 [<span data-ttu-id="fb44f-412">Třídy typu coclass pro ladění</span><span class="sxs-lookup"><span data-stu-id="fb44f-412">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="fb44f-413">Globální statické funkce pro ladění</span><span class="sxs-lookup"><span data-stu-id="fb44f-413">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [<span data-ttu-id="fb44f-414">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="fb44f-414">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [<span data-ttu-id="fb44f-415">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="fb44f-415">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
