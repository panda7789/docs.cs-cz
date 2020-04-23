---
title: Vystavení komponent COM pro rozhraní .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- exposing COM components to .NET Framework
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: e78b14f1-e487-43cd-9c6d-1a07483f1730
ms.openlocfilehash: 914f72b5e4840555541943620ca2df1f629b0604
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123529"
---
# <a name="exposing-com-components-to-the-net-framework"></a><span data-ttu-id="b8e29-102">Vystavení komponent COM pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b8e29-102">Exposing COM Components to the .NET Framework</span></span>
<span data-ttu-id="b8e29-103">Tato část shrnuje proces potřebný k vystavení existující součásti modelu COM pro spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="b8e29-103">This section summarizes the process needed to expose an existing COM component to managed code.</span></span> <span data-ttu-id="b8e29-104">Podrobnosti o vytváření serverů COM, které úzce integrují s .NET Framework, najdete v tématu věnovaném [hlediskům návrhu pro spoluprovozování](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="b8e29-104">For details about writing COM servers that tightly integrate with the .NET Framework, see [Design Considerations for Interoperation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100)).</span></span>
  
 <span data-ttu-id="b8e29-105">Existující komponenty modelu COM jsou cenné prostředky ve spravovaném kódu jako obchodní aplikace střední vrstvy nebo jako izolované funkce.</span><span class="sxs-lookup"><span data-stu-id="b8e29-105">Existing COM components are valuable resources in managed code as middle-tier business applications or as isolated functionality.</span></span> <span data-ttu-id="b8e29-106">Ideální komponenta má primární spolupracující sestavení a je v souladu s požadavky na programování, které jsou uloženy v modelu COM.</span><span class="sxs-lookup"><span data-stu-id="b8e29-106">An ideal component has a primary interop assembly and conforms tightly to the programming standards imposed by COM.</span></span>  
  
#### <a name="to-expose-com-components-to-the-net-framework"></a><span data-ttu-id="b8e29-107">Vystavení komponent modelu COM pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b8e29-107">To expose COM components to the .NET Framework</span></span>  
  
1. <span data-ttu-id="b8e29-108">[Importujte knihovnu typů jako sestavení](importing-a-type-library-as-an-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="b8e29-108">[Import a type library as an assembly](importing-a-type-library-as-an-assembly.md).</span></span>  
  
     <span data-ttu-id="b8e29-109">Modul CLR (Common Language Runtime) vyžaduje metadata pro všechny typy, včetně typů COM.</span><span class="sxs-lookup"><span data-stu-id="b8e29-109">The common language runtime requires metadata for all types, including COM types.</span></span> <span data-ttu-id="b8e29-110">Existuje několik způsobů, jak získat sestavení obsahující typy COM importované jako metadata.</span><span class="sxs-lookup"><span data-stu-id="b8e29-110">There are several ways to obtain an assembly containing COM types imported as metadata.</span></span>  
  
2. <span data-ttu-id="b8e29-111">[Použijte typy com ve spravovaném kódu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="b8e29-111">[Use COM types in managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span></span>  
  
     <span data-ttu-id="b8e29-112">Můžete zkontrolovat typy modelu COM, aktivovat instance a vyvolat metody objektu COM stejným způsobem jako u libovolného spravovaného typu.</span><span class="sxs-lookup"><span data-stu-id="b8e29-112">You can inspect COM types, activate instances, and invoke methods on the COM object the same way you do for any managed type.</span></span>  
  
3. <span data-ttu-id="b8e29-113">[Zkompilujte projekt interoperability](compiling-an-interop-project.md).</span><span class="sxs-lookup"><span data-stu-id="b8e29-113">[Compile an interop project](compiling-an-interop-project.md).</span></span>  
  
     <span data-ttu-id="b8e29-114">Windows SDK poskytuje kompilátory pro několik jazyků kompatibilních se specifikací CLS (Common Language Specification), včetně Visual Basic, C# a C++.</span><span class="sxs-lookup"><span data-stu-id="b8e29-114">The Windows SDK provides compilers for several languages compliant with the Common Language Specification (CLS), including Visual Basic, C#, and C++.</span></span>  
  
4. <span data-ttu-id="b8e29-115">[Nasazení aplikace spolupráce](deploying-an-interop-application.md)</span><span class="sxs-lookup"><span data-stu-id="b8e29-115">[Deploy an interop application](deploying-an-interop-application.md).</span></span>  
  
     <span data-ttu-id="b8e29-116">Aplikace Interop jsou nejlépe nasazeny jako podepsaná sestavení v globální mezipaměti sestavení ( [silně pojmenovaná](../../standard/assembly/strong-named.md)).</span><span class="sxs-lookup"><span data-stu-id="b8e29-116">Interop applications are best deployed as [strong-named](../../standard/assembly/strong-named.md), signed assemblies in the global assembly cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8e29-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="b8e29-117">See also</span></span>

- [<span data-ttu-id="b8e29-118">Spolupráce s nespravovaným kódem</span><span class="sxs-lookup"><span data-stu-id="b8e29-118">Interoperating with Unmanaged Code</span></span>](index.md)
- <span data-ttu-id="b8e29-119">[Faktory návrhu pro spoluprovozování](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b8e29-119">[Design Considerations for Interoperation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))</span></span>
- [<span data-ttu-id="b8e29-120">Ukázka zprostředkovatele s objekty COM: klient .NET a server COM</span><span class="sxs-lookup"><span data-stu-id="b8e29-120">COM Interop Sample: .NET Client and COM Server</span></span>](com-interop-sample-net-client-and-com-server.md)
- [<span data-ttu-id="b8e29-121">Jazyková nezávislost a jazykově nezávislé komponenty</span><span class="sxs-lookup"><span data-stu-id="b8e29-121">Language Independence and Language-Independent Components</span></span>](../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="b8e29-122">Gacutil. exe (nástroj Global Assembly Cache Tool)</span><span class="sxs-lookup"><span data-stu-id="b8e29-122">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
