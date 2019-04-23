---
title: 'Postupy: Přidávání odkazů do knihoven typů'
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- type libraries
- COM interop, importing type library
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b3fda2af84ff74e129c36dc966bad247bdf9e20
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59427133"
---
# <a name="how-to-add-references-to-type-libraries"></a><span data-ttu-id="f050f-102">Postupy: Přidávání odkazů do knihoven typů</span><span class="sxs-lookup"><span data-stu-id="f050f-102">How to: Add References to Type Libraries</span></span>
<span data-ttu-id="f050f-103">Visual Studio vytvoří definiční sestavení obsahující metadata, když přidáte odkaz na knihovnu typů.</span><span class="sxs-lookup"><span data-stu-id="f050f-103">Visual Studio generates an interop assembly containing metadata when you add a reference to a type library.</span></span> <span data-ttu-id="f050f-104">Pokud je k dispozici primární sestavení zprostředkovatele komunikace, Visual Studio používá existující sestavení před generováním nového sestavení zprostředkovatele komunikace.</span><span class="sxs-lookup"><span data-stu-id="f050f-104">If a primary interop assembly is available, Visual Studio uses the existing assembly before generating a new interop assembly.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a><span data-ttu-id="f050f-105">Chcete-li přidat odkaz na knihovnu typů v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f050f-105">To add a reference to a type library in Visual Studio</span></span>  
  
1. <span data-ttu-id="f050f-106">Instalace knihovny COM DLL nebo EXE soubor v počítači, není-li soubor Windows Setup.exe provede instalaci za vás.</span><span class="sxs-lookup"><span data-stu-id="f050f-106">Install the COM DLL or EXE file on your computer, unless a Windows Setup.exe file performs the installation for you.</span></span>  
  
2. <span data-ttu-id="f050f-107">Zvolte **projektu**, **přidat odkaz na**.</span><span class="sxs-lookup"><span data-stu-id="f050f-107">Choose **Project**, **Add Reference**.</span></span>  
  
3. <span data-ttu-id="f050f-108">Vyberte ve Správci odkazů **COM**.</span><span class="sxs-lookup"><span data-stu-id="f050f-108">In the Reference Manager, choose **COM**.</span></span>  
  
4. <span data-ttu-id="f050f-109">Vyberte knihovnu typů, ze seznamu nebo vyhledání souboru .tlb.</span><span class="sxs-lookup"><span data-stu-id="f050f-109">Select the type library from the list, or browse for the .tlb file.</span></span>  
  
5. <span data-ttu-id="f050f-110">Zvolte **OK**.</span><span class="sxs-lookup"><span data-stu-id="f050f-110">Choose **OK**.</span></span>  
  
6. <span data-ttu-id="f050f-111">V Průzkumníku řešení otevřete místní nabídku pro odkaz, který jste právě přidali a klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="f050f-111">In Solution Explorer, open the shortcut menu for the reference you just added, and then choose **Properties**.</span></span>  
  
7. <span data-ttu-id="f050f-112">V **vlastnosti** okno, ujistěte se, že **Embed Interop Types** je nastavena na **True**.</span><span class="sxs-lookup"><span data-stu-id="f050f-112">In the **Properties** window, make sure that the **Embed Interop Types** property is set to **True**.</span></span> <span data-ttu-id="f050f-113">To způsobí, že Visual Studio pro vložení informací o typu pro typy modelu COM v spustitelné soubory, takže odpadá potřeba k nasazení primárních sestavení vzájemné spolupráce s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="f050f-113">This causes Visual Studio to embed type information for COM types in your executables, eliminating the need to deploy primary interop assemblies with your app.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f050f-114">Pole možnosti nabídky a dialogové okno se mohou lišit v závislosti na verzi sady Visual Studio, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="f050f-114">The menu and dialog box options may vary depending on the version of Visual Studio you're using.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a><span data-ttu-id="f050f-115">Chcete-li přidat odkaz na knihovnu typů pro sestavení příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="f050f-115">To add a reference to a type library for command-line compilation</span></span>  
  
1. <span data-ttu-id="f050f-116">Generování sestavení vzájemné spolupráce, jak je popsáno v [jak: Generování sestavení vzájemné spolupráce z knihoven typů](how-to-generate-interop-assemblies-from-type-libraries.md).</span><span class="sxs-lookup"><span data-stu-id="f050f-116">Generate an interop assembly as described in [How to: Generate Interop Assemblies from Type Libraries](how-to-generate-interop-assemblies-from-type-libraries.md).</span></span>  
  
2. <span data-ttu-id="f050f-117">Použití [/link (C# – možnosti kompilátoru)](../../csharp/language-reference/compiler-options/link-compiler-option.md) nebo [/Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) – možnost kompilátoru s názvem sestavení vzájemné spolupráce pro vložení informací o typu pro model COM typy, které do vašeho spustitelné soubory.</span><span class="sxs-lookup"><span data-stu-id="f050f-117">Use the [/link (C# Compiler Options)](../../csharp/language-reference/compiler-options/link-compiler-option.md) or [/link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) compiler option with the interop assembly name to embed type information for COM types in your executables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f050f-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f050f-118">See also</span></span>

- [<span data-ttu-id="f050f-119">Import knihovny typů ve formě sestavení</span><span class="sxs-lookup"><span data-stu-id="f050f-119">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
- [<span data-ttu-id="f050f-120">Vystavení komponent COM pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f050f-120">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
- [<span data-ttu-id="f050f-121">Návod: Vložení typů ze spravovaných sestavení v sadě Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="f050f-121">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (C#)</span></span>](../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md) 
- [<span data-ttu-id="f050f-122">Návod: Vložení typů ze spravovaných sestavení v sadě Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f050f-122">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)
- [<span data-ttu-id="f050f-123">/ Link (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="f050f-123">/link (C# Compiler Options)</span></span>](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [<span data-ttu-id="f050f-124">/ Link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f050f-124">/link (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/link.md)
