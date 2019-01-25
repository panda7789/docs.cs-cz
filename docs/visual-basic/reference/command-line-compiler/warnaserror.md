---
title: -warnaserror (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
ms.openlocfilehash: 1b8bc004705be4113d875dd7909426e2d253112d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54534979"
---
# <a name="-warnaserror-visual-basic"></a><span data-ttu-id="68aac-102">-warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="68aac-102">-warnaserror (Visual Basic)</span></span>
<span data-ttu-id="68aac-103">Způsobí, že kompilátor první výskyt upozornění považovat za chybu.</span><span class="sxs-lookup"><span data-stu-id="68aac-103">Causes the compiler to treat the first occurrence of a warning as an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68aac-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68aac-104">Syntax</span></span>  
  
```  
-warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="68aac-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="68aac-105">Arguments</span></span>  
  
|<span data-ttu-id="68aac-106">Termín</span><span class="sxs-lookup"><span data-stu-id="68aac-106">Term</span></span>|<span data-ttu-id="68aac-107">Definice</span><span class="sxs-lookup"><span data-stu-id="68aac-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="68aac-108">+ &#124; -</span><span class="sxs-lookup"><span data-stu-id="68aac-108">+ &#124; -</span></span>|<span data-ttu-id="68aac-109">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="68aac-109">Optional.</span></span> <span data-ttu-id="68aac-110">Ve výchozím nastavení `-warnaserror-` je v platnosti; upozornění nezabrání kompilátor vytváří výstupní soubor.</span><span class="sxs-lookup"><span data-stu-id="68aac-110">By default, `-warnaserror-` is in effect; warnings do not prevent the compiler from producing an output file.</span></span> <span data-ttu-id="68aac-111">`-warnaserror` Možnost, která je stejná jako `-warnaserror+`, způsobí upozornění budou považována za chyby.</span><span class="sxs-lookup"><span data-stu-id="68aac-111">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>|  
|`numberList`|<span data-ttu-id="68aac-112">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="68aac-112">Optional.</span></span> <span data-ttu-id="68aac-113">Čárkami oddělený seznam ID upozornění čísla, ke kterému `-warnaserror` možnost se vztahuje.</span><span class="sxs-lookup"><span data-stu-id="68aac-113">Comma-delimited list of the warning ID numbers to which the `-warnaserror` option applies.</span></span> <span data-ttu-id="68aac-114">Pokud není zadána žádná ID upozornění, `-warnaserror` možnost se vztahuje na všechna upozornění.</span><span class="sxs-lookup"><span data-stu-id="68aac-114">If no warning ID is specified, the `-warnaserror` option applies to all warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68aac-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="68aac-115">Remarks</span></span>  
 <span data-ttu-id="68aac-116">`-warnaserror` Možnost zpracuje všechna upozornění jako chyby.</span><span class="sxs-lookup"><span data-stu-id="68aac-116">The `-warnaserror` option treats all warnings as errors.</span></span> <span data-ttu-id="68aac-117">Všechny zprávy, které by obvykle hlášeny jako varování jsou hlášeny jako chyby.</span><span class="sxs-lookup"><span data-stu-id="68aac-117">Any messages that would ordinarily be reported as warnings are instead reported as errors.</span></span> <span data-ttu-id="68aac-118">Kompilátor oznámí další výskyty stejného upozornění jako upozornění.</span><span class="sxs-lookup"><span data-stu-id="68aac-118">The compiler reports subsequent occurrences of the same warning as warnings.</span></span>  
  
 <span data-ttu-id="68aac-119">Ve výchozím nastavení `-warnaserror-` je v platnosti, což způsobí, že upozornění bude pouze informační.</span><span class="sxs-lookup"><span data-stu-id="68aac-119">By default, `-warnaserror-` is in effect, which causes the warnings to be informational only.</span></span> <span data-ttu-id="68aac-120">`-warnaserror` Možnost, která je stejná jako `-warnaserror+`, způsobí upozornění budou považována za chyby.</span><span class="sxs-lookup"><span data-stu-id="68aac-120">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="68aac-121">Pokud chcete pouze několik specifická upozornění budou považována za chyby, můžete zadat čárkou oddělený seznam čísel upozornění pro nakládání s chybami.</span><span class="sxs-lookup"><span data-stu-id="68aac-121">If you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="68aac-122">`-warnaserror` Možnost neřídí, jak se zobrazí upozornění.</span><span class="sxs-lookup"><span data-stu-id="68aac-122">The `-warnaserror` option does not control how warnings are displayed.</span></span> <span data-ttu-id="68aac-123">Použití [- nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) možnost zakázat upozornění.</span><span class="sxs-lookup"><span data-stu-id="68aac-123">Use the [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) option to disable warnings.</span></span>  
  
|<span data-ttu-id="68aac-124">Chcete-li nastavit warnaserror – považovat všechna upozornění jako chyby v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="68aac-124">To set -warnaserror to treat all warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="68aac-125">1.  Mají projekt vybraný v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="68aac-125">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="68aac-126">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="68aac-126">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="68aac-127">2.  Klikněte na tlačítko **kompilaci** kartu.</span><span class="sxs-lookup"><span data-stu-id="68aac-127">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="68aac-128">3.  Ujistěte se, **zakázat všechna upozornění** zaškrtávací políčko je zaškrtnuté políčko.</span><span class="sxs-lookup"><span data-stu-id="68aac-128">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="68aac-129">4.  Zkontrolujte, **považovat všechna upozornění jako chyby** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="68aac-129">4.  Check the **Treat all warnings as errors** check box.</span></span>|  
  
|<span data-ttu-id="68aac-130">Chcete-li nastavit warnaserror – považovat specifická upozornění jako chyby v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="68aac-130">To set -warnaserror to treat specific warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="68aac-131">1.  Mají projekt vybraný v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="68aac-131">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="68aac-132">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="68aac-132">On the **Project** menu, click **Properties**.</span></span><br /><span data-ttu-id="68aac-133">2.  Klikněte na tlačítko **kompilaci** kartu.</span><span class="sxs-lookup"><span data-stu-id="68aac-133">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="68aac-134">3.  Ujistěte se, **zakázat všechna upozornění** zaškrtávací políčko je zaškrtnuté políčko.</span><span class="sxs-lookup"><span data-stu-id="68aac-134">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="68aac-135">4.  Ujistěte se, **považovat všechna upozornění jako chyby** zaškrtávací políčko je zaškrtnuté políčko.</span><span class="sxs-lookup"><span data-stu-id="68aac-135">4.  Make sure the **Treat all warnings as errors** check box is unchecked.</span></span><br /><span data-ttu-id="68aac-136">5.  Vyberte **chyba** z **oznámení** sloupce sousedícího s upozornění, která mají být považována za chybu.</span><span class="sxs-lookup"><span data-stu-id="68aac-136">5.  Select **Error** from the **Notification** column adjacent to the warning that should be treated as an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="68aac-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="68aac-137">Example</span></span>  
 <span data-ttu-id="68aac-138">Následující kód zkompiluje `In.vb` a instruuje kompilátor, aby zobrazuje chybu pro první výskyt každé varování, které nalezne.</span><span class="sxs-lookup"><span data-stu-id="68aac-138">The following code compiles `In.vb` and directs the compiler to display an error for the first occurrence of every warning it finds.</span></span>  
  
```console
vbc -warnaserror in.vb  
```  
  
## <a name="example"></a><span data-ttu-id="68aac-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="68aac-139">Example</span></span>  
 <span data-ttu-id="68aac-140">Následující kód zkompiluje `T2.vb` a pouze upozornění pro nepoužívané místní proměnné (42024) považuje za chybu.</span><span class="sxs-lookup"><span data-stu-id="68aac-140">The following code compiles `T2.vb` and treats only the warning for unused local variables (42024) as an error.</span></span>  
  
```console
vbc -warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="68aac-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="68aac-141">See also</span></span>
- [<span data-ttu-id="68aac-142">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="68aac-142">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="68aac-143">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="68aac-143">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="68aac-144">Konfigurace upozornění v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="68aac-144">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
