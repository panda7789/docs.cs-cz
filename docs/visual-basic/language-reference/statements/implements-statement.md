---
title: Implements – Příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.Implements
- Implements
helpviewer_keywords:
- Implements statement [Visual Basic], syntax
- Implements statement [Visual Basic]
- interface implementation [Visual Basic], Implements statement
ms.assetid: 1fafb83f-f55a-4215-8ea9-681e8622613d
ms.openlocfilehash: e2e279b2c935dd082cbf832265a8ad09e6dffe9e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351150"
---
# <a name="implements-statement"></a><span data-ttu-id="8af84-102">Implements – Příkaz</span><span class="sxs-lookup"><span data-stu-id="8af84-102">Implements Statement</span></span>
<span data-ttu-id="8af84-103">Určuje jedno nebo více rozhraní nebo členů rozhraní, které musí být implementovány v definici třídy nebo struktury, ve které se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="8af84-103">Specifies one or more interfaces, or interface members, that must be implemented in the class or structure definition in which it appears.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8af84-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8af84-104">Syntax</span></span>  
  
```vb  
Implements interfacename [, ...]  
' -or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="8af84-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="8af84-105">Parts</span></span>  
 `interfacename`  
 <span data-ttu-id="8af84-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="8af84-106">Required.</span></span> <span data-ttu-id="8af84-107">Rozhraní, jehož vlastnosti, procedury a události mají být implementovány odpovídajícími členy třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="8af84-107">An interface whose properties, procedures, and events are to be implemented by corresponding members in the class or structure.</span></span>  
  
 `interfacemember`  
 <span data-ttu-id="8af84-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="8af84-108">Required.</span></span> <span data-ttu-id="8af84-109">Člen rozhraní, které je implementováno.</span><span class="sxs-lookup"><span data-stu-id="8af84-109">The member of an interface that is being implemented.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8af84-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8af84-110">Remarks</span></span>  
 <span data-ttu-id="8af84-111">Rozhraní je kolekce prototypů představujících členy (vlastnosti, procedury a události) zapouzdření rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8af84-111">An interface is a collection of prototypes representing the members (properties, procedures, and events) the interface encapsulates.</span></span> <span data-ttu-id="8af84-112">Rozhraní obsahují pouze deklarace členů; třídy a struktury implementují tyto členy.</span><span class="sxs-lookup"><span data-stu-id="8af84-112">Interfaces contain only the declarations for members; classes and structures implement these members.</span></span> <span data-ttu-id="8af84-113">Další informace naleznete v tématu [rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="8af84-113">For more information, see [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="8af84-114">Příkaz `Implements` musí bezprostředně následovat po příkazu `Class` nebo `Structure`.</span><span class="sxs-lookup"><span data-stu-id="8af84-114">The `Implements` statement must immediately follow the `Class` or `Structure` statement.</span></span>  
  
 <span data-ttu-id="8af84-115">Při implementaci rozhraní je nutné implementovat všechny členy deklarované v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8af84-115">When you implement an interface, you must implement all the members declared in the interface.</span></span> <span data-ttu-id="8af84-116">Vynechání všech členů je považováno za chybu syntaxe.</span><span class="sxs-lookup"><span data-stu-id="8af84-116">Omitting any member is considered to be a syntax error.</span></span> <span data-ttu-id="8af84-117">Chcete-li implementovat jednotlivé členy, zadáte klíčové slovo [Implements](../../../visual-basic/language-reference/statements/implements-clause.md) (které je odděleno od příkazu `Implements`), pokud deklarujete člena ve třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="8af84-117">To implement an individual member, you specify the [Implements](../../../visual-basic/language-reference/statements/implements-clause.md) keyword (which is separate from the `Implements` statement) when you declare the member in the class or structure.</span></span> <span data-ttu-id="8af84-118">Další informace naleznete v tématu [rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="8af84-118">For more information, see [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="8af84-119">Třídy mohou používat [privátní](../../../visual-basic/language-reference/modifiers/private.md) implementace vlastností a postupů, ale tyto členy jsou přístupné pouze přetypováním instance implementující třídy do proměnné deklarované jako typ rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8af84-119">Classes can use [Private](../../../visual-basic/language-reference/modifiers/private.md) implementations of properties and procedures, but these members are accessible only by casting an instance of the implementing class into a variable declared to be of the type of the interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8af84-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="8af84-120">Example</span></span>  
 <span data-ttu-id="8af84-121">Následující příklad ukazuje, jak použít příkaz `Implements` pro implementaci členů rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8af84-121">The following example shows how to use the `Implements` statement to implement members of an interface.</span></span> <span data-ttu-id="8af84-122">Definuje rozhraní s názvem `ICustomerInfo` s událostí, vlastností a procedurou.</span><span class="sxs-lookup"><span data-stu-id="8af84-122">It defines an interface named `ICustomerInfo` with an event, a property, and a procedure.</span></span> <span data-ttu-id="8af84-123">Třída `customerInfo` implementuje všechny členy definované v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8af84-123">The class `customerInfo` implements all the members defined in the interface.</span></span>  
  
 [!code-vb[VbVbalrStatements#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#33)]  
  
 <span data-ttu-id="8af84-124">Všimněte si, že třída `customerInfo` používá příkaz `Implements` na samostatné řádce zdrojového kódu k označení toho, že třída implementuje všechny členy rozhraní `ICustomerInfo`.</span><span class="sxs-lookup"><span data-stu-id="8af84-124">Note that the class `customerInfo` uses the `Implements` statement on a separate source code line to indicate that the class implements all the members of the `ICustomerInfo` interface.</span></span> <span data-ttu-id="8af84-125">Pak každý člen ve třídě používá klíčové slovo `Implements` jako součást své deklarace členů, aby označoval, že implementuje tento člen rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8af84-125">Then each member in the class uses the `Implements` keyword as part of its member declaration to indicate that it implements that interface member.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8af84-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="8af84-126">Example</span></span>  
 <span data-ttu-id="8af84-127">Následující dva postupy ukazují, jak můžete použít rozhraní implementované v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8af84-127">The following two procedures show how you could use the interface implemented in the preceding example.</span></span> <span data-ttu-id="8af84-128">Chcete-li otestovat implementaci, přidejte tyto procedury do projektu a zavolejte `testImplements` proceduru.</span><span class="sxs-lookup"><span data-stu-id="8af84-128">To test the implementation, add these procedures to your project and call the `testImplements` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#34)]  
  
## <a name="see-also"></a><span data-ttu-id="8af84-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8af84-129">See also</span></span>

- [<span data-ttu-id="8af84-130">Implementace</span><span class="sxs-lookup"><span data-stu-id="8af84-130">Implements</span></span>](../../../visual-basic/language-reference/statements/implements-clause.md)
- [<span data-ttu-id="8af84-131">Příkaz Interface</span><span class="sxs-lookup"><span data-stu-id="8af84-131">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="8af84-132">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="8af84-132">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
