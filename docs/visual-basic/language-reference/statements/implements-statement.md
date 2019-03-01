---
title: Implements – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Implements
- Implements
helpviewer_keywords:
- Implements statement [Visual Basic], syntax
- Implements statement [Visual Basic]
- interface implementation [Visual Basic], Implements statement
ms.assetid: 1fafb83f-f55a-4215-8ea9-681e8622613d
ms.openlocfilehash: 75776e0d78bc1d8a834333ea4c3cc0a9291d1ed1
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965008"
---
# <a name="implements-statement"></a><span data-ttu-id="3f19f-102">Implements – Příkaz</span><span class="sxs-lookup"><span data-stu-id="3f19f-102">Implements Statement</span></span>
<span data-ttu-id="3f19f-103">Určuje jeden nebo více rozhraní, nebo člen rozhraní, které musí být implementován ve třídě nebo definice struktury, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="3f19f-103">Specifies one or more interfaces, or interface members, that must be implemented in the class or structure definition in which it appears.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f19f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f19f-104">Syntax</span></span>  
  
```  
Implements interfacename [, ...]  
-or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="3f19f-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="3f19f-105">Parts</span></span>  
 `interfacename`  
 <span data-ttu-id="3f19f-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="3f19f-106">Required.</span></span> <span data-ttu-id="3f19f-107">Rozhraní, jehož vlastnosti, procedury a události jsou k implementaci odpovídající členy třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="3f19f-107">An interface whose properties, procedures, and events are to be implemented by corresponding members in the class or structure.</span></span>  
  
 `interfacemember`  
 <span data-ttu-id="3f19f-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="3f19f-108">Required.</span></span> <span data-ttu-id="3f19f-109">Člen rozhraní, které se implementuje.</span><span class="sxs-lookup"><span data-stu-id="3f19f-109">The member of an interface that is being implemented.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f19f-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3f19f-110">Remarks</span></span>  
 <span data-ttu-id="3f19f-111">Rozhraní je kolekce představující členy (vlastnosti, procedury a události) prototypů zapouzdřuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3f19f-111">An interface is a collection of prototypes representing the members (properties, procedures, and events) the interface encapsulates.</span></span> <span data-ttu-id="3f19f-112">Rozhraní obsahovat pouze deklarace pro členy. třídy a struktury implementace těchto členů.</span><span class="sxs-lookup"><span data-stu-id="3f19f-112">Interfaces contain only the declarations for members; classes and structures implement these members.</span></span> <span data-ttu-id="3f19f-113">Další informace najdete v tématu [rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="3f19f-113">For more information, see [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="3f19f-114">`Implements` Příkaz musí následovat bezprostředně `Class` nebo `Structure` příkazu.</span><span class="sxs-lookup"><span data-stu-id="3f19f-114">The `Implements` statement must immediately follow the `Class` or `Structure` statement.</span></span>  
  
 <span data-ttu-id="3f19f-115">Při implementaci rozhraní, musí implementovat všechny členy deklarované v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3f19f-115">When you implement an interface, you must implement all the members declared in the interface.</span></span> <span data-ttu-id="3f19f-116">Každý člen s vynecháním se považuje za chybu syntaxe.</span><span class="sxs-lookup"><span data-stu-id="3f19f-116">Omitting any member is considered to be a syntax error.</span></span> <span data-ttu-id="3f19f-117">Chcete-li implementovat jednotliví členové, zadejte [implementuje](../../../visual-basic/language-reference/statements/implements-clause.md) – klíčové slovo (které jsou oddělené od `Implements` příkaz) Pokud deklarujete člena třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="3f19f-117">To implement an individual member, you specify the [Implements](../../../visual-basic/language-reference/statements/implements-clause.md) keyword (which is separate from the `Implements` statement) when you declare the member in the class or structure.</span></span> <span data-ttu-id="3f19f-118">Další informace najdete v tématu [rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="3f19f-118">For more information, see [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="3f19f-119">Můžete použít třídy [privátní](../../../visual-basic/language-reference/modifiers/private.md) implementace vlastnosti a postupy, ale tyto členy jsou přístupné pouze pomocí přetypování instance implementující třídu do proměnné deklarované se typ rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3f19f-119">Classes can use [Private](../../../visual-basic/language-reference/modifiers/private.md) implementations of properties and procedures, but these members are accessible only by casting an instance of the implementing class into a variable declared to be of the type of the interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f19f-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="3f19f-120">Example</span></span>  
 <span data-ttu-id="3f19f-121">Následující příklad ukazuje způsob použití `Implements` příkaz implementovat členy rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3f19f-121">The following example shows how to use the `Implements` statement to implement members of an interface.</span></span> <span data-ttu-id="3f19f-122">Definuje rozhraní s názvem `ICustomerInfo` událost, vlastnosti a procedury.</span><span class="sxs-lookup"><span data-stu-id="3f19f-122">It defines an interface named `ICustomerInfo` with an event, a property, and a procedure.</span></span> <span data-ttu-id="3f19f-123">Třída `customerInfo` implementuje všechny členy definované v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3f19f-123">The class `customerInfo` implements all the members defined in the interface.</span></span>  
  
 [!code-vb[VbVbalrStatements#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#33)]  
  
 <span data-ttu-id="3f19f-124">Všimněte si, že třída `customerInfo` používá `Implements` příkazem na řádku samostatného zdrojového kódu k označení, že třída implementuje všechny členy `ICustomerInfo` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3f19f-124">Note that the class `customerInfo` uses the `Implements` statement on a separate source code line to indicate that the class implements all the members of the `ICustomerInfo` interface.</span></span> <span data-ttu-id="3f19f-125">Poté každý člen ve třídě, použije `Implements` – klíčové slovo jako součást její deklarace člena k označení, že implementuje člena rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3f19f-125">Then each member in the class uses the `Implements` keyword as part of its member declaration to indicate that it implements that interface member.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f19f-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="3f19f-126">Example</span></span>  
 <span data-ttu-id="3f19f-127">Následující dva postupy ukazují, jak můžete použít rozhraní implementované v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="3f19f-127">The following two procedures show how you could use the interface implemented in the preceding example.</span></span> <span data-ttu-id="3f19f-128">K otestování implementace, přidejte do projektu a volání těchto postupů `testImplements` postup.</span><span class="sxs-lookup"><span data-stu-id="3f19f-128">To test the implementation, add these procedures to your project and call the `testImplements` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#34)]  
  
## <a name="see-also"></a><span data-ttu-id="3f19f-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3f19f-129">See also</span></span>
- [<span data-ttu-id="3f19f-130">Implementuje</span><span class="sxs-lookup"><span data-stu-id="3f19f-130">Implements</span></span>](../../../visual-basic/language-reference/statements/implements-clause.md)
- [<span data-ttu-id="3f19f-131">Příkaz Interface</span><span class="sxs-lookup"><span data-stu-id="3f19f-131">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="3f19f-132">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="3f19f-132">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
