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
ms.openlocfilehash: 0550e4ad700494c8773a5d9b5b282dfa116adfed
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58813363"
---
# <a name="-baseaddress"></a><span data-ttu-id="d2a9c-102">-baseaddress</span><span class="sxs-lookup"><span data-stu-id="d2a9c-102">-baseaddress</span></span>
<span data-ttu-id="d2a9c-103">Určuje výchozí základní adresa, při vytváření knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="d2a9c-103">Specifies a default base address when creating a DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2a9c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2a9c-104">Syntax</span></span>  
  
```  
-baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="d2a9c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d2a9c-105">Arguments</span></span>  
  
|<span data-ttu-id="d2a9c-106">Termín</span><span class="sxs-lookup"><span data-stu-id="d2a9c-106">Term</span></span>|<span data-ttu-id="d2a9c-107">Definice</span><span class="sxs-lookup"><span data-stu-id="d2a9c-107">Definition</span></span>|  
|---|---|  
|`address`|<span data-ttu-id="d2a9c-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="d2a9c-108">Required.</span></span> <span data-ttu-id="d2a9c-109">Základní adresa pro knihovnu DLL.</span><span class="sxs-lookup"><span data-stu-id="d2a9c-109">The base address for the DLL.</span></span> <span data-ttu-id="d2a9c-110">Tato adresa musí být zadán jako šestnáctkové číslo.</span><span class="sxs-lookup"><span data-stu-id="d2a9c-110">This address must be specified as a hexadecimal number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2a9c-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d2a9c-111">Remarks</span></span>  
 <span data-ttu-id="d2a9c-112">Výchozí základní adresa pro knihovnu DLL se nastavuje [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d2a9c-112">The default base address for a DLL is set by the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span>  
  
 <span data-ttu-id="d2a9c-113">Mějte na paměti, že se zaokrouhlí nižší řád slova v této adrese.</span><span class="sxs-lookup"><span data-stu-id="d2a9c-113">Be aware that the lower-order word in this address is rounded.</span></span> <span data-ttu-id="d2a9c-114">Například pokud chcete zadat 0x11110001, to se zaokrouhlí na 0x11110000.</span><span class="sxs-lookup"><span data-stu-id="d2a9c-114">For example, if you specify 0x11110001, it is rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="d2a9c-115">Chcete-li dokončit proces podepisování pro knihovnu DLL, použijte `–R` – možnost Nástroje pro silné pojmenovávání (Sn.exe).</span><span class="sxs-lookup"><span data-stu-id="d2a9c-115">To complete the signing process for a DLL, use the `–R` option of the Strong Naming tool (Sn.exe).</span></span>  
  
 <span data-ttu-id="d2a9c-116">Tato možnost se ignoruje, pokud cíl není knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="d2a9c-116">This option is ignored if the target is not a DLL.</span></span>  
  
|<span data-ttu-id="d2a9c-117">Chcete-li nastavit - baseaddress v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d2a9c-117">To set -baseaddress in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="d2a9c-118">1.  Mají projekt vybraný v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="d2a9c-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="d2a9c-119">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="d2a9c-119">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="d2a9c-120">2.  Klikněte na tlačítko **kompilaci** kartu.</span><span class="sxs-lookup"><span data-stu-id="d2a9c-120">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="d2a9c-121">3.  Klikněte na tlačítko **Advanced**.</span><span class="sxs-lookup"><span data-stu-id="d2a9c-121">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="d2a9c-122">4.  Upravte hodnotu v **základní adresa knihovny DLL:** pole.</span><span class="sxs-lookup"><span data-stu-id="d2a9c-122">4.  Modify the value in the **DLL base address:** box.</span></span> <span data-ttu-id="d2a9c-123">**Poznámka:**      **Základní adresa knihovny DLL:** pole je jen pro čtení, pokud cíl není knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="d2a9c-123">**Note:**      The **DLL base address:** box is read-only unless the target is a DLL.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d2a9c-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d2a9c-124">See also</span></span>

- [<span data-ttu-id="d2a9c-125">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="d2a9c-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="d2a9c-126">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2a9c-126">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="d2a9c-127">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="d2a9c-127">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- <span data-ttu-id="d2a9c-128">[Sn.exe (nástroj pro silný název)](../../../framework/tools/sn-exe-strong-name-tool.md))</span><span class="sxs-lookup"><span data-stu-id="d2a9c-128">[Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md))</span></span>
