---
title: Balení .NET Framework sestavení pro model COM
description: Zabalit sestavení .NET pro COM Shromážděte seznam typů, které mohou aplikace modelu COM spotřebovat, pokyny pro správu verzí a nasazení a knihovnu typů.
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, packaging assemblies
- packaging assemblies for COM
- Tlbexp.exe
- TypeLibConverter class
- .NET Services Installation tool
- Assembly Registration tool
- Type Library Exporter
- Reqsvcs.exe
- interoperation with unmanaged code, exposing .NET Framework components
- interoperation with unmanaged code, packaging assemblies
- COM interop, exposing COM components
- Reqasm.exe
ms.assetid: 39dc55aa-f2a1-4093-87bb-f1c0edb6e761
ms.openlocfilehash: 4963892419fd1caec4483123f820d62967a87dd6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620830"
---
# <a name="packaging-a-net-framework-assembly-for-com"></a><span data-ttu-id="5d106-104">Balení .NET Framework sestavení pro model COM</span><span class="sxs-lookup"><span data-stu-id="5d106-104">Packaging a .NET Framework Assembly for COM</span></span>

<span data-ttu-id="5d106-105">Vývojáři modelu COM můžou těžit z následujících informací o spravovaných typech, které plánuje začlenit do své aplikace:</span><span class="sxs-lookup"><span data-stu-id="5d106-105">COM developers can benefit from the following information about the managed types they plan to incorporate in their application:</span></span>

- <span data-ttu-id="5d106-106">Seznam typů, které mohou využívat aplikace modelu COM</span><span class="sxs-lookup"><span data-stu-id="5d106-106">A list of types that COM applications can consume</span></span>

  <span data-ttu-id="5d106-107">Některé spravované typy jsou pro COM neviditelné; Některé jsou viditelné, ale nelze je vytvořit. a některé jsou viditelné i vytvořitelné.</span><span class="sxs-lookup"><span data-stu-id="5d106-107">Some managed types are invisible to COM; some are visible but not creatable; and some are both visible and creatable.</span></span> <span data-ttu-id="5d106-108">Sestavení může obsahovat libovolnou kombinaci neviditelných, viditelných, nevytvořitelné a vytvořitelné typy.</span><span class="sxs-lookup"><span data-stu-id="5d106-108">An assembly can comprise any combination of invisible, visible, not creatable, and creatable types.</span></span> <span data-ttu-id="5d106-109">Pro úplnost Identifikujte typy v sestavení, které chcete zpřístupnit modelu COM, zejména v případě, že jsou tyto typy podmnožinou typů vystavených .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5d106-109">For completeness, identify the types in an assembly that you intend to expose to COM, especially when those types are a subset of the types exposed to the .NET Framework.</span></span>

  <span data-ttu-id="5d106-110">Další informace naleznete v tématu [kvalifikační typy rozhraní .NET pro spoluprovozování](../../standard/native-interop/qualify-net-types-for-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="5d106-110">For additional information, see [Qualifying .NET Types for Interoperation](../../standard/native-interop/qualify-net-types-for-interoperation.md).</span></span>

- <span data-ttu-id="5d106-111">Pokyny pro správu verzí</span><span class="sxs-lookup"><span data-stu-id="5d106-111">Versioning instructions</span></span>

  <span data-ttu-id="5d106-112">Spravované třídy, které implementují rozhraní třídy (rozhraní generované zprostředkovatelem komunikace s objekty COM), podléhají omezením správy verzí.</span><span class="sxs-lookup"><span data-stu-id="5d106-112">Managed classes that implement the class interface (a COM interop-generated interface) are subject to versioning restrictions.</span></span>

  <span data-ttu-id="5d106-113">Pokyny k používání rozhraní třídy naleznete v tématu [Představujeme rozhraní třídy](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).</span><span class="sxs-lookup"><span data-stu-id="5d106-113">For guidelines on using the class interface, see [Introducing the class interface](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).</span></span>

- <span data-ttu-id="5d106-114">Pokyny k nasazení</span><span class="sxs-lookup"><span data-stu-id="5d106-114">Deployment instructions</span></span>

  <span data-ttu-id="5d106-115">Sestavení se silným názvem, která jsou podepsaná vydavatelem, mohou být nainstalována do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="5d106-115">Strong-named assemblies that are signed by a publisher can be installed into the global assembly cache.</span></span> <span data-ttu-id="5d106-116">Nepodepsaná sestavení musí být nainstalována v počítači uživatele jako soukromá sestavení.</span><span class="sxs-lookup"><span data-stu-id="5d106-116">Unsigned assemblies must be installed on the user's machine as private assemblies.</span></span>

  <span data-ttu-id="5d106-117">Další informace najdete v tématu [požadavky na zabezpečení sestavení](../../standard/assembly/security-considerations.md).</span><span class="sxs-lookup"><span data-stu-id="5d106-117">For additional information, see [Assembly Security Considerations](../../standard/assembly/security-considerations.md).</span></span>

- <span data-ttu-id="5d106-118">Zahrnutí knihovny typů</span><span class="sxs-lookup"><span data-stu-id="5d106-118">Type library inclusion</span></span>

  <span data-ttu-id="5d106-119">Většina typů vyžaduje knihovnu typů, pokud je využívána aplikací modelu COM.</span><span class="sxs-lookup"><span data-stu-id="5d106-119">Most types require a type library when consumed by a COM application.</span></span> <span data-ttu-id="5d106-120">Můžete vygenerovat knihovnu typů nebo použít tuto úlohu vývojáři modelu COM.</span><span class="sxs-lookup"><span data-stu-id="5d106-120">You can generate a type library or have COM developers perform this task.</span></span> <span data-ttu-id="5d106-121">Windows SDK poskytuje následující možnosti pro vygenerování knihovny typů:</span><span class="sxs-lookup"><span data-stu-id="5d106-121">The Windows SDK provides the following options for generating a type library:</span></span>

  - [<span data-ttu-id="5d106-122">knihovna typů – exportér</span><span class="sxs-lookup"><span data-stu-id="5d106-122">Type Library Exporter</span></span>](#cpconpackagingassemblyforcomanchor1)

  - [<span data-ttu-id="5d106-123">TypeLibConverter – třída</span><span class="sxs-lookup"><span data-stu-id="5d106-123">TypeLibConverter Class</span></span>](#cpconpackagingassemblyforcomanchor2)

  - [<span data-ttu-id="5d106-124">Nástroj pro registraci sestavení</span><span class="sxs-lookup"><span data-stu-id="5d106-124">Assembly Registration Tool</span></span>](#cpconpackagingassemblyforcomanchor3)

  - [<span data-ttu-id="5d106-125">Nástroj pro instalaci služeb .NET</span><span class="sxs-lookup"><span data-stu-id="5d106-125">.NET Services Installation Tool</span></span>](#cpconpackagingassemblyforcomanchor4)

  <span data-ttu-id="5d106-126">Bez ohledu na to, jaký mechanismus zvolíte, jsou do generované knihovny typů zahrnuty pouze veřejné typy definované v sestavení, které zadáte.</span><span class="sxs-lookup"><span data-stu-id="5d106-126">Regardless of the mechanism you choose, only public types defined in the assembly you supply are included in the generated type library.</span></span>

<span data-ttu-id="5d106-127">Pokyny najdete v tématu [Postup: vložení knihoven typů jako prostředků Win32 do. Aplikace založené na síti](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="5d106-127">For instructions, see [How to: Embed Type Libraries as Win32 Resources in .NET-Based Applications](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100)).</span></span>

<a name="cpconpackagingassemblyforcomanchor1"></a>

## <a name="type-library-exporter"></a><span data-ttu-id="5d106-128">knihovna typů – exportér</span><span class="sxs-lookup"><span data-stu-id="5d106-128">Type Library Exporter</span></span>

<span data-ttu-id="5d106-129">[Exportér knihovny typů (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) je nástroj příkazového řádku, který převádí třídy a rozhraní obsažená v sestavení na knihovnu typů modelu COM.</span><span class="sxs-lookup"><span data-stu-id="5d106-129">The [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) is a command-line tool that converts the classes and interfaces contained in an assembly to a COM type library.</span></span> <span data-ttu-id="5d106-130">Jakmile jsou informace o typu třídy k dispozici, mohou klienti modelu COM vytvořit instanci třídy .NET a volat metody instance stejně, jako by šlo o objekt modelu COM.</span><span class="sxs-lookup"><span data-stu-id="5d106-130">Once the type information of the class is available, COM clients can create an instance of the .NET class and call the methods of the instance, just as if it were a COM object.</span></span> <span data-ttu-id="5d106-131">Tlbexp.exe převádí celé sestavení najednou.</span><span class="sxs-lookup"><span data-stu-id="5d106-131">Tlbexp.exe converts an entire assembly at one time.</span></span> <span data-ttu-id="5d106-132">Pomocí nástroje Tlbexp.exe nelze generovat informace o typu pro podtypy definované v sestavení.</span><span class="sxs-lookup"><span data-stu-id="5d106-132">You cannot use Tlbexp.exe to generate type information for a subset of the types defined in an assembly.</span></span>

<a name="cpconpackagingassemblyforcomanchor2"></a>

## <a name="typelibconverter-class"></a><span data-ttu-id="5d106-133">TypeLibConverter – třída</span><span class="sxs-lookup"><span data-stu-id="5d106-133">TypeLibConverter Class</span></span>

<span data-ttu-id="5d106-134"><xref:System.Runtime.InteropServices.TypeLibConverter>Třída, která je umístěna v oboru názvů **System. Runtime. Interop** , převede třídy a rozhraní obsažené v sestavení na knihovnu typů modelu COM.</span><span class="sxs-lookup"><span data-stu-id="5d106-134">The <xref:System.Runtime.InteropServices.TypeLibConverter> class, located in the **System.Runtime.Interop** namespace, converts the classes and interfaces contained in an assembly to a COM type library.</span></span> <span data-ttu-id="5d106-135">Toto rozhraní API vytváří stejné informace o typu jako Exportér knihovny typů, jak je popsáno v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="5d106-135">This API produces the same type information as the Type Library Exporter, described in the previous section.</span></span>

<span data-ttu-id="5d106-136">**Třída TypeLibConverter** implementuje rozhraní <xref:System.Runtime.InteropServices.ITypeLibConverter> .</span><span class="sxs-lookup"><span data-stu-id="5d106-136">The **TypeLibConverter class** implements the <xref:System.Runtime.InteropServices.ITypeLibConverter>.</span></span>

<a name="cpconpackagingassemblyforcomanchor3"></a>

## <a name="assembly-registration-tool"></a><span data-ttu-id="5d106-137">Nástroj pro registraci sestavení</span><span class="sxs-lookup"><span data-stu-id="5d106-137">Assembly Registration Tool</span></span>

<span data-ttu-id="5d106-138">[Nástroj pro registraci sestavení (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) může generovat a registrovat knihovnu typů při použití možnosti **/TLB:** .</span><span class="sxs-lookup"><span data-stu-id="5d106-138">The [Assembly Registration Tool (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) can generate and register a type library when you apply the **/tlb:** option.</span></span> <span data-ttu-id="5d106-139">Klienti modelu COM vyžadují, aby byly knihovny typů nainstalovány v registru systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5d106-139">COM clients require that type libraries be installed in the Windows registry.</span></span> <span data-ttu-id="5d106-140">Bez této možnosti Regasm.exe pouze registrují typy v sestavení, nikoli v knihovně typů.</span><span class="sxs-lookup"><span data-stu-id="5d106-140">Without this option, Regasm.exe only registers the types in an assembly, not the type library.</span></span> <span data-ttu-id="5d106-141">Registrace typů v sestavení a registrace knihovny typů jsou odlišné aktivity.</span><span class="sxs-lookup"><span data-stu-id="5d106-141">Registering the types in an assembly and registering the type library are distinct activities.</span></span>

<a name="cpconpackagingassemblyforcomanchor4"></a>

## <a name="net-services-installation-tool"></a><span data-ttu-id="5d106-142">Nástroj pro instalaci služeb .NET</span><span class="sxs-lookup"><span data-stu-id="5d106-142">.NET Services Installation Tool</span></span>

<span data-ttu-id="5d106-143">[Nástroj pro instalaci služeb .NET Services (Regsvcs.exe)](../tools/regsvcs-exe-net-services-installation-tool.md) přidává spravované třídy do služby komponent Windows 2000 a kombinuje několik úloh v rámci jednoho nástroje.</span><span class="sxs-lookup"><span data-stu-id="5d106-143">The [.NET Services Installation Tool (Regsvcs.exe)](../tools/regsvcs-exe-net-services-installation-tool.md) adds managed classes to Windows 2000 Component Services and combines several tasks within a single tool.</span></span> <span data-ttu-id="5d106-144">Kromě načítání a registrace sestavení může Regsvcs.exe generovat, registrovat a instalovat knihovnu typů do existující aplikace COM+ 1,0.</span><span class="sxs-lookup"><span data-stu-id="5d106-144">In addition to loading and registering an assembly, Regsvcs.exe can generate, register, and install the type library into an existing COM+ 1.0 application.</span></span>

## <a name="see-also"></a><span data-ttu-id="5d106-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5d106-145">See also</span></span>

- <xref:System.Runtime.InteropServices.TypeLibConverter>
- <xref:System.Runtime.InteropServices.ITypeLibConverter>
- [<span data-ttu-id="5d106-146">Vystavení komponent architektury .NET Framework pro COM</span><span class="sxs-lookup"><span data-stu-id="5d106-146">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="5d106-147">Kvalifikace typů .NET pro spolupráci</span><span class="sxs-lookup"><span data-stu-id="5d106-147">Qualifying .NET Types for Interoperation</span></span>](../../standard/native-interop/qualify-net-types-for-interoperation.md)
- [<span data-ttu-id="5d106-148">Představení rozhraní třídy</span><span class="sxs-lookup"><span data-stu-id="5d106-148">Introducing the class interface</span></span>](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface)
- [<span data-ttu-id="5d106-149">Požadavky na zabezpečení sestavení</span><span class="sxs-lookup"><span data-stu-id="5d106-149">Assembly Security Considerations</span></span>](../../standard/assembly/security-considerations.md)
- [<span data-ttu-id="5d106-150">Tlbexp.exe (typ Exportér knihovny)</span><span class="sxs-lookup"><span data-stu-id="5d106-150">Tlbexp.exe (Type Library Exporter)</span></span>](../tools/tlbexp-exe-type-library-exporter.md)
- [<span data-ttu-id="5d106-151">Registrování sestav pomocí modelu COM</span><span class="sxs-lookup"><span data-stu-id="5d106-151">Registering Assemblies with COM</span></span>](registering-assemblies-with-com.md)
- <span data-ttu-id="5d106-152">[Postupy: vkládání knihoven typů jako prostředků Win32 v aplikacích](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5d106-152">[How to: Embed Type Libraries as Win32 Resources in Applications](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100))</span></span>
