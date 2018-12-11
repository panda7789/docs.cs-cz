---
title: 'Postupy: Manipulace s řetězci základní v .NET'
description: Viz příklad, který volá metody mnoha řetězci.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET Framework], examples
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
author: rpetrusha
ms.author: ronpet
ms.custom: seodec18
ms.openlocfilehash: 11f8043745c631a642b437339240cbf06fc8df5b
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130634"
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a><span data-ttu-id="842ed-103">Postupy: Manipulace s řetězci základní v .NET</span><span class="sxs-lookup"><span data-stu-id="842ed-103">How to: Perform Basic String Manipulations in .NET</span></span>
<span data-ttu-id="842ed-104">Následující příklad používá některé z metod popsaných v tématu [základní operace s řetězci](../../../docs/standard/base-types/basic-string-operations.md) témata k vytvoření třídy, která provádí manipulace s řetězci způsobem, který se může nacházet v reálné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="842ed-104">The following example uses some of the methods discussed in the [Basic String Operations](../../../docs/standard/base-types/basic-string-operations.md) topics to construct a class that performs string manipulations in a manner that might be found in a real-world application.</span></span> <span data-ttu-id="842ed-105">`MailToData` Třída obsahuje název a adresu osoby v samostatných vlastnosti a poskytuje způsob, jak zkombinovat `City`, `State`, a `Zip` pole do jednoho řetězce pro zobrazení pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="842ed-105">The `MailToData` class stores the name and address of an individual in separate properties and provides a way to combine the `City`, `State`, and `Zip` fields into a single string for display to the user.</span></span> <span data-ttu-id="842ed-106">Kromě toho třída umožňuje uživateli zadat město, stát a informace o PSČ jako jeden řetězec; aplikaci automaticky analyzuje jeden řetězec a vloží do odpovídající vlastnosti správné informace.</span><span class="sxs-lookup"><span data-stu-id="842ed-106">Furthermore, the class allows the user to enter the city, state, and ZIP Code information as a single string; the application automatically parses the single string and enters the proper information into the corresponding property.</span></span>  
  
 <span data-ttu-id="842ed-107">Pro zjednodušení tento příklad používá konzolovou aplikaci pomocí rozhraní příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="842ed-107">For simplicity, this example uses a console application with a command-line interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="842ed-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="842ed-108">Example</span></span>  
 [!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
 [!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]  
  
 <span data-ttu-id="842ed-109">Pokud je spuštěn předchozí kód, uživatel se zobrazí výzva, zadejte název nebo adresu.</span><span class="sxs-lookup"><span data-stu-id="842ed-109">When the preceding code is executed, the user is asked to enter his or her name and address.</span></span> <span data-ttu-id="842ed-110">Aplikace umístí informace v příslušné vlastnosti a zobrazí informace uživateli vytvořit jeden řetězec, který zobrazuje Město, stát a informace o PSČ.</span><span class="sxs-lookup"><span data-stu-id="842ed-110">The application places the information in the appropriate properties and displays the information back to the user, creating a single string that displays the city, state, and ZIP Code information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="842ed-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="842ed-111">See also</span></span>

- [<span data-ttu-id="842ed-112">Základní operace s řetězci</span><span class="sxs-lookup"><span data-stu-id="842ed-112">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
