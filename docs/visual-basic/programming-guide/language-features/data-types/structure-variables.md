---
title: Proměnné struktury (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
ms.openlocfilehash: a86a60def9ac1b8140194ecb6f5e784c62a0e101
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630967"
---
# <a name="structure-variables-visual-basic"></a><span data-ttu-id="a9a87-102">Proměnné struktury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a9a87-102">Structure Variables (Visual Basic)</span></span>

<span data-ttu-id="a9a87-103">Po vytvoření struktury můžete jako typ deklarovat proměnné na úrovni procedury a modulu.</span><span class="sxs-lookup"><span data-stu-id="a9a87-103">Once you have created a structure, you can declare procedure-level and module-level variables as that type.</span></span> <span data-ttu-id="a9a87-104">Můžete například vytvořit strukturu, která zaznamenává informace o počítačovém systému.</span><span class="sxs-lookup"><span data-stu-id="a9a87-104">For example, you can create a structure that records information about a computer system.</span></span> <span data-ttu-id="a9a87-105">Následující příklad ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="a9a87-105">The following example demonstrates this.</span></span>

```vb
Public Structure systemInfo
    Public cPU As String
    Public memory As Long
    Public purchaseDate As Date
End Structure
```

<span data-ttu-id="a9a87-106">Nyní můžete deklarovat proměnné tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="a9a87-106">You can now declare variables of that type.</span></span> <span data-ttu-id="a9a87-107">Následující deklarace tento příklad ilustruje.</span><span class="sxs-lookup"><span data-stu-id="a9a87-107">The following declaration illustrates this.</span></span>

```vb
Dim mySystem, yourSystem As systemInfo
```

> [!NOTE]
> <span data-ttu-id="a9a87-108">Ve třídách a modulech jsou struktury deklarované pomocí [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) výchozí pro veřejný přístup.</span><span class="sxs-lookup"><span data-stu-id="a9a87-108">In classes and modules, structures declared using the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) default to public access.</span></span> <span data-ttu-id="a9a87-109">Pokud máte v úmyslu strukturu jako soukromou, ujistěte se, že ji deklarujete pomocí klíčového slova [Private](../../../../visual-basic/language-reference/modifiers/private.md) .</span><span class="sxs-lookup"><span data-stu-id="a9a87-109">If you intend a structure to be private, make sure you declare it using the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword.</span></span>

## <a name="access-to-structure-values"></a><span data-ttu-id="a9a87-110">Přístup k hodnotám struktury</span><span class="sxs-lookup"><span data-stu-id="a9a87-110">Access to Structure Values</span></span>

<span data-ttu-id="a9a87-111">Chcete-li přiřadit a načíst hodnoty z prvků proměnné struktury, použijte stejnou syntaxi, jako je použit k nastavení a získání vlastností objektu.</span><span class="sxs-lookup"><span data-stu-id="a9a87-111">To assign and retrieve values from the elements of a structure variable, you use the same syntax as you use to set and get properties on an object.</span></span> <span data-ttu-id="a9a87-112">Umístěte operátor přístupu členů (`.`) mezi název proměnné struktury a název elementu.</span><span class="sxs-lookup"><span data-stu-id="a9a87-112">You place the member access operator (`.`) between the structure variable name and the element name.</span></span> <span data-ttu-id="a9a87-113">Následující příklad přistupuje k prvkům proměnných dříve deklarovaných jako typ `systemInfo`.</span><span class="sxs-lookup"><span data-stu-id="a9a87-113">The following example accesses elements of the variables previously declared as type `systemInfo`.</span></span>

```vb
mySystem.cPU = "486"
Dim tooOld As Boolean
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True
```

## <a name="assigning-structure-variables"></a><span data-ttu-id="a9a87-114">Přiřazení proměnných struktury</span><span class="sxs-lookup"><span data-stu-id="a9a87-114">Assigning Structure Variables</span></span>

<span data-ttu-id="a9a87-115">Můžete také přiřadit jednu proměnnou k druhé, pokud jsou obě stejné typu struktury.</span><span class="sxs-lookup"><span data-stu-id="a9a87-115">You can also assign one variable to another if both are of the same structure type.</span></span> <span data-ttu-id="a9a87-116">Tím se zkopírují všechny prvky jedné struktury do odpovídajících prvků v druhé.</span><span class="sxs-lookup"><span data-stu-id="a9a87-116">This copies all the elements of one structure to the corresponding elements in the other.</span></span> <span data-ttu-id="a9a87-117">Následující deklarace tento příklad ilustruje.</span><span class="sxs-lookup"><span data-stu-id="a9a87-117">The following declaration illustrates this.</span></span>

```vb
yourSystem = mySystem
```

<span data-ttu-id="a9a87-118">Pokud prvek struktury je odkazový typ, jako `String`je například, `Object`nebo pole, je zkopírován ukazatel na data.</span><span class="sxs-lookup"><span data-stu-id="a9a87-118">If a structure element is a reference type, such as a `String`, `Object`, or array, the pointer to the data is copied.</span></span> <span data-ttu-id="a9a87-119">V předchozím příkladu, pokud `systemInfo` obsahoval proměnnou objektu, pak předchozí příklad zkopíroval ukazatel z `mySystem` na `yourSystem`a a změna dat objektu prostřednictvím jedné struktury bude platit při použití prostřednictvím jiné struktury.</span><span class="sxs-lookup"><span data-stu-id="a9a87-119">In the previous example, if `systemInfo` had included an object variable, then the preceding example would have copied the pointer from `mySystem` to `yourSystem`, and a change to the object's data through one structure would be in effect when accessed through the other structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="a9a87-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a9a87-120">See also</span></span>

- [<span data-ttu-id="a9a87-121">Datové typy</span><span class="sxs-lookup"><span data-stu-id="a9a87-121">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="a9a87-122">Základní datové typy</span><span class="sxs-lookup"><span data-stu-id="a9a87-122">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="a9a87-123">Složené datové typy</span><span class="sxs-lookup"><span data-stu-id="a9a87-123">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="a9a87-124">Typy hodnot a odkazové typy</span><span class="sxs-lookup"><span data-stu-id="a9a87-124">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="a9a87-125">Struktury</span><span class="sxs-lookup"><span data-stu-id="a9a87-125">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="a9a87-126">Řešení potíží s datovými typy</span><span class="sxs-lookup"><span data-stu-id="a9a87-126">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="a9a87-127">Postupy: Deklarace struktury</span><span class="sxs-lookup"><span data-stu-id="a9a87-127">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="a9a87-128">Struktury a ostatní programovací elementy</span><span class="sxs-lookup"><span data-stu-id="a9a87-128">Structures and Other Programming Elements</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [<span data-ttu-id="a9a87-129">Struktury a třídy</span><span class="sxs-lookup"><span data-stu-id="a9a87-129">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [<span data-ttu-id="a9a87-130">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="a9a87-130">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
