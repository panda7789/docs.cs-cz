---
title: "Sestavení nelze vygenerovat: &lt;chybová zpráva&gt;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords: BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9dcf3d4bec379faa5783ca17847b91f9739df598
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="unable-to-emit-assembly-lterror-messagegt"></a><span data-ttu-id="25d89-102">Sestavení nelze vygenerovat: &lt;chybová zpráva&gt;</span><span class="sxs-lookup"><span data-stu-id="25d89-102">Unable to emit assembly: &lt;error message&gt;</span></span>
<span data-ttu-id="25d89-103">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompilátoru volá Linker sestavení (Al.exe, také známé jako Alink) ke generování sestavení s manifestu, s linkeru reporting chybu ve fázi emisí vytváření sestavení.</span><span class="sxs-lookup"><span data-stu-id="25d89-103">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest, with the linker reporting an error in the emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="25d89-104">**ID chyby:** BC30145</span><span class="sxs-lookup"><span data-stu-id="25d89-104">**Error ID:** BC30145</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="25d89-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="25d89-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="25d89-106">Prověřením uvozovkách chybové zprávy a podívejte se téma [Nástroj Al.exe chyby a upozornění](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) pro další vysvětlení a doporučení.</span><span class="sxs-lookup"><span data-stu-id="25d89-106">Examine the quoted error message and consult the topic [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) for further explanation and advice.</span></span>  
  
2.  <span data-ttu-id="25d89-107">Zkuste se sestavení ručně, buď pomocí [Al.exe (Linker sestavení)](https://msdn.microsoft.com/library/c405shex) nebo [Sn.exe (nástroj silným názvem)](https://msdn.microsoft.com/library/k5b5tt23).</span><span class="sxs-lookup"><span data-stu-id="25d89-107">Try signing the assembly manually, using either the [Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex) or the [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23).</span></span>  
  
3.  <span data-ttu-id="25d89-108">Pokud potíže potrvají, shromažďovat informace o okolnostech a upozornění služby Microsoft Product Support Services.</span><span class="sxs-lookup"><span data-stu-id="25d89-108">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
### <a name="to-sign-the-assembly-manually"></a><span data-ttu-id="25d89-109">K podepsání sestavení ručně</span><span class="sxs-lookup"><span data-stu-id="25d89-109">To sign the assembly manually</span></span>  
  
1.  <span data-ttu-id="25d89-110">Použití [Sn.exe (nástroj silným názvem)](https://msdn.microsoft.com/library/k5b5tt23) k vytvoření souboru pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="25d89-110">Use the [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23) to create a public/private key pair file.</span></span>  
  
     <span data-ttu-id="25d89-111">Tento soubor má příponu .snk.</span><span class="sxs-lookup"><span data-stu-id="25d89-111">This file has a .snk extension.</span></span>  
  
2.  <span data-ttu-id="25d89-112">Odstraňte odkaz na modelu COM, která generuje chybu ze svého projektu.</span><span class="sxs-lookup"><span data-stu-id="25d89-112">Delete the COM reference that is generating the error from your project.</span></span>  
  
3.  <span data-ttu-id="25d89-113">Z Windows **spustit** nabídky, přejděte na příkaz **programy**, přejděte na příkaz **Microsoft Visual Studio 2008**, přejděte na příkaz **nástroje sady Visual Studio**, a pak klikněte na tlačítko **příkazový řádek sady Visual Studio 2008**.</span><span class="sxs-lookup"><span data-stu-id="25d89-113">From the Windows **Start** menu, point to **Programs**, point to **Microsoft Visual Studio 2008**, point to **Visual Studio Tools**, and then click **Visual Studio 2008 Command Prompt**.</span></span>  
  
4.  <span data-ttu-id="25d89-114">Přesunout do adresáře, kam chcete umístit vaše obálku sestavení.</span><span class="sxs-lookup"><span data-stu-id="25d89-114">Move to the directory where you want to place your assembly wrapper.</span></span>  
  
5.  <span data-ttu-id="25d89-115">Zadejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="25d89-115">Type the following code.</span></span>  
  
    ```  
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>  
    ```  
  
     <span data-ttu-id="25d89-116">Příklad kódu, který můžete zadat by následující.</span><span class="sxs-lookup"><span data-stu-id="25d89-116">An example of the code you might enter would be the following.</span></span>  
  
    ```  
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"  
    ```  
  
     <span data-ttu-id="25d89-117">Pokud cesta nebo soubor obsahuje mezery, použijte uvozovky (").</span><span class="sxs-lookup"><span data-stu-id="25d89-117">Use double quotation marks (") if a path or file contains spaces.</span></span>  
  
6.  <span data-ttu-id="25d89-118">V [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], přidejte sestavení .NET odkaz na soubor, který jste právě vytvořili.</span><span class="sxs-lookup"><span data-stu-id="25d89-118">In [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], add a .NET Assembly reference to the file you just created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25d89-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="25d89-119">See Also</span></span>  
 [<span data-ttu-id="25d89-120">Al.exe (Linker sestavení)</span><span class="sxs-lookup"><span data-stu-id="25d89-120">Al.exe (Assembly Linker)</span></span>](https://msdn.microsoft.com/library/c405shex)  
 [<span data-ttu-id="25d89-121">Al.exe nástroj chyby a upozornění</span><span class="sxs-lookup"><span data-stu-id="25d89-121">Al.exe Tool Errors and Warnings</span></span>](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)  
 [<span data-ttu-id="25d89-122">Sn.exe (nástroj pro silný název)</span><span class="sxs-lookup"><span data-stu-id="25d89-122">Sn.exe (Strong Name Tool)</span></span>](https://msdn.microsoft.com/library/k5b5tt23)  
 [<span data-ttu-id="25d89-123">Postupy: vytvoření páru veřejného a privátního klíče RSA</span><span class="sxs-lookup"><span data-stu-id="25d89-123">How to: Create a Public-Private Key Pair</span></span>](http://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114)  
 [<span data-ttu-id="25d89-124">Kontaktujte nás</span><span class="sxs-lookup"><span data-stu-id="25d89-124">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
