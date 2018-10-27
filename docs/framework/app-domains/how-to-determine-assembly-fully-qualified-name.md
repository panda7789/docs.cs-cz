---
title: 'Postupy: určení sestavení&#39;s plně kvalifikovaný název'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 009dae23-e1f6-4a64-9a9a-32e4c34802b0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bb5978859ba25e1595ac3da7a2d7dad8cc2cad85
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50041099"
---
# <a name="how-to-determine-an-assembly39s-fully-qualified-name"></a><span data-ttu-id="52ea9-102">Postupy: určení sestavení&#39;s plně kvalifikovaný název</span><span class="sxs-lookup"><span data-stu-id="52ea9-102">How to: Determine an Assembly&#39;s Fully Qualified Name</span></span>
<span data-ttu-id="52ea9-103">Chcete-li zjistit plně kvalifikovaný název sestavení v globální mezipaměti sestavení, použijte Global Assembly Cache Tool ([Gacutil.exe](../../../docs/framework/tools/gacutil-exe-gac-tool.md)).</span><span class="sxs-lookup"><span data-stu-id="52ea9-103">To discover the fully qualified name of an assembly in the global assembly cache, use the Global Assembly Cache Tool ([Gacutil.exe](../../../docs/framework/tools/gacutil-exe-gac-tool.md)).</span></span> <span data-ttu-id="52ea9-104">Zobrazit [postupy: zobrazení obsahu globální mezipaměti sestavení](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="52ea9-104">See [How to: View the Contents of the Global Assembly Cache](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md).</span></span>  
  
 <span data-ttu-id="52ea9-105">Pro sestavení, které nejsou v globální mezipaměti sestavení, je možné získat plně kvalifikovaný název v několika způsoby: kód můžete použít k výstupu informací do konzoly nebo do proměnné, nebo můžete použít [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)pro přezkoumání metadat sestavení, který obsahuje plně kvalifikovaný název.</span><span class="sxs-lookup"><span data-stu-id="52ea9-105">For assemblies that are not in the global assembly cache, you can get the fully qualified assembly name in a number of ways: can use code to output the information to the console or to a variable, or you can use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's metadata, which contains the fully qualified name.</span></span>  
  
-   <span data-ttu-id="52ea9-106">Pokud už je sestavení zavedeno aplikací, můžete načíst hodnotu <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> vlastnost získat plně kvalifikovaný název.</span><span class="sxs-lookup"><span data-stu-id="52ea9-106">If the assembly is already loaded by the application, you can retrieve the value of the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property to get the fully qualified name.</span></span> <span data-ttu-id="52ea9-107">Tento přístup můžete použít, zda je sestavení v mezipaměti GAC.</span><span class="sxs-lookup"><span data-stu-id="52ea9-107">You can use this approach whether or not the assembly is in the GAC.</span></span> <span data-ttu-id="52ea9-108">Příklad uvádí ukázku.</span><span class="sxs-lookup"><span data-stu-id="52ea9-108">The example provides an illustration.</span></span>  
  
-   <span data-ttu-id="52ea9-109">Pokud znáte cesta systému souborů sestavení, můžete volat statickou (`Shared` v jazyce Visual Basic) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> metodu k získání plně kvalifikovaný název.</span><span class="sxs-lookup"><span data-stu-id="52ea9-109">If you know the assembly's file system path, you can call the static (`Shared` in Visual Basic) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> method to get the fully qualified assembly name.</span></span> <span data-ttu-id="52ea9-110">Níže je jednoduchý příklad.</span><span class="sxs-lookup"><span data-stu-id="52ea9-110">The following is a simple example.</span></span>  
  
     [!code-csharp[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/cs/getassemblyname1.cs#1)]
     [!code-vb[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/vb/getassemblyname1.vb#1)]  
  
-   <span data-ttu-id="52ea9-111">Můžete použít [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) pro přezkoumání metadat sestavení, který obsahuje plně kvalifikovaný název.</span><span class="sxs-lookup"><span data-stu-id="52ea9-111">You can use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's metadata, which contains the fully qualified name.</span></span>  
  
 <span data-ttu-id="52ea9-112">Další informace o nastavení atributů sestavení, jako je verze, jazykovou verzi a název sestavení najdete v tématu [nastavení atributů sestavení](../../../docs/framework/app-domains/set-assembly-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="52ea9-112">For more information about setting assembly attributes such as version, culture, and assembly name, see [Setting Assembly Attributes](../../../docs/framework/app-domains/set-assembly-attributes.md).</span></span> <span data-ttu-id="52ea9-113">Další informace o přiřazení sestavení silným názvem naleznete v tématu [vytvoření a použití sestavení](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="52ea9-113">For more information about giving an assembly a strong name, see [Creating and Using Strong-Named Assemblies](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="52ea9-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="52ea9-114">Example</span></span>  
 <span data-ttu-id="52ea9-115">Následující příklad kódu ukazuje, jak zobrazit plně kvalifikovaný název sestavení obsahující dané třídy do konzoly.</span><span class="sxs-lookup"><span data-stu-id="52ea9-115">The following code example shows how to display the fully qualified name of an assembly containing a specified class to the console.</span></span> <span data-ttu-id="52ea9-116">Protože načte název sestavení, které aplikace byl již načten, není důležité, zda je sestavení v mezipaměti GAC.</span><span class="sxs-lookup"><span data-stu-id="52ea9-116">Because it retrieves the name of an assembly that the app has already loaded, it does not matter whether the assembly is in the GAC.</span></span>  
  
 [!code-cpp[Assembly.Fullname#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.FullName/CPP/example2.cpp#2)]
 [!code-csharp[Assembly.Fullname#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.FullName/CS/example2.cs#2)]
 [!code-vb[Assembly.Fullname#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.FullName/VB/example2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="52ea9-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="52ea9-117">See Also</span></span>  
- [<span data-ttu-id="52ea9-118">Názvy sestavení</span><span class="sxs-lookup"><span data-stu-id="52ea9-118">Assembly Names</span></span>](../../../docs/framework/app-domains/assembly-names.md)  
- [<span data-ttu-id="52ea9-119">Vytváření sestavení</span><span class="sxs-lookup"><span data-stu-id="52ea9-119">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
- [<span data-ttu-id="52ea9-120">Vytváření a používání sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="52ea9-120">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
- [<span data-ttu-id="52ea9-121">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="52ea9-121">Global Assembly Cache</span></span>](../../../docs/framework/app-domains/gac.md)  
- [<span data-ttu-id="52ea9-122">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="52ea9-122">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
- [<span data-ttu-id="52ea9-123">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="52ea9-123">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
