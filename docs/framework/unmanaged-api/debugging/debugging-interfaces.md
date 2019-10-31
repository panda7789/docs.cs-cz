---
title: Debugging – rozhraní
ms.date: 02/07/2019
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
ms.openlocfilehash: 07b39666637628102e9ffafd2c059ba0d4b51b92
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73097194"
---
# <a name="debugging-interfaces"></a><span data-ttu-id="f0fde-102">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f0fde-102">Debugging Interfaces</span></span>
<span data-ttu-id="f0fde-103">Tato část popisuje nespravovaná rozhraní, která zpracovávají ladění programu, který je spouštěn v modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="f0fde-103">This section describes the unmanaged interfaces that handle the debugging of a program that is executing in the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f0fde-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="f0fde-104">In This Section</span></span>  
 <span data-ttu-id="f0fde-105">\ [rozhraní ICLRDataEnumMemoryRegions –](iclrdataenummemoryregions-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-105">[ICLRDataEnumMemoryRegions Interface](iclrdataenummemoryregions-interface.md)\</span></span>
 <span data-ttu-id="f0fde-106">Představuje způsob, jak vytvořit výčet oblastí paměti zadaných volajícími.</span><span class="sxs-lookup"><span data-stu-id="f0fde-106">Provides a method to enumerate regions of memory that are specified by callers.</span></span>  
  
 <span data-ttu-id="f0fde-107">\ [rozhraní ICLRDataEnumMemoryRegionsCallback –](iclrdataenummemoryregionscallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-107">[ICLRDataEnumMemoryRegionsCallback Interface](iclrdataenummemoryregionscallback-interface.md)\</span></span>
 <span data-ttu-id="f0fde-108">Poskytuje metodu zpětného volání pro `EnumMemoryRegions` pro hlášení ladicímu programu, výsledek pokusu o vytvoření výčtu konkrétní oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="f0fde-108">Provides a callback method for `EnumMemoryRegions` to report to the debugger, the result of an attempt to enumerate a specified region of memory.</span></span>  
  
 <span data-ttu-id="f0fde-109">\ [rozhraní ICLRDataTarget](iclrdatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-109">[ICLRDataTarget Interface](iclrdatatarget-interface.md)\</span></span>
 <span data-ttu-id="f0fde-110">Poskytuje metody pro interakci s cílovým procesem CLR.</span><span class="sxs-lookup"><span data-stu-id="f0fde-110">Provides methods for interaction with a target CLR process.</span></span>  
  
 <span data-ttu-id="f0fde-111">\ [rozhraní ICLRDataTarget2](iclrdatatarget2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-111">[ICLRDataTarget2 Interface](iclrdatatarget2-interface.md)\</span></span>
 <span data-ttu-id="f0fde-112">Podtřída `ICLRDataTarget`, kterou vrstva služeb Data Access používá ke zpracování oblastí virtuální paměti v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="f0fde-112">A subclass of `ICLRDataTarget` that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
 <span data-ttu-id="f0fde-113">\ [rozhraní ICLRDataTarget3](iclrdatatarget3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-113">[ICLRDataTarget3 Interface](iclrdatatarget3-interface.md)\</span></span>
 <span data-ttu-id="f0fde-114">Podtřída [ICLRDataTarget2](iclrdatatarget2-interface.md) , která poskytuje přístup k informacím o výjimce.</span><span class="sxs-lookup"><span data-stu-id="f0fde-114">A subclass of [ICLRDataTarget2](iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
 <span data-ttu-id="f0fde-115">\ [rozhraní ICLRDebugging](iclrdebugging-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-115">[ICLRDebugging Interface](iclrdebugging-interface.md)\</span></span>
 <span data-ttu-id="f0fde-116">Poskytuje metody, které zpracovávají načítání a uvolňování modulů pro ladění.</span><span class="sxs-lookup"><span data-stu-id="f0fde-116">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
 <span data-ttu-id="f0fde-117">\ [rozhraní ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-117">[ICLRDebuggingLibraryProvider Interface](iclrdebugginglibraryprovider-interface.md)\</span></span>
 <span data-ttu-id="f0fde-118">Obsahuje metodu [metody ProvideLibrary –](iclrdebugginglibraryprovider-providelibrary-method.md) , která získá rozhraní zpětného volání zprostředkovatele knihovny, které umožňuje umístění a načtení knihoven ladění pro Common Language Runtime v konkrétní verzi.</span><span class="sxs-lookup"><span data-stu-id="f0fde-118">Includes the [ProvideLibrary Method](iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
 <span data-ttu-id="f0fde-119">\ [rozhraní ICLRMetadataLocator –](iclrmetadatalocator-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-119">[ICLRMetadataLocator Interface](iclrmetadatalocator-interface.md)\</span></span>
 <span data-ttu-id="f0fde-120">Rozhraní používané vrstvou služeb přístupu k datům k vyhledání metadat sestavení v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="f0fde-120">Interface used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
 <span data-ttu-id="f0fde-121">\ [rozhraní ICorDebug](icordebug-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-121">[ICorDebug Interface](icordebug-interface.md)\</span></span>
 <span data-ttu-id="f0fde-122">Poskytuje metody, které umožňují vývojářům ladit aplikace v prostředí CLR.</span><span class="sxs-lookup"><span data-stu-id="f0fde-122">Provides methods that allow developers to debug applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="f0fde-123">\ [rozhraní ICorDebugAppDomain](icordebugappdomain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-123">[ICorDebugAppDomain Interface](icordebugappdomain-interface.md)\</span></span>
 <span data-ttu-id="f0fde-124">Poskytuje metody pro ladění domén aplikace.</span><span class="sxs-lookup"><span data-stu-id="f0fde-124">Provides methods for debugging application domains.</span></span>  
  
 <span data-ttu-id="f0fde-125">\ [rozhraní ICorDebugAppDomain2](icordebugappdomain2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-125">[ICorDebugAppDomain2 Interface](icordebugappdomain2-interface.md)\</span></span>
 <span data-ttu-id="f0fde-126">Poskytuje metody pro práci s poli, ukazateli, ukazateli na funkci a typy ByRef.</span><span class="sxs-lookup"><span data-stu-id="f0fde-126">Provides methods to work with arrays, pointers, function pointers, and ByRef types.</span></span> <span data-ttu-id="f0fde-127">Toto rozhraní je rozšířením rozhraní `ICorDebugAppDomain`.</span><span class="sxs-lookup"><span data-stu-id="f0fde-127">This interface is an extension of the `ICorDebugAppDomain` interface.</span></span>  
  
 <span data-ttu-id="f0fde-128">\ [rozhraní ICorDebugAppDomain3](icordebugappdomain3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-128">[ICorDebugAppDomain3 Interface](icordebugappdomain3-interface.md)\</span></span>
 <span data-ttu-id="f0fde-129">Poskytuje metody pro práci s typy prostředí Windows Runtime v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="f0fde-129">Provides methods to work with the Windows Runtime types in an application domain.</span></span> <span data-ttu-id="f0fde-130">Toto rozhraní je rozšířením rozhraní `ICorDebugAppDomain` a `ICorDebugAppDomain2`.</span><span class="sxs-lookup"><span data-stu-id="f0fde-130">This interface is an extension of the `ICorDebugAppDomain` and `ICorDebugAppDomain2` interfaces.</span></span>  
  
 <span data-ttu-id="f0fde-131">\ [rozhraní ICorDebugAppDomain4](icordebugappdomain4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-131">[ICorDebugAppDomain4 Interface](icordebugappdomain4-interface.md)\</span></span>
 <span data-ttu-id="f0fde-132">Logicky rozšiřuje rozhraní [ICorDebugAppDomain](icordebugappdomain-interface.md) , aby získala spravovaný objekt z obálky s přípravnou modelem COM.</span><span class="sxs-lookup"><span data-stu-id="f0fde-132">Logically extends the [ICorDebugAppDomain](icordebugappdomain-interface.md) interface to get a managed object from a COM callable wrapper.</span></span>  
  
 <span data-ttu-id="f0fde-133">\ [rozhraní ICorDebugAppDomainEnum](icordebugappdomainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-133">[ICorDebugAppDomainEnum Interface](icordebugappdomainenum-interface.md)\</span></span>
 <span data-ttu-id="f0fde-134">Poskytuje metodu, která vrací zadaný počet `ICorDebugAppDomain` hodnot od dalšího umístění ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="f0fde-134">Provides a method that returns a specified number of `ICorDebugAppDomain` values starting at the next location in the enumeration.</span></span>  
  
 <span data-ttu-id="f0fde-135">\ [rozhraní ICorDebugArrayValue](icordebugarrayvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-135">[ICorDebugArrayValue Interface](icordebugarrayvalue-interface.md)\</span></span>
 <span data-ttu-id="f0fde-136">Podtřída `ICorDebugHeapValue`, která představuje jednorozměrné nebo multidimenzionální pole.</span><span class="sxs-lookup"><span data-stu-id="f0fde-136">A subclass of `ICorDebugHeapValue` that represents a single-dimensional or multi-dimensional array.</span></span>  
  
 <span data-ttu-id="f0fde-137">\ [rozhraní ICorDebugAssembly](icordebugassembly-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-137">[ICorDebugAssembly Interface](icordebugassembly-interface.md)\</span></span>
 <span data-ttu-id="f0fde-138">Představuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="f0fde-138">Represents an assembly.</span></span>  
  
 <span data-ttu-id="f0fde-139">\ [rozhraní ICorDebugAssembly2](icordebugassembly2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-139">[ICorDebugAssembly2 Interface](icordebugassembly2-interface.md)\</span></span>
 <span data-ttu-id="f0fde-140">Představuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="f0fde-140">Represents an assembly.</span></span> <span data-ttu-id="f0fde-141">Toto rozhraní je rozšířením rozhraní `ICorDebugAssembly`.</span><span class="sxs-lookup"><span data-stu-id="f0fde-141">This interface is an extension of the `ICorDebugAssembly` interface.</span></span>  
  
 <span data-ttu-id="f0fde-142">\ [rozhraní ICorDebugAssembly3](icordebugassembly3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-142">[ICorDebugAssembly3 Interface](icordebugassembly3-interface.md)\</span></span>
 <span data-ttu-id="f0fde-143">Logicky rozšiřuje rozhraní [ICorDebugAssembly](icordebugassembly-interface.md) , aby poskytovala podporu pro sestavení kontejneru a jejich obsažená sestavení.</span><span class="sxs-lookup"><span data-stu-id="f0fde-143">Logically extends the [ICorDebugAssembly](icordebugassembly-interface.md) interface to provide support for container assemblies and their contained assemblies.</span></span> <span data-ttu-id="f0fde-144">**K dispozici pouze v .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="f0fde-144">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="f0fde-145">\ [rozhraní ICorDebugAssemblyEnum](icordebugassemblyenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-145">[ICorDebugAssemblyEnum Interface](icordebugassemblyenum-interface.md)\</span></span>
 <span data-ttu-id="f0fde-146">Implementuje metody `ICorDebugEnum` a vytvoří výčet `ICorDebugAssembly` polí.</span><span class="sxs-lookup"><span data-stu-id="f0fde-146">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugAssembly` arrays.</span></span>  
  
 <span data-ttu-id="f0fde-147">\ [rozhraní ICorDebugBlockingObjectEnum –](icordebugblockingobjectenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-147">[ICorDebugBlockingObjectEnum Interface](icordebugblockingobjectenum-interface.md)\</span></span>
 <span data-ttu-id="f0fde-148">Poskytuje enumerátor pro seznam struktur [CorDebugBlockingObject –](cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="f0fde-148">Provides an enumerator for a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
 <span data-ttu-id="f0fde-149">\ [rozhraní ICorDebugBoxValue](icordebugboxvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-149">[ICorDebugBoxValue Interface](icordebugboxvalue-interface.md)\</span></span>
 <span data-ttu-id="f0fde-150">Podtřída `ICorDebugHeapValue`, která představuje zabalený objekt třídy hodnot.</span><span class="sxs-lookup"><span data-stu-id="f0fde-150">A subclass of `ICorDebugHeapValue` that represents a boxed value class object.</span></span>  
  
 <span data-ttu-id="f0fde-151">\ [rozhraní ICorDebugBreakpoint](icordebugbreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-151">[ICorDebugBreakpoint Interface](icordebugbreakpoint-interface.md)\</span></span>
 <span data-ttu-id="f0fde-152">Představuje zarážku ve funkci nebo bod sledování na hodnotě.</span><span class="sxs-lookup"><span data-stu-id="f0fde-152">Represents a breakpoint in a function or a watch point on a value.</span></span>  
  
 <span data-ttu-id="f0fde-153">\ [rozhraní ICorDebugBreakpointEnum](icordebugbreakpointenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-153">[ICorDebugBreakpointEnum Interface](icordebugbreakpointenum-interface.md)\</span></span>
 <span data-ttu-id="f0fde-154">Implementuje metody `ICorDebugEnum` a vytvoří výčet `ICorDebugBreakpoint` polí.</span><span class="sxs-lookup"><span data-stu-id="f0fde-154">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugBreakpoint` arrays.</span></span>  
  
 <span data-ttu-id="f0fde-155">\ [rozhraní ICorDebugChain](icordebugchain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-155">[ICorDebugChain Interface](icordebugchain-interface.md)\</span></span>
 <span data-ttu-id="f0fde-156">Představuje segment fyzického nebo logického zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="f0fde-156">Represents a segment of a physical or logical call stack.</span></span>  
  
 <span data-ttu-id="f0fde-157">\ [rozhraní ICorDebugChainEnum](icordebugchainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-157">[ICorDebugChainEnum Interface](icordebugchainenum-interface.md)\</span></span>
 <span data-ttu-id="f0fde-158">Implementuje metody `ICorDebugEnum` a vytvoří výčet `ICorDebugChain` polí.</span><span class="sxs-lookup"><span data-stu-id="f0fde-158">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugChain` arrays.</span></span>  
  
 <span data-ttu-id="f0fde-159">\ [rozhraní ICorDebugClass](icordebugclass-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-159">[ICorDebugClass Interface](icordebugclass-interface.md)\</span></span>
 <span data-ttu-id="f0fde-160">Představuje typ, který může být základní nebo komplexní (tj. definovaný uživatelem).</span><span class="sxs-lookup"><span data-stu-id="f0fde-160">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="f0fde-161">Pokud je typ obecný, `ICorDebugClass` představuje obecný typ bez instancí.</span><span class="sxs-lookup"><span data-stu-id="f0fde-161">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
 <span data-ttu-id="f0fde-162">\ [rozhraní ICorDebugClass2](icordebugclass2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-162">[ICorDebugClass2 Interface](icordebugclass2-interface.md)\</span></span>
 <span data-ttu-id="f0fde-163">Představuje obecnou třídu nebo třídu s parametrem metody typu <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="f0fde-163">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="f0fde-164">Toto rozhraní rozšiřuje `ICorDebugClass`.</span><span class="sxs-lookup"><span data-stu-id="f0fde-164">This interface extends `ICorDebugClass`.</span></span>  
  
 <span data-ttu-id="f0fde-165">\ [rozhraní ICorDebugCode](icordebugcode-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-165">[ICorDebugCode Interface](icordebugcode-interface1.md)\</span></span>
 <span data-ttu-id="f0fde-166">Představuje segment kódu jazyka MSIL nebo nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="f0fde-166">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
 <span data-ttu-id="f0fde-167">\ [rozhraní ICorDebugCode2](icordebugcode2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-167">[ICorDebugCode2 Interface](icordebugcode2-interface.md)\</span></span>
 <span data-ttu-id="f0fde-168">Poskytuje metody, které rozšiřuje možnosti `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="f0fde-168">Provides methods that extend the capabilities of `ICorDebugCode`.</span></span>  
  
 <span data-ttu-id="f0fde-169">\ [rozhraní ICorDebugCode3](icordebugcode3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-169">[ICorDebugCode3 Interface](icordebugcode3-interface.md)\</span></span>
 <span data-ttu-id="f0fde-170">Poskytuje metodu, která rozšiřuje [ICorDebugCode](icordebugcode-interface1.md) a [ICorDebugCode2](icordebugcode2-interface.md) a poskytuje informace o spravované návratové hodnotě.</span><span class="sxs-lookup"><span data-stu-id="f0fde-170">Provides a method that extends [ICorDebugCode](icordebugcode-interface1.md) and [ICorDebugCode2](icordebugcode2-interface.md) to provide information about a managed return value.</span></span>  
  
 <span data-ttu-id="f0fde-171">\ [rozhraní ICorDebugCode4](icordebugcode4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-171">[ICorDebugCode4 Interface](icordebugcode4-interface.md)\</span></span>
 <span data-ttu-id="f0fde-172">Poskytuje metodu, která umožňuje ladicímu programu vytvořit výčet místních proměnných a argumentů ve funkci.</span><span class="sxs-lookup"><span data-stu-id="f0fde-172">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="f0fde-173">\ [rozhraní ICorDebugCodeEnum](icordebugcodeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-173">[ICorDebugCodeEnum Interface](icordebugcodeenum-interface.md)\</span></span>
 <span data-ttu-id="f0fde-174">Implementuje metody `ICorDebugEnum` a vytvoří výčet `ICorDebugCode` polí.</span><span class="sxs-lookup"><span data-stu-id="f0fde-174">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugCode` arrays.</span></span>  
  
 <span data-ttu-id="f0fde-175">\ [rozhraní ICorDebugComObjectValue](icordebugcomobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-175">[ICorDebugComObjectValue Interface](icordebugcomobjectvalue-interface.md)\</span></span>
 <span data-ttu-id="f0fde-176">Poskytuje metody pro načtení objektů z mezipaměti rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f0fde-176">Provides methods to retrieve cached interface objects.</span></span>  
  
 <span data-ttu-id="f0fde-177">\ [rozhraní ICorDebugContext –](icordebugcontext-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-177">[ICorDebugContext Interface](icordebugcontext-interface.md)\</span></span>
 <span data-ttu-id="f0fde-178">Představuje objekt kontextu.</span><span class="sxs-lookup"><span data-stu-id="f0fde-178">Represents a context object.</span></span> <span data-ttu-id="f0fde-179">Toto rozhraní zatím nebylo implementováno.</span><span class="sxs-lookup"><span data-stu-id="f0fde-179">This interface has not been implemented yet.</span></span>  
  
 <span data-ttu-id="f0fde-180">\ [rozhraní ICorDebugController](icordebugcontroller-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-180">[ICorDebugController Interface](icordebugcontroller-interface.md)\</span></span>
 <span data-ttu-id="f0fde-181">Představuje obor, buď <xref:System.Diagnostics.Process>, nebo <xref:System.AppDomain>, ve kterém lze ovládat kontext provádění kódu.</span><span class="sxs-lookup"><span data-stu-id="f0fde-181">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
 <span data-ttu-id="f0fde-182">\ [rozhraní ICorDebugDataTarget](icordebugdatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-182">[ICorDebugDataTarget Interface](icordebugdatatarget-interface.md)\</span></span>
 <span data-ttu-id="f0fde-183">Poskytuje rozhraní zpětného volání, které poskytuje přístup ke konkrétnímu cílovému procesu.</span><span class="sxs-lookup"><span data-stu-id="f0fde-183">Provides a callback interface that provides access to a particular target process.</span></span>  
  
 <span data-ttu-id="f0fde-184">\ [rozhraní ICorDebugDataTarget2](icordebugdatatarget2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-184">[ICorDebugDataTarget2 Interface](icordebugdatatarget2-interface.md)\</span></span>
 <span data-ttu-id="f0fde-185">Logicky rozšiřuje rozhraní [ICorDebugDataTarget](icordebugdatatarget-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="f0fde-185">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="f0fde-186">**K dispozici pouze v .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="f0fde-186">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="f0fde-187">\ [rozhraní ICorDebugDataTarget3](icordebugdatatarget3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-187">[ICorDebugDataTarget3 Interface](icordebugdatatarget3-interface.md)\</span></span>
 <span data-ttu-id="f0fde-188">Logicky rozšiřuje rozhraní [ICorDebugDataTarget](icordebugdatatarget-interface.md) , aby poskytovala informace o načtených modulech.</span><span class="sxs-lookup"><span data-stu-id="f0fde-188">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span> <span data-ttu-id="f0fde-189">**K dispozici pouze v .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="f0fde-189">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="f0fde-190">\ [rozhraní ICorDebugDebugEvent](icordebugdebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-190">[ICorDebugDebugEvent Interface](icordebugdebugevent-interface.md)\</span></span>
 <span data-ttu-id="f0fde-191">Definuje základní rozhraní, ze kterého jsou odvozeny všechny události `ICorDebug` ladění.</span><span class="sxs-lookup"><span data-stu-id="f0fde-191">Defines the base interface from which all `ICorDebug` debug events derive.</span></span> <span data-ttu-id="f0fde-192">**K dispozici pouze v .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="f0fde-192">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="f0fde-193">\ [rozhraní ICorDebugEditAndContinueErrorInfo](icordebugeditandcontinueerrorinfo-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-193">[ICorDebugEditAndContinueErrorInfo Interface](icordebugeditandcontinueerrorinfo-interface.md)\</span></span>
 <span data-ttu-id="f0fde-194">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="f0fde-194">Obsolete.</span></span> <span data-ttu-id="f0fde-195">Toto rozhraní nepoužívejte.</span><span class="sxs-lookup"><span data-stu-id="f0fde-195">Do not use this interface.</span></span>  
  
 <span data-ttu-id="f0fde-196">\ [rozhraní ICorDebugEditAndContinueSnapshot](icordebugeditandcontinuesnapshot-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-196">[ICorDebugEditAndContinueSnapshot Interface](icordebugeditandcontinuesnapshot-interface.md)\</span></span>
 <span data-ttu-id="f0fde-197">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="f0fde-197">Obsolete.</span></span> <span data-ttu-id="f0fde-198">Toto rozhraní nepoužívejte.</span><span class="sxs-lookup"><span data-stu-id="f0fde-198">Do not use this interface.</span></span>  
  
 <span data-ttu-id="f0fde-199">\ [rozhraní ICorDebugEnum](icordebugenum-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-199">[ICorDebugEnum Interface](icordebugenum-interface1.md)\</span></span>
 <span data-ttu-id="f0fde-200">Slouží jako abstraktní základní rozhraní pro enumerátory ladění.</span><span class="sxs-lookup"><span data-stu-id="f0fde-200">Serves as the abstract base interface for debugging enumerators.</span></span>  
  
 <span data-ttu-id="f0fde-201">\ [rozhraní ICorDebugErrorInfoEnum](icordebugerrorinfoenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-201">[ICorDebugErrorInfoEnum Interface](icordebugerrorinfoenum-interface.md)\</span></span>
 <span data-ttu-id="f0fde-202">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="f0fde-202">Obsolete.</span></span> <span data-ttu-id="f0fde-203">Toto rozhraní nepoužívejte.</span><span class="sxs-lookup"><span data-stu-id="f0fde-203">Do not use this interface.</span></span>  
  
 <span data-ttu-id="f0fde-204">\ [rozhraní ICorDebugEval](icordebugeval-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-204">[ICorDebugEval Interface](icordebugeval-interface.md)\</span></span>
 <span data-ttu-id="f0fde-205">Poskytuje metody povolující ladicímu programu spouštět kód v kontextu laděného kódu.</span><span class="sxs-lookup"><span data-stu-id="f0fde-205">Provides methods to enable the debugger to execute code within the context of the code being debugged.</span></span>  
  
 <span data-ttu-id="f0fde-206">\ [rozhraní ICorDebugEval2](icordebugeval2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-206">[ICorDebugEval2 Interface](icordebugeval2-interface.md)\</span></span>
 <span data-ttu-id="f0fde-207">Rozšiřuje `ICorDebugEval` pro zajištění podpory pro obecné typy.</span><span class="sxs-lookup"><span data-stu-id="f0fde-207">Extends `ICorDebugEval` to provide support for generic types.</span></span>  
  
 <span data-ttu-id="f0fde-208">\ [rozhraní ICorDebugExceptionDebugEvent](icordebugexceptiondebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-208">[ICorDebugExceptionDebugEvent Interface](icordebugexceptiondebugevent-interface.md)\</span></span>
 <span data-ttu-id="f0fde-209">Rozšiřuje rozhraní [ICorDebugDebugEvent](icordebugdebugevent-interface.md) pro podporu událostí výjimek.</span><span class="sxs-lookup"><span data-stu-id="f0fde-209">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support exception events.</span></span> <span data-ttu-id="f0fde-210">**K dispozici pouze v .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="f0fde-210">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="f0fde-211">\ [rozhraní ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-211">[ICorDebugExceptionObjectCallStackEnum Interface](icordebugexceptionobjectcallstackenum-interface.md)\</span></span>
 <span data-ttu-id="f0fde-212">Poskytuje enumerátor pro informace zásobníku volání, který je vložený v objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="f0fde-212">Provides an enumerator for call stack information that is embedded in an exception object.</span></span>  
  
 <span data-ttu-id="f0fde-213">\ [rozhraní ICorDebugExceptionObjectValue –](icordebugexceptionobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-213">[ICorDebugExceptionObjectValue Interface](icordebugexceptionobjectvalue-interface.md)\</span></span>
 <span data-ttu-id="f0fde-214">Rozšiřuje rozhraní [ICorDebugObjectValue](icordebugobjectvalue-interface.md) pro poskytnutí informací o trasování zásobníku z objektu spravované výjimky.</span><span class="sxs-lookup"><span data-stu-id="f0fde-214">Extends the [ICorDebugObjectValue](icordebugobjectvalue-interface.md) interface to provide stack trace information from a managed exception object.</span></span>  
  
 <span data-ttu-id="f0fde-215">\ [rozhraní ICorDebugFrame](icordebugframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-215">[ICorDebugFrame Interface](icordebugframe-interface.md)\</span></span>
 <span data-ttu-id="f0fde-216">Představuje snímek aktuálního zásobníku.</span><span class="sxs-lookup"><span data-stu-id="f0fde-216">Represents a frame on the current stack.</span></span>  
  
 <span data-ttu-id="f0fde-217">\ [rozhraní ICorDebugFrameEnum](icordebugframeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-217">[ICorDebugFrameEnum Interface](icordebugframeenum-interface.md)\</span></span>
 <span data-ttu-id="f0fde-218">Implementuje metody `ICorDebugEnum` a vytvoří výčet `ICorDebugFrame` polí.</span><span class="sxs-lookup"><span data-stu-id="f0fde-218">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugFrame` arrays.</span></span>  
  
 <span data-ttu-id="f0fde-219">\ [rozhraní ICorDebugFunction](icordebugfunction-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-219">[ICorDebugFunction Interface](icordebugfunction-interface1.md)\</span></span>
 <span data-ttu-id="f0fde-220">Představuje spravovanou funkci nebo metodu.</span><span class="sxs-lookup"><span data-stu-id="f0fde-220">Represents a managed function or method.</span></span>  
  
 <span data-ttu-id="f0fde-221">\ [rozhraní ICorDebugFunction2](icordebugfunction2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-221">[ICorDebugFunction2 Interface](icordebugfunction2-interface.md)\</span></span>
 <span data-ttu-id="f0fde-222">Logicky rozšiřuje `ICorDebugFunction` a poskytuje podporu pro Pouze můj kód krokování prostřednictvím ladění.</span><span class="sxs-lookup"><span data-stu-id="f0fde-222">Logically extends `ICorDebugFunction` to provide support for Just My Code step-through debugging.</span></span>  
  
 <span data-ttu-id="f0fde-223">\ [rozhraní ICorDebugFunction3](icordebugfunction3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-223">[ICorDebugFunction3 Interface](icordebugfunction3-interface.md)\</span></span>
 <span data-ttu-id="f0fde-224">Logicky rozšiřuje rozhraní [ICorDebugFunction](icordebugfunction-interface1.md) a poskytuje přístup k kódu z požadavku ReJIT.</span><span class="sxs-lookup"><span data-stu-id="f0fde-224">Logically extends the [ICorDebugFunction](icordebugfunction-interface1.md) interface to provide access to code from a ReJIT request.</span></span>  
  
 <span data-ttu-id="f0fde-225">\ [rozhraní ICorDebugFunctionBreakpoint](icordebugfunctionbreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-225">[ICorDebugFunctionBreakpoint Interface](icordebugfunctionbreakpoint-interface.md)\</span></span>
 <span data-ttu-id="f0fde-226">Rozšiřuje `ICorDebugBreakpoint` o podporu zarážek v rámci funkcí.</span><span class="sxs-lookup"><span data-stu-id="f0fde-226">Extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
 <span data-ttu-id="f0fde-227">\ [rozhraní ICorDebugGCReferenceEnum –](icordebuggcreferenceenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-227">[ICorDebugGCReferenceEnum Interface](icordebuggcreferenceenum-interface.md)\</span></span>
 <span data-ttu-id="f0fde-228">Poskytuje enumerátor pro objekty, které budou uvolněny z paměti.</span><span class="sxs-lookup"><span data-stu-id="f0fde-228">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
 <span data-ttu-id="f0fde-229">\ [rozhraní ICorDebugGenericValue](icordebuggenericvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-229">[ICorDebugGenericValue Interface](icordebuggenericvalue-interface.md)\</span></span>
 <span data-ttu-id="f0fde-230">Podtřída `ICorDebugValue`, která se vztahuje na všechny hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f0fde-230">A subclass of `ICorDebugValue` that applies to all values.</span></span> <span data-ttu-id="f0fde-231">Toto rozhraní poskytuje metody Get a Set pro hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f0fde-231">This interface provides Get and Set methods for the value.</span></span>  
  
 <span data-ttu-id="f0fde-232">\ [rozhraní ICorDebugGuidToTypeEnum –](icordebugguidtotypeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-232">[ICorDebugGuidToTypeEnum Interface](icordebugguidtotypeenum-interface.md)\</span></span>
 <span data-ttu-id="f0fde-233">Poskytuje enumerátor pro objekt, který mapuje identifikátory GUID a odpovídající objekty `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="f0fde-233">Provides an enumerator for an object that maps GUIDs and their corresponding `ICorDebugType` objects.</span></span>  
  
 <span data-ttu-id="f0fde-234">\ [rozhraní ICorDebugHandleValue](icordebughandlevalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-234">[ICorDebugHandleValue Interface](icordebughandlevalue-interface.md)\</span></span>
 <span data-ttu-id="f0fde-235">Podtřída `ICorDebugReferenceValue` reprezentující referenční hodnotu, do které ladicí program vytvořil popisovač pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="f0fde-235">A subclass of `ICorDebugReferenceValue` that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
 <span data-ttu-id="f0fde-236">\ [rozhraní ICorDebugHeapEnum –](icordebugheapenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-236">[ICorDebugHeapEnum Interface](icordebugheapenum-interface.md)\</span></span>
 <span data-ttu-id="f0fde-237">Poskytuje enumerátor pro objekty na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="f0fde-237">Provides an enumerator for objects on the managed heap.</span></span>  
  
 <span data-ttu-id="f0fde-238">\ [rozhraní ICorDebugHeapSegmentEnum –](icordebugheapsegmentenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-238">[ICorDebugHeapSegmentEnum Interface](icordebugheapsegmentenum-interface.md)\</span></span>
 <span data-ttu-id="f0fde-239">Poskytuje enumerátor pro oblasti paměti spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="f0fde-239">Provides an enumerator for the memory regions of the managed heap.</span></span>  
  
 <span data-ttu-id="f0fde-240">\ [rozhraní ICorDebugHeapValue](icordebugheapvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-240">[ICorDebugHeapValue Interface](icordebugheapvalue-interface.md)\</span></span>
 <span data-ttu-id="f0fde-241">Podtřída `ICorDebugValue`, která představuje objekt, který byl shromážděn systémem uvolňování paměti CLR.</span><span class="sxs-lookup"><span data-stu-id="f0fde-241">A subclass of `ICorDebugValue` that represents an object that has been collected by the CLR garbage collector.</span></span>  
  
 <span data-ttu-id="f0fde-242">\ [rozhraní ICorDebugHeapValue2](icordebugheapvalue2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-242">[ICorDebugHeapValue2 Interface](icordebugheapvalue2-interface1.md)\</span></span>
 <span data-ttu-id="f0fde-243">Rozšíření `ICorDebugHeapValue`, které poskytuje podporu pro obslužné rutiny modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="f0fde-243">An extension of `ICorDebugHeapValue` that provides support for runtime handles.</span></span>  
  
 <span data-ttu-id="f0fde-244">\ [rozhraní ICorDebugHeapValue3](icordebugheapvalue3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-244">[ICorDebugHeapValue3 Interface](icordebugheapvalue3-interface.md)\</span></span>
 <span data-ttu-id="f0fde-245">Zpřístupní vlastnosti uzamčení sledování objektů.</span><span class="sxs-lookup"><span data-stu-id="f0fde-245">Exposes the monitor lock properties of objects.</span></span>  
  
 <span data-ttu-id="f0fde-246">\ [rozhraní ICorDebugILCode](icordebugilcode-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-246">[ICorDebugILCode Interface](icordebugilcode-interface.md)\</span></span>
 <span data-ttu-id="f0fde-247">Představuje segment kódu zprostředkujícího jazyka (IL).</span><span class="sxs-lookup"><span data-stu-id="f0fde-247">Represents a segment of intermediate language (IL) code.</span></span>  
  
 <span data-ttu-id="f0fde-248">\ [rozhraní ICorDebugILCode2](icordebugilcode2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-248">[ICorDebugILCode2 Interface](icordebugilcode2-interface.md)\</span></span>
 <span data-ttu-id="f0fde-249">Logicky rozšiřuje rozhraní [ICorDebugILCode](icordebugilcode-interface.md) a poskytuje metody, které vracejí token pro místní proměnnou funkce a které mapují posuny instrumentované zprostředkujícího jazyka (IL) profileru na původní posunutí metody Il.</span><span class="sxs-lookup"><span data-stu-id="f0fde-249">Logically extends the [ICorDebugILCode](icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
 <span data-ttu-id="f0fde-250">\ [rozhraní ICorDebugILFrame](icordebugilframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-250">[ICorDebugILFrame Interface](icordebugilframe-interface.md)\</span></span>
 <span data-ttu-id="f0fde-251">Představuje rámec zásobníku kódu MSIL.</span><span class="sxs-lookup"><span data-stu-id="f0fde-251">Represents a stack frame of MSIL code.</span></span>  
  
 <span data-ttu-id="f0fde-252">\ [rozhraní ICorDebugILFrame2](icordebugilframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-252">[ICorDebugILFrame2 Interface](icordebugilframe2-interface.md)\</span></span>
 <span data-ttu-id="f0fde-253">Logické rozšíření `ICorDebugILFrame`.</span><span class="sxs-lookup"><span data-stu-id="f0fde-253">A logical extension of `ICorDebugILFrame`.</span></span>  
  
 <span data-ttu-id="f0fde-254">\ [rozhraní ICorDebugILFrame3](icordebugilframe3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-254">[ICorDebugILFrame3 Interface](icordebugilframe3-interface.md)\</span></span>
 <span data-ttu-id="f0fde-255">Poskytuje metodu, která zapouzdřuje vrácenou hodnotu funkce.</span><span class="sxs-lookup"><span data-stu-id="f0fde-255">Provides a method that encapsulates the return value of a function.</span></span>  
  
 <span data-ttu-id="f0fde-256">\ [rozhraní ICorDebugILFrame4](icordebugilframe4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-256">[ICorDebugILFrame4 Interface](icordebugilframe4-interface.md)\</span></span>
 <span data-ttu-id="f0fde-257">Poskytuje metody, které umožňují přístup k místním proměnným a kódu v bloku rozhraní IL (Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="f0fde-257">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="f0fde-258">Parametr určuje, jestli má ladicí program přístup k proměnným a kódu přidanému v profileru ReJIT instrumentace.</span><span class="sxs-lookup"><span data-stu-id="f0fde-258">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
 <span data-ttu-id="f0fde-259">\ [rozhraní ICorDebugInstanceFieldSymbol](icordebuginstancefieldsymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-259">[ICorDebugInstanceFieldSymbol Interface](icordebuginstancefieldsymbol-interface.md)\</span></span>
 <span data-ttu-id="f0fde-260">Představuje informace o symbolech ladění pro pole instance.</span><span class="sxs-lookup"><span data-stu-id="f0fde-260">Represents the debug symbol information for an instance field.</span></span> <span data-ttu-id="f0fde-261">**K dispozici pouze v .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="f0fde-261">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="f0fde-262">\ [rozhraní ICorDebugInternalFrame](icordebuginternalframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-262">[ICorDebugInternalFrame Interface](icordebuginternalframe-interface.md)\</span></span>
 <span data-ttu-id="f0fde-263">Určuje typy rámců pro ladicí program.</span><span class="sxs-lookup"><span data-stu-id="f0fde-263">Identifies frame types for the debugger.</span></span>  
  
 <span data-ttu-id="f0fde-264">\ [rozhraní ICorDebugInternalFrame2](icordebuginternalframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-264">[ICorDebugInternalFrame2 Interface](icordebuginternalframe2-interface.md)\</span></span>
 <span data-ttu-id="f0fde-265">Obsahuje informace o vnitřních rámečcích, včetně adresy zásobníku a pozice ve vztahu k [ICorDebugFrame](icordebugframe-interface.md) objektům.</span><span class="sxs-lookup"><span data-stu-id="f0fde-265">Provides information about internal frames, including stack address and position in relation to [ICorDebugFrame](icordebugframe-interface.md) objects.</span></span>  
  
 <span data-ttu-id="f0fde-266">\ [rozhraní metoda ICorDebugLoadedModule](icordebugloadedmodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-266">[ICorDebugLoadedModule Interface](icordebugloadedmodule-interface.md)\</span></span>
 <span data-ttu-id="f0fde-267">Poskytuje informace o načteném modulu.</span><span class="sxs-lookup"><span data-stu-id="f0fde-267">Provides information about a loaded module.</span></span> <span data-ttu-id="f0fde-268">**K dispozici pouze v .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="f0fde-268">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="f0fde-269">\ [rozhraní ICorDebugManagedCallback](icordebugmanagedcallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-269">[ICorDebugManagedCallback Interface](icordebugmanagedcallback-interface.md)\</span></span>
 <span data-ttu-id="f0fde-270">Poskytuje metody pro zpětná volání procesu ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="f0fde-270">Provides methods to process debugger callbacks.</span></span>  
  
 <span data-ttu-id="f0fde-271">\ [rozhraní ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-271">[ICorDebugManagedCallback2 Interface](icordebugmanagedcallback2-interface.md)\</span></span>
 <span data-ttu-id="f0fde-272">Poskytuje metody pro podporu zpracování výjimek ladicího programu a spravované pomocníky ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="f0fde-272">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="f0fde-273">`ICorDebugManagedCallback2` je logické rozšíření `ICorDebugManagedCallback`.</span><span class="sxs-lookup"><span data-stu-id="f0fde-273">`ICorDebugManagedCallback2` is a logical extension of `ICorDebugManagedCallback`.</span></span>  
  
 <span data-ttu-id="f0fde-274">\ [rozhraní ICorDebugManagedCallback3 –](icordebugmanagedcallback3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-274">[ICorDebugManagedCallback3 Interface](icordebugmanagedcallback3-interface.md)\</span></span>
 <span data-ttu-id="f0fde-275">Poskytuje metodu zpětného volání, která určuje, že povolené vlastní oznámení ladicího programu bylo vyvoláno.</span><span class="sxs-lookup"><span data-stu-id="f0fde-275">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
 <span data-ttu-id="f0fde-276">\ [rozhraní ICorDebugMDA](icordebugmda-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-276">[ICorDebugMDA Interface](icordebugmda-interface.md)\</span></span>
 <span data-ttu-id="f0fde-277">Představuje zprávu pomocníka spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="f0fde-277">Represents a managed debugging assistant (MDA) message.</span></span>  
  
 <span data-ttu-id="f0fde-278">\ [rozhraní ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-278">[ICorDebugMemoryBuffer Interface](icordebugmemorybuffer-interface.md)\</span></span>
 <span data-ttu-id="f0fde-279">Představuje vyrovnávací paměť v paměti.</span><span class="sxs-lookup"><span data-stu-id="f0fde-279">Represents an in-memory buffer.</span></span> <span data-ttu-id="f0fde-280">**K dispozici pouze v .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="f0fde-280">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="f0fde-281">\ [rozhraní ICorDebugMergedAssemblyRecord](icordebugmergedassemblyrecord-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-281">[ICorDebugMergedAssemblyRecord Interface](icordebugmergedassemblyrecord-interface.md)\</span></span>
 <span data-ttu-id="f0fde-282">Poskytuje informace o sloučeném sestavení.</span><span class="sxs-lookup"><span data-stu-id="f0fde-282">Provides information about a merged assembly.</span></span> <span data-ttu-id="f0fde-283">**K dispozici pouze v .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="f0fde-283">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="f0fde-284">\ [rozhraní ICorDebugMetaDataLocator –](icordebugmetadatalocator-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-284">[ICorDebugMetaDataLocator Interface](icordebugmetadatalocator-interface.md)\</span></span>
 <span data-ttu-id="f0fde-285">Poskytuje informace metadat k ladicímu programu.</span><span class="sxs-lookup"><span data-stu-id="f0fde-285">Provides metadata information to the debugger.</span></span>  
  
 <span data-ttu-id="f0fde-286">\ [rozhraní ICorDebugModule](icordebugmodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-286">[ICorDebugModule Interface](icordebugmodule-interface.md)\</span></span>
 <span data-ttu-id="f0fde-287">Představuje modul CLR, který je spustitelný soubor nebo dynamická knihovna (DLL).</span><span class="sxs-lookup"><span data-stu-id="f0fde-287">Represents a CLR module, which is either an executable or a dynamic-link library (DLL).</span></span>  
  
 <span data-ttu-id="f0fde-288">\ [rozhraní ICorDebugModule2](icordebugmodule2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-288">[ICorDebugModule2 Interface](icordebugmodule2-interface.md)\</span></span>
 <span data-ttu-id="f0fde-289">Slouží jako logické rozšíření `ICorDebugModule`.</span><span class="sxs-lookup"><span data-stu-id="f0fde-289">Serves as a logical extension to `ICorDebugModule`.</span></span>  
  
 <span data-ttu-id="f0fde-290">\ [rozhraní ICorDebugModule3](icordebugmodule3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-290">[ICorDebugModule3 Interface](icordebugmodule3-interface.md)\</span></span>
 <span data-ttu-id="f0fde-291">Vytvoří čtečku symbolů pro dynamický modul.</span><span class="sxs-lookup"><span data-stu-id="f0fde-291">Creates a symbol reader for a dynamic module.</span></span>  
  
 <span data-ttu-id="f0fde-292">\ [rozhraní ICorDebugModuleBreakpoint](icordebugmodulebreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-292">[ICorDebugModuleBreakpoint Interface](icordebugmodulebreakpoint-interface.md)\</span></span>
 <span data-ttu-id="f0fde-293">Rozšiřuje `ICorDebugBreakpoint` o poskytnutí přístupu ke konkrétním modulům.</span><span class="sxs-lookup"><span data-stu-id="f0fde-293">Extends `ICorDebugBreakpoint` to provide access to specific modules.</span></span>  
  
 <span data-ttu-id="f0fde-294">\ [rozhraní ICorDebugModuleDebugEvent](icordebugmoduledebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-294">[ICorDebugModuleDebugEvent Interface](icordebugmoduledebugevent-interface.md)\</span></span>
 <span data-ttu-id="f0fde-295">Rozšiřuje rozhraní [ICorDebugDebugEvent](icordebugdebugevent-interface.md) pro podporu událostí na úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="f0fde-295">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support module-level events.</span></span> <span data-ttu-id="f0fde-296">**K dispozici pouze v .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="f0fde-296">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="f0fde-297">\ [rozhraní ICorDebugModuleEnum](icordebugmoduleenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-297">[ICorDebugModuleEnum Interface](icordebugmoduleenum-interface.md)\</span></span>
 <span data-ttu-id="f0fde-298">Implementuje metody `ICorDebugEnum` a vytvoří výčet `ICorDebugModule` polí.</span><span class="sxs-lookup"><span data-stu-id="f0fde-298">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugModule` arrays.</span></span>  
  
 <span data-ttu-id="f0fde-299">\ [rozhraní ICorDebugMutableDataTarget](icordebugmutabledatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-299">[ICorDebugMutableDataTarget Interface](icordebugmutabledatatarget-interface.md)\</span></span>
 <span data-ttu-id="f0fde-300">Rozšiřuje rozhraní [ICorDebugDataTarget](icordebugdatatarget-interface.md) pro podporu proměnlivých datových cílů.</span><span class="sxs-lookup"><span data-stu-id="f0fde-300">Extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
 <span data-ttu-id="f0fde-301">\ [rozhraní ICorDebugNativeFrame](icordebugnativeframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-301">[ICorDebugNativeFrame Interface](icordebugnativeframe-interface.md)\</span></span>
 <span data-ttu-id="f0fde-302">Specializovaná implementace `ICorDebugFrame` používaná pro nativní rámce.</span><span class="sxs-lookup"><span data-stu-id="f0fde-302">A specialized implementation of `ICorDebugFrame` used for native frames.</span></span>  
  
 <span data-ttu-id="f0fde-303">\ [rozhraní ICorDebugNativeFrame2](icordebugnativeframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-303">[ICorDebugNativeFrame2 Interface](icordebugnativeframe2-interface.md)\</span></span>
 <span data-ttu-id="f0fde-304">Poskytuje metody, které testují podřízené a nadřazené vztahy rámce.</span><span class="sxs-lookup"><span data-stu-id="f0fde-304">Provides methods that test for child and parent frame relationships.</span></span>  
  
 <span data-ttu-id="f0fde-305">\ [rozhraní ICorDebugObjectEnum](icordebugobjectenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-305">[ICorDebugObjectEnum Interface](icordebugobjectenum-interface.md)\</span></span>
 <span data-ttu-id="f0fde-306">Implementuje metody `ICorDebugEnum` a vytvoří výčet polí objektů podle jejich relativních virtuálních adres (RVA).</span><span class="sxs-lookup"><span data-stu-id="f0fde-306">Implements `ICorDebugEnum` methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
 <span data-ttu-id="f0fde-307">\ [rozhraní ICorDebugObjectValue](icordebugobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-307">[ICorDebugObjectValue Interface](icordebugobjectvalue-interface.md)\</span></span>
 <span data-ttu-id="f0fde-308">Podtřída `ICorDebugValue`, která představuje hodnotu, která obsahuje objekt.</span><span class="sxs-lookup"><span data-stu-id="f0fde-308">A subclass of `ICorDebugValue` that represents a value that contains an object.</span></span>  
  
 <span data-ttu-id="f0fde-309">\ [rozhraní ICorDebugObjectValue2](icordebugobjectvalue2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-309">[ICorDebugObjectValue2 Interface](icordebugobjectvalue2-interface.md)\</span></span>
 <span data-ttu-id="f0fde-310">Rozšiřuje `ICorDebugObjectValue` pro podporu dědičnosti a přepsání.</span><span class="sxs-lookup"><span data-stu-id="f0fde-310">Extends `ICorDebugObjectValue` to support inheritance and overrides.</span></span>  
  
 <span data-ttu-id="f0fde-311">\ [rozhraní ICorDebugProcess](icordebugprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-311">[ICorDebugProcess Interface](icordebugprocess-interface.md)\</span></span>
 <span data-ttu-id="f0fde-312">Představuje proces, který spouští spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="f0fde-312">Represents a process that is executing managed code.</span></span>  
  
 <span data-ttu-id="f0fde-313">\ [rozhraní ICorDebugProcess2](icordebugprocess2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-313">[ICorDebugProcess2 Interface](icordebugprocess2-interface1.md)\</span></span>
 <span data-ttu-id="f0fde-314">Logické rozšíření `ICorDebugProcess`.</span><span class="sxs-lookup"><span data-stu-id="f0fde-314">A logical extension of `ICorDebugProcess`.</span></span>  
  
 <span data-ttu-id="f0fde-315">\ [rozhraní ICorDebugProcess3 –](icordebugprocess3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-315">[ICorDebugProcess3 Interface](icordebugprocess3-interface.md)\</span></span>
 <span data-ttu-id="f0fde-316">Řídí vlastní oznámení ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="f0fde-316">Controls custom debugger notifications.</span></span>

 <span data-ttu-id="f0fde-317">\ [rozhraní ICorDebugProcess4](icordebugprocess4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-317">[ICorDebugProcess4 Interface](icordebugprocess4-interface.md)\</span></span>
 <span data-ttu-id="f0fde-318">Poskytuje podporu pro vzdálené řízení spouštění procesů.</span><span class="sxs-lookup"><span data-stu-id="f0fde-318">Provides support for out of process execution control.</span></span>
  
 <span data-ttu-id="f0fde-319">\ [rozhraní ICorDebugProcess5](icordebugprocess5-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-319">[ICorDebugProcess5 Interface](icordebugprocess5-interface.md)\</span></span>
 <span data-ttu-id="f0fde-320">Rozšiřuje rozhraní [ICorDebugProcess](icordebugprocess-interface.md) pro podporu přístupu ke spravované haldě, k poskytnutí informací o uvolnění paměti spravovaných objektů a určení, zda ladicí program načítá obrázky z místní mezipaměti nativních bitových kopií aplikace.</span><span class="sxs-lookup"><span data-stu-id="f0fde-320">Extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application's local native image cache.</span></span>  
  
 <span data-ttu-id="f0fde-321">\ [rozhraní ICorDebugProcess6](icordebugprocess6-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-321">[ICorDebugProcess6 Interface](icordebugprocess6-interface.md)\</span></span>
 <span data-ttu-id="f0fde-322">Logicky rozšiřuje rozhraní [ICorDebugProcess](icordebugprocess-interface.md) a povoluje funkce jako dekódování spravovaných událostí ladění, které jsou zakódované v nativních událostech ladění výjimek a rozdělování virtuálních modulů.</span><span class="sxs-lookup"><span data-stu-id="f0fde-322">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span> <span data-ttu-id="f0fde-323">**K dispozici pouze v .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="f0fde-323">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="f0fde-324">\ [rozhraní ICorDebugProcess7](icordebugprocess7-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-324">[ICorDebugProcess7 Interface](icordebugprocess7-interface.md)\</span></span>
 <span data-ttu-id="f0fde-325">Poskytuje metodu, která konfiguruje ladicí program pro zpracování aktualizací metadat v paměti v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="f0fde-325">Provides a method that configures the debugger to handle in-memory metadata updates in the target process.</span></span>  
  
 <span data-ttu-id="f0fde-326">\ [rozhraní ICorDebugProcess8](icordebugprocess8-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-326">[ICorDebugProcess8 Interface](icordebugprocess8-interface.md)\</span></span>
 <span data-ttu-id="f0fde-327">Logicky rozšiřuje rozhraní [ICorDebugProcess](icordebugprocess-interface.md) a povoluje nebo zakazuje určité typy zpětných volání výjimek [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="f0fde-327">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable or disable certain types of [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
 <span data-ttu-id="f0fde-328">\ [rozhraní ICorDebugProcessEnum](icordebugprocessenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-328">[ICorDebugProcessEnum Interface](icordebugprocessenum-interface.md)\</span></span>
 <span data-ttu-id="f0fde-329">Implementuje metody `ICorDebugEnum` a vytvoří výčet `ICorDebugProcess` polí.</span><span class="sxs-lookup"><span data-stu-id="f0fde-329">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugProcess` arrays.</span></span>  
  
 <span data-ttu-id="f0fde-330">\ [rozhraní ICorDebugReferenceValue](icordebugreferencevalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-330">[ICorDebugReferenceValue Interface](icordebugreferencevalue-interface.md)\</span></span>
 <span data-ttu-id="f0fde-331">Podtřída `ICorDebugValue`, která podporuje typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="f0fde-331">A subclass of `ICorDebugValue` that supports reference types.</span></span>  
  
 <span data-ttu-id="f0fde-332">\ [rozhraní ICorDebugRegisterSet](icordebugregisterset-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-332">[ICorDebugRegisterSet Interface](icordebugregisterset-interface.md)\</span></span>
 <span data-ttu-id="f0fde-333">Představuje sadu registrů, které jsou k dispozici v počítači, který aktuálně spouští kód.</span><span class="sxs-lookup"><span data-stu-id="f0fde-333">Represents the set of registers available on the machine that is currently executing code.</span></span>  
  
 <span data-ttu-id="f0fde-334">\ [rozhraní ICorDebugRegisterSet2](icordebugregisterset2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-334">[ICorDebugRegisterSet2 Interface](icordebugregisterset2-interface.md)\</span></span>
 <span data-ttu-id="f0fde-335">Rozšiřuje možnosti `ICorDebugRegisterSet` pro hardwarové platformy, které mají více než 64 registrů.</span><span class="sxs-lookup"><span data-stu-id="f0fde-335">Extends the capabilities of `ICorDebugRegisterSet` for hardware platforms that have more than 64 registers.</span></span>  
  
 <span data-ttu-id="f0fde-336">\ [rozhraní ICorDebugRemote](icordebugremote-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-336">[ICorDebugRemote Interface](icordebugremote-interface.md)\</span></span>
 <span data-ttu-id="f0fde-337">Umožňuje spustit nebo připojit spravovaný ladicí program ke vzdálenému cílovému procesu.</span><span class="sxs-lookup"><span data-stu-id="f0fde-337">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
 <span data-ttu-id="f0fde-338">\ [rozhraní ICorDebugRemoteTarget](icordebugremotetarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-338">[ICorDebugRemoteTarget Interface](icordebugremotetarget-interface.md)\</span></span>
 <span data-ttu-id="f0fde-339">Poskytuje metody umožňující ladit aplikace programu Silverlight v prostředí CLR.</span><span class="sxs-lookup"><span data-stu-id="f0fde-339">Provides methods that enable you to debug Silverlight-based applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="f0fde-340">\ [rozhraní ICorDebugRuntimeUnwindableFrame –](icordebugruntimeunwindableframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-340">[ICorDebugRuntimeUnwindableFrame Interface](icordebugruntimeunwindableframe-interface.md)\</span></span>
 <span data-ttu-id="f0fde-341">Poskytuje podporu pro nespravované metody, které vyžadují modul CLR k uvolnění rámce.</span><span class="sxs-lookup"><span data-stu-id="f0fde-341">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
 <span data-ttu-id="f0fde-342">\ [rozhraní ICorDebugStackWalk](icordebugstackwalk-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-342">[ICorDebugStackWalk Interface](icordebugstackwalk-interface.md)\</span></span>
 <span data-ttu-id="f0fde-343">Poskytuje metody pro získání spravovaných metod nebo rámců v zásobníku vlákna.</span><span class="sxs-lookup"><span data-stu-id="f0fde-343">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
 <span data-ttu-id="f0fde-344">\ [rozhraní ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-344">[ICorDebugStaticFieldSymbol Interface](icordebugstaticfieldsymbol-interface.md)\</span></span>
 <span data-ttu-id="f0fde-345">Představuje informace o symbolech ladění pro statické pole.</span><span class="sxs-lookup"><span data-stu-id="f0fde-345">Represents the debug symbol information for a static field.</span></span> <span data-ttu-id="f0fde-346">**K dispozici pouze v .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="f0fde-346">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="f0fde-347">\ [rozhraní ICorDebugStepper](icordebugstepper-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-347">[ICorDebugStepper Interface](icordebugstepper-interface.md)\</span></span>
 <span data-ttu-id="f0fde-348">Představuje krok ve spuštění kódu, který je prováděn pomocí ladicího programu, slouží jako identifikátor mezi vydáním a dokončením příkazu a umožňuje krok zrušit.</span><span class="sxs-lookup"><span data-stu-id="f0fde-348">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
 <span data-ttu-id="f0fde-349">\ [rozhraní ICorDebugStepper2](icordebugstepper2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-349">[ICorDebugStepper2 Interface](icordebugstepper2-interface1.md)\</span></span>
 <span data-ttu-id="f0fde-350">Poskytuje podporu ladění Pouze můj kód (JMC).</span><span class="sxs-lookup"><span data-stu-id="f0fde-350">Provides support for Just My Code (JMC) debugging.</span></span>  
  
 <span data-ttu-id="f0fde-351">\ [rozhraní ICorDebugStepperEnum](icordebugstepperenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-351">[ICorDebugStepperEnum Interface](icordebugstepperenum-interface.md)\</span></span>
 <span data-ttu-id="f0fde-352">Implementuje metody `ICorDebugEnum` a vytvoří výčet `ICorDebugStepper` polí.</span><span class="sxs-lookup"><span data-stu-id="f0fde-352">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugStepper` arrays.</span></span>  
  
 <span data-ttu-id="f0fde-353">\ [rozhraní ICorDebugStringValue](icordebugstringvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-353">[ICorDebugStringValue Interface](icordebugstringvalue-interface.md)\</span></span>
 <span data-ttu-id="f0fde-354">Podtřída `ICorDebugHeapValue`, která se vztahuje na řetězcové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f0fde-354">A subclass of `ICorDebugHeapValue` that applies to string values.</span></span>  
  
 <span data-ttu-id="f0fde-355">\ [rozhraní ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-355">[ICorDebugSymbolProvider Interface](icordebugsymbolprovider-interface.md)\</span></span>
 <span data-ttu-id="f0fde-356">Poskytuje metody, které lze použít k načtení informací o symbolech ladění.</span><span class="sxs-lookup"><span data-stu-id="f0fde-356">Provides methods that can be used to retrieve debug symbol information.</span></span> <span data-ttu-id="f0fde-357">**K dispozici pouze v .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="f0fde-357">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="f0fde-358">\ [rozhraní ICorDebugSymbolProvider2](icordebugsymbolprovider2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-358">[ICorDebugSymbolProvider2 Interface](icordebugsymbolprovider2-interface.md)\</span></span>
 <span data-ttu-id="f0fde-359">Logicky rozšiřuje rozhraní [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) a načítá Další informace o symbolech ladění.</span><span class="sxs-lookup"><span data-stu-id="f0fde-359">Logically extends the [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span> <span data-ttu-id="f0fde-360">**K dispozici pouze v .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="f0fde-360">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="f0fde-361">\ [rozhraní ICorDebugThread](icordebugthread-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-361">[ICorDebugThread Interface](icordebugthread-interface.md)\</span></span>
 <span data-ttu-id="f0fde-362">Představuje vlákno v procesu.</span><span class="sxs-lookup"><span data-stu-id="f0fde-362">Represents a thread in a process.</span></span> <span data-ttu-id="f0fde-363">Doba životnosti `ICorDebugThread` instance je stejná jako životnost vlákna, které představuje.</span><span class="sxs-lookup"><span data-stu-id="f0fde-363">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
 <span data-ttu-id="f0fde-364">\ [rozhraní ICorDebugThread2](icordebugthread2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-364">[ICorDebugThread2 Interface](icordebugthread2-interface.md)\</span></span>
 <span data-ttu-id="f0fde-365">Slouží jako logické rozšíření `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="f0fde-365">Serves as a logical extension to `ICorDebugThread`.</span></span>  
  
 <span data-ttu-id="f0fde-366">\ [rozhraní ICorDebugThread3](icordebugthread3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-366">[ICorDebugThread3 Interface](icordebugthread3-interface.md)\</span></span>
 <span data-ttu-id="f0fde-367">Poskytuje vstupní bod pro [ICorDebugStackWalk](icordebugstackwalk-interface.md) a odpovídající rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f0fde-367">Provides the entry point to the [ICorDebugStackWalk](icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
 <span data-ttu-id="f0fde-368">\ [rozhraní ICorDebugThread4](icordebugthread4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-368">[ICorDebugThread4 Interface](icordebugthread4-interface.md)\</span></span>
 <span data-ttu-id="f0fde-369">Poskytuje informace o blokování vlákna.</span><span class="sxs-lookup"><span data-stu-id="f0fde-369">Provides thread blocking information.</span></span>  
  
 <span data-ttu-id="f0fde-370">\ [rozhraní ICorDebugThreadEnum](icordebugthreadenum-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-370">[ICorDebugThreadEnum Interface](icordebugthreadenum-interface1.md)\</span></span>
 <span data-ttu-id="f0fde-371">Implementuje metody `ICorDebugEnum` a vytvoří výčet `ICorDebugThread` polí.</span><span class="sxs-lookup"><span data-stu-id="f0fde-371">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugThread` arrays.</span></span>  
  
 <span data-ttu-id="f0fde-372">\ [rozhraní ICorDebugType](icordebugtype-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-372">[ICorDebugType Interface](icordebugtype-interface.md)\</span></span>
 <span data-ttu-id="f0fde-373">Představuje typ, který může být základní nebo komplexní (tj. definovaný uživatelem).</span><span class="sxs-lookup"><span data-stu-id="f0fde-373">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="f0fde-374">Pokud je typ obecný, `ICorDebugType` představuje obecný typ s instancemi.</span><span class="sxs-lookup"><span data-stu-id="f0fde-374">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
 <span data-ttu-id="f0fde-375">\ [rozhraní ICorDebugType2](icordebugtype2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-375">[ICorDebugType2 Interface](icordebugtype2-interface.md)\</span></span>
 <span data-ttu-id="f0fde-376">Rozšiřuje rozhraní [ICorDebugType](icordebugtype-interface.md) , aby získal identifikátor typu základního typu nebo komplexního (uživatelsky definovaného) typu.</span><span class="sxs-lookup"><span data-stu-id="f0fde-376">Extends the [ICorDebugType](icordebugtype-interface.md) interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
 <span data-ttu-id="f0fde-377">\ [rozhraní ICorDebugTypeEnum](icordebugtypeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-377">[ICorDebugTypeEnum Interface](icordebugtypeenum-interface.md)\</span></span>
 <span data-ttu-id="f0fde-378">Implementuje metody `ICorDebugEnum` a vytvoří výčet `ICorDebugType` polí.</span><span class="sxs-lookup"><span data-stu-id="f0fde-378">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugType` arrays.</span></span>  
  
 <span data-ttu-id="f0fde-379">\ [rozhraní ICorDebugUnmanagedCallback –](icordebugunmanagedcallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-379">[ICorDebugUnmanagedCallback Interface](icordebugunmanagedcallback-interface.md)\</span></span>
 <span data-ttu-id="f0fde-380">Poskytuje oznámení nativních událostí, které přímo nesouvisejí s CLR.</span><span class="sxs-lookup"><span data-stu-id="f0fde-380">Provides notification of native events that are not directly related to the CLR.</span></span>  
  
 <span data-ttu-id="f0fde-381">[ICorDebugValue](icordebugvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-381">[ICorDebugValue](icordebugvalue-interface.md)</span></span>\
 <span data-ttu-id="f0fde-382">Představuje hodnotu pro čtení nebo zápis v laděném procesu.</span><span class="sxs-lookup"><span data-stu-id="f0fde-382">Represents a read or write value in the process being debugged.</span></span>  
  
 <span data-ttu-id="f0fde-383">[ICorDebugValue2](icordebugvalue2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-383">[ICorDebugValue2](icordebugvalue2-interface.md)</span></span>\
 <span data-ttu-id="f0fde-384">Rozšiřuje `ICorDebugValue` a poskytuje podporu pro `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="f0fde-384">Extends `ICorDebugValue` to provide support for `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="f0fde-385">\ [rozhraní ICorDebugValue3 –](icordebugvalue3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-385">[ICorDebugValue3 Interface](icordebugvalue3-interface.md)\</span></span>
 <span data-ttu-id="f0fde-386">Rozšiřuje rozhraní "ICorDebugValue" a "ICorDebugValue2" tak, aby poskytovala podporu pro pole, která jsou větší než 2 GB.</span><span class="sxs-lookup"><span data-stu-id="f0fde-386">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
 <span data-ttu-id="f0fde-387">[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-387">[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)</span></span>\
 <span data-ttu-id="f0fde-388">Rozšiřuje `ICorDebugBreakpoint` o poskytnutí přístupu k určitým hodnotám.</span><span class="sxs-lookup"><span data-stu-id="f0fde-388">Extends `ICorDebugBreakpoint` to provide access to specific values.</span></span>  
  
 <span data-ttu-id="f0fde-389">[ICorDebugValueEnum](icordebugvalueenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-389">[ICorDebugValueEnum](icordebugvalueenum-interface.md)</span></span>\
 <span data-ttu-id="f0fde-390">Implementuje metody `ICorDebugEnum` a vytvoří výčet `ICorDebugValue` polí.</span><span class="sxs-lookup"><span data-stu-id="f0fde-390">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugValue` arrays.</span></span>  
  
 <span data-ttu-id="f0fde-391">\ [rozhraní ICorDebugVariableHome](icordebugvariablehome-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-391">[ICorDebugVariableHome Interface](icordebugvariablehome-interface.md)\</span></span>
 <span data-ttu-id="f0fde-392">Představuje místní proměnnou nebo argument funkce.</span><span class="sxs-lookup"><span data-stu-id="f0fde-392">Represents a local variable or argument of a function.</span></span>  
  
 <span data-ttu-id="f0fde-393">\ [rozhraní ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-393">[ICorDebugVariableHomeEnum Interface](icordebugvariablehomeenum-interface.md)\</span></span>
 <span data-ttu-id="f0fde-394">Poskytuje enumerátor pro místní proměnné a argumenty ve funkci.</span><span class="sxs-lookup"><span data-stu-id="f0fde-394">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="f0fde-395">\ [rozhraní ICorDebugVariableSymbol](icordebugvariablesymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-395">[ICorDebugVariableSymbol Interface](icordebugvariablesymbol-interface.md)\</span></span>
 <span data-ttu-id="f0fde-396">Načte informace o ladicím symbolu pro proměnnou.</span><span class="sxs-lookup"><span data-stu-id="f0fde-396">Retrieves the debug symbol information for a variable.</span></span> <span data-ttu-id="f0fde-397">**K dispozici pouze v .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="f0fde-397">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="f0fde-398">\ [rozhraní ICorDebugVirtualUnwinder](icordebugvirtualunwinder-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-398">[ICorDebugVirtualUnwinder Interface](icordebugvirtualunwinder-interface.md)\</span></span>
 <span data-ttu-id="f0fde-399">Poskytuje metody, které vám pomůžou při odvíjení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="f0fde-399">Provides methods to help in stack unwinding.</span></span> <span data-ttu-id="f0fde-400">**K dispozici pouze v .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="f0fde-400">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="f0fde-401">\ [rozhraní ICorPublish –](icorpublish-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-401">[ICorPublish Interface](icorpublish-interface.md)\</span></span>
 <span data-ttu-id="f0fde-402">Slouží jako obecné rozhraní pro procesy publikování.</span><span class="sxs-lookup"><span data-stu-id="f0fde-402">Serves as the general interface for the publishing processes.</span></span>  
  
 <span data-ttu-id="f0fde-403">\ [rozhraní ICorPublishAppDomain](icorpublishappdomain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-403">[ICorPublishAppDomain Interface](icorpublishappdomain-interface.md)\</span></span>
 <span data-ttu-id="f0fde-404">Představuje a poskytuje informace o aplikační doméně.</span><span class="sxs-lookup"><span data-stu-id="f0fde-404">Represents and provides information about an application domain.</span></span>  
  
 <span data-ttu-id="f0fde-405">\ [rozhraní ICorPublishAppDomainEnum –](icorpublishappdomainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-405">[ICorPublishAppDomainEnum Interface](icorpublishappdomainenum-interface.md)\</span></span>
 <span data-ttu-id="f0fde-406">Poskytuje metody, které procházejí kolekci `ICorPublishAppDomain` objektů, které aktuálně existují v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="f0fde-406">Provides methods that traverse a collection of `ICorPublishAppDomain` objects that currently exist within a process.</span></span>  
  
 <span data-ttu-id="f0fde-407">\ [rozhraní ICorPublishEnum](icorpublishenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-407">[ICorPublishEnum Interface](icorpublishenum-interface.md)\</span></span>
 <span data-ttu-id="f0fde-408">Slouží jako abstraktní základ pro enumerátory publikování.</span><span class="sxs-lookup"><span data-stu-id="f0fde-408">Serves as the abstract base for publishing enumerators.</span></span>  
  
 <span data-ttu-id="f0fde-409">\ [rozhraní ICorPublishProcess](icorpublishprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-409">[ICorPublishProcess Interface](icorpublishprocess-interface.md)\</span></span>
 <span data-ttu-id="f0fde-410">Poskytuje metody, které přistupují k informacím o procesu.</span><span class="sxs-lookup"><span data-stu-id="f0fde-410">Provides methods that access information about a process.</span></span>  
  
 <span data-ttu-id="f0fde-411">\ [rozhraní ICorPublishProcessEnum –](icorpublishprocessenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-411">[ICorPublishProcessEnum Interface](icorpublishprocessenum-interface.md)\</span></span>
 <span data-ttu-id="f0fde-412">Poskytuje metody, které procházejí kolekci `ICorPublishProcess` objektů.</span><span class="sxs-lookup"><span data-stu-id="f0fde-412">Provides methods that traverse a collection of `ICorPublishProcess` objects.</span></span>  

 <span data-ttu-id="f0fde-413">\ [rozhraní ISOSDacInterface](isosdacinterface-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-413">[ISOSDacInterface Interface](isosdacinterface-interface.md)\</span></span>
 <span data-ttu-id="f0fde-414">Poskytuje pomocné metody pro přístup k datům z `SOS`.</span><span class="sxs-lookup"><span data-stu-id="f0fde-414">Provides helper methods to access data from `SOS`.</span></span>

 <span data-ttu-id="f0fde-415">\ [rozhraní IXCLRDataMethodDefinition](ixclrdatamethoddefinition-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-415">[IXCLRDataMethodDefinition Interface](ixclrdatamethoddefinition-interface.md)\</span></span>
 <span data-ttu-id="f0fde-416">Poskytuje metody pro dotazování na informace o definici metody.</span><span class="sxs-lookup"><span data-stu-id="f0fde-416">Provides methods for querying information about a method definition.</span></span>
 
 <span data-ttu-id="f0fde-417">\ [rozhraní IXCLRDataMethodInstance](ixclrdatamethodinstance-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-417">[IXCLRDataMethodInstance Interface](ixclrdatamethodinstance-interface.md)\</span></span>
 <span data-ttu-id="f0fde-418">Poskytuje metody pro dotazování na informace o instanci metody.</span><span class="sxs-lookup"><span data-stu-id="f0fde-418">Provides methods for querying information about a method instance.</span></span>
 
 <span data-ttu-id="f0fde-419">\ [rozhraní IXCLRDataModule](ixclrdatamodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-419">[IXCLRDataModule Interface](ixclrdatamodule-interface.md)\</span></span>
 <span data-ttu-id="f0fde-420">Poskytuje metody pro dotazování na informace o načteném modulu.</span><span class="sxs-lookup"><span data-stu-id="f0fde-420">Provides methods for querying information about a loaded module.</span></span>
 
 <span data-ttu-id="f0fde-421">\ [rozhraní IXCLRDataProcess](ixclrdataprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-421">[IXCLRDataProcess Interface](ixclrdataprocess-interface.md)\</span></span>
 <span data-ttu-id="f0fde-422">Poskytuje metody pro dotazování na informace o procesu.</span><span class="sxs-lookup"><span data-stu-id="f0fde-422">Provides methods for querying information about a process.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="f0fde-423">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="f0fde-423">Related Sections</span></span>  
 <span data-ttu-id="f0fde-424">[Ladění tříd typu coclass](debugging-coclasses.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-424">[Debugging Coclasses](debugging-coclasses.md)</span></span>\
 <span data-ttu-id="f0fde-425">[Ladění globálních statických funkcí](debugging-global-static-functions.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-425">[Debugging Global Static Functions](debugging-global-static-functions.md)</span></span>\
 <span data-ttu-id="f0fde-426">\ [výčtů ladění](debugging-enumerations.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-426">[Debugging Enumerations](debugging-enumerations.md)\</span></span>
 <span data-ttu-id="f0fde-427">\ [struktury ladění](debugging-structures.md)</span><span class="sxs-lookup"><span data-stu-id="f0fde-427">[Debugging Structures](debugging-structures.md)\</span></span>
