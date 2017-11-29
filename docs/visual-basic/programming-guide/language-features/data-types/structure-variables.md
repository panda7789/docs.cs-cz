---
title: "Proměnné struktury (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ef42c44de84caffde909eb2b3e9361016a6abb97
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="structure-variables-visual-basic"></a><span data-ttu-id="e28eb-102">Proměnné struktury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e28eb-102">Structure Variables (Visual Basic)</span></span>
<span data-ttu-id="e28eb-103">Jakmile vytvoříte strukturu, můžou deklarovat proměnné úroveň procedury a úroveň modulu jako typu.</span><span class="sxs-lookup"><span data-stu-id="e28eb-103">Once you have created a structure, you can declare procedure-level and module-level variables as that type.</span></span> <span data-ttu-id="e28eb-104">Můžete například vytvořit strukturu aby zaznamenávalo informace o systému počítače.</span><span class="sxs-lookup"><span data-stu-id="e28eb-104">For example, you can create a structure that records information about a computer system.</span></span> <span data-ttu-id="e28eb-105">Následující příklad ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="e28eb-105">The following example demonstrates this.</span></span>  
  
```  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public purchaseDate As Date  
End Structure  
```  
  
 <span data-ttu-id="e28eb-106">Nyní je možné deklarovat proměnné daného typu.</span><span class="sxs-lookup"><span data-stu-id="e28eb-106">You can now declare variables of that type.</span></span> <span data-ttu-id="e28eb-107">To ukazuje následující prohlášení.</span><span class="sxs-lookup"><span data-stu-id="e28eb-107">The following declaration illustrates this.</span></span>  
  
```  
Dim mySystem, yourSystem As systemInfo  
```  
  
> [!NOTE]
>  <span data-ttu-id="e28eb-108">Třídy a moduly, struktury deklarováno s použitím [Dim – příkaz](../../../../visual-basic/language-reference/statements/dim-statement.md) výchozí nastavení veřejný přístup.</span><span class="sxs-lookup"><span data-stu-id="e28eb-108">In classes and modules, structures declared using the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) default to public access.</span></span> <span data-ttu-id="e28eb-109">Pokud máte v úmyslu struktura důvěrné, ujistěte se, je pomocí deklarovat [privátní](../../../../visual-basic/language-reference/modifiers/private.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="e28eb-109">If you intend a structure to be private, make sure you declare it using the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword.</span></span>  
  
## <a name="access-to-structure-values"></a><span data-ttu-id="e28eb-110">Přístup k hodnotám struktura</span><span class="sxs-lookup"><span data-stu-id="e28eb-110">Access to Structure Values</span></span>  
 <span data-ttu-id="e28eb-111">Pokud chcete přiřadit a načtení hodnoty z elementů struktura proměnné, použijte stejnou syntaxi jako použijte k nastavení a získat vlastnosti objektu.</span><span class="sxs-lookup"><span data-stu-id="e28eb-111">To assign and retrieve values from the elements of a structure variable, you use the same syntax as you use to set and get properties on an object.</span></span> <span data-ttu-id="e28eb-112">Umístěte operátor přístupu členů (`.`) mezi názvu proměnné struktura a název elementu.</span><span class="sxs-lookup"><span data-stu-id="e28eb-112">You place the member access operator (`.`) between the structure variable name and the element name.</span></span> <span data-ttu-id="e28eb-113">Následující příklad používá elementy proměnných dříve deklarované jako typ `systemInfo`.</span><span class="sxs-lookup"><span data-stu-id="e28eb-113">The following example accesses elements of the variables previously declared as type `systemInfo`.</span></span>  
  
```  
mySystem.cPU = "486"  
Dim tooOld As Boolean  
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True  
```  
  
## <a name="assigning-structure-variables"></a><span data-ttu-id="e28eb-114">Přiřazení proměnné struktury</span><span class="sxs-lookup"><span data-stu-id="e28eb-114">Assigning Structure Variables</span></span>  
 <span data-ttu-id="e28eb-115">Můžete také přiřadit jednu proměnnou do jiného, pokud jsou obě stejného typu Struktura.</span><span class="sxs-lookup"><span data-stu-id="e28eb-115">You can also assign one variable to another if both are of the same structure type.</span></span> <span data-ttu-id="e28eb-116">Zkopíruje všechny elementy struktury jeden odpovídající elementům ve druhé.</span><span class="sxs-lookup"><span data-stu-id="e28eb-116">This copies all the elements of one structure to the corresponding elements in the other.</span></span> <span data-ttu-id="e28eb-117">To ukazuje následující prohlášení.</span><span class="sxs-lookup"><span data-stu-id="e28eb-117">The following declaration illustrates this.</span></span>  
  
```  
yourSystem = mySystem  
```  
  
 <span data-ttu-id="e28eb-118">Pokud element struktura, jako je typu odkazu `String`, `Object`, nebo se zkopíruje pole, které má ukazatel na data.</span><span class="sxs-lookup"><span data-stu-id="e28eb-118">If a structure element is a reference type, such as a `String`, `Object`, or array, the pointer to the data is copied.</span></span> <span data-ttu-id="e28eb-119">V předchozím příkladu Pokud `systemInfo` měl zahrnuté proměnné objektu, pak by ukazatel z zkopírovali v předchozím příkladu `mySystem` k `yourSystem`, a ke změně dat objektu prostřednictvím jedné struktury by platný při přístupu k prostřednictvím jiné struktury.</span><span class="sxs-lookup"><span data-stu-id="e28eb-119">In the previous example, if `systemInfo` had included an object variable, then the preceding example would have copied the pointer from `mySystem` to `yourSystem`, and a change to the object's data through one structure would be in effect when accessed through the other structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e28eb-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="e28eb-120">See Also</span></span>  
 [<span data-ttu-id="e28eb-121">Datové typy</span><span class="sxs-lookup"><span data-stu-id="e28eb-121">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="e28eb-122">Základní datové typy</span><span class="sxs-lookup"><span data-stu-id="e28eb-122">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [<span data-ttu-id="e28eb-123">Složené datové typy</span><span class="sxs-lookup"><span data-stu-id="e28eb-123">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [<span data-ttu-id="e28eb-124">Typy hodnot a odkazové typy</span><span class="sxs-lookup"><span data-stu-id="e28eb-124">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="e28eb-125">Struktury</span><span class="sxs-lookup"><span data-stu-id="e28eb-125">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="e28eb-126">Řešení potíží s datové typy</span><span class="sxs-lookup"><span data-stu-id="e28eb-126">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="e28eb-127">Postupy: definice struktury</span><span class="sxs-lookup"><span data-stu-id="e28eb-127">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="e28eb-128">Struktury a ostatní programovací elementy</span><span class="sxs-lookup"><span data-stu-id="e28eb-128">Structures and Other Programming Elements</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)  
 [<span data-ttu-id="e28eb-129">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="e28eb-129">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 [<span data-ttu-id="e28eb-130">Structure – příkaz</span><span class="sxs-lookup"><span data-stu-id="e28eb-130">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
