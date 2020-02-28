---
title: Řetězce formátu výčtu
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
ms.openlocfilehash: da7634758f5c4319fa18612d216682dc141318fd
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78155955"
---
# <a name="enumeration-format-strings"></a><span data-ttu-id="23d25-102">Řetězce formátu výčtu</span><span class="sxs-lookup"><span data-stu-id="23d25-102">Enumeration format strings</span></span>

<span data-ttu-id="23d25-103">Metodu <xref:System.Enum.ToString%2A?displayProperty=nameWithType> lze použít k vytvoření nového řetězcového objektu, který představuje číselnou, šestnáctkovou nebo řetězcovou hodnotu člena výčtu.</span><span class="sxs-lookup"><span data-stu-id="23d25-103">You can use the <xref:System.Enum.ToString%2A?displayProperty=nameWithType> method to create a new string object that represents the numeric, hexadecimal, or string value of an enumeration member.</span></span> <span data-ttu-id="23d25-104">Tato metoda přebírá jeden z formátovacích řetězců výčtu k určení hodnoty, kterou chcete vrátit.</span><span class="sxs-lookup"><span data-stu-id="23d25-104">This method takes one of the enumeration formatting strings to specify the value that you want returned.</span></span>

<span data-ttu-id="23d25-105">V následujících oddílech jsou uvedeny řetězce formátování výčtu a hodnoty, které vrací.</span><span class="sxs-lookup"><span data-stu-id="23d25-105">The following sections list the enumeration formatting strings and the values they return.</span></span> <span data-ttu-id="23d25-106">Tyto specifikátory formátu nerozlišují velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="23d25-106">These format specifiers are not case-sensitive.</span></span>

## <a name="g-or-g"></a><span data-ttu-id="23d25-107">G nebo g</span><span class="sxs-lookup"><span data-stu-id="23d25-107">G or g</span></span>

<span data-ttu-id="23d25-108">Zobrazuje položku výčtu jako řetězcovou hodnotu, pokud je to možné, a jinak zobrazuje celočíselnou hodnotu aktuální instance.</span><span class="sxs-lookup"><span data-stu-id="23d25-108">Displays the enumeration entry as a string value, if possible, and otherwise displays the integer value of the current instance.</span></span> <span data-ttu-id="23d25-109">Pokud je výčet definován s nastaveným atributem **Flags** , jsou řetězcové hodnoty každé platné položky zřetězeny dohromady, oddělené čárkami.</span><span class="sxs-lookup"><span data-stu-id="23d25-109">If the enumeration is defined with the **Flags** attribute set, the string values of each valid entry are concatenated together, separated by commas.</span></span> <span data-ttu-id="23d25-110">Pokud atribut **Flags** není nastaven, zobrazí se jako číselná položka neplatná hodnota.</span><span class="sxs-lookup"><span data-stu-id="23d25-110">If the **Flags** attribute is not set, an invalid value is displayed as a numeric entry.</span></span> <span data-ttu-id="23d25-111">Následující příklad znázorňuje specifikátor formátu G.</span><span class="sxs-lookup"><span data-stu-id="23d25-111">The following example illustrates the G format specifier.</span></span>

[!code-csharp[Formatting.Enum#1](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#1)]
[!code-vb[Formatting.Enum#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#1)]

## <a name="f-or-f"></a><span data-ttu-id="23d25-112">F nebo f</span><span class="sxs-lookup"><span data-stu-id="23d25-112">F or f</span></span>

<span data-ttu-id="23d25-113">Pokud je to možné, zobrazí položku výčtu jako řetězcovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="23d25-113">Displays the enumeration entry as a string value, if possible.</span></span> <span data-ttu-id="23d25-114">Pokud hodnota může být zcela zobrazená jako součet položek ve výčtu (i když atribut **Flags** není přítomný), jsou řetězcové hodnoty každé platné položky zřetězeny dohromady, oddělené čárkami.</span><span class="sxs-lookup"><span data-stu-id="23d25-114">If the value can be completely displayed as a summation of the entries in the enumeration (even if the **Flags** attribute is not present), the string values of each valid entry are concatenated together, separated by commas.</span></span> <span data-ttu-id="23d25-115">Pokud hodnota nemůže být zcela určena položkami výčtu, bude hodnota formátována jako celočíselná hodnota.</span><span class="sxs-lookup"><span data-stu-id="23d25-115">If the value cannot be completely determined by the enumeration entries, then the value is formatted as the integer value.</span></span> <span data-ttu-id="23d25-116">Následující příklad ilustruje specifikátor formátu F.</span><span class="sxs-lookup"><span data-stu-id="23d25-116">The following example illustrates the F format specifier.</span></span>

[!code-csharp[Formatting.Enum#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#2)]
[!code-vb[Formatting.Enum#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#2)]

## <a name="d-or-d"></a><span data-ttu-id="23d25-117">D nebo d</span><span class="sxs-lookup"><span data-stu-id="23d25-117">D or d</span></span>

<span data-ttu-id="23d25-118">Zobrazí položku výčtu jako celočíselnou hodnotu v nejkratší možné reprezentaci.</span><span class="sxs-lookup"><span data-stu-id="23d25-118">Displays the enumeration entry as an integer value in the shortest representation possible.</span></span> <span data-ttu-id="23d25-119">Následující příklad ilustruje specifikátor formátu D.</span><span class="sxs-lookup"><span data-stu-id="23d25-119">The following example illustrates the D format specifier.</span></span>

[!code-csharp[Formatting.Enum#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#3)]
[!code-vb[Formatting.Enum#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#3)]

## <a name="x-or-x"></a><span data-ttu-id="23d25-120">X nebo x</span><span class="sxs-lookup"><span data-stu-id="23d25-120">X or x</span></span>

<span data-ttu-id="23d25-121">Zobrazí položku výčtu jako šestnáctkovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="23d25-121">Displays the enumeration entry as a hexadecimal value.</span></span> <span data-ttu-id="23d25-122">Hodnota je vyjádřena podle potřeby počátečními nulami pro zajištění, že výsledný řetězec má dva znaky pro každý bajt v [základním číselném typu](xref:System.Enum.GetUnderlyingType%2A)typu výčtu.</span><span class="sxs-lookup"><span data-stu-id="23d25-122">The value is represented with leading zeros as necessary, to ensure that the result string has two characters for each byte in the enumeration type's [underlying numeric type](xref:System.Enum.GetUnderlyingType%2A).</span></span> <span data-ttu-id="23d25-123">Následující příklad znázorňuje specifikátor formátu X.</span><span class="sxs-lookup"><span data-stu-id="23d25-123">The following example illustrates the X format specifier.</span></span> <span data-ttu-id="23d25-124">V příkladu je podkladový typ obou <xref:System.ConsoleColor> i <xref:System.IO.FileAttributes> <xref:System.Int32>nebo celé číslo 32 (nebo 4 bajt), které vytváří výsledný řetězec 8 znaků.</span><span class="sxs-lookup"><span data-stu-id="23d25-124">In the example, the underlying type of both <xref:System.ConsoleColor> and <xref:System.IO.FileAttributes> is <xref:System.Int32>, or a 32-bit (or 4-byte) integer, which produces an 8-character result string.</span></span>

[!code-csharp[Formatting.Enum#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#4)]
[!code-vb[Formatting.Enum#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#4)]

## <a name="example"></a><span data-ttu-id="23d25-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="23d25-125">Example</span></span>

<span data-ttu-id="23d25-126">Následující příklad definuje výčet s názvem `Colors`, který se skládá ze tří položek: `Red`, `Blue`a `Green`.</span><span class="sxs-lookup"><span data-stu-id="23d25-126">The following example defines an enumeration called `Colors` that consists of three entries: `Red`, `Blue`, and `Green`.</span></span>

[!code-csharp[Formatting.Enum#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#5)]
[!code-vb[Formatting.Enum#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#5)]

<span data-ttu-id="23d25-127">Po definování výčtu může být instance deklarována následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="23d25-127">After the enumeration is defined, an instance can be declared in the following manner.</span></span>

[!code-csharp[Formatting.Enum#6](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#6)]
[!code-vb[Formatting.Enum#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#6)]

<span data-ttu-id="23d25-128">Metodu `Color.ToString(System.String)` lze následně použít k zobrazení hodnoty výčtu různými způsoby v závislosti na použitém specifikátoru formátu.</span><span class="sxs-lookup"><span data-stu-id="23d25-128">The `Color.ToString(System.String)` method can then be used to display the enumeration value in different ways, depending on the format specifier passed to it.</span></span>

[!code-csharp[Formatting.Enum#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#7)]
[!code-vb[Formatting.Enum#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#7)]

## <a name="see-also"></a><span data-ttu-id="23d25-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="23d25-129">See also</span></span>

- [<span data-ttu-id="23d25-130">Typy formátování</span><span class="sxs-lookup"><span data-stu-id="23d25-130">Formatting Types</span></span>](formatting-types.md)
