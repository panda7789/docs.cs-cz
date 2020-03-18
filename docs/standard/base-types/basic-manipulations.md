---
title: Základní manipulace s řetězci v rozhraní .NET
description: Viz příklad, který volá mnoho metod řetězce.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET Framework], examples
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
ms.openlocfilehash: 87ce7a79ce18ca8f5579841ad9e52e2519d6ac73
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187262"
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a><span data-ttu-id="87e25-103">Postup: Provedení základních manipulací s řetězci v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="87e25-103">How to: Perform Basic String Manipulations in .NET</span></span>

<span data-ttu-id="87e25-104">Následující příklad používá některé metody popsané v tématech [základní operace řetězce](../../../docs/standard/base-types/basic-string-operations.md) k vytvoření třídy, která provádí manipulaci s řetězci způsobem, který může být nalezen v reálné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="87e25-104">The following example uses some of the methods discussed in the [Basic String Operations](../../../docs/standard/base-types/basic-string-operations.md) topics to construct a class that performs string manipulations in a manner that might be found in a real-world application.</span></span> <span data-ttu-id="87e25-105">Třída `MailToData` ukládá název a adresu jednotlivce v samostatných vlastnostech `City`a `State`poskytuje `Zip` způsob, jak kombinovat , a pole do jednoho řetězce pro zobrazení uživateli.</span><span class="sxs-lookup"><span data-stu-id="87e25-105">The `MailToData` class stores the name and address of an individual in separate properties and provides a way to combine the `City`, `State`, and `Zip` fields into a single string for display to the user.</span></span> <span data-ttu-id="87e25-106">Kromě toho třída umožňuje uživateli zadat informace o městě, stavu a PSČ jako jeden řetězec; aplikace automaticky analyzuje jeden řetězec a zadá správné informace do odpovídající vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="87e25-106">Furthermore, the class allows the user to enter the city, state, and ZIP Code information as a single string; the application automatically parses the single string and enters the proper information into the corresponding property.</span></span>  
  
<span data-ttu-id="87e25-107">Pro jednoduchost tento příklad používá konzolovou aplikaci s rozhraním příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="87e25-107">For simplicity, this example uses a console application with a command-line interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87e25-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="87e25-108">Example</span></span>  

[!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
[!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]  
  
<span data-ttu-id="87e25-109">Při spuštění předchozího kódu je uživatel vyzván k zadání svého jména a adresy.</span><span class="sxs-lookup"><span data-stu-id="87e25-109">When the preceding code is executed, the user is asked to enter their name and address.</span></span> <span data-ttu-id="87e25-110">Aplikace umístí informace do příslušných vlastností a zobrazí informace zpět uživateli, čímž vytvoří jeden řetězec, který zobrazuje informace o městě, stavu a PSČ.</span><span class="sxs-lookup"><span data-stu-id="87e25-110">The application places the information in the appropriate properties and displays the information back to the user, creating a single string that displays the city, state, and ZIP Code information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87e25-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="87e25-111">See also</span></span>

- [<span data-ttu-id="87e25-112">Základní operace s řetězci</span><span class="sxs-lookup"><span data-stu-id="87e25-112">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
