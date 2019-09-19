---
title: 'Postupy: Načtení sestavení do domény aplikace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, loading assemblies
- loading assemblies
ms.assetid: 1432aa2d-bd83-4346-bf3b-a1b7920e2aa9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86b66d0a88864188d67aab19de67aaa857a06eaa
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053167"
---
# <a name="how-to-load-assemblies-into-an-application-domain"></a><span data-ttu-id="732c2-102">Postupy: Načtení sestavení do domény aplikace</span><span class="sxs-lookup"><span data-stu-id="732c2-102">How to: Load Assemblies into an Application Domain</span></span>
<span data-ttu-id="732c2-103">Existuje několik způsobů, jak načíst sestavení do domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="732c2-103">There are several ways to load an assembly into an application domain.</span></span> <span data-ttu-id="732c2-104">Doporučeným `static` způsobem je použít metodu (`Shared` v <xref:System.Reflection.Assembly?displayProperty=nameWithType> Visual Basic) <xref:System.Reflection.Assembly.Load%2A> třídy.</span><span class="sxs-lookup"><span data-stu-id="732c2-104">The recommended way is to use the `static` (`Shared` in Visual Basic) <xref:System.Reflection.Assembly.Load%2A> method of the <xref:System.Reflection.Assembly?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="732c2-105">Další způsoby, jak lze načíst sestavení, zahrnují:</span><span class="sxs-lookup"><span data-stu-id="732c2-105">Other ways assemblies can be loaded include:</span></span>  
  
- <span data-ttu-id="732c2-106"><xref:System.Reflection.Assembly.LoadFrom%2A> Metoda<xref:System.Reflection.Assembly> třídy načte sestavení příslušné umístění souboru.</span><span class="sxs-lookup"><span data-stu-id="732c2-106">The <xref:System.Reflection.Assembly.LoadFrom%2A> method of the <xref:System.Reflection.Assembly> class loads an assembly given its file location.</span></span> <span data-ttu-id="732c2-107">Načítání sestavení s touto metodou používá jiný kontext zatížení.</span><span class="sxs-lookup"><span data-stu-id="732c2-107">Loading assemblies with this method uses a different load context.</span></span>  
  
- <span data-ttu-id="732c2-108">Metody <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> a<xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> načtou sestavení do kontextu pouze pro reflexi.</span><span class="sxs-lookup"><span data-stu-id="732c2-108">The <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> and <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> methods load an assembly into the reflection-only context.</span></span> <span data-ttu-id="732c2-109">Sestavení, která jsou načtena do tohoto kontextu, lze prozkoumat, ale nejsou provedena, a umožnit tak zkoumání sestavení, která cílí na jiné platformy.</span><span class="sxs-lookup"><span data-stu-id="732c2-109">Assemblies loaded into this context can be examined but not executed, allowing the examination of assemblies that target other platforms.</span></span> <span data-ttu-id="732c2-110">Viz [jak: Načíst sestavení do kontextu](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)pouze pro reflexi.</span><span class="sxs-lookup"><span data-stu-id="732c2-110">See [How to: Load Assemblies into the Reflection-Only Context](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="732c2-111">Kontext pouze pro reflexi je v .NET Framework verze 2,0 nový.</span><span class="sxs-lookup"><span data-stu-id="732c2-111">The reflection-only context is new in the .NET Framework version 2.0.</span></span>  
  
- <span data-ttu-id="732c2-112"><xref:System.AppDomain.CreateInstanceAndUnwrap%2A> Metody jako <xref:System.AppDomain.CreateInstance%2A> a<xref:System.AppDomain> třídy mohou načítat sestavení do domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="732c2-112">Methods such as <xref:System.AppDomain.CreateInstance%2A> and <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> of the <xref:System.AppDomain> class can load assemblies into an application domain.</span></span>  
  
- <span data-ttu-id="732c2-113"><xref:System.Type.GetType%2A> Metoda<xref:System.Type> třídy může načíst sestavení.</span><span class="sxs-lookup"><span data-stu-id="732c2-113">The <xref:System.Type.GetType%2A> method of the <xref:System.Type> class can load assemblies.</span></span>  
  
- <span data-ttu-id="732c2-114"><xref:System.AppDomain.Load%2A> Metoda<xref:System.AppDomain?displayProperty=nameWithType> třídy může načíst sestavení, ale používá se hlavně pro interoperabilitu modelu COM.</span><span class="sxs-lookup"><span data-stu-id="732c2-114">The <xref:System.AppDomain.Load%2A> method of the <xref:System.AppDomain?displayProperty=nameWithType> class can load assemblies, but is primarily used for COM interoperability.</span></span> <span data-ttu-id="732c2-115">Neměl by být použit pro načtení sestavení do domény aplikace jiné než domény aplikace, ze které je volána.</span><span class="sxs-lookup"><span data-stu-id="732c2-115">It should not be used to load assemblies into an application domain other than the application domain from which it is called.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="732c2-116">Počínaje verzí 2,0 .NET Framework modul runtime nenačte sestavení, které bylo zkompilováno s verzí .NET Framework, která má vyšší číslo verze než aktuálně načtený modul runtime.</span><span class="sxs-lookup"><span data-stu-id="732c2-116">Starting with the .NET Framework version 2.0, the runtime will not load an assembly that was compiled with a version of the .NET Framework that has a higher version number than the currently loaded runtime.</span></span> <span data-ttu-id="732c2-117">To platí pro kombinaci hlavních a vedlejších součástí čísla verze.</span><span class="sxs-lookup"><span data-stu-id="732c2-117">This applies to the combination of the major and minor components of the version number.</span></span>  
  
 <span data-ttu-id="732c2-118">Můžete určit způsob, jakým je zkompilovaný kód JIT (just-in-time) z načtených sestavení sdílen mezi doménami aplikace.</span><span class="sxs-lookup"><span data-stu-id="732c2-118">You can specify the way the just-in-time (JIT) compiled code from loaded assemblies is shared between application domains.</span></span> <span data-ttu-id="732c2-119">Další informace naleznete v tématu [aplikační domény a sestavení](application-domains.md#application-domains-and-assemblies).</span><span class="sxs-lookup"><span data-stu-id="732c2-119">For more information, see [Application domains and assemblies](application-domains.md#application-domains-and-assemblies).</span></span>  
  
## <a name="example"></a><span data-ttu-id="732c2-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="732c2-120">Example</span></span>  
 <span data-ttu-id="732c2-121">Následující kód načte sestavení s názvem "example. exe" nebo "example. dll" do aktuální domény aplikace, získá typ pojmenovaný `Example` ze sestavení, získá metodu bez parametrů pojmenovanou `MethodA` pro daný typ a spustí metodu.</span><span class="sxs-lookup"><span data-stu-id="732c2-121">The following code loads an assembly named "example.exe" or "example.dll" into the current application domain, gets a type named `Example` from the assembly, gets a parameterless method named `MethodA` for that type, and executes the method.</span></span> <span data-ttu-id="732c2-122">Kompletní diskuzi o získání informací z načteného sestavení naleznete v tématu [Dynamické načítání a používání typů](../reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="732c2-122">For a complete discussion on obtaining information from a loaded assembly, see [Dynamically Loading and Using Types](../reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
 [!code-cpp[System.AppDomain.Load#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source2.cpp#2)]
 [!code-csharp[System.AppDomain.Load#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source2.cs#2)]
 [!code-vb[System.AppDomain.Load#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="732c2-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="732c2-123">See also</span></span>

- <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>
- [<span data-ttu-id="732c2-124">Programování s aplikačními doménami</span><span class="sxs-lookup"><span data-stu-id="732c2-124">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="732c2-125">Reflexe</span><span class="sxs-lookup"><span data-stu-id="732c2-125">Reflection</span></span>](../reflection-and-codedom/reflection.md)
- [<span data-ttu-id="732c2-126">Používání domén aplikací</span><span class="sxs-lookup"><span data-stu-id="732c2-126">Using Application Domains</span></span>](use.md)
- [<span data-ttu-id="732c2-127">Postupy: Načíst sestavení do kontextu pouze pro reflexi</span><span class="sxs-lookup"><span data-stu-id="732c2-127">How to: Load Assemblies into the Reflection-Only Context</span></span>](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)
- [<span data-ttu-id="732c2-128">Aplikační domény a sestavení</span><span class="sxs-lookup"><span data-stu-id="732c2-128">Application domains and assemblies</span></span>](application-domains.md#application-domains-and-assemblies)
