---
title: Vytváření nových řetězců v rozhraní .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CopyTo method
- Join method
- Format method
- Concat method
- strings [.NET Framework], creating
- Insert method
ms.assetid: 06fdf123-2fac-4459-8904-eb48ab908a30
ms.openlocfilehash: ef65c50111d6ba91ab70d0b9c8cb90c606f9366c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73103816"
---
# <a name="creating-new-strings-in-net"></a><span data-ttu-id="e3fdf-102">Vytváření nových řetězců v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="e3fdf-102">Creating New Strings in .NET</span></span>
<span data-ttu-id="e3fdf-103">Rozhraní .NET Framework umožňuje řetězce, které mají být vytvořeny pomocí jednoduché přiřazení a také přetížení konstruktortřídy pro podporu vytváření řetězců pomocí několika různých parametrů.</span><span class="sxs-lookup"><span data-stu-id="e3fdf-103">The .NET Framework allows strings to be created using simple assignment, and also overloads a class constructor to support string creation using a number of different parameters.</span></span> <span data-ttu-id="e3fdf-104">Rozhraní .NET Framework také poskytuje <xref:System.String?displayProperty=nameWithType> několik metod ve třídě, které vytvářejí nové objekty řetězce kombinací několika řetězců, polí řetězců nebo objektů.</span><span class="sxs-lookup"><span data-stu-id="e3fdf-104">The .NET Framework also provides several methods in the <xref:System.String?displayProperty=nameWithType> class that create new string objects by combining several strings, arrays of strings, or objects.</span></span>  
  
## <a name="creating-strings-using-assignment"></a><span data-ttu-id="e3fdf-105">Vytváření řetězců pomocí přiřazení</span><span class="sxs-lookup"><span data-stu-id="e3fdf-105">Creating Strings Using Assignment</span></span>  
 <span data-ttu-id="e3fdf-106">Nejjednodušší způsob, jak vytvořit <xref:System.String> nový objekt, je jednoduše přiřadit <xref:System.String> literál řetězce k objektu.</span><span class="sxs-lookup"><span data-stu-id="e3fdf-106">The easiest way to create a new <xref:System.String> object is simply to assign a string literal to a <xref:System.String> object.</span></span>  
  
## <a name="creating-strings-using-a-class-constructor"></a><span data-ttu-id="e3fdf-107">Vytváření řetězců pomocí konstruktoru třídy</span><span class="sxs-lookup"><span data-stu-id="e3fdf-107">Creating Strings Using a Class Constructor</span></span>  
 <span data-ttu-id="e3fdf-108">Přetížení konstruktoru <xref:System.String> třídy můžete použít k vytvoření řetězců z polí znaků.</span><span class="sxs-lookup"><span data-stu-id="e3fdf-108">You can use overloads of the <xref:System.String> class constructor to create strings from character arrays.</span></span> <span data-ttu-id="e3fdf-109">Můžete také vytvořit nový řetězec duplikováním konkrétníznak zadaný počet opakování.</span><span class="sxs-lookup"><span data-stu-id="e3fdf-109">You can also create a new string by duplicating a particular character a specified number of times.</span></span>  
  
## <a name="methods-that-return-strings"></a><span data-ttu-id="e3fdf-110">Metody, které vracejí řetězce</span><span class="sxs-lookup"><span data-stu-id="e3fdf-110">Methods that Return Strings</span></span>  
 <span data-ttu-id="e3fdf-111">V následující tabulce je uvedeno několik užitečných metod, které vracejí nové objekty řetězce.</span><span class="sxs-lookup"><span data-stu-id="e3fdf-111">The following table lists several useful methods that return new string objects.</span></span>  
  
|<span data-ttu-id="e3fdf-112">Název metody</span><span class="sxs-lookup"><span data-stu-id="e3fdf-112">Method name</span></span>|<span data-ttu-id="e3fdf-113">Použití</span><span class="sxs-lookup"><span data-stu-id="e3fdf-113">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|<span data-ttu-id="e3fdf-114">Vytvoří formátovaný řetězec ze sady vstupních objektů.</span><span class="sxs-lookup"><span data-stu-id="e3fdf-114">Builds a formatted string from a set of input objects.</span></span>|  
|<xref:System.String.Concat%2A?displayProperty=nameWithType>|<span data-ttu-id="e3fdf-115">Vytvoří řetězce ze dvou nebo více řetězců.</span><span class="sxs-lookup"><span data-stu-id="e3fdf-115">Builds strings from two or more strings.</span></span>|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|<span data-ttu-id="e3fdf-116">Vytvoří nový řetězec kombinací pole řetězců.</span><span class="sxs-lookup"><span data-stu-id="e3fdf-116">Builds a new string by combining an array of strings.</span></span>|  
|<xref:System.String.Insert%2A?displayProperty=nameWithType>|<span data-ttu-id="e3fdf-117">Vytvoří nový řetězec vložením řetězce do zadaného indexu existujícího řetězce.</span><span class="sxs-lookup"><span data-stu-id="e3fdf-117">Builds a new string by inserting a string into the specified index of an existing string.</span></span>|  
|<xref:System.String.CopyTo%2A?displayProperty=nameWithType>|<span data-ttu-id="e3fdf-118">Zkopíruje zadané znaky v řetězci do zadané pozice v poli znaků.</span><span class="sxs-lookup"><span data-stu-id="e3fdf-118">Copies specified characters in a string into a specified position in an array of characters.</span></span>|  
  
### <a name="format"></a><span data-ttu-id="e3fdf-119">Formát</span><span class="sxs-lookup"><span data-stu-id="e3fdf-119">Format</span></span>  
 <span data-ttu-id="e3fdf-120">Metodu **String.Format** můžete použít k vytvoření formátovaných řetězců a zřetězení řetězců představujících více objektů.</span><span class="sxs-lookup"><span data-stu-id="e3fdf-120">You can use the **String.Format** method to create formatted strings and concatenate strings representing multiple objects.</span></span> <span data-ttu-id="e3fdf-121">Tato metoda automaticky převede všechny předané objekt na řetězec.</span><span class="sxs-lookup"><span data-stu-id="e3fdf-121">This method automatically converts any passed object into a string.</span></span> <span data-ttu-id="e3fdf-122">Například pokud aplikace musí zobrazit hodnotu **Int32** a **DateTime** hodnotu pro uživatele, můžete snadno vytvořit řetězec reprezentovat tyto hodnoty pomocí **Format** metoda.</span><span class="sxs-lookup"><span data-stu-id="e3fdf-122">For example, if your application must display an **Int32** value and a **DateTime** value to the user, you can easily construct a string to represent these values using the **Format** method.</span></span> <span data-ttu-id="e3fdf-123">Informace o konvencích formátování použitých touto metodou naleznete v části [o složeném formátování](../../../docs/standard/base-types/composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="e3fdf-123">For information about formatting conventions used with this method, see the section on [composite formatting](../../../docs/standard/base-types/composite-formatting.md).</span></span>  
  
 <span data-ttu-id="e3fdf-124">Následující příklad používá metodu **Format** k vytvoření řetězce, který používá celou proměnnou.</span><span class="sxs-lookup"><span data-stu-id="e3fdf-124">The following example uses the **Format** method to create a string that uses an integer variable.</span></span>  
  
 [!code-csharp[Strings.Creating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#1)]
 [!code-vb[Strings.Creating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#1)]  
  
 <span data-ttu-id="e3fdf-125">V tomto<xref:System.DateTime.Now%2A?displayProperty=nameWithType> příkladu zobrazí aktuální datum a čas způsobem určeným jazykovou verzí přidruženou k aktuálnímu vláknu.</span><span class="sxs-lookup"><span data-stu-id="e3fdf-125">In this example,<xref:System.DateTime.Now%2A?displayProperty=nameWithType> displays the current date and time in a manner specified by the culture associated with the current thread.</span></span>  
  
### <a name="concat"></a><span data-ttu-id="e3fdf-126">Concat</span><span class="sxs-lookup"><span data-stu-id="e3fdf-126">Concat</span></span>  
 <span data-ttu-id="e3fdf-127">**String.Concat** metoda lze snadno vytvořit nový objekt řetězce ze dvou nebo více existujících objektů.</span><span class="sxs-lookup"><span data-stu-id="e3fdf-127">The **String.Concat** method can be used to easily create a new string object from two or more existing objects.</span></span> <span data-ttu-id="e3fdf-128">Poskytuje jazykově nezávislý způsob, jak zřetězit řetězce.</span><span class="sxs-lookup"><span data-stu-id="e3fdf-128">It provides a language-independent way to concatenate strings.</span></span> <span data-ttu-id="e3fdf-129">Tato metoda přijímá všechny třídy, která je odvozena z **System.Object**.</span><span class="sxs-lookup"><span data-stu-id="e3fdf-129">This method accepts any class that derives from **System.Object**.</span></span> <span data-ttu-id="e3fdf-130">Následující příklad vytvoří řetězec ze dvou existujících objektů řetězce a oddělující znak.</span><span class="sxs-lookup"><span data-stu-id="e3fdf-130">The following example creates a string from two existing string objects and a separating character.</span></span>  
  
 [!code-csharp[Strings.Creating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#2)]
 [!code-vb[Strings.Creating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#2)]  
  
### <a name="join"></a><span data-ttu-id="e3fdf-131">Spojit</span><span class="sxs-lookup"><span data-stu-id="e3fdf-131">Join</span></span>  
 <span data-ttu-id="e3fdf-132">Metoda **String.Join** vytvoří nový řetězec z pole řetězců a oddělovacířetězec.</span><span class="sxs-lookup"><span data-stu-id="e3fdf-132">The **String.Join** method creates a new string from an array of strings and a separator string.</span></span> <span data-ttu-id="e3fdf-133">Tato metoda je užitečná, pokud chcete zřetězit více řetězců dohromady, takže seznam možná odděleny čárkou.</span><span class="sxs-lookup"><span data-stu-id="e3fdf-133">This method is useful if you want to concatenate multiple strings together, making a list perhaps separated by a comma.</span></span>  
  
 <span data-ttu-id="e3fdf-134">Následující příklad používá mezeru k vytvoření svázání pole řetězců.</span><span class="sxs-lookup"><span data-stu-id="e3fdf-134">The following example uses a space to bind a string array.</span></span>  
  
 [!code-csharp[Strings.Creating#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#3)]
 [!code-vb[Strings.Creating#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#3)]  
  
### <a name="insert"></a><span data-ttu-id="e3fdf-135">Vložit</span><span class="sxs-lookup"><span data-stu-id="e3fdf-135">Insert</span></span>  
 <span data-ttu-id="e3fdf-136">Metoda **String.Insert** vytvoří nový řetězec vložením řetězce do zadané pozice v jiném řetězci.</span><span class="sxs-lookup"><span data-stu-id="e3fdf-136">The **String.Insert** method creates a new string by inserting a string into a specified position in another string.</span></span> <span data-ttu-id="e3fdf-137">Tato metoda používá index založený na nule.</span><span class="sxs-lookup"><span data-stu-id="e3fdf-137">This method uses a zero-based index.</span></span> <span data-ttu-id="e3fdf-138">Následující příklad vloží řetězec do páté pozice `MyString` indexu a vytvoří nový řetězec s touto hodnotou.</span><span class="sxs-lookup"><span data-stu-id="e3fdf-138">The following example inserts a string into the fifth index position of `MyString` and creates a new string with this value.</span></span>  
  
 [!code-csharp[Strings.Creating#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#4)]
 [!code-vb[Strings.Creating#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#4)]  
  
### <a name="copyto"></a><span data-ttu-id="e3fdf-139">Copyto</span><span class="sxs-lookup"><span data-stu-id="e3fdf-139">CopyTo</span></span>  
 <span data-ttu-id="e3fdf-140">Metoda **String.CopyTo** zkopíruje části řetězce do pole znaků.</span><span class="sxs-lookup"><span data-stu-id="e3fdf-140">The **String.CopyTo** method copies portions of a string into an array of characters.</span></span> <span data-ttu-id="e3fdf-141">Můžete zadat počáteční index řetězce i počet znaků, které mají být zkopírovány.</span><span class="sxs-lookup"><span data-stu-id="e3fdf-141">You can specify both the beginning index of the string and the number of characters to be copied.</span></span> <span data-ttu-id="e3fdf-142">Tato metoda přebírá zdrojový index, pole znaků, cílový index a počet znaků ke kopírování.</span><span class="sxs-lookup"><span data-stu-id="e3fdf-142">This method takes the source index, an array of characters, the destination index, and the number of characters to copy.</span></span> <span data-ttu-id="e3fdf-143">Všechny indexy jsou založeny na nule.</span><span class="sxs-lookup"><span data-stu-id="e3fdf-143">All indexes are zero-based.</span></span>  
  
 <span data-ttu-id="e3fdf-144">Následující příklad používá **CopyTo** metoda kopírovat znaky slova "Hello" z objektu řetězce do první pozice indexu pole znaků.</span><span class="sxs-lookup"><span data-stu-id="e3fdf-144">The following example uses the **CopyTo** method to copy the characters of the word "Hello" from a string object to the first index position of an array of characters.</span></span>  
  
 [!code-csharp[Strings.Creating#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#5)]
 [!code-vb[Strings.Creating#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="e3fdf-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="e3fdf-145">See also</span></span>

- [<span data-ttu-id="e3fdf-146">Základní operace s řetězci</span><span class="sxs-lookup"><span data-stu-id="e3fdf-146">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
- [<span data-ttu-id="e3fdf-147">Složené formátování</span><span class="sxs-lookup"><span data-stu-id="e3fdf-147">Composite Formatting</span></span>](../../../docs/standard/base-types/composite-formatting.md)
