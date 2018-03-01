---
title: "Sestavení nelze vygenerovat: &lt;chybová zpráva&gt;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b19b6439d85822c69adac0b3e0e04b2f31299836
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="unable-to-emit-assembly-lterror-messagegt"></a><span data-ttu-id="c0d87-102">Sestavení nelze vygenerovat: &lt;chybová zpráva&gt;</span><span class="sxs-lookup"><span data-stu-id="c0d87-102">Unable to emit assembly: &lt;error message&gt;</span></span>
<span data-ttu-id="c0d87-103">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompilátoru volá Linker sestavení (Al.exe, také známé jako Alink) ke generování sestavení s manifestu, s linkeru reporting chybu ve fázi emisí vytváření sestavení.</span><span class="sxs-lookup"><span data-stu-id="c0d87-103">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest, with the linker reporting an error in the emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="c0d87-104">**ID chyby:** BC30145</span><span class="sxs-lookup"><span data-stu-id="c0d87-104">**Error ID:** BC30145</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c0d87-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="c0d87-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="c0d87-106">Prověřením uvozovkách chybové zprávy a podívejte se téma [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="c0d87-106">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="c0d87-107">Další vysvětlení a Rady, jak.</span><span class="sxs-lookup"><span data-stu-id="c0d87-107">for further explanation and advice.</span></span>  
  
2.  <span data-ttu-id="c0d87-108">Zkuste se sestavení ručně, buď pomocí [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) nebo [Sn.exe (nástroj silným názvem)](../../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="c0d87-108">Try signing the assembly manually, using either the [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) or the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md).</span></span>  
  
3.  <span data-ttu-id="c0d87-109">Pokud potíže potrvají, shromažďovat informace o okolnostech a upozornění služby Microsoft Product Support Services.</span><span class="sxs-lookup"><span data-stu-id="c0d87-109">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
### <a name="to-sign-the-assembly-manually"></a><span data-ttu-id="c0d87-110">K podepsání sestavení ručně</span><span class="sxs-lookup"><span data-stu-id="c0d87-110">To sign the assembly manually</span></span>  
  
1.  <span data-ttu-id="c0d87-111">Použití [Sn.exe (nástroj silným názvem)][Sn.exe (nástroj silným názvem)](../../../framework/tools/sn-exe-strong-name-tool.md)) k vytvoření souboru pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="c0d87-111">Use the [Sn.exe (Strong Name Tool)][Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)) to create a public/private key pair file.</span></span>  
  
     <span data-ttu-id="c0d87-112">Tento soubor má příponu .snk.</span><span class="sxs-lookup"><span data-stu-id="c0d87-112">This file has a .snk extension.</span></span>  
  
2.  <span data-ttu-id="c0d87-113">Odstraňte odkaz na modelu COM, která generuje chybu ze svého projektu.</span><span class="sxs-lookup"><span data-stu-id="c0d87-113">Delete the COM reference that is generating the error from your project.</span></span>  
  
3.  <span data-ttu-id="c0d87-114">Z Windows **spustit** nabídky, přejděte na příkaz **programy**, přejděte na příkaz **Microsoft Visual Studio 2008**, přejděte na příkaz **nástroje sady Visual Studio**, a pak klikněte na tlačítko **příkazový řádek sady Visual Studio 2008**.</span><span class="sxs-lookup"><span data-stu-id="c0d87-114">From the Windows **Start** menu, point to **Programs**, point to **Microsoft Visual Studio 2008**, point to **Visual Studio Tools**, and then click **Visual Studio 2008 Command Prompt**.</span></span>  
  
4.  <span data-ttu-id="c0d87-115">Přesunout do adresáře, kam chcete umístit vaše obálku sestavení.</span><span class="sxs-lookup"><span data-stu-id="c0d87-115">Move to the directory where you want to place your assembly wrapper.</span></span>  
  
5.  <span data-ttu-id="c0d87-116">Zadejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="c0d87-116">Type the following code.</span></span>  
  
    ```  
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>  
    ```  
  
     <span data-ttu-id="c0d87-117">Příklad kódu, který můžete zadat by následující.</span><span class="sxs-lookup"><span data-stu-id="c0d87-117">An example of the code you might enter would be the following.</span></span>  
  
    ```  
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"  
    ```  
  
     <span data-ttu-id="c0d87-118">Pokud cesta nebo soubor obsahuje mezery, použijte uvozovky (").</span><span class="sxs-lookup"><span data-stu-id="c0d87-118">Use double quotation marks (") if a path or file contains spaces.</span></span>  
  
6.  <span data-ttu-id="c0d87-119">V [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], přidejte sestavení .NET odkaz na soubor, který jste právě vytvořili.</span><span class="sxs-lookup"><span data-stu-id="c0d87-119">In [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], add a .NET Assembly reference to the file you just created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0d87-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="c0d87-120">See Also</span></span>  
 
 <span data-ttu-id="c0d87-121">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="c0d87-121">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span>  
 <span data-ttu-id="c0d87-122">[Sn.exe (nástroj pro silný název)] [Sn.exe (nástroj pro silný název)](../../../framework/tools/sn-exe-strong-name-tool.md))</span><span class="sxs-lookup"><span data-stu-id="c0d87-122">[Sn.exe (Strong Name Tool)][Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md))</span></span>  
 [<span data-ttu-id="c0d87-123">Postupy: Vytvoření páru veřejného a soukromého klíče</span><span class="sxs-lookup"><span data-stu-id="c0d87-123">How to: Create a Public-Private Key Pair</span></span>](../../../framework/app-domains/how-to-create-a-public-private-key-pair.md)  
 [<span data-ttu-id="c0d87-124">Kontaktujte nás</span><span class="sxs-lookup"><span data-stu-id="c0d87-124">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
