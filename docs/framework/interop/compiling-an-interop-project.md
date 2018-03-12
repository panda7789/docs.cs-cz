---
title: Kompilace projektu interoperability
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interoperation with unmanaged code, compiling
- COM interop, compiling
- exposing COM components to .NET Framework
- compiling interop projects
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: 6fcf6588-5e25-41af-b4ae-780974f2c3df
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8115df3159b715fbd01a15621c391cbe35612dfe
ms.sourcegitcommit: d95a91d685565f4d95c8773b558752864a6a3d7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2018
---
# <a name="compiling-an-interop-project"></a><span data-ttu-id="3f70f-102">Kompilace projektu interoperability</span><span class="sxs-lookup"><span data-stu-id="3f70f-102">Compiling an Interop Project</span></span>
<span data-ttu-id="3f70f-103">Projektů spolupráce COM, které odkazují na jeden nebo více sestavení obsahující importované typy modelu COM kompilovány jako ostatní spravovaný projekt.</span><span class="sxs-lookup"><span data-stu-id="3f70f-103">COM interop projects that reference one or more assemblies containing imported COM types are compiled like any other managed project.</span></span> <span data-ttu-id="3f70f-104">Sestavení spolupráce ve vývojovém prostředí, jako je například Visual Studio, můžete odkazovat, nebo můžete použít, je při použití příkazového řádku kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="3f70f-104">You can reference interop assemblies in a development environment such as Visual Studio, or you can reference them when you use a command-line compiler.</span></span> <span data-ttu-id="3f70f-105">V obou případech správně, kompilace sestavení vzájemné spolupráce musí být ve stejném adresáři jako ostatní soubory projektu.</span><span class="sxs-lookup"><span data-stu-id="3f70f-105">In either case, to compile properly, the interop assembly must be in the same directory as the other project files.</span></span>  
  
 <span data-ttu-id="3f70f-106">Chcete-li sestavení vzájemné spolupráce dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="3f70f-106">There are two ways to reference interop assemblies:</span></span>  
  
-   <span data-ttu-id="3f70f-107">Vložené typy spolupráce: od verze [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] a [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)], můžete určit, aby kompilátoru pro vložení informací o typu ze sestavení spolupráce do spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="3f70f-107">Embedded interop types: Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] and [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)], you can instruct the compiler to embed type information from an interop assembly into your executable.</span></span> <span data-ttu-id="3f70f-108">Toto je doporučený postup.</span><span class="sxs-lookup"><span data-stu-id="3f70f-108">This is the recommended technique.</span></span>  
  
-   <span data-ttu-id="3f70f-109">Nasazení sestavení vzájemné spolupráce: můžete vytvořit standardní odkaz na sestavení spolupráce.</span><span class="sxs-lookup"><span data-stu-id="3f70f-109">Deploying interop assemblies: You can create a standard reference to an interop assembly.</span></span> <span data-ttu-id="3f70f-110">V takovém případě musí být nasazený sestavení vzájemné spolupráce s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="3f70f-110">In this case, the interop assembly must be deployed with your application.</span></span>  
  
 <span data-ttu-id="3f70f-111">Rozdíly mezi tyto dva postupy jsou popsány podrobněji na [pomocí typy modelu COM v spravovaného kódu](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="3f70f-111">The differences between these two techniques are discussed in greater detail in [Using COM Types in Managed Code](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100)).</span></span>  
  
 <span data-ttu-id="3f70f-112">Vložení typů spolupráce pomocí sady Visual Studio je znázorněn v [návod: vložení informací o typu ze sestavení sady Microsoft Office](http://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3) a [návod: vložení typů ze spravovaných sestavení](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).</span><span class="sxs-lookup"><span data-stu-id="3f70f-112">Embedding interop types with Visual Studio is demonstrated in [Walkthrough: Embedding Type Information from Microsoft Office Assemblies](http://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3) and [Walkthrough: Embedding Types from Managed Assemblies](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).</span></span>  
  
 <span data-ttu-id="3f70f-113">Odkazování na sestavení spolupráce s kompilátoru příkazového řádku a vložení informací o typu do vaší spustitelné soubory, použijte [/Link (možnosti kompilátoru C#)](~/docs/csharp/language-reference/compiler-options/link-compiler-option.md) nebo [/Link (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/link.md) přepínače kompilátoru a Zadejte název sestavení vzájemné spolupráce.</span><span class="sxs-lookup"><span data-stu-id="3f70f-113">To reference an interop assembly with a command-line compiler and embed type information in your executables, use the [/link (C# Compiler Options)](~/docs/csharp/language-reference/compiler-options/link-compiler-option.md) or the [/link (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/link.md) compiler switch and specify the name of the interop assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3f70f-114">Visual C++ aplikace nelze vložit informace o typu, ale můžou spolupracovat s aplikacemi nebo doplňky, které provádějí.</span><span class="sxs-lookup"><span data-stu-id="3f70f-114">Visual C++ applications cannot embed type information, but they can interoperate with applications or add-ins that do.</span></span>  
  
 <span data-ttu-id="3f70f-115">Kompilace aplikace, která zahrnuje primárních sestavení vzájemné spolupráce při nasazení, použijte **/reference** přepínače kompilátoru a zadejte název sestavení vzájemné spolupráce.</span><span class="sxs-lookup"><span data-stu-id="3f70f-115">To compile an application that includes a primary interop assembly when it is deployed, use the **/reference** compiler switch and specify the name of the interop assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f70f-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="3f70f-116">See Also</span></span>  
 [<span data-ttu-id="3f70f-117">Vystavení komponent COM pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3f70f-117">Exposing COM Components to the .NET Framework</span></span>](../../../docs/framework/interop/exposing-com-components.md)  
 [<span data-ttu-id="3f70f-118">Jazyková nezávislost a jazykově nezávislé komponenty</span><span class="sxs-lookup"><span data-stu-id="3f70f-118">Language Independence and Language-Independent Components</span></span>](../../../docs/standard/language-independence-and-language-independent-components.md)  
 <span data-ttu-id="3f70f-119">[Použití typy modelu COM ve spravovaném kódu](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3f70f-119">[Using COM Types in Managed Code](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100))</span></span>  
 [<span data-ttu-id="3f70f-120">Návod: Vložení informací o typu ze sestavení Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="3f70f-120">Walkthrough: Embedding Type Information from Microsoft Office Assemblies</span></span>](http://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3)  
 [<span data-ttu-id="3f70f-121">Návod: Vložení typů ze spravovaných sestavení</span><span class="sxs-lookup"><span data-stu-id="3f70f-121">Walkthrough: Embedding Types from Managed Assemblies</span></span>](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)  
 [<span data-ttu-id="3f70f-122">Import knihovny typů ve formě sestavení</span><span class="sxs-lookup"><span data-stu-id="3f70f-122">Importing a Type Library as an Assembly</span></span>](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)
