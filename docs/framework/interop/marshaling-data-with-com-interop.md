---
title: Zařazování dat se spoluprací COM
ms.date: 09/07/2017
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
ms.openlocfilehash: ae41713d5349321725599c0c38d7c6fc515c374b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181376"
---
# <a name="marshaling-data-with-com-interop"></a><span data-ttu-id="55543-102">Zařazování dat se spoluprací COM</span><span class="sxs-lookup"><span data-stu-id="55543-102">Marshaling Data with COM Interop</span></span>
<span data-ttu-id="55543-103">Com interop poskytuje podporu pro použití objektů COM ze spravovaného kódu a vystavení spravovaných objektů com.</span><span class="sxs-lookup"><span data-stu-id="55543-103">COM interop provides support for both using COM objects from managed code and exposing managed objects to COM.</span></span> <span data-ttu-id="55543-104">Podpora pro zařazování dat do a z COM je rozsáhlá a téměř vždy poskytuje správné zařazování chování.</span><span class="sxs-lookup"><span data-stu-id="55543-104">Support for marshaling data to and from COM is extensive and almost always provides the correct marshaling behavior.</span></span>  
  
 <span data-ttu-id="55543-105">Sada Windows SDK obsahuje následující nástroje pro propojení COM:</span><span class="sxs-lookup"><span data-stu-id="55543-105">The Windows SDK includes the following COM interop tools:</span></span>  
  
- <span data-ttu-id="55543-106">[Importknihovny typů (Tlbimp.exe),](../tools/tlbimp-exe-type-library-importer.md)který převede knihovnu typů COM na interop sestavení.</span><span class="sxs-lookup"><span data-stu-id="55543-106">[Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md), which converts a COM type library to an interop assembly.</span></span> <span data-ttu-id="55543-107">Z tohoto sestavení interop zařazování služba generuje obálky, které provádějí zařazování dat mezi spravované a nespravované paměti.</span><span class="sxs-lookup"><span data-stu-id="55543-107">From this assembly, the interop marshaling service generates wrappers that perform data marshaling between managed and unmanaged memory.</span></span>  
  
- <span data-ttu-id="55543-108">[Typ knihovny Exportér (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md), který vytváří knihovnu typu COM ze sestavení a generuje obálku, která provádí zařazování během volání metody.</span><span class="sxs-lookup"><span data-stu-id="55543-108">[Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md), which produces a COM type library from an assembly and generates a wrapper that performs marshaling during method calls.</span></span>  
  
 <span data-ttu-id="55543-109">Následující části odkazují na témata, která popisují procesy pro přizpůsobení obálky meziop, pokud můžete (nebo musíte) poskytnout zařazovací zařízení další informace o typu.</span><span class="sxs-lookup"><span data-stu-id="55543-109">The following sections link to topics that describe the processes for customizing interop wrappers when you can (or must) supply the marshaler with additional type information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="55543-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="55543-110">In This Section</span></span>  
<span data-ttu-id="55543-111">[Postup: Ruční vytvoření obalů](how-to-create-wrappers-manually.md) Popisuje, jak ručně vytvořit obálku com ve spravovaném zdrojovém kódu.</span><span class="sxs-lookup"><span data-stu-id="55543-111">[How to: Create Wrappers Manually](how-to-create-wrappers-manually.md) Describes how to create a COM wrapper manually in managed source code.</span></span>

 [<span data-ttu-id="55543-112">Postup: Migrace spravovaného kódu DCOM do WCF</span><span class="sxs-lookup"><span data-stu-id="55543-112">How to: Migrate Managed-Code DCOM to WCF</span></span>](how-to-migrate-managed-code-dcom-to-wcf.md)  
 <span data-ttu-id="55543-113">Popisuje, jak migrovat spravovaný kód DCOM do WCF pro nejbezpečnější řešení.</span><span class="sxs-lookup"><span data-stu-id="55543-113">Describes how to migrate managed DCOM code to WCF for the most secure solution.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="55543-114">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="55543-114">Related Sections</span></span>  
 <span data-ttu-id="55543-115">[Datové typy COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="55543-115">[COM Data Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span></span>  
 <span data-ttu-id="55543-116">Poskytuje odpovídající spravované a nespravované datové typy.</span><span class="sxs-lookup"><span data-stu-id="55543-116">Provides corresponding managed and unmanaged data types.</span></span>  
  
 <span data-ttu-id="55543-117">[Přizpůsobení com callable obálky](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="55543-117">[Customizing COM Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))</span></span>  
 <span data-ttu-id="55543-118">Popisuje, jak explicitně zařazovat datové typy pomocí atributu <xref:System.Runtime.InteropServices.MarshalAsAttribute> v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="55543-118">Describes how to explicitly marshal data types using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute at design time.</span></span>  
  
 <span data-ttu-id="55543-119">[Přizpůsobení reložií s runtime voláním](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="55543-119">[Customizing Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span></span>  
 <span data-ttu-id="55543-120">Popisuje, jak upravit zařazování chování typů v sestavení interop a jak definovat typy COM ručně.</span><span class="sxs-lookup"><span data-stu-id="55543-120">Describes how to adjust the marshaling behavior of types in an interop assembly and how to define COM types manually.</span></span>  
  
 <span data-ttu-id="55543-121">[Pokročilá interoperabilita com](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="55543-121">[Advanced COM Interoperability](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>  
 <span data-ttu-id="55543-122">Obsahuje odkazy na další informace o začlenění komponent modelu COM do aplikace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="55543-122">Provides links to more information about incorporating COM components into your .NET Framework application.</span></span>  
  
 <span data-ttu-id="55543-123">[Souhrn převodu knihovny sestavení k typu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="55543-123">[Assembly to Type Library Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span></span>  
 <span data-ttu-id="55543-124">Popisuje sestavení, které má být napsáno, aby byl proces převodu exportu knihovny zadán.</span><span class="sxs-lookup"><span data-stu-id="55543-124">Describes the assembly to type library export conversion process.</span></span>  
  
 <span data-ttu-id="55543-125">[Souhrn převodu knihovny typů do sestavení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="55543-125">[Type Library to Assembly Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span></span>  
 <span data-ttu-id="55543-126">Popisuje knihovnu typů pro proces převodu převodu sestavení.</span><span class="sxs-lookup"><span data-stu-id="55543-126">Describes the type library to assembly import conversion process.</span></span>  
  
 <span data-ttu-id="55543-127">[Spolupráce pomocí obecných typů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="55543-127">[Interoperating Using Generic Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span></span>  
 <span data-ttu-id="55543-128">Popisuje, které akce jsou podporovány při použití obecných typů pro interoperabilitu com.</span><span class="sxs-lookup"><span data-stu-id="55543-128">Describes which actions are supported when using generic types for COM interoperability.</span></span>
