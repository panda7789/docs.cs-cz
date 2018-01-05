---
title: "Postup: provedení manipulace s řetězci základní v rozhraní .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: strings [.NET Framework], examples
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8d3d5351a0a639a3f0b674640bcaaf7321ca0d76
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a><span data-ttu-id="72e9a-102">Postup: provedení manipulace s řetězci základní v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="72e9a-102">How to: Perform Basic String Manipulations in .NET</span></span>
<span data-ttu-id="72e9a-103">Následující příklad používá některé z metod popsaných v tématu [základní operace s řetězci](../../../docs/standard/base-types/basic-string-operations.md) témata pro vytvoření třídy, která provádí manipulace s řetězci způsobem, který se může nacházet v reálné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="72e9a-103">The following example uses some of the methods discussed in the [Basic String Operations](../../../docs/standard/base-types/basic-string-operations.md) topics to construct a class that performs string manipulations in a manner that might be found in a real-world application.</span></span> <span data-ttu-id="72e9a-104">`MailToData` Třída obsahuje název a adresu osoby v samostatných vlastnosti a poskytuje způsob, jak kombinovat `City`, `State`, a `Zip` do jednoho řetězce pro zobrazení pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="72e9a-104">The `MailToData` class stores the name and address of an individual in separate properties and provides a way to combine the `City`, `State`, and `Zip` fields into a single string for display to the user.</span></span> <span data-ttu-id="72e9a-105">Kromě toho třída umožňuje uživateli zadat města, státu a informace o PSČ jako jeden řetězec; aplikace automaticky analyzuje daný řetězec a vloží správné informace do odpovídající vlastnost.</span><span class="sxs-lookup"><span data-stu-id="72e9a-105">Furthermore, the class allows the user to enter the city, state, and ZIP Code information as a single string; the application automatically parses the single string and enters the proper information into the corresponding property.</span></span>  
  
 <span data-ttu-id="72e9a-106">Pro zjednodušení tento příklad používá konzolovou aplikaci pomocí rozhraní příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="72e9a-106">For simplicity, this example uses a console application with a command-line interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72e9a-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="72e9a-107">Example</span></span>  
 [!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
 [!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]  
  
 <span data-ttu-id="72e9a-108">Po provedení předchozí kód uživateli se zobrazí výzva k zadání názvu a adresy.</span><span class="sxs-lookup"><span data-stu-id="72e9a-108">When the preceding code is executed, the user is asked to enter his or her name and address.</span></span> <span data-ttu-id="72e9a-109">Aplikace umístí informace do příslušných vlastností a zobrazí informace o uživateli, vytvoření jednoho řetězce, který zobrazí města, státu a informace o PSČ.</span><span class="sxs-lookup"><span data-stu-id="72e9a-109">The application places the information in the appropriate properties and displays the information back to the user, creating a single string that displays the city, state, and ZIP Code information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72e9a-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="72e9a-110">See Also</span></span>  
 [<span data-ttu-id="72e9a-111">Základní operace s řetězci</span><span class="sxs-lookup"><span data-stu-id="72e9a-111">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
