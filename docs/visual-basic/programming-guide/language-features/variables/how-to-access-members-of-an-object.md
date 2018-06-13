---
title: 'Postupy: Přístup ke členům v objektu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
ms.openlocfilehash: 62be2955bd1f62fa5af4e54fb0af5e7dca29c421
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650917"
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a><span data-ttu-id="d7751-102">Postupy: Přístup ke členům v objektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d7751-102">How to: Access Members of an Object (Visual Basic)</span></span>
<span data-ttu-id="d7751-103">Až budete mít proměnná objektu, který odkazuje na objekt, často chcete pracovat se členy tohoto objektu, například metody, vlastnosti, pole a události.</span><span class="sxs-lookup"><span data-stu-id="d7751-103">When you have an object variable that refers to an object, you often want to work with the members of that object, such as its methods, properties, fields, and events.</span></span> <span data-ttu-id="d7751-104">Například po vytvoření nové <xref:System.Windows.Forms.Form> objekt, můžete chtít nastavit jeho <xref:System.Windows.Forms.Control.Text%2A> vlastnost nebo volání jeho <xref:System.Windows.Forms.Control.Focus%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="d7751-104">For example, once you have created a new <xref:System.Windows.Forms.Form> object, you might want to set its <xref:System.Windows.Forms.Control.Text%2A> property or call its <xref:System.Windows.Forms.Control.Focus%2A> method.</span></span>  
  
## <a name="accessing-members"></a><span data-ttu-id="d7751-105">Získávání přístupu k členům</span><span class="sxs-lookup"><span data-stu-id="d7751-105">Accessing Members</span></span>  
 <span data-ttu-id="d7751-106">Členové objektu přistupujete prostřednictvím proměnné, která odkazuje na ni.</span><span class="sxs-lookup"><span data-stu-id="d7751-106">You access an object's members through the variable that refers to it.</span></span>  
  
#### <a name="to-access-members-of-an-object"></a><span data-ttu-id="d7751-107">Pro přístup k členům v objektu</span><span class="sxs-lookup"><span data-stu-id="d7751-107">To access members of an object</span></span>  
  
-   <span data-ttu-id="d7751-108">Použití operátoru přístup ke členu (`.`) mezi názvu proměnné objektu a název člena.</span><span class="sxs-lookup"><span data-stu-id="d7751-108">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>  
  
    ```  
    currentText = newForm.Text  
    ```  
  
     <span data-ttu-id="d7751-109">Pokud je člen [sdílené](../../../../visual-basic/language-reference/modifiers/shared.md), není nutné proměnnou, do které k němu přístup.</span><span class="sxs-lookup"><span data-stu-id="d7751-109">If the member is [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), you do not need a variable to access it.</span></span>  
  
## <a name="accessing-members-of-an-object-of-known-type"></a><span data-ttu-id="d7751-110">Přístup ke členům v objektu známé typu</span><span class="sxs-lookup"><span data-stu-id="d7751-110">Accessing Members of an Object of Known Type</span></span>  
 <span data-ttu-id="d7751-111">Pokud znáte typ objektu v době kompilace, můžete použít *časné vazby* pro proměnné, která odkazuje na ni.</span><span class="sxs-lookup"><span data-stu-id="d7751-111">If you know the type of an object at compile time, you can use *early binding* for a variable that refers to it.</span></span>  
  
#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a><span data-ttu-id="d7751-112">Pro přístup k členům v objektu, pro kterou je znát typ v době kompilace</span><span class="sxs-lookup"><span data-stu-id="d7751-112">To access members of an object for which you know the type at compile time</span></span>  
  
1.  <span data-ttu-id="d7751-113">Deklarujte proměnnou objektu bude typu objektu, který chcete přiřadit k proměnné.</span><span class="sxs-lookup"><span data-stu-id="d7751-113">Declare the object variable to be of the type of the object you intend to assign to the variable.</span></span>  
  
    ```  
    Dim extraForm As System.Windows.Forms.Form  
    ```  
  
     <span data-ttu-id="d7751-114">S `Option Strict On`, můžete přiřadit pouze <xref:System.Windows.Forms.Form> objekty (nebo objekty typu odvozené od <xref:System.Windows.Forms.Form>) k `extraForm`.</span><span class="sxs-lookup"><span data-stu-id="d7751-114">With `Option Strict On`, you can assign only <xref:System.Windows.Forms.Form> objects (or objects of a type derived from <xref:System.Windows.Forms.Form>) to `extraForm`.</span></span> <span data-ttu-id="d7751-115">Pokud jste definovali třídu nebo strukturu s rozšíření `CType` převod na <xref:System.Windows.Forms.Form>, můžete také přiřadit třídy nebo struktury k `extraForm`.</span><span class="sxs-lookup"><span data-stu-id="d7751-115">If you have defined a class or structure with a widening `CType` conversion to <xref:System.Windows.Forms.Form>, you can also assign that class or structure to `extraForm`.</span></span>  
  
2.  <span data-ttu-id="d7751-116">Použití operátoru přístup ke členu (`.`) mezi názvu proměnné objektu a název člena.</span><span class="sxs-lookup"><span data-stu-id="d7751-116">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>  
  
    ```  
    extraForm.Show()  
    ```  
  
     <span data-ttu-id="d7751-117">Můžete všechny metody a vlastnosti specifické pro přístup <xref:System.Windows.Forms.Form> třída, bez ohledu na to, co `Option Strict` nastavení je.</span><span class="sxs-lookup"><span data-stu-id="d7751-117">You can access all of the methods and properties specific to the <xref:System.Windows.Forms.Form> class, no matter what the `Option Strict` setting is.</span></span>  
  
## <a name="accessing-members-of-an-object-of-unknown-type"></a><span data-ttu-id="d7751-118">Přístup ke členům objekt neznámého typu.</span><span class="sxs-lookup"><span data-stu-id="d7751-118">Accessing Members of an Object of Unknown Type</span></span>  
 <span data-ttu-id="d7751-119">Pokud neznáte typ objektu v době kompilace, musíte použít *pozdní vazby* pro všechny proměnné, která odkazuje na ni.</span><span class="sxs-lookup"><span data-stu-id="d7751-119">If you do not know the type of an object at compile time, you must use *late binding* for any variable that refers to it.</span></span>  
  
#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a><span data-ttu-id="d7751-120">Pro přístup k členům v objektu, pro kterou neznáte typ v době kompilace</span><span class="sxs-lookup"><span data-stu-id="d7751-120">To access members of an object for which you do not know the type at compile time</span></span>  
  
1.  <span data-ttu-id="d7751-121">Deklarace proměnné objektu bude [Object – datový typ](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="d7751-121">Declare the object variable to be of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="d7751-122">(Deklarace proměnné jako `Object` je stejný jako deklarace jej jako <xref:System.Object?displayProperty=nameWithType>.)</span><span class="sxs-lookup"><span data-stu-id="d7751-122">(Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=nameWithType>.)</span></span>  
  
    ```  
    Dim someControl As Object  
    ```  
  
     <span data-ttu-id="d7751-123">S `Option Strict On`, můžete přístup pouze členové, které jsou definovány na <xref:System.Object> třídy.</span><span class="sxs-lookup"><span data-stu-id="d7751-123">With `Option Strict On`, you can access only the members that are defined on the <xref:System.Object> class.</span></span>  
  
2.  <span data-ttu-id="d7751-124">Použití operátoru přístup ke členu (`.`) mezi názvu proměnné objektu a název člena.</span><span class="sxs-lookup"><span data-stu-id="d7751-124">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>  
  
    ```  
    someControl.GetType()  
    ```  
  
     <span data-ttu-id="d7751-125">Abyste mohli přístup ke členům v libovolného objektu přiřadit proměnné objektu, musíte nastavit `Option Strict Off`.</span><span class="sxs-lookup"><span data-stu-id="d7751-125">To be able to access the members of any object you assign to the object variable, you must set `Option Strict Off`.</span></span> <span data-ttu-id="d7751-126">Když to uděláte, kompilátor nemůže zaručit, že je daný člen je zveřejněný prostřednictvím objektu, který přiřadíte k proměnné.</span><span class="sxs-lookup"><span data-stu-id="d7751-126">When you do this, the compiler cannot guarantee that a given member is exposed by the object you assign to the variable.</span></span> <span data-ttu-id="d7751-127">Pokud objekt nevystavuje členem pokusu o přístup, <xref:System.MemberAccessException> došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="d7751-127">If the object does not expose a member you attempt to access, a <xref:System.MemberAccessException> exception occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7751-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="d7751-128">See Also</span></span>  
 <xref:System.Object>  
 <xref:System.Windows.Forms.Form>  
 <xref:System.MemberAccessException>  
 [<span data-ttu-id="d7751-129">Objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="d7751-129">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="d7751-130">Deklarace objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="d7751-130">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [<span data-ttu-id="d7751-131">Datový typ Object</span><span class="sxs-lookup"><span data-stu-id="d7751-131">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [<span data-ttu-id="d7751-132">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="d7751-132">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
