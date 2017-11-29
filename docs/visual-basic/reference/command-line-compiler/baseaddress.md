---
title: /baseaddress
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- /baseaddress
- baseaddress
helpviewer_keywords:
- -baseaddress compiler option [Visual Basic]
- /baseaddress compiler option [Visual Basic]
- baseaddress compiler option [Visual Basic]
ms.assetid: c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8be88bf4834ca58b1fe708eb1ef7188c583fef0f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="baseaddress"></a><span data-ttu-id="5ad66-102">/baseaddress</span><span class="sxs-lookup"><span data-stu-id="5ad66-102">/baseaddress</span></span>
<span data-ttu-id="5ad66-103">Určuje výchozí základní adresu při vytváření knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="5ad66-103">Specifies a default base address when creating a DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ad66-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ad66-104">Syntax</span></span>  
  
```  
/baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="5ad66-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="5ad66-105">Arguments</span></span>  
  
|<span data-ttu-id="5ad66-106">Termín</span><span class="sxs-lookup"><span data-stu-id="5ad66-106">Term</span></span>|<span data-ttu-id="5ad66-107">Definice</span><span class="sxs-lookup"><span data-stu-id="5ad66-107">Definition</span></span>|  
|---|---|  
|`address`|<span data-ttu-id="5ad66-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="5ad66-108">Required.</span></span> <span data-ttu-id="5ad66-109">Základní adresa pro knihovnu DLL.</span><span class="sxs-lookup"><span data-stu-id="5ad66-109">The base address for the DLL.</span></span> <span data-ttu-id="5ad66-110">Tato adresa musí být zadán jako o hexadecimální číslo.</span><span class="sxs-lookup"><span data-stu-id="5ad66-110">This address must be specified as a hexadecimal number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ad66-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5ad66-111">Remarks</span></span>  
 <span data-ttu-id="5ad66-112">Výchozí základní adresy knihovny DLL se nastavuje pomocí [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5ad66-112">The default base address for a DLL is set by the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span>  
  
 <span data-ttu-id="5ad66-113">Upozorňujeme, že se zaokrouhlí na slovo nižší pořadí v tuto adresu.</span><span class="sxs-lookup"><span data-stu-id="5ad66-113">Be aware that the lower-order word in this address is rounded.</span></span> <span data-ttu-id="5ad66-114">Například pokud zadáte 0x11110001, je zaokrouhlen 0x11110000.</span><span class="sxs-lookup"><span data-stu-id="5ad66-114">For example, if you specify 0x11110001, it is rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="5ad66-115">Chcete-li dokončit proces podepisování pro knihovny DLL, použijte `–R` – možnost nástroje silné názvy (Sn.exe).</span><span class="sxs-lookup"><span data-stu-id="5ad66-115">To complete the signing process for a DLL, use the `–R` option of the Strong Naming tool (Sn.exe).</span></span>  
  
 <span data-ttu-id="5ad66-116">Tato možnost je ignorována, pokud cíl není knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="5ad66-116">This option is ignored if the target is not a DLL.</span></span>  
  
|<span data-ttu-id="5ad66-117">Chcete-li nastavit/BaseAddress v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5ad66-117">To set /baseaddress in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="5ad66-118">1.  Máte projekt vybraný v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="5ad66-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="5ad66-119">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="5ad66-119">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="5ad66-120">Další informace najdete v tématu [Úvod do Návrhář projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="5ad66-120">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="5ad66-121">2.  Klikněte **zkompilovat** kartě.</span><span class="sxs-lookup"><span data-stu-id="5ad66-121">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="5ad66-122">3.  Klikněte na tlačítko **rozšířené**.</span><span class="sxs-lookup"><span data-stu-id="5ad66-122">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="5ad66-123">4.  Změňte hodnotu v **základní adresy knihovny DLL:** pole.</span><span class="sxs-lookup"><span data-stu-id="5ad66-123">4.  Modify the value in the **DLL base address:** box.</span></span> <span data-ttu-id="5ad66-124">**Poznámka:** **základní adresy knihovny DLL:** pole je jen pro čtení, není-li cílem knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="5ad66-124">**Note:**      The **DLL base address:** box is read-only unless the target is a DLL.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5ad66-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="5ad66-125">See Also</span></span>  
 [<span data-ttu-id="5ad66-126">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="5ad66-126">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="5ad66-127">/ target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5ad66-127">/target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="5ad66-128">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="5ad66-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="5ad66-129">Sn.exe (nástroj pro silný název)</span><span class="sxs-lookup"><span data-stu-id="5ad66-129">Sn.exe (Strong Name Tool)</span></span>](https://msdn.microsoft.com/library/k5b5tt23)
