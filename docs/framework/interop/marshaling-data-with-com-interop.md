---
title: Zařazování dat se spoluprací COM
ms.date: 09/07/2017
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
ms.openlocfilehash: 24fa390c94baaa0fe009ebe513f2eb7aa34d34fa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73114001"
---
# <a name="marshaling-data-with-com-interop"></a><span data-ttu-id="82a5e-102">Zařazování dat se spoluprací COM</span><span class="sxs-lookup"><span data-stu-id="82a5e-102">Marshaling Data with COM Interop</span></span>
<span data-ttu-id="82a5e-103">Zprostředkovatel komunikace s objekty COM poskytuje podporu jak pro použití objektů COM ze spravovaného kódu, tak pro vystavování spravovaných objektů do modelu COM.</span><span class="sxs-lookup"><span data-stu-id="82a5e-103">COM interop provides support for both using COM objects from managed code and exposing managed objects to COM.</span></span> <span data-ttu-id="82a5e-104">Podpora pro zařazování dat do a z modelu COM je rozsáhlá a téměř vždy poskytuje správné chování při zařazování.</span><span class="sxs-lookup"><span data-stu-id="82a5e-104">Support for marshaling data to and from COM is extensive and almost always provides the correct marshaling behavior.</span></span>  
  
 <span data-ttu-id="82a5e-105">Windows SDK obsahuje následující nástroje COM interop:</span><span class="sxs-lookup"><span data-stu-id="82a5e-105">The Windows SDK includes the following COM interop tools:</span></span>  
  
- <span data-ttu-id="82a5e-106">[Importér knihovny typů (Tlbimp. exe)](../tools/tlbimp-exe-type-library-importer.md), který převede knihovnu typů modelu COM na definiční sestavení.</span><span class="sxs-lookup"><span data-stu-id="82a5e-106">[Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md), which converts a COM type library to an interop assembly.</span></span> <span data-ttu-id="82a5e-107">Z tohoto sestavení vygeneruje služba interop marshaling obálky, které provádějí zařazování dat mezi spravovanou a nespravovanou pamětí.</span><span class="sxs-lookup"><span data-stu-id="82a5e-107">From this assembly, the interop marshaling service generates wrappers that perform data marshaling between managed and unmanaged memory.</span></span>  
  
- <span data-ttu-id="82a5e-108">[Exportér knihovny typů (Tlbexp. exe)](../tools/tlbexp-exe-type-library-exporter.md), který vytváří knihovnu typů modelu COM ze sestavení a generuje obálku, která provádí zařazování během volání metody.</span><span class="sxs-lookup"><span data-stu-id="82a5e-108">[Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md), which produces a COM type library from an assembly and generates a wrapper that performs marshaling during method calls.</span></span>  
  
 <span data-ttu-id="82a5e-109">Následující části odkazují na témata, která popisují procesy pro přizpůsobení obálky spolupráce, když můžete (nebo musíte) zařazovacímu programu dodat Další informace o typu.</span><span class="sxs-lookup"><span data-stu-id="82a5e-109">The following sections link to topics that describe the processes for customizing interop wrappers when you can (or must) supply the marshaler with additional type information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="82a5e-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="82a5e-110">In This Section</span></span>  
<span data-ttu-id="82a5e-111">[Postupy: ruční vytváření obálek](how-to-create-wrappers-manually.md) </span><span class="sxs-lookup"><span data-stu-id="82a5e-111">[How to: Create Wrappers Manually](how-to-create-wrappers-manually.md) </span></span>  
<span data-ttu-id="82a5e-112">Popisuje, jak vytvořit obálku COM ručně ve spravovaném zdrojovém kódu.</span><span class="sxs-lookup"><span data-stu-id="82a5e-112">Describes how to create a COM wrapper manually in managed source code.</span></span> 
 
 [<span data-ttu-id="82a5e-113">Postup: Migrace spravovaného kódu DCOM do WCF</span><span class="sxs-lookup"><span data-stu-id="82a5e-113">How to: Migrate Managed-Code DCOM to WCF</span></span>](how-to-migrate-managed-code-dcom-to-wcf.md)  
 <span data-ttu-id="82a5e-114">V této části najdete popis postupu migrace spravovaného kódu DCOM do WCF pro nejbezpečnější řešení.</span><span class="sxs-lookup"><span data-stu-id="82a5e-114">Describes how to migrate managed DCOM code to WCF for the most secure solution.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="82a5e-115">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="82a5e-115">Related Sections</span></span>  
 <span data-ttu-id="82a5e-116">[Datové typy COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="82a5e-116">[COM Data Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span></span>  
 <span data-ttu-id="82a5e-117">Poskytuje odpovídající spravované a nespravované datové typy.</span><span class="sxs-lookup"><span data-stu-id="82a5e-117">Provides corresponding managed and unmanaged data types.</span></span>  
  
 <span data-ttu-id="82a5e-118">[Přizpůsobení vydaných obálek modelu COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="82a5e-118">[Customizing COM Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))</span></span>  
 <span data-ttu-id="82a5e-119">V této části najdete popis postupu explicitního zařazování datových typů pomocí atributu <xref:System.Runtime.InteropServices.MarshalAsAttribute> v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="82a5e-119">Describes how to explicitly marshal data types using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute at design time.</span></span>  
  
 <span data-ttu-id="82a5e-120">[Přizpůsobení obálek za běhu, které se budou volat](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="82a5e-120">[Customizing Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span></span>  
 <span data-ttu-id="82a5e-121">Popisuje, jak upravit chování zařazování typů v definičním sestavení a jak definovat typy COM ručně.</span><span class="sxs-lookup"><span data-stu-id="82a5e-121">Describes how to adjust the marshaling behavior of types in an interop assembly and how to define COM types manually.</span></span>  
  
 <span data-ttu-id="82a5e-122">[Pokročilá interoperabilita modelu COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="82a5e-122">[Advanced COM Interoperability](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>  
 <span data-ttu-id="82a5e-123">Obsahuje odkazy na Další informace o zahrnutí komponent modelu COM do aplikace .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="82a5e-123">Provides links to more information about incorporating COM components into your .NET Framework application.</span></span>  
  
 <span data-ttu-id="82a5e-124">[Souhrn převodu sestavení na knihovnu typů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="82a5e-124">[Assembly to Type Library Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span></span>  
 <span data-ttu-id="82a5e-125">Popisuje sestavení pro proces převodu exportu knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="82a5e-125">Describes the assembly to type library export conversion process.</span></span>  
  
 <span data-ttu-id="82a5e-126">[Souhrn převodu knihovny typů na sestavení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="82a5e-126">[Type Library to Assembly Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span></span>  
 <span data-ttu-id="82a5e-127">Popisuje proces převodu knihovny typů na sestavení.</span><span class="sxs-lookup"><span data-stu-id="82a5e-127">Describes the type library to assembly import conversion process.</span></span>  
  
 <span data-ttu-id="82a5e-128">[Spolupráce pomocí obecných typů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="82a5e-128">[Interoperating Using Generic Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span></span>  
 <span data-ttu-id="82a5e-129">Popisuje, které akce jsou podporovány při použití obecných typů pro interoperabilitu modelu COM.</span><span class="sxs-lookup"><span data-stu-id="82a5e-129">Describes which actions are supported when using generic types for COM interoperability.</span></span>
