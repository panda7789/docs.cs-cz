---
title: "Zabalení sestavení pro model COM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 72b9237a8abeee936070799c5087abc6b45ff3b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="packaging-an-assembly-for-com"></a><span data-ttu-id="bfa34-102">Zabalení sestavení pro model COM</span><span class="sxs-lookup"><span data-stu-id="bfa34-102">Packaging an Assembly for COM</span></span>
<span data-ttu-id="bfa34-103">COM vývojáři mohou využít následující informace o spravovaných typů, že chtějí začlenit ve svých aplikacích:</span><span class="sxs-lookup"><span data-stu-id="bfa34-103">COM developers can benefit from the following information about the managed types they plan to incorporate in their application:</span></span>  
  
-   <span data-ttu-id="bfa34-104">Seznam typů, které můžou využívat aplikace modelu COM</span><span class="sxs-lookup"><span data-stu-id="bfa34-104">A list of types that COM applications can consume</span></span>  
  
     <span data-ttu-id="bfa34-105">Některé spravované typy jsou neviditelná pro COM; Některé jsou viditelné, ale není vytvořitelné; a některé jsou viditelné a vytvořitelné.</span><span class="sxs-lookup"><span data-stu-id="bfa34-105">Some managed types are invisible to COM; some are visible but not creatable; and some are both visible and creatable.</span></span> <span data-ttu-id="bfa34-106">Sestavení může obsahovat libovolnou kombinaci typů neviditelná, viditelné, není vytvořitelné a vytvořitelné.</span><span class="sxs-lookup"><span data-stu-id="bfa34-106">An assembly can comprise any combination of invisible, visible, not creatable, and creatable types.</span></span> <span data-ttu-id="bfa34-107">Pro úplnost Identifikujte typy v sestavení, které máte v úmyslu umístěte do modelu COM, zejména v případě, že tyto typy jsou podmnožinou typy vystavený rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bfa34-107">For completeness, identify the types in an assembly that you intend to expose to COM, especially when those types are a subset of the types exposed to the .NET Framework.</span></span>  
  
     <span data-ttu-id="bfa34-108">Další informace najdete v tématu [kvalifikace typů .NET pro spolupráci](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="bfa34-108">For additional information, see [Qualifying .NET Types for Interoperation](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md).</span></span>  
  
-   <span data-ttu-id="bfa34-109">Správa verzí pokyny</span><span class="sxs-lookup"><span data-stu-id="bfa34-109">Versioning instructions</span></span>  
  
     <span data-ttu-id="bfa34-110">Spravované třídy, které implementují rozhraní třídy (rozhraní modelu COM generované zprostředkovatel komunikace s objekty) se vztahují omezení Správa verzí.</span><span class="sxs-lookup"><span data-stu-id="bfa34-110">Managed classes that implement the class interface (a COM interop-generated interface) are subject to versioning restrictions.</span></span>  
  
     <span data-ttu-id="bfa34-111">Na pomocí třídy rozhraní, naleznete na adrese [představení rozhraní třídy](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024).</span><span class="sxs-lookup"><span data-stu-id="bfa34-111">For guidelines on using the class interface, see [Introducing the Class Interface](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024).</span></span>  
  
-   <span data-ttu-id="bfa34-112">Pokyny k nasazení</span><span class="sxs-lookup"><span data-stu-id="bfa34-112">Deployment instructions</span></span>  
  
     <span data-ttu-id="bfa34-113">Sestavení se silným názvem, které jsou podepsané vydavatelem lze nainstalovat do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="bfa34-113">Strong-named assemblies that are signed by a publisher can be installed into the global assembly cache.</span></span> <span data-ttu-id="bfa34-114">Nepodepsaná sestavení musí být nainstalován na počítači uživatele jako soukromá sestavení.</span><span class="sxs-lookup"><span data-stu-id="bfa34-114">Unsigned assemblies must be installed on the user's machine as private assemblies.</span></span>  
  
     <span data-ttu-id="bfa34-115">Další informace najdete v tématu [důležité informace o zabezpečení sestavení](../../../docs/framework/app-domains/assembly-security-considerations.md).</span><span class="sxs-lookup"><span data-stu-id="bfa34-115">For additional information, see [Assembly Security Considerations](../../../docs/framework/app-domains/assembly-security-considerations.md).</span></span>  
  
-   <span data-ttu-id="bfa34-116">Zahrnutí knihovny typů</span><span class="sxs-lookup"><span data-stu-id="bfa34-116">Type library inclusion</span></span>  
  
     <span data-ttu-id="bfa34-117">Většina typů vyžadují knihovny typů při spotřebovávají aplikace modelu COM.</span><span class="sxs-lookup"><span data-stu-id="bfa34-117">Most types require a type library when consumed by a COM application.</span></span> <span data-ttu-id="bfa34-118">Můžete vygenerovat knihovny typů nebo mít COM vývojáři provedení této úlohy.</span><span class="sxs-lookup"><span data-stu-id="bfa34-118">You can generate a type library or have COM developers perform this task.</span></span> <span data-ttu-id="bfa34-119">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Poskytuje následující možnosti pro generování knihovny typů:</span><span class="sxs-lookup"><span data-stu-id="bfa34-119">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] provides the following options for generating a type library:</span></span>  
  
    -   [<span data-ttu-id="bfa34-120">Knihovna typů – Exportér</span><span class="sxs-lookup"><span data-stu-id="bfa34-120">Type Library Exporter</span></span>](#cpconpackagingassemblyforcomanchor1)  
  
    -   [<span data-ttu-id="bfa34-121">TypeLibConverter – třída</span><span class="sxs-lookup"><span data-stu-id="bfa34-121">TypeLibConverter Class</span></span>](#cpconpackagingassemblyforcomanchor2)  
  
    -   [<span data-ttu-id="bfa34-122">Registrace sestavení – nástroj</span><span class="sxs-lookup"><span data-stu-id="bfa34-122">Assembly Registration Tool</span></span>](#cpconpackagingassemblyforcomanchor3)  
  
    -   [<span data-ttu-id="bfa34-123">Nástroj pro instalaci služeb .NET</span><span class="sxs-lookup"><span data-stu-id="bfa34-123">.NET Services Installation Tool</span></span>](#cpconpackagingassemblyforcomanchor4)  
  
     <span data-ttu-id="bfa34-124">Bez ohledu na to mechanismus, který zvolíte jsou zahrnuty pouze veřejné typy definované v sestavení, ve kterém zadáte v knihovně generovaného typu.</span><span class="sxs-lookup"><span data-stu-id="bfa34-124">Regardless of the mechanism you choose, only public types defined in the assembly you supply are included in the generated type library.</span></span>  
  
     <span data-ttu-id="bfa34-125">Můžete balíček knihovny typů jako samostatný soubor nebo vložit jako zdrojového souboru Win32 v rámci. Aplikace založené na Asp.net.</span><span class="sxs-lookup"><span data-stu-id="bfa34-125">You can package a type library as a separate file or embed it as Win32 resource file within a .NET-based application.</span></span> <span data-ttu-id="bfa34-126">Microsoft Visual Basic 6.0 provést tuto úlohu pro vás automaticky. ale při použití [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)], je nutné ručně vložit vaší knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="bfa34-126">Microsoft Visual Basic 6.0 performed this task for you automatically; however, when using [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)], you must embed your type library manually.</span></span> <span data-ttu-id="bfa34-127">Pokyny najdete v tématu [postupy: vložení knihovny typů jako Win32 prostředky v. Aplikace založené na NET](http://msdn.microsoft.com/en-us/c97b4b8c-2ab7-4ac7-8fc8-0ba5c5d59c44).</span><span class="sxs-lookup"><span data-stu-id="bfa34-127">For instructions, see [How to: Embed Type Libraries as Win32 Resources in .NET-Based Applications](http://msdn.microsoft.com/en-us/c97b4b8c-2ab7-4ac7-8fc8-0ba5c5d59c44).</span></span>  
  
<a name="cpconpackagingassemblyforcomanchor1"></a>   
## <a name="type-library-exporter"></a><span data-ttu-id="bfa34-128">knihovna typů – exportér</span><span class="sxs-lookup"><span data-stu-id="bfa34-128">Type Library Exporter</span></span>  
 <span data-ttu-id="bfa34-129">[Exportér knihovny typů (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) je nástroj příkazového řádku, který převádí třídy a rozhraní, které jsou součástí sestavení pro knihovny typů COM.</span><span class="sxs-lookup"><span data-stu-id="bfa34-129">The [Type Library Exporter (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) is a command-line tool that converts the classes and interfaces contained in an assembly to a COM type library.</span></span> <span data-ttu-id="bfa34-130">Jakmile informace o typu třídy je k dispozici, klienti COM můžete vytvořit instance třídy rozhraní .NET a volání metody instance, stejně, jako by šlo objektu COM.</span><span class="sxs-lookup"><span data-stu-id="bfa34-130">Once the type information of the class is available, COM clients can create an instance of the .NET class and call the methods of the instance, just as if it were a COM object.</span></span> <span data-ttu-id="bfa34-131">Tlbexp.exe převede celé sestavení najednou.</span><span class="sxs-lookup"><span data-stu-id="bfa34-131">Tlbexp.exe converts an entire assembly at one time.</span></span> <span data-ttu-id="bfa34-132">Pomocí nástroje Tlbexp.exe nelze generovat informace o typu pro podtypy definované v sestavení.</span><span class="sxs-lookup"><span data-stu-id="bfa34-132">You cannot use Tlbexp.exe to generate type information for a subset of the types defined in an assembly.</span></span>  
  
<a name="cpconpackagingassemblyforcomanchor2"></a>   
## <a name="typelibconverter-class"></a><span data-ttu-id="bfa34-133">TypeLibConverter – třída</span><span class="sxs-lookup"><span data-stu-id="bfa34-133">TypeLibConverter Class</span></span>  
 <span data-ttu-id="bfa34-134"><xref:System.Runtime.InteropServices.TypeLibConverter> Třídy, které jsou umístěné v **System.Runtime.Interop** převede obor názvů, třídy a rozhraní, které jsou součástí sestavení pro knihovny typů COM.</span><span class="sxs-lookup"><span data-stu-id="bfa34-134">The <xref:System.Runtime.InteropServices.TypeLibConverter> class, located in the **System.Runtime.Interop** namespace, converts the classes and interfaces contained in an assembly to a COM type library.</span></span> <span data-ttu-id="bfa34-135">Toto rozhraní API vytváří stejný typ informace jako Export knihovny typů popsané v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="bfa34-135">This API produces the same type information as the Type Library Exporter, described in the previous section.</span></span>  
  
 <span data-ttu-id="bfa34-136">**TypeLibConverter – třída** implementuje <xref:System.Runtime.InteropServices.ITypeLibConverter>.</span><span class="sxs-lookup"><span data-stu-id="bfa34-136">The **TypeLibConverter class** implements the <xref:System.Runtime.InteropServices.ITypeLibConverter>.</span></span>  
  
<a name="cpconpackagingassemblyforcomanchor3"></a>   
## <a name="assembly-registration-tool"></a><span data-ttu-id="bfa34-137">Registrace sestavení – nástroj</span><span class="sxs-lookup"><span data-stu-id="bfa34-137">Assembly Registration Tool</span></span>  
 <span data-ttu-id="bfa34-138">[Nástroj pro registraci sestavení (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) vygenerovat a registraci knihovny typů, při použití **/tlb:** možnost.</span><span class="sxs-lookup"><span data-stu-id="bfa34-138">The [Assembly Registration Tool (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) can generate and register a type library when you apply the **/tlb:** option.</span></span> <span data-ttu-id="bfa34-139">Klienti COM vyžadují instalaci knihovny typů v registru systému Windows.</span><span class="sxs-lookup"><span data-stu-id="bfa34-139">COM clients require that type libraries be installed in the Windows registry.</span></span> <span data-ttu-id="bfa34-140">Bez této možnosti Regasm.exe pouze registruje typy v sestavení, není knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="bfa34-140">Without this option, Regasm.exe only registers the types in an assembly, not the type library.</span></span> <span data-ttu-id="bfa34-141">Registrace typy v sestavení a registraci knihovny typů jsou odlišné aktivity.</span><span class="sxs-lookup"><span data-stu-id="bfa34-141">Registering the types in an assembly and registering the type library are distinct activities.</span></span>  
  
<a name="cpconpackagingassemblyforcomanchor4"></a>   
## <a name="net-services-installation-tool"></a><span data-ttu-id="bfa34-142">Nástroj pro instalaci služeb .NET</span><span class="sxs-lookup"><span data-stu-id="bfa34-142">.NET Services Installation Tool</span></span>  
 <span data-ttu-id="bfa34-143">[Nástroj pro instalaci služeb .NET (Regsvcs.exe)](../../../docs/framework/tools/regsvcs-exe-net-services-installation-tool.md) přidá spravované třídy do služby součásti systému Windows 2000 a kombinuje několik úkolů v rámci jediného nástroje.</span><span class="sxs-lookup"><span data-stu-id="bfa34-143">The [.NET Services Installation Tool (Regsvcs.exe)](../../../docs/framework/tools/regsvcs-exe-net-services-installation-tool.md) adds managed classes to Windows 2000 Component Services and combines several tasks within a single tool.</span></span> <span data-ttu-id="bfa34-144">Kromě načítání a registraci sestavení, Regsvcs.exe generovat, zaregistrujte a nainstalovat do existující aplikace COM + 1.0 knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="bfa34-144">In addition to loading and registering an assembly, Regsvcs.exe can generate, register, and install the type library into an existing COM+ 1.0 application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfa34-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="bfa34-145">See Also</span></span>  
 <xref:System.Runtime.InteropServices.TypeLibConverter>  
 <xref:System.Runtime.InteropServices.ITypeLibConverter>  
 [<span data-ttu-id="bfa34-146">Vystavení komponent architektury .NET Framework pro COM</span><span class="sxs-lookup"><span data-stu-id="bfa34-146">Exposing .NET Framework Components to COM</span></span>](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [<span data-ttu-id="bfa34-147">Kvalifikace typů .NET pro spolupráci</span><span class="sxs-lookup"><span data-stu-id="bfa34-147">Qualifying .NET Types for Interoperation</span></span>](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md)  
 [<span data-ttu-id="bfa34-148">Představení rozhraní – třída</span><span class="sxs-lookup"><span data-stu-id="bfa34-148">Introducing the Class Interface</span></span>](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024)  
 [<span data-ttu-id="bfa34-149">Důležité informace o zabezpečení sestavení</span><span class="sxs-lookup"><span data-stu-id="bfa34-149">Assembly Security Considerations</span></span>](../../../docs/framework/app-domains/assembly-security-considerations.md)  
 [<span data-ttu-id="bfa34-150">Tlbexp.exe (exportér knihovny typů)</span><span class="sxs-lookup"><span data-stu-id="bfa34-150">Tlbexp.exe (Type Library Exporter)</span></span>](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)  
 [<span data-ttu-id="bfa34-151">Registrování sestav pomocí modelu COM</span><span class="sxs-lookup"><span data-stu-id="bfa34-151">Registering Assemblies with COM</span></span>](../../../docs/framework/interop/registering-assemblies-with-com.md)  
 [<span data-ttu-id="bfa34-152">Postupy: vložení knihovny typů jako Win32 prostředky v aplikacích</span><span class="sxs-lookup"><span data-stu-id="bfa34-152">How to: Embed Type Libraries as Win32 Resources in Applications</span></span>](http://msdn.microsoft.com/en-us/c97b4b8c-2ab7-4ac7-8fc8-0ba5c5d59c44)
