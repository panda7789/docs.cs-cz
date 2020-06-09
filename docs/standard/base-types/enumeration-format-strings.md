---
title: Vytvoření výčtu řetězců formátu
description: Vytvářejte řetězce formátu výčtu pomocí metody Enum. ToString v rozhraní .NET. Formátuje číselné, šestnáctkové a řetězcové hodnoty členů výčtu.
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
ms.openlocfilehash: 825357cf4a56132dae0870972d316eff89b0c94f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84583424"
---
# <a name="enumeration-format-strings"></a><span data-ttu-id="7c78c-104">Vytvoření výčtu řetězců formátu</span><span class="sxs-lookup"><span data-stu-id="7c78c-104">Enumeration format strings</span></span>

<span data-ttu-id="7c78c-105">Metodu lze použít <xref:System.Enum.ToString%2A?displayProperty=nameWithType> k vytvoření nového řetězcového objektu, který představuje číselnou, šestnáctkovou nebo řetězcovou hodnotu člena výčtu.</span><span class="sxs-lookup"><span data-stu-id="7c78c-105">You can use the <xref:System.Enum.ToString%2A?displayProperty=nameWithType> method to create a new string object that represents the numeric, hexadecimal, or string value of an enumeration member.</span></span> <span data-ttu-id="7c78c-106">Tato metoda přebírá jeden z formátovacích řetězců výčtu k určení hodnoty, kterou chcete vrátit.</span><span class="sxs-lookup"><span data-stu-id="7c78c-106">This method takes one of the enumeration formatting strings to specify the value that you want returned.</span></span>

<span data-ttu-id="7c78c-107">V následujících oddílech jsou uvedeny řetězce formátování výčtu a hodnoty, které vrací.</span><span class="sxs-lookup"><span data-stu-id="7c78c-107">The following sections list the enumeration formatting strings and the values they return.</span></span> <span data-ttu-id="7c78c-108">Tyto specifikátory formátu nerozlišují velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="7c78c-108">These format specifiers are not case-sensitive.</span></span>

## <a name="g-or-g"></a><span data-ttu-id="7c78c-109">G nebo g</span><span class="sxs-lookup"><span data-stu-id="7c78c-109">G or g</span></span>

<span data-ttu-id="7c78c-110">Zobrazuje položku výčtu jako řetězcovou hodnotu, pokud je to možné, a jinak zobrazuje celočíselnou hodnotu aktuální instance.</span><span class="sxs-lookup"><span data-stu-id="7c78c-110">Displays the enumeration entry as a string value, if possible, and otherwise displays the integer value of the current instance.</span></span> <span data-ttu-id="7c78c-111">Pokud je výčet definován s nastaveným atributem **Flags** , jsou řetězcové hodnoty každé platné položky zřetězeny dohromady, oddělené čárkami.</span><span class="sxs-lookup"><span data-stu-id="7c78c-111">If the enumeration is defined with the **Flags** attribute set, the string values of each valid entry are concatenated together, separated by commas.</span></span> <span data-ttu-id="7c78c-112">Pokud atribut **Flags** není nastaven, zobrazí se jako číselná položka neplatná hodnota.</span><span class="sxs-lookup"><span data-stu-id="7c78c-112">If the **Flags** attribute is not set, an invalid value is displayed as a numeric entry.</span></span> <span data-ttu-id="7c78c-113">Následující příklad znázorňuje specifikátor formátu G.</span><span class="sxs-lookup"><span data-stu-id="7c78c-113">The following example illustrates the G format specifier.</span></span>

[!code-csharp[Formatting.Enum#1](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#1)]
[!code-vb[Formatting.Enum#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#1)]

## <a name="f-or-f"></a><span data-ttu-id="7c78c-114">F nebo f</span><span class="sxs-lookup"><span data-stu-id="7c78c-114">F or f</span></span>

<span data-ttu-id="7c78c-115">Pokud je to možné, zobrazí položku výčtu jako řetězcovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7c78c-115">Displays the enumeration entry as a string value, if possible.</span></span> <span data-ttu-id="7c78c-116">Pokud hodnota může být zcela zobrazená jako součet položek ve výčtu (i když atribut **Flags** není přítomný), jsou řetězcové hodnoty každé platné položky zřetězeny dohromady, oddělené čárkami.</span><span class="sxs-lookup"><span data-stu-id="7c78c-116">If the value can be completely displayed as a summation of the entries in the enumeration (even if the **Flags** attribute is not present), the string values of each valid entry are concatenated together, separated by commas.</span></span> <span data-ttu-id="7c78c-117">Pokud hodnota nemůže být zcela určena položkami výčtu, bude hodnota formátována jako celočíselná hodnota.</span><span class="sxs-lookup"><span data-stu-id="7c78c-117">If the value cannot be completely determined by the enumeration entries, then the value is formatted as the integer value.</span></span> <span data-ttu-id="7c78c-118">Následující příklad ilustruje specifikátor formátu F.</span><span class="sxs-lookup"><span data-stu-id="7c78c-118">The following example illustrates the F format specifier.</span></span>

[!code-csharp[Formatting.Enum#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#2)]
[!code-vb[Formatting.Enum#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#2)]

## <a name="d-or-d"></a><span data-ttu-id="7c78c-119">D nebo d</span><span class="sxs-lookup"><span data-stu-id="7c78c-119">D or d</span></span>

<span data-ttu-id="7c78c-120">Zobrazí položku výčtu jako celočíselnou hodnotu v nejkratší možné reprezentaci.</span><span class="sxs-lookup"><span data-stu-id="7c78c-120">Displays the enumeration entry as an integer value in the shortest representation possible.</span></span> <span data-ttu-id="7c78c-121">Následující příklad ilustruje specifikátor formátu D.</span><span class="sxs-lookup"><span data-stu-id="7c78c-121">The following example illustrates the D format specifier.</span></span>

[!code-csharp[Formatting.Enum#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#3)]
[!code-vb[Formatting.Enum#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#3)]

## <a name="x-or-x"></a><span data-ttu-id="7c78c-122">X nebo x</span><span class="sxs-lookup"><span data-stu-id="7c78c-122">X or x</span></span>

<span data-ttu-id="7c78c-123">Zobrazí položku výčtu jako šestnáctkovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7c78c-123">Displays the enumeration entry as a hexadecimal value.</span></span> <span data-ttu-id="7c78c-124">Hodnota je vyjádřena podle potřeby počátečními nulami pro zajištění, že výsledný řetězec má dva znaky pro každý bajt v [základním číselném typu](xref:System.Enum.GetUnderlyingType%2A)typu výčtu.</span><span class="sxs-lookup"><span data-stu-id="7c78c-124">The value is represented with leading zeros as necessary, to ensure that the result string has two characters for each byte in the enumeration type's [underlying numeric type](xref:System.Enum.GetUnderlyingType%2A).</span></span> <span data-ttu-id="7c78c-125">Následující příklad znázorňuje specifikátor formátu X.</span><span class="sxs-lookup"><span data-stu-id="7c78c-125">The following example illustrates the X format specifier.</span></span> <span data-ttu-id="7c78c-126">V příkladu nadřazený typ <xref:System.ConsoleColor> a <xref:System.IO.FileAttributes> je <xref:System.Int32> , nebo 32 (nebo 4 bajt) celé číslo, které vytváří výsledný řetězec 8 znaků.</span><span class="sxs-lookup"><span data-stu-id="7c78c-126">In the example, the underlying type of both <xref:System.ConsoleColor> and <xref:System.IO.FileAttributes> is <xref:System.Int32>, or a 32-bit (or 4-byte) integer, which produces an 8-character result string.</span></span>

[!code-csharp[Formatting.Enum#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#4)]
[!code-vb[Formatting.Enum#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#4)]

## <a name="example"></a><span data-ttu-id="7c78c-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="7c78c-127">Example</span></span>

<span data-ttu-id="7c78c-128">Následující příklad definuje výčet `Colors` s názvem, který se skládá ze tří položek: `Red` , `Blue` a `Green` .</span><span class="sxs-lookup"><span data-stu-id="7c78c-128">The following example defines an enumeration called `Colors` that consists of three entries: `Red`, `Blue`, and `Green`.</span></span>

[!code-csharp[Formatting.Enum#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#5)]
[!code-vb[Formatting.Enum#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#5)]

<span data-ttu-id="7c78c-129">Po definování výčtu může být instance deklarována následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="7c78c-129">After the enumeration is defined, an instance can be declared in the following manner.</span></span>

[!code-csharp[Formatting.Enum#6](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#6)]
[!code-vb[Formatting.Enum#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#6)]

<span data-ttu-id="7c78c-130">`Color.ToString(System.String)`Metoda může být použita k zobrazení hodnoty výčtu různými způsoby v závislosti na použitém specifikátoru formátu.</span><span class="sxs-lookup"><span data-stu-id="7c78c-130">The `Color.ToString(System.String)` method can then be used to display the enumeration value in different ways, depending on the format specifier passed to it.</span></span>

[!code-csharp[Formatting.Enum#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#7)]
[!code-vb[Formatting.Enum#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#7)]

## <a name="see-also"></a><span data-ttu-id="7c78c-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="7c78c-131">See also</span></span>

- [<span data-ttu-id="7c78c-132">Typy formátování</span><span class="sxs-lookup"><span data-stu-id="7c78c-132">Formatting Types</span></span>](formatting-types.md)
