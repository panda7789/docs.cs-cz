---
title: /warnaserror (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 04b79b3d14a9c4a9f9721860cd1ed44032dfa5d1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="warnaserror-visual-basic"></a><span data-ttu-id="d94b4-102">/warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d94b4-102">/warnaserror (Visual Basic)</span></span>
<span data-ttu-id="d94b4-103">Způsobí, že kompilátor první výskyt upozornění považovat za chybu.</span><span class="sxs-lookup"><span data-stu-id="d94b4-103">Causes the compiler to treat the first occurrence of a warning as an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d94b4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d94b4-104">Syntax</span></span>  
  
```  
/warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d94b4-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d94b4-105">Arguments</span></span>  
  
|<span data-ttu-id="d94b4-106">Termín</span><span class="sxs-lookup"><span data-stu-id="d94b4-106">Term</span></span>|<span data-ttu-id="d94b4-107">Definice</span><span class="sxs-lookup"><span data-stu-id="d94b4-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="d94b4-108">+ &#124; -</span><span class="sxs-lookup"><span data-stu-id="d94b4-108">+ &#124; -</span></span>|<span data-ttu-id="d94b4-109">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="d94b4-109">Optional.</span></span> <span data-ttu-id="d94b4-110">Ve výchozím nastavení `/warnaserror-` je v platnosti; upozornění nezabrání kompilátor vytvoření výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="d94b4-110">By default, `/warnaserror-` is in effect; warnings do not prevent the compiler from producing an output file.</span></span> <span data-ttu-id="d94b4-111">`/warnaserror` Možnost, která je stejná jako `/warnaserror+`, způsobí, že upozornění jsou považovány za chyby.</span><span class="sxs-lookup"><span data-stu-id="d94b4-111">The `/warnaserror` option, which is the same as `/warnaserror+`, causes warnings to be treated as errors.</span></span>|  
|`numberList`|<span data-ttu-id="d94b4-112">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="d94b4-112">Optional.</span></span> <span data-ttu-id="d94b4-113">Čárkami oddělený seznam ID upozornění čísla, ke kterému `/warnaserror` možnost se vztahuje.</span><span class="sxs-lookup"><span data-stu-id="d94b4-113">Comma-delimited list of the warning ID numbers to which the `/warnaserror` option applies.</span></span> <span data-ttu-id="d94b4-114">Pokud je zadáno žádné ID upozornění, `/warnaserror` možnost se vztahuje na všechny výstrahy.</span><span class="sxs-lookup"><span data-stu-id="d94b4-114">If no warning ID is specified, the `/warnaserror` option applies to all warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d94b4-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d94b4-115">Remarks</span></span>  
 <span data-ttu-id="d94b4-116">`/warnaserror` Možnost zpracovává všech upozornění jako chyby.</span><span class="sxs-lookup"><span data-stu-id="d94b4-116">The `/warnaserror` option treats all warnings as errors.</span></span> <span data-ttu-id="d94b4-117">Všechny zprávy, které by obvykle hlášeny jako upozornění jsou hlášeny jako chyby.</span><span class="sxs-lookup"><span data-stu-id="d94b4-117">Any messages that would ordinarily be reported as warnings are instead reported as errors.</span></span> <span data-ttu-id="d94b4-118">Kompilátor hlásí následné výskyty stejné upozornění jako upozornění.</span><span class="sxs-lookup"><span data-stu-id="d94b4-118">The compiler reports subsequent occurrences of the same warning as warnings.</span></span>  
  
 <span data-ttu-id="d94b4-119">Ve výchozím nastavení `/warnaserror-` je v platnosti, což způsobí, že upozornění být pouze informační.</span><span class="sxs-lookup"><span data-stu-id="d94b4-119">By default, `/warnaserror-` is in effect, which causes the warnings to be informational only.</span></span> <span data-ttu-id="d94b4-120">`/warnaserror` Možnost, která je stejná jako `/warnaserror+`, způsobí, že upozornění jsou považovány za chyby.</span><span class="sxs-lookup"><span data-stu-id="d94b4-120">The `/warnaserror` option, which is the same as `/warnaserror+`, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="d94b4-121">Pokud chcete pouze několik konkrétní upozornění jsou považovány za chyby, můžete určit seznam oddělený čárkami čísel upozornění považovat za chyby.</span><span class="sxs-lookup"><span data-stu-id="d94b4-121">If you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d94b4-122">`/warnaserror` Možnost neřídí zobrazení upozornění.</span><span class="sxs-lookup"><span data-stu-id="d94b4-122">The `/warnaserror` option does not control how warnings are displayed.</span></span> <span data-ttu-id="d94b4-123">Použití [/nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) možnost zakázat upozornění.</span><span class="sxs-lookup"><span data-stu-id="d94b4-123">Use the [/nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) option to disable warnings.</span></span>  
  
|<span data-ttu-id="d94b4-124">Chcete-li nastavit/warnaserror zachází všech upozornění jako chyby v prostředí Visual Studio IDE</span><span class="sxs-lookup"><span data-stu-id="d94b4-124">To set /warnaserror to treat all warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="d94b4-125">1.  Máte projekt vybraný v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="d94b4-125">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="d94b4-126">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="d94b4-126">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="d94b4-127">Další informace najdete v tématu [Úvod do Návrhář projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="d94b4-127">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="d94b4-128">2.  Klikněte **zkompilovat** kartě.</span><span class="sxs-lookup"><span data-stu-id="d94b4-128">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="d94b4-129">3.  Zajistěte, aby **zakázat všech upozornění** zaškrtávací políčko je zaškrtnuté políčko.</span><span class="sxs-lookup"><span data-stu-id="d94b4-129">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="d94b4-130">4.  Zkontrolujte **zpracovává všechna upozornění jako chyby** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="d94b4-130">4.  Check the **Treat all warnings as errors** check box.</span></span>|  
  
|<span data-ttu-id="d94b4-131">Chcete-li nastavit/warnaserror zacházet s konkrétní upozornění jako chyby v prostředí Visual Studio IDE</span><span class="sxs-lookup"><span data-stu-id="d94b4-131">To set /warnaserror to treat specific warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="d94b4-132">1.  Máte projekt vybraný v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="d94b4-132">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="d94b4-133">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="d94b4-133">On the **Project** menu, click **Properties**.</span></span><br /><span data-ttu-id="d94b4-134">2.  Klikněte **zkompilovat** kartě.</span><span class="sxs-lookup"><span data-stu-id="d94b4-134">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="d94b4-135">3.  Zajistěte, aby **zakázat všech upozornění** zaškrtávací políčko je zaškrtnuté políčko.</span><span class="sxs-lookup"><span data-stu-id="d94b4-135">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="d94b4-136">4.  Zajistěte, aby **zpracovává všechna upozornění jako chyby** zaškrtávací políčko je zaškrtnuté políčko.</span><span class="sxs-lookup"><span data-stu-id="d94b4-136">4.  Make sure the **Treat all warnings as errors** check box is unchecked.</span></span><br /><span data-ttu-id="d94b4-137">5.  Vyberte **chyba** z **oznámení** sloupec přiléhající k upozornění, že by měl být považovat za chybu.</span><span class="sxs-lookup"><span data-stu-id="d94b4-137">5.  Select **Error** from the **Notification** column adjacent to the warning that should be treated as an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d94b4-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="d94b4-138">Example</span></span>  
 <span data-ttu-id="d94b4-139">Následující kód zkompiluje `In.vb` a přesměruje kompilátoru zobrazuje chybu pro první výskyt každé varování najde.</span><span class="sxs-lookup"><span data-stu-id="d94b4-139">The following code compiles `In.vb` and directs the compiler to display an error for the first occurrence of every warning it finds.</span></span>  
  
```  
vbc /warnaserror in.vb  
```  
  
## <a name="example"></a><span data-ttu-id="d94b4-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="d94b4-140">Example</span></span>  
 <span data-ttu-id="d94b4-141">Následující kód zkompiluje `T2.vb` a pouze upozornění pro místní proměnné (42024) považuje za chybu.</span><span class="sxs-lookup"><span data-stu-id="d94b4-141">The following code compiles `T2.vb` and treats only the warning for unused local variables (42024) as an error.</span></span>  
  
```  
vbc /warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="d94b4-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="d94b4-142">See Also</span></span>  
 [<span data-ttu-id="d94b4-143">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="d94b4-143">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="d94b4-144">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="d94b4-144">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="d94b4-145">Konfigurace upozornění v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d94b4-145">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
