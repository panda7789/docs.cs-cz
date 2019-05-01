---
title: 'Postupy: Přístup k členům v objektu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
ms.openlocfilehash: de00e428cc3d9d7a5688e853b0ff4295fec5b3e9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052128"
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a><span data-ttu-id="a4013-102">Postupy: Přístup k členům v objektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4013-102">How to: Access Members of an Object (Visual Basic)</span></span>
<span data-ttu-id="a4013-103">Až budete mít proměnné objektu, který odkazuje na objekt, často chcete pracovat s členy tohoto objektu, jako jsou metody, vlastnosti, pole a události.</span><span class="sxs-lookup"><span data-stu-id="a4013-103">When you have an object variable that refers to an object, you often want to work with the members of that object, such as its methods, properties, fields, and events.</span></span> <span data-ttu-id="a4013-104">Například po vytvoření nového <xref:System.Windows.Forms.Form> objektu, můžete chtít nastavit jeho <xref:System.Windows.Forms.Control.Text%2A> vlastností nebo volání jeho <xref:System.Windows.Forms.Control.Focus%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="a4013-104">For example, once you have created a new <xref:System.Windows.Forms.Form> object, you might want to set its <xref:System.Windows.Forms.Control.Text%2A> property or call its <xref:System.Windows.Forms.Control.Focus%2A> method.</span></span>  
  
## <a name="accessing-members"></a><span data-ttu-id="a4013-105">Přístup ke členům</span><span class="sxs-lookup"><span data-stu-id="a4013-105">Accessing Members</span></span>  
 <span data-ttu-id="a4013-106">Získáte přístup k členům objektu prostřednictvím proměnné, která odkazuje na ni.</span><span class="sxs-lookup"><span data-stu-id="a4013-106">You access an object's members through the variable that refers to it.</span></span>  
  
#### <a name="to-access-members-of-an-object"></a><span data-ttu-id="a4013-107">Pro přístup ke členům objektu</span><span class="sxs-lookup"><span data-stu-id="a4013-107">To access members of an object</span></span>  
  
- <span data-ttu-id="a4013-108">Operátor přístupu členů (`.`) mezi názvem proměnné objektu a název člena.</span><span class="sxs-lookup"><span data-stu-id="a4013-108">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>  
  
    ```  
    currentText = newForm.Text  
    ```  
  
     <span data-ttu-id="a4013-109">Pokud je člen [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), není nutné proměnnou, která k němu přístup.</span><span class="sxs-lookup"><span data-stu-id="a4013-109">If the member is [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), you do not need a variable to access it.</span></span>  
  
## <a name="accessing-members-of-an-object-of-known-type"></a><span data-ttu-id="a4013-110">Přístup ke členům objektu známého typu</span><span class="sxs-lookup"><span data-stu-id="a4013-110">Accessing Members of an Object of Known Type</span></span>  
 <span data-ttu-id="a4013-111">Pokud víte, typ objektu v době kompilace, můžete použít *časné vazby* pro proměnnou, která odkazuje na ni.</span><span class="sxs-lookup"><span data-stu-id="a4013-111">If you know the type of an object at compile time, you can use *early binding* for a variable that refers to it.</span></span>  
  
#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a><span data-ttu-id="a4013-112">Pro přístup ke členům objektu, pro kterou znáte typ v době kompilace</span><span class="sxs-lookup"><span data-stu-id="a4013-112">To access members of an object for which you know the type at compile time</span></span>  
  
1. <span data-ttu-id="a4013-113">Deklarace proměnné objektu typu objektu, který máte v úmyslu přiřadit k proměnné.</span><span class="sxs-lookup"><span data-stu-id="a4013-113">Declare the object variable to be of the type of the object you intend to assign to the variable.</span></span>  
  
    ```  
    Dim extraForm As System.Windows.Forms.Form  
    ```  
  
     <span data-ttu-id="a4013-114">S `Option Strict On`, můžete přiřadit pouze <xref:System.Windows.Forms.Form> objekty (nebo objekty typu odvozeného z <xref:System.Windows.Forms.Form>) k `extraForm`.</span><span class="sxs-lookup"><span data-stu-id="a4013-114">With `Option Strict On`, you can assign only <xref:System.Windows.Forms.Form> objects (or objects of a type derived from <xref:System.Windows.Forms.Form>) to `extraForm`.</span></span> <span data-ttu-id="a4013-115">Pokud jste definovali třídy nebo struktury se rozšiřující `CType` převod na <xref:System.Windows.Forms.Form>, můžete také přiřadit dané třídy nebo struktury na `extraForm`.</span><span class="sxs-lookup"><span data-stu-id="a4013-115">If you have defined a class or structure with a widening `CType` conversion to <xref:System.Windows.Forms.Form>, you can also assign that class or structure to `extraForm`.</span></span>  
  
2. <span data-ttu-id="a4013-116">Operátor přístupu členů (`.`) mezi názvem proměnné objektu a název člena.</span><span class="sxs-lookup"><span data-stu-id="a4013-116">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>  
  
    ```  
    extraForm.Show()  
    ```  
  
     <span data-ttu-id="a4013-117">Všechny metody a vlastnosti specifické pro dostanete <xref:System.Windows.Forms.Form> třídy, bez ohledu na to, co `Option Strict` nastavení je.</span><span class="sxs-lookup"><span data-stu-id="a4013-117">You can access all of the methods and properties specific to the <xref:System.Windows.Forms.Form> class, no matter what the `Option Strict` setting is.</span></span>  
  
## <a name="accessing-members-of-an-object-of-unknown-type"></a><span data-ttu-id="a4013-118">Přístup ke členům objekt neznámého typu.</span><span class="sxs-lookup"><span data-stu-id="a4013-118">Accessing Members of an Object of Unknown Type</span></span>  
 <span data-ttu-id="a4013-119">Pokud neznáte typ objektu v době kompilace, je nutné použít *pozdní vazby* pro jakoukoli proměnnou, která odkazuje na ni.</span><span class="sxs-lookup"><span data-stu-id="a4013-119">If you do not know the type of an object at compile time, you must use *late binding* for any variable that refers to it.</span></span>  
  
#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a><span data-ttu-id="a4013-120">Pro přístup ke členům objektu, pro kterou neznáte typ v době kompilace</span><span class="sxs-lookup"><span data-stu-id="a4013-120">To access members of an object for which you do not know the type at compile time</span></span>  
  
1. <span data-ttu-id="a4013-121">Deklarace proměnné objektu bude [datový typ objektu](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="a4013-121">Declare the object variable to be of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="a4013-122">(Deklarace proměnné jako `Object` je stejné jako deklarování jako <xref:System.Object?displayProperty=nameWithType>.)</span><span class="sxs-lookup"><span data-stu-id="a4013-122">(Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=nameWithType>.)</span></span>  
  
    ```  
    Dim someControl As Object  
    ```  
  
     <span data-ttu-id="a4013-123">S `Option Strict On`, dostanete pouze členy, které jsou definovány na <xref:System.Object> třídy.</span><span class="sxs-lookup"><span data-stu-id="a4013-123">With `Option Strict On`, you can access only the members that are defined on the <xref:System.Object> class.</span></span>  
  
2. <span data-ttu-id="a4013-124">Operátor přístupu členů (`.`) mezi názvem proměnné objektu a název člena.</span><span class="sxs-lookup"><span data-stu-id="a4013-124">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>  
  
    ```  
    someControl.GetType()  
    ```  
  
     <span data-ttu-id="a4013-125">Aby bylo možné pro přístup ke členům libovolný objekt přiřadit k proměnné, je nutné nastavit `Option Strict Off`.</span><span class="sxs-lookup"><span data-stu-id="a4013-125">To be able to access the members of any object you assign to the object variable, you must set `Option Strict Off`.</span></span> <span data-ttu-id="a4013-126">Když toto provedete, kompilátor nemůže zaručit, že je daný člen je zveřejněný prostřednictvím objektu, který je přiřadit k proměnné.</span><span class="sxs-lookup"><span data-stu-id="a4013-126">When you do this, the compiler cannot guarantee that a given member is exposed by the object you assign to the variable.</span></span> <span data-ttu-id="a4013-127">Pokud objekt nevystavuje člen pokus o přístup, <xref:System.MemberAccessException> dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="a4013-127">If the object does not expose a member you attempt to access, a <xref:System.MemberAccessException> exception occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4013-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a4013-128">See also</span></span>

- <xref:System.Object>
- <xref:System.Windows.Forms.Form>
- <xref:System.MemberAccessException>
- [<span data-ttu-id="a4013-129">Objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="a4013-129">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="a4013-130">Deklarace objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="a4013-130">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="a4013-131">Datový typ Object</span><span class="sxs-lookup"><span data-stu-id="a4013-131">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="a4013-132">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="a4013-132">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
