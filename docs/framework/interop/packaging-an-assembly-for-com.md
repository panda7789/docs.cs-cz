---
title: Zabalení sestavení pro model COM
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fdbbc169999a9faa2ac1c33c8573e51b76899b74
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032433"
---
# <a name="packaging-an-assembly-for-com"></a><span data-ttu-id="d9ecb-102">Zabalení sestavení pro model COM</span><span class="sxs-lookup"><span data-stu-id="d9ecb-102">Packaging an Assembly for COM</span></span>

<span data-ttu-id="d9ecb-103">Následující informace o spravované typy, že chtějí začlenit ve svých aplikacích využívat vývojáři COM:</span><span class="sxs-lookup"><span data-stu-id="d9ecb-103">COM developers can benefit from the following information about the managed types they plan to incorporate in their application:</span></span>

- <span data-ttu-id="d9ecb-104">Seznam typů, které využívají aplikace modelu COM</span><span class="sxs-lookup"><span data-stu-id="d9ecb-104">A list of types that COM applications can consume</span></span>

  <span data-ttu-id="d9ecb-105">Některé spravované typy nejsou viditelná modelu COM; Některé jsou zobrazena, ale není vytvořitelný; a některé jsou viditelné a vytvořitelné.</span><span class="sxs-lookup"><span data-stu-id="d9ecb-105">Some managed types are invisible to COM; some are visible but not creatable; and some are both visible and creatable.</span></span> <span data-ttu-id="d9ecb-106">Sestavení může obsahovat libovolnou kombinaci typů neviditelné, není možné vytvořit, přehledné a vytvořitelné.</span><span class="sxs-lookup"><span data-stu-id="d9ecb-106">An assembly can comprise any combination of invisible, visible, not creatable, and creatable types.</span></span> <span data-ttu-id="d9ecb-107">Pro úplnost jaké typy v sestavení, které chcete vystavit rozhraní COM, zejména v případě, že tyto typy jsou podmnožinou typy, které jsou vystaveny rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d9ecb-107">For completeness, identify the types in an assembly that you intend to expose to COM, especially when those types are a subset of the types exposed to the .NET Framework.</span></span>

  <span data-ttu-id="d9ecb-108">Další informace najdete v tématu [kvalifikace typů .NET pro spolupráci](qualifying-net-types-for-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="d9ecb-108">For additional information, see [Qualifying .NET Types for Interoperation](qualifying-net-types-for-interoperation.md).</span></span>

- <span data-ttu-id="d9ecb-109">Správa verzí pokyny</span><span class="sxs-lookup"><span data-stu-id="d9ecb-109">Versioning instructions</span></span>

  <span data-ttu-id="d9ecb-110">Spravované třídy, které implementují rozhraní třídy (rozhraní modelu COM interop generované) se vztahují omezení správy verzí.</span><span class="sxs-lookup"><span data-stu-id="d9ecb-110">Managed classes that implement the class interface (a COM interop-generated interface) are subject to versioning restrictions.</span></span>

  <span data-ttu-id="d9ecb-111">Pokyny k používání rozhraní, naleznete v tématu [představení rozhraní třídy](com-callable-wrapper.md#introducing-the-class-interface).</span><span class="sxs-lookup"><span data-stu-id="d9ecb-111">For guidelines on using the class interface, see [Introducing the class interface](com-callable-wrapper.md#introducing-the-class-interface).</span></span>

- <span data-ttu-id="d9ecb-112">Pokyny k nasazení</span><span class="sxs-lookup"><span data-stu-id="d9ecb-112">Deployment instructions</span></span>

  <span data-ttu-id="d9ecb-113">Sestavení se silným názvem, které jsou podepsané vydavatelem je možné nainstalovat do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="d9ecb-113">Strong-named assemblies that are signed by a publisher can be installed into the global assembly cache.</span></span> <span data-ttu-id="d9ecb-114">Nepodepsaná sestavení musí být nainstalována na počítač uživatele jako soukromá sestavení.</span><span class="sxs-lookup"><span data-stu-id="d9ecb-114">Unsigned assemblies must be installed on the user's machine as private assemblies.</span></span>

  <span data-ttu-id="d9ecb-115">Další informace najdete v tématu [důležité informace o zabezpečení sestavení](../app-domains/assembly-security-considerations.md).</span><span class="sxs-lookup"><span data-stu-id="d9ecb-115">For additional information, see [Assembly Security Considerations](../app-domains/assembly-security-considerations.md).</span></span>

- <span data-ttu-id="d9ecb-116">Zahrnutí knihovny typů</span><span class="sxs-lookup"><span data-stu-id="d9ecb-116">Type library inclusion</span></span>

  <span data-ttu-id="d9ecb-117">Většina typů vyžadují knihovny typů při používané aplikace modelu COM.</span><span class="sxs-lookup"><span data-stu-id="d9ecb-117">Most types require a type library when consumed by a COM application.</span></span> <span data-ttu-id="d9ecb-118">Můžete generovat knihovnu typů nebo mají vývojáři COM provedení této úlohy.</span><span class="sxs-lookup"><span data-stu-id="d9ecb-118">You can generate a type library or have COM developers perform this task.</span></span> <span data-ttu-id="d9ecb-119">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Poskytuje následující možnosti pro vytváření knihovny typů:</span><span class="sxs-lookup"><span data-stu-id="d9ecb-119">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] provides the following options for generating a type library:</span></span>

  - [<span data-ttu-id="d9ecb-120">Exportér knihovny typů</span><span class="sxs-lookup"><span data-stu-id="d9ecb-120">Type Library Exporter</span></span>](#cpconpackagingassemblyforcomanchor1)

  - [<span data-ttu-id="d9ecb-121">Typelibconverter – třída</span><span class="sxs-lookup"><span data-stu-id="d9ecb-121">TypeLibConverter Class</span></span>](#cpconpackagingassemblyforcomanchor2)

  - [<span data-ttu-id="d9ecb-122">Nástroj registrace sestavení</span><span class="sxs-lookup"><span data-stu-id="d9ecb-122">Assembly Registration Tool</span></span>](#cpconpackagingassemblyforcomanchor3)

  - [<span data-ttu-id="d9ecb-123">Nástroj pro instalaci služeb .NET</span><span class="sxs-lookup"><span data-stu-id="d9ecb-123">.NET Services Installation Tool</span></span>](#cpconpackagingassemblyforcomanchor4)

  <span data-ttu-id="d9ecb-124">Bez ohledu na to mechanismus, který zvolíte jsou pouze veřejné typy definované v sestavení, ve kterém zadáte součástí vygenerovanou knihovnu typů.</span><span class="sxs-lookup"><span data-stu-id="d9ecb-124">Regardless of the mechanism you choose, only public types defined in the assembly you supply are included in the generated type library.</span></span>

  <span data-ttu-id="d9ecb-125">Můžete zabalit jako samostatný soubor knihovny typů nebo ji vložit jako soubor prostředků Win32 v rámci. Aplikace založené na síť.</span><span class="sxs-lookup"><span data-stu-id="d9ecb-125">You can package a type library as a separate file or embed it as Win32 resource file within a .NET-based application.</span></span> <span data-ttu-id="d9ecb-126">Microsoft Visual Basic 6.0 provést tuto úlohu pro vás automaticky. ale při použití [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)], je nutné ručně vložit vaše knihovna typů.</span><span class="sxs-lookup"><span data-stu-id="d9ecb-126">Microsoft Visual Basic 6.0 performed this task for you automatically; however, when using [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)], you must embed your type library manually.</span></span> <span data-ttu-id="d9ecb-127">Pokyny najdete v tématu [jak: Vložte jako prostředky systému Win32 v knihovny typů. Aplikace založené na NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="d9ecb-127">For instructions, see [How to: Embed Type Libraries as Win32 Resources in .NET-Based Applications](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100)).</span></span>

<a name="cpconpackagingassemblyforcomanchor1"></a>

## <a name="type-library-exporter"></a><span data-ttu-id="d9ecb-128">knihovna typů – exportér</span><span class="sxs-lookup"><span data-stu-id="d9ecb-128">Type Library Exporter</span></span>

<span data-ttu-id="d9ecb-129">[Exportér knihovny typů (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) je nástroj příkazového řádku, který převede třídy a rozhraní, které jsou obsaženy v sestavení na knihovnu typů modelu COM.</span><span class="sxs-lookup"><span data-stu-id="d9ecb-129">The [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) is a command-line tool that converts the classes and interfaces contained in an assembly to a COM type library.</span></span> <span data-ttu-id="d9ecb-130">Jakmile je k dispozici informace o typu třídy, klientům modelu COM můžete vytvořit instance třídy .NET a volání metod instance, stejně jako by šlo objekt modelu COM.</span><span class="sxs-lookup"><span data-stu-id="d9ecb-130">Once the type information of the class is available, COM clients can create an instance of the .NET class and call the methods of the instance, just as if it were a COM object.</span></span> <span data-ttu-id="d9ecb-131">Tlbexp.exe převede celé sestavení najednou.</span><span class="sxs-lookup"><span data-stu-id="d9ecb-131">Tlbexp.exe converts an entire assembly at one time.</span></span> <span data-ttu-id="d9ecb-132">Pomocí nástroje Tlbexp.exe nelze generovat informace o typu pro podtypy definované v sestavení.</span><span class="sxs-lookup"><span data-stu-id="d9ecb-132">You cannot use Tlbexp.exe to generate type information for a subset of the types defined in an assembly.</span></span>

<a name="cpconpackagingassemblyforcomanchor2"></a>

## <a name="typelibconverter-class"></a><span data-ttu-id="d9ecb-133">Typelibconverter – třída</span><span class="sxs-lookup"><span data-stu-id="d9ecb-133">TypeLibConverter Class</span></span>

<span data-ttu-id="d9ecb-134"><xref:System.Runtime.InteropServices.TypeLibConverter> Třídy, které jsou umístěné v **System.Runtime.Interop** převede obor názvů, třídy a rozhraní, které jsou obsaženy v sestavení na knihovnu typů modelu COM.</span><span class="sxs-lookup"><span data-stu-id="d9ecb-134">The <xref:System.Runtime.InteropServices.TypeLibConverter> class, located in the **System.Runtime.Interop** namespace, converts the classes and interfaces contained in an assembly to a COM type library.</span></span> <span data-ttu-id="d9ecb-135">Toto rozhraní API poskytuje stejné informace o typu jako Exportér knihovny typů, je popsáno v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="d9ecb-135">This API produces the same type information as the Type Library Exporter, described in the previous section.</span></span>

<span data-ttu-id="d9ecb-136">**Typelibconverter – třída** implementuje <xref:System.Runtime.InteropServices.ITypeLibConverter>.</span><span class="sxs-lookup"><span data-stu-id="d9ecb-136">The **TypeLibConverter class** implements the <xref:System.Runtime.InteropServices.ITypeLibConverter>.</span></span>

<a name="cpconpackagingassemblyforcomanchor3"></a>

## <a name="assembly-registration-tool"></a><span data-ttu-id="d9ecb-137">Nástroj registrace sestavení</span><span class="sxs-lookup"><span data-stu-id="d9ecb-137">Assembly Registration Tool</span></span>

<span data-ttu-id="d9ecb-138">[Nástroj registrace sestavení (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) můžete vygenerovat a zaregistrovat knihovnu typů, při použití **/tlb:** možnost.</span><span class="sxs-lookup"><span data-stu-id="d9ecb-138">The [Assembly Registration Tool (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) can generate and register a type library when you apply the **/tlb:** option.</span></span> <span data-ttu-id="d9ecb-139">Klienti modelu COM vyžadují instalaci knihoven typů v registru Windows.</span><span class="sxs-lookup"><span data-stu-id="d9ecb-139">COM clients require that type libraries be installed in the Windows registry.</span></span> <span data-ttu-id="d9ecb-140">Bez této možnosti Regasm.exe pouze registruje typy v sestavení, nikoli knihovnu typů.</span><span class="sxs-lookup"><span data-stu-id="d9ecb-140">Without this option, Regasm.exe only registers the types in an assembly, not the type library.</span></span> <span data-ttu-id="d9ecb-141">Registrace typů v sestavení a registraci knihovny typů jsou různé aktivity.</span><span class="sxs-lookup"><span data-stu-id="d9ecb-141">Registering the types in an assembly and registering the type library are distinct activities.</span></span>

<a name="cpconpackagingassemblyforcomanchor4"></a>

## <a name="net-services-installation-tool"></a><span data-ttu-id="d9ecb-142">.NET Services Installation Tool</span><span class="sxs-lookup"><span data-stu-id="d9ecb-142">.NET Services Installation Tool</span></span>

<span data-ttu-id="d9ecb-143">[Nástroj pro instalaci služeb .NET (Regsvcs.exe)](../tools/regsvcs-exe-net-services-installation-tool.md) přidá spravované třídy Služba komponent Windows 2000 a kombinuje několik úkolů v rámci jediného nástroje.</span><span class="sxs-lookup"><span data-stu-id="d9ecb-143">The [.NET Services Installation Tool (Regsvcs.exe)](../tools/regsvcs-exe-net-services-installation-tool.md) adds managed classes to Windows 2000 Component Services and combines several tasks within a single tool.</span></span> <span data-ttu-id="d9ecb-144">Kromě načítá a registruje sestavení, Regsvcs.exe generovat, registrace a instalace do existující aplikace modelu COM + 1.0 knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="d9ecb-144">In addition to loading and registering an assembly, Regsvcs.exe can generate, register, and install the type library into an existing COM+ 1.0 application.</span></span>

## <a name="see-also"></a><span data-ttu-id="d9ecb-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d9ecb-145">See also</span></span>

- <xref:System.Runtime.InteropServices.TypeLibConverter>
- <xref:System.Runtime.InteropServices.ITypeLibConverter>
- [<span data-ttu-id="d9ecb-146">Vystavení komponent architektury .NET Framework pro COM</span><span class="sxs-lookup"><span data-stu-id="d9ecb-146">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="d9ecb-147">Kvalifikace typů .NET pro spolupráci</span><span class="sxs-lookup"><span data-stu-id="d9ecb-147">Qualifying .NET Types for Interoperation</span></span>](qualifying-net-types-for-interoperation.md)
- [<span data-ttu-id="d9ecb-148">Představení rozhraní třídy</span><span class="sxs-lookup"><span data-stu-id="d9ecb-148">Introducing the class interface</span></span>](com-callable-wrapper.md#introducing-the-class-interface)
- [<span data-ttu-id="d9ecb-149">Důležité informace o zabezpečení sestavení</span><span class="sxs-lookup"><span data-stu-id="d9ecb-149">Assembly Security Considerations</span></span>](../app-domains/assembly-security-considerations.md)
- [<span data-ttu-id="d9ecb-150">Tlbexp.exe (exportér knihovny typů)</span><span class="sxs-lookup"><span data-stu-id="d9ecb-150">Tlbexp.exe (Type Library Exporter)</span></span>](../tools/tlbexp-exe-type-library-exporter.md)
- [<span data-ttu-id="d9ecb-151">Registrování sestav pomocí modelu COM</span><span class="sxs-lookup"><span data-stu-id="d9ecb-151">Registering Assemblies with COM</span></span>](registering-assemblies-with-com.md)
- <span data-ttu-id="d9ecb-152">[Postupy: Knihovny typů vkládání jako prostředky systému Win32 do aplikací](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d9ecb-152">[How to: Embed Type Libraries as Win32 Resources in Applications](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100))</span></span>
