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
ms.openlocfilehash: 2b7aa028afeaf4230ee079f0d4071a5cd6a21c65
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59320909"
---
# <a name="exposing-com-components-to-the-net-framework"></a><span data-ttu-id="cee56-102">Vystavení komponent COM pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="cee56-102">Exposing COM Components to the .NET Framework</span></span>
<span data-ttu-id="cee56-103">Tento oddíl shrnuje procesu nutné vystavit existující komponenty modelu COM pro spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="cee56-103">This section summarizes the process needed to expose an existing COM component to managed code.</span></span> <span data-ttu-id="cee56-104">Podrobnosti o vytváření serverů modelu COM, který úzce integrace s rozhraním .NET Framework, naleznete v tématu [aspekty návrhu pro spolupráci](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="cee56-104">For details about writing COM servers that tightly integrate with the .NET Framework, see [Design Considerations for Interoperation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100)).</span></span>
  
 <span data-ttu-id="cee56-105">Střední vrstvy obchodní aplikace nebo jako izolované funkce stávající komponentami modelu COM jsou cenné prostředky ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="cee56-105">Existing COM components are valuable resources in managed code as middle-tier business applications or as isolated functionality.</span></span> <span data-ttu-id="cee56-106">Ideální komponenta má primární sestavení zprostředkovatele komunikace a úzce odpovídá programovacím standardy stanovené modelu COM.</span><span class="sxs-lookup"><span data-stu-id="cee56-106">An ideal component has a primary interop assembly and conforms tightly to the programming standards imposed by COM.</span></span>  
  
#### <a name="to-expose-com-components-to-the-net-framework"></a><span data-ttu-id="cee56-107">Vystavení komponent COM pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="cee56-107">To expose COM components to the .NET Framework</span></span>  
  
1. <span data-ttu-id="cee56-108">[Import knihovny typů jako sestavení,](importing-a-type-library-as-an-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="cee56-108">[Import a type library as an assembly](importing-a-type-library-as-an-assembly.md).</span></span>  
  
     <span data-ttu-id="cee56-109">Modul common language runtime požaduje metadata pro všechny typy, včetně typů modelu COM.</span><span class="sxs-lookup"><span data-stu-id="cee56-109">The common language runtime requires metadata for all types, including COM types.</span></span> <span data-ttu-id="cee56-110">Existuje několik způsobů, jak získat sestavení obsahující typy modelu COM importovat jako metadata.</span><span class="sxs-lookup"><span data-stu-id="cee56-110">There are several ways to obtain an assembly containing COM types imported as metadata.</span></span>  
  
2. <span data-ttu-id="cee56-111">[Použijte typy modelu COM ve spravovaném kódu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="cee56-111">[Use COM types in managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span></span>  
  
     <span data-ttu-id="cee56-112">Můžete kontrolovat typy modelu COM, aktivovat instance a volat metody u objektu COM stejným způsobem jako u jakékoli spravovaného typu.</span><span class="sxs-lookup"><span data-stu-id="cee56-112">You can inspect COM types, activate instances, and invoke methods on the COM object the same way you do for any managed type.</span></span>  
  
3. <span data-ttu-id="cee56-113">[Kompilace projektu interoperability](compiling-an-interop-project.md).</span><span class="sxs-lookup"><span data-stu-id="cee56-113">[Compile an interop project](compiling-an-interop-project.md).</span></span>  
  
     <span data-ttu-id="cee56-114">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Obsahuje kompilátory pro několik jazyků kompatibilních s specifikace CLS (Common Language), včetně [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C#a C++.</span><span class="sxs-lookup"><span data-stu-id="cee56-114">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] provides compilers for several languages compliant with the Common Language Specification (CLS), including [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C#, and C++.</span></span>  
  
4. <span data-ttu-id="cee56-115">[Nasazení aplikace spolupráce](deploying-an-interop-application.md).</span><span class="sxs-lookup"><span data-stu-id="cee56-115">[Deploy an interop application](deploying-an-interop-application.md).</span></span>  
  
     <span data-ttu-id="cee56-116">Spolupráce – aplikace se nejlépe nasadit jako [silným názvem](../app-domains/strong-named-assemblies.md), podepsaná sestavení v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="cee56-116">Interop applications are best deployed as [strong-named](../app-domains/strong-named-assemblies.md), signed assemblies in the global assembly cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cee56-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cee56-117">See also</span></span>

- [<span data-ttu-id="cee56-118">Spolupráce s nespravovaným kódem</span><span class="sxs-lookup"><span data-stu-id="cee56-118">Interoperating with Unmanaged Code</span></span>](index.md)
- [<span data-ttu-id="cee56-119">Aspekty návrhu pro spolupráci</span><span class="sxs-lookup"><span data-stu-id="cee56-119">Design Considerations for Interoperation</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))
- [<span data-ttu-id="cee56-120">Ukázka zprostředkovatele s objekty COM: klient .NET a server COM</span><span class="sxs-lookup"><span data-stu-id="cee56-120">COM Interop Sample: .NET Client and COM Server</span></span>](com-interop-sample-net-client-and-com-server.md)
- [<span data-ttu-id="cee56-121">Jazyková nezávislost a jazykově nezávislé komponenty</span><span class="sxs-lookup"><span data-stu-id="cee56-121">Language Independence and Language-Independent Components</span></span>](../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="cee56-122">Gacutil.exe (nástroj globální mezipaměti sestavení)</span><span class="sxs-lookup"><span data-stu-id="cee56-122">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
