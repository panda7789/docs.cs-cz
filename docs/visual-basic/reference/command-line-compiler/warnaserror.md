---
title: -warnaserror (Visual Basic)
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ae8ed68045529e626f2788f854d8e6a6933e7e2
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="-warnaserror-visual-basic"></a><span data-ttu-id="d68c0-102">-warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d68c0-102">-warnaserror (Visual Basic)</span></span>
<span data-ttu-id="d68c0-103">Způsobí, že kompilátor první výskyt upozornění považovat za chybu.</span><span class="sxs-lookup"><span data-stu-id="d68c0-103">Causes the compiler to treat the first occurrence of a warning as an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d68c0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d68c0-104">Syntax</span></span>  
  
```  
-warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d68c0-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d68c0-105">Arguments</span></span>  
  
|<span data-ttu-id="d68c0-106">Termín</span><span class="sxs-lookup"><span data-stu-id="d68c0-106">Term</span></span>|<span data-ttu-id="d68c0-107">Definice</span><span class="sxs-lookup"><span data-stu-id="d68c0-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="d68c0-108">+ &#124; -</span><span class="sxs-lookup"><span data-stu-id="d68c0-108">+ &#124; -</span></span>|<span data-ttu-id="d68c0-109">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="d68c0-109">Optional.</span></span> <span data-ttu-id="d68c0-110">Ve výchozím nastavení `-warnaserror-` je v platnosti; upozornění nezabrání kompilátor vytvoření výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="d68c0-110">By default, `-warnaserror-` is in effect; warnings do not prevent the compiler from producing an output file.</span></span> <span data-ttu-id="d68c0-111">`-warnaserror` Možnost, která je stejná jako `-warnaserror+`, způsobí, že upozornění jsou považovány za chyby.</span><span class="sxs-lookup"><span data-stu-id="d68c0-111">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>|  
|`numberList`|<span data-ttu-id="d68c0-112">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="d68c0-112">Optional.</span></span> <span data-ttu-id="d68c0-113">Čárkami oddělený seznam ID upozornění čísla, ke kterému `-warnaserror` možnost se vztahuje.</span><span class="sxs-lookup"><span data-stu-id="d68c0-113">Comma-delimited list of the warning ID numbers to which the `-warnaserror` option applies.</span></span> <span data-ttu-id="d68c0-114">Pokud je zadáno žádné ID upozornění, `-warnaserror` možnost se vztahuje na všechny výstrahy.</span><span class="sxs-lookup"><span data-stu-id="d68c0-114">If no warning ID is specified, the `-warnaserror` option applies to all warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d68c0-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d68c0-115">Remarks</span></span>  
 <span data-ttu-id="d68c0-116">`-warnaserror` Možnost zpracovává všech upozornění jako chyby.</span><span class="sxs-lookup"><span data-stu-id="d68c0-116">The `-warnaserror` option treats all warnings as errors.</span></span> <span data-ttu-id="d68c0-117">Všechny zprávy, které by obvykle hlášeny jako upozornění jsou hlášeny jako chyby.</span><span class="sxs-lookup"><span data-stu-id="d68c0-117">Any messages that would ordinarily be reported as warnings are instead reported as errors.</span></span> <span data-ttu-id="d68c0-118">Kompilátor hlásí následné výskyty stejné upozornění jako upozornění.</span><span class="sxs-lookup"><span data-stu-id="d68c0-118">The compiler reports subsequent occurrences of the same warning as warnings.</span></span>  
  
 <span data-ttu-id="d68c0-119">Ve výchozím nastavení `-warnaserror-` je v platnosti, což způsobí, že upozornění být pouze informační.</span><span class="sxs-lookup"><span data-stu-id="d68c0-119">By default, `-warnaserror-` is in effect, which causes the warnings to be informational only.</span></span> <span data-ttu-id="d68c0-120">`-warnaserror` Možnost, která je stejná jako `-warnaserror+`, způsobí, že upozornění jsou považovány za chyby.</span><span class="sxs-lookup"><span data-stu-id="d68c0-120">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="d68c0-121">Pokud chcete pouze několik konkrétní upozornění jsou považovány za chyby, můžete určit seznam oddělený čárkami čísel upozornění považovat za chyby.</span><span class="sxs-lookup"><span data-stu-id="d68c0-121">If you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d68c0-122">`-warnaserror` Možnost neřídí zobrazení upozornění.</span><span class="sxs-lookup"><span data-stu-id="d68c0-122">The `-warnaserror` option does not control how warnings are displayed.</span></span> <span data-ttu-id="d68c0-123">Použití [- nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) možnost zakázat upozornění.</span><span class="sxs-lookup"><span data-stu-id="d68c0-123">Use the [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) option to disable warnings.</span></span>  
  
|<span data-ttu-id="d68c0-124">Chcete-li nastavit - warnaserror zpracovává všechna upozornění jako chyby v prostředí Visual Studio IDE</span><span class="sxs-lookup"><span data-stu-id="d68c0-124">To set -warnaserror to treat all warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="d68c0-125">1.  Máte projekt vybraný v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="d68c0-125">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="d68c0-126">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="d68c0-126">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="d68c0-127">2.  Klikněte **zkompilovat** kartě.</span><span class="sxs-lookup"><span data-stu-id="d68c0-127">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="d68c0-128">3.  Zajistěte, aby **zakázat všech upozornění** zaškrtávací políčko je zaškrtnuté políčko.</span><span class="sxs-lookup"><span data-stu-id="d68c0-128">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="d68c0-129">4.  Zkontrolujte **zpracovává všechna upozornění jako chyby** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="d68c0-129">4.  Check the **Treat all warnings as errors** check box.</span></span>|  
  
|<span data-ttu-id="d68c0-130">Chcete-li nastavit - warnaserror zacházet s konkrétní upozornění jako chyby v prostředí Visual Studio IDE</span><span class="sxs-lookup"><span data-stu-id="d68c0-130">To set -warnaserror to treat specific warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="d68c0-131">1.  Máte projekt vybraný v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="d68c0-131">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="d68c0-132">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="d68c0-132">On the **Project** menu, click **Properties**.</span></span><br /><span data-ttu-id="d68c0-133">2.  Klikněte **zkompilovat** kartě.</span><span class="sxs-lookup"><span data-stu-id="d68c0-133">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="d68c0-134">3.  Zajistěte, aby **zakázat všech upozornění** zaškrtávací políčko je zaškrtnuté políčko.</span><span class="sxs-lookup"><span data-stu-id="d68c0-134">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="d68c0-135">4.  Zajistěte, aby **zpracovává všechna upozornění jako chyby** zaškrtávací políčko je zaškrtnuté políčko.</span><span class="sxs-lookup"><span data-stu-id="d68c0-135">4.  Make sure the **Treat all warnings as errors** check box is unchecked.</span></span><br /><span data-ttu-id="d68c0-136">5.  Vyberte **chyba** z **oznámení** sloupec přiléhající k upozornění, že by měl být považovat za chybu.</span><span class="sxs-lookup"><span data-stu-id="d68c0-136">5.  Select **Error** from the **Notification** column adjacent to the warning that should be treated as an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d68c0-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="d68c0-137">Example</span></span>  
 <span data-ttu-id="d68c0-138">Následující kód zkompiluje `In.vb` a přesměruje kompilátoru zobrazuje chybu pro první výskyt každé varování najde.</span><span class="sxs-lookup"><span data-stu-id="d68c0-138">The following code compiles `In.vb` and directs the compiler to display an error for the first occurrence of every warning it finds.</span></span>  
  
```console
vbc -warnaserror in.vb  
```  
  
## <a name="example"></a><span data-ttu-id="d68c0-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="d68c0-139">Example</span></span>  
 <span data-ttu-id="d68c0-140">Následující kód zkompiluje `T2.vb` a pouze upozornění pro místní proměnné (42024) považuje za chybu.</span><span class="sxs-lookup"><span data-stu-id="d68c0-140">The following code compiles `T2.vb` and treats only the warning for unused local variables (42024) as an error.</span></span>  
  
```console
vbc -warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="d68c0-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="d68c0-141">See Also</span></span>  
 [<span data-ttu-id="d68c0-142">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="d68c0-142">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="d68c0-143">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="d68c0-143">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="d68c0-144">Konfigurace upozornění v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d68c0-144">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
