---
title: Kompilace projektu interoperability
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
helpviewer_keywords:
- interoperation with unmanaged code, compiling
- COM interop, compiling
- exposing COM components to .NET Framework
- compiling interop projects
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: 6fcf6588-5e25-41af-b4ae-780974f2c3df
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f64300e2f00eea788fcea9bd607af815cbea611d
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
---
# <a name="compiling-an-interop-project"></a><span data-ttu-id="a4aba-102">Kompilace projektu interoperability</span><span class="sxs-lookup"><span data-stu-id="a4aba-102">Compiling an Interop Project</span></span>
<span data-ttu-id="a4aba-103">Projektů spolupráce COM, které odkazují na jeden nebo více sestavení obsahující importované typy modelu COM kompilovány jako ostatní spravovaný projekt.</span><span class="sxs-lookup"><span data-stu-id="a4aba-103">COM interop projects that reference one or more assemblies containing imported COM types are compiled like any other managed project.</span></span> <span data-ttu-id="a4aba-104">Sestavení spolupráce ve vývojovém prostředí, jako je například Visual Studio, můžete odkazovat, nebo můžete použít, je při použití příkazového řádku kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="a4aba-104">You can reference interop assemblies in a development environment such as Visual Studio, or you can reference them when you use a command-line compiler.</span></span> <span data-ttu-id="a4aba-105">V obou případech správně, kompilace sestavení vzájemné spolupráce musí být ve stejném adresáři jako ostatní soubory projektu.</span><span class="sxs-lookup"><span data-stu-id="a4aba-105">In either case, to compile properly, the interop assembly must be in the same directory as the other project files.</span></span>  
  
 <span data-ttu-id="a4aba-106">Chcete-li sestavení vzájemné spolupráce dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="a4aba-106">There are two ways to reference interop assemblies:</span></span>  
  
-   <span data-ttu-id="a4aba-107">Vložené typy spolupráce: od verze [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] a [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)], můžete určit, aby kompilátoru pro vložení informací o typu ze sestavení spolupráce do spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="a4aba-107">Embedded interop types: Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] and [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)], you can instruct the compiler to embed type information from an interop assembly into your executable.</span></span> <span data-ttu-id="a4aba-108">Toto je doporučený postup.</span><span class="sxs-lookup"><span data-stu-id="a4aba-108">This is the recommended technique.</span></span>  
  
-   <span data-ttu-id="a4aba-109">Nasazení sestavení vzájemné spolupráce: můžete vytvořit standardní odkaz na sestavení spolupráce.</span><span class="sxs-lookup"><span data-stu-id="a4aba-109">Deploying interop assemblies: You can create a standard reference to an interop assembly.</span></span> <span data-ttu-id="a4aba-110">V takovém případě musí být nasazený sestavení vzájemné spolupráce s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="a4aba-110">In this case, the interop assembly must be deployed with your application.</span></span>  
  
 <span data-ttu-id="a4aba-111">Rozdíly mezi tyto dva postupy jsou popsány podrobněji na [pomocí typy modelu COM v spravovaného kódu](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a4aba-111">The differences between these two techniques are discussed in greater detail in [Using COM Types in Managed Code](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100)).</span></span>  
  
 <span data-ttu-id="a4aba-112">Vložení typů spolupráce pomocí sady Visual Studio je znázorněn v [návod: vložení informací o typu ze sestavení sady Microsoft Office](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100)) a [návod: vložení typů ze spravovaných sestavení](https://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).</span><span class="sxs-lookup"><span data-stu-id="a4aba-112">Embedding interop types with Visual Studio is demonstrated in [Walkthrough: Embedding Type Information from Microsoft Office Assemblies](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100)) and [Walkthrough: Embedding Types from Managed Assemblies](https://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).</span></span>  
  
 <span data-ttu-id="a4aba-113">Odkazování na sestavení spolupráce s kompilátoru příkazového řádku a vložení informací o typu do vaší spustitelné soubory, použijte [/Link (možnosti kompilátoru C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md) nebo [/Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) přepínače kompilátoru a Zadejte název sestavení vzájemné spolupráce.</span><span class="sxs-lookup"><span data-stu-id="a4aba-113">To reference an interop assembly with a command-line compiler and embed type information in your executables, use the [/link (C# Compiler Options)](../../csharp/language-reference/compiler-options/link-compiler-option.md) or the [/link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) compiler switch and specify the name of the interop assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a4aba-114">Visual C++ aplikace nelze vložit informace o typu, ale můžou spolupracovat s aplikacemi nebo doplňky, které provádějí.</span><span class="sxs-lookup"><span data-stu-id="a4aba-114">Visual C++ applications cannot embed type information, but they can interoperate with applications or add-ins that do.</span></span>  
  
 <span data-ttu-id="a4aba-115">Kompilace aplikace, která zahrnuje primárních sestavení vzájemné spolupráce při nasazení, použijte **/reference** přepínače kompilátoru a zadejte název sestavení vzájemné spolupráce.</span><span class="sxs-lookup"><span data-stu-id="a4aba-115">To compile an application that includes a primary interop assembly when it is deployed, use the **/reference** compiler switch and specify the name of the interop assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4aba-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="a4aba-116">See Also</span></span>  
 [<span data-ttu-id="a4aba-117">Vystavení komponent COM pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a4aba-117">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)  
 [<span data-ttu-id="a4aba-118">Jazyková nezávislost a jazykově nezávislé komponenty</span><span class="sxs-lookup"><span data-stu-id="a4aba-118">Language Independence and Language-Independent Components</span></span>](../../standard/language-independence-and-language-independent-components.md)  
 <span data-ttu-id="a4aba-119">[Použití typy modelu COM ve spravovaném kódu](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a4aba-119">[Using COM Types in Managed Code](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100))</span></span>  
 <span data-ttu-id="a4aba-120">[Návod: Vložení informací o typu ze sestavení Microsoft Office](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a4aba-120">[Walkthrough: Embedding Type Information from Microsoft Office Assemblies](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100))</span></span>  
 [<span data-ttu-id="a4aba-121">Návod: Vložení typů ze spravovaných sestavení</span><span class="sxs-lookup"><span data-stu-id="a4aba-121">Walkthrough: Embedding Types from Managed Assemblies</span></span>](https://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)  
 [<span data-ttu-id="a4aba-122">Import knihovny typů ve formě sestavení</span><span class="sxs-lookup"><span data-stu-id="a4aba-122">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
