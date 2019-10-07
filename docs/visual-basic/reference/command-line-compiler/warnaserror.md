---
title: -warnaserror – (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
ms.openlocfilehash: 8af6d3ef4efecd53dcf38c33d0aa2cf182f07d30
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004648"
---
# <a name="-warnaserror-visual-basic"></a><span data-ttu-id="9e389-102">-warnaserror – (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e389-102">-warnaserror (Visual Basic)</span></span>
<span data-ttu-id="9e389-103">Způsobí, že kompilátor bude zacházet s prvním výskytem upozornění jako s chybou.</span><span class="sxs-lookup"><span data-stu-id="9e389-103">Causes the compiler to treat the first occurrence of a warning as an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e389-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9e389-104">Syntax</span></span>  
  
```console  
-warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="9e389-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="9e389-105">Arguments</span></span>  
  
|<span data-ttu-id="9e389-106">Termín</span><span class="sxs-lookup"><span data-stu-id="9e389-106">Term</span></span>|<span data-ttu-id="9e389-107">Definice</span><span class="sxs-lookup"><span data-stu-id="9e389-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="9e389-108">+ &#124; -</span><span class="sxs-lookup"><span data-stu-id="9e389-108">+ &#124; -</span></span>|<span data-ttu-id="9e389-109">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="9e389-109">Optional.</span></span> <span data-ttu-id="9e389-110">Ve výchozím nastavení platí `-warnaserror-`; Upozornění nebrání kompilátoru v vytváření výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="9e389-110">By default, `-warnaserror-` is in effect; warnings do not prevent the compiler from producing an output file.</span></span> <span data-ttu-id="9e389-111">Možnost `-warnaserror`, která je stejná jako `-warnaserror+`, způsobí, že upozornění budou považována za chyby.</span><span class="sxs-lookup"><span data-stu-id="9e389-111">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>|  
|`numberList`|<span data-ttu-id="9e389-112">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="9e389-112">Optional.</span></span> <span data-ttu-id="9e389-113">Seznam čísel ID upozornění oddělených čárkami, na které se vztahuje možnost `-warnaserror`.</span><span class="sxs-lookup"><span data-stu-id="9e389-113">Comma-delimited list of the warning ID numbers to which the `-warnaserror` option applies.</span></span> <span data-ttu-id="9e389-114">Pokud není zadané žádné ID upozornění, bude možnost `-warnaserror` platit pro všechna upozornění.</span><span class="sxs-lookup"><span data-stu-id="9e389-114">If no warning ID is specified, the `-warnaserror` option applies to all warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e389-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9e389-115">Remarks</span></span>  
 <span data-ttu-id="9e389-116">Možnost `-warnaserror` zpracovává všechna upozornění jako chyby.</span><span class="sxs-lookup"><span data-stu-id="9e389-116">The `-warnaserror` option treats all warnings as errors.</span></span> <span data-ttu-id="9e389-117">Všechny zprávy, které by byly obvykle hlášeny jako upozornění, jsou místo toho hlášeny jako chyby.</span><span class="sxs-lookup"><span data-stu-id="9e389-117">Any messages that would ordinarily be reported as warnings are instead reported as errors.</span></span> <span data-ttu-id="9e389-118">Kompilátor ohlásí následné výskyty stejného upozornění jako upozornění.</span><span class="sxs-lookup"><span data-stu-id="9e389-118">The compiler reports subsequent occurrences of the same warning as warnings.</span></span>  
  
 <span data-ttu-id="9e389-119">Ve výchozím nastavení platí `-warnaserror-`, což způsobí, že upozornění budou pouze informativní.</span><span class="sxs-lookup"><span data-stu-id="9e389-119">By default, `-warnaserror-` is in effect, which causes the warnings to be informational only.</span></span> <span data-ttu-id="9e389-120">Možnost `-warnaserror`, která je stejná jako `-warnaserror+`, způsobí, že upozornění budou považována za chyby.</span><span class="sxs-lookup"><span data-stu-id="9e389-120">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="9e389-121">Pokud chcete, aby se jako chyby považovala jenom některá konkrétní upozornění, můžete zadat čárkami oddělený seznam čísel upozornění, která se budou považovat za chyby.</span><span class="sxs-lookup"><span data-stu-id="9e389-121">If you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9e389-122">Možnost `-warnaserror` neurčuje, jak se zobrazují upozornění.</span><span class="sxs-lookup"><span data-stu-id="9e389-122">The `-warnaserror` option does not control how warnings are displayed.</span></span> <span data-ttu-id="9e389-123">Pro vypnutí upozornění použijte možnost [-](../../../visual-basic/reference/command-line-compiler/nowarn.md) upozornění.</span><span class="sxs-lookup"><span data-stu-id="9e389-123">Use the [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) option to disable warnings.</span></span>  
  
|<span data-ttu-id="9e389-124">Nastavení-warnaserror –, aby považovala všechna upozornění jako chyby v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9e389-124">To set -warnaserror to treat all warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="9e389-125">1. v **Průzkumník řešení**mít vybraný projekt.</span><span class="sxs-lookup"><span data-stu-id="9e389-125">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="9e389-126">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="9e389-126">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="9e389-127">2. klikněte na kartu **kompilovat** .</span><span class="sxs-lookup"><span data-stu-id="9e389-127">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="9e389-128">3. Ujistěte se, že není zaškrtnuté políčko **Zakázat všechna upozornění** .</span><span class="sxs-lookup"><span data-stu-id="9e389-128">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="9e389-129">4. zaškrtněte políčko **považovat všechna upozornění za chyby** .</span><span class="sxs-lookup"><span data-stu-id="9e389-129">4.  Check the **Treat all warnings as errors** check box.</span></span>|  
  
|<span data-ttu-id="9e389-130">Nastavení-warnaserror – pro zacházení s konkrétními upozorněními jako s chybami v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9e389-130">To set -warnaserror to treat specific warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="9e389-131">1. v **Průzkumník řešení**mít vybraný projekt.</span><span class="sxs-lookup"><span data-stu-id="9e389-131">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="9e389-132">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="9e389-132">On the **Project** menu, click **Properties**.</span></span><br /><span data-ttu-id="9e389-133">2. klikněte na kartu **kompilovat** .</span><span class="sxs-lookup"><span data-stu-id="9e389-133">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="9e389-134">3. Ujistěte se, že není zaškrtnuté políčko **Zakázat všechna upozornění** .</span><span class="sxs-lookup"><span data-stu-id="9e389-134">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="9e389-135">4. Ujistěte se, že není zaškrtnuté políčko **považovat všechna upozornění jako chyby** .</span><span class="sxs-lookup"><span data-stu-id="9e389-135">4.  Make sure the **Treat all warnings as errors** check box is unchecked.</span></span><br /><span data-ttu-id="9e389-136">5. Vyberte **chybu** ze sloupce **oznámení** vedle upozornění, které by mělo být považováno za chybu.</span><span class="sxs-lookup"><span data-stu-id="9e389-136">5.  Select **Error** from the **Notification** column adjacent to the warning that should be treated as an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9e389-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="9e389-137">Example</span></span>  
 <span data-ttu-id="9e389-138">Následující kód zkompiluje `In.vb` a nasměruje kompilátor, aby zobrazil chybu pro první výskyt každého upozornění, které najde.</span><span class="sxs-lookup"><span data-stu-id="9e389-138">The following code compiles `In.vb` and directs the compiler to display an error for the first occurrence of every warning it finds.</span></span>  
  
```console
vbc -warnaserror in.vb  
```  
  
## <a name="example"></a><span data-ttu-id="9e389-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="9e389-139">Example</span></span>  
 <span data-ttu-id="9e389-140">Následující kód zkompiluje `T2.vb` a považuje pouze upozornění na nepoužívané místní proměnné (42024) jako chybu.</span><span class="sxs-lookup"><span data-stu-id="9e389-140">The following code compiles `T2.vb` and treats only the warning for unused local variables (42024) as an error.</span></span>  
  
```console
vbc -warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="9e389-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9e389-141">See also</span></span>

- [<span data-ttu-id="9e389-142">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="9e389-142">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="9e389-143">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="9e389-143">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="9e389-144">Konfigurace upozornění v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9e389-144">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
