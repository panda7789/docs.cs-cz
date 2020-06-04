---
title: 'Postupy: Určení řetězce spojeného s hodnotou výčtu'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
ms.openlocfilehash: 525da9206472afefa9f85b49ceee0775cbd168c3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414463"
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a><span data-ttu-id="7842e-102">Postupy: Určení řetězce spojeného s hodnotou výčtu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7842e-102">How to: Determine the String Associated with an Enumeration Value (Visual Basic)</span></span>
<span data-ttu-id="7842e-103"><xref:System.Enum.GetValues%2A>Metody a <xref:System.Enum.GetNames%2A> umožňují určit řetězce a hodnoty přidružené ke členům výčtu.</span><span class="sxs-lookup"><span data-stu-id="7842e-103">The <xref:System.Enum.GetValues%2A> and <xref:System.Enum.GetNames%2A> methods allow you to determine the strings and values associated with enumeration members.</span></span>  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a><span data-ttu-id="7842e-104">Určení řetězce přidruženého k výčtu</span><span class="sxs-lookup"><span data-stu-id="7842e-104">To determine the string associated with an enumeration</span></span>  
  
- <span data-ttu-id="7842e-105">Použijte <xref:System.Enum.GetNames%2A> metodu pro načtení řetězců přidružených k členům výčtu.</span><span class="sxs-lookup"><span data-stu-id="7842e-105">Use the <xref:System.Enum.GetNames%2A> method to retrieve the strings associated with the enumeration members.</span></span> <span data-ttu-id="7842e-106">Tento příklad deklaruje výčet, `flavorEnum` a poté používá <xref:System.Enum.GetNames%2A> metodu k zobrazení řetězců přidružených k jednotlivým členům.</span><span class="sxs-lookup"><span data-stu-id="7842e-106">This example declares an enumeration, `flavorEnum`, then uses the <xref:System.Enum.GetNames%2A> method to display the strings associated with each member.</span></span>  
  
     [!code-vb[VbEnumsTask#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="7842e-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="7842e-107">See also</span></span>

- <xref:System.Enum.GetValues%2A>
- <xref:System.Enum.GetNames%2A>
- <xref:System.Enum>
- [<span data-ttu-id="7842e-108">Postupy: deklarace výčtu</span><span class="sxs-lookup"><span data-stu-id="7842e-108">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="7842e-109">Postupy: Odkazování na člena výčtu</span><span class="sxs-lookup"><span data-stu-id="7842e-109">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="7842e-110">Výčty a kvalifikace názvu</span><span class="sxs-lookup"><span data-stu-id="7842e-110">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="7842e-111">Postupy: Iterace ve výčtu jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7842e-111">How to: Iterate Through An Enumeration in Visual Basic</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="7842e-112">Kdy použít výčet</span><span class="sxs-lookup"><span data-stu-id="7842e-112">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="7842e-113">Enum – příkaz</span><span class="sxs-lookup"><span data-stu-id="7842e-113">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)
