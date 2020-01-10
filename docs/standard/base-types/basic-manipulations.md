---
title: 'Postupy: provádění základních manipulace s řetězci v rozhraní .NET'
description: Podívejte se na příklad, který volá mnoho řetězcových metod.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET Framework], examples
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
ms.openlocfilehash: ff7abee460b4085fa9e039e678c975338ccb511a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711503"
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a><span data-ttu-id="6fde3-103">Postupy: provádění základních manipulace s řetězci v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="6fde3-103">How to: Perform Basic String Manipulations in .NET</span></span>
<span data-ttu-id="6fde3-104">Následující příklad používá některé z metod popsaných v tématech [základních řetězcových operací](../../../docs/standard/base-types/basic-string-operations.md) k vytvoření třídy, která provádí manipulaci s řetězci způsobem, který může být nalezen v reálné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="6fde3-104">The following example uses some of the methods discussed in the [Basic String Operations](../../../docs/standard/base-types/basic-string-operations.md) topics to construct a class that performs string manipulations in a manner that might be found in a real-world application.</span></span> <span data-ttu-id="6fde3-105">Třída `MailToData` ukládá jméno a adresu jednotlivce do samostatných vlastností a poskytuje způsob, jak kombinovat pole `City`, `State`a `Zip` do jednoho řetězce pro zobrazení uživateli.</span><span class="sxs-lookup"><span data-stu-id="6fde3-105">The `MailToData` class stores the name and address of an individual in separate properties and provides a way to combine the `City`, `State`, and `Zip` fields into a single string for display to the user.</span></span> <span data-ttu-id="6fde3-106">Kromě toho třída umožňuje uživateli zadat město, stav a informace o PSČ jako jeden řetězec; aplikace automaticky analyzuje jediný řetězec a zadá správné informace do odpovídající vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6fde3-106">Furthermore, the class allows the user to enter the city, state, and ZIP Code information as a single string; the application automatically parses the single string and enters the proper information into the corresponding property.</span></span>  
  
 <span data-ttu-id="6fde3-107">V zájmu jednoduchosti tento příklad používá konzolovou aplikaci s rozhraním příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="6fde3-107">For simplicity, this example uses a console application with a command-line interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6fde3-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="6fde3-108">Example</span></span>  
 [!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
 [!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]  
  
 <span data-ttu-id="6fde3-109">Po spuštění předchozího kódu se uživateli zobrazí výzva k zadání jeho jména a adresy.</span><span class="sxs-lookup"><span data-stu-id="6fde3-109">When the preceding code is executed, the user is asked to enter his or her name and address.</span></span> <span data-ttu-id="6fde3-110">Aplikace umístí informace do příslušných vlastností a zobrazí informace zpět uživateli a vytvoří jeden řetězec, který zobrazí informace o městě, stavu a PSČ.</span><span class="sxs-lookup"><span data-stu-id="6fde3-110">The application places the information in the appropriate properties and displays the information back to the user, creating a single string that displays the city, state, and ZIP Code information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fde3-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6fde3-111">See also</span></span>

- [<span data-ttu-id="6fde3-112">Základní operace s řetězci</span><span class="sxs-lookup"><span data-stu-id="6fde3-112">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
