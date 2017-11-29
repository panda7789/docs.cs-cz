---
title: "Struktury a ostatní programovací elementy (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- structures [Visual Basic], arrays
- procedures [Visual Basic], structures as arguments to
- objects [Visual Basic], structure elements
- arrays [Visual Basic], structure elements
- nested structures [Visual Basic]
ms.assetid: 0f849313-ccd2-4c9a-acb9-69de6751c088
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: de343c06ec255d6cb68aa25d733e85385e884769
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="structures-and-other-programming-elements-visual-basic"></a><span data-ttu-id="3dc96-102">Struktury a ostatní programovací elementy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3dc96-102">Structures and Other Programming Elements (Visual Basic)</span></span>
<span data-ttu-id="3dc96-103">Struktury můžete použít ve spojení se pole, objekty a postupů, a také mezi sebou.</span><span class="sxs-lookup"><span data-stu-id="3dc96-103">You can use structures in conjunction with arrays, objects, and procedures, as well as with each other.</span></span> <span data-ttu-id="3dc96-104">Interakce používají stejnou syntaxi jako tyto prvky použijte jednotlivě.</span><span class="sxs-lookup"><span data-stu-id="3dc96-104">The interactions use the same syntax as these elements use individually.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3dc96-105">Nelze inicializovat všechny elementy struktury v deklarace struktury.</span><span class="sxs-lookup"><span data-stu-id="3dc96-105">You cannot initialize any of the structure elements in the structure declaration.</span></span> <span data-ttu-id="3dc96-106">Hodnoty můžete přiřadit pouze na elementy proměnné, která byla deklarována jako struktura typu.</span><span class="sxs-lookup"><span data-stu-id="3dc96-106">You can assign values only to elements of a variable that has been declared to be of a structure type.</span></span>  
  
## <a name="structures-and-arrays"></a><span data-ttu-id="3dc96-107">Struktury a pole</span><span class="sxs-lookup"><span data-stu-id="3dc96-107">Structures and Arrays</span></span>  
 <span data-ttu-id="3dc96-108">Struktury může obsahovat pole jako jeden nebo více jeho elementy.</span><span class="sxs-lookup"><span data-stu-id="3dc96-108">A structure can contain an array as one or more of its elements.</span></span> <span data-ttu-id="3dc96-109">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="3dc96-109">The following example illustrates this.</span></span>  
  
```vb  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure   
```  
  
 <span data-ttu-id="3dc96-110">Hodnoty pole v rámci struktury přístup stejným způsobem jako přístup k vlastnosti objektu.</span><span class="sxs-lookup"><span data-stu-id="3dc96-110">You access the values of an array within a structure the same way you access a property on an object.</span></span> <span data-ttu-id="3dc96-111">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="3dc96-111">The following example illustrates this.</span></span>  
  
```vb  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 <span data-ttu-id="3dc96-112">Můžete také deklarovat pole struktury.</span><span class="sxs-lookup"><span data-stu-id="3dc96-112">You can also declare an array of structures.</span></span> <span data-ttu-id="3dc96-113">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="3dc96-113">The following example illustrates this.</span></span>  
  
```vb  
Dim allSystems(100) As systemInfo  
```  
  
 <span data-ttu-id="3dc96-114">Provedením stejná pravidla pro přístup k součástem této architektury data.</span><span class="sxs-lookup"><span data-stu-id="3dc96-114">You follow the same rules to access the components of this data architecture.</span></span> <span data-ttu-id="3dc96-115">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="3dc96-115">The following example illustrates this.</span></span>  
  
```vb  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## <a name="structures-and-objects"></a><span data-ttu-id="3dc96-116">Struktury a objekty</span><span class="sxs-lookup"><span data-stu-id="3dc96-116">Structures and Objects</span></span>  
 <span data-ttu-id="3dc96-117">Struktury může obsahovat objekt jako jeden nebo více jeho elementy.</span><span class="sxs-lookup"><span data-stu-id="3dc96-117">A structure can contain an object as one or more of its elements.</span></span> <span data-ttu-id="3dc96-118">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="3dc96-118">The following example illustrates this.</span></span>  
  
```vb  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 <span data-ttu-id="3dc96-119">Ve deklarace, byste měli používat konkrétní objekt třídy místo `Object`.</span><span class="sxs-lookup"><span data-stu-id="3dc96-119">You should use a specific object class in such a declaration, rather than `Object`.</span></span>  
  
## <a name="structures-and-procedures"></a><span data-ttu-id="3dc96-120">Struktury a postupy</span><span class="sxs-lookup"><span data-stu-id="3dc96-120">Structures and Procedures</span></span>  
 <span data-ttu-id="3dc96-121">Můžete předat do struktury jako argumentu procedury.</span><span class="sxs-lookup"><span data-stu-id="3dc96-121">You can pass a structure as a procedure argument.</span></span> <span data-ttu-id="3dc96-122">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="3dc96-122">The following example illustrates this.</span></span>  
  
```vb  
Public currentCPUName As String = "700MHz Pentium compatible"  
Public currentMemorySize As Long = 256  
Public Sub fillSystem(ByRef someSystem As systemInfo)  
    someSystem.cPU = currentCPUName  
    someSystem.memory = currentMemorySize  
    someSystem.purchaseDate = Now  
End Sub  
```  
  
 <span data-ttu-id="3dc96-123">V předchozím příkladu předá strukturu *odkazem*, což umožňuje postupu upravte jeho elementy, aby byl změny se projeví ve volání kódu.</span><span class="sxs-lookup"><span data-stu-id="3dc96-123">The preceding example passes the structure *by reference*, which allows the procedure to modify its elements so that the changes take effect in the calling code.</span></span> <span data-ttu-id="3dc96-124">Pokud chcete chránit struktura proti takové úpravy, předejte jej hodnotou.</span><span class="sxs-lookup"><span data-stu-id="3dc96-124">If you want to protect a structure against such modification, pass it by value.</span></span>  
  
 <span data-ttu-id="3dc96-125">Můžete se taky vrátit do struktury z `Function` postupu.</span><span class="sxs-lookup"><span data-stu-id="3dc96-125">You can also return a structure from a `Function` procedure.</span></span> <span data-ttu-id="3dc96-126">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="3dc96-126">The following example illustrates this.</span></span>  
  
```vb  
Dim allSystems(100) As systemInfo  
Function findByDate(ByVal searchDate As Date) As systemInfo  
    Dim i As Integer  
    For i = 1 To 100  
        If allSystems(i).purchaseDate = searchDate Then Return allSystems(i)  
    Next i  
   ' Process error: system with desired purchase date not found.  
End Function  
```  
  
## <a name="structures-within-structures"></a><span data-ttu-id="3dc96-127">Struktury v rámci struktury</span><span class="sxs-lookup"><span data-stu-id="3dc96-127">Structures Within Structures</span></span>  
 <span data-ttu-id="3dc96-128">Struktury může obsahovat jiné struktury.</span><span class="sxs-lookup"><span data-stu-id="3dc96-128">Structures can contain other structures.</span></span> <span data-ttu-id="3dc96-129">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="3dc96-129">The following example illustrates this.</span></span>  
  
```vb  
Public Structure driveInfo  
    Public type As String  
    Public size As Long  
End Structure  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As driveInfo  
    Public purchaseDate As Date  
End Structure  
```  
  
```vb  
Dim allSystems(100) As systemInfo  
ReDim allSystems(1).diskDrives(3)  
allSystems(1).diskDrives(0).type = "Floppy"  
```  
  
 <span data-ttu-id="3dc96-130">Tento postup můžete taky zapouzdření struktuře definované v jeden modul v rámci struktuře definované v různých modulu.</span><span class="sxs-lookup"><span data-stu-id="3dc96-130">You can also use this technique to encapsulate a structure defined in one module within a structure defined in a different module.</span></span>  
  
 <span data-ttu-id="3dc96-131">Struktury může obsahovat jiné struktur pro libovolný hloubka.</span><span class="sxs-lookup"><span data-stu-id="3dc96-131">Structures can contain other structures to an arbitrary depth.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dc96-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="3dc96-132">See Also</span></span>  
 [<span data-ttu-id="3dc96-133">Datové typy</span><span class="sxs-lookup"><span data-stu-id="3dc96-133">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="3dc96-134">Základní datové typy</span><span class="sxs-lookup"><span data-stu-id="3dc96-134">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [<span data-ttu-id="3dc96-135">Složené datové typy</span><span class="sxs-lookup"><span data-stu-id="3dc96-135">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [<span data-ttu-id="3dc96-136">Typy hodnot a odkazové typy</span><span class="sxs-lookup"><span data-stu-id="3dc96-136">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="3dc96-137">Struktury</span><span class="sxs-lookup"><span data-stu-id="3dc96-137">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="3dc96-138">Řešení potíží s datové typy</span><span class="sxs-lookup"><span data-stu-id="3dc96-138">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="3dc96-139">Postupy: definice struktury</span><span class="sxs-lookup"><span data-stu-id="3dc96-139">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="3dc96-140">Proměnné struktury</span><span class="sxs-lookup"><span data-stu-id="3dc96-140">Structure Variables</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)  
 [<span data-ttu-id="3dc96-141">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="3dc96-141">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 [<span data-ttu-id="3dc96-142">Structure – příkaz</span><span class="sxs-lookup"><span data-stu-id="3dc96-142">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
