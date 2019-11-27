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
# <a name="-warnaserror-visual-basic"></a><span data-ttu-id="d6b08-102">-warnaserror – (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6b08-102">-warnaserror (Visual Basic)</span></span>
<span data-ttu-id="d6b08-103">Způsobí, že kompilátor bude zacházet s prvním výskytem upozornění jako s chybou.</span><span class="sxs-lookup"><span data-stu-id="d6b08-103">Causes the compiler to treat the first occurrence of a warning as an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6b08-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6b08-104">Syntax</span></span>  
  
```console  
-warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d6b08-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d6b08-105">Arguments</span></span>  
  
|<span data-ttu-id="d6b08-106">Termín</span><span class="sxs-lookup"><span data-stu-id="d6b08-106">Term</span></span>|<span data-ttu-id="d6b08-107">Definice</span><span class="sxs-lookup"><span data-stu-id="d6b08-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="d6b08-108">+ &#124; -</span><span class="sxs-lookup"><span data-stu-id="d6b08-108">+ &#124; -</span></span>|<span data-ttu-id="d6b08-109">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="d6b08-109">Optional.</span></span> <span data-ttu-id="d6b08-110">Ve výchozím nastavení je `-warnaserror-` aktivní. Upozornění nebrání kompilátoru v vytváření výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="d6b08-110">By default, `-warnaserror-` is in effect; warnings do not prevent the compiler from producing an output file.</span></span> <span data-ttu-id="d6b08-111">Možnost `-warnaserror`, která je stejná jako `-warnaserror+`, způsobí, že upozornění budou považována za chyby.</span><span class="sxs-lookup"><span data-stu-id="d6b08-111">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>|  
|`numberList`|<span data-ttu-id="d6b08-112">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="d6b08-112">Optional.</span></span> <span data-ttu-id="d6b08-113">Seznam čísel ID upozornění oddělených čárkami, na které se vztahuje možnost `-warnaserror`</span><span class="sxs-lookup"><span data-stu-id="d6b08-113">Comma-delimited list of the warning ID numbers to which the `-warnaserror` option applies.</span></span> <span data-ttu-id="d6b08-114">Pokud není zadané žádné ID upozornění, možnost `-warnaserror` platí pro všechna upozornění.</span><span class="sxs-lookup"><span data-stu-id="d6b08-114">If no warning ID is specified, the `-warnaserror` option applies to all warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6b08-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d6b08-115">Remarks</span></span>  
 <span data-ttu-id="d6b08-116">Možnost `-warnaserror` zpracovává všechna upozornění jako chyby.</span><span class="sxs-lookup"><span data-stu-id="d6b08-116">The `-warnaserror` option treats all warnings as errors.</span></span> <span data-ttu-id="d6b08-117">Všechny zprávy, které by byly obvykle hlášeny jako upozornění, jsou místo toho hlášeny jako chyby.</span><span class="sxs-lookup"><span data-stu-id="d6b08-117">Any messages that would ordinarily be reported as warnings are instead reported as errors.</span></span> <span data-ttu-id="d6b08-118">Kompilátor ohlásí následné výskyty stejného upozornění jako upozornění.</span><span class="sxs-lookup"><span data-stu-id="d6b08-118">The compiler reports subsequent occurrences of the same warning as warnings.</span></span>  
  
 <span data-ttu-id="d6b08-119">Ve výchozím nastavení je `-warnaserror-` aktivní, což způsobí, že upozornění budou pouze informativní.</span><span class="sxs-lookup"><span data-stu-id="d6b08-119">By default, `-warnaserror-` is in effect, which causes the warnings to be informational only.</span></span> <span data-ttu-id="d6b08-120">Možnost `-warnaserror`, která je stejná jako `-warnaserror+`, způsobí, že upozornění budou považována za chyby.</span><span class="sxs-lookup"><span data-stu-id="d6b08-120">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="d6b08-121">Pokud chcete, aby se jako chyby považovala jenom některá konkrétní upozornění, můžete zadat čárkami oddělený seznam čísel upozornění, která se budou považovat za chyby.</span><span class="sxs-lookup"><span data-stu-id="d6b08-121">If you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d6b08-122">Možnost `-warnaserror` neurčuje, jak se zobrazují upozornění.</span><span class="sxs-lookup"><span data-stu-id="d6b08-122">The `-warnaserror` option does not control how warnings are displayed.</span></span> <span data-ttu-id="d6b08-123">Pro vypnutí upozornění použijte možnost [-](../../../visual-basic/reference/command-line-compiler/nowarn.md) upozornění.</span><span class="sxs-lookup"><span data-stu-id="d6b08-123">Use the [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) option to disable warnings.</span></span>  
  
|<span data-ttu-id="d6b08-124">Nastavení-warnaserror –, aby považovala všechna upozornění jako chyby v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d6b08-124">To set -warnaserror to treat all warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="d6b08-125">1. v **Průzkumník řešení**mít vybraný projekt.</span><span class="sxs-lookup"><span data-stu-id="d6b08-125">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="d6b08-126">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="d6b08-126">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="d6b08-127">2. klikněte na kartu **kompilovat** .</span><span class="sxs-lookup"><span data-stu-id="d6b08-127">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="d6b08-128">3. Ujistěte se, že není zaškrtnuté políčko **Zakázat všechna upozornění** .</span><span class="sxs-lookup"><span data-stu-id="d6b08-128">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="d6b08-129">4. zaškrtněte políčko **považovat všechna upozornění za chyby** .</span><span class="sxs-lookup"><span data-stu-id="d6b08-129">4.  Check the **Treat all warnings as errors** check box.</span></span>|  
  
|<span data-ttu-id="d6b08-130">Nastavení-warnaserror – pro zacházení s konkrétními upozorněními jako s chybami v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d6b08-130">To set -warnaserror to treat specific warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="d6b08-131">1. v **Průzkumník řešení**mít vybraný projekt.</span><span class="sxs-lookup"><span data-stu-id="d6b08-131">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="d6b08-132">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="d6b08-132">On the **Project** menu, click **Properties**.</span></span><br /><span data-ttu-id="d6b08-133">2. klikněte na kartu **kompilovat** .</span><span class="sxs-lookup"><span data-stu-id="d6b08-133">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="d6b08-134">3. Ujistěte se, že není zaškrtnuté políčko **Zakázat všechna upozornění** .</span><span class="sxs-lookup"><span data-stu-id="d6b08-134">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="d6b08-135">4. Ujistěte se, že není zaškrtnuté políčko **považovat všechna upozornění jako chyby** .</span><span class="sxs-lookup"><span data-stu-id="d6b08-135">4.  Make sure the **Treat all warnings as errors** check box is unchecked.</span></span><br /><span data-ttu-id="d6b08-136">5. Vyberte **chybu** ze sloupce **oznámení** vedle upozornění, které by mělo být považováno za chybu.</span><span class="sxs-lookup"><span data-stu-id="d6b08-136">5.  Select **Error** from the **Notification** column adjacent to the warning that should be treated as an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d6b08-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6b08-137">Example</span></span>  
 <span data-ttu-id="d6b08-138">Následující kód zkompiluje `In.vb` a nasměruje kompilátor, aby zobrazil chybu pro první výskyt každého upozornění, které najde.</span><span class="sxs-lookup"><span data-stu-id="d6b08-138">The following code compiles `In.vb` and directs the compiler to display an error for the first occurrence of every warning it finds.</span></span>  
  
```console
vbc -warnaserror in.vb  
```  
  
## <a name="example"></a><span data-ttu-id="d6b08-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6b08-139">Example</span></span>  
 <span data-ttu-id="d6b08-140">Následující kód zkompiluje `T2.vb` a považuje pouze upozornění na nepoužívané místní proměnné (42024) jako chybu.</span><span class="sxs-lookup"><span data-stu-id="d6b08-140">The following code compiles `T2.vb` and treats only the warning for unused local variables (42024) as an error.</span></span>  
  
```console
vbc -warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="d6b08-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d6b08-141">See also</span></span>

- [<span data-ttu-id="d6b08-142">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="d6b08-142">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="d6b08-143">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="d6b08-143">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="d6b08-144">Konfigurace upozornění v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d6b08-144">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
