---
title: Výčet řetězců formátu – .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- format specifiers, enumeration format strings
- enumeration format strings
- formatting [.NET Framework], enumeration
ms.assetid: dd1ff672-1052-42cf-8666-4924fb6cd1a1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c71592537a31527bda6db08da8c36e798270d5a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032835"
---
# <a name="enumeration-format-strings"></a><span data-ttu-id="06dfd-102">Výčet řetězců formátu</span><span class="sxs-lookup"><span data-stu-id="06dfd-102">Enumeration format strings</span></span>

<span data-ttu-id="06dfd-103">Můžete použít <xref:System.Enum.ToString%2A?displayProperty=nameWithType> metodu pro vytvoření nového objektu řetězec, který představuje číselná, šestnáctkové číslo nebo řetězcové hodnoty na člena výčtu.</span><span class="sxs-lookup"><span data-stu-id="06dfd-103">You can use the <xref:System.Enum.ToString%2A?displayProperty=nameWithType> method to create a new string object that represents the numeric, hexadecimal, or string value of an enumeration member.</span></span> <span data-ttu-id="06dfd-104">Tato metoda přebírá jeden výčet formátování řetězce k určení, které se mají vracet hodnotu.</span><span class="sxs-lookup"><span data-stu-id="06dfd-104">This method takes one of the enumeration formatting strings to specify the value that you want returned.</span></span>

<span data-ttu-id="06dfd-105">Výčet formátování řetězců a hodnoty, které vracejí naleznete v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="06dfd-105">The following sections list the enumeration formatting strings and the values they return.</span></span> <span data-ttu-id="06dfd-106">Tyto specifikátory formátu nerozlišují malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="06dfd-106">These format specifiers are not case-sensitive.</span></span>

## <a name="g-or-g"></a><span data-ttu-id="06dfd-107">G nebo g</span><span class="sxs-lookup"><span data-stu-id="06dfd-107">G or g</span></span>

<span data-ttu-id="06dfd-108">Zobrazí výčet položku jako hodnotu řetězce, pokud je to možné a v opačném případě se zobrazí celočíselnou hodnotu aktuální instance.</span><span class="sxs-lookup"><span data-stu-id="06dfd-108">Displays the enumeration entry as a string value, if possible, and otherwise displays the integer value of the current instance.</span></span> <span data-ttu-id="06dfd-109">Pokud je definován výčet s **příznaky** nastaven atribut řetězců jsou hodnoty pro každou platnou položku zřetězených dohromady, oddělené čárkami.</span><span class="sxs-lookup"><span data-stu-id="06dfd-109">If the enumeration is defined with the **Flags** attribute set, the string values of each valid entry are concatenated together, separated by commas.</span></span> <span data-ttu-id="06dfd-110">Pokud **příznaky** atribut není nastaven, je neplatná hodnota zobrazí jako číselného vstupu.</span><span class="sxs-lookup"><span data-stu-id="06dfd-110">If the **Flags** attribute is not set, an invalid value is displayed as a numeric entry.</span></span> <span data-ttu-id="06dfd-111">Následující příklad ukazuje specifikátor formátu.</span><span class="sxs-lookup"><span data-stu-id="06dfd-111">The following example illustrates the G format specifier.</span></span>

[!code-csharp[Formatting.Enum#1](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#1)]
[!code-vb[Formatting.Enum#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#1)]

## <a name="f-or-f"></a><span data-ttu-id="06dfd-112">F nebo f</span><span class="sxs-lookup"><span data-stu-id="06dfd-112">F or f</span></span>

<span data-ttu-id="06dfd-113">Zobrazí výčet položku jako řetězcovou hodnotu, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="06dfd-113">Displays the enumeration entry as a string value, if possible.</span></span> <span data-ttu-id="06dfd-114">Pokud hodnota může být zcela zobrazena jako souhrn položky ve výčtu (i v případě, **příznaky** atribut není k dispozici), řetězcové hodnoty pro každou platnou položku jsou společně zřetězených, oddělené čárkami.</span><span class="sxs-lookup"><span data-stu-id="06dfd-114">If the value can be completely displayed as a summation of the entries in the enumeration (even if the **Flags** attribute is not present), the string values of each valid entry are concatenated together, separated by commas.</span></span> <span data-ttu-id="06dfd-115">Pokud hodnotu nelze určit zcela podle položek výčtu, hodnota formátována jako hodnota celého čísla.</span><span class="sxs-lookup"><span data-stu-id="06dfd-115">If the value cannot be completely determined by the enumeration entries, then the value is formatted as the integer value.</span></span> <span data-ttu-id="06dfd-116">Následující příklad ukazuje specifikátor formátu F.</span><span class="sxs-lookup"><span data-stu-id="06dfd-116">The following example illustrates the F format specifier.</span></span>

[!code-csharp[Formatting.Enum#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#2)]
[!code-vb[Formatting.Enum#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#2)]

## <a name="d-or-d"></a><span data-ttu-id="06dfd-117">D nebo d</span><span class="sxs-lookup"><span data-stu-id="06dfd-117">D or d</span></span>

<span data-ttu-id="06dfd-118">Zobrazí výčet položku jako celočíselnou hodnotu v nejkratší možné reprezentaci.</span><span class="sxs-lookup"><span data-stu-id="06dfd-118">Displays the enumeration entry as an integer value in the shortest representation possible.</span></span> <span data-ttu-id="06dfd-119">Následující příklad ukazuje specifikátor formátu D.</span><span class="sxs-lookup"><span data-stu-id="06dfd-119">The following example illustrates the D format specifier.</span></span>

[!code-csharp[Formatting.Enum#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#3)]
[!code-vb[Formatting.Enum#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#3)]

## <a name="x-or-x"></a><span data-ttu-id="06dfd-120">X or x</span><span class="sxs-lookup"><span data-stu-id="06dfd-120">X or x</span></span>

<span data-ttu-id="06dfd-121">Zobrazí výčet položku jako šestnáctková hodnota.</span><span class="sxs-lookup"><span data-stu-id="06dfd-121">Displays the enumeration entry as a hexadecimal value.</span></span> <span data-ttu-id="06dfd-122">Hodnota je reprezentován počátečními nulami podle potřeby zajistit, že hodnota je minimální osm číslic v délce.</span><span class="sxs-lookup"><span data-stu-id="06dfd-122">The value is represented with leading zeros as necessary, to ensure that the value is a minimum eight digits in length.</span></span> <span data-ttu-id="06dfd-123">Následující příklad ukazuje specifikátor formátu X.</span><span class="sxs-lookup"><span data-stu-id="06dfd-123">The following example illustrates the X format specifier.</span></span>

[!code-csharp[Formatting.Enum#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#4)]      
[!code-vb[Formatting.Enum#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#4)]

## <a name="example"></a><span data-ttu-id="06dfd-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="06dfd-124">Example</span></span>

<span data-ttu-id="06dfd-125">Následující příklad definuje výčet nazvaný `Colors` , který se skládá ze tří položek: `Red`, `Blue`, a `Green`.</span><span class="sxs-lookup"><span data-stu-id="06dfd-125">The following example defines an enumeration called `Colors` that consists of three entries: `Red`, `Blue`, and `Green`.</span></span>

[!code-csharp[Formatting.Enum#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#5)]
[!code-vb[Formatting.Enum#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#5)]

<span data-ttu-id="06dfd-126">Po definování výčtu instance mohou být deklarovány následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="06dfd-126">After the enumeration is defined, an instance can be declared in the following manner.</span></span>

[!code-csharp[Formatting.Enum#6](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#6)]
[!code-vb[Formatting.Enum#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#6)]

<span data-ttu-id="06dfd-127">`Color.ToString(System.String)` Metoda je pak možné k zobrazení hodnoty výčtu různými způsoby v závislosti na specifikátor formátu do něho předaný.</span><span class="sxs-lookup"><span data-stu-id="06dfd-127">The `Color.ToString(System.String)` method can then be used to display the enumeration value in different ways, depending on the format specifier passed to it.</span></span>

[!code-csharp[Formatting.Enum#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#7)]
[!code-vb[Formatting.Enum#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#7)]

## <a name="see-also"></a><span data-ttu-id="06dfd-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="06dfd-128">See also</span></span>

- [<span data-ttu-id="06dfd-129">Typy formátování</span><span class="sxs-lookup"><span data-stu-id="06dfd-129">Formatting Types</span></span>](formatting-types.md)