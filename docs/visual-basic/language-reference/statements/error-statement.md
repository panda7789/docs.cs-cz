---
title: "Error – příkaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.error
helpviewer_keywords:
- Error statement [Visual Basic], syntax
- Error statement [Visual Basic]
- Error keyword [Visual Basic]
- run-time errors [Visual Basic], codes
- errors [Visual Basic], simulating
ms.assetid: 85cd5c59-5224-4f02-aaf5-fcfefab17a29
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3cd3245fd3e9e62b1b6443e9787c97808a0d179d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="error-statement"></a><span data-ttu-id="2bb4c-102">Error – příkaz</span><span class="sxs-lookup"><span data-stu-id="2bb4c-102">Error Statement</span></span>
<span data-ttu-id="2bb4c-103">Simuluje došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="2bb4c-103">Simulates the occurrence of an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bb4c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2bb4c-104">Syntax</span></span>  
  
```  
Error errornumber  
```  
  
## <a name="parts"></a><span data-ttu-id="2bb4c-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="2bb4c-105">Parts</span></span>  
 `errornumber`  
 <span data-ttu-id="2bb4c-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="2bb4c-106">Required.</span></span> <span data-ttu-id="2bb4c-107">Může být jakékoli platné číslo chyby.</span><span class="sxs-lookup"><span data-stu-id="2bb4c-107">Can be any valid error number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2bb4c-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2bb4c-108">Remarks</span></span>  
 <span data-ttu-id="2bb4c-109">`Error` Příkaz je podporován z důvodu zpětné kompatibility.</span><span class="sxs-lookup"><span data-stu-id="2bb4c-109">The `Error` statement is supported for backward compatibility.</span></span> <span data-ttu-id="2bb4c-110">V nový kód, zejména při vytváření objektů, použijte `Err` objektu `Raise` metoda ke generování chyb spuštění.</span><span class="sxs-lookup"><span data-stu-id="2bb4c-110">In new code, especially when creating objects, use the `Err` object's `Raise` method to generate run-time errors.</span></span>  
  
 <span data-ttu-id="2bb4c-111">Pokud `errornumber` je definována `Error` příkaz volá obslužnou rutinu chyby po vlastnosti `Err` objekt jsou přiřazeny následující výchozí hodnoty:</span><span class="sxs-lookup"><span data-stu-id="2bb4c-111">If `errornumber` is defined, the `Error` statement calls the error handler after the properties of the `Err` object are assigned the following default values:</span></span>  
  
|<span data-ttu-id="2bb4c-112">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="2bb4c-112">Property</span></span>|<span data-ttu-id="2bb4c-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2bb4c-113">Value</span></span>|  
|--------------|-----------|  
|`Number`|<span data-ttu-id="2bb4c-114">Hodnota zadaná jako argument `Error` příkaz.</span><span class="sxs-lookup"><span data-stu-id="2bb4c-114">Value specified as argument to `Error` statement.</span></span> <span data-ttu-id="2bb4c-115">Může být jakékoli platné číslo chyby.</span><span class="sxs-lookup"><span data-stu-id="2bb4c-115">Can be any valid error number.</span></span>|  
|`Source`|<span data-ttu-id="2bb4c-116">Název aktuálního projektu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2bb4c-116">Name of the current Visual Basic project.</span></span>|  
|`Description`|<span data-ttu-id="2bb4c-117">Řetězcový výraz odpovídající vrácenou hodnotu `Error` funkce pro zadaný `Number`, pokud existuje tento řetězec.</span><span class="sxs-lookup"><span data-stu-id="2bb4c-117">String expression corresponding to the return value of the `Error` function for the specified `Number`, if this string exists.</span></span> <span data-ttu-id="2bb4c-118">Pokud řetězec neexistuje, `Description` obsahuje řetězec nulové délky ("").</span><span class="sxs-lookup"><span data-stu-id="2bb4c-118">If the string does not exist, `Description` contains a zero-length string ("").</span></span>|  
|`HelpFile`|<span data-ttu-id="2bb4c-119">Plně kvalifikovaný jednotky, cesta a název souboru příslušné souboru nápovědy prostředí Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2bb4c-119">The fully qualified drive, path, and file name of the appropriate Visual Basic Help file.</span></span>|  
|`HelpContext`|<span data-ttu-id="2bb4c-120">Odpovídající Nápověda Visual Basic kontextu ID pro příslušné chyby do souboru `Number` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2bb4c-120">The appropriate Visual Basic Help file context ID for the error corresponding to the `Number` property.</span></span>|  
|`LastDLLError`|<span data-ttu-id="2bb4c-121">Nula.</span><span class="sxs-lookup"><span data-stu-id="2bb4c-121">Zero.</span></span>|  
  
 <span data-ttu-id="2bb4c-122">Pokud žádná obslužná rutina chyby existuje, nebo pokud je zapnuta žádná chybová zpráva se vytvoří a zobrazí z `Err` vlastnosti objektu.</span><span class="sxs-lookup"><span data-stu-id="2bb4c-122">If no error handler exists, or if none is enabled, an error message is created and displayed from the `Err` object properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2bb4c-123">Některé hostování aplikací Visual Basic nelze vytvořit objekty.</span><span class="sxs-lookup"><span data-stu-id="2bb4c-123">Some Visual Basic host applications cannot create objects.</span></span> <span data-ttu-id="2bb4c-124">Naleznete v dokumentaci k hostitelskou aplikaci k určení, zda může vytvořit tříd a objektů.</span><span class="sxs-lookup"><span data-stu-id="2bb4c-124">See your host application's documentation to determine whether it can create classes and objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2bb4c-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="2bb4c-125">Example</span></span>  
 <span data-ttu-id="2bb4c-126">Tento příklad používá `Error` příkaz ke generování číslo chyby 11.</span><span class="sxs-lookup"><span data-stu-id="2bb4c-126">This example uses the `Error` statement to generate error number 11.</span></span>  
  
```  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a><span data-ttu-id="2bb4c-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2bb4c-127">Requirements</span></span>  
 <span data-ttu-id="2bb4c-128">**Namespace:** [Microsoft.VisualBasic –](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="2bb4c-128">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="2bb4c-129">**Sestavení:** jazyka Visual Basic Runtime Library (v souboru Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="2bb4c-129">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bb4c-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="2bb4c-130">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>  
 <xref:Microsoft.VisualBasic.Information.Err%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>  
 [<span data-ttu-id="2bb4c-131">On Error – příkaz</span><span class="sxs-lookup"><span data-stu-id="2bb4c-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)  
 [<span data-ttu-id="2bb4c-132">Resume – příkaz</span><span class="sxs-lookup"><span data-stu-id="2bb4c-132">Resume Statement</span></span>](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [<span data-ttu-id="2bb4c-133">Chybové zprávy</span><span class="sxs-lookup"><span data-stu-id="2bb4c-133">Error Messages</span></span>](../../../visual-basic/language-reference/error-messages/index.md)
