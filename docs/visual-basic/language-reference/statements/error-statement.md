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
ms.openlocfilehash: 35ba1f19654d1d23ac1ec73564bc36b0af4f6777
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404742"
---
# <a name="error-statement"></a><span data-ttu-id="76ee3-102">Error – příkaz</span><span class="sxs-lookup"><span data-stu-id="76ee3-102">Error Statement</span></span>
<span data-ttu-id="76ee3-103">Simuluje výskyt chyby.</span><span class="sxs-lookup"><span data-stu-id="76ee3-103">Simulates the occurrence of an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76ee3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="76ee3-104">Syntax</span></span>  
  
```vb  
Error errornumber  
```  
  
## <a name="parts"></a><span data-ttu-id="76ee3-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="76ee3-105">Parts</span></span>  
 `errornumber`  
 <span data-ttu-id="76ee3-106">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="76ee3-106">Required.</span></span> <span data-ttu-id="76ee3-107">Může to být jakékoli platné číslo chyby.</span><span class="sxs-lookup"><span data-stu-id="76ee3-107">Can be any valid error number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76ee3-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="76ee3-108">Remarks</span></span>  
 <span data-ttu-id="76ee3-109">`Error`Příkaz se podporuje kvůli zpětné kompatibilitě.</span><span class="sxs-lookup"><span data-stu-id="76ee3-109">The `Error` statement is supported for backward compatibility.</span></span> <span data-ttu-id="76ee3-110">V novém kódu, zejména při vytváření objektů, použijte `Err` `Raise` metodu objektu pro generování běhových chyb.</span><span class="sxs-lookup"><span data-stu-id="76ee3-110">In new code, especially when creating objects, use the `Err` object's `Raise` method to generate run-time errors.</span></span>  
  
 <span data-ttu-id="76ee3-111">Pokud `errornumber` je definován, `Error` příkaz zavolá obslužnou rutinu chyby poté, co `Err` jsou vlastnosti objektu přiřazeny následující výchozí hodnoty:</span><span class="sxs-lookup"><span data-stu-id="76ee3-111">If `errornumber` is defined, the `Error` statement calls the error handler after the properties of the `Err` object are assigned the following default values:</span></span>  
  
|<span data-ttu-id="76ee3-112">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="76ee3-112">Property</span></span>|<span data-ttu-id="76ee3-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="76ee3-113">Value</span></span>|  
|--------------|-----------|  
|`Number`|<span data-ttu-id="76ee3-114">Hodnota zadaná jako argument `Error` into příkazu</span><span class="sxs-lookup"><span data-stu-id="76ee3-114">Value specified as argument to `Error` statement.</span></span> <span data-ttu-id="76ee3-115">Může to být jakékoli platné číslo chyby.</span><span class="sxs-lookup"><span data-stu-id="76ee3-115">Can be any valid error number.</span></span>|  
|`Source`|<span data-ttu-id="76ee3-116">Název aktuálního projektu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="76ee3-116">Name of the current Visual Basic project.</span></span>|  
|`Description`|<span data-ttu-id="76ee3-117">Řetězcový výraz odpovídající vrácené hodnotě `Error` funkce pro zadanou hodnotu `Number` , pokud tento řetězec existuje.</span><span class="sxs-lookup"><span data-stu-id="76ee3-117">String expression corresponding to the return value of the `Error` function for the specified `Number`, if this string exists.</span></span> <span data-ttu-id="76ee3-118">Pokud řetězec neexistuje, `Description` obsahuje řetězec s nulovou délkou ("").</span><span class="sxs-lookup"><span data-stu-id="76ee3-118">If the string does not exist, `Description` contains a zero-length string ("").</span></span>|  
|`HelpFile`|<span data-ttu-id="76ee3-119">Plně kvalifikovaná jednotka, cesta a název souboru pro příslušný soubor s Visual Basic Help.</span><span class="sxs-lookup"><span data-stu-id="76ee3-119">The fully qualified drive, path, and file name of the appropriate Visual Basic Help file.</span></span>|  
|`HelpContext`|<span data-ttu-id="76ee3-120">Příslušné ID kontextového souboru Help Visual Basic pro chybu odpovídající `Number` Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="76ee3-120">The appropriate Visual Basic Help file context ID for the error corresponding to the `Number` property.</span></span>|  
|`LastDLLError`|<span data-ttu-id="76ee3-121">0</span><span class="sxs-lookup"><span data-stu-id="76ee3-121">Zero.</span></span>|  
  
 <span data-ttu-id="76ee3-122">Pokud neexistují žádné obslužné rutiny chyb nebo pokud není žádná povolená, vytvoří se chybová zpráva, která se zobrazí z `Err` vlastností objektu.</span><span class="sxs-lookup"><span data-stu-id="76ee3-122">If no error handler exists, or if none is enabled, an error message is created and displayed from the `Err` object properties.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="76ee3-123">Některé hostitelské aplikace Visual Basic nemůžou vytvářet objekty.</span><span class="sxs-lookup"><span data-stu-id="76ee3-123">Some Visual Basic host applications cannot create objects.</span></span> <span data-ttu-id="76ee3-124">Informace o tom, zda může vytvořit třídy a objekty, naleznete v dokumentaci hostitelské aplikace.</span><span class="sxs-lookup"><span data-stu-id="76ee3-124">See your host application's documentation to determine whether it can create classes and objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76ee3-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="76ee3-125">Example</span></span>  
 <span data-ttu-id="76ee3-126">V tomto příkladu se pomocí `Error` příkazu vygeneruje chybová zpráva číslo 11.</span><span class="sxs-lookup"><span data-stu-id="76ee3-126">This example uses the `Error` statement to generate error number 11.</span></span>  
  
```vb  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a><span data-ttu-id="76ee3-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="76ee3-127">Requirements</span></span>  
 <span data-ttu-id="76ee3-128">**Obor názvů:** [Microsoft. VisualBasic](../runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="76ee3-128">**Namespace:** [Microsoft.VisualBasic](../runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="76ee3-129">**Sestavení:** Knihovna Visual Basic runtime (v souboru Microsoft. VisualBasic. dll)</span><span class="sxs-lookup"><span data-stu-id="76ee3-129">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76ee3-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="76ee3-130">See also</span></span>

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [<span data-ttu-id="76ee3-131">On Error – příkaz</span><span class="sxs-lookup"><span data-stu-id="76ee3-131">On Error Statement</span></span>](on-error-statement.md)
- [<span data-ttu-id="76ee3-132">Resume – příkaz</span><span class="sxs-lookup"><span data-stu-id="76ee3-132">Resume Statement</span></span>](resume-statement.md)
- [<span data-ttu-id="76ee3-133">Chybové zprávy</span><span class="sxs-lookup"><span data-stu-id="76ee3-133">Error Messages</span></span>](../error-messages/index.md)
