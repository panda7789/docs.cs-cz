---
title: -nowarn
ms.date: 07/20/2015
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
ms.openlocfilehash: 880fdf4931dadea547d64d0506bd3e978956468e
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005395"
---
# <a name="-nowarn"></a><span data-ttu-id="39f23-102">-nowarn</span><span class="sxs-lookup"><span data-stu-id="39f23-102">-nowarn</span></span>
<span data-ttu-id="39f23-103">Potlačí schopnost kompilátoru generovat upozornění.</span><span class="sxs-lookup"><span data-stu-id="39f23-103">Suppresses the compiler's ability to generate warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39f23-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="39f23-104">Syntax</span></span>  
  
```console  
-nowarn[:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="39f23-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="39f23-105">Arguments</span></span>  
  
|<span data-ttu-id="39f23-106">Termín</span><span class="sxs-lookup"><span data-stu-id="39f23-106">Term</span></span>|<span data-ttu-id="39f23-107">Definice</span><span class="sxs-lookup"><span data-stu-id="39f23-107">Definition</span></span>|  
|---|---|  
|`numberList`|<span data-ttu-id="39f23-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="39f23-108">Optional.</span></span> <span data-ttu-id="39f23-109">Čárkami oddělený seznam čísel ID upozornění, které by měl kompilátor potlačit.</span><span class="sxs-lookup"><span data-stu-id="39f23-109">Comma-delimited list of the warning ID numbers that the compiler should suppress.</span></span> <span data-ttu-id="39f23-110">Nejsou-li ID upozornění zadána, budou potlačena všechna upozornění.</span><span class="sxs-lookup"><span data-stu-id="39f23-110">If the warning IDs are not specified, all warnings are suppressed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39f23-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="39f23-111">Remarks</span></span>  
 <span data-ttu-id="39f23-112">Možnost `-nowarn` způsobí, že kompilátor negeneruje upozornění.</span><span class="sxs-lookup"><span data-stu-id="39f23-112">The `-nowarn` option causes the compiler to not generate warnings.</span></span> <span data-ttu-id="39f23-113">Chcete-li potlačit jednotlivá upozornění, zadejte ID upozornění do možnosti `-nowarn` za dvojtečkou.</span><span class="sxs-lookup"><span data-stu-id="39f23-113">To suppress an individual warning, supply the warning ID to the `-nowarn` option following the colon.</span></span> <span data-ttu-id="39f23-114">Více čísel upozornění oddělte čárkami.</span><span class="sxs-lookup"><span data-stu-id="39f23-114">Separate multiple warning numbers with commas.</span></span>  
  
 <span data-ttu-id="39f23-115">Je nutné zadat pouze číselnou část identifikátoru upozornění.</span><span class="sxs-lookup"><span data-stu-id="39f23-115">You need to specify only the numeric part of the warning identifier.</span></span> <span data-ttu-id="39f23-116">Například pokud chcete potlačit BC42024, upozornění pro nepoužívané místní proměnné, zadejte `-nowarn:42024`.</span><span class="sxs-lookup"><span data-stu-id="39f23-116">For example, if you want to suppress BC42024, the warning for unused local variables, specify `-nowarn:42024`.</span></span>  
  
 <span data-ttu-id="39f23-117">Další informace o číslech ID upozornění najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="39f23-117">For more information on the warning ID numbers, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
|<span data-ttu-id="39f23-118">Nastavení-upozornění v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="39f23-118">To set -nowarn in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="39f23-119">1. v **Průzkumník řešení**mít vybraný projekt.</span><span class="sxs-lookup"><span data-stu-id="39f23-119">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="39f23-120">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="39f23-120">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="39f23-121">2. klikněte na kartu **kompilovat** .</span><span class="sxs-lookup"><span data-stu-id="39f23-121">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="39f23-122">3. Zaškrtnutím políčka **Zakázat všechna upozornění** zakážete všechna upozornění.</span><span class="sxs-lookup"><span data-stu-id="39f23-122">3.  Select the **Disable all warnings** check box to disable all warnings.</span></span><br />     <span data-ttu-id="39f23-123">ani</span><span class="sxs-lookup"><span data-stu-id="39f23-123">- or -</span></span><br />     <span data-ttu-id="39f23-124">Chcete-li zakázat konkrétní upozornění, klikněte na tlačítko **žádné** v rozevíracím seznamu vedle upozornění.</span><span class="sxs-lookup"><span data-stu-id="39f23-124">To disable a particular warning, click **None** from the drop-down list adjacent to the warning.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="39f23-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="39f23-125">Example</span></span>  
 <span data-ttu-id="39f23-126">Následující kód zkompiluje `T2.vb` a nezobrazuje žádná upozornění.</span><span class="sxs-lookup"><span data-stu-id="39f23-126">The following code compiles `T2.vb` and does not display any warnings.</span></span>  
  
```console
vbc -nowarn t2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="39f23-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="39f23-127">Example</span></span>  
 <span data-ttu-id="39f23-128">Následující kód zkompiluje `T2.vb` a nezobrazuje upozornění pro nepoužívané místní proměnné (42024).</span><span class="sxs-lookup"><span data-stu-id="39f23-128">The following code compiles `T2.vb` and does not display the warnings for unused local variables (42024).</span></span>  
  
```console
vbc -nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="39f23-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="39f23-129">See also</span></span>

- [<span data-ttu-id="39f23-130">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="39f23-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="39f23-131">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="39f23-131">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="39f23-132">Konfigurace upozornění v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="39f23-132">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
