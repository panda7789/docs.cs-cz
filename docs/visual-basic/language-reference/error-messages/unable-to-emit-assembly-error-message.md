---
title: 'Sestavení nelze vygenerovat: <error message>'
ms.date: 08/14/2018
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
ms.openlocfilehash: 530aaee40be92bf72ee4b83b4141108e9b81c8a1
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70968857"
---
# <a name="unable-to-emit-assembly-error-message"></a><span data-ttu-id="02af6-102">Nelze vygenerovat sestavení: \<chybová zpráva ></span><span class="sxs-lookup"><span data-stu-id="02af6-102">Unable to emit assembly: \<error message></span></span>

<span data-ttu-id="02af6-103">Kompilátor Visual Basic volá linker sestavení (*Al. exe*, označovaný také jako ALink) pro generování sestavení s manifestem a linker hlásí chybu ve fázi emisí pro vytvoření sestavení.</span><span class="sxs-lookup"><span data-stu-id="02af6-103">The Visual Basic compiler calls the Assembly Linker (*Al.exe*, also known as Alink) to generate an assembly with a manifest, and the linker reports an error in the emission stage of creating the assembly.</span></span>

<span data-ttu-id="02af6-104">**ID chyby:** BC30145</span><span class="sxs-lookup"><span data-stu-id="02af6-104">**Error ID:** BC30145</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="02af6-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="02af6-105">To correct this error</span></span>

1. <span data-ttu-id="02af6-106">Projděte si chybovou zprávu v uvozovkách a vyhledejte další vysvětlení a Rady v tématu [Al. exe](../../../framework/tools/al-exe-assembly-linker.md) .</span><span class="sxs-lookup"><span data-stu-id="02af6-106">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) for further explanation and advice.</span></span>

2. <span data-ttu-id="02af6-107">Zkuste podepsat sestavení ručně pomocí nástroje [Al. exe](../../../framework/tools/al-exe-assembly-linker.md) nebo [sn. exe (Nástroj pro silný název)](../../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="02af6-107">Try signing the assembly manually, using either the [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) or the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md).</span></span>

3. <span data-ttu-id="02af6-108">Pokud chyba přetrvává, shromážděte informace o okolnostech a upozorněte služby podpory společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="02af6-108">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>

### <a name="to-sign-the-assembly-manually"></a><span data-ttu-id="02af6-109">Postup ručního podepsání sestavení</span><span class="sxs-lookup"><span data-stu-id="02af6-109">To sign the assembly manually</span></span>

1. <span data-ttu-id="02af6-110">K vytvoření souboru dvojice veřejného a privátního klíče použijte [Nástroj Sn. exe (Strong Name)](../../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="02af6-110">Use the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)) to create a public/private key pair file.</span></span>

   <span data-ttu-id="02af6-111">Tento soubor má příponu *. snk* .</span><span class="sxs-lookup"><span data-stu-id="02af6-111">This file has an *.snk* extension.</span></span>

2. <span data-ttu-id="02af6-112">Odstraňte odkaz modelu COM, který generuje chybu z vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="02af6-112">Delete the COM reference that is generating the error from your project.</span></span>

3. <span data-ttu-id="02af6-113">Otevřete [Developer Command Prompt pro Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="02af6-113">Open the [Developer Command Prompt for Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md).</span></span>

   <span data-ttu-id="02af6-114">Ve Windows 10 zadejte **Developer Command Prompt** do vyhledávacího pole na hlavním panelu.</span><span class="sxs-lookup"><span data-stu-id="02af6-114">In Windows 10, enter **Developer command prompt** into the search box on the task bar.</span></span> <span data-ttu-id="02af6-115">Pak v seznamu výsledků vyberte **Developer Command Prompt pro VS 2017** .</span><span class="sxs-lookup"><span data-stu-id="02af6-115">Then, select **Developer Command Prompt for VS 2017** from the results list.</span></span>

4. <span data-ttu-id="02af6-116">Změňte adresář na adresář, do kterého chcete umístit obálku sestavení.</span><span class="sxs-lookup"><span data-stu-id="02af6-116">Change the directory to the directory where you want to place your assembly wrapper.</span></span>

5. <span data-ttu-id="02af6-117">Zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="02af6-117">Enter the following command:</span></span>

    ```cmd
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>
    ```

   <span data-ttu-id="02af6-118">Příklad skutečného příkazu, který byste mohli zadat, je:</span><span class="sxs-lookup"><span data-stu-id="02af6-118">An example of the actual command you might enter is:</span></span>

    ```cmd
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"
    ```

   > [!TIP]
   > <span data-ttu-id="02af6-119">Pokud cesta nebo soubor obsahuje mezery, použijte dvojité uvozovky.</span><span class="sxs-lookup"><span data-stu-id="02af6-119">Use double quotation marks if a path or file contains spaces.</span></span>

6. <span data-ttu-id="02af6-120">V aplikaci Visual Studio přidejte odkaz na sestavení .NET do souboru, který jste právě vytvořili.</span><span class="sxs-lookup"><span data-stu-id="02af6-120">In Visual Studio, add a .NET Assembly reference to the file you just created.</span></span>

## <a name="see-also"></a><span data-ttu-id="02af6-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="02af6-121">See also</span></span>

- [<span data-ttu-id="02af6-122">Al.exe</span><span class="sxs-lookup"><span data-stu-id="02af6-122">Al.exe</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="02af6-123">Sn.exe (nástroj pro silný název)</span><span class="sxs-lookup"><span data-stu-id="02af6-123">Sn.exe (Strong Name Tool)</span></span>](../../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="02af6-124">Postupy: Vytvoření páru klíčů veřejného a soukromého</span><span class="sxs-lookup"><span data-stu-id="02af6-124">How to: Create a Public-Private Key Pair</span></span>](../../../standard/assembly/create-public-private-key-pair.md)
- [<span data-ttu-id="02af6-125">Kontaktujte nás</span><span class="sxs-lookup"><span data-stu-id="02af6-125">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
