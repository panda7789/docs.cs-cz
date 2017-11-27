---
title: "Postupy: Přidávání odkazů do knihoven typů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- type libraries
- COM interop, importing type library
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e5bbc99c3c40b0864a7c1c25cb79a3d7c26e3a86
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-references-to-type-libraries"></a><span data-ttu-id="ecae9-102">Postupy: Přidávání odkazů do knihoven typů</span><span class="sxs-lookup"><span data-stu-id="ecae9-102">How to: Add References to Type Libraries</span></span>
<span data-ttu-id="ecae9-103">Visual Studio generuje spolupráce sestavení obsahující metadata, když přidáte odkaz na knihovnu typů.</span><span class="sxs-lookup"><span data-stu-id="ecae9-103">Visual Studio generates an interop assembly containing metadata when you add a reference to a type library.</span></span> <span data-ttu-id="ecae9-104">Pokud je primární spolupracující sestavení je k dispozici, Visual Studio použije existující sestavení před vygenerováním nové sestavení vzájemné spolupráce.</span><span class="sxs-lookup"><span data-stu-id="ecae9-104">If a primary interop assembly is available, Visual Studio uses the existing assembly before generating a new interop assembly.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a><span data-ttu-id="ecae9-105">Chcete-li přidat odkaz na knihovnu typů v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ecae9-105">To add a reference to a type library in Visual Studio</span></span>  
  
1.  <span data-ttu-id="ecae9-106">Nainstalujte soubor COM DLL nebo EXE v počítači, pokud soubor Setup.exe systému Windows pro vás provede instalaci.</span><span class="sxs-lookup"><span data-stu-id="ecae9-106">Install the COM DLL or EXE file on your computer, unless a Windows Setup.exe file performs the installation for you.</span></span>  
  
2.  <span data-ttu-id="ecae9-107">Zvolte **projektu**, **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="ecae9-107">Choose **Project**, **Add Reference**.</span></span>  
  
3.  <span data-ttu-id="ecae9-108">Zvolte ve Správci odkaz **COM**.</span><span class="sxs-lookup"><span data-stu-id="ecae9-108">In the Reference Manager, choose **COM**.</span></span>  
  
4.  <span data-ttu-id="ecae9-109">Vyberte typ knihovnu ze seznamu nebo .tlb soubor vyhledejte.</span><span class="sxs-lookup"><span data-stu-id="ecae9-109">Select the type library from the list, or browse for the .tlb file.</span></span>  
  
5.  <span data-ttu-id="ecae9-110">Zvolte **OK**.</span><span class="sxs-lookup"><span data-stu-id="ecae9-110">Choose **OK**.</span></span>  
  
6.  <span data-ttu-id="ecae9-111">V Průzkumníku řešení otevřete místní nabídku pro odkaz, na které jste právě přidali a potom zvolte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="ecae9-111">In Solution Explorer, open the shortcut menu for the reference you just added, and then choose **Properties**.</span></span>  
  
7.  <span data-ttu-id="ecae9-112">V **vlastnosti** okna, ujistěte se, že **vložit zprostředkovatel komunikace s objekty typy** je nastavena na **True**.</span><span class="sxs-lookup"><span data-stu-id="ecae9-112">In the **Properties** window, make sure that the **Embed Interop Types** property is set to **True**.</span></span> <span data-ttu-id="ecae9-113">To způsobí, že Visual Studio pro vložení informací o typu pro typy modelu COM v spustitelné soubory, takže není nutné nasadit primárních sestavení vzájemné spolupráce s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="ecae9-113">This causes Visual Studio to embed type information for COM types in your executables, eliminating the need to deploy primary interop assemblies with your app.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ecae9-114">Nabídce a dialogové okno Možnosti se může lišit v závislosti na verzi Visual Studia, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="ecae9-114">The menu and dialog box options may vary depending on the version of Visual Studio you're using.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a><span data-ttu-id="ecae9-115">Chcete-li přidat odkaz na knihovnu typů pro příkazového řádku kompilace</span><span class="sxs-lookup"><span data-stu-id="ecae9-115">To add a reference to a type library for command-line compilation</span></span>  
  
1.  <span data-ttu-id="ecae9-116">Generování sestavení vzájemné spolupráce, jak je popsáno v [postupy: generování sestavení zprostředkovatel komunikace s objekty z knihoven typů](../../../docs/framework/interop/how-to-generate-interop-assemblies-from-type-libraries.md).</span><span class="sxs-lookup"><span data-stu-id="ecae9-116">Generate an interop assembly as described in [How to: Generate Interop Assemblies from Type Libraries](../../../docs/framework/interop/how-to-generate-interop-assemblies-from-type-libraries.md).</span></span>  
  
2.  <span data-ttu-id="ecae9-117">Použití [/Link (možnosti kompilátoru C#)](~/docs/csharp/language-reference/compiler-options/link-compiler-option.md) nebo [/Link (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/link.md) – možnost kompilátoru s názvem sestavení vzájemné spolupráce pro vložení informací o typu pro model COM typy, které do vašeho spustitelné soubory.</span><span class="sxs-lookup"><span data-stu-id="ecae9-117">Use the [/link (C# Compiler Options)](~/docs/csharp/language-reference/compiler-options/link-compiler-option.md) or [/link (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/link.md) compiler option with the interop assembly name to embed type information for COM types in your executables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecae9-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="ecae9-118">See Also</span></span>  
 [<span data-ttu-id="ecae9-119">Import knihovny typů jako sestavení</span><span class="sxs-lookup"><span data-stu-id="ecae9-119">Importing a Type Library as an Assembly</span></span>](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)  
 [<span data-ttu-id="ecae9-120">Vystavení součástí COM v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ecae9-120">Exposing COM Components to the .NET Framework</span></span>](../../../docs/framework/interop/exposing-com-components.md)  
 [<span data-ttu-id="ecae9-121">Návod: Vložení informací o typu ze sestavení sady Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="ecae9-121">Walkthrough: Embedding Type Information from Microsoft Office Assemblies</span></span>](http://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3)  
 [<span data-ttu-id="ecae9-122">Návod: Vložení typů z řízených sestavení</span><span class="sxs-lookup"><span data-stu-id="ecae9-122">Walkthrough: Embedding Types from Managed Assemblies</span></span>](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)  
 [<span data-ttu-id="ecae9-123">/ Link (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="ecae9-123">/link (C# Compiler Options)</span></span>](~/docs/csharp/language-reference/compiler-options/link-compiler-option.md)  
 [<span data-ttu-id="ecae9-124">/ Link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ecae9-124">/link (Visual Basic)</span></span>](~/docs/visual-basic/reference/command-line-compiler/link.md)
