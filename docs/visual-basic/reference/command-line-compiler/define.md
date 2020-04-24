---
title: -define
ms.date: 03/10/2018
helpviewer_keywords:
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
ms.openlocfilehash: 5035466de4aa17c374824e1b0f02ed594731a9d3
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716802"
---
# <a name="-define-visual-basic"></a><span data-ttu-id="8e0e7-102">-define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e0e7-102">-define (Visual Basic)</span></span>
<span data-ttu-id="8e0e7-103">Definuje podmíněné konstanty kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="8e0e7-103">Defines conditional compiler constants.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e0e7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8e0e7-104">Syntax</span></span>  
  
```console  
-define:["]symbol[=value][,symbol[=value]]["]  
```

<span data-ttu-id="8e0e7-105">– nebo –</span><span class="sxs-lookup"><span data-stu-id="8e0e7-105">or</span></span>

```console  
-d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a><span data-ttu-id="8e0e7-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="8e0e7-106">Arguments</span></span>  
  
|<span data-ttu-id="8e0e7-107">Označení</span><span class="sxs-lookup"><span data-stu-id="8e0e7-107">Term</span></span>|<span data-ttu-id="8e0e7-108">Definice</span><span class="sxs-lookup"><span data-stu-id="8e0e7-108">Definition</span></span>|  
|---|---|  
|`symbol`|<span data-ttu-id="8e0e7-109">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="8e0e7-109">Required.</span></span> <span data-ttu-id="8e0e7-110">Symbol, který má být definován.</span><span class="sxs-lookup"><span data-stu-id="8e0e7-110">The symbol to define.</span></span>|  
|`value`|<span data-ttu-id="8e0e7-111">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="8e0e7-111">Optional.</span></span> <span data-ttu-id="8e0e7-112">Hodnota, která má `symbol`být přiřazena.</span><span class="sxs-lookup"><span data-stu-id="8e0e7-112">The value to assign `symbol`.</span></span> <span data-ttu-id="8e0e7-113">Pokud `value` je řetězec, musí být ohraničen znakem zpětného lomítka nebo posloupnosti uvozovek (\\") místo uvozovek.</span><span class="sxs-lookup"><span data-stu-id="8e0e7-113">If `value` is a string, it must be surrounded by backslash/quotation-mark sequences (\\") instead of quotation marks.</span></span> <span data-ttu-id="8e0e7-114">Pokud není zadána žádná hodnota, bude provedena hodnota true.</span><span class="sxs-lookup"><span data-stu-id="8e0e7-114">If no value is specified, then it is taken to be True.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e0e7-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8e0e7-115">Remarks</span></span>  
 <span data-ttu-id="8e0e7-116">`-define` Možnost má podobný efekt jako použití `#Const` direktivy preprocesoru ve zdrojovém souboru s tím rozdílem, že konstanty definované `-define` s jsou veřejné a platí pro všechny soubory v projektu.</span><span class="sxs-lookup"><span data-stu-id="8e0e7-116">The `-define` option has an effect similar to using a `#Const` preprocessor directive in your source file, except that constants defined with `-define` are public and apply to all files in the project.</span></span>  
  
 <span data-ttu-id="8e0e7-117">Můžete použít symboly vytvořené pomocí této možnosti s `#If`... `Then`... `#Else` direktiva podmíněného kompilování zdrojových souborů.</span><span class="sxs-lookup"><span data-stu-id="8e0e7-117">You can use symbols created by this option with the `#If`...`Then`...`#Else` directive to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="8e0e7-118">`-d`je krátký tvar `-define`.</span><span class="sxs-lookup"><span data-stu-id="8e0e7-118">`-d` is the short form of `-define`.</span></span>  
  
 <span data-ttu-id="8e0e7-119">Můžete definovat více symbolů `-define` pomocí čárky pro oddělení definic symbolů.</span><span class="sxs-lookup"><span data-stu-id="8e0e7-119">You can define multiple symbols with `-define` by using a comma to separate symbol definitions.</span></span>  
  
|<span data-ttu-id="8e0e7-120">Nastavení – definice v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8e0e7-120">To set -define in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="8e0e7-121">1. v **Průzkumník řešení**mít vybraný projekt.</span><span class="sxs-lookup"><span data-stu-id="8e0e7-121">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="8e0e7-122">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="8e0e7-122">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="8e0e7-123">2. klikněte na kartu **kompilovat** .</span><span class="sxs-lookup"><span data-stu-id="8e0e7-123">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="8e0e7-124">3. klikněte na tlačítko **Upřesnit**.</span><span class="sxs-lookup"><span data-stu-id="8e0e7-124">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="8e0e7-125">4. upravte hodnotu v poli **vlastní konstanty** .</span><span class="sxs-lookup"><span data-stu-id="8e0e7-125">4.  Modify the value in the **Custom Constants** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8e0e7-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="8e0e7-126">Example</span></span>  
 <span data-ttu-id="8e0e7-127">Následující kód definuje a poté používá dvě podmíněné konstanty kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="8e0e7-127">The following code defines and then uses two conditional compiler constants.</span></span>  
  
 [!code-vb[VbVbalrCompiler#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#45)]  
  
## <a name="see-also"></a><span data-ttu-id="8e0e7-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="8e0e7-128">See also</span></span>

- [<span data-ttu-id="8e0e7-129">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="8e0e7-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="8e0e7-130">Direktivy #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="8e0e7-130">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="8e0e7-131">Direktiva #Const</span><span class="sxs-lookup"><span data-stu-id="8e0e7-131">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)
- [<span data-ttu-id="8e0e7-132">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="8e0e7-132">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
