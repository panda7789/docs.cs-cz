---
title: 'Postupy: Přístup ke členům objektu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
ms.openlocfilehash: 882046b829ade2da7c10b3db4c0d6c9ca9f3d579
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630841"
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a><span data-ttu-id="52db8-102">Postupy: Přístup ke členům objektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52db8-102">How to: Access Members of an Object (Visual Basic)</span></span>

<span data-ttu-id="52db8-103">Máte-li objektovou proměnnou, která odkazuje na objekt, často chcete pracovat s členy tohoto objektu, například jeho metodami, vlastnostmi, poli a událostmi.</span><span class="sxs-lookup"><span data-stu-id="52db8-103">When you have an object variable that refers to an object, you often want to work with the members of that object, such as its methods, properties, fields, and events.</span></span> <span data-ttu-id="52db8-104">Například Jakmile vytvoříte nový <xref:System.Windows.Forms.Form> objekt, můžete chtít nastavit jeho <xref:System.Windows.Forms.Control.Text%2A> vlastnost nebo zavolat její <xref:System.Windows.Forms.Control.Focus%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="52db8-104">For example, once you have created a new <xref:System.Windows.Forms.Form> object, you might want to set its <xref:System.Windows.Forms.Control.Text%2A> property or call its <xref:System.Windows.Forms.Control.Focus%2A> method.</span></span>

## <a name="accessing-members"></a><span data-ttu-id="52db8-105">Přístup ke členům</span><span class="sxs-lookup"><span data-stu-id="52db8-105">Accessing Members</span></span>

<span data-ttu-id="52db8-106">Přistupujete k členům objektu přes proměnnou, která na ni odkazuje.</span><span class="sxs-lookup"><span data-stu-id="52db8-106">You access an object's members through the variable that refers to it.</span></span>

#### <a name="to-access-members-of-an-object"></a><span data-ttu-id="52db8-107">Přístup ke členům objektu</span><span class="sxs-lookup"><span data-stu-id="52db8-107">To access members of an object</span></span>

- <span data-ttu-id="52db8-108">Použijte operátor přístupu členů (`.`) mezi názvem proměnné objektu a názvem člena.</span><span class="sxs-lookup"><span data-stu-id="52db8-108">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>

    ```vb
    currentText = newForm.Text
    ```

    <span data-ttu-id="52db8-109">Pokud je člen [sdílen](../../../../visual-basic/language-reference/modifiers/shared.md), nepotřebujete k přístupu k němu proměnnou.</span><span class="sxs-lookup"><span data-stu-id="52db8-109">If the member is [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), you do not need a variable to access it.</span></span>

## <a name="accessing-members-of-an-object-of-known-type"></a><span data-ttu-id="52db8-110">Přístup ke členům objektu známého typu</span><span class="sxs-lookup"><span data-stu-id="52db8-110">Accessing Members of an Object of Known Type</span></span>

<span data-ttu-id="52db8-111">Pokud znáte typ objektu v době kompilace, můžete použít *počáteční vazbu* pro proměnnou, která na ni odkazuje.</span><span class="sxs-lookup"><span data-stu-id="52db8-111">If you know the type of an object at compile time, you can use *early binding* for a variable that refers to it.</span></span>

#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a><span data-ttu-id="52db8-112">Pro přístup ke členům objektu, pro který znáte typ v době kompilace</span><span class="sxs-lookup"><span data-stu-id="52db8-112">To access members of an object for which you know the type at compile time</span></span>

1. <span data-ttu-id="52db8-113">Deklarujte proměnnou objektu pro typ objektu, který chcete přiřadit proměnné.</span><span class="sxs-lookup"><span data-stu-id="52db8-113">Declare the object variable to be of the type of the object you intend to assign to the variable.</span></span>

    ```vb
    Dim extraForm As System.Windows.Forms.Form
    ```

    <span data-ttu-id="52db8-114">Pomocí `Option Strict On`můžete přiřadit pouze <xref:System.Windows.Forms.Form> objekty (nebo objekty typu odvozené z <xref:System.Windows.Forms.Form>) k `extraForm`.</span><span class="sxs-lookup"><span data-stu-id="52db8-114">With `Option Strict On`, you can assign only <xref:System.Windows.Forms.Form> objects (or objects of a type derived from <xref:System.Windows.Forms.Form>) to `extraForm`.</span></span> <span data-ttu-id="52db8-115">Pokud jste definovali třídu nebo strukturu s rozšiřujícím `CType` převodem na <xref:System.Windows.Forms.Form>, můžete tuto třídu nebo strukturu přiřadit také k `extraForm`.</span><span class="sxs-lookup"><span data-stu-id="52db8-115">If you have defined a class or structure with a widening `CType` conversion to <xref:System.Windows.Forms.Form>, you can also assign that class or structure to `extraForm`.</span></span>

2. <span data-ttu-id="52db8-116">Použijte operátor přístupu členů (`.`) mezi názvem proměnné objektu a názvem člena.</span><span class="sxs-lookup"><span data-stu-id="52db8-116">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>

    ```vb
    extraForm.Show()
    ```

    <span data-ttu-id="52db8-117">Ke všem metodám a vlastnostem, které jsou specifické pro <xref:System.Windows.Forms.Form> třídu, můžete přistupovat bez ohledu na `Option Strict` to, co je nastavení.</span><span class="sxs-lookup"><span data-stu-id="52db8-117">You can access all of the methods and properties specific to the <xref:System.Windows.Forms.Form> class, no matter what the `Option Strict` setting is.</span></span>

## <a name="accessing-members-of-an-object-of-unknown-type"></a><span data-ttu-id="52db8-118">Přístup ke členům objektu neznámého typu</span><span class="sxs-lookup"><span data-stu-id="52db8-118">Accessing Members of an Object of Unknown Type</span></span>

<span data-ttu-id="52db8-119">Pokud neznáte typ objektu v době kompilace, je nutné použít *pozdní vazbu* pro libovolnou proměnnou, která na ni odkazuje.</span><span class="sxs-lookup"><span data-stu-id="52db8-119">If you do not know the type of an object at compile time, you must use *late binding* for any variable that refers to it.</span></span>

#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a><span data-ttu-id="52db8-120">Pro přístup ke členům objektu, pro který neznáte typ v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="52db8-120">To access members of an object for which you do not know the type at compile time</span></span>

1. <span data-ttu-id="52db8-121">Deklarujte proměnnou objektu pro [datový typ objektu](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="52db8-121">Declare the object variable to be of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="52db8-122">(Deklarace proměnné tak, `Object` jak je stejná jako deklarace <xref:System.Object?displayProperty=nameWithType>jako.)</span><span class="sxs-lookup"><span data-stu-id="52db8-122">(Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=nameWithType>.)</span></span>

    ```vb
    Dim someControl As Object
    ```

    <span data-ttu-id="52db8-123">Pomocí `Option Strict On`nástroje máte přístup pouze k členům, které jsou definovány <xref:System.Object> ve třídě.</span><span class="sxs-lookup"><span data-stu-id="52db8-123">With `Option Strict On`, you can access only the members that are defined on the <xref:System.Object> class.</span></span>

2. <span data-ttu-id="52db8-124">Použijte operátor přístupu členů (`.`) mezi názvem proměnné objektu a názvem člena.</span><span class="sxs-lookup"><span data-stu-id="52db8-124">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>

    ```vb
    someControl.GetType()
    ```

    <span data-ttu-id="52db8-125">Aby bylo možné přistupovat ke členům libovolného objektu, který přiřadíte proměnné objektu, je nutné nastavit `Option Strict Off`.</span><span class="sxs-lookup"><span data-stu-id="52db8-125">To be able to access the members of any object you assign to the object variable, you must set `Option Strict Off`.</span></span> <span data-ttu-id="52db8-126">Pokud to uděláte, kompilátor nemůže zaručit, že daný člen je zveřejněn objektem, který přiřadíte proměnné.</span><span class="sxs-lookup"><span data-stu-id="52db8-126">When you do this, the compiler cannot guarantee that a given member is exposed by the object you assign to the variable.</span></span> <span data-ttu-id="52db8-127">Pokud objekt nezveřejňuje člena, ke kterému se pokoušíte získat přístup <xref:System.MemberAccessException> , dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="52db8-127">If the object does not expose a member you attempt to access, a <xref:System.MemberAccessException> exception occurs.</span></span>

## <a name="see-also"></a><span data-ttu-id="52db8-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="52db8-128">See also</span></span>

- <xref:System.Object>
- <xref:System.Windows.Forms.Form>
- <xref:System.MemberAccessException>
- [<span data-ttu-id="52db8-129">Objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="52db8-129">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="52db8-130">Deklarace objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="52db8-130">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="52db8-131">Datový typ Object</span><span class="sxs-lookup"><span data-stu-id="52db8-131">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="52db8-132">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="52db8-132">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
