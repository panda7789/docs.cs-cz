---
title: 'Postupy: Přístup ke členům v objektu'
ms.date: 07/20/2015
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
ms.openlocfilehash: 2826a3c98b9f19b08cc943d0f67cdd34ac90f526
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410539"
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a><span data-ttu-id="e8815-102">Postupy: Přístup ke členům v objektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e8815-102">How to: Access Members of an Object (Visual Basic)</span></span>

<span data-ttu-id="e8815-103">Máte-li objektovou proměnnou, která odkazuje na objekt, často chcete pracovat s členy tohoto objektu, například jeho metodami, vlastnostmi, poli a událostmi.</span><span class="sxs-lookup"><span data-stu-id="e8815-103">When you have an object variable that refers to an object, you often want to work with the members of that object, such as its methods, properties, fields, and events.</span></span> <span data-ttu-id="e8815-104">Například Jakmile vytvoříte nový <xref:System.Windows.Forms.Form> objekt, můžete chtít nastavit jeho <xref:System.Windows.Forms.Control.Text%2A> vlastnost nebo zavolat její <xref:System.Windows.Forms.Control.Focus%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="e8815-104">For example, once you have created a new <xref:System.Windows.Forms.Form> object, you might want to set its <xref:System.Windows.Forms.Control.Text%2A> property or call its <xref:System.Windows.Forms.Control.Focus%2A> method.</span></span>

## <a name="accessing-members"></a><span data-ttu-id="e8815-105">Přístup ke členům</span><span class="sxs-lookup"><span data-stu-id="e8815-105">Accessing Members</span></span>

<span data-ttu-id="e8815-106">Přistupujete k členům objektu přes proměnnou, která na ni odkazuje.</span><span class="sxs-lookup"><span data-stu-id="e8815-106">You access an object's members through the variable that refers to it.</span></span>

#### <a name="to-access-members-of-an-object"></a><span data-ttu-id="e8815-107">Přístup ke členům objektu</span><span class="sxs-lookup"><span data-stu-id="e8815-107">To access members of an object</span></span>

- <span data-ttu-id="e8815-108">Použijte operátor přístupu členů ( `.` ) mezi názvem proměnné objektu a názvem člena.</span><span class="sxs-lookup"><span data-stu-id="e8815-108">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>

    ```vb
    currentText = newForm.Text
    ```

    <span data-ttu-id="e8815-109">Pokud je člen [sdílen](../../../language-reference/modifiers/shared.md), nepotřebujete k přístupu k němu proměnnou.</span><span class="sxs-lookup"><span data-stu-id="e8815-109">If the member is [Shared](../../../language-reference/modifiers/shared.md), you do not need a variable to access it.</span></span>

## <a name="accessing-members-of-an-object-of-known-type"></a><span data-ttu-id="e8815-110">Přístup ke členům objektu známého typu</span><span class="sxs-lookup"><span data-stu-id="e8815-110">Accessing Members of an Object of Known Type</span></span>

<span data-ttu-id="e8815-111">Pokud znáte typ objektu v době kompilace, můžete použít *počáteční vazbu* pro proměnnou, která na ni odkazuje.</span><span class="sxs-lookup"><span data-stu-id="e8815-111">If you know the type of an object at compile time, you can use *early binding* for a variable that refers to it.</span></span>

#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a><span data-ttu-id="e8815-112">Pro přístup ke členům objektu, pro který znáte typ v době kompilace</span><span class="sxs-lookup"><span data-stu-id="e8815-112">To access members of an object for which you know the type at compile time</span></span>

1. <span data-ttu-id="e8815-113">Deklarujte proměnnou objektu pro typ objektu, který chcete přiřadit proměnné.</span><span class="sxs-lookup"><span data-stu-id="e8815-113">Declare the object variable to be of the type of the object you intend to assign to the variable.</span></span>

    ```vb
    Dim extraForm As System.Windows.Forms.Form
    ```

    <span data-ttu-id="e8815-114">Pomocí `Option Strict On` můžete přiřadit pouze <xref:System.Windows.Forms.Form> objekty (nebo objekty typu odvozené z <xref:System.Windows.Forms.Form> ) k `extraForm` .</span><span class="sxs-lookup"><span data-stu-id="e8815-114">With `Option Strict On`, you can assign only <xref:System.Windows.Forms.Form> objects (or objects of a type derived from <xref:System.Windows.Forms.Form>) to `extraForm`.</span></span> <span data-ttu-id="e8815-115">Pokud jste definovali třídu nebo strukturu s rozšiřujícím `CType` převodem na <xref:System.Windows.Forms.Form> , můžete tuto třídu nebo strukturu přiřadit také k `extraForm` .</span><span class="sxs-lookup"><span data-stu-id="e8815-115">If you have defined a class or structure with a widening `CType` conversion to <xref:System.Windows.Forms.Form>, you can also assign that class or structure to `extraForm`.</span></span>

2. <span data-ttu-id="e8815-116">Použijte operátor přístupu členů ( `.` ) mezi názvem proměnné objektu a názvem člena.</span><span class="sxs-lookup"><span data-stu-id="e8815-116">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>

    ```vb
    extraForm.Show()
    ```

    <span data-ttu-id="e8815-117">Ke všem metodám a vlastnostem, které jsou specifické pro <xref:System.Windows.Forms.Form> třídu, můžete přistupovat bez ohledu na to, co `Option Strict` je nastavení.</span><span class="sxs-lookup"><span data-stu-id="e8815-117">You can access all of the methods and properties specific to the <xref:System.Windows.Forms.Form> class, no matter what the `Option Strict` setting is.</span></span>

## <a name="accessing-members-of-an-object-of-unknown-type"></a><span data-ttu-id="e8815-118">Přístup ke členům objektu neznámého typu</span><span class="sxs-lookup"><span data-stu-id="e8815-118">Accessing Members of an Object of Unknown Type</span></span>

<span data-ttu-id="e8815-119">Pokud neznáte typ objektu v době kompilace, je nutné použít *pozdní vazbu* pro libovolnou proměnnou, která na ni odkazuje.</span><span class="sxs-lookup"><span data-stu-id="e8815-119">If you do not know the type of an object at compile time, you must use *late binding* for any variable that refers to it.</span></span>

#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a><span data-ttu-id="e8815-120">Pro přístup ke členům objektu, pro který neznáte typ v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="e8815-120">To access members of an object for which you do not know the type at compile time</span></span>

1. <span data-ttu-id="e8815-121">Deklarujte proměnnou objektu pro [datový typ objektu](../../../language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="e8815-121">Declare the object variable to be of the [Object Data Type](../../../language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="e8815-122">(Deklarace proměnné tak, jak `Object` je stejná jako deklarace jako <xref:System.Object?displayProperty=nameWithType> .)</span><span class="sxs-lookup"><span data-stu-id="e8815-122">(Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=nameWithType>.)</span></span>

    ```vb
    Dim someControl As Object
    ```

    <span data-ttu-id="e8815-123">Pomocí nástroje máte `Option Strict On` přístup pouze k členům, které jsou definovány ve <xref:System.Object> třídě.</span><span class="sxs-lookup"><span data-stu-id="e8815-123">With `Option Strict On`, you can access only the members that are defined on the <xref:System.Object> class.</span></span>

2. <span data-ttu-id="e8815-124">Použijte operátor přístupu členů ( `.` ) mezi názvem proměnné objektu a názvem člena.</span><span class="sxs-lookup"><span data-stu-id="e8815-124">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>

    ```vb
    someControl.GetType()
    ```

    <span data-ttu-id="e8815-125">Aby bylo možné přistupovat ke členům libovolného objektu, který přiřadíte proměnné objektu, je nutné nastavit `Option Strict Off` .</span><span class="sxs-lookup"><span data-stu-id="e8815-125">To be able to access the members of any object you assign to the object variable, you must set `Option Strict Off`.</span></span> <span data-ttu-id="e8815-126">Pokud to uděláte, kompilátor nemůže zaručit, že daný člen je zveřejněn objektem, který přiřadíte proměnné.</span><span class="sxs-lookup"><span data-stu-id="e8815-126">When you do this, the compiler cannot guarantee that a given member is exposed by the object you assign to the variable.</span></span> <span data-ttu-id="e8815-127">Pokud objekt nezveřejňuje člena, ke kterému se pokoušíte získat přístup, <xref:System.MemberAccessException> dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="e8815-127">If the object does not expose a member you attempt to access, a <xref:System.MemberAccessException> exception occurs.</span></span>

## <a name="see-also"></a><span data-ttu-id="e8815-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="e8815-128">See also</span></span>

- <xref:System.Object>
- <xref:System.Windows.Forms.Form>
- <xref:System.MemberAccessException>
- [<span data-ttu-id="e8815-129">Proměnné objektu</span><span class="sxs-lookup"><span data-stu-id="e8815-129">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="e8815-130">Deklarace proměnné objektu</span><span class="sxs-lookup"><span data-stu-id="e8815-130">Object Variable Declaration</span></span>](object-variable-declaration.md)
- [<span data-ttu-id="e8815-131">Datový typ objektu</span><span class="sxs-lookup"><span data-stu-id="e8815-131">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="e8815-132">Option Strict – příkaz</span><span class="sxs-lookup"><span data-stu-id="e8815-132">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
