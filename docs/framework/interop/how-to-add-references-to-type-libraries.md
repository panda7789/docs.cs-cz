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
ms.openlocfilehash: a666c0e079fb30ecdd32aad64f44434d8253acf4
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971893"
---
# <a name="how-to-add-references-to-type-libraries"></a><span data-ttu-id="3885c-102">Postupy: Přidávání odkazů do knihoven typů</span><span class="sxs-lookup"><span data-stu-id="3885c-102">How to: Add References to Type Libraries</span></span>
<span data-ttu-id="3885c-103">Když přidáte odkaz na knihovnu typů, Visual Studio vygeneruje sestavení vzájemné spolupráce obsahující metadata.</span><span class="sxs-lookup"><span data-stu-id="3885c-103">Visual Studio generates an interop assembly containing metadata when you add a reference to a type library.</span></span> <span data-ttu-id="3885c-104">Pokud je k dispozici primární sestavení vzájemné spolupráce, Visual Studio použije existující sestavení před generováním nového definičního sestavení.</span><span class="sxs-lookup"><span data-stu-id="3885c-104">If a primary interop assembly is available, Visual Studio uses the existing assembly before generating a new interop assembly.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a><span data-ttu-id="3885c-105">Přidání odkazu na knihovnu typů v aplikaci Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3885c-105">To add a reference to a type library in Visual Studio</span></span>  
  
1. <span data-ttu-id="3885c-106">Nainstalujte do počítače soubor DLL nebo EXE knihovny COM, pokud soubor instalační program systému Windows. exe instalaci neprovede.</span><span class="sxs-lookup"><span data-stu-id="3885c-106">Install the COM DLL or EXE file on your computer, unless a Windows Setup.exe file performs the installation for you.</span></span>  
  
2. <span data-ttu-id="3885c-107">Vyberte **projekt**, **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="3885c-107">Choose **Project**, **Add Reference**.</span></span>  
  
3. <span data-ttu-id="3885c-108">Ve Správci odkazů vyberte **com**.</span><span class="sxs-lookup"><span data-stu-id="3885c-108">In the Reference Manager, choose **COM**.</span></span>  
  
4. <span data-ttu-id="3885c-109">V seznamu vyberte knihovnu typů nebo vyhledejte soubor. tlb.</span><span class="sxs-lookup"><span data-stu-id="3885c-109">Select the type library from the list, or browse for the .tlb file.</span></span>  
  
5. <span data-ttu-id="3885c-110">Zvolte **OK**.</span><span class="sxs-lookup"><span data-stu-id="3885c-110">Choose **OK**.</span></span>  
  
6. <span data-ttu-id="3885c-111">V Průzkumník řešení otevřete místní nabídku pro odkaz, který jste právě přidali, a pak zvolte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="3885c-111">In Solution Explorer, open the shortcut menu for the reference you just added, and then choose **Properties**.</span></span>  
  
7. <span data-ttu-id="3885c-112">V okně **vlastnosti** se ujistěte, že je vlastnost **Embed Interop Types** nastavená na **hodnotu true**.</span><span class="sxs-lookup"><span data-stu-id="3885c-112">In the **Properties** window, make sure that the **Embed Interop Types** property is set to **True**.</span></span> <span data-ttu-id="3885c-113">To způsobí, že Visual Studio vloží do vašich spustitelných souborů informace o typu modelu COM, což eliminuje nutnost nasazení primárních sestavení vzájemné spolupráce s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="3885c-113">This causes Visual Studio to embed type information for COM types in your executables, eliminating the need to deploy primary interop assemblies with your app.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3885c-114">Možnosti nabídky a dialogového okna se můžou lišit v závislosti na verzi sady Visual Studio, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="3885c-114">The menu and dialog box options may vary depending on the version of Visual Studio you're using.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a><span data-ttu-id="3885c-115">Přidání odkazu na knihovnu typů pro kompilaci příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="3885c-115">To add a reference to a type library for command-line compilation</span></span>  
  
1. <span data-ttu-id="3885c-116">Vygenerujte sestavení vzájemné spolupráce, jak [je popsáno v tématu Postupy: Vygenerujte sestavení vzájemné spolupráce z](how-to-generate-interop-assemblies-from-type-libraries.md)knihoven typů.</span><span class="sxs-lookup"><span data-stu-id="3885c-116">Generate an interop assembly as described in [How to: Generate Interop Assemblies from Type Libraries](how-to-generate-interop-assemblies-from-type-libraries.md).</span></span>  
  
2. <span data-ttu-id="3885c-117">K vložení informací o typu pro typy COM ve vašich spustitelných souborech použijte možnost kompilátoru [/Link (C# Compiler Options)](../../csharp/language-reference/compiler-options/link-compiler-option.md) nebo [/Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) s názvem sestavení spolupráce.</span><span class="sxs-lookup"><span data-stu-id="3885c-117">Use the [/link (C# Compiler Options)](../../csharp/language-reference/compiler-options/link-compiler-option.md) or [/link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) compiler option with the interop assembly name to embed type information for COM types in your executables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3885c-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3885c-118">See also</span></span>

- [<span data-ttu-id="3885c-119">Import knihovny typů ve formě sestavení</span><span class="sxs-lookup"><span data-stu-id="3885c-119">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
- [<span data-ttu-id="3885c-120">Vystavení komponent COM pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3885c-120">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
- [<span data-ttu-id="3885c-121">Návod: Vložení typů ze spravovaných sestavení v aplikaci Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3885c-121">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio</span></span>](../../standard/assembly/embed-types-visual-studio.md) 
- [<span data-ttu-id="3885c-122">/Link (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="3885c-122">/link (C# Compiler Options)</span></span>](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [<span data-ttu-id="3885c-123">/Link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3885c-123">/link (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/link.md)
