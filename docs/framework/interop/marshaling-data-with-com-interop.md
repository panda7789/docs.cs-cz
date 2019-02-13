---
title: Zařazování dat se spoluprací COM
ms.date: 09/07/2017
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab4dbdd0a69b158ff5c49949bee5089bd3fe095c
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/13/2019
ms.locfileid: "56220530"
---
# <a name="marshaling-data-with-com-interop"></a><span data-ttu-id="c82df-102">Zařazování dat se spoluprací COM</span><span class="sxs-lookup"><span data-stu-id="c82df-102">Marshaling Data with COM Interop</span></span>
<span data-ttu-id="c82df-103">Komunikace s objekty COM poskytuje podporu pro používání objektů modelu COM ze spravovaného kódu i vystavení spravované objekty do modelu COM.</span><span class="sxs-lookup"><span data-stu-id="c82df-103">COM interop provides support for both using COM objects from managed code and exposing managed objects to COM.</span></span> <span data-ttu-id="c82df-104">Podpora zařazování dat do a z modelu COM je rozsáhlý a téměř vždy poskytuje správné chování zařazování.</span><span class="sxs-lookup"><span data-stu-id="c82df-104">Support for marshaling data to and from COM is extensive and almost always provides the correct marshaling behavior.</span></span>  
  
 <span data-ttu-id="c82df-105">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Obsahuje následující nástroje vzájemné spolupráce COM:</span><span class="sxs-lookup"><span data-stu-id="c82df-105">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] includes the following COM interop tools:</span></span>  
  
-   <span data-ttu-id="c82df-106">[Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), která převede knihovnu typů modelu COM pro definiční sestavení.</span><span class="sxs-lookup"><span data-stu-id="c82df-106">[Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), which converts a COM type library to an interop assembly.</span></span> <span data-ttu-id="c82df-107">Z tohoto sestavení zprostředkovatele komunikace s objekty zařazování služby generuje obálky, které provádějí data zařazování mezi spravovanými a nespravovanými paměti.</span><span class="sxs-lookup"><span data-stu-id="c82df-107">From this assembly, the interop marshaling service generates wrappers that perform data marshaling between managed and unmanaged memory.</span></span>  
  
-   <span data-ttu-id="c82df-108">[Exportér knihovny (Tlbexp.exe) zadejte](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), který vytvoří knihovnu typů modelu COM ze sestavení a generuje obálku, která provádí zařazování během volání metody.</span><span class="sxs-lookup"><span data-stu-id="c82df-108">[Type Library Exporter (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), which produces a COM type library from an assembly and generates a wrapper that performs marshaling during method calls.</span></span>  
  
 <span data-ttu-id="c82df-109">Následující části odkaz na témata popisující procesy pro přizpůsobení spolupráce obálky, když je můžete (nebo musí) zadat zařazovací modul s informace o dalších typech.</span><span class="sxs-lookup"><span data-stu-id="c82df-109">The following sections link to topics that describe the processes for customizing interop wrappers when you can (or must) supply the marshaler with additional type information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c82df-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="c82df-110">In This Section</span></span>  
<span data-ttu-id="c82df-111">[Postupy: Ruční vytváření obálek](how-to-create-wrappers-manually.md) </span><span class="sxs-lookup"><span data-stu-id="c82df-111">[How to: Create Wrappers Manually](how-to-create-wrappers-manually.md) </span></span>  
<span data-ttu-id="c82df-112">Popisuje, jak ručně vytvořit obálky COM ve spravovaném zdrojovém kódu.</span><span class="sxs-lookup"><span data-stu-id="c82df-112">Describes how to create a COM wrapper manually in managed source code.</span></span> 
 
 [<span data-ttu-id="c82df-113">Postupy: Migrace spravovaného kódu DCOM do WCF</span><span class="sxs-lookup"><span data-stu-id="c82df-113">How to: Migrate Managed-Code DCOM to WCF</span></span>](../../../docs/framework/interop/how-to-migrate-managed-code-dcom-to-wcf.md)  
 <span data-ttu-id="c82df-114">Popisuje postup migrace spravovaného kódu DCOM do WCF nejbezpečnější řešení.</span><span class="sxs-lookup"><span data-stu-id="c82df-114">Describes how to migrate managed DCOM code to WCF for the most secure solution.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c82df-115">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="c82df-115">Related Sections</span></span>  
 <span data-ttu-id="c82df-116">[Datové typy COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c82df-116">[COM Data Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span></span>  
 <span data-ttu-id="c82df-117">Poskytuje odpovídající spravované a nespravované datové typy.</span><span class="sxs-lookup"><span data-stu-id="c82df-117">Provides corresponding managed and unmanaged data types.</span></span>  
  
 <span data-ttu-id="c82df-118">[Přizpůsobení obálek volatelných aplikacemi COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c82df-118">[Customizing COM Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))</span></span>  
 <span data-ttu-id="c82df-119">Popisuje, jak explicitně zařazení pomocí datových typů <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="c82df-119">Describes how to explicitly marshal data types using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute at design time.</span></span>  
  
 <span data-ttu-id="c82df-120">[Přizpůsobení obálek Volatelných za běhu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c82df-120">[Customizing Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span></span>  
 <span data-ttu-id="c82df-121">Popisuje, jak chcete-li upravit chování zařazování typů v sestavení vzájemné spolupráce a tom, jak definovat typy modelu COM ručně.</span><span class="sxs-lookup"><span data-stu-id="c82df-121">Describes how to adjust the marshaling behavior of types in an interop assembly and how to define COM types manually.</span></span>  
  
 <span data-ttu-id="c82df-122">[Rozšířená interoperabilita modelu COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c82df-122">[Advanced COM Interoperability](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>  
 <span data-ttu-id="c82df-123">Obsahuje odkazy na další informace o začlenění komponenty modelu COM do vaší aplikace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c82df-123">Provides links to more information about incorporating COM components into your .NET Framework application.</span></span>  
  
 <span data-ttu-id="c82df-124">[Sestavení zadejte souhrn převodu knihovny](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c82df-124">[Assembly to Type Library Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span></span>  
 <span data-ttu-id="c82df-125">Popisuje sestavení na typ procesu převodu export knihovny.</span><span class="sxs-lookup"><span data-stu-id="c82df-125">Describes the assembly to type library export conversion process.</span></span>  
  
 <span data-ttu-id="c82df-126">[Souhrn převodu sestavení knihovny typů na](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c82df-126">[Type Library to Assembly Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span></span>  
 <span data-ttu-id="c82df-127">Popisuje knihovnu typů do sestavení procesu převodu při importování.</span><span class="sxs-lookup"><span data-stu-id="c82df-127">Describes the type library to assembly import conversion process.</span></span>  
  
 <span data-ttu-id="c82df-128">[Spolupráce pomocí obecných typů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c82df-128">[Interoperating Using Generic Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span></span>  
 <span data-ttu-id="c82df-129">Popisuje akce, které jsou podporovány při použití obecných typů pro interoperabilitu COM.</span><span class="sxs-lookup"><span data-stu-id="c82df-129">Describes which actions are supported when using generic types for COM interoperability.</span></span>
