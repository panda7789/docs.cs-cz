---
title: "Volitelné parametry (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- parameters [Visual Basic], optional
- Visual Basic code, procedures
- procedures [Visual Basic], optional arguments
- optional arguments
- named arguments [Visual Basic], and optional arguments
- optional parameters
- Optional keyword [Visual Basic], optional arguments
- arguments [Visual Basic], optional
- optional arguments [Visual Basic], and named arguments
ms.assetid: 398d2845-1069-4e94-b934-a73b545c8b87
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e57023f594cfe4cd79d59cc8541fcf18018de0ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="optional-parameters-visual-basic"></a><span data-ttu-id="d707c-102">Volitelné parametry (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d707c-102">Optional Parameters (Visual Basic)</span></span>
<span data-ttu-id="d707c-103">Můžete určit, že parametr procedury je volitelný, a při volání této procedury se nemusí zadávat žádný argument.</span><span class="sxs-lookup"><span data-stu-id="d707c-103">You can specify that a procedure parameter is optional and no argument has to be supplied for it when the procedure is called.</span></span> <span data-ttu-id="d707c-104">*Volitelné parametry* jsou označeny `Optional` – klíčové slovo v definici postupu.</span><span class="sxs-lookup"><span data-stu-id="d707c-104">*Optional parameters* are indicated by the `Optional` keyword in the procedure definition.</span></span> <span data-ttu-id="d707c-105">Platí následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="d707c-105">The following rules apply:</span></span>  
  
-   <span data-ttu-id="d707c-106">Každý volitelný parametr v definici procedury musí mít výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d707c-106">Every optional parameter in the procedure definition must specify a default value.</span></span>  
  
-   <span data-ttu-id="d707c-107">Výchozí hodnota volitelného parametru musí být konstantní výraz.</span><span class="sxs-lookup"><span data-stu-id="d707c-107">The default value for an optional parameter must be a constant expression.</span></span>  
  
-   <span data-ttu-id="d707c-108">Každý parametr, který v definici procedury následuje za volitelným parametrem, musí být také volitelný.</span><span class="sxs-lookup"><span data-stu-id="d707c-108">Every parameter following an optional parameter in the procedure definition must also be optional.</span></span>  
  
 <span data-ttu-id="d707c-109">Následující syntaxe znázorňuje deklaraci procedury s volitelným parametrem:</span><span class="sxs-lookup"><span data-stu-id="d707c-109">The following syntax shows a procedure declaration with an optional parameter:</span></span>  
  
```vb  
Sub name(ByVal parameter1 As datatype1, Optional ByVal parameter2 As datatype2 = defaultvalue)  
```  
  
## <a name="calling-procedures-with-optional-parameters"></a><span data-ttu-id="d707c-110">Volání procedur s volitelnými parametry</span><span class="sxs-lookup"><span data-stu-id="d707c-110">Calling Procedures with Optional Parameters</span></span>  
 <span data-ttu-id="d707c-111">Při volání procedury s volitelným parametrem se můžete rozhodnout, zda zadáte argument.</span><span class="sxs-lookup"><span data-stu-id="d707c-111">When you call a procedure with an optional parameter, you can choose whether to supply the argument.</span></span> <span data-ttu-id="d707c-112">Pokud ho nezadáte, použije procedura výchozí hodnotu deklarovanou pro tento parametr.</span><span class="sxs-lookup"><span data-stu-id="d707c-112">If you do not, the procedure uses the default value declared for that parameter.</span></span>  
  
 <span data-ttu-id="d707c-113">Pokud v seznamu argumentů vynecháte jeden nebo více volitelných argumentů, označíte jejich pozice pomocí po sobě jdoucích čárek.</span><span class="sxs-lookup"><span data-stu-id="d707c-113">When you omit one or more optional arguments in the argument list, you use successive commas to mark their positions.</span></span> <span data-ttu-id="d707c-114">V následujícím ukázkovém volání je zadán první a čtvrtý argument, ale nikoli druhý a třetí:</span><span class="sxs-lookup"><span data-stu-id="d707c-114">The following example call supplies the first and fourth arguments but not the second or third:</span></span>  
  
```vb  
Sub name(argument 1, , , argument 4)  
```  
  
 <span data-ttu-id="d707c-115">Následující příklad vytvoří několik volání `MsgBox` funkce.</span><span class="sxs-lookup"><span data-stu-id="d707c-115">The following example makes several calls to the `MsgBox` function.</span></span> <span data-ttu-id="d707c-116">`MsgBox`jeden vyžaduje parametr a dva volitelné parametry.</span><span class="sxs-lookup"><span data-stu-id="d707c-116">`MsgBox` has one required parameter and two optional parameters.</span></span>  
  
 <span data-ttu-id="d707c-117">První volání `MsgBox` poskytuje všechny tři argumenty v pořadí, které `MsgBox` definuje je.</span><span class="sxs-lookup"><span data-stu-id="d707c-117">The first call to `MsgBox` supplies all three arguments in the order that `MsgBox` defines them.</span></span> <span data-ttu-id="d707c-118">Ve druhém volání je zadán pouze povinný argument.</span><span class="sxs-lookup"><span data-stu-id="d707c-118">The second call supplies only the required argument.</span></span> <span data-ttu-id="d707c-119">Ve třetím a čtvrtém volání je zadán první a třetí argument.</span><span class="sxs-lookup"><span data-stu-id="d707c-119">The third and fourth calls supply the first and third arguments.</span></span> <span data-ttu-id="d707c-120">Třetí volání tak činí podle pozice a čtvrté volání podle názvu.</span><span class="sxs-lookup"><span data-stu-id="d707c-120">The third call does this by position, and the fourth call does it by name.</span></span>  
  
 [!code-vb[VbVbcnProcedures#47](./codesnippet/VisualBasic/optional-parameters_1.vb)]  
  
## <a name="determining-whether-an-optional-argument-is-present"></a><span data-ttu-id="d707c-121">Určení, zda existuje volitelný argument</span><span class="sxs-lookup"><span data-stu-id="d707c-121">Determining Whether an Optional Argument Is Present</span></span>  
 <span data-ttu-id="d707c-122">Procedura nedokáže za běhu zjistit, zda byl daný argument vynechán nebo zda volající kód explicitně poskytuje výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d707c-122">A procedure cannot detect at run time whether a given argument has been omitted or the calling code has explicitly supplied the default value.</span></span> <span data-ttu-id="d707c-123">Pokud to potřebujete rozlišit, můžete jako výchozí nastavit nějakou nepravděpodobnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d707c-123">If you need to make this distinction, you can set an unlikely value as the default.</span></span> <span data-ttu-id="d707c-124">Následující postup definuje volitelný parametr `office`a testy pro jeho výchozí hodnotu `QJZ`, pokud chcete zobrazit, pokud byla vynechána ve volání:</span><span class="sxs-lookup"><span data-stu-id="d707c-124">The following procedure defines the optional parameter `office`, and tests for its default value, `QJZ`, to see if it has been omitted in the call:</span></span>  
  
 [!code-vb[VbVbcnProcedures#46](./codesnippet/VisualBasic/optional-parameters_2.vb)]  
  
 <span data-ttu-id="d707c-125">Pokud volitelný parametr, jako je typ odkazu `String`, můžete použít `Nothing` jako výchozí hodnota zadaná, nejedná se očekávaná hodnota pro argument.</span><span class="sxs-lookup"><span data-stu-id="d707c-125">If the optional parameter is a reference type such as a `String`, you can use `Nothing` as the default value, provided this is not an expected value for the argument.</span></span>  
  
## <a name="optional-parameters-and-overloading"></a><span data-ttu-id="d707c-126">Volitelné parametry a přetěžování</span><span class="sxs-lookup"><span data-stu-id="d707c-126">Optional Parameters and Overloading</span></span>  
 <span data-ttu-id="d707c-127">Proceduru s volitelnými parametry lze definovat také pomocí přetěžování.</span><span class="sxs-lookup"><span data-stu-id="d707c-127">Another way to define a procedure with optional parameters is to use overloading.</span></span> <span data-ttu-id="d707c-128">Pokud máte jeden volitelný parametr, můžete definovat dvě přetížené verze procedury – jednu s parametrem a druhou bez parametru.</span><span class="sxs-lookup"><span data-stu-id="d707c-128">If you have one optional parameter, you can define two overloaded versions of the procedure, one accepting the parameter and one without it.</span></span> <span data-ttu-id="d707c-129">S rostoucím počtem volitelných parametrů se zvyšuje složitost.</span><span class="sxs-lookup"><span data-stu-id="d707c-129">This approach becomes more complicated as the number of optional parameters increases.</span></span> <span data-ttu-id="d707c-130">Výhodou ale je, že máte absolutní jistotu, zda volající program poskytl jednotlivé volitelné argumenty.</span><span class="sxs-lookup"><span data-stu-id="d707c-130">However, its advantage is that you can be absolutely sure whether the calling program supplied each optional argument.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d707c-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="d707c-131">See Also</span></span>  
 [<span data-ttu-id="d707c-132">Postupy</span><span class="sxs-lookup"><span data-stu-id="d707c-132">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="d707c-133">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="d707c-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="d707c-134">Předávání argumentů podle hodnoty a podle Reference</span><span class="sxs-lookup"><span data-stu-id="d707c-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="d707c-135">Předávání argumentů podle pozice a názvu</span><span class="sxs-lookup"><span data-stu-id="d707c-135">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)  
 [<span data-ttu-id="d707c-136">Pole parametrů</span><span class="sxs-lookup"><span data-stu-id="d707c-136">Parameter Arrays</span></span>](./parameter-arrays.md)  
 [<span data-ttu-id="d707c-137">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="d707c-137">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="d707c-138">Volitelné</span><span class="sxs-lookup"><span data-stu-id="d707c-138">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)  
 [<span data-ttu-id="d707c-139">ParamArray</span><span class="sxs-lookup"><span data-stu-id="d707c-139">ParamArray</span></span>](../../../../visual-basic/language-reference/modifiers/paramarray.md)
