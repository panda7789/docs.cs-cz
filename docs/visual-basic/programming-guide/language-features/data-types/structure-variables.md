---
title: Proměnné struktury (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
ms.openlocfilehash: 9a6e542e297a17f44d929235530ae6058cf13a36
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663385"
---
# <a name="structure-variables-visual-basic"></a><span data-ttu-id="af2e2-102">Proměnné struktury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af2e2-102">Structure Variables (Visual Basic)</span></span>
<span data-ttu-id="af2e2-103">Po vytvoření struktury můžete deklarovat proměnné, postup úroveň a úroveň modulu jako tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="af2e2-103">Once you have created a structure, you can declare procedure-level and module-level variables as that type.</span></span> <span data-ttu-id="af2e2-104">Můžete například vytvořit strukturu tohoto zaznamenává informace o systému počítače.</span><span class="sxs-lookup"><span data-stu-id="af2e2-104">For example, you can create a structure that records information about a computer system.</span></span> <span data-ttu-id="af2e2-105">Následující příklad ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="af2e2-105">The following example demonstrates this.</span></span>  
  
```  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public purchaseDate As Date  
End Structure  
```  
  
 <span data-ttu-id="af2e2-106">Nyní můžete deklarovat proměnné tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="af2e2-106">You can now declare variables of that type.</span></span> <span data-ttu-id="af2e2-107">To znázorňuje následující deklarace.</span><span class="sxs-lookup"><span data-stu-id="af2e2-107">The following declaration illustrates this.</span></span>  
  
```  
Dim mySystem, yourSystem As systemInfo  
```  
  
> [!NOTE]
>  <span data-ttu-id="af2e2-108">Ve třídách a moduly, struktur deklarované pomocí [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) výchozí veřejný přístup.</span><span class="sxs-lookup"><span data-stu-id="af2e2-108">In classes and modules, structures declared using the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) default to public access.</span></span> <span data-ttu-id="af2e2-109">Pokud máte v úmyslu struktura bude privátní, ujistěte se, že deklarujete jej s použitím [privátní](../../../../visual-basic/language-reference/modifiers/private.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="af2e2-109">If you intend a structure to be private, make sure you declare it using the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword.</span></span>  
  
## <a name="access-to-structure-values"></a><span data-ttu-id="af2e2-110">Přístup k hodnotám struktura</span><span class="sxs-lookup"><span data-stu-id="af2e2-110">Access to Structure Values</span></span>  
 <span data-ttu-id="af2e2-111">Přiřazení a načítat hodnoty z elementů proměnnou struktury, použijete stejnou syntaxi jako použijte k nastavení a načtení vlastností pro objekt.</span><span class="sxs-lookup"><span data-stu-id="af2e2-111">To assign and retrieve values from the elements of a structure variable, you use the same syntax as you use to set and get properties on an object.</span></span> <span data-ttu-id="af2e2-112">Umístit operátor přístupu členů (`.`) mezi názvem proměnné struktury a název elementu.</span><span class="sxs-lookup"><span data-stu-id="af2e2-112">You place the member access operator (`.`) between the structure variable name and the element name.</span></span> <span data-ttu-id="af2e2-113">Následující příklad přistupuje k prvky proměnných dříve deklarovány jako typ `systemInfo`.</span><span class="sxs-lookup"><span data-stu-id="af2e2-113">The following example accesses elements of the variables previously declared as type `systemInfo`.</span></span>  
  
```  
mySystem.cPU = "486"  
Dim tooOld As Boolean  
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True  
```  
  
## <a name="assigning-structure-variables"></a><span data-ttu-id="af2e2-114">Přiřazení proměnné struktury</span><span class="sxs-lookup"><span data-stu-id="af2e2-114">Assigning Structure Variables</span></span>  
 <span data-ttu-id="af2e2-115">Můžete také přiřadit jednu proměnnou do jiného, pokud jsou obě stejného typu Struktura.</span><span class="sxs-lookup"><span data-stu-id="af2e2-115">You can also assign one variable to another if both are of the same structure type.</span></span> <span data-ttu-id="af2e2-116">To zkopíruje všechny prvky z jedné struktury na odpovídající elementy v jiném.</span><span class="sxs-lookup"><span data-stu-id="af2e2-116">This copies all the elements of one structure to the corresponding elements in the other.</span></span> <span data-ttu-id="af2e2-117">To znázorňuje následující deklarace.</span><span class="sxs-lookup"><span data-stu-id="af2e2-117">The following declaration illustrates this.</span></span>  
  
```  
yourSystem = mySystem  
```  
  
 <span data-ttu-id="af2e2-118">Pokud element struktury, jako je typem odkazu `String`, `Object`, nebo pole, ukazatel na data zkopírována.</span><span class="sxs-lookup"><span data-stu-id="af2e2-118">If a structure element is a reference type, such as a `String`, `Object`, or array, the pointer to the data is copied.</span></span> <span data-ttu-id="af2e2-119">V předchozím příkladu Pokud `systemInfo` obsahoval proměnné objektu, pak by jste zkopírovali v předchozím příkladu ukazatel z `mySystem` k `yourSystem`, a změna data objektu prostřednictvím jedné struktury by při přístupu nebudou platit prostřednictvím jiné struktury.</span><span class="sxs-lookup"><span data-stu-id="af2e2-119">In the previous example, if `systemInfo` had included an object variable, then the preceding example would have copied the pointer from `mySystem` to `yourSystem`, and a change to the object's data through one structure would be in effect when accessed through the other structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af2e2-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="af2e2-120">See also</span></span>

- [<span data-ttu-id="af2e2-121">Datové typy</span><span class="sxs-lookup"><span data-stu-id="af2e2-121">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="af2e2-122">Základní datové typy</span><span class="sxs-lookup"><span data-stu-id="af2e2-122">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="af2e2-123">Složené datové typy</span><span class="sxs-lookup"><span data-stu-id="af2e2-123">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="af2e2-124">Typy hodnot a odkazové typy</span><span class="sxs-lookup"><span data-stu-id="af2e2-124">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="af2e2-125">Struktury</span><span class="sxs-lookup"><span data-stu-id="af2e2-125">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="af2e2-126">Řešení potíží s datovými typy</span><span class="sxs-lookup"><span data-stu-id="af2e2-126">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="af2e2-127">Postupy: Deklarace struktury</span><span class="sxs-lookup"><span data-stu-id="af2e2-127">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="af2e2-128">Struktury a ostatní programovací elementy</span><span class="sxs-lookup"><span data-stu-id="af2e2-128">Structures and Other Programming Elements</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [<span data-ttu-id="af2e2-129">Struktury a třídy</span><span class="sxs-lookup"><span data-stu-id="af2e2-129">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [<span data-ttu-id="af2e2-130">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="af2e2-130">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
