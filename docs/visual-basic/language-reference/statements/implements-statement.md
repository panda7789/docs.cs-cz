---
title: "Implements – Příkaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Implements
- Implements
helpviewer_keywords:
- Implements statement [Visual Basic], syntax
- Implements statement [Visual Basic]
- interface implementation [Visual Basic], Implements statement
ms.assetid: 1fafb83f-f55a-4215-8ea9-681e8622613d
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1103305ffbf5425d9a6a6a09695437968642710d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="implements-statement"></a><span data-ttu-id="27a5a-102">Implements – Příkaz</span><span class="sxs-lookup"><span data-stu-id="27a5a-102">Implements Statement</span></span>
<span data-ttu-id="27a5a-103">Určuje jeden nebo více rozhraní, nebo členy rozhraní, které musí být implementována ve třídě nebo definice struktury, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="27a5a-103">Specifies one or more interfaces, or interface members, that must be implemented in the class or structure definition in which it appears.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27a5a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27a5a-104">Syntax</span></span>  
  
```  
Implements interfacename [, ...]  
-or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="27a5a-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="27a5a-105">Parts</span></span>  
 `interfacename`  
 <span data-ttu-id="27a5a-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="27a5a-106">Required.</span></span> <span data-ttu-id="27a5a-107">Rozhraní, jejichž vlastnosti, postupy a události se mají odpovídající členové v třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="27a5a-107">An interface whose properties, procedures, and events are to be implemented by corresponding members in the class or structure.</span></span>  
  
 `interfacemember`  
 <span data-ttu-id="27a5a-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="27a5a-108">Required.</span></span> <span data-ttu-id="27a5a-109">Členové rozhraní, které se implementuje.</span><span class="sxs-lookup"><span data-stu-id="27a5a-109">The member of an interface that is being implemented.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27a5a-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="27a5a-110">Remarks</span></span>  
 <span data-ttu-id="27a5a-111">Rozhraní je kolekce představující členy (vlastnosti, postupy a události) prototypů zapouzdří rozhraní.</span><span class="sxs-lookup"><span data-stu-id="27a5a-111">An interface is a collection of prototypes representing the members (properties, procedures, and events) the interface encapsulates.</span></span> <span data-ttu-id="27a5a-112">Rozhraní obsahovat pouze deklarace pro členy; třídy a struktury implementovat tyto členy.</span><span class="sxs-lookup"><span data-stu-id="27a5a-112">Interfaces contain only the declarations for members; classes and structures implement these members.</span></span> <span data-ttu-id="27a5a-113">Další informace najdete v tématu [rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="27a5a-113">For more information, see [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="27a5a-114">`Implements` Příkaz okamžitě postupujte `Class` nebo `Structure` příkaz.</span><span class="sxs-lookup"><span data-stu-id="27a5a-114">The `Implements` statement must immediately follow the `Class` or `Structure` statement.</span></span>  
  
 <span data-ttu-id="27a5a-115">Při implementaci rozhraní musí implementovat všechny členy v rozhraní deklarovat.</span><span class="sxs-lookup"><span data-stu-id="27a5a-115">When you implement an interface, you must implement all the members declared in the interface.</span></span> <span data-ttu-id="27a5a-116">Vynechání kteréhokoli člena se považuje za chybu syntaxe.</span><span class="sxs-lookup"><span data-stu-id="27a5a-116">Omitting any member is considered to be a syntax error.</span></span> <span data-ttu-id="27a5a-117">K implementaci jednotlivými členy, zadejte [implementuje](../../../visual-basic/language-reference/statements/implements-clause.md) – klíčové slovo (které jsou oddělené od `Implements` příkaz) Pokud je člen v třídu nebo strukturu deklarovat.</span><span class="sxs-lookup"><span data-stu-id="27a5a-117">To implement an individual member, you specify the [Implements](../../../visual-basic/language-reference/statements/implements-clause.md) keyword (which is separate from the `Implements` statement) when you declare the member in the class or structure.</span></span> <span data-ttu-id="27a5a-118">Další informace najdete v tématu [rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="27a5a-118">For more information, see [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="27a5a-119">Můžete použít třídy [privátní](../../../visual-basic/language-reference/modifiers/private.md) implementace vlastností a postupy, ale tito členové jsou přístupné pouze přetypování deklarována instance implementující třídu do proměnné být typu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="27a5a-119">Classes can use [Private](../../../visual-basic/language-reference/modifiers/private.md) implementations of properties and procedures, but these members are accessible only by casting an instance of the implementing class into a variable declared to be of the type of the interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27a5a-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="27a5a-120">Example</span></span>  
 <span data-ttu-id="27a5a-121">Následující příklad ukazuje způsob použití `Implements` příkaz, který má implementace členů rozhraní.</span><span class="sxs-lookup"><span data-stu-id="27a5a-121">The following example shows how to use the `Implements` statement to implement members of an interface.</span></span> <span data-ttu-id="27a5a-122">Definuje rozhraní s názvem `ICustomerInfo` se událost, vlastnosti a procedury.</span><span class="sxs-lookup"><span data-stu-id="27a5a-122">It defines an interface named `ICustomerInfo` with an event, a property, and a procedure.</span></span> <span data-ttu-id="27a5a-123">Třída `customerInfo` implementuje všechny členy, které jsou definované v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="27a5a-123">The class `customerInfo` implements all the members defined in the interface.</span></span>  
  
 [!code-vb[VbVbalrStatements#33](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/implements-statement_1.vb)]  
  
 <span data-ttu-id="27a5a-124">Všimněte si, že třída `customerInfo` používá `Implements` příkazem na řádku samostatného zdrojového kódu k označení, že třída implementuje všechny členy `ICustomerInfo` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="27a5a-124">Note that the class `customerInfo` uses the `Implements` statement on a separate source code line to indicate that the class implements all the members of the `ICustomerInfo` interface.</span></span> <span data-ttu-id="27a5a-125">Poté každý člen ve třídě, používá `Implements` – klíčové slovo v rámci jeho deklarace členů k označení, že implementuje tohoto člena rozhraní.</span><span class="sxs-lookup"><span data-stu-id="27a5a-125">Then each member in the class uses the `Implements` keyword as part of its member declaration to indicate that it implements that interface member.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27a5a-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="27a5a-126">Example</span></span>  
 <span data-ttu-id="27a5a-127">Následující dva postupy ukazují, jak můžete použít rozhraní implementované v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="27a5a-127">The following two procedures show how you could use the interface implemented in the preceding example.</span></span> <span data-ttu-id="27a5a-128">Chcete-li otestovat implementace, přidejte tyto postupy projekt a volání `testImplements` postupu.</span><span class="sxs-lookup"><span data-stu-id="27a5a-128">To test the implementation, add these procedures to your project and call the `testImplements` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#34](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/implements-statement_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="27a5a-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="27a5a-129">See Also</span></span>  
 [<span data-ttu-id="27a5a-130">Implementuje</span><span class="sxs-lookup"><span data-stu-id="27a5a-130">Implements</span></span>](../../../visual-basic/language-reference/statements/implements-clause.md)  
 [<span data-ttu-id="27a5a-131">Interface – příkaz</span><span class="sxs-lookup"><span data-stu-id="27a5a-131">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="27a5a-132">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="27a5a-132">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
