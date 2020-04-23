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
ms.openlocfilehash: 32102910ae674a97e941e1346a1898585f503527
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123674"
---
# <a name="compiling-an-interop-project"></a><span data-ttu-id="c7229-102">Kompilace projektu interoperability</span><span class="sxs-lookup"><span data-stu-id="c7229-102">Compiling an Interop Project</span></span>

<span data-ttu-id="c7229-103">Projekty Interop modelu COM, které odkazují na jedno nebo více sestavení obsahujících importované typy modelu COM, jsou kompilovány stejným způsobem jako jakýkoli jiný spravovaný projekt.</span><span class="sxs-lookup"><span data-stu-id="c7229-103">COM interop projects that reference one or more assemblies containing imported COM types are compiled like any other managed project.</span></span> <span data-ttu-id="c7229-104">Můžete odkazovat na sestavení spolupráce ve vývojovém prostředí, jako je například Visual Studio, nebo na ně můžete odkazovat při použití kompilátoru příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="c7229-104">You can reference interop assemblies in a development environment such as Visual Studio, or you can reference them when you use a command-line compiler.</span></span> <span data-ttu-id="c7229-105">V obou případech pro správné kompilování definičního sestavení musí být ve stejném adresáři jako jiné soubory projektu.</span><span class="sxs-lookup"><span data-stu-id="c7229-105">In either case, to compile properly, the interop assembly must be in the same directory as the other project files.</span></span>

 <span data-ttu-id="c7229-106">Existují dva způsoby, jak odkazovat na definiční sestavení:</span><span class="sxs-lookup"><span data-stu-id="c7229-106">There are two ways to reference interop assemblies:</span></span>

- <span data-ttu-id="c7229-107">Vložené typy spolupráce: počínaje .NET Framework 4 a Visual Studio 2010 můžete instruovat kompilátor, aby vložil informace o typu ze sestavení pro spolupráci do spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="c7229-107">Embedded interop types: Beginning with the .NET Framework 4 and Visual Studio 2010, you can instruct the compiler to embed type information from an interop assembly into your executable.</span></span> <span data-ttu-id="c7229-108">Toto je doporučený postup.</span><span class="sxs-lookup"><span data-stu-id="c7229-108">This is the recommended technique.</span></span>

- <span data-ttu-id="c7229-109">Nasazení definičních sestavení: můžete vytvořit standardní odkaz na definiční sestavení.</span><span class="sxs-lookup"><span data-stu-id="c7229-109">Deploying interop assemblies: You can create a standard reference to an interop assembly.</span></span> <span data-ttu-id="c7229-110">V takovém případě musí být definiční sestavení nasazeno s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="c7229-110">In this case, the interop assembly must be deployed with your application.</span></span>

 <span data-ttu-id="c7229-111">Rozdíly mezi těmito dvěma technikami jsou podrobněji popsány v tématu [použití typů modelu COM ve spravovaném kódu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="c7229-111">The differences between these two techniques are discussed in greater detail in [Using COM Types in Managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span></span>

 <span data-ttu-id="c7229-112">Vkládání typů spolupráce pomocí sady Visual Studio je znázorněno v [návodu: Vložení typů ze spravovaných sestavení v aplikaci Visual Studio](../../standard/assembly/embed-types-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="c7229-112">Embedding interop types with Visual Studio is demonstrated in [Walkthrough: Embedding Types from Managed Assemblies in Visual Studio](../../standard/assembly/embed-types-visual-studio.md).</span></span>

 <span data-ttu-id="c7229-113">Chcete-li odkazovat na definiční sestavení s kompilátorem příkazového řádku a vkládat informace o typu ve vašich spustitelných souborech, použijte přepínač [-Link (možnosti kompilátoru C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md) nebo přepínač [-Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) a zadejte název sestavení vzájemné spolupráce.</span><span class="sxs-lookup"><span data-stu-id="c7229-113">To reference an interop assembly with a command-line compiler and embed type information in your executables, use the [-link (C# Compiler Options)](../../csharp/language-reference/compiler-options/link-compiler-option.md) or the [-link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) compiler switch and specify the name of the interop assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="c7229-114">Aplikace Visual C++ nemůžou vkládat informace o typu, ale můžou spolupracovat s aplikacemi nebo doplňky, které to dělají.</span><span class="sxs-lookup"><span data-stu-id="c7229-114">Visual C++ applications cannot embed type information, but they can interoperate with applications or add-ins that do.</span></span>

 <span data-ttu-id="c7229-115">Chcete-li zkompilovat aplikaci, která zahrnuje primární definiční sestavení při nasazení, použijte přepínač **/reference** Compiler a zadejte název definičního sestavení.</span><span class="sxs-lookup"><span data-stu-id="c7229-115">To compile an application that includes a primary interop assembly when it is deployed, use the **/reference** compiler switch and specify the name of the interop assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="c7229-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="c7229-116">See also</span></span>

- [<span data-ttu-id="c7229-117">Vystavení komponent COM pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c7229-117">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
- [<span data-ttu-id="c7229-118">Jazyková nezávislost a jazykově nezávislé komponenty</span><span class="sxs-lookup"><span data-stu-id="c7229-118">Language Independence and Language-Independent Components</span></span>](../../standard/language-independence-and-language-independent-components.md)
- <span data-ttu-id="c7229-119">[Použití typů modelu COM ve spravovaném kódu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c7229-119">[Using COM Types in Managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span></span>
- [<span data-ttu-id="c7229-120">Návod: Vložení typů ze spravovaných sestavení v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c7229-120">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio</span></span>](../../standard/assembly/embed-types-visual-studio.md)
- [<span data-ttu-id="c7229-121">Import knihovny typů ve formě sestavení</span><span class="sxs-lookup"><span data-stu-id="c7229-121">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
