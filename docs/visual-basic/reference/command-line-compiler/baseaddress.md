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
ms.openlocfilehash: e8dfe95ef3385635f5839ecc96047911544a256e
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591446"
---
# <a name="-baseaddress"></a><span data-ttu-id="44c2f-102">-baseaddress</span><span class="sxs-lookup"><span data-stu-id="44c2f-102">-baseaddress</span></span>
<span data-ttu-id="44c2f-103">Určuje výchozí základní adresa, při vytváření knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="44c2f-103">Specifies a default base address when creating a DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44c2f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44c2f-104">Syntax</span></span>  
  
```  
-baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="44c2f-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="44c2f-105">Arguments</span></span>  
  
|<span data-ttu-id="44c2f-106">Termín</span><span class="sxs-lookup"><span data-stu-id="44c2f-106">Term</span></span>|<span data-ttu-id="44c2f-107">Definice</span><span class="sxs-lookup"><span data-stu-id="44c2f-107">Definition</span></span>|  
|---|---|  
|`address`|<span data-ttu-id="44c2f-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="44c2f-108">Required.</span></span> <span data-ttu-id="44c2f-109">Základní adresa pro knihovnu DLL.</span><span class="sxs-lookup"><span data-stu-id="44c2f-109">The base address for the DLL.</span></span> <span data-ttu-id="44c2f-110">Tato adresa musí být zadán jako šestnáctkové číslo.</span><span class="sxs-lookup"><span data-stu-id="44c2f-110">This address must be specified as a hexadecimal number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44c2f-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="44c2f-111">Remarks</span></span>  
 <span data-ttu-id="44c2f-112">Výchozí základní adresa knihovny DLL je nastavena pomocí rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="44c2f-112">The default base address for a DLL is set by the .NET Framework.</span></span>  
  
 <span data-ttu-id="44c2f-113">Mějte na paměti, že se zaokrouhlí nižší řád slova v této adrese.</span><span class="sxs-lookup"><span data-stu-id="44c2f-113">Be aware that the lower-order word in this address is rounded.</span></span> <span data-ttu-id="44c2f-114">Například pokud chcete zadat 0x11110001, to se zaokrouhlí na 0x11110000.</span><span class="sxs-lookup"><span data-stu-id="44c2f-114">For example, if you specify 0x11110001, it is rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="44c2f-115">Chcete-li dokončit proces podepisování pro knihovnu DLL, použijte `–R` – možnost Nástroje pro silné pojmenovávání (Sn.exe).</span><span class="sxs-lookup"><span data-stu-id="44c2f-115">To complete the signing process for a DLL, use the `–R` option of the Strong Naming tool (Sn.exe).</span></span>  
  
 <span data-ttu-id="44c2f-116">Tato možnost se ignoruje, pokud cíl není knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="44c2f-116">This option is ignored if the target is not a DLL.</span></span>  
  
|<span data-ttu-id="44c2f-117">Chcete-li nastavit - baseaddress v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="44c2f-117">To set -baseaddress in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="44c2f-118">1.  Mají projekt vybraný v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="44c2f-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="44c2f-119">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="44c2f-119">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="44c2f-120">2.  Klikněte na tlačítko **kompilaci** kartu.</span><span class="sxs-lookup"><span data-stu-id="44c2f-120">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="44c2f-121">3.  Klikněte na tlačítko **Advanced**.</span><span class="sxs-lookup"><span data-stu-id="44c2f-121">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="44c2f-122">4.  Upravte hodnotu v **základní adresa knihovny DLL:** pole.</span><span class="sxs-lookup"><span data-stu-id="44c2f-122">4.  Modify the value in the **DLL base address:** box.</span></span> <span data-ttu-id="44c2f-123">**Poznámka:**      **Základní adresa knihovny DLL:** pole je jen pro čtení, pokud cíl není knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="44c2f-123">**Note:**      The **DLL base address:** box is read-only unless the target is a DLL.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="44c2f-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="44c2f-124">See also</span></span>

- [<span data-ttu-id="44c2f-125">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="44c2f-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="44c2f-126">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44c2f-126">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="44c2f-127">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="44c2f-127">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- <span data-ttu-id="44c2f-128">[Sn.exe (nástroj pro silný název)](../../../framework/tools/sn-exe-strong-name-tool.md))</span><span class="sxs-lookup"><span data-stu-id="44c2f-128">[Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md))</span></span>
