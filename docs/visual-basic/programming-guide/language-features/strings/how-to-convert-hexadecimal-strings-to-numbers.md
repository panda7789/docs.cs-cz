---
title: 'Postupy: Převod hexadecimálních řetězců na čísla'
ms.date: 01/31/2018
helpviewer_keywords:
- numbers [Visual Basic], hexadecimals
- hexadecimals [Visual Basic], decimals
- examples [Visual Basic], string conversion
- decimals [Visual Basic], hexadecimals
- string conversion [Visual Basic], hexadecimal to numbers
ms.assetid: 76675807-eadb-4c08-bd50-e6c6ff4b8ced
ms.openlocfilehash: f0a97a0c212a64bfa4db4606ee526b666f07877a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347175"
---
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a><span data-ttu-id="ec42e-102">Postupy: Převod hexadecimálních řetězců na čísla (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ec42e-102">How to: Convert Hexadecimal Strings to Numbers (Visual Basic)</span></span>

<span data-ttu-id="ec42e-103">Tento příklad převede šestnáctkový řetězec na celé číslo pomocí metody <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ec42e-103">This example converts a hexadecimal string to an integer using the <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> method.</span></span>

## <a name="to-convert-a-hexadecimal-string-to-a-number"></a><span data-ttu-id="ec42e-104">Převod šestnáctkového řetězce na číslo</span><span class="sxs-lookup"><span data-stu-id="ec42e-104">To convert a hexadecimal string to a number</span></span>

- <span data-ttu-id="ec42e-105">Použijte metodu <xref:System.Convert.ToInt32(System.String,System.Int32)> k převedení čísla vyjádřeného v základu-16 na celé číslo.</span><span class="sxs-lookup"><span data-stu-id="ec42e-105">Use the <xref:System.Convert.ToInt32(System.String,System.Int32)> method to convert the number expressed in base-16 to an integer.</span></span>

  <span data-ttu-id="ec42e-106">Prvním argumentem metody <xref:System.Convert.ToInt32(System.String,System.Int32)> je řetězec, který se má převést.</span><span class="sxs-lookup"><span data-stu-id="ec42e-106">The first argument of the <xref:System.Convert.ToInt32(System.String,System.Int32)> method is the string to convert.</span></span> <span data-ttu-id="ec42e-107">Druhý argument popisuje, na jaké bázi se číslo vyjadřuje. šestnáctková je 16.</span><span class="sxs-lookup"><span data-stu-id="ec42e-107">The second argument describes what base the number is expressed in; hexadecimal is base 16.</span></span>

  [!code-vb[VbVbalrStrings#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#62)]

- <span data-ttu-id="ec42e-108">Všimněte si, že šestnáctkový řetězec má následující omezení:</span><span class="sxs-lookup"><span data-stu-id="ec42e-108">Note that the hexadecimal string has the following restrictions:</span></span>

  - <span data-ttu-id="ec42e-109">Nemůže obsahovat předponu `&h`.</span><span class="sxs-lookup"><span data-stu-id="ec42e-109">It cannot include the `&h` prefix.</span></span>
  - <span data-ttu-id="ec42e-110">Nemůže obsahovat `_` oddělovač číslic.</span><span class="sxs-lookup"><span data-stu-id="ec42e-110">It cannot include the `_` digit separator.</span></span>

  <span data-ttu-id="ec42e-111">Pokud je k dispozici Předpona nebo oddělovač číslic, volání metody <xref:System.Convert.ToInt32(System.String,System.Int32)> vyvolá <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="ec42e-111">If the prefix or a digit separator is present, the call to the <xref:System.Convert.ToInt32(System.String,System.Int32)> method throws a <xref:System.FormatException>.</span></span>

## <a name="see-also"></a><span data-ttu-id="ec42e-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ec42e-112">See also</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>
