---
title: -nowarn
ms.date: 07/20/2015
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
ms.openlocfilehash: 31f7a2b771cfa1bcc6581d720aa0de3505aec826
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58828209"
---
# <a name="-nowarn"></a><span data-ttu-id="6228f-102">-nowarn</span><span class="sxs-lookup"><span data-stu-id="6228f-102">-nowarn</span></span>
<span data-ttu-id="6228f-103">Potlačí umožňuje kompilátoru generovat upozornění.</span><span class="sxs-lookup"><span data-stu-id="6228f-103">Suppresses the compiler's ability to generate warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6228f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6228f-104">Syntax</span></span>  
  
```  
-nowarn[:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="6228f-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="6228f-105">Arguments</span></span>  
  
|<span data-ttu-id="6228f-106">Termín</span><span class="sxs-lookup"><span data-stu-id="6228f-106">Term</span></span>|<span data-ttu-id="6228f-107">Definice</span><span class="sxs-lookup"><span data-stu-id="6228f-107">Definition</span></span>|  
|---|---|  
|`numberList`|<span data-ttu-id="6228f-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="6228f-108">Optional.</span></span> <span data-ttu-id="6228f-109">Čárkami oddělený seznam ID čísla upozornění, které kompilátor potlačit.</span><span class="sxs-lookup"><span data-stu-id="6228f-109">Comma-delimited list of the warning ID numbers that the compiler should suppress.</span></span> <span data-ttu-id="6228f-110">Pokud nejsou zadané ID upozornění, jsou potlačeny všechny výstrahy.</span><span class="sxs-lookup"><span data-stu-id="6228f-110">If the warning IDs are not specified, all warnings are suppressed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6228f-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6228f-111">Remarks</span></span>  
 <span data-ttu-id="6228f-112">`-nowarn` Možnost způsobí, že kompilátor negeneruje upozornění.</span><span class="sxs-lookup"><span data-stu-id="6228f-112">The `-nowarn` option causes the compiler to not generate warnings.</span></span> <span data-ttu-id="6228f-113">Pro potlačení jednotlivých upozornění, zadejte ID upozornění `-nowarn` možnost za dvojtečkou.</span><span class="sxs-lookup"><span data-stu-id="6228f-113">To suppress an individual warning, supply the warning ID to the `-nowarn` option following the colon.</span></span> <span data-ttu-id="6228f-114">Více čísel upozornění oddělte čárkami.</span><span class="sxs-lookup"><span data-stu-id="6228f-114">Separate multiple warning numbers with commas.</span></span>  
  
 <span data-ttu-id="6228f-115">Je třeba zadat pouze číselnou část identifikátoru upozornění.</span><span class="sxs-lookup"><span data-stu-id="6228f-115">You need to specify only the numeric part of the warning identifier.</span></span> <span data-ttu-id="6228f-116">Například pokud chcete potlačit BC42024 upozornění pro nepoužívané místní proměnné, zadejte `-nowarn:42024`.</span><span class="sxs-lookup"><span data-stu-id="6228f-116">For example, if you want to suppress BC42024, the warning for unused local variables, specify `-nowarn:42024`.</span></span>  
  
 <span data-ttu-id="6228f-117">Další informace o ID čísla upozornění, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="6228f-117">For more information on the warning ID numbers, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
|<span data-ttu-id="6228f-118">Chcete-li nastavit - nowarn v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6228f-118">To set -nowarn in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="6228f-119">1.  Mají projekt vybraný v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="6228f-119">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="6228f-120">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="6228f-120">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="6228f-121">2.  Klikněte na tlačítko **kompilaci** kartu.</span><span class="sxs-lookup"><span data-stu-id="6228f-121">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="6228f-122">3.  Vyberte **zakázat všechna upozornění** zaškrtávací políčko Zakázat všechna upozornění.</span><span class="sxs-lookup"><span data-stu-id="6228f-122">3.  Select the **Disable all warnings** check box to disable all warnings.</span></span><br />     <span data-ttu-id="6228f-123">- nebo -</span><span class="sxs-lookup"><span data-stu-id="6228f-123">- or -</span></span><br />     <span data-ttu-id="6228f-124">Chcete-li zakázat konkrétní upozornění, klikněte na tlačítko **žádný** z rozevíracího seznamu vedle upozornění.</span><span class="sxs-lookup"><span data-stu-id="6228f-124">To disable a particular warning, click **None** from the drop-down list adjacent to the warning.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6228f-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="6228f-125">Example</span></span>  
 <span data-ttu-id="6228f-126">Následující kód zkompiluje `T2.vb` a nezobrazí žádné upozornění.</span><span class="sxs-lookup"><span data-stu-id="6228f-126">The following code compiles `T2.vb` and does not display any warnings.</span></span>  
  
```console
vbc -nowarn t2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="6228f-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="6228f-127">Example</span></span>  
 <span data-ttu-id="6228f-128">Následující kód zkompiluje `T2.vb` a nezobrazí upozornění pro nepoužívané místní proměnné (42024).</span><span class="sxs-lookup"><span data-stu-id="6228f-128">The following code compiles `T2.vb` and does not display the warnings for unused local variables (42024).</span></span>  
  
```console
vbc -nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="6228f-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6228f-129">See also</span></span>

- [<span data-ttu-id="6228f-130">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="6228f-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="6228f-131">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="6228f-131">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="6228f-132">Konfigurace upozornění v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6228f-132">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
