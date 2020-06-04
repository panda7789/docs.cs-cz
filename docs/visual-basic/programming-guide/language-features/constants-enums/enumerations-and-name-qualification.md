---
title: Výčty a kvalifikace názvu
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- Imports statement [Visual Basic], namespace declarations
- declaring namespaces [Visual Basic], enumerations
- name collisions
- ambiguous names [Visual Basic], enumerations
- enumerations [Visual Basic], name qualification
- names [Visual Basic], avoiding conflicts
- namespaces [Visual Basic], declaring
- naming conflicts, enumerations
- naming conflicts, qualifying names
- declaring enumerations
- references [Visual Basic], enumeration members
- naming conventions [Visual Basic], naming conflicts
- declarations [Visual Basic], namespaces
ms.assetid: 08ba2738-df52-4140-bc55-f57c871c9b73
ms.openlocfilehash: 4b09284b8282c481e406050d37cbdb2f3c8686bc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414502"
---
# <a name="enumerations-and-name-qualification-visual-basic"></a><span data-ttu-id="f4552-102">Výčty a kvalifikace názvu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f4552-102">Enumerations and Name Qualification (Visual Basic)</span></span>
<span data-ttu-id="f4552-103">Obvykle při odkazování na člena výčtu musíte kvalifikovat název člena s názvem výčtu.</span><span class="sxs-lookup"><span data-stu-id="f4552-103">Normally, when referring to a member of an enumeration, you must qualify the member name with the enumeration name.</span></span> <span data-ttu-id="f4552-104">Například pro odkazování na `Sunday` člena `Days` výčtu byste měli použít následující syntaxi:</span><span class="sxs-lookup"><span data-stu-id="f4552-104">For example, to refer to the `Sunday` member of your `Days` enumeration, you would use the following syntax:</span></span>  
  
 [!code-vb[VbEnumsTask#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#18)]  
  
## <a name="using-the-imports-statement"></a><span data-ttu-id="f4552-105">Použití příkazu Imports</span><span class="sxs-lookup"><span data-stu-id="f4552-105">Using the Imports Statement</span></span>  
 <span data-ttu-id="f4552-106">Můžete se vyhnout použití plně kvalifikovaného názvu přidáním `Imports` příkazu do oddílu deklarace oboru názvů v kódu, jak je uvedeno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f4552-106">You can avoid using fully qualified names by adding an `Imports` statement to the namespace declarations section of your code, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 <span data-ttu-id="f4552-107">`Imports`Příkaz naimportuje názvy oborů názvů z odkazovaných projektů a sestavení a ze stejného projektu jako modul, ve kterém se zobrazí příkaz.</span><span class="sxs-lookup"><span data-stu-id="f4552-107">An `Imports` statement imports namespace names from referenced projects and assemblies and from within the same project as the module in which the statement appears.</span></span> <span data-ttu-id="f4552-108">Po přidání tohoto příkazu můžete odkazovat na členy výčtu bez kvalifikace, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f4552-108">Once this statement is added, you can refer to your enumeration members without qualification, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#24)]  
  
 <span data-ttu-id="f4552-109">Uspořádáním sad souvisejících konstant v výčtech můžete použít stejné konstantní názvy v různých kontextech.</span><span class="sxs-lookup"><span data-stu-id="f4552-109">By organizing sets of related constants in enumerations, you can use the same constant names in different contexts.</span></span> <span data-ttu-id="f4552-110">Můžete například použít stejné názvy pro konstanty v týdnu ve `Days` `WorkDays` výčtech a.</span><span class="sxs-lookup"><span data-stu-id="f4552-110">For example, you can use the same names for the weekday constants in the `Days` and `WorkDays` enumerations.</span></span> <span data-ttu-id="f4552-111">Použijete-li `Imports` příkaz s výčty, musíte být opatrní, aby nedocházelo k nejednoznačným odkazům.</span><span class="sxs-lookup"><span data-stu-id="f4552-111">If you use the `Imports` statement with your enumerations, you must be careful to avoid ambiguous references.</span></span> <span data-ttu-id="f4552-112">Uvažujte následující příklad:</span><span class="sxs-lookup"><span data-stu-id="f4552-112">Consider the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 [!code-vb[VbEnumsTask#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#25)]  
  
 <span data-ttu-id="f4552-113">Za předpokladu, že `Monday` je členem `Days` výčtu i `Workdays` výčtu, tento kód vygeneruje chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="f4552-113">Assuming that `Monday` is a member of both the `Days` enumeration and the `Workdays` enumeration, this code generates a compiler error.</span></span> <span data-ttu-id="f4552-114">Chcete-li se vyhnout dvojznačným odkazům při odkazování na jednotlivé konstanty, kvalifikovat název konstanty pomocí jeho výčtu.</span><span class="sxs-lookup"><span data-stu-id="f4552-114">To avoid ambiguous references when referring to an individual constant, qualify the constant name with its enumeration.</span></span> <span data-ttu-id="f4552-115">Následující kód odkazuje na `Saturday` konstanty ve `Days` `WorkDays` výčtech a.</span><span class="sxs-lookup"><span data-stu-id="f4552-115">The following code refers to the `Saturday` constants in the `Days` and `WorkDays` enumerations.</span></span>  
  
 [!code-vb[VbEnumsTask#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="f4552-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="f4552-116">See also</span></span>

- [<span data-ttu-id="f4552-117">Konstanty a výčty</span><span class="sxs-lookup"><span data-stu-id="f4552-117">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
- [<span data-ttu-id="f4552-118">Postupy: deklarace výčtu</span><span class="sxs-lookup"><span data-stu-id="f4552-118">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="f4552-119">Postupy: Odkazování na člena výčtu</span><span class="sxs-lookup"><span data-stu-id="f4552-119">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="f4552-120">Postupy: Iterace ve výčtu jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f4552-120">How to: Iterate Through An Enumeration in Visual Basic</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="f4552-121">Postupy: Určení řetězce spojeného s hodnotou výčtu</span><span class="sxs-lookup"><span data-stu-id="f4552-121">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="f4552-122">Kdy použít výčet</span><span class="sxs-lookup"><span data-stu-id="f4552-122">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="f4552-123">Datové typy konstanty a literálu</span><span class="sxs-lookup"><span data-stu-id="f4552-123">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="f4552-124">Enum – příkaz</span><span class="sxs-lookup"><span data-stu-id="f4552-124">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)
- [<span data-ttu-id="f4552-125">Imports – příkaz (obor názvů a typ rozhraní .NET)</span><span class="sxs-lookup"><span data-stu-id="f4552-125">Imports Statement (.NET Namespace and Type)</span></span>](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="f4552-126">Datové typy</span><span class="sxs-lookup"><span data-stu-id="f4552-126">Data Types</span></span>](../../../language-reference/data-types/index.md)
