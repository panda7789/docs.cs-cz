---
title: -warnaserror
ms.date: 03/13/2018
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
ms.openlocfilehash: f9ca5575e2a042d68fc490494f2e86991d58b80c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351712"
---
# <a name="-warnaserror-visual-basic"></a><span data-ttu-id="307d3-102">-warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="307d3-102">-warnaserror (Visual Basic)</span></span>
<span data-ttu-id="307d3-103">Causes the compiler to treat the first occurrence of a warning as an error.</span><span class="sxs-lookup"><span data-stu-id="307d3-103">Causes the compiler to treat the first occurrence of a warning as an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="307d3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="307d3-104">Syntax</span></span>  
  
```console  
-warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="307d3-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="307d3-105">Arguments</span></span>  
  
|<span data-ttu-id="307d3-106">Termín</span><span class="sxs-lookup"><span data-stu-id="307d3-106">Term</span></span>|<span data-ttu-id="307d3-107">Definice</span><span class="sxs-lookup"><span data-stu-id="307d3-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="307d3-108">+ &#124; -</span><span class="sxs-lookup"><span data-stu-id="307d3-108">+ &#124; -</span></span>|<span data-ttu-id="307d3-109">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="307d3-109">Optional.</span></span> <span data-ttu-id="307d3-110">By default, `-warnaserror-` is in effect; warnings do not prevent the compiler from producing an output file.</span><span class="sxs-lookup"><span data-stu-id="307d3-110">By default, `-warnaserror-` is in effect; warnings do not prevent the compiler from producing an output file.</span></span> <span data-ttu-id="307d3-111">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span><span class="sxs-lookup"><span data-stu-id="307d3-111">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>|  
|`numberList`|<span data-ttu-id="307d3-112">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="307d3-112">Optional.</span></span> <span data-ttu-id="307d3-113">Comma-delimited list of the warning ID numbers to which the `-warnaserror` option applies.</span><span class="sxs-lookup"><span data-stu-id="307d3-113">Comma-delimited list of the warning ID numbers to which the `-warnaserror` option applies.</span></span> <span data-ttu-id="307d3-114">If no warning ID is specified, the `-warnaserror` option applies to all warnings.</span><span class="sxs-lookup"><span data-stu-id="307d3-114">If no warning ID is specified, the `-warnaserror` option applies to all warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="307d3-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="307d3-115">Remarks</span></span>  
 <span data-ttu-id="307d3-116">The `-warnaserror` option treats all warnings as errors.</span><span class="sxs-lookup"><span data-stu-id="307d3-116">The `-warnaserror` option treats all warnings as errors.</span></span> <span data-ttu-id="307d3-117">Any messages that would ordinarily be reported as warnings are instead reported as errors.</span><span class="sxs-lookup"><span data-stu-id="307d3-117">Any messages that would ordinarily be reported as warnings are instead reported as errors.</span></span> <span data-ttu-id="307d3-118">The compiler reports subsequent occurrences of the same warning as warnings.</span><span class="sxs-lookup"><span data-stu-id="307d3-118">The compiler reports subsequent occurrences of the same warning as warnings.</span></span>  
  
 <span data-ttu-id="307d3-119">By default, `-warnaserror-` is in effect, which causes the warnings to be informational only.</span><span class="sxs-lookup"><span data-stu-id="307d3-119">By default, `-warnaserror-` is in effect, which causes the warnings to be informational only.</span></span> <span data-ttu-id="307d3-120">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span><span class="sxs-lookup"><span data-stu-id="307d3-120">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="307d3-121">If you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span><span class="sxs-lookup"><span data-stu-id="307d3-121">If you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="307d3-122">The `-warnaserror` option does not control how warnings are displayed.</span><span class="sxs-lookup"><span data-stu-id="307d3-122">The `-warnaserror` option does not control how warnings are displayed.</span></span> <span data-ttu-id="307d3-123">Use the [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) option to disable warnings.</span><span class="sxs-lookup"><span data-stu-id="307d3-123">Use the [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) option to disable warnings.</span></span>  
  
|<span data-ttu-id="307d3-124">To set -warnaserror to treat all warnings as errors in the Visual Studio IDE</span><span class="sxs-lookup"><span data-stu-id="307d3-124">To set -warnaserror to treat all warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="307d3-125">1.  Have a project selected in **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="307d3-125">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="307d3-126">On the **Project** menu, click **Properties**.</span><span class="sxs-lookup"><span data-stu-id="307d3-126">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="307d3-127">2.  Click the **Compile** tab.</span><span class="sxs-lookup"><span data-stu-id="307d3-127">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="307d3-128">3.  Make sure the **Disable all warnings** check box is unchecked.</span><span class="sxs-lookup"><span data-stu-id="307d3-128">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="307d3-129">4.  Check the **Treat all warnings as errors** check box.</span><span class="sxs-lookup"><span data-stu-id="307d3-129">4.  Check the **Treat all warnings as errors** check box.</span></span>|  
  
|<span data-ttu-id="307d3-130">To set -warnaserror to treat specific warnings as errors in the Visual Studio IDE</span><span class="sxs-lookup"><span data-stu-id="307d3-130">To set -warnaserror to treat specific warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="307d3-131">1.  Have a project selected in **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="307d3-131">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="307d3-132">On the **Project** menu, click **Properties**.</span><span class="sxs-lookup"><span data-stu-id="307d3-132">On the **Project** menu, click **Properties**.</span></span><br /><span data-ttu-id="307d3-133">2.  Click the **Compile** tab.</span><span class="sxs-lookup"><span data-stu-id="307d3-133">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="307d3-134">3.  Make sure the **Disable all warnings** check box is unchecked.</span><span class="sxs-lookup"><span data-stu-id="307d3-134">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="307d3-135">4.  Make sure the **Treat all warnings as errors** check box is unchecked.</span><span class="sxs-lookup"><span data-stu-id="307d3-135">4.  Make sure the **Treat all warnings as errors** check box is unchecked.</span></span><br /><span data-ttu-id="307d3-136">5.  Select **Error** from the **Notification** column adjacent to the warning that should be treated as an error.</span><span class="sxs-lookup"><span data-stu-id="307d3-136">5.  Select **Error** from the **Notification** column adjacent to the warning that should be treated as an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="307d3-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="307d3-137">Example</span></span>  
 <span data-ttu-id="307d3-138">The following code compiles `In.vb` and directs the compiler to display an error for the first occurrence of every warning it finds.</span><span class="sxs-lookup"><span data-stu-id="307d3-138">The following code compiles `In.vb` and directs the compiler to display an error for the first occurrence of every warning it finds.</span></span>  
  
```console
vbc -warnaserror in.vb  
```  
  
## <a name="example"></a><span data-ttu-id="307d3-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="307d3-139">Example</span></span>  
 <span data-ttu-id="307d3-140">The following code compiles `T2.vb` and treats only the warning for unused local variables (42024) as an error.</span><span class="sxs-lookup"><span data-stu-id="307d3-140">The following code compiles `T2.vb` and treats only the warning for unused local variables (42024) as an error.</span></span>  
  
```console
vbc -warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="307d3-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="307d3-141">See also</span></span>

- [<span data-ttu-id="307d3-142">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="307d3-142">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="307d3-143">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="307d3-143">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="307d3-144">Konfigurace upozornění v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="307d3-144">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
