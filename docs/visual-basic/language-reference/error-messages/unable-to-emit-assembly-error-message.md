---
title: 'Sestavení nelze vygenerovat: <error message>'
ms.date: 08/14/2018
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
ms.openlocfilehash: d564f4f4462a691504297d65575956c5f06691ca
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61936276"
---
# <a name="unable-to-emit-assembly-error-message"></a><span data-ttu-id="2ab9c-102">Sestavení nelze vygenerovat: \<chybová zpráva ></span><span class="sxs-lookup"><span data-stu-id="2ab9c-102">Unable to emit assembly: \<error message></span></span>

<span data-ttu-id="2ab9c-103">Kompilátor jazyka Visual Basic volá Assembly Linker (*Al.exe*, označovaný také jako Alink) ke generování manifestu a propojovací program sestavení nahlásí chybu ve fázi emisí vytváření sestavení.</span><span class="sxs-lookup"><span data-stu-id="2ab9c-103">The Visual Basic compiler calls the Assembly Linker (*Al.exe*, also known as Alink) to generate an assembly with a manifest, and the linker reports an error in the emission stage of creating the assembly.</span></span>

<span data-ttu-id="2ab9c-104">**ID chyby:** BC30145</span><span class="sxs-lookup"><span data-stu-id="2ab9c-104">**Error ID:** BC30145</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="2ab9c-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="2ab9c-105">To correct this error</span></span>

1. <span data-ttu-id="2ab9c-106">Zkontrolujte v uvozovkách chybovou zprávu a najdete v tématu [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) pro další vysvětlení a poradenství.</span><span class="sxs-lookup"><span data-stu-id="2ab9c-106">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) for further explanation and advice.</span></span>

2. <span data-ttu-id="2ab9c-107">Zkuste se sestavení ručně, buď pomocí [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) nebo [Sn.exe (nástroj Strong Name)](../../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="2ab9c-107">Try signing the assembly manually, using either the [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) or the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md).</span></span>

3. <span data-ttu-id="2ab9c-108">Pokud potíže potrvají, shromážděte informace o okolnostech a upozornit Microsoft Product Support Services.</span><span class="sxs-lookup"><span data-stu-id="2ab9c-108">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>

### <a name="to-sign-the-assembly-manually"></a><span data-ttu-id="2ab9c-109">K podepsání sestavení ručně</span><span class="sxs-lookup"><span data-stu-id="2ab9c-109">To sign the assembly manually</span></span>

1. <span data-ttu-id="2ab9c-110">Použít [Sn.exe (nástroj Strong Name)](../../../framework/tools/sn-exe-strong-name-tool.md)) k vytvoření souboru pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="2ab9c-110">Use the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)) to create a public/private key pair file.</span></span>

   <span data-ttu-id="2ab9c-111">Tento soubor má *.snk* rozšíření.</span><span class="sxs-lookup"><span data-stu-id="2ab9c-111">This file has an *.snk* extension.</span></span>

2. <span data-ttu-id="2ab9c-112">Odstraňte odkaz modelu COM, který generuje chybu z projektu.</span><span class="sxs-lookup"><span data-stu-id="2ab9c-112">Delete the COM reference that is generating the error from your project.</span></span>

3. <span data-ttu-id="2ab9c-113">Otevřít [Developer Command Prompt pro sadu Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="2ab9c-113">Open the [Developer Command Prompt for Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md).</span></span>

   <span data-ttu-id="2ab9c-114">Ve Windows 10, zadejte **příkazový řádek pro vývojáře** do vyhledávacího pole na hlavním panelu.</span><span class="sxs-lookup"><span data-stu-id="2ab9c-114">In Windows 10, enter **Developer command prompt** into the search box on the task bar.</span></span> <span data-ttu-id="2ab9c-115">Vyberte **Developer Command Prompt for VS 2017** ze seznamu výsledků.</span><span class="sxs-lookup"><span data-stu-id="2ab9c-115">Then, select **Developer Command Prompt for VS 2017** from the results list.</span></span>

4. <span data-ttu-id="2ab9c-116">Změňte adresář na adresář, kam chcete umístit vaše sestavení obálky.</span><span class="sxs-lookup"><span data-stu-id="2ab9c-116">Change the directory to the directory where you want to place your assembly wrapper.</span></span>

5. <span data-ttu-id="2ab9c-117">Zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="2ab9c-117">Enter the following command:</span></span>

    ```cmd
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>
    ```

   <span data-ttu-id="2ab9c-118">Je například skutečný příkaz, který můžete například zadat:</span><span class="sxs-lookup"><span data-stu-id="2ab9c-118">An example of the actual command you might enter is:</span></span>

    ```cmd
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"
    ```

   > [!TIP]
   > <span data-ttu-id="2ab9c-119">Pokud cestu nebo soubor obsahuje mezery, použijte uvozovky.</span><span class="sxs-lookup"><span data-stu-id="2ab9c-119">Use double quotation marks if a path or file contains spaces.</span></span>

6. <span data-ttu-id="2ab9c-120">V sadě Visual Studio přidejte odkaz sestavení .NET do souboru, který jste právě vytvořili.</span><span class="sxs-lookup"><span data-stu-id="2ab9c-120">In Visual Studio, add a .NET Assembly reference to the file you just created.</span></span>

## <a name="see-also"></a><span data-ttu-id="2ab9c-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2ab9c-121">See also</span></span>

- [<span data-ttu-id="2ab9c-122">Al.exe</span><span class="sxs-lookup"><span data-stu-id="2ab9c-122">Al.exe</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="2ab9c-123">Sn.exe (nástroj pro silný název)</span><span class="sxs-lookup"><span data-stu-id="2ab9c-123">Sn.exe (Strong Name Tool)</span></span>](../../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="2ab9c-124">Postupy: Vytvoření páru veřejného a privátního klíče</span><span class="sxs-lookup"><span data-stu-id="2ab9c-124">How to: Create a Public-Private Key Pair</span></span>](../../../framework/app-domains/how-to-create-a-public-private-key-pair.md)
- [<span data-ttu-id="2ab9c-125">Kontaktujte nás</span><span class="sxs-lookup"><span data-stu-id="2ab9c-125">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)