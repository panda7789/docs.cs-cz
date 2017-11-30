---
title: /nowarn
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8da27ea2f9f0a4d370928d70cda1a796b822d97c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="nowarn"></a><span data-ttu-id="00cfc-102">/nowarn</span><span class="sxs-lookup"><span data-stu-id="00cfc-102">/nowarn</span></span>
<span data-ttu-id="00cfc-103">Potlačí schopnost kompilátoru generovat upozornění.</span><span class="sxs-lookup"><span data-stu-id="00cfc-103">Suppresses the compiler's ability to generate warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00cfc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00cfc-104">Syntax</span></span>  
  
```  
/nowarn[:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="00cfc-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="00cfc-105">Arguments</span></span>  
  
|<span data-ttu-id="00cfc-106">Termín</span><span class="sxs-lookup"><span data-stu-id="00cfc-106">Term</span></span>|<span data-ttu-id="00cfc-107">Definice</span><span class="sxs-lookup"><span data-stu-id="00cfc-107">Definition</span></span>|  
|---|---|  
|`numberList`|<span data-ttu-id="00cfc-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="00cfc-108">Optional.</span></span> <span data-ttu-id="00cfc-109">Čárkami oddělený seznam ID čísla upozornění, která by měla potlačit kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="00cfc-109">Comma-delimited list of the warning ID numbers that the compiler should suppress.</span></span> <span data-ttu-id="00cfc-110">Pokud nejsou zadané ID upozornění, jsou potlačovány všech upozornění.</span><span class="sxs-lookup"><span data-stu-id="00cfc-110">If the warning IDs are not specified, all warnings are suppressed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00cfc-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="00cfc-111">Remarks</span></span>  
 <span data-ttu-id="00cfc-112">`/nowarn` Způsobí, že kompilátor negeneruje upozornění.</span><span class="sxs-lookup"><span data-stu-id="00cfc-112">The `/nowarn` option causes the compiler to not generate warnings.</span></span> <span data-ttu-id="00cfc-113">Chcete-li potlačit jednotlivých upozornění, zadat ID upozornění na `/nowarn` možnost za dvojtečkou.</span><span class="sxs-lookup"><span data-stu-id="00cfc-113">To suppress an individual warning, supply the warning ID to the `/nowarn` option following the colon.</span></span> <span data-ttu-id="00cfc-114">Více čísel upozornění oddělujte čárkami.</span><span class="sxs-lookup"><span data-stu-id="00cfc-114">Separate multiple warning numbers with commas.</span></span>  
  
 <span data-ttu-id="00cfc-115">Je třeba zadat pouze číselnou část identifikátor upozornění.</span><span class="sxs-lookup"><span data-stu-id="00cfc-115">You need to specify only the numeric part of the warning identifier.</span></span> <span data-ttu-id="00cfc-116">Například pokud chcete potlačit BC42024 upozornění pro místní proměnné, zadejte `/nowarn:42024`.</span><span class="sxs-lookup"><span data-stu-id="00cfc-116">For example, if you want to suppress BC42024, the warning for unused local variables, specify `/nowarn:42024`.</span></span>  
  
 <span data-ttu-id="00cfc-117">Další informace o čísla ID upozornění najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="00cfc-117">For more information on the warning ID numbers, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
|<span data-ttu-id="00cfc-118">Chcete-li nastavit/nowarn v sadě Visual Studio integrované vývojové prostředí</span><span class="sxs-lookup"><span data-stu-id="00cfc-118">To set /nowarn in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="00cfc-119">1.  Máte projekt vybraný v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="00cfc-119">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="00cfc-120">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="00cfc-120">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="00cfc-121">Další informace najdete v tématu [Úvod do Návrhář projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="00cfc-121">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="00cfc-122">2.  Klikněte **zkompilovat** kartě.</span><span class="sxs-lookup"><span data-stu-id="00cfc-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="00cfc-123">3.  Vyberte **zakázat všech upozornění** zaškrtávací políčko Zakázat všech upozornění.</span><span class="sxs-lookup"><span data-stu-id="00cfc-123">3.  Select the **Disable all warnings** check box to disable all warnings.</span></span><br />     <span data-ttu-id="00cfc-124">- nebo -</span><span class="sxs-lookup"><span data-stu-id="00cfc-124">- or -</span></span><br />     <span data-ttu-id="00cfc-125">Chcete-li zakázat konkrétní upozornění, klikněte na tlačítko **žádné** v rozevíracím seznamu přiléhající k upozornění.</span><span class="sxs-lookup"><span data-stu-id="00cfc-125">To disable a particular warning, click **None** from the drop-down list adjacent to the warning.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="00cfc-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="00cfc-126">Example</span></span>  
 <span data-ttu-id="00cfc-127">Následující kód zkompiluje `T2.vb` a nezobrazí žádné upozornění.</span><span class="sxs-lookup"><span data-stu-id="00cfc-127">The following code compiles `T2.vb` and does not display any warnings.</span></span>  
  
```  
vbc /nowarn t2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="00cfc-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="00cfc-128">Example</span></span>  
 <span data-ttu-id="00cfc-129">Následující kód zkompiluje `T2.vb` a nezobrazí upozornění pro místní proměnné (42024).</span><span class="sxs-lookup"><span data-stu-id="00cfc-129">The following code compiles `T2.vb` and does not display the warnings for unused local variables (42024).</span></span>  
  
```  
vbc /nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="00cfc-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="00cfc-130">See Also</span></span>  
 [<span data-ttu-id="00cfc-131">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="00cfc-131">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="00cfc-132">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="00cfc-132">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="00cfc-133">Konfigurace upozornění v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="00cfc-133">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
