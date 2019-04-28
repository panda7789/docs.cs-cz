---
title: Kompilace projektu interoperability
ms.date: 03/30/2017
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
ms.openlocfilehash: 9b9f0cd44e5ab9a33db4dd2ef52681f40ca54080
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61643540"
---
# <a name="compiling-an-interop-project"></a><span data-ttu-id="371fd-102">Kompilace projektu interoperability</span><span class="sxs-lookup"><span data-stu-id="371fd-102">Compiling an Interop Project</span></span>

<span data-ttu-id="371fd-103">Projektů spolupráce modelu COM, které odkazují na jeden nebo více sestavení, která obsahují importované typy modelu COM jsou kompilovány jako ostatní spravovaného projektu.</span><span class="sxs-lookup"><span data-stu-id="371fd-103">COM interop projects that reference one or more assemblies containing imported COM types are compiled like any other managed project.</span></span> <span data-ttu-id="371fd-104">Můžete odkazovat na sestavení vzájemné spolupráce ve vývojovém prostředí, jako je Visual Studio, nebo je můžete odkazovat, při použití příkazového řádku kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="371fd-104">You can reference interop assemblies in a development environment such as Visual Studio, or you can reference them when you use a command-line compiler.</span></span> <span data-ttu-id="371fd-105">V obou případech se pro kompilaci správně, definiční sestavení musí být ve stejném adresáři jako jiné soubory projektu.</span><span class="sxs-lookup"><span data-stu-id="371fd-105">In either case, to compile properly, the interop assembly must be in the same directory as the other project files.</span></span>

 <span data-ttu-id="371fd-106">Existují dva způsoby, jak odkazovat na sestavení vzájemné spolupráce:</span><span class="sxs-lookup"><span data-stu-id="371fd-106">There are two ways to reference interop assemblies:</span></span>

- <span data-ttu-id="371fd-107">Vložené typy spolupráce: Počínaje [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] a Visual Studio 2010, můžete dát pokyn kompilátoru k vložení informací o typu ze sestavení vzájemné spolupráce do spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="371fd-107">Embedded interop types: Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] and Visual Studio 2010, you can instruct the compiler to embed type information from an interop assembly into your executable.</span></span> <span data-ttu-id="371fd-108">Toto je doporučený postup.</span><span class="sxs-lookup"><span data-stu-id="371fd-108">This is the recommended technique.</span></span>

- <span data-ttu-id="371fd-109">Nasazení sestavení vzájemné spolupráce: Můžete vytvořit standardní odkaz na sestavení vzájemné spolupráce.</span><span class="sxs-lookup"><span data-stu-id="371fd-109">Deploying interop assemblies: You can create a standard reference to an interop assembly.</span></span> <span data-ttu-id="371fd-110">V takovém případě musí být nasazeny sestavení zprostředkovatele komunikace s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="371fd-110">In this case, the interop assembly must be deployed with your application.</span></span>

 <span data-ttu-id="371fd-111">Rozdíly mezi tyto dva postupy jsou podrobně popsány v větší [typy modelu COM pomocí spravovaného kódu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="371fd-111">The differences between these two techniques are discussed in greater detail in [Using COM Types in Managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span></span>

 <span data-ttu-id="371fd-112">Vkládání typů spolupráce pomocí sady Visual Studio jsou popsané v článku [názorný postup: Vložení typů ze spravovaných sestavení v sadě Visual Studio (C#)](/docs/csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md), a [názorný postup: Vložení typů ze spravovaných sestavení v sadě Visual Studio (Visual Basic)](/docs/visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="371fd-112">Embedding interop types with Visual Studio is demonstrated in [Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (C#)](/docs/csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md), and [Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (Visual Basic)](/docs/visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md).</span></span>

 <span data-ttu-id="371fd-113">Chcete-li odkazovat na sestavení vzájemné spolupráce pomocí kompilátoru příkazového řádku a vložit informace o typu v vaše spustitelné soubory, použijte [/Link (možnosti kompilátoru C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md) nebo [/Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) přepínače kompilátoru a Zadejte název sestavení vzájemné spolupráce.</span><span class="sxs-lookup"><span data-stu-id="371fd-113">To reference an interop assembly with a command-line compiler and embed type information in your executables, use the [/link (C# Compiler Options)](../../csharp/language-reference/compiler-options/link-compiler-option.md) or the [/link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) compiler switch and specify the name of the interop assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="371fd-114">Aplikace Visual C++ nelze vložit informace o typu, ale můžou spolupracovat s aplikací nebo doplňky, které provést.</span><span class="sxs-lookup"><span data-stu-id="371fd-114">Visual C++ applications cannot embed type information, but they can interoperate with applications or add-ins that do.</span></span>

 <span data-ttu-id="371fd-115">Chcete-li kompilovat aplikaci, která obsahuje primární sestavení zprostředkovatele komunikace při nasazení, použijte **/reference** přepínače kompilátoru a zadejte název sestavení vzájemné spolupráce.</span><span class="sxs-lookup"><span data-stu-id="371fd-115">To compile an application that includes a primary interop assembly when it is deployed, use the **/reference** compiler switch and specify the name of the interop assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="371fd-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="371fd-116">See also</span></span>

- [<span data-ttu-id="371fd-117">Vystavení komponent COM pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="371fd-117">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
- [<span data-ttu-id="371fd-118">Jazyková nezávislost a jazykově nezávislé komponenty</span><span class="sxs-lookup"><span data-stu-id="371fd-118">Language Independence and Language-Independent Components</span></span>](../../standard/language-independence-and-language-independent-components.md)
- <span data-ttu-id="371fd-119">[Používání typů modelu COM ve spravovaném kódu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="371fd-119">[Using COM Types in Managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span></span>
- [<span data-ttu-id="371fd-120">Návod: Vložení typů ze spravovaných sestavení v sadě Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="371fd-120">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (C#)</span></span>](/docs/csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)
- [<span data-ttu-id="371fd-121">Návod: Vložení typů ze spravovaných sestavení v sadě Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="371fd-121">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (Visual Basic)</span></span>](/docs/visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)
- [<span data-ttu-id="371fd-122">Import knihovny typů ve formě sestavení</span><span class="sxs-lookup"><span data-stu-id="371fd-122">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)