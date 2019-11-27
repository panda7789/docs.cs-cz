---
title: Error – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.error
helpviewer_keywords:
- Error statement [Visual Basic], syntax
- Error statement [Visual Basic]
- Error keyword [Visual Basic]
- run-time errors [Visual Basic], codes
- errors [Visual Basic], simulating
ms.assetid: 85cd5c59-5224-4f02-aaf5-fcfefab17a29
ms.openlocfilehash: 668ffbc7b8db73a706c5771bb0734a77f8fc0206
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351237"
---
# <a name="error-statement"></a><span data-ttu-id="b7d66-102">Error – příkaz</span><span class="sxs-lookup"><span data-stu-id="b7d66-102">Error Statement</span></span>
<span data-ttu-id="b7d66-103">Simuluje výskyt chyby.</span><span class="sxs-lookup"><span data-stu-id="b7d66-103">Simulates the occurrence of an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7d66-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7d66-104">Syntax</span></span>  
  
```vb  
Error errornumber  
```  
  
## <a name="parts"></a><span data-ttu-id="b7d66-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="b7d66-105">Parts</span></span>  
 `errornumber`  
 <span data-ttu-id="b7d66-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="b7d66-106">Required.</span></span> <span data-ttu-id="b7d66-107">Může to být jakékoli platné číslo chyby.</span><span class="sxs-lookup"><span data-stu-id="b7d66-107">Can be any valid error number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7d66-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b7d66-108">Remarks</span></span>  
 <span data-ttu-id="b7d66-109">Příkaz `Error` je podporován z důvodu zpětné kompatibility.</span><span class="sxs-lookup"><span data-stu-id="b7d66-109">The `Error` statement is supported for backward compatibility.</span></span> <span data-ttu-id="b7d66-110">V novém kódu, zejména při vytváření objektů, použijte metodu `Raise` `Err`ho objektu k vygenerování běhových chyb.</span><span class="sxs-lookup"><span data-stu-id="b7d66-110">In new code, especially when creating objects, use the `Err` object's `Raise` method to generate run-time errors.</span></span>  
  
 <span data-ttu-id="b7d66-111">Je-li definována `errornumber`, příkaz `Error` volá obslužnou rutinu chyby poté, co jsou vlastnosti objektu `Err` přiřazeny následující výchozí hodnoty:</span><span class="sxs-lookup"><span data-stu-id="b7d66-111">If `errornumber` is defined, the `Error` statement calls the error handler after the properties of the `Err` object are assigned the following default values:</span></span>  
  
|<span data-ttu-id="b7d66-112">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="b7d66-112">Property</span></span>|<span data-ttu-id="b7d66-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b7d66-113">Value</span></span>|  
|--------------|-----------|  
|`Number`|<span data-ttu-id="b7d66-114">Hodnota zadaná jako argument pro příkaz `Error`.</span><span class="sxs-lookup"><span data-stu-id="b7d66-114">Value specified as argument to `Error` statement.</span></span> <span data-ttu-id="b7d66-115">Může to být jakékoli platné číslo chyby.</span><span class="sxs-lookup"><span data-stu-id="b7d66-115">Can be any valid error number.</span></span>|  
|`Source`|<span data-ttu-id="b7d66-116">Název aktuálního projektu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b7d66-116">Name of the current Visual Basic project.</span></span>|  
|`Description`|<span data-ttu-id="b7d66-117">Řetězcový výraz odpovídající hodnotě vrácené funkce `Error` pro zadaný `Number`, pokud tento řetězec existuje.</span><span class="sxs-lookup"><span data-stu-id="b7d66-117">String expression corresponding to the return value of the `Error` function for the specified `Number`, if this string exists.</span></span> <span data-ttu-id="b7d66-118">Pokud řetězec neexistuje, `Description` obsahuje řetězec s nulovou délkou ("").</span><span class="sxs-lookup"><span data-stu-id="b7d66-118">If the string does not exist, `Description` contains a zero-length string ("").</span></span>|  
|`HelpFile`|<span data-ttu-id="b7d66-119">Plně kvalifikovaná jednotka, cesta a název souboru pro příslušný soubor s Visual Basic Help.</span><span class="sxs-lookup"><span data-stu-id="b7d66-119">The fully qualified drive, path, and file name of the appropriate Visual Basic Help file.</span></span>|  
|`HelpContext`|<span data-ttu-id="b7d66-120">Příslušné ID kontextového souboru Help Visual Basic pro chybu odpovídající vlastnosti `Number`.</span><span class="sxs-lookup"><span data-stu-id="b7d66-120">The appropriate Visual Basic Help file context ID for the error corresponding to the `Number` property.</span></span>|  
|`LastDLLError`|<span data-ttu-id="b7d66-121">Vynulujte.</span><span class="sxs-lookup"><span data-stu-id="b7d66-121">Zero.</span></span>|  
  
 <span data-ttu-id="b7d66-122">Pokud neexistují žádné obslužné rutiny chyb nebo pokud není žádná povolená, vytvoří se chybová zpráva, která se zobrazí z vlastností objektu `Err`.</span><span class="sxs-lookup"><span data-stu-id="b7d66-122">If no error handler exists, or if none is enabled, an error message is created and displayed from the `Err` object properties.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b7d66-123">Některé hostitelské aplikace Visual Basic nemůžou vytvářet objekty.</span><span class="sxs-lookup"><span data-stu-id="b7d66-123">Some Visual Basic host applications cannot create objects.</span></span> <span data-ttu-id="b7d66-124">Informace o tom, zda může vytvořit třídy a objekty, naleznete v dokumentaci hostitelské aplikace.</span><span class="sxs-lookup"><span data-stu-id="b7d66-124">See your host application's documentation to determine whether it can create classes and objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7d66-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="b7d66-125">Example</span></span>  
 <span data-ttu-id="b7d66-126">V tomto příkladu se k vygenerování čísla chyby 11 používá příkaz `Error`.</span><span class="sxs-lookup"><span data-stu-id="b7d66-126">This example uses the `Error` statement to generate error number 11.</span></span>  
  
```vb  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a><span data-ttu-id="b7d66-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b7d66-127">Requirements</span></span>  
 <span data-ttu-id="b7d66-128">**Obor názvů:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="b7d66-128">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="b7d66-129">**Sestavení:** Knihovna Visual Basic runtime (v souboru Microsoft. VisualBasic. dll)</span><span class="sxs-lookup"><span data-stu-id="b7d66-129">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7d66-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b7d66-130">See also</span></span>

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [<span data-ttu-id="b7d66-131">Příkaz On Error</span><span class="sxs-lookup"><span data-stu-id="b7d66-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
- [<span data-ttu-id="b7d66-132">Příkaz Resume</span><span class="sxs-lookup"><span data-stu-id="b7d66-132">Resume Statement</span></span>](../../../visual-basic/language-reference/statements/resume-statement.md)
- [<span data-ttu-id="b7d66-133">Chybové zprávy</span><span class="sxs-lookup"><span data-stu-id="b7d66-133">Error Messages</span></span>](../../../visual-basic/language-reference/error-messages/index.md)
