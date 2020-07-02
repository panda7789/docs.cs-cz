---
title: 'Postupy: Přidávání odkazů do knihoven typů'
description: Naučte se, jak přidat odkazy na knihovny typů v aplikaci Visual Studio nebo pro kompilaci příkazového řádku.
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- type libraries
- COM interop, importing type library
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
ms.openlocfilehash: a3c24385c9cc7debe95aa10369b050897415bc46
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617428"
---
# <a name="how-to-add-references-to-type-libraries"></a><span data-ttu-id="f348f-103">Postupy: Přidávání odkazů do knihoven typů</span><span class="sxs-lookup"><span data-stu-id="f348f-103">How to: Add References to Type Libraries</span></span>
<span data-ttu-id="f348f-104">Když přidáte odkaz na knihovnu typů, Visual Studio vygeneruje sestavení vzájemné spolupráce obsahující metadata.</span><span class="sxs-lookup"><span data-stu-id="f348f-104">Visual Studio generates an interop assembly containing metadata when you add a reference to a type library.</span></span> <span data-ttu-id="f348f-105">Pokud je k dispozici primární sestavení vzájemné spolupráce, Visual Studio použije existující sestavení před generováním nového definičního sestavení.</span><span class="sxs-lookup"><span data-stu-id="f348f-105">If a primary interop assembly is available, Visual Studio uses the existing assembly before generating a new interop assembly.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a><span data-ttu-id="f348f-106">Přidání odkazu na knihovnu typů v aplikaci Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f348f-106">To add a reference to a type library in Visual Studio</span></span>  
  
1. <span data-ttu-id="f348f-107">Nainstalujte do počítače soubor DLL nebo EXE knihovny COM, pokud soubor Setup.exe Windows neprovede instalaci za vás.</span><span class="sxs-lookup"><span data-stu-id="f348f-107">Install the COM DLL or EXE file on your computer, unless a Windows Setup.exe file performs the installation for you.</span></span>  
  
2. <span data-ttu-id="f348f-108">Vyberte **projekt**, **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="f348f-108">Choose **Project**, **Add Reference**.</span></span>  
  
3. <span data-ttu-id="f348f-109">Ve Správci odkazů vyberte **com**.</span><span class="sxs-lookup"><span data-stu-id="f348f-109">In the Reference Manager, choose **COM**.</span></span>  
  
4. <span data-ttu-id="f348f-110">V seznamu vyberte knihovnu typů nebo vyhledejte soubor. tlb.</span><span class="sxs-lookup"><span data-stu-id="f348f-110">Select the type library from the list, or browse for the .tlb file.</span></span>  
  
5. <span data-ttu-id="f348f-111">Vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="f348f-111">Choose **OK**.</span></span>  
  
6. <span data-ttu-id="f348f-112">V Průzkumník řešení otevřete místní nabídku pro odkaz, který jste právě přidali, a pak zvolte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="f348f-112">In Solution Explorer, open the shortcut menu for the reference you just added, and then choose **Properties**.</span></span>  
  
7. <span data-ttu-id="f348f-113">V okně **vlastnosti** se ujistěte, že je vlastnost **Embed Interop Types** nastavená na **hodnotu true**.</span><span class="sxs-lookup"><span data-stu-id="f348f-113">In the **Properties** window, make sure that the **Embed Interop Types** property is set to **True**.</span></span> <span data-ttu-id="f348f-114">To způsobí, že Visual Studio vloží do vašich spustitelných souborů informace o typu modelu COM, což eliminuje nutnost nasazení primárních sestavení vzájemné spolupráce s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="f348f-114">This causes Visual Studio to embed type information for COM types in your executables, eliminating the need to deploy primary interop assemblies with your app.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f348f-115">Možnosti nabídky a dialogového okna se můžou lišit v závislosti na verzi sady Visual Studio, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="f348f-115">The menu and dialog box options may vary depending on the version of Visual Studio you're using.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a><span data-ttu-id="f348f-116">Přidání odkazu na knihovnu typů pro kompilaci příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="f348f-116">To add a reference to a type library for command-line compilation</span></span>  
  
1. <span data-ttu-id="f348f-117">Vygenerujte sestavení vzájemné spolupráce, jak je popsáno v tématu [Postupy: generování sestavení vzájemné spolupráce z knihoven typů](how-to-generate-interop-assemblies-from-type-libraries.md).</span><span class="sxs-lookup"><span data-stu-id="f348f-117">Generate an interop assembly as described in [How to: Generate Interop Assemblies from Type Libraries](how-to-generate-interop-assemblies-from-type-libraries.md).</span></span>  
  
2. <span data-ttu-id="f348f-118">Použijte možnost [-Link (možnosti kompilátoru C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md) nebo [-Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) s názvem definičního sestavení pro vložení informací o typu pro typy com ve vašich spustitelných souborech.</span><span class="sxs-lookup"><span data-stu-id="f348f-118">Use the [-link (C# Compiler Options)](../../csharp/language-reference/compiler-options/link-compiler-option.md) or [-link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) compiler option with the interop assembly name to embed type information for COM types in your executables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f348f-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f348f-119">See also</span></span>

- [<span data-ttu-id="f348f-120">Import knihovny typů ve formě sestavení</span><span class="sxs-lookup"><span data-stu-id="f348f-120">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
- [<span data-ttu-id="f348f-121">Vystavení komponent COM pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f348f-121">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
- [<span data-ttu-id="f348f-122">Návod: Vložení typů ze spravovaných sestavení v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f348f-122">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio</span></span>](../../standard/assembly/embed-types-visual-studio.md)
- [<span data-ttu-id="f348f-123">-Link (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="f348f-123">-link (C# Compiler Options)</span></span>](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [<span data-ttu-id="f348f-124">-Link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f348f-124">-link (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/link.md)
