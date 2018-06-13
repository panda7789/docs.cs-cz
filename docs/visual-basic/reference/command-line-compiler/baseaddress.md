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
ms.openlocfilehash: 6331a55bb1d20b5804605db103dcfd2997e348d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650147"
---
# <a name="-baseaddress"></a><span data-ttu-id="c91dd-102">-baseaddress</span><span class="sxs-lookup"><span data-stu-id="c91dd-102">-baseaddress</span></span>
<span data-ttu-id="c91dd-103">Určuje výchozí základní adresu při vytváření knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="c91dd-103">Specifies a default base address when creating a DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c91dd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c91dd-104">Syntax</span></span>  
  
```  
-baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="c91dd-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="c91dd-105">Arguments</span></span>  
  
|<span data-ttu-id="c91dd-106">Termín</span><span class="sxs-lookup"><span data-stu-id="c91dd-106">Term</span></span>|<span data-ttu-id="c91dd-107">Definice</span><span class="sxs-lookup"><span data-stu-id="c91dd-107">Definition</span></span>|  
|---|---|  
|`address`|<span data-ttu-id="c91dd-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="c91dd-108">Required.</span></span> <span data-ttu-id="c91dd-109">Základní adresa pro knihovnu DLL.</span><span class="sxs-lookup"><span data-stu-id="c91dd-109">The base address for the DLL.</span></span> <span data-ttu-id="c91dd-110">Tato adresa musí být zadán jako o hexadecimální číslo.</span><span class="sxs-lookup"><span data-stu-id="c91dd-110">This address must be specified as a hexadecimal number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c91dd-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c91dd-111">Remarks</span></span>  
 <span data-ttu-id="c91dd-112">Výchozí základní adresy knihovny DLL se nastavuje pomocí [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c91dd-112">The default base address for a DLL is set by the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span>  
  
 <span data-ttu-id="c91dd-113">Upozorňujeme, že se zaokrouhlí na slovo nižší pořadí v tuto adresu.</span><span class="sxs-lookup"><span data-stu-id="c91dd-113">Be aware that the lower-order word in this address is rounded.</span></span> <span data-ttu-id="c91dd-114">Například pokud zadáte 0x11110001, je zaokrouhlen 0x11110000.</span><span class="sxs-lookup"><span data-stu-id="c91dd-114">For example, if you specify 0x11110001, it is rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="c91dd-115">Chcete-li dokončit proces podepisování pro knihovny DLL, použijte `–R` – možnost nástroje silné názvy (Sn.exe).</span><span class="sxs-lookup"><span data-stu-id="c91dd-115">To complete the signing process for a DLL, use the `–R` option of the Strong Naming tool (Sn.exe).</span></span>  
  
 <span data-ttu-id="c91dd-116">Tato možnost je ignorována, pokud cíl není knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="c91dd-116">This option is ignored if the target is not a DLL.</span></span>  
  
|<span data-ttu-id="c91dd-117">Chcete-li nastavit - baseaddress v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c91dd-117">To set -baseaddress in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="c91dd-118">1.  Máte projekt vybraný v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="c91dd-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="c91dd-119">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="c91dd-119">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="c91dd-120">2.  Klikněte **zkompilovat** kartě.</span><span class="sxs-lookup"><span data-stu-id="c91dd-120">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="c91dd-121">3.  Klikněte na tlačítko **rozšířené**.</span><span class="sxs-lookup"><span data-stu-id="c91dd-121">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="c91dd-122">4.  Změňte hodnotu v **základní adresy knihovny DLL:** pole.</span><span class="sxs-lookup"><span data-stu-id="c91dd-122">4.  Modify the value in the **DLL base address:** box.</span></span> <span data-ttu-id="c91dd-123">**Poznámka:** **základní adresy knihovny DLL:** pole je jen pro čtení, není-li cílem knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="c91dd-123">**Note:**      The **DLL base address:** box is read-only unless the target is a DLL.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c91dd-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="c91dd-124">See Also</span></span>  
 [<span data-ttu-id="c91dd-125">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="c91dd-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="c91dd-126">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c91dd-126">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="c91dd-127">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="c91dd-127">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 <span data-ttu-id="c91dd-128">[Sn.exe (nástroj pro silný název)] [Sn.exe (nástroj pro silný název)](../../../framework/tools/sn-exe-strong-name-tool.md))</span><span class="sxs-lookup"><span data-stu-id="c91dd-128">[Sn.exe (Strong Name Tool)][Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md))</span></span>
