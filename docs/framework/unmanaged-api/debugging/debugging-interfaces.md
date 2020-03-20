---
title: Debugging – rozhraní
ms.date: 02/07/2019
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
ms.openlocfilehash: c4b9cdc2bc90096ab7c3b041bd8aa2742b48c35c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179167"
---
# <a name="debugging-interfaces"></a><span data-ttu-id="2d109-102">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2d109-102">Debugging Interfaces</span></span>
<span data-ttu-id="2d109-103">Tato část popisuje nespravovaná rozhraní, která zpracovávají ladění programu, který je spouštěn v modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="2d109-103">This section describes the unmanaged interfaces that handle the debugging of a program that is executing in the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2d109-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="2d109-104">In This Section</span></span>  
 <span data-ttu-id="2d109-105">[Rozhraní ICLRDataEnumMemoryRegions](iclrdataenummemoryregions-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-105">[ICLRDataEnumMemoryRegions Interface](iclrdataenummemoryregions-interface.md)</span></span>\
 <span data-ttu-id="2d109-106">Představuje způsob, jak vytvořit výčet oblastí paměti zadaných volajícími.</span><span class="sxs-lookup"><span data-stu-id="2d109-106">Provides a method to enumerate regions of memory that are specified by callers.</span></span>  
  
 <span data-ttu-id="2d109-107">[Rozhraní ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-107">[ICLRDataEnumMemoryRegionsCallback Interface](iclrdataenummemoryregionscallback-interface.md)</span></span>\
 <span data-ttu-id="2d109-108">Poskytuje metodu zpětného volání pro `EnumMemoryRegions` hlášení ladicího programu, což je výsledek pokusu o výčet zadané oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="2d109-108">Provides a callback method for `EnumMemoryRegions` to report to the debugger, the result of an attempt to enumerate a specified region of memory.</span></span>  
  
 <span data-ttu-id="2d109-109">[Rozhraní ICLRDataTarget](iclrdatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-109">[ICLRDataTarget Interface](iclrdatatarget-interface.md)</span></span>\
 <span data-ttu-id="2d109-110">Poskytuje metody pro interakci s cílovým procesem CLR.</span><span class="sxs-lookup"><span data-stu-id="2d109-110">Provides methods for interaction with a target CLR process.</span></span>  
  
 <span data-ttu-id="2d109-111">[Rozhraní ICLRDataTarget2](iclrdatatarget2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-111">[ICLRDataTarget2 Interface](iclrdatatarget2-interface.md)</span></span>\
 <span data-ttu-id="2d109-112">`ICLRDataTarget` Podtřída, která se používá vrstvou služeb přístupu k datům k manipulaci s oblastmi virtuální paměti v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="2d109-112">A subclass of `ICLRDataTarget` that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
 <span data-ttu-id="2d109-113">[Rozhraní ICLRDataTarget3](iclrdatatarget3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-113">[ICLRDataTarget3 Interface](iclrdatatarget3-interface.md)</span></span>\
 <span data-ttu-id="2d109-114">Podtřída [ICLRDataTarget2,](iclrdatatarget2-interface.md) která poskytuje přístup k informacím o výjimce.</span><span class="sxs-lookup"><span data-stu-id="2d109-114">A subclass of [ICLRDataTarget2](iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
 <span data-ttu-id="2d109-115">[Rozhraní ICLR Debugging](iclrdebugging-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-115">[ICLRDebugging Interface](iclrdebugging-interface.md)</span></span>\
 <span data-ttu-id="2d109-116">Poskytuje metody, které zpracovávají načítání a uvolňování modulů pro ladění.</span><span class="sxs-lookup"><span data-stu-id="2d109-116">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
 <span data-ttu-id="2d109-117">[Rozhraní ICLR DebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-117">[ICLRDebuggingLibraryProvider Interface](iclrdebugginglibraryprovider-interface.md)</span></span>\
 <span data-ttu-id="2d109-118">Zahrnuje [metodu ProvideLibrary Method,](iclrdebugginglibraryprovider-providelibrary-method.md) která získá rozhraní pro zpětné volání zprostředkovatele knihovny, které umožňuje knihovny ladění specifické pro běžné moduly runtime specifické pro zpracování a načtení na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="2d109-118">Includes the [ProvideLibrary Method](iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
 <span data-ttu-id="2d109-119">[Rozhraní ICLRMetadataLocator](iclrmetadatalocator-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-119">[ICLRMetadataLocator Interface](iclrmetadatalocator-interface.md)</span></span>\
 <span data-ttu-id="2d109-120">Rozhraní používané vrstvou služeb přístupu k datům k vyhledání metadat sestavení v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="2d109-120">Interface used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
 <span data-ttu-id="2d109-121">[Rozhraní ICorDebug](icordebug-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-121">[ICorDebug Interface](icordebug-interface.md)</span></span>\
 <span data-ttu-id="2d109-122">Poskytuje metody, které umožňují vývojářům ladit aplikace v prostředí CLR.</span><span class="sxs-lookup"><span data-stu-id="2d109-122">Provides methods that allow developers to debug applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="2d109-123">[Rozhraní ICorDebugAppDomain](icordebugappdomain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-123">[ICorDebugAppDomain Interface](icordebugappdomain-interface.md)</span></span>\
 <span data-ttu-id="2d109-124">Poskytuje metody pro ladění domén aplikace.</span><span class="sxs-lookup"><span data-stu-id="2d109-124">Provides methods for debugging application domains.</span></span>  
  
 <span data-ttu-id="2d109-125">[Rozhraní ICorDebugAppDomain2](icordebugappdomain2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-125">[ICorDebugAppDomain2 Interface](icordebugappdomain2-interface.md)</span></span>\
 <span data-ttu-id="2d109-126">Poskytuje metody pro práci s poli, ukazateli, ukazateli na funkci a typy ByRef.</span><span class="sxs-lookup"><span data-stu-id="2d109-126">Provides methods to work with arrays, pointers, function pointers, and ByRef types.</span></span> <span data-ttu-id="2d109-127">Toto rozhraní je `ICorDebugAppDomain` rozšíření rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2d109-127">This interface is an extension of the `ICorDebugAppDomain` interface.</span></span>  
  
 <span data-ttu-id="2d109-128">[Rozhraní ICorDebugAppDomain3](icordebugappdomain3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-128">[ICorDebugAppDomain3 Interface](icordebugappdomain3-interface.md)</span></span>\
 <span data-ttu-id="2d109-129">Poskytuje metody pro práci s typy prostředí Windows Runtime v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="2d109-129">Provides methods to work with the Windows Runtime types in an application domain.</span></span> <span data-ttu-id="2d109-130">Toto rozhraní je `ICorDebugAppDomain` rozšíření `ICorDebugAppDomain2` a rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2d109-130">This interface is an extension of the `ICorDebugAppDomain` and `ICorDebugAppDomain2` interfaces.</span></span>  
  
 <span data-ttu-id="2d109-131">[Rozhraní ICorDebugAppDomain4](icordebugappdomain4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-131">[ICorDebugAppDomain4 Interface](icordebugappdomain4-interface.md)</span></span>\
 <span data-ttu-id="2d109-132">Logicky rozšiřuje rozhraní [ICorDebugAppDomain](icordebugappdomain-interface.md) získat spravovaný objekt z com volatelné obálky.</span><span class="sxs-lookup"><span data-stu-id="2d109-132">Logically extends the [ICorDebugAppDomain](icordebugappdomain-interface.md) interface to get a managed object from a COM callable wrapper.</span></span>  
  
 <span data-ttu-id="2d109-133">[Rozhraní ICorDebugAppDomainEnum](icordebugappdomainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-133">[ICorDebugAppDomainEnum Interface](icordebugappdomainenum-interface.md)</span></span>\
 <span data-ttu-id="2d109-134">Poskytuje metodu, která vrací `ICorDebugAppDomain` zadaný počet hodnot začínajících na dalším místě ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="2d109-134">Provides a method that returns a specified number of `ICorDebugAppDomain` values starting at the next location in the enumeration.</span></span>  
  
 <span data-ttu-id="2d109-135">[Rozhraní ICorDebugArrayValue](icordebugarrayvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-135">[ICorDebugArrayValue Interface](icordebugarrayvalue-interface.md)</span></span>\
 <span data-ttu-id="2d109-136">`ICorDebugHeapValue` Podtřída, která představuje jednorozměrné nebo vícerozměrné pole.</span><span class="sxs-lookup"><span data-stu-id="2d109-136">A subclass of `ICorDebugHeapValue` that represents a single-dimensional or multi-dimensional array.</span></span>  
  
 <span data-ttu-id="2d109-137">[Rozhraní ICorDebugAssembly](icordebugassembly-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-137">[ICorDebugAssembly Interface](icordebugassembly-interface.md)</span></span>\
 <span data-ttu-id="2d109-138">Představuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="2d109-138">Represents an assembly.</span></span>  
  
 <span data-ttu-id="2d109-139">[Rozhraní ICorDebugAssembly2](icordebugassembly2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-139">[ICorDebugAssembly2 Interface](icordebugassembly2-interface.md)</span></span>\
 <span data-ttu-id="2d109-140">Představuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="2d109-140">Represents an assembly.</span></span> <span data-ttu-id="2d109-141">Toto rozhraní je `ICorDebugAssembly` rozšíření rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2d109-141">This interface is an extension of the `ICorDebugAssembly` interface.</span></span>  
  
 <span data-ttu-id="2d109-142">[Rozhraní ICorDebugAssembly3](icordebugassembly3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-142">[ICorDebugAssembly3 Interface](icordebugassembly3-interface.md)</span></span>\
 <span data-ttu-id="2d109-143">Logicky rozšiřuje rozhraní [ICorDebugAssembly](icordebugassembly-interface.md) poskytnout podporu pro sestavení kontejnerů a jejich obsažené sestavení.</span><span class="sxs-lookup"><span data-stu-id="2d109-143">Logically extends the [ICorDebugAssembly](icordebugassembly-interface.md) interface to provide support for container assemblies and their contained assemblies.</span></span> <span data-ttu-id="2d109-144">**K dispozici pouze na nativním rozhraní .NET.**</span><span class="sxs-lookup"><span data-stu-id="2d109-144">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="2d109-145">[Rozhraní ICorDebugAssemblyEnum](icordebugassemblyenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-145">[ICorDebugAssemblyEnum Interface](icordebugassemblyenum-interface.md)</span></span>\
 <span data-ttu-id="2d109-146">Implementuje `ICorDebugEnum` metody a vyjmenovává `ICorDebugAssembly` pole.</span><span class="sxs-lookup"><span data-stu-id="2d109-146">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugAssembly` arrays.</span></span>  
  
 <span data-ttu-id="2d109-147">[Rozhraní ICorDebugBlockingObjectEnum](icordebugblockingobjectenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-147">[ICorDebugBlockingObjectEnum Interface](icordebugblockingobjectenum-interface.md)</span></span>\
 <span data-ttu-id="2d109-148">Poskytuje čítač pro seznam [cordebugBlockingObject](cordebugblockingobject-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="2d109-148">Provides an enumerator for a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
 <span data-ttu-id="2d109-149">[Rozhraní ICorDebugBoxValue](icordebugboxvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-149">[ICorDebugBoxValue Interface](icordebugboxvalue-interface.md)</span></span>\
 <span data-ttu-id="2d109-150">`ICorDebugHeapValue` Podtřída, která představuje objekt třídy s krabicovou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="2d109-150">A subclass of `ICorDebugHeapValue` that represents a boxed value class object.</span></span>  
  
 <span data-ttu-id="2d109-151">[Rozhraní ICorDebugBreakpoint](icordebugbreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-151">[ICorDebugBreakpoint Interface](icordebugbreakpoint-interface.md)</span></span>\
 <span data-ttu-id="2d109-152">Představuje zarážku ve funkci nebo bod sledování na hodnotě.</span><span class="sxs-lookup"><span data-stu-id="2d109-152">Represents a breakpoint in a function or a watch point on a value.</span></span>  
  
 <span data-ttu-id="2d109-153">[Rozhraní ICorDebugBreakpointEnum](icordebugbreakpointenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-153">[ICorDebugBreakpointEnum Interface](icordebugbreakpointenum-interface.md)</span></span>\
 <span data-ttu-id="2d109-154">Implementuje `ICorDebugEnum` metody a vyjmenovává `ICorDebugBreakpoint` pole.</span><span class="sxs-lookup"><span data-stu-id="2d109-154">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugBreakpoint` arrays.</span></span>  
  
 <span data-ttu-id="2d109-155">[Rozhraní ICorDebugChain](icordebugchain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-155">[ICorDebugChain Interface](icordebugchain-interface.md)</span></span>\
 <span data-ttu-id="2d109-156">Představuje segment fyzického nebo logického zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="2d109-156">Represents a segment of a physical or logical call stack.</span></span>  
  
 <span data-ttu-id="2d109-157">[Rozhraní ICorDebugChainEnum](icordebugchainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-157">[ICorDebugChainEnum Interface](icordebugchainenum-interface.md)</span></span>\
 <span data-ttu-id="2d109-158">Implementuje `ICorDebugEnum` metody a vyjmenovává `ICorDebugChain` pole.</span><span class="sxs-lookup"><span data-stu-id="2d109-158">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugChain` arrays.</span></span>  
  
 <span data-ttu-id="2d109-159">[Rozhraní ICorDebugClass](icordebugclass-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-159">[ICorDebugClass Interface](icordebugclass-interface.md)</span></span>\
 <span data-ttu-id="2d109-160">Představuje typ, který může být základní nebo komplexní (tj. definovaný uživatelem).</span><span class="sxs-lookup"><span data-stu-id="2d109-160">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="2d109-161">Pokud je typ `ICorDebugClass` obecný, představuje neinstance obecný typ.</span><span class="sxs-lookup"><span data-stu-id="2d109-161">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
 <span data-ttu-id="2d109-162">[Rozhraní ICorDebugClass2](icordebugclass2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-162">[ICorDebugClass2 Interface](icordebugclass2-interface.md)</span></span>\
 <span data-ttu-id="2d109-163">Představuje obecnou třídu nebo třídu s <xref:System.Type>parametrem metody typu .</span><span class="sxs-lookup"><span data-stu-id="2d109-163">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="2d109-164">Toto rozhraní `ICorDebugClass`rozšiřuje .</span><span class="sxs-lookup"><span data-stu-id="2d109-164">This interface extends `ICorDebugClass`.</span></span>  
  
 <span data-ttu-id="2d109-165">[Rozhraní ICorDebugCode](icordebugcode-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-165">[ICorDebugCode Interface](icordebugcode-interface1.md)</span></span>\
 <span data-ttu-id="2d109-166">Představuje segment kódu jazyka MSIL nebo nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="2d109-166">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
 <span data-ttu-id="2d109-167">[Rozhraní ICorDebugCode2](icordebugcode2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-167">[ICorDebugCode2 Interface](icordebugcode2-interface.md)</span></span>\
 <span data-ttu-id="2d109-168">Poskytuje metody, které `ICorDebugCode`rozšiřují možnosti .</span><span class="sxs-lookup"><span data-stu-id="2d109-168">Provides methods that extend the capabilities of `ICorDebugCode`.</span></span>  
  
 <span data-ttu-id="2d109-169">[Rozhraní ICorDebugCode3](icordebugcode3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-169">[ICorDebugCode3 Interface](icordebugcode3-interface.md)</span></span>\
 <span data-ttu-id="2d109-170">Poskytuje metodu, která rozšiřuje [ICorDebugCode](icordebugcode-interface1.md) a [ICorDebugCode2](icordebugcode2-interface.md) poskytnout informace o spravované vrácená hodnota.</span><span class="sxs-lookup"><span data-stu-id="2d109-170">Provides a method that extends [ICorDebugCode](icordebugcode-interface1.md) and [ICorDebugCode2](icordebugcode2-interface.md) to provide information about a managed return value.</span></span>  
  
 <span data-ttu-id="2d109-171">[Rozhraní ICorDebugCode4](icordebugcode4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-171">[ICorDebugCode4 Interface](icordebugcode4-interface.md)</span></span>\
 <span data-ttu-id="2d109-172">Poskytuje metodu, která umožňuje ladicí program pro výčet místníproměnné a argumenty ve funkci.</span><span class="sxs-lookup"><span data-stu-id="2d109-172">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="2d109-173">[Rozhraní ICorDebugCodeEnum](icordebugcodeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-173">[ICorDebugCodeEnum Interface](icordebugcodeenum-interface.md)</span></span>\
 <span data-ttu-id="2d109-174">Implementuje `ICorDebugEnum` metody a vyjmenovává `ICorDebugCode` pole.</span><span class="sxs-lookup"><span data-stu-id="2d109-174">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugCode` arrays.</span></span>  
  
 <span data-ttu-id="2d109-175">[Rozhraní ICorDebugComObjectValue](icordebugcomobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-175">[ICorDebugComObjectValue Interface](icordebugcomobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="2d109-176">Poskytuje metody pro načtení objektů z mezipaměti rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2d109-176">Provides methods to retrieve cached interface objects.</span></span>  
  
 <span data-ttu-id="2d109-177">[Rozhraní ICorDebugContext](icordebugcontext-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-177">[ICorDebugContext Interface](icordebugcontext-interface.md)</span></span>\
 <span data-ttu-id="2d109-178">Představuje objekt kontextu.</span><span class="sxs-lookup"><span data-stu-id="2d109-178">Represents a context object.</span></span> <span data-ttu-id="2d109-179">Toto rozhraní zatím nebylo implementováno.</span><span class="sxs-lookup"><span data-stu-id="2d109-179">This interface has not been implemented yet.</span></span>  
  
 <span data-ttu-id="2d109-180">[Rozhraní ICorDebugController](icordebugcontroller-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-180">[ICorDebugController Interface](icordebugcontroller-interface.md)</span></span>\
 <span data-ttu-id="2d109-181">Představuje obor, <xref:System.Diagnostics.Process> nebo nebo <xref:System.AppDomain>, ve kterém může být řízen kontext spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="2d109-181">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
 <span data-ttu-id="2d109-182">[Rozhraní ICorDebugDataTarget](icordebugdatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-182">[ICorDebugDataTarget Interface](icordebugdatatarget-interface.md)</span></span>\
 <span data-ttu-id="2d109-183">Poskytuje rozhraní zpětného volání, které poskytuje přístup ke konkrétnímu cílovému procesu.</span><span class="sxs-lookup"><span data-stu-id="2d109-183">Provides a callback interface that provides access to a particular target process.</span></span>  
  
 <span data-ttu-id="2d109-184">[Rozhraní ICorDebugDataTarget2](icordebugdatatarget2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-184">[ICorDebugDataTarget2 Interface](icordebugdatatarget2-interface.md)</span></span>\
 <span data-ttu-id="2d109-185">Logicky rozšiřuje rozhraní [ICorDebugDataTarget.](icordebugdatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-185">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="2d109-186">**K dispozici pouze na nativním rozhraní .NET.**</span><span class="sxs-lookup"><span data-stu-id="2d109-186">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="2d109-187">[Rozhraní ICorDebugDataTarget3](icordebugdatatarget3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-187">[ICorDebugDataTarget3 Interface](icordebugdatatarget3-interface.md)</span></span>\
 <span data-ttu-id="2d109-188">Logicky rozšiřuje rozhraní [ICorDebugDataTarget](icordebugdatatarget-interface.md) poskytnout informace o načtených modulů.</span><span class="sxs-lookup"><span data-stu-id="2d109-188">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span> <span data-ttu-id="2d109-189">**K dispozici pouze na nativním rozhraní .NET.**</span><span class="sxs-lookup"><span data-stu-id="2d109-189">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="2d109-190">[Rozhraní ICorDebugDebugEvent](icordebugdebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-190">[ICorDebugDebugEvent Interface](icordebugdebugevent-interface.md)</span></span>\
 <span data-ttu-id="2d109-191">Definuje základní rozhraní, ze `ICorDebug` kterého jsou odvozeny všechny události ladění.</span><span class="sxs-lookup"><span data-stu-id="2d109-191">Defines the base interface from which all `ICorDebug` debug events derive.</span></span> <span data-ttu-id="2d109-192">**K dispozici pouze na nativním rozhraní .NET.**</span><span class="sxs-lookup"><span data-stu-id="2d109-192">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="2d109-193">[Rozhraní ICorDebugEditAndContinueErrorInfo](icordebugeditandcontinueerrorinfo-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-193">[ICorDebugEditAndContinueErrorInfo Interface](icordebugeditandcontinueerrorinfo-interface.md)</span></span>\
 <span data-ttu-id="2d109-194">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="2d109-194">Obsolete.</span></span> <span data-ttu-id="2d109-195">Toto rozhraní nepoužívejte.</span><span class="sxs-lookup"><span data-stu-id="2d109-195">Do not use this interface.</span></span>  
  
 <span data-ttu-id="2d109-196">[Rozhraní ICorDebugEditAndContinueSnapshot](icordebugeditandcontinuesnapshot-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-196">[ICorDebugEditAndContinueSnapshot Interface](icordebugeditandcontinuesnapshot-interface.md)</span></span>\
 <span data-ttu-id="2d109-197">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="2d109-197">Obsolete.</span></span> <span data-ttu-id="2d109-198">Toto rozhraní nepoužívejte.</span><span class="sxs-lookup"><span data-stu-id="2d109-198">Do not use this interface.</span></span>  
  
 <span data-ttu-id="2d109-199">[Rozhraní ICorDebugEnum](icordebugenum-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-199">[ICorDebugEnum Interface](icordebugenum-interface1.md)</span></span>\
 <span data-ttu-id="2d109-200">Slouží jako abstraktní základní rozhraní pro enumerátory ladění.</span><span class="sxs-lookup"><span data-stu-id="2d109-200">Serves as the abstract base interface for debugging enumerators.</span></span>  
  
 <span data-ttu-id="2d109-201">[Rozhraní ICorDebugErrorInfoEnum](icordebugerrorinfoenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-201">[ICorDebugErrorInfoEnum Interface](icordebugerrorinfoenum-interface.md)</span></span>\
 <span data-ttu-id="2d109-202">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="2d109-202">Obsolete.</span></span> <span data-ttu-id="2d109-203">Toto rozhraní nepoužívejte.</span><span class="sxs-lookup"><span data-stu-id="2d109-203">Do not use this interface.</span></span>  
  
 <span data-ttu-id="2d109-204">[Rozhraní ICorDebugEval](icordebugeval-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-204">[ICorDebugEval Interface](icordebugeval-interface.md)</span></span>\
 <span data-ttu-id="2d109-205">Poskytuje metody povolující ladicímu programu spouštět kód v kontextu laděného kódu.</span><span class="sxs-lookup"><span data-stu-id="2d109-205">Provides methods to enable the debugger to execute code within the context of the code being debugged.</span></span>  
  
 <span data-ttu-id="2d109-206">[Rozhraní ICorDebugEval2](icordebugeval2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-206">[ICorDebugEval2 Interface](icordebugeval2-interface.md)</span></span>\
 <span data-ttu-id="2d109-207">Rozšiřuje `ICorDebugEval` poskytovat podporu pro obecné typy.</span><span class="sxs-lookup"><span data-stu-id="2d109-207">Extends `ICorDebugEval` to provide support for generic types.</span></span>  
  
 <span data-ttu-id="2d109-208">[Rozhraní ICorDebugExceptionDebugEvent](icordebugexceptiondebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-208">[ICorDebugExceptionDebugEvent Interface](icordebugexceptiondebugevent-interface.md)</span></span>\
 <span data-ttu-id="2d109-209">Rozšiřuje rozhraní [ICorDebugDebugEvent](icordebugdebugevent-interface.md) pro podporu událostí výjimky.</span><span class="sxs-lookup"><span data-stu-id="2d109-209">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support exception events.</span></span> <span data-ttu-id="2d109-210">**K dispozici pouze na nativním rozhraní .NET.**</span><span class="sxs-lookup"><span data-stu-id="2d109-210">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="2d109-211">[Rozhraní ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-211">[ICorDebugExceptionObjectCallStackEnum Interface](icordebugexceptionobjectcallstackenum-interface.md)</span></span>\
 <span data-ttu-id="2d109-212">Poskytuje enumerátor pro informace zásobníku volání, který je vložený v objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="2d109-212">Provides an enumerator for call stack information that is embedded in an exception object.</span></span>  
  
 <span data-ttu-id="2d109-213">[Rozhraní ICorDebugExceptionObject](icordebugexceptionobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-213">[ICorDebugExceptionObjectValue Interface](icordebugexceptionobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="2d109-214">Rozšiřuje rozhraní [ICorDebugObjectValue](icordebugobjectvalue-interface.md) poskytnout informace o trasování zásobníku ze spravovaného objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="2d109-214">Extends the [ICorDebugObjectValue](icordebugobjectvalue-interface.md) interface to provide stack trace information from a managed exception object.</span></span>  
  
 <span data-ttu-id="2d109-215">[Rozhraní ICorDebugFrame](icordebugframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-215">[ICorDebugFrame Interface](icordebugframe-interface.md)</span></span>\
 <span data-ttu-id="2d109-216">Představuje snímek aktuálního zásobníku.</span><span class="sxs-lookup"><span data-stu-id="2d109-216">Represents a frame on the current stack.</span></span>  
  
 <span data-ttu-id="2d109-217">[Rozhraní ICorDebugFrameEnum](icordebugframeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-217">[ICorDebugFrameEnum Interface](icordebugframeenum-interface.md)</span></span>\
 <span data-ttu-id="2d109-218">Implementuje `ICorDebugEnum` metody a vyjmenovává `ICorDebugFrame` pole.</span><span class="sxs-lookup"><span data-stu-id="2d109-218">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugFrame` arrays.</span></span>  
  
 <span data-ttu-id="2d109-219">[Rozhraní ICorDebugFunction](icordebugfunction-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-219">[ICorDebugFunction Interface](icordebugfunction-interface1.md)</span></span>\
 <span data-ttu-id="2d109-220">Představuje spravovanou funkci nebo metodu.</span><span class="sxs-lookup"><span data-stu-id="2d109-220">Represents a managed function or method.</span></span>  
  
 <span data-ttu-id="2d109-221">[Rozhraní ICorDebugFunction2](icordebugfunction2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-221">[ICorDebugFunction2 Interface](icordebugfunction2-interface.md)</span></span>\
 <span data-ttu-id="2d109-222">Logicky rozšiřuje `ICorDebugFunction` poskytovat podporu pro pouze můj kód krok-through ladění.</span><span class="sxs-lookup"><span data-stu-id="2d109-222">Logically extends `ICorDebugFunction` to provide support for Just My Code step-through debugging.</span></span>  
  
 <span data-ttu-id="2d109-223">[Rozhraní ICorDebugFunction3](icordebugfunction3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-223">[ICorDebugFunction3 Interface](icordebugfunction3-interface.md)</span></span>\
 <span data-ttu-id="2d109-224">Logicky rozšiřuje rozhraní [ICorDebugFunction](icordebugfunction-interface1.md) poskytnout přístup ke kódu z požadavku ReJIT.</span><span class="sxs-lookup"><span data-stu-id="2d109-224">Logically extends the [ICorDebugFunction](icordebugfunction-interface1.md) interface to provide access to code from a ReJIT request.</span></span>  
  
 <span data-ttu-id="2d109-225">[Rozhraní ICorDebugFunctionBreakpoint](icordebugfunctionbreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-225">[ICorDebugFunctionBreakpoint Interface](icordebugfunctionbreakpoint-interface.md)</span></span>\
 <span data-ttu-id="2d109-226">Rozšiřuje `ICorDebugBreakpoint` pro podporu zarážek v rámci funkce.</span><span class="sxs-lookup"><span data-stu-id="2d109-226">Extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
 <span data-ttu-id="2d109-227">[Rozhraní ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-227">[ICorDebugGCReferenceEnum Interface](icordebuggcreferenceenum-interface.md)</span></span>\
 <span data-ttu-id="2d109-228">Poskytuje enumerátor pro objekty, které budou uvolněny z paměti.</span><span class="sxs-lookup"><span data-stu-id="2d109-228">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
 <span data-ttu-id="2d109-229">[Rozhraní ICorDebugGenericValue](icordebuggenericvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-229">[ICorDebugGenericValue Interface](icordebuggenericvalue-interface.md)</span></span>\
 <span data-ttu-id="2d109-230">`ICorDebugValue` Podtřída, která platí pro všechny hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2d109-230">A subclass of `ICorDebugValue` that applies to all values.</span></span> <span data-ttu-id="2d109-231">Toto rozhraní poskytuje metody Get a Set pro hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2d109-231">This interface provides Get and Set methods for the value.</span></span>  
  
 <span data-ttu-id="2d109-232">[Rozhraní ICorDebugGuidToTypeEnum](icordebugguidtotypeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-232">[ICorDebugGuidToTypeEnum Interface](icordebugguidtotypeenum-interface.md)</span></span>\
 <span data-ttu-id="2d109-233">Poskytuje čítač výčtu pro objekt, který `ICorDebugType` mapuje identifikátory GUID a jejich odpovídající objekty.</span><span class="sxs-lookup"><span data-stu-id="2d109-233">Provides an enumerator for an object that maps GUIDs and their corresponding `ICorDebugType` objects.</span></span>  
  
 <span data-ttu-id="2d109-234">[Rozhraní ICorDebugHandleValue](icordebughandlevalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-234">[ICorDebugHandleValue Interface](icordebughandlevalue-interface.md)</span></span>\
 <span data-ttu-id="2d109-235">`ICorDebugReferenceValue` Podtřída, která představuje referenční hodnotu, na kterou ladicí program vytvořil popisovač pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="2d109-235">A subclass of `ICorDebugReferenceValue` that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
 <span data-ttu-id="2d109-236">[Rozhraní ICorDebugHeapEnum](icordebugheapenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-236">[ICorDebugHeapEnum Interface](icordebugheapenum-interface.md)</span></span>\
 <span data-ttu-id="2d109-237">Poskytuje enumerátor pro objekty na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="2d109-237">Provides an enumerator for objects on the managed heap.</span></span>  
  
 <span data-ttu-id="2d109-238">[Rozhraní ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-238">[ICorDebugHeapSegmentEnum Interface](icordebugheapsegmentenum-interface.md)</span></span>\
 <span data-ttu-id="2d109-239">Poskytuje enumerátor pro oblasti paměti spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="2d109-239">Provides an enumerator for the memory regions of the managed heap.</span></span>  
  
 <span data-ttu-id="2d109-240">[Rozhraní ICorDebugHeapValue](icordebugheapvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-240">[ICorDebugHeapValue Interface](icordebugheapvalue-interface.md)</span></span>\
 <span data-ttu-id="2d109-241">`ICorDebugValue` Podtřída, která představuje objekt, který byl shromážděn uvolňováníclr.</span><span class="sxs-lookup"><span data-stu-id="2d109-241">A subclass of `ICorDebugValue` that represents an object that has been collected by the CLR garbage collector.</span></span>  
  
 <span data-ttu-id="2d109-242">[Rozhraní ICorDebugHeap2](icordebugheapvalue2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-242">[ICorDebugHeapValue2 Interface](icordebugheapvalue2-interface1.md)</span></span>\
 <span data-ttu-id="2d109-243">`ICorDebugHeapValue` Rozšíření, které poskytuje podporu pro runtime popisovače.</span><span class="sxs-lookup"><span data-stu-id="2d109-243">An extension of `ICorDebugHeapValue` that provides support for runtime handles.</span></span>  
  
 <span data-ttu-id="2d109-244">[Rozhraní ICorDebugHeapValue3](icordebugheapvalue3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-244">[ICorDebugHeapValue3 Interface](icordebugheapvalue3-interface.md)</span></span>\
 <span data-ttu-id="2d109-245">Zpřístupní vlastnosti uzamčení sledování objektů.</span><span class="sxs-lookup"><span data-stu-id="2d109-245">Exposes the monitor lock properties of objects.</span></span>  
  
 <span data-ttu-id="2d109-246">[Rozhraní ICorDebugILCode](icordebugilcode-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-246">[ICorDebugILCode Interface](icordebugilcode-interface.md)</span></span>\
 <span data-ttu-id="2d109-247">Představuje segment kódu zprostředkujícího jazyka (IL).</span><span class="sxs-lookup"><span data-stu-id="2d109-247">Represents a segment of intermediate language (IL) code.</span></span>  
  
 <span data-ttu-id="2d109-248">[Rozhraní ICorDebugILCode2](icordebugilcode2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-248">[ICorDebugILCode2 Interface](icordebugilcode2-interface.md)</span></span>\
 <span data-ttu-id="2d109-249">Logicky rozšiřuje rozhraní [ICorDebugILCode](icordebugilcode-interface.md) poskytnout metody, které vrátí token pro podpis místní proměnné funkce a které mapují profiler instrumentované zprostředkující jazyk (IL) posuny původní metody IL posuny.</span><span class="sxs-lookup"><span data-stu-id="2d109-249">Logically extends the [ICorDebugILCode](icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
 <span data-ttu-id="2d109-250">[Rozhraní ICorDebugILFrame](icordebugilframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-250">[ICorDebugILFrame Interface](icordebugilframe-interface.md)</span></span>\
 <span data-ttu-id="2d109-251">Představuje rámec zásobníku kódu MSIL.</span><span class="sxs-lookup"><span data-stu-id="2d109-251">Represents a stack frame of MSIL code.</span></span>  
  
 <span data-ttu-id="2d109-252">[Rozhraní ICorDebugILFrame2](icordebugilframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-252">[ICorDebugILFrame2 Interface](icordebugilframe2-interface.md)</span></span>\
 <span data-ttu-id="2d109-253">Logické rozšíření `ICorDebugILFrame`.</span><span class="sxs-lookup"><span data-stu-id="2d109-253">A logical extension of `ICorDebugILFrame`.</span></span>  
  
 <span data-ttu-id="2d109-254">[Rozhraní ICorDebugILFrame3](icordebugilframe3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-254">[ICorDebugILFrame3 Interface](icordebugilframe3-interface.md)</span></span>\
 <span data-ttu-id="2d109-255">Poskytuje metodu, která zapouzdřuje vrácenou hodnotu funkce.</span><span class="sxs-lookup"><span data-stu-id="2d109-255">Provides a method that encapsulates the return value of a function.</span></span>  
  
 <span data-ttu-id="2d109-256">[Rozhraní ICorDebugILFrame4](icordebugilframe4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-256">[ICorDebugILFrame4 Interface](icordebugilframe4-interface.md)</span></span>\
 <span data-ttu-id="2d109-257">Poskytuje metody, které umožňují přístup k místním proměnným a kódu v rámci zásobníku kódu zprostředkujícího jazyka (IL).</span><span class="sxs-lookup"><span data-stu-id="2d109-257">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="2d109-258">Parametr určuje, zda ladicí program má přístup k proměnným a kód přidán v profileru ReJIT instrumentace.</span><span class="sxs-lookup"><span data-stu-id="2d109-258">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
 <span data-ttu-id="2d109-259">[Rozhraní ICorDebugInstanceFieldSymbol](icordebuginstancefieldsymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-259">[ICorDebugInstanceFieldSymbol Interface](icordebuginstancefieldsymbol-interface.md)</span></span>\
 <span data-ttu-id="2d109-260">Představuje informace o symbolu ladění pro pole instance.</span><span class="sxs-lookup"><span data-stu-id="2d109-260">Represents the debug symbol information for an instance field.</span></span> <span data-ttu-id="2d109-261">**K dispozici pouze na nativním rozhraní .NET.**</span><span class="sxs-lookup"><span data-stu-id="2d109-261">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="2d109-262">[Rozhraní ICorDebugInternalFrame](icordebuginternalframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-262">[ICorDebugInternalFrame Interface](icordebuginternalframe-interface.md)</span></span>\
 <span data-ttu-id="2d109-263">Určuje typy rámců pro ladicí program.</span><span class="sxs-lookup"><span data-stu-id="2d109-263">Identifies frame types for the debugger.</span></span>  
  
 <span data-ttu-id="2d109-264">[Rozhraní ICorDebugInternalFrame2](icordebuginternalframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-264">[ICorDebugInternalFrame2 Interface](icordebuginternalframe2-interface.md)</span></span>\
 <span data-ttu-id="2d109-265">Obsahuje informace o vnitřních rámcích, včetně adresy zásobníku a pozice ve vztahu k objektům [ICorDebugFrame.](icordebugframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-265">Provides information about internal frames, including stack address and position in relation to [ICorDebugFrame](icordebugframe-interface.md) objects.</span></span>  
  
 <span data-ttu-id="2d109-266">[Rozhraní ICorDebugLoadedModule](icordebugloadedmodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-266">[ICorDebugLoadedModule Interface](icordebugloadedmodule-interface.md)</span></span>\
 <span data-ttu-id="2d109-267">Obsahuje informace o načteném modulu.</span><span class="sxs-lookup"><span data-stu-id="2d109-267">Provides information about a loaded module.</span></span> <span data-ttu-id="2d109-268">**K dispozici pouze na nativním rozhraní .NET.**</span><span class="sxs-lookup"><span data-stu-id="2d109-268">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="2d109-269">[Rozhraní ICorDebugManagedCallback](icordebugmanagedcallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-269">[ICorDebugManagedCallback Interface](icordebugmanagedcallback-interface.md)</span></span>\
 <span data-ttu-id="2d109-270">Poskytuje metody pro zpětná volání procesu ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="2d109-270">Provides methods to process debugger callbacks.</span></span>  
  
 <span data-ttu-id="2d109-271">[Rozhraní ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-271">[ICorDebugManagedCallback2 Interface](icordebugmanagedcallback2-interface.md)</span></span>\
 <span data-ttu-id="2d109-272">Poskytuje metody pro podporu zpracování výjimek ladicího programu a spravované pomocníky ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="2d109-272">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="2d109-273">`ICorDebugManagedCallback2`je logickým `ICorDebugManagedCallback`rozšířením .</span><span class="sxs-lookup"><span data-stu-id="2d109-273">`ICorDebugManagedCallback2` is a logical extension of `ICorDebugManagedCallback`.</span></span>  
  
 <span data-ttu-id="2d109-274">[Rozhraní ICorDebugManagedCallback3](icordebugmanagedcallback3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-274">[ICorDebugManagedCallback3 Interface](icordebugmanagedcallback3-interface.md)</span></span>\
 <span data-ttu-id="2d109-275">Poskytuje metodu zpětného volání, která určuje, že povolené vlastní oznámení ladicího programu bylo vyvoláno.</span><span class="sxs-lookup"><span data-stu-id="2d109-275">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
 <span data-ttu-id="2d109-276">[Rozhraní ICorDebugMDA](icordebugmda-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-276">[ICorDebugMDA Interface](icordebugmda-interface.md)</span></span>\
 <span data-ttu-id="2d109-277">Představuje zprávu pomocníka spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="2d109-277">Represents a managed debugging assistant (MDA) message.</span></span>  
  
 <span data-ttu-id="2d109-278">[Rozhraní ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-278">[ICorDebugMemoryBuffer Interface](icordebugmemorybuffer-interface.md)</span></span>\
 <span data-ttu-id="2d109-279">Představuje vyrovnávací paměť v paměti.</span><span class="sxs-lookup"><span data-stu-id="2d109-279">Represents an in-memory buffer.</span></span> <span data-ttu-id="2d109-280">**K dispozici pouze na nativním rozhraní .NET.**</span><span class="sxs-lookup"><span data-stu-id="2d109-280">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="2d109-281">[Rozhraní ICorDebugMergedAssemblyRecord](icordebugmergedassemblyrecord-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-281">[ICorDebugMergedAssemblyRecord Interface](icordebugmergedassemblyrecord-interface.md)</span></span>\
 <span data-ttu-id="2d109-282">Obsahuje informace o sloučeném sestavení.</span><span class="sxs-lookup"><span data-stu-id="2d109-282">Provides information about a merged assembly.</span></span> <span data-ttu-id="2d109-283">**K dispozici pouze na nativním rozhraní .NET.**</span><span class="sxs-lookup"><span data-stu-id="2d109-283">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="2d109-284">[Rozhraní ICorDebugMetaDataLocator](icordebugmetadatalocator-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-284">[ICorDebugMetaDataLocator Interface](icordebugmetadatalocator-interface.md)</span></span>\
 <span data-ttu-id="2d109-285">Poskytuje informace metadat k ladicímu programu.</span><span class="sxs-lookup"><span data-stu-id="2d109-285">Provides metadata information to the debugger.</span></span>  
  
 <span data-ttu-id="2d109-286">[Rozhraní ICorDebugModule](icordebugmodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-286">[ICorDebugModule Interface](icordebugmodule-interface.md)</span></span>\
 <span data-ttu-id="2d109-287">Představuje modul CLR, který je spustitelný soubor nebo dynamická knihovna (DLL).</span><span class="sxs-lookup"><span data-stu-id="2d109-287">Represents a CLR module, which is either an executable or a dynamic-link library (DLL).</span></span>  
  
 <span data-ttu-id="2d109-288">[Rozhraní ICorDebugModule2](icordebugmodule2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-288">[ICorDebugModule2 Interface](icordebugmodule2-interface.md)</span></span>\
 <span data-ttu-id="2d109-289">Slouží jako logické `ICorDebugModule`rozšíření .</span><span class="sxs-lookup"><span data-stu-id="2d109-289">Serves as a logical extension to `ICorDebugModule`.</span></span>  
  
 <span data-ttu-id="2d109-290">[Rozhraní ICorDebugModule3](icordebugmodule3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-290">[ICorDebugModule3 Interface](icordebugmodule3-interface.md)</span></span>\
 <span data-ttu-id="2d109-291">Vytvoří čtečku symbolů pro dynamický modul.</span><span class="sxs-lookup"><span data-stu-id="2d109-291">Creates a symbol reader for a dynamic module.</span></span>  
  
 <span data-ttu-id="2d109-292">[Rozhraní ICorDebugModuleBreakpoint](icordebugmodulebreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-292">[ICorDebugModuleBreakpoint Interface](icordebugmodulebreakpoint-interface.md)</span></span>\
 <span data-ttu-id="2d109-293">Rozšiřuje `ICorDebugBreakpoint` poskytovat přístup ke konkrétním modulům.</span><span class="sxs-lookup"><span data-stu-id="2d109-293">Extends `ICorDebugBreakpoint` to provide access to specific modules.</span></span>  
  
 <span data-ttu-id="2d109-294">[Rozhraní ICorDebugModuleDebugEvent](icordebugmoduledebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-294">[ICorDebugModuleDebugEvent Interface](icordebugmoduledebugevent-interface.md)</span></span>\
 <span data-ttu-id="2d109-295">Rozšiřuje rozhraní [ICorDebugDebugEvent](icordebugdebugevent-interface.md) pro podporu událostí na úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="2d109-295">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support module-level events.</span></span> <span data-ttu-id="2d109-296">**K dispozici pouze na nativním rozhraní .NET.**</span><span class="sxs-lookup"><span data-stu-id="2d109-296">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="2d109-297">[Rozhraní ICorDebugModuleEnum](icordebugmoduleenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-297">[ICorDebugModuleEnum Interface](icordebugmoduleenum-interface.md)</span></span>\
 <span data-ttu-id="2d109-298">Implementuje `ICorDebugEnum` metody a vyjmenovává `ICorDebugModule` pole.</span><span class="sxs-lookup"><span data-stu-id="2d109-298">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugModule` arrays.</span></span>  
  
 <span data-ttu-id="2d109-299">[Rozhraní ICorDebugMutableDataTarget](icordebugmutabledatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-299">[ICorDebugMutableDataTarget Interface](icordebugmutabledatatarget-interface.md)</span></span>\
 <span data-ttu-id="2d109-300">Rozšiřuje rozhraní [ICorDebugDataTarget](icordebugdatatarget-interface.md) pro podporu proměnlivých datových cílů.</span><span class="sxs-lookup"><span data-stu-id="2d109-300">Extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
 <span data-ttu-id="2d109-301">[Rozhraní ICorDebugNativeFrame](icordebugnativeframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-301">[ICorDebugNativeFrame Interface](icordebugnativeframe-interface.md)</span></span>\
 <span data-ttu-id="2d109-302">Specializovaná implementace `ICorDebugFrame` pro nativní rámce.</span><span class="sxs-lookup"><span data-stu-id="2d109-302">A specialized implementation of `ICorDebugFrame` used for native frames.</span></span>  
  
 <span data-ttu-id="2d109-303">[Rozhraní ICorDebugNativeFrame2](icordebugnativeframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-303">[ICorDebugNativeFrame2 Interface](icordebugnativeframe2-interface.md)</span></span>\
 <span data-ttu-id="2d109-304">Poskytuje metody, které testují podřízené a nadřazené vztahy rámce.</span><span class="sxs-lookup"><span data-stu-id="2d109-304">Provides methods that test for child and parent frame relationships.</span></span>  
  
 <span data-ttu-id="2d109-305">[Rozhraní ICorDebugObjectEnum](icordebugobjectenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-305">[ICorDebugObjectEnum Interface](icordebugobjectenum-interface.md)</span></span>\
 <span data-ttu-id="2d109-306">Implementuje `ICorDebugEnum` metody a vyjmenovává pole objektů podle jejich relativní virtuální adresy (RVAs).</span><span class="sxs-lookup"><span data-stu-id="2d109-306">Implements `ICorDebugEnum` methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
 <span data-ttu-id="2d109-307">[Rozhraní ICorDebugObjectValue](icordebugobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-307">[ICorDebugObjectValue Interface](icordebugobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="2d109-308">`ICorDebugValue` Podtřída, která představuje hodnotu, která obsahuje objekt.</span><span class="sxs-lookup"><span data-stu-id="2d109-308">A subclass of `ICorDebugValue` that represents a value that contains an object.</span></span>  
  
 <span data-ttu-id="2d109-309">[Rozhraní ICorDebugObjectValue2](icordebugobjectvalue2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-309">[ICorDebugObjectValue2 Interface](icordebugobjectvalue2-interface.md)</span></span>\
 <span data-ttu-id="2d109-310">Rozšiřuje `ICorDebugObjectValue` se na podporu dědičnosti a přepsání.</span><span class="sxs-lookup"><span data-stu-id="2d109-310">Extends `ICorDebugObjectValue` to support inheritance and overrides.</span></span>  
  
 <span data-ttu-id="2d109-311">[Rozhraní ICorDebugProcess](icordebugprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-311">[ICorDebugProcess Interface](icordebugprocess-interface.md)</span></span>\
 <span data-ttu-id="2d109-312">Představuje proces, který spouští spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="2d109-312">Represents a process that is executing managed code.</span></span>  
  
 <span data-ttu-id="2d109-313">[Rozhraní ICorDebugProcess2](icordebugprocess2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-313">[ICorDebugProcess2 Interface](icordebugprocess2-interface1.md)</span></span>\
 <span data-ttu-id="2d109-314">Logické rozšíření `ICorDebugProcess`.</span><span class="sxs-lookup"><span data-stu-id="2d109-314">A logical extension of `ICorDebugProcess`.</span></span>  
  
 <span data-ttu-id="2d109-315">[Rozhraní ICorDebugProcess3](icordebugprocess3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-315">[ICorDebugProcess3 Interface](icordebugprocess3-interface.md)</span></span>\
 <span data-ttu-id="2d109-316">Řídí vlastní oznámení ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="2d109-316">Controls custom debugger notifications.</span></span>

 <span data-ttu-id="2d109-317">[Rozhraní ICorDebugProcess4](icordebugprocess4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-317">[ICorDebugProcess4 Interface](icordebugprocess4-interface.md)</span></span>\
 <span data-ttu-id="2d109-318">Poskytuje podporu pro řízení provádění mimo proces.</span><span class="sxs-lookup"><span data-stu-id="2d109-318">Provides support for out of process execution control.</span></span>
  
 <span data-ttu-id="2d109-319">[Rozhraní ICorDebugProcess5](icordebugprocess5-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-319">[ICorDebugProcess5 Interface](icordebugprocess5-interface.md)</span></span>\
 <span data-ttu-id="2d109-320">Rozšiřuje rozhraní [ICorDebugProcess](icordebugprocess-interface.md) pro podporu přístupu ke spravované haldě, poskytuje informace o uvolňování paměti spravovaných objektů a k určení, zda ladicí program načte obrazy z místní mezipaměti nativního obrázku aplikace.</span><span class="sxs-lookup"><span data-stu-id="2d109-320">Extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application's local native image cache.</span></span>  
  
 <span data-ttu-id="2d109-321">[Rozhraní ICorDebugProcess6](icordebugprocess6-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-321">[ICorDebugProcess6 Interface](icordebugprocess6-interface.md)</span></span>\
 <span data-ttu-id="2d109-322">Logicky rozšiřuje rozhraní [ICorDebugProcess](icordebugprocess-interface.md) povolit funkce, jako je dekódování spravované ladicí události, které jsou kódovány v nativní výjimky ladění událostí a rozdělení virtuálního modulu.</span><span class="sxs-lookup"><span data-stu-id="2d109-322">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span> <span data-ttu-id="2d109-323">**K dispozici pouze na nativním rozhraní .NET.**</span><span class="sxs-lookup"><span data-stu-id="2d109-323">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="2d109-324">[Rozhraní ICorDebugProcess7](icordebugprocess7-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-324">[ICorDebugProcess7 Interface](icordebugprocess7-interface.md)</span></span>\
 <span data-ttu-id="2d109-325">Poskytuje metodu, která konfiguruje ladicí program pro zpracování aktualizací metadat v paměti v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="2d109-325">Provides a method that configures the debugger to handle in-memory metadata updates in the target process.</span></span>  
  
 <span data-ttu-id="2d109-326">[Rozhraní ICorDebugProcess8](icordebugprocess8-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-326">[ICorDebugProcess8 Interface](icordebugprocess8-interface.md)</span></span>\
 <span data-ttu-id="2d109-327">Logicky rozšiřuje rozhraní [ICorDebugProcess](icordebugprocess-interface.md) pro povolení nebo zakázání určitých typů zpětná volání výjimek [ICorDebugManagedCallback2.](icordebugmanagedcallback2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-327">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable or disable certain types of [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
 <span data-ttu-id="2d109-328">[Rozhraní ICorDebugProcessEnum](icordebugprocessenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-328">[ICorDebugProcessEnum Interface](icordebugprocessenum-interface.md)</span></span>\
 <span data-ttu-id="2d109-329">Implementuje `ICorDebugEnum` metody a vyjmenovává `ICorDebugProcess` pole.</span><span class="sxs-lookup"><span data-stu-id="2d109-329">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugProcess` arrays.</span></span>  
  
 <span data-ttu-id="2d109-330">[Rozhraní ICorDebugReferenceValue](icordebugreferencevalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-330">[ICorDebugReferenceValue Interface](icordebugreferencevalue-interface.md)</span></span>\
 <span data-ttu-id="2d109-331">`ICorDebugValue` Podtřída, která podporuje typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="2d109-331">A subclass of `ICorDebugValue` that supports reference types.</span></span>  
  
 <span data-ttu-id="2d109-332">[Rozhraní ICorDebugRegisterSet](icordebugregisterset-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-332">[ICorDebugRegisterSet Interface](icordebugregisterset-interface.md)</span></span>\
 <span data-ttu-id="2d109-333">Představuje sadu registrů, které jsou k dispozici v počítači, který aktuálně spouští kód.</span><span class="sxs-lookup"><span data-stu-id="2d109-333">Represents the set of registers available on the machine that is currently executing code.</span></span>  
  
 <span data-ttu-id="2d109-334">[Rozhraní ICorDebugRegisterSet2](icordebugregisterset2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-334">[ICorDebugRegisterSet2 Interface](icordebugregisterset2-interface.md)</span></span>\
 <span data-ttu-id="2d109-335">Rozšiřuje možnosti `ICorDebugRegisterSet` pro hardwarové platformy, které mají více než 64 registrů.</span><span class="sxs-lookup"><span data-stu-id="2d109-335">Extends the capabilities of `ICorDebugRegisterSet` for hardware platforms that have more than 64 registers.</span></span>  
  
 <span data-ttu-id="2d109-336">[Vzdálené rozhraní ICorDebug](icordebugremote-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-336">[ICorDebugRemote Interface](icordebugremote-interface.md)</span></span>\
 <span data-ttu-id="2d109-337">Umožňuje spustit nebo připojit spravovaný ladicí program ke vzdálenému cílovému procesu.</span><span class="sxs-lookup"><span data-stu-id="2d109-337">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
 <span data-ttu-id="2d109-338">[Rozhraní ICorDebugRemoteTarget](icordebugremotetarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-338">[ICorDebugRemoteTarget Interface](icordebugremotetarget-interface.md)</span></span>\
 <span data-ttu-id="2d109-339">Poskytuje metody umožňující ladit aplikace programu Silverlight v prostředí CLR.</span><span class="sxs-lookup"><span data-stu-id="2d109-339">Provides methods that enable you to debug Silverlight-based applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="2d109-340">[Rozhraní ICorDebugRuntimeUnwindableFrame](icordebugruntimeunwindableframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-340">[ICorDebugRuntimeUnwindableFrame Interface](icordebugruntimeunwindableframe-interface.md)</span></span>\
 <span data-ttu-id="2d109-341">Poskytuje podporu pro nespravované metody, které vyžadují modul CLR k uvolnění rámce.</span><span class="sxs-lookup"><span data-stu-id="2d109-341">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
 <span data-ttu-id="2d109-342">[Rozhraní ICorDebugStackWalk](icordebugstackwalk-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-342">[ICorDebugStackWalk Interface](icordebugstackwalk-interface.md)</span></span>\
 <span data-ttu-id="2d109-343">Poskytuje metody pro získání spravovaných metod nebo rámců v zásobníku vlákna.</span><span class="sxs-lookup"><span data-stu-id="2d109-343">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
 <span data-ttu-id="2d109-344">[Rozhraní ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-344">[ICorDebugStaticFieldSymbol Interface](icordebugstaticfieldsymbol-interface.md)</span></span>\
 <span data-ttu-id="2d109-345">Představuje informace o symbolu ladění pro statické pole.</span><span class="sxs-lookup"><span data-stu-id="2d109-345">Represents the debug symbol information for a static field.</span></span> <span data-ttu-id="2d109-346">**K dispozici pouze na nativním rozhraní .NET.**</span><span class="sxs-lookup"><span data-stu-id="2d109-346">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="2d109-347">[Rozhraní ICorDebugStepper](icordebugstepper-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-347">[ICorDebugStepper Interface](icordebugstepper-interface.md)</span></span>\
 <span data-ttu-id="2d109-348">Představuje krok ve spuštění kódu, který je prováděn pomocí ladicího programu, slouží jako identifikátor mezi vydáním a dokončením příkazu a umožňuje krok zrušit.</span><span class="sxs-lookup"><span data-stu-id="2d109-348">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
 <span data-ttu-id="2d109-349">[Rozhraní ICorDebugStepper2](icordebugstepper2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-349">[ICorDebugStepper2 Interface](icordebugstepper2-interface1.md)</span></span>\
 <span data-ttu-id="2d109-350">Poskytuje podporu ladění Pouze můj kód (JMC).</span><span class="sxs-lookup"><span data-stu-id="2d109-350">Provides support for Just My Code (JMC) debugging.</span></span>  
  
 <span data-ttu-id="2d109-351">[Rozhraní ICorDebugStepperEnum](icordebugstepperenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-351">[ICorDebugStepperEnum Interface](icordebugstepperenum-interface.md)</span></span>\
 <span data-ttu-id="2d109-352">Implementuje `ICorDebugEnum` metody a vyjmenovává `ICorDebugStepper` pole.</span><span class="sxs-lookup"><span data-stu-id="2d109-352">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugStepper` arrays.</span></span>  
  
 <span data-ttu-id="2d109-353">[Rozhraní ICorDebugStringValue](icordebugstringvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-353">[ICorDebugStringValue Interface](icordebugstringvalue-interface.md)</span></span>\
 <span data-ttu-id="2d109-354">`ICorDebugHeapValue` Podtřída, která platí pro řetězcové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2d109-354">A subclass of `ICorDebugHeapValue` that applies to string values.</span></span>  
  
 <span data-ttu-id="2d109-355">[Rozhraní ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-355">[ICorDebugSymbolProvider Interface](icordebugsymbolprovider-interface.md)</span></span>\
 <span data-ttu-id="2d109-356">Poskytuje metody, které lze použít k načtení informací o symbolu ladění.</span><span class="sxs-lookup"><span data-stu-id="2d109-356">Provides methods that can be used to retrieve debug symbol information.</span></span> <span data-ttu-id="2d109-357">**K dispozici pouze na nativním rozhraní .NET.**</span><span class="sxs-lookup"><span data-stu-id="2d109-357">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="2d109-358">[Rozhraní ICorDebugSymbolProvider2](icordebugsymbolprovider2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-358">[ICorDebugSymbolProvider2 Interface](icordebugsymbolprovider2-interface.md)</span></span>\
 <span data-ttu-id="2d109-359">Logicky rozšiřuje rozhraní [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) načíst další informace o symbolu ladění.</span><span class="sxs-lookup"><span data-stu-id="2d109-359">Logically extends the [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span> <span data-ttu-id="2d109-360">**K dispozici pouze na nativním rozhraní .NET.**</span><span class="sxs-lookup"><span data-stu-id="2d109-360">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="2d109-361">[Rozhraní ICorDebugThread](icordebugthread-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-361">[ICorDebugThread Interface](icordebugthread-interface.md)</span></span>\
 <span data-ttu-id="2d109-362">Představuje vlákno v procesu.</span><span class="sxs-lookup"><span data-stu-id="2d109-362">Represents a thread in a process.</span></span> <span data-ttu-id="2d109-363">Životnost `ICorDebugThread` instance je stejná jako životnost vlákna, které představuje.</span><span class="sxs-lookup"><span data-stu-id="2d109-363">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
 <span data-ttu-id="2d109-364">[Rozhraní ICorDebugThread2](icordebugthread2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-364">[ICorDebugThread2 Interface](icordebugthread2-interface.md)</span></span>\
 <span data-ttu-id="2d109-365">Slouží jako logické `ICorDebugThread`rozšíření .</span><span class="sxs-lookup"><span data-stu-id="2d109-365">Serves as a logical extension to `ICorDebugThread`.</span></span>  
  
 <span data-ttu-id="2d109-366">[Rozhraní ICorDebugThread3](icordebugthread3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-366">[ICorDebugThread3 Interface](icordebugthread3-interface.md)</span></span>\
 <span data-ttu-id="2d109-367">Poskytuje vstupní bod [iCorDebugStackWalk](icordebugstackwalk-interface.md) a odpovídající rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2d109-367">Provides the entry point to the [ICorDebugStackWalk](icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
 <span data-ttu-id="2d109-368">[Rozhraní ICorDebugThread4](icordebugthread4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-368">[ICorDebugThread4 Interface](icordebugthread4-interface.md)</span></span>\
 <span data-ttu-id="2d109-369">Poskytuje informace o blokování vlákna.</span><span class="sxs-lookup"><span data-stu-id="2d109-369">Provides thread blocking information.</span></span>  
  
 <span data-ttu-id="2d109-370">[Rozhraní ICorDebugThreadEnum](icordebugthreadenum-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-370">[ICorDebugThreadEnum Interface](icordebugthreadenum-interface1.md)</span></span>\
 <span data-ttu-id="2d109-371">Implementuje `ICorDebugEnum` metody a vyjmenovává `ICorDebugThread` pole.</span><span class="sxs-lookup"><span data-stu-id="2d109-371">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugThread` arrays.</span></span>  
  
 <span data-ttu-id="2d109-372">[Rozhraní ICorDebugType](icordebugtype-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-372">[ICorDebugType Interface](icordebugtype-interface.md)</span></span>\
 <span data-ttu-id="2d109-373">Představuje typ, který může být základní nebo komplexní (tj. definovaný uživatelem).</span><span class="sxs-lookup"><span data-stu-id="2d109-373">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="2d109-374">Pokud je typ `ICorDebugType` obecný, představuje instance obecný typ.</span><span class="sxs-lookup"><span data-stu-id="2d109-374">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
 <span data-ttu-id="2d109-375">[Rozhraní ICorDebugType2](icordebugtype2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-375">[ICorDebugType2 Interface](icordebugtype2-interface.md)</span></span>\
 <span data-ttu-id="2d109-376">Rozšiřuje rozhraní [ICorDebugType](icordebugtype-interface.md) načíst identifikátor typu základního typu nebo komplexní (uživatelem definované) typu.</span><span class="sxs-lookup"><span data-stu-id="2d109-376">Extends the [ICorDebugType](icordebugtype-interface.md) interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
 <span data-ttu-id="2d109-377">[Rozhraní ICorDebugTypeEnum](icordebugtypeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-377">[ICorDebugTypeEnum Interface](icordebugtypeenum-interface.md)</span></span>\
 <span data-ttu-id="2d109-378">Implementuje `ICorDebugEnum` metody a vyjmenovává `ICorDebugType` pole.</span><span class="sxs-lookup"><span data-stu-id="2d109-378">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugType` arrays.</span></span>  
  
 <span data-ttu-id="2d109-379">[Rozhraní ICorDebugUnmanagedCallback](icordebugunmanagedcallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-379">[ICorDebugUnmanagedCallback Interface](icordebugunmanagedcallback-interface.md)</span></span>\
 <span data-ttu-id="2d109-380">Poskytuje oznámení nativních událostí, které přímo nesouvisejí s CLR.</span><span class="sxs-lookup"><span data-stu-id="2d109-380">Provides notification of native events that are not directly related to the CLR.</span></span>  
  
 <span data-ttu-id="2d109-381">[Hodnota ICorDebugValue](icordebugvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-381">[ICorDebugValue](icordebugvalue-interface.md)</span></span>\
 <span data-ttu-id="2d109-382">Představuje hodnotu pro čtení nebo zápis v laděném procesu.</span><span class="sxs-lookup"><span data-stu-id="2d109-382">Represents a read or write value in the process being debugged.</span></span>  
  
 <span data-ttu-id="2d109-383">[Hodnota ICorDebugValue2](icordebugvalue2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-383">[ICorDebugValue2](icordebugvalue2-interface.md)</span></span>\
 <span data-ttu-id="2d109-384">Rozšiřuje `ICorDebugValue` poskytovat podporu `ICorDebugType`pro .</span><span class="sxs-lookup"><span data-stu-id="2d109-384">Extends `ICorDebugValue` to provide support for `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="2d109-385">[Rozhraní ICorDebugValue3](icordebugvalue3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-385">[ICorDebugValue3 Interface](icordebugvalue3-interface.md)</span></span>\
 <span data-ttu-id="2d109-386">Rozšiřuje rozhraní "ICorDebugValue" a "ICorDebugValue2" poskytovat podporu pro pole, která jsou větší než 2 GB.</span><span class="sxs-lookup"><span data-stu-id="2d109-386">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
 <span data-ttu-id="2d109-387">[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-387">[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)</span></span>\
 <span data-ttu-id="2d109-388">Rozšiřuje `ICorDebugBreakpoint` poskytnout přístup ke konkrétním hodnotám.</span><span class="sxs-lookup"><span data-stu-id="2d109-388">Extends `ICorDebugBreakpoint` to provide access to specific values.</span></span>  
  
 <span data-ttu-id="2d109-389">[ICorDebugValueEnum](icordebugvalueenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-389">[ICorDebugValueEnum](icordebugvalueenum-interface.md)</span></span>\
 <span data-ttu-id="2d109-390">Implementuje `ICorDebugEnum` metody a vyjmenovává `ICorDebugValue` pole.</span><span class="sxs-lookup"><span data-stu-id="2d109-390">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugValue` arrays.</span></span>  
  
 <span data-ttu-id="2d109-391">[Rozhraní ICorDebugVariableHome](icordebugvariablehome-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-391">[ICorDebugVariableHome Interface](icordebugvariablehome-interface.md)</span></span>\
 <span data-ttu-id="2d109-392">Představuje místní proměnnou nebo argument funkce.</span><span class="sxs-lookup"><span data-stu-id="2d109-392">Represents a local variable or argument of a function.</span></span>  
  
 <span data-ttu-id="2d109-393">[Rozhraní ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-393">[ICorDebugVariableHomeEnum Interface](icordebugvariablehomeenum-interface.md)</span></span>\
 <span data-ttu-id="2d109-394">Poskytuje čítač pro místní proměnné a argumenty ve funkci.</span><span class="sxs-lookup"><span data-stu-id="2d109-394">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="2d109-395">[Rozhraní ICorDebugVariableSymbol](icordebugvariablesymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-395">[ICorDebugVariableSymbol Interface](icordebugvariablesymbol-interface.md)</span></span>\
 <span data-ttu-id="2d109-396">Načte informace o symbolu ladění pro proměnnou.</span><span class="sxs-lookup"><span data-stu-id="2d109-396">Retrieves the debug symbol information for a variable.</span></span> <span data-ttu-id="2d109-397">**K dispozici pouze na nativním rozhraní .NET.**</span><span class="sxs-lookup"><span data-stu-id="2d109-397">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="2d109-398">[Rozhraní ICorDebugVirtualUnwinder](icordebugvirtualunwinder-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-398">[ICorDebugVirtualUnwinder Interface](icordebugvirtualunwinder-interface.md)</span></span>\
 <span data-ttu-id="2d109-399">Poskytuje metody, které pomáhají při odvíjení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="2d109-399">Provides methods to help in stack unwinding.</span></span> <span data-ttu-id="2d109-400">**K dispozici pouze na nativním rozhraní .NET.**</span><span class="sxs-lookup"><span data-stu-id="2d109-400">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="2d109-401">[Rozhraní ICorPublish](icorpublish-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-401">[ICorPublish Interface](icorpublish-interface.md)</span></span>\
 <span data-ttu-id="2d109-402">Slouží jako obecné rozhraní pro procesy publikování.</span><span class="sxs-lookup"><span data-stu-id="2d109-402">Serves as the general interface for the publishing processes.</span></span>  
  
 <span data-ttu-id="2d109-403">[Rozhraní iCorpublishAppDomain](icorpublishappdomain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-403">[ICorPublishAppDomain Interface](icorpublishappdomain-interface.md)</span></span>\
 <span data-ttu-id="2d109-404">Představuje a poskytuje informace o aplikační doméně.</span><span class="sxs-lookup"><span data-stu-id="2d109-404">Represents and provides information about an application domain.</span></span>  
  
 <span data-ttu-id="2d109-405">[Rozhraní ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-405">[ICorPublishAppDomainEnum Interface](icorpublishappdomainenum-interface.md)</span></span>\
 <span data-ttu-id="2d109-406">Poskytuje metody, které procházejí `ICorPublishAppDomain` kolekcí objektů, které aktuálně existují v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="2d109-406">Provides methods that traverse a collection of `ICorPublishAppDomain` objects that currently exist within a process.</span></span>  
  
 <span data-ttu-id="2d109-407">[Rozhraní ICorPublishEnum](icorpublishenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-407">[ICorPublishEnum Interface](icorpublishenum-interface.md)</span></span>\
 <span data-ttu-id="2d109-408">Slouží jako abstraktní základ pro enumerátory publikování.</span><span class="sxs-lookup"><span data-stu-id="2d109-408">Serves as the abstract base for publishing enumerators.</span></span>  
  
 <span data-ttu-id="2d109-409">[Rozhraní ICorPublishProcess](icorpublishprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-409">[ICorPublishProcess Interface](icorpublishprocess-interface.md)</span></span>\
 <span data-ttu-id="2d109-410">Poskytuje metody, které přistupují k informacím o procesu.</span><span class="sxs-lookup"><span data-stu-id="2d109-410">Provides methods that access information about a process.</span></span>  
  
 <span data-ttu-id="2d109-411">[Rozhraní ICorPublishProcessEnum](icorpublishprocessenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-411">[ICorPublishProcessEnum Interface](icorpublishprocessenum-interface.md)</span></span>\
 <span data-ttu-id="2d109-412">Poskytuje metody, které procházejí `ICorPublishProcess` kolekcí objektů.</span><span class="sxs-lookup"><span data-stu-id="2d109-412">Provides methods that traverse a collection of `ICorPublishProcess` objects.</span></span>  

 <span data-ttu-id="2d109-413">[Rozhraní ISOSDacInterface](isosdacinterface-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-413">[ISOSDacInterface Interface](isosdacinterface-interface.md)</span></span>\
 <span data-ttu-id="2d109-414">Poskytuje pomocné metody pro `SOS`přístup k datům z aplikace .</span><span class="sxs-lookup"><span data-stu-id="2d109-414">Provides helper methods to access data from `SOS`.</span></span>

 <span data-ttu-id="2d109-415">[Rozhraní IXCLRDataMethodDefinitionDefinition](ixclrdatamethoddefinition-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-415">[IXCLRDataMethodDefinition Interface](ixclrdatamethoddefinition-interface.md)</span></span>\
 <span data-ttu-id="2d109-416">Poskytuje metody pro dotazování na informace o definici metody.</span><span class="sxs-lookup"><span data-stu-id="2d109-416">Provides methods for querying information about a method definition.</span></span>

 <span data-ttu-id="2d109-417">[Rozhraní IXCLRDataMethodInstance](ixclrdatamethodinstance-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-417">[IXCLRDataMethodInstance Interface](ixclrdatamethodinstance-interface.md)</span></span>\
 <span data-ttu-id="2d109-418">Poskytuje metody pro dotazování na informace o instanci metody.</span><span class="sxs-lookup"><span data-stu-id="2d109-418">Provides methods for querying information about a method instance.</span></span>

 <span data-ttu-id="2d109-419">[Rozhraní IXCLRDataModule](ixclrdatamodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-419">[IXCLRDataModule Interface](ixclrdatamodule-interface.md)</span></span>\
 <span data-ttu-id="2d109-420">Poskytuje metody pro dotazování informací o načteném modulu.</span><span class="sxs-lookup"><span data-stu-id="2d109-420">Provides methods for querying information about a loaded module.</span></span>

 <span data-ttu-id="2d109-421">[Rozhraní IXCLRDataProcess](ixclrdataprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-421">[IXCLRDataProcess Interface](ixclrdataprocess-interface.md)</span></span>\
 <span data-ttu-id="2d109-422">Poskytuje metody pro dotazování na informace o procesu.</span><span class="sxs-lookup"><span data-stu-id="2d109-422">Provides methods for querying information about a process.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="2d109-423">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="2d109-423">Related Sections</span></span>  
 <span data-ttu-id="2d109-424">[Ladění kotříd](debugging-coclasses.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-424">[Debugging Coclasses](debugging-coclasses.md)</span></span>\
 <span data-ttu-id="2d109-425">[Ladění globálních statických funkcí](debugging-global-static-functions.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-425">[Debugging Global Static Functions](debugging-global-static-functions.md)</span></span>\
 <span data-ttu-id="2d109-426">[Ladění výčtů](debugging-enumerations.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-426">[Debugging Enumerations](debugging-enumerations.md)</span></span>\
 <span data-ttu-id="2d109-427">[Ladicí struktury](debugging-structures.md)</span><span class="sxs-lookup"><span data-stu-id="2d109-427">[Debugging Structures](debugging-structures.md)</span></span>\
