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
ms.openlocfilehash: ec65c75fcfd907097f1cd1e0d3092a547272a782
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933247"
---
# <a name="structures-and-other-programming-elements-visual-basic"></a><span data-ttu-id="611e4-102">Struktury a ostatní programovací elementy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="611e4-102">Structures and Other Programming Elements (Visual Basic)</span></span>
<span data-ttu-id="611e4-103">Struktury můžete používat ve spojení s poli, objekty a procedurami a také mezi sebou.</span><span class="sxs-lookup"><span data-stu-id="611e4-103">You can use structures in conjunction with arrays, objects, and procedures, as well as with each other.</span></span> <span data-ttu-id="611e4-104">Interakce používají stejnou syntaxi, protože tyto prvky používají samostatně.</span><span class="sxs-lookup"><span data-stu-id="611e4-104">The interactions use the same syntax as these elements use individually.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="611e4-105">V deklaraci struktury nelze inicializovat žádné prvky struktury.</span><span class="sxs-lookup"><span data-stu-id="611e4-105">You cannot initialize any of the structure elements in the structure declaration.</span></span> <span data-ttu-id="611e4-106">Hodnoty lze přiřadit pouze k prvkům proměnné, které byly deklarovány jako typ struktury.</span><span class="sxs-lookup"><span data-stu-id="611e4-106">You can assign values only to elements of a variable that has been declared to be of a structure type.</span></span>  
  
## <a name="structures-and-arrays"></a><span data-ttu-id="611e4-107">Struktury a pole</span><span class="sxs-lookup"><span data-stu-id="611e4-107">Structures and Arrays</span></span>  
 <span data-ttu-id="611e4-108">Struktura může obsahovat pole jako jeden nebo více jeho prvků.</span><span class="sxs-lookup"><span data-stu-id="611e4-108">A structure can contain an array as one or more of its elements.</span></span> <span data-ttu-id="611e4-109">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="611e4-109">The following example illustrates this.</span></span>  
  
```vb  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure   
```  
  
 <span data-ttu-id="611e4-110">Přístup k hodnotám pole v rámci struktury je stejný způsob, jakým přistupujete k vlastnosti objektu.</span><span class="sxs-lookup"><span data-stu-id="611e4-110">You access the values of an array within a structure the same way you access a property on an object.</span></span> <span data-ttu-id="611e4-111">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="611e4-111">The following example illustrates this.</span></span>  
  
```vb  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 <span data-ttu-id="611e4-112">Můžete také deklarovat pole struktur.</span><span class="sxs-lookup"><span data-stu-id="611e4-112">You can also declare an array of structures.</span></span> <span data-ttu-id="611e4-113">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="611e4-113">The following example illustrates this.</span></span>  
  
```vb  
Dim allSystems(100) As systemInfo  
```  
  
 <span data-ttu-id="611e4-114">Pro přístup k součástem této architektury dat se řiďte stejná pravidla.</span><span class="sxs-lookup"><span data-stu-id="611e4-114">You follow the same rules to access the components of this data architecture.</span></span> <span data-ttu-id="611e4-115">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="611e4-115">The following example illustrates this.</span></span>  
  
```vb  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## <a name="structures-and-objects"></a><span data-ttu-id="611e4-116">Struktury a objekty</span><span class="sxs-lookup"><span data-stu-id="611e4-116">Structures and Objects</span></span>  
 <span data-ttu-id="611e4-117">Struktura může obsahovat objekt jako jeden nebo více jeho prvků.</span><span class="sxs-lookup"><span data-stu-id="611e4-117">A structure can contain an object as one or more of its elements.</span></span> <span data-ttu-id="611e4-118">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="611e4-118">The following example illustrates this.</span></span>  
  
```vb  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 <span data-ttu-id="611e4-119">V takové deklaraci byste měli použít konkrétní třídu objektu, nikoli `Object`.</span><span class="sxs-lookup"><span data-stu-id="611e4-119">You should use a specific object class in such a declaration, rather than `Object`.</span></span>  
  
## <a name="structures-and-procedures"></a><span data-ttu-id="611e4-120">Struktury a postupy</span><span class="sxs-lookup"><span data-stu-id="611e4-120">Structures and Procedures</span></span>  
 <span data-ttu-id="611e4-121">Strukturu můžete předat jako argument procedury.</span><span class="sxs-lookup"><span data-stu-id="611e4-121">You can pass a structure as a procedure argument.</span></span> <span data-ttu-id="611e4-122">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="611e4-122">The following example illustrates this.</span></span>  
  
```vb  
Public currentCPUName As String = "700MHz Pentium compatible"  
Public currentMemorySize As Long = 256  
Public Sub fillSystem(ByRef someSystem As systemInfo)  
    someSystem.cPU = currentCPUName  
    someSystem.memory = currentMemorySize  
    someSystem.purchaseDate = Now  
End Sub  
```  
  
 <span data-ttu-id="611e4-123">Předchozí příklad předá strukturu *odkazem*, což umožňuje, aby procedura změnila své prvky tak, aby se změny projevily v volajícím kódu.</span><span class="sxs-lookup"><span data-stu-id="611e4-123">The preceding example passes the structure *by reference*, which allows the procedure to modify its elements so that the changes take effect in the calling code.</span></span> <span data-ttu-id="611e4-124">Pokud chcete chránit strukturu pro takovou úpravu, předejte ji podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="611e4-124">If you want to protect a structure against such modification, pass it by value.</span></span>  
  
 <span data-ttu-id="611e4-125">Můžete také vrátit strukturu z `Function` procedury.</span><span class="sxs-lookup"><span data-stu-id="611e4-125">You can also return a structure from a `Function` procedure.</span></span> <span data-ttu-id="611e4-126">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="611e4-126">The following example illustrates this.</span></span>  
  
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
  
## <a name="structures-within-structures"></a><span data-ttu-id="611e4-127">Struktury ve strukturách</span><span class="sxs-lookup"><span data-stu-id="611e4-127">Structures Within Structures</span></span>  
 <span data-ttu-id="611e4-128">Struktury mohou obsahovat jiné struktury.</span><span class="sxs-lookup"><span data-stu-id="611e4-128">Structures can contain other structures.</span></span> <span data-ttu-id="611e4-129">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="611e4-129">The following example illustrates this.</span></span>  
  
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
  
 <span data-ttu-id="611e4-130">Tento postup můžete použít také k zapouzdření struktury definované v jednom modulu v rámci struktury definované v jiném modulu.</span><span class="sxs-lookup"><span data-stu-id="611e4-130">You can also use this technique to encapsulate a structure defined in one module within a structure defined in a different module.</span></span>  
  
 <span data-ttu-id="611e4-131">Struktury mohou obsahovat jiné struktury s libovolnou hloubkou.</span><span class="sxs-lookup"><span data-stu-id="611e4-131">Structures can contain other structures to an arbitrary depth.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="611e4-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="611e4-132">See also</span></span>

- [<span data-ttu-id="611e4-133">Datové typy</span><span class="sxs-lookup"><span data-stu-id="611e4-133">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="611e4-134">Základní datové typy</span><span class="sxs-lookup"><span data-stu-id="611e4-134">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="611e4-135">Složené datové typy</span><span class="sxs-lookup"><span data-stu-id="611e4-135">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="611e4-136">Typy hodnot a odkazové typy</span><span class="sxs-lookup"><span data-stu-id="611e4-136">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="611e4-137">Struktury</span><span class="sxs-lookup"><span data-stu-id="611e4-137">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="611e4-138">Řešení potíží s datovými typy</span><span class="sxs-lookup"><span data-stu-id="611e4-138">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="611e4-139">Postupy: Deklarace struktury</span><span class="sxs-lookup"><span data-stu-id="611e4-139">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="611e4-140">Proměnné struktury</span><span class="sxs-lookup"><span data-stu-id="611e4-140">Structure Variables</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)
- [<span data-ttu-id="611e4-141">Struktury a třídy</span><span class="sxs-lookup"><span data-stu-id="611e4-141">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [<span data-ttu-id="611e4-142">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="611e4-142">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
