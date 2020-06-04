---
title: -nowarn
ms.date: 07/20/2015
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
ms.openlocfilehash: 37851f99eb88543e939ce48995ded41958e57cc3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397485"
---
# <a name="-nowarn"></a><span data-ttu-id="c2bab-102">-nowarn</span><span class="sxs-lookup"><span data-stu-id="c2bab-102">-nowarn</span></span>
<span data-ttu-id="c2bab-103">Potlačí schopnost kompilátoru generovat upozornění.</span><span class="sxs-lookup"><span data-stu-id="c2bab-103">Suppresses the compiler's ability to generate warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2bab-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c2bab-104">Syntax</span></span>  
  
```console  
-nowarn[:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="c2bab-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="c2bab-105">Arguments</span></span>  
  
|<span data-ttu-id="c2bab-106">Pojem</span><span class="sxs-lookup"><span data-stu-id="c2bab-106">Term</span></span>|<span data-ttu-id="c2bab-107">Definice</span><span class="sxs-lookup"><span data-stu-id="c2bab-107">Definition</span></span>|  
|---|---|  
|`numberList`|<span data-ttu-id="c2bab-108">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="c2bab-108">Optional.</span></span> <span data-ttu-id="c2bab-109">Čárkami oddělený seznam čísel ID upozornění, které by měl kompilátor potlačit.</span><span class="sxs-lookup"><span data-stu-id="c2bab-109">Comma-delimited list of the warning ID numbers that the compiler should suppress.</span></span> <span data-ttu-id="c2bab-110">Nejsou-li ID upozornění zadána, budou potlačena všechna upozornění.</span><span class="sxs-lookup"><span data-stu-id="c2bab-110">If the warning IDs are not specified, all warnings are suppressed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2bab-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c2bab-111">Remarks</span></span>  
 <span data-ttu-id="c2bab-112">`-nowarn`Možnost způsobí, že kompilátor negeneruje upozornění.</span><span class="sxs-lookup"><span data-stu-id="c2bab-112">The `-nowarn` option causes the compiler to not generate warnings.</span></span> <span data-ttu-id="c2bab-113">Chcete-li potlačit jednotlivá upozornění, zadejte ID upozornění pro `-nowarn` parametr za dvojtečkou.</span><span class="sxs-lookup"><span data-stu-id="c2bab-113">To suppress an individual warning, supply the warning ID to the `-nowarn` option following the colon.</span></span> <span data-ttu-id="c2bab-114">Více čísel upozornění oddělte čárkami.</span><span class="sxs-lookup"><span data-stu-id="c2bab-114">Separate multiple warning numbers with commas.</span></span>  
  
 <span data-ttu-id="c2bab-115">Je nutné zadat pouze číselnou část identifikátoru upozornění.</span><span class="sxs-lookup"><span data-stu-id="c2bab-115">You need to specify only the numeric part of the warning identifier.</span></span> <span data-ttu-id="c2bab-116">Například pokud chcete potlačit BC42024, upozornění pro nepoužívané místní proměnné, zadejte `-nowarn:42024` .</span><span class="sxs-lookup"><span data-stu-id="c2bab-116">For example, if you want to suppress BC42024, the warning for unused local variables, specify `-nowarn:42024`.</span></span>  
  
 <span data-ttu-id="c2bab-117">Další informace o číslech ID upozornění najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="c2bab-117">For more information on the warning ID numbers, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
|<span data-ttu-id="c2bab-118">Nastavení-upozornění v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c2bab-118">To set -nowarn in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="c2bab-119">1. v **Průzkumník řešení**mít vybraný projekt.</span><span class="sxs-lookup"><span data-stu-id="c2bab-119">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="c2bab-120">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="c2bab-120">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="c2bab-121">2. klikněte na kartu **kompilovat** .</span><span class="sxs-lookup"><span data-stu-id="c2bab-121">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="c2bab-122">3. Zaškrtnutím políčka **Zakázat všechna upozornění** zakážete všechna upozornění.</span><span class="sxs-lookup"><span data-stu-id="c2bab-122">3.  Select the **Disable all warnings** check box to disable all warnings.</span></span><br />     <span data-ttu-id="c2bab-123">- nebo -</span><span class="sxs-lookup"><span data-stu-id="c2bab-123">- or -</span></span><br />     <span data-ttu-id="c2bab-124">Chcete-li zakázat konkrétní upozornění, klikněte na tlačítko **žádné** v rozevíracím seznamu vedle upozornění.</span><span class="sxs-lookup"><span data-stu-id="c2bab-124">To disable a particular warning, click **None** from the drop-down list adjacent to the warning.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c2bab-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="c2bab-125">Example</span></span>  
 <span data-ttu-id="c2bab-126">Následující kód zkompiluje `T2.vb` a nezobrazuje žádná upozornění.</span><span class="sxs-lookup"><span data-stu-id="c2bab-126">The following code compiles `T2.vb` and does not display any warnings.</span></span>  
  
```console
vbc -nowarn t2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="c2bab-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="c2bab-127">Example</span></span>  
 <span data-ttu-id="c2bab-128">Následující kód zkompiluje `T2.vb` a nezobrazuje upozornění pro nepoužité místní proměnné (42024).</span><span class="sxs-lookup"><span data-stu-id="c2bab-128">The following code compiles `T2.vb` and does not display the warnings for unused local variables (42024).</span></span>  
  
```console
vbc -nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="c2bab-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="c2bab-129">See also</span></span>

- [<span data-ttu-id="c2bab-130">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="c2bab-130">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="c2bab-131">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="c2bab-131">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="c2bab-132">Konfigurace upozornění v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c2bab-132">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
