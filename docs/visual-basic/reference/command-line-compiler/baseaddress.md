---
title: -baseaddress
ms.date: 08/09/2018
f1_keywords:
- /baseaddress
- baseaddress
helpviewer_keywords:
- -baseaddress compiler option [Visual Basic]
- /baseaddress compiler option [Visual Basic]
- baseaddress compiler option [Visual Basic]
ms.assetid: c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47
ms.openlocfilehash: 6ee842dbe65cbd9d147e77ec523a2b031d303738
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002386"
---
# <a name="-baseaddress"></a><span data-ttu-id="1db8b-102">-baseaddress</span><span class="sxs-lookup"><span data-stu-id="1db8b-102">-baseaddress</span></span>
<span data-ttu-id="1db8b-103">Určuje výchozí základní adresu při vytváření knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="1db8b-103">Specifies a default base address when creating a DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1db8b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1db8b-104">Syntax</span></span>  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="1db8b-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="1db8b-105">Arguments</span></span>  
  
|<span data-ttu-id="1db8b-106">Termín</span><span class="sxs-lookup"><span data-stu-id="1db8b-106">Term</span></span>|<span data-ttu-id="1db8b-107">Definice</span><span class="sxs-lookup"><span data-stu-id="1db8b-107">Definition</span></span>|  
|---|---|  
|`address`|<span data-ttu-id="1db8b-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="1db8b-108">Required.</span></span> <span data-ttu-id="1db8b-109">Základní adresa knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="1db8b-109">The base address for the DLL.</span></span> <span data-ttu-id="1db8b-110">Tato adresa musí být zadána jako šestnáctkové číslo.</span><span class="sxs-lookup"><span data-stu-id="1db8b-110">This address must be specified as a hexadecimal number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1db8b-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1db8b-111">Remarks</span></span>  
 <span data-ttu-id="1db8b-112">Výchozí základní adresa pro knihovnu DLL je nastavena .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1db8b-112">The default base address for a DLL is set by the .NET Framework.</span></span>  
  
 <span data-ttu-id="1db8b-113">Uvědomte si, že slovo v této adrese se zaokrouhluje na zaoblené.</span><span class="sxs-lookup"><span data-stu-id="1db8b-113">Be aware that the lower-order word in this address is rounded.</span></span> <span data-ttu-id="1db8b-114">Pokud například zadáte 0x11110001, je zaokrouhlena na 0x11110000.</span><span class="sxs-lookup"><span data-stu-id="1db8b-114">For example, if you specify 0x11110001, it is rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="1db8b-115">Chcete-li dokončit proces podepisování pro knihovnu DLL, použijte možnost `–R` nástroje pro vytváření silných názvů (Sn. exe).</span><span class="sxs-lookup"><span data-stu-id="1db8b-115">To complete the signing process for a DLL, use the `–R` option of the Strong Naming tool (Sn.exe).</span></span>  
  
 <span data-ttu-id="1db8b-116">Tato možnost je ignorována, pokud cíl není knihovna DLL.</span><span class="sxs-lookup"><span data-stu-id="1db8b-116">This option is ignored if the target is not a DLL.</span></span>  
  
|<span data-ttu-id="1db8b-117">Nastavení-BaseAddress v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1db8b-117">To set -baseaddress in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="1db8b-118">1. v **Průzkumník řešení**mít vybraný projekt.</span><span class="sxs-lookup"><span data-stu-id="1db8b-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="1db8b-119">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="1db8b-119">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="1db8b-120">2. klikněte na kartu **kompilovat** .</span><span class="sxs-lookup"><span data-stu-id="1db8b-120">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="1db8b-121">3. klikněte na tlačítko **Upřesnit**.</span><span class="sxs-lookup"><span data-stu-id="1db8b-121">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="1db8b-122">4. upravte hodnotu v poli **základní adresa knihovny DLL:** .</span><span class="sxs-lookup"><span data-stu-id="1db8b-122">4.  Modify the value in the **DLL base address:** box.</span></span> <span data-ttu-id="1db8b-123">**Poznámka:**      **Základní adresa knihovny DLL:** box je jen pro čtení, pokud cíl není knihovna DLL.</span><span class="sxs-lookup"><span data-stu-id="1db8b-123">**Note:**      The **DLL base address:** box is read-only unless the target is a DLL.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1db8b-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1db8b-124">See also</span></span>

- [<span data-ttu-id="1db8b-125">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="1db8b-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="1db8b-126">-Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1db8b-126">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="1db8b-127">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="1db8b-127">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- <span data-ttu-id="1db8b-128">[Sn. exe (Nástroj pro silný název)](../../../framework/tools/sn-exe-strong-name-tool.md))</span><span class="sxs-lookup"><span data-stu-id="1db8b-128">[Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md))</span></span>
