---
title: 'Postupy: Iterace ve výčtu'
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: fb6fbdd45ca0e84ccb9fc55296d78e3867d5fe25
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414424"
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a><span data-ttu-id="de28b-102">Postupy: Iterace ve výčtu jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="de28b-102">How to: Iterate Through An Enumeration in Visual Basic</span></span>
<span data-ttu-id="de28b-103">Výčty poskytují pohodlný způsob práce se sadami souvisejících konstant a k přidružení konstantních hodnot k názvům.</span><span class="sxs-lookup"><span data-stu-id="de28b-103">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="de28b-104">Chcete-li iterovat prostřednictvím výčtu, můžete jej přesunout do pole pomocí <xref:System.Enum.GetValues%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="de28b-104">To iterate through an enumeration, you can move it into an array using the <xref:System.Enum.GetValues%2A> method.</span></span> <span data-ttu-id="de28b-105">Můžete také iterovat prostřednictvím výčtu pomocí `For...Each` příkazu <xref:System.Enum.GetNames%2A> nebo <xref:System.Enum.GetValues%2A> k extrakci řetězcové nebo číselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="de28b-105">You could also iterate through an enumeration using a `For...Each` statement, using the <xref:System.Enum.GetNames%2A> or <xref:System.Enum.GetValues%2A> method to extract the string or numeric value.</span></span>  
  
### <a name="to-iterate-through-an-enumeration"></a><span data-ttu-id="de28b-106">Iterace prostřednictvím výčtu</span><span class="sxs-lookup"><span data-stu-id="de28b-106">To iterate through an enumeration</span></span>  
  
- <span data-ttu-id="de28b-107">Deklarujte pole a převeďte na něj výčet pomocí <xref:System.Enum.GetValues%2A> metody před předáním pole stejným způsobem jako jakákoli jiná proměnná.</span><span class="sxs-lookup"><span data-stu-id="de28b-107">Declare an array and convert the enumeration to it with the <xref:System.Enum.GetValues%2A> method before passing the array as you would any other variable.</span></span> <span data-ttu-id="de28b-108">Následující příklad zobrazuje jednotlivé členy výčtu <xref:Microsoft.VisualBasic.FirstDayOfWeek> při iterování prostřednictvím výčtu.</span><span class="sxs-lookup"><span data-stu-id="de28b-108">The following example displays each member of the enumeration <xref:Microsoft.VisualBasic.FirstDayOfWeek> as it iterates through the enumeration.</span></span>  
  
     [!code-vb[VbEnumsTask#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="de28b-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="de28b-109">See also</span></span>

- [<span data-ttu-id="de28b-110">Přehled výčtů</span><span class="sxs-lookup"><span data-stu-id="de28b-110">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="de28b-111">Postupy: deklarace výčtu</span><span class="sxs-lookup"><span data-stu-id="de28b-111">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="de28b-112">Kdy použít výčet</span><span class="sxs-lookup"><span data-stu-id="de28b-112">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="de28b-113">Postupy: Určení řetězce spojeného s hodnotou výčtu</span><span class="sxs-lookup"><span data-stu-id="de28b-113">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="de28b-114">Postupy: Odkazování na člena výčtu</span><span class="sxs-lookup"><span data-stu-id="de28b-114">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="de28b-115">Výčty a kvalifikace názvu</span><span class="sxs-lookup"><span data-stu-id="de28b-115">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="de28b-116">Pole</span><span class="sxs-lookup"><span data-stu-id="de28b-116">Arrays</span></span>](../arrays/index.md)
