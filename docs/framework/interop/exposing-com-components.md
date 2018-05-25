---
title: Vystavení komponent COM pro rozhraní .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- exposing COM components to .NET Framework
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: e78b14f1-e487-43cd-9c6d-1a07483f1730
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f644e4f4ff47e31c0f2aaadb577aa6715b445d29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="exposing-com-components-to-the-net-framework"></a><span data-ttu-id="95387-102">Vystavení komponent COM pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="95387-102">Exposing COM Components to the .NET Framework</span></span>
<span data-ttu-id="95387-103">Tento oddíl shrnuje proces nutný k zpřístupnění existující součást COM do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="95387-103">This section summarizes the process needed to expose an existing COM component to managed code.</span></span> <span data-ttu-id="95387-104">Podrobnosti o zápis servery COM, která úzce integrovat s rozhraním .NET Framework, najdete v části [aspekty návrhu pro spolupráci](https://msdn.microsoft.com/library/b59637f6-fe35-40d6-ae72-901e7a707689(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="95387-104">For details about writing COM servers that tightly integrate with the .NET Framework, see [Design Considerations for Interoperation](https://msdn.microsoft.com/library/b59637f6-fe35-40d6-ae72-901e7a707689(v=vs.100)).</span></span>
  
 <span data-ttu-id="95387-105">Existující součásti COM jsou cenné prostředky ve spravovaném kódu jako střední vrstvu obchodní aplikace nebo jako izolované funkce.</span><span class="sxs-lookup"><span data-stu-id="95387-105">Existing COM components are valuable resources in managed code as middle-tier business applications or as isolated functionality.</span></span> <span data-ttu-id="95387-106">Ideální součást má primární spolupracující sestavení a úzce vyhovuje standardům programovací způsobené COM.</span><span class="sxs-lookup"><span data-stu-id="95387-106">An ideal component has a primary interop assembly and conforms tightly to the programming standards imposed by COM.</span></span>  
  
#### <a name="to-expose-com-components-to-the-net-framework"></a><span data-ttu-id="95387-107">K vystavení součástí COM v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="95387-107">To expose COM components to the .NET Framework</span></span>  
  
1.  <span data-ttu-id="95387-108">[Import knihovny typů jako sestavení](importing-a-type-library-as-an-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="95387-108">[Import a type library as an assembly](importing-a-type-library-as-an-assembly.md).</span></span>  
  
     <span data-ttu-id="95387-109">Modul common language runtime požaduje metadata pro všechny typy, včetně typy modelu COM.</span><span class="sxs-lookup"><span data-stu-id="95387-109">The common language runtime requires metadata for all types, including COM types.</span></span> <span data-ttu-id="95387-110">Existuje několik způsobů, jak získat sestavení obsahující typy modelu COM importován jako metadata.</span><span class="sxs-lookup"><span data-stu-id="95387-110">There are several ways to obtain an assembly containing COM types imported as metadata.</span></span>  
  
2.  <span data-ttu-id="95387-111">[Vytvoření typů COM ve spravovaném kódu](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="95387-111">[Create COM types in managed Code](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100)).</span></span>  
  
     <span data-ttu-id="95387-112">Můžete zkontrolovat typy modelu COM, aktivovat instancí a vyvolání metody pro objekt COM stejným způsobem jako u jakékoli spravovaného typu.</span><span class="sxs-lookup"><span data-stu-id="95387-112">You can inspect COM types, activate instances, and invoke methods on the COM object the same way you do for any managed type.</span></span>  
  
3.  <span data-ttu-id="95387-113">[Kompilace projektu interoperability](compiling-an-interop-project.md).</span><span class="sxs-lookup"><span data-stu-id="95387-113">[Compile an interop project](compiling-an-interop-project.md).</span></span>  
  
     <span data-ttu-id="95387-114">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Poskytuje kompilátory pro několik jazyků kompatibilní s specifikace CLS (Common Language), včetně [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C# a C++.</span><span class="sxs-lookup"><span data-stu-id="95387-114">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] provides compilers for several languages compliant with the Common Language Specification (CLS), including [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C#, and C++.</span></span>  
  
4.  <span data-ttu-id="95387-115">[Nasazení aplikace spolupráce](deploying-an-interop-application.md).</span><span class="sxs-lookup"><span data-stu-id="95387-115">[Deploy an interop application](deploying-an-interop-application.md).</span></span>  
  
     <span data-ttu-id="95387-116">Spolupráce – aplikace nejlépe nasazených jako [silným názvem](../app-domains/strong-named-assemblies.md), podepsané sestavení v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="95387-116">Interop applications are best deployed as [strong-named](../app-domains/strong-named-assemblies.md), signed assemblies in the global assembly cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95387-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="95387-117">See Also</span></span>  
 [<span data-ttu-id="95387-118">Spolupráce s nespravovaným kódem</span><span class="sxs-lookup"><span data-stu-id="95387-118">Interoperating with Unmanaged Code</span></span>](index.md)  
 <span data-ttu-id="95387-119">[Aspekty návrhu pro spolupráci](https://msdn.microsoft.com/library/b59637f6-fe35-40d6-ae72-901e7a707689(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="95387-119">[Design Considerations for Interoperation](https://msdn.microsoft.com/library/b59637f6-fe35-40d6-ae72-901e7a707689(v=vs.100))</span></span>  
 [<span data-ttu-id="95387-120">Ukázka zprostředkovatele s objekty COM: klient .NET a server COM</span><span class="sxs-lookup"><span data-stu-id="95387-120">COM Interop Sample: .NET Client and COM Server</span></span>](com-interop-sample-net-client-and-com-server.md)  
 [<span data-ttu-id="95387-121">Jazyková nezávislost a jazykově nezávislé komponenty</span><span class="sxs-lookup"><span data-stu-id="95387-121">Language Independence and Language-Independent Components</span></span>](../../standard/language-independence-and-language-independent-components.md)  
 [<span data-ttu-id="95387-122">Gacutil.exe (nástroj globální mezipaměti sestavení)</span><span class="sxs-lookup"><span data-stu-id="95387-122">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
