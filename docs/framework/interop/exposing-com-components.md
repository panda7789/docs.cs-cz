---
title: Vystavení komponent COM pro rozhraní .NET Framework
description: Zjistěte, jaký je proces vystavování komponent modelu COM v rozhraní .NET. Komponenty modelu COM jsou cenné ve spravovaném kódu jako obchodní aplikace střední vrstvy nebo izolované funkce.
ms.date: 03/30/2017
helpviewer_keywords:
- exposing COM components to .NET Framework
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: e78b14f1-e487-43cd-9c6d-1a07483f1730
ms.openlocfilehash: 459ba7ffed2e4f6c458f89a63b2baa37180d270d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620843"
---
# <a name="exposing-com-components-to-the-net-framework"></a><span data-ttu-id="7cc2a-104">Vystavení komponent COM pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7cc2a-104">Exposing COM Components to the .NET Framework</span></span>
<span data-ttu-id="7cc2a-105">Tato část shrnuje proces potřebný k vystavení existující součásti modelu COM pro spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="7cc2a-105">This section summarizes the process needed to expose an existing COM component to managed code.</span></span> <span data-ttu-id="7cc2a-106">Podrobnosti o vytváření serverů COM, které úzce integrují s .NET Framework, najdete v tématu věnovaném [hlediskům návrhu pro spoluprovozování](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="7cc2a-106">For details about writing COM servers that tightly integrate with the .NET Framework, see [Design Considerations for Interoperation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100)).</span></span>
  
 <span data-ttu-id="7cc2a-107">Existující komponenty modelu COM jsou cenné prostředky ve spravovaném kódu jako obchodní aplikace střední vrstvy nebo jako izolované funkce.</span><span class="sxs-lookup"><span data-stu-id="7cc2a-107">Existing COM components are valuable resources in managed code as middle-tier business applications or as isolated functionality.</span></span> <span data-ttu-id="7cc2a-108">Ideální komponenta má primární spolupracující sestavení a je v souladu s požadavky na programování, které jsou uloženy v modelu COM.</span><span class="sxs-lookup"><span data-stu-id="7cc2a-108">An ideal component has a primary interop assembly and conforms tightly to the programming standards imposed by COM.</span></span>  
  
#### <a name="to-expose-com-components-to-the-net-framework"></a><span data-ttu-id="7cc2a-109">Vystavení komponent modelu COM pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7cc2a-109">To expose COM components to the .NET Framework</span></span>  
  
1. <span data-ttu-id="7cc2a-110">[Importujte knihovnu typů jako sestavení](importing-a-type-library-as-an-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="7cc2a-110">[Import a type library as an assembly](importing-a-type-library-as-an-assembly.md).</span></span>  
  
     <span data-ttu-id="7cc2a-111">Modul CLR (Common Language Runtime) vyžaduje metadata pro všechny typy, včetně typů COM.</span><span class="sxs-lookup"><span data-stu-id="7cc2a-111">The common language runtime requires metadata for all types, including COM types.</span></span> <span data-ttu-id="7cc2a-112">Existuje několik způsobů, jak získat sestavení obsahující typy COM importované jako metadata.</span><span class="sxs-lookup"><span data-stu-id="7cc2a-112">There are several ways to obtain an assembly containing COM types imported as metadata.</span></span>  
  
2. <span data-ttu-id="7cc2a-113">[Použijte typy com ve spravovaném kódu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="7cc2a-113">[Use COM types in managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span></span>  
  
     <span data-ttu-id="7cc2a-114">Můžete zkontrolovat typy modelu COM, aktivovat instance a vyvolat metody objektu COM stejným způsobem jako u libovolného spravovaného typu.</span><span class="sxs-lookup"><span data-stu-id="7cc2a-114">You can inspect COM types, activate instances, and invoke methods on the COM object the same way you do for any managed type.</span></span>  
  
3. <span data-ttu-id="7cc2a-115">[Zkompilujte projekt interoperability](compiling-an-interop-project.md).</span><span class="sxs-lookup"><span data-stu-id="7cc2a-115">[Compile an interop project](compiling-an-interop-project.md).</span></span>  
  
     <span data-ttu-id="7cc2a-116">Windows SDK poskytuje kompilátory pro několik jazyků kompatibilních se specifikací CLS (Common Language Specification), včetně Visual Basic, C# a C++.</span><span class="sxs-lookup"><span data-stu-id="7cc2a-116">The Windows SDK provides compilers for several languages compliant with the Common Language Specification (CLS), including Visual Basic, C#, and C++.</span></span>  
  
4. <span data-ttu-id="7cc2a-117">[Nasazení aplikace spolupráce](deploying-an-interop-application.md)</span><span class="sxs-lookup"><span data-stu-id="7cc2a-117">[Deploy an interop application](deploying-an-interop-application.md).</span></span>  
  
     <span data-ttu-id="7cc2a-118">Aplikace Interop jsou nejlépe nasazeny jako podepsaná sestavení v globální mezipaměti sestavení ( [silně pojmenovaná](../../standard/assembly/strong-named.md)).</span><span class="sxs-lookup"><span data-stu-id="7cc2a-118">Interop applications are best deployed as [strong-named](../../standard/assembly/strong-named.md), signed assemblies in the global assembly cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cc2a-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7cc2a-119">See also</span></span>

- [<span data-ttu-id="7cc2a-120">Spolupráce s nespravovaným kódem</span><span class="sxs-lookup"><span data-stu-id="7cc2a-120">Interoperating with Unmanaged Code</span></span>](index.md)
- <span data-ttu-id="7cc2a-121">[Faktory návrhu pro spoluprovozování](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7cc2a-121">[Design Considerations for Interoperation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))</span></span>
- [<span data-ttu-id="7cc2a-122">Ukázka zprostředkovatele s objekty COM: klient .NET a server COM</span><span class="sxs-lookup"><span data-stu-id="7cc2a-122">COM Interop Sample: .NET Client and COM Server</span></span>](com-interop-sample-net-client-and-com-server.md)
- [<span data-ttu-id="7cc2a-123">Jazyková nezávislost a jazykově nezávislé komponenty</span><span class="sxs-lookup"><span data-stu-id="7cc2a-123">Language Independence and Language-Independent Components</span></span>](../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="7cc2a-124">Gacutil.exe (nástroj Global Assembly Cache Tool)</span><span class="sxs-lookup"><span data-stu-id="7cc2a-124">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
