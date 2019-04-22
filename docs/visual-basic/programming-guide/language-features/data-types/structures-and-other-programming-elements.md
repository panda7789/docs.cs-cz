---
title: Struktury a ostatní programovací elementy (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], arrays
- procedures [Visual Basic], structures as arguments to
- objects [Visual Basic], structure elements
- arrays [Visual Basic], structure elements
- nested structures [Visual Basic]
ms.assetid: 0f849313-ccd2-4c9a-acb9-69de6751c088
ms.openlocfilehash: a943bbdec617ba6c95685df3a4fcdb36b52def22
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819097"
---
# <a name="structures-and-other-programming-elements-visual-basic"></a><span data-ttu-id="f7f9b-102">Struktury a ostatní programovací elementy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f7f9b-102">Structures and Other Programming Elements (Visual Basic)</span></span>
<span data-ttu-id="f7f9b-103">Struktury můžete použít ve spojení s pole objektů a postupy, stejně jako mezi sebou.</span><span class="sxs-lookup"><span data-stu-id="f7f9b-103">You can use structures in conjunction with arrays, objects, and procedures, as well as with each other.</span></span> <span data-ttu-id="f7f9b-104">Interakce používají stejnou syntaxi jako tyto prvky použít jednotlivě.</span><span class="sxs-lookup"><span data-stu-id="f7f9b-104">The interactions use the same syntax as these elements use individually.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7f9b-105">Nelze inicializovat prvky struktury v deklaraci struktury.</span><span class="sxs-lookup"><span data-stu-id="f7f9b-105">You cannot initialize any of the structure elements in the structure declaration.</span></span> <span data-ttu-id="f7f9b-106">Pouze na prvky, které jsou deklarované se strukturovaným typem proměnné můžete přiřadit hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f7f9b-106">You can assign values only to elements of a variable that has been declared to be of a structure type.</span></span>  
  
## <a name="structures-and-arrays"></a><span data-ttu-id="f7f9b-107">Struktury a pole</span><span class="sxs-lookup"><span data-stu-id="f7f9b-107">Structures and Arrays</span></span>  
 <span data-ttu-id="f7f9b-108">Struktura může obsahovat pole jako jeden nebo více z jeho prvků.</span><span class="sxs-lookup"><span data-stu-id="f7f9b-108">A structure can contain an array as one or more of its elements.</span></span> <span data-ttu-id="f7f9b-109">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="f7f9b-109">The following example illustrates this.</span></span>  
  
```vb  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure   
```  
  
 <span data-ttu-id="f7f9b-110">Máte přístup k hodnoty pole v rámci struktury stejným způsobem, přístup k vlastnosti pro objekt.</span><span class="sxs-lookup"><span data-stu-id="f7f9b-110">You access the values of an array within a structure the same way you access a property on an object.</span></span> <span data-ttu-id="f7f9b-111">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="f7f9b-111">The following example illustrates this.</span></span>  
  
```vb  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 <span data-ttu-id="f7f9b-112">Můžete také deklarovat pole struktur.</span><span class="sxs-lookup"><span data-stu-id="f7f9b-112">You can also declare an array of structures.</span></span> <span data-ttu-id="f7f9b-113">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="f7f9b-113">The following example illustrates this.</span></span>  
  
```vb  
Dim allSystems(100) As systemInfo  
```  
  
 <span data-ttu-id="f7f9b-114">Můžete řídit stejnými pravidly pro přístup k součástem tato architektura data.</span><span class="sxs-lookup"><span data-stu-id="f7f9b-114">You follow the same rules to access the components of this data architecture.</span></span> <span data-ttu-id="f7f9b-115">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="f7f9b-115">The following example illustrates this.</span></span>  
  
```vb  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## <a name="structures-and-objects"></a><span data-ttu-id="f7f9b-116">Struktury a objekty</span><span class="sxs-lookup"><span data-stu-id="f7f9b-116">Structures and Objects</span></span>  
 <span data-ttu-id="f7f9b-117">Struktura může obsahovat objekt jako jeden nebo více z jeho prvků.</span><span class="sxs-lookup"><span data-stu-id="f7f9b-117">A structure can contain an object as one or more of its elements.</span></span> <span data-ttu-id="f7f9b-118">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="f7f9b-118">The following example illustrates this.</span></span>  
  
```vb  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 <span data-ttu-id="f7f9b-119">Používejte konkrétní objekt třídy v deklaraci, spíše než `Object`.</span><span class="sxs-lookup"><span data-stu-id="f7f9b-119">You should use a specific object class in such a declaration, rather than `Object`.</span></span>  
  
## <a name="structures-and-procedures"></a><span data-ttu-id="f7f9b-120">Struktury a postupy</span><span class="sxs-lookup"><span data-stu-id="f7f9b-120">Structures and Procedures</span></span>  
 <span data-ttu-id="f7f9b-121">Struktury lze předat jako argument procedury.</span><span class="sxs-lookup"><span data-stu-id="f7f9b-121">You can pass a structure as a procedure argument.</span></span> <span data-ttu-id="f7f9b-122">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="f7f9b-122">The following example illustrates this.</span></span>  
  
```vb  
Public currentCPUName As String = "700MHz Pentium compatible"  
Public currentMemorySize As Long = 256  
Public Sub fillSystem(ByRef someSystem As systemInfo)  
    someSystem.cPU = currentCPUName  
    someSystem.memory = currentMemorySize  
    someSystem.purchaseDate = Now  
End Sub  
```  
  
 <span data-ttu-id="f7f9b-123">Předchozí příklad předává struktury *odkazem*, což umožňuje postupu upravte jeho prvky tak, aby se změny projevily ve volajícím kódu.</span><span class="sxs-lookup"><span data-stu-id="f7f9b-123">The preceding example passes the structure *by reference*, which allows the procedure to modify its elements so that the changes take effect in the calling code.</span></span> <span data-ttu-id="f7f9b-124">Pokud chcete chránit proti takové změny struktury, předejte hodnotou.</span><span class="sxs-lookup"><span data-stu-id="f7f9b-124">If you want to protect a structure against such modification, pass it by value.</span></span>  
  
 <span data-ttu-id="f7f9b-125">Můžete se taky vrátit struktury z `Function` postup.</span><span class="sxs-lookup"><span data-stu-id="f7f9b-125">You can also return a structure from a `Function` procedure.</span></span> <span data-ttu-id="f7f9b-126">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="f7f9b-126">The following example illustrates this.</span></span>  
  
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
  
## <a name="structures-within-structures"></a><span data-ttu-id="f7f9b-127">Struktury v rámci struktury</span><span class="sxs-lookup"><span data-stu-id="f7f9b-127">Structures Within Structures</span></span>  
 <span data-ttu-id="f7f9b-128">Struktury mohou obsahovat jiné struktury.</span><span class="sxs-lookup"><span data-stu-id="f7f9b-128">Structures can contain other structures.</span></span> <span data-ttu-id="f7f9b-129">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="f7f9b-129">The following example illustrates this.</span></span>  
  
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
  
 <span data-ttu-id="f7f9b-130">Tento postup lze také použít k zapouzdření struktuře definované v jeden modul v rámci struktury definované v jiný modul.</span><span class="sxs-lookup"><span data-stu-id="f7f9b-130">You can also use this technique to encapsulate a structure defined in one module within a structure defined in a different module.</span></span>  
  
 <span data-ttu-id="f7f9b-131">Struktury mohou obsahovat další struktury do libovolné hloubky.</span><span class="sxs-lookup"><span data-stu-id="f7f9b-131">Structures can contain other structures to an arbitrary depth.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7f9b-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f7f9b-132">See also</span></span>

- [<span data-ttu-id="f7f9b-133">Datové typy</span><span class="sxs-lookup"><span data-stu-id="f7f9b-133">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="f7f9b-134">Základní datové typy</span><span class="sxs-lookup"><span data-stu-id="f7f9b-134">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="f7f9b-135">Složené datové typy</span><span class="sxs-lookup"><span data-stu-id="f7f9b-135">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="f7f9b-136">Typy hodnot a odkazové typy</span><span class="sxs-lookup"><span data-stu-id="f7f9b-136">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="f7f9b-137">Struktury</span><span class="sxs-lookup"><span data-stu-id="f7f9b-137">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="f7f9b-138">Řešení potíží s datovými typy</span><span class="sxs-lookup"><span data-stu-id="f7f9b-138">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="f7f9b-139">Postupy: Deklarace struktury</span><span class="sxs-lookup"><span data-stu-id="f7f9b-139">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="f7f9b-140">Proměnné struktury</span><span class="sxs-lookup"><span data-stu-id="f7f9b-140">Structure Variables</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)
- [<span data-ttu-id="f7f9b-141">Struktury a třídy</span><span class="sxs-lookup"><span data-stu-id="f7f9b-141">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [<span data-ttu-id="f7f9b-142">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="f7f9b-142">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
