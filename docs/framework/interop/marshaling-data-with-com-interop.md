---
title: Zařazování dat se spoluprací COM
description: Viz články, které se týkají zařazování dat pomocí zprostředkovatele komunikace s objekty COM. Nástroje Tlbimp.exe a Tlbexp.exe převádějí mezi knihovnou typu COM a definičním sestavením.
ms.date: 09/07/2017
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
ms.openlocfilehash: eedfb60a75e2fe5fafdaa786dbb54adddf28400e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621506"
---
# <a name="marshaling-data-with-com-interop"></a><span data-ttu-id="20417-104">Zařazování dat se spoluprací COM</span><span class="sxs-lookup"><span data-stu-id="20417-104">Marshaling Data with COM Interop</span></span>
<span data-ttu-id="20417-105">Zprostředkovatel komunikace s objekty COM poskytuje podporu jak pro použití objektů COM ze spravovaného kódu, tak pro vystavování spravovaných objektů do modelu COM.</span><span class="sxs-lookup"><span data-stu-id="20417-105">COM interop provides support for both using COM objects from managed code and exposing managed objects to COM.</span></span> <span data-ttu-id="20417-106">Podpora pro zařazování dat do a z modelu COM je rozsáhlá a téměř vždy poskytuje správné chování při zařazování.</span><span class="sxs-lookup"><span data-stu-id="20417-106">Support for marshaling data to and from COM is extensive and almost always provides the correct marshaling behavior.</span></span>  
  
 <span data-ttu-id="20417-107">Windows SDK obsahuje následující nástroje COM interop:</span><span class="sxs-lookup"><span data-stu-id="20417-107">The Windows SDK includes the following COM interop tools:</span></span>  
  
- <span data-ttu-id="20417-108">[Importér knihovny typů (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md), který převede knihovnu typů modelu COM na definiční sestavení.</span><span class="sxs-lookup"><span data-stu-id="20417-108">[Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md), which converts a COM type library to an interop assembly.</span></span> <span data-ttu-id="20417-109">Z tohoto sestavení vygeneruje služba interop marshaling obálky, které provádějí zařazování dat mezi spravovanou a nespravovanou pamětí.</span><span class="sxs-lookup"><span data-stu-id="20417-109">From this assembly, the interop marshaling service generates wrappers that perform data marshaling between managed and unmanaged memory.</span></span>  
  
- <span data-ttu-id="20417-110">[Exportér knihovny typů (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md), která vytvoří knihovnu typů modelu COM ze sestavení a vygeneruje obálku, která provádí zařazování při volání metody.</span><span class="sxs-lookup"><span data-stu-id="20417-110">[Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md), which produces a COM type library from an assembly and generates a wrapper that performs marshaling during method calls.</span></span>  
  
 <span data-ttu-id="20417-111">Následující části odkazují na témata, která popisují procesy pro přizpůsobení obálky spolupráce, když můžete (nebo musíte) zařazovacímu programu dodat Další informace o typu.</span><span class="sxs-lookup"><span data-stu-id="20417-111">The following sections link to topics that describe the processes for customizing interop wrappers when you can (or must) supply the marshaler with additional type information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="20417-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="20417-112">In This Section</span></span>  
<span data-ttu-id="20417-113">[Postupy: ruční vytváření obálek](how-to-create-wrappers-manually.md) Popisuje, jak vytvořit obálku COM ručně ve spravovaném zdrojovém kódu.</span><span class="sxs-lookup"><span data-stu-id="20417-113">[How to: Create Wrappers Manually](how-to-create-wrappers-manually.md) Describes how to create a COM wrapper manually in managed source code.</span></span>

 [<span data-ttu-id="20417-114">Postupy: Migrace spravovaného kódu DCOM do WCF</span><span class="sxs-lookup"><span data-stu-id="20417-114">How to: Migrate Managed-Code DCOM to WCF</span></span>](how-to-migrate-managed-code-dcom-to-wcf.md)  
 <span data-ttu-id="20417-115">V této části najdete popis postupu migrace spravovaného kódu DCOM do WCF pro nejbezpečnější řešení.</span><span class="sxs-lookup"><span data-stu-id="20417-115">Describes how to migrate managed DCOM code to WCF for the most secure solution.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="20417-116">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="20417-116">Related Sections</span></span>  
 <span data-ttu-id="20417-117">[Datové typy COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="20417-117">[COM Data Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span></span>  
 <span data-ttu-id="20417-118">Poskytuje odpovídající spravované a nespravované datové typy.</span><span class="sxs-lookup"><span data-stu-id="20417-118">Provides corresponding managed and unmanaged data types.</span></span>  
  
 <span data-ttu-id="20417-119">[Přizpůsobení vydaných obálek modelu COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="20417-119">[Customizing COM Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))</span></span>  
 <span data-ttu-id="20417-120">V této části najdete popis postupu explicitního zařazování datových typů pomocí <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributu v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="20417-120">Describes how to explicitly marshal data types using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute at design time.</span></span>  
  
 <span data-ttu-id="20417-121">[Přizpůsobení obálek za běhu, které se budou volat](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="20417-121">[Customizing Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span></span>  
 <span data-ttu-id="20417-122">Popisuje, jak upravit chování zařazování typů v definičním sestavení a jak definovat typy COM ručně.</span><span class="sxs-lookup"><span data-stu-id="20417-122">Describes how to adjust the marshaling behavior of types in an interop assembly and how to define COM types manually.</span></span>  
  
 <span data-ttu-id="20417-123">[Pokročilá interoperabilita modelu COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="20417-123">[Advanced COM Interoperability](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>  
 <span data-ttu-id="20417-124">Obsahuje odkazy na Další informace o zahrnutí komponent modelu COM do aplikace .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="20417-124">Provides links to more information about incorporating COM components into your .NET Framework application.</span></span>  
  
 <span data-ttu-id="20417-125">[Souhrn převodu sestavení na knihovnu typů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="20417-125">[Assembly to Type Library Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span></span>  
 <span data-ttu-id="20417-126">Popisuje sestavení pro proces převodu exportu knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="20417-126">Describes the assembly to type library export conversion process.</span></span>  
  
 <span data-ttu-id="20417-127">[Souhrn převodu knihovny typů na sestavení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="20417-127">[Type Library to Assembly Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span></span>  
 <span data-ttu-id="20417-128">Popisuje proces převodu knihovny typů na sestavení.</span><span class="sxs-lookup"><span data-stu-id="20417-128">Describes the type library to assembly import conversion process.</span></span>  
  
 <span data-ttu-id="20417-129">[Spolupráce pomocí obecných typů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="20417-129">[Interoperating Using Generic Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span></span>  
 <span data-ttu-id="20417-130">Popisuje, které akce jsou podporovány při použití obecných typů pro interoperabilitu modelu COM.</span><span class="sxs-lookup"><span data-stu-id="20417-130">Describes which actions are supported when using generic types for COM interoperability.</span></span>
