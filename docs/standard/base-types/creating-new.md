---
title: Vytváření nových řetězců v .NET
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
ms.openlocfilehash: a5dfe6429ac135202874f0524a252a7af900bd8d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279009"
---
# <a name="creating-new-strings-in-net"></a><span data-ttu-id="b5d54-102">Vytváření nových řetězců v .NET</span><span class="sxs-lookup"><span data-stu-id="b5d54-102">Creating New Strings in .NET</span></span>
<span data-ttu-id="b5d54-103">.NET Framework umožňuje vytvoření řetězců pomocí jednoduchého přiřazení a také přetížení konstruktoru třídy pro podporu vytváření řetězců pomocí několika různých parametrů.</span><span class="sxs-lookup"><span data-stu-id="b5d54-103">The .NET Framework allows strings to be created using simple assignment, and also overloads a class constructor to support string creation using a number of different parameters.</span></span> <span data-ttu-id="b5d54-104">.NET Framework také poskytuje několik metod ve <xref:System.String?displayProperty=nameWithType> třídě, které vytvářejí nové řetězcové objekty kombinací několika řetězců, polí řetězců nebo objektů.</span><span class="sxs-lookup"><span data-stu-id="b5d54-104">The .NET Framework also provides several methods in the <xref:System.String?displayProperty=nameWithType> class that create new string objects by combining several strings, arrays of strings, or objects.</span></span>  
  
## <a name="creating-strings-using-assignment"></a><span data-ttu-id="b5d54-105">Vytváření řetězců pomocí přiřazení</span><span class="sxs-lookup"><span data-stu-id="b5d54-105">Creating Strings Using Assignment</span></span>  
 <span data-ttu-id="b5d54-106">Nejjednodušší způsob, jak vytvořit nový <xref:System.String> objekt, je jednoduše přiřadit řetězcový literál <xref:System.String> objektu.</span><span class="sxs-lookup"><span data-stu-id="b5d54-106">The easiest way to create a new <xref:System.String> object is simply to assign a string literal to a <xref:System.String> object.</span></span>  
  
## <a name="creating-strings-using-a-class-constructor"></a><span data-ttu-id="b5d54-107">Vytváření řetězců pomocí konstruktoru třídy</span><span class="sxs-lookup"><span data-stu-id="b5d54-107">Creating Strings Using a Class Constructor</span></span>  
 <span data-ttu-id="b5d54-108">Pomocí přetížení <xref:System.String> konstruktoru třídy lze vytvořit řetězce z polí znaků.</span><span class="sxs-lookup"><span data-stu-id="b5d54-108">You can use overloads of the <xref:System.String> class constructor to create strings from character arrays.</span></span> <span data-ttu-id="b5d54-109">Můžete také vytvořit nový řetězec duplikováním určitého znaku a zadáním počtu opakování.</span><span class="sxs-lookup"><span data-stu-id="b5d54-109">You can also create a new string by duplicating a particular character a specified number of times.</span></span>  
  
## <a name="methods-that-return-strings"></a><span data-ttu-id="b5d54-110">Metody, které vracejí řetězce</span><span class="sxs-lookup"><span data-stu-id="b5d54-110">Methods that Return Strings</span></span>  
 <span data-ttu-id="b5d54-111">Následující tabulka uvádí několik užitečných metod, které vracejí nové řetězcové objekty.</span><span class="sxs-lookup"><span data-stu-id="b5d54-111">The following table lists several useful methods that return new string objects.</span></span>  
  
|<span data-ttu-id="b5d54-112">Název metody</span><span class="sxs-lookup"><span data-stu-id="b5d54-112">Method name</span></span>|<span data-ttu-id="b5d54-113">Použití</span><span class="sxs-lookup"><span data-stu-id="b5d54-113">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|<span data-ttu-id="b5d54-114">Vytvoří formátovaný řetězec ze sady vstupních objektů.</span><span class="sxs-lookup"><span data-stu-id="b5d54-114">Builds a formatted string from a set of input objects.</span></span>|  
|<xref:System.String.Concat%2A?displayProperty=nameWithType>|<span data-ttu-id="b5d54-115">Vytvoří řetězce ze dvou nebo více řetězců.</span><span class="sxs-lookup"><span data-stu-id="b5d54-115">Builds strings from two or more strings.</span></span>|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|<span data-ttu-id="b5d54-116">Vytvoří nový řetězec kombinováním pole řetězců.</span><span class="sxs-lookup"><span data-stu-id="b5d54-116">Builds a new string by combining an array of strings.</span></span>|  
|<xref:System.String.Insert%2A?displayProperty=nameWithType>|<span data-ttu-id="b5d54-117">Vytvoří nový řetězec vložením řetězce do zadaného indexu stávajícího řetězce.</span><span class="sxs-lookup"><span data-stu-id="b5d54-117">Builds a new string by inserting a string into the specified index of an existing string.</span></span>|  
|<xref:System.String.CopyTo%2A?displayProperty=nameWithType>|<span data-ttu-id="b5d54-118">Zkopíruje zadané znaky v řetězci do zadané pozice v poli znaků.</span><span class="sxs-lookup"><span data-stu-id="b5d54-118">Copies specified characters in a string into a specified position in an array of characters.</span></span>|  
  
### <a name="format"></a><span data-ttu-id="b5d54-119">Formát</span><span class="sxs-lookup"><span data-stu-id="b5d54-119">Format</span></span>  
 <span data-ttu-id="b5d54-120">Můžete použít metodu **String. Format** pro vytváření formátovaných řetězců a zřetězení řetězců představujících více objektů.</span><span class="sxs-lookup"><span data-stu-id="b5d54-120">You can use the **String.Format** method to create formatted strings and concatenate strings representing multiple objects.</span></span> <span data-ttu-id="b5d54-121">Tato metoda automaticky převede všechny předané objekty do řetězce.</span><span class="sxs-lookup"><span data-stu-id="b5d54-121">This method automatically converts any passed object into a string.</span></span> <span data-ttu-id="b5d54-122">Například pokud vaše aplikace musí zobrazit hodnotu **Int32** a hodnotu **DateTime** uživateli, můžete snadno vytvořit řetězec, který bude reprezentovat tyto hodnoty pomocí metody **Format** .</span><span class="sxs-lookup"><span data-stu-id="b5d54-122">For example, if your application must display an **Int32** value and a **DateTime** value to the user, you can easily construct a string to represent these values using the **Format** method.</span></span> <span data-ttu-id="b5d54-123">Informace o konvencích formátování použitých s touto metodou najdete v části [složeného formátování](composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="b5d54-123">For information about formatting conventions used with this method, see the section on [composite formatting](composite-formatting.md).</span></span>  
  
 <span data-ttu-id="b5d54-124">Následující příklad používá metodu **Format** k vytvoření řetězce, který používá proměnnou typu Integer.</span><span class="sxs-lookup"><span data-stu-id="b5d54-124">The following example uses the **Format** method to create a string that uses an integer variable.</span></span>  
  
 [!code-csharp[Strings.Creating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#1)]
 [!code-vb[Strings.Creating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#1)]  
  
 <span data-ttu-id="b5d54-125">V tomto příkladu <xref:System.DateTime.Now%2A?displayProperty=nameWithType> zobrazuje aktuální datum a čas způsobem určeným jazykovou verzí přidruženou k aktuálnímu vláknu.</span><span class="sxs-lookup"><span data-stu-id="b5d54-125">In this example,<xref:System.DateTime.Now%2A?displayProperty=nameWithType> displays the current date and time in a manner specified by the culture associated with the current thread.</span></span>  
  
### <a name="concat"></a><span data-ttu-id="b5d54-126">Concat</span><span class="sxs-lookup"><span data-stu-id="b5d54-126">Concat</span></span>  
 <span data-ttu-id="b5d54-127">Metodu **String. Concat** lze použít k snadnému vytvoření nového objektu řetězce ze dvou nebo více existujících objektů.</span><span class="sxs-lookup"><span data-stu-id="b5d54-127">The **String.Concat** method can be used to easily create a new string object from two or more existing objects.</span></span> <span data-ttu-id="b5d54-128">Poskytuje jazykově nezávislé způsob zřetězení řetězců.</span><span class="sxs-lookup"><span data-stu-id="b5d54-128">It provides a language-independent way to concatenate strings.</span></span> <span data-ttu-id="b5d54-129">Tato metoda přijímá všechny třídy, které jsou odvozeny z typu **System. Object**.</span><span class="sxs-lookup"><span data-stu-id="b5d54-129">This method accepts any class that derives from **System.Object**.</span></span> <span data-ttu-id="b5d54-130">Následující příklad vytvoří řetězec ze dvou existujících řetězcových objektů a oddělujícího znaku.</span><span class="sxs-lookup"><span data-stu-id="b5d54-130">The following example creates a string from two existing string objects and a separating character.</span></span>  
  
 [!code-csharp[Strings.Creating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#2)]
 [!code-vb[Strings.Creating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#2)]  
  
### <a name="join"></a><span data-ttu-id="b5d54-131">Spojit</span><span class="sxs-lookup"><span data-stu-id="b5d54-131">Join</span></span>  
 <span data-ttu-id="b5d54-132">Metoda **String. Join** vytvoří nový řetězec z pole řetězců a oddělovačového řetězce.</span><span class="sxs-lookup"><span data-stu-id="b5d54-132">The **String.Join** method creates a new string from an array of strings and a separator string.</span></span> <span data-ttu-id="b5d54-133">Tato metoda je užitečná, pokud chcete zřetězit více řetězců dohromady, takže seznam je pravděpodobně oddělen čárkou.</span><span class="sxs-lookup"><span data-stu-id="b5d54-133">This method is useful if you want to concatenate multiple strings together, making a list perhaps separated by a comma.</span></span>  
  
 <span data-ttu-id="b5d54-134">Následující příklad používá prostor pro svázání pole řetězců.</span><span class="sxs-lookup"><span data-stu-id="b5d54-134">The following example uses a space to bind a string array.</span></span>  
  
 [!code-csharp[Strings.Creating#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#3)]
 [!code-vb[Strings.Creating#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#3)]  
  
### <a name="insert"></a><span data-ttu-id="b5d54-135">Vložit</span><span class="sxs-lookup"><span data-stu-id="b5d54-135">Insert</span></span>  
 <span data-ttu-id="b5d54-136">Metoda **String. Insert** vytvoří nový řetězec vložením řetězce do zadané pozice v jiném řetězci.</span><span class="sxs-lookup"><span data-stu-id="b5d54-136">The **String.Insert** method creates a new string by inserting a string into a specified position in another string.</span></span> <span data-ttu-id="b5d54-137">Tato metoda používá index založený na nule.</span><span class="sxs-lookup"><span data-stu-id="b5d54-137">This method uses a zero-based index.</span></span> <span data-ttu-id="b5d54-138">Následující příklad vloží řetězec do páté pozice indexu v `MyString` a vytvoří nový řetězec s touto hodnotou.</span><span class="sxs-lookup"><span data-stu-id="b5d54-138">The following example inserts a string into the fifth index position of `MyString` and creates a new string with this value.</span></span>  
  
 [!code-csharp[Strings.Creating#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#4)]
 [!code-vb[Strings.Creating#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#4)]  
  
### <a name="copyto"></a><span data-ttu-id="b5d54-139">Kopírovat</span><span class="sxs-lookup"><span data-stu-id="b5d54-139">CopyTo</span></span>  
 <span data-ttu-id="b5d54-140">Metoda **String. CopyTo** kopíruje části řetězce do pole znaků.</span><span class="sxs-lookup"><span data-stu-id="b5d54-140">The **String.CopyTo** method copies portions of a string into an array of characters.</span></span> <span data-ttu-id="b5d54-141">Můžete zadat jak počáteční index řetězce, tak počet znaků, které mají být zkopírovány.</span><span class="sxs-lookup"><span data-stu-id="b5d54-141">You can specify both the beginning index of the string and the number of characters to be copied.</span></span> <span data-ttu-id="b5d54-142">Tato metoda získá zdrojový index, pole znaků, cílový index a počet znaků, které mají být zkopírovány.</span><span class="sxs-lookup"><span data-stu-id="b5d54-142">This method takes the source index, an array of characters, the destination index, and the number of characters to copy.</span></span> <span data-ttu-id="b5d54-143">Všechny indexy jsou počítány od nuly.</span><span class="sxs-lookup"><span data-stu-id="b5d54-143">All indexes are zero-based.</span></span>  
  
 <span data-ttu-id="b5d54-144">Následující příklad používá metodu **CopyTo** ke zkopírování znaků slova "Hello" z objektu řetězce na první pozici indexu pole znaků.</span><span class="sxs-lookup"><span data-stu-id="b5d54-144">The following example uses the **CopyTo** method to copy the characters of the word "Hello" from a string object to the first index position of an array of characters.</span></span>  
  
 [!code-csharp[Strings.Creating#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#5)]
 [!code-vb[Strings.Creating#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="b5d54-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="b5d54-145">See also</span></span>

- [<span data-ttu-id="b5d54-146">Základní operace s řetězci</span><span class="sxs-lookup"><span data-stu-id="b5d54-146">Basic String Operations</span></span>](basic-string-operations.md)
- [<span data-ttu-id="b5d54-147">Složené formátování</span><span class="sxs-lookup"><span data-stu-id="b5d54-147">Composite Formatting</span></span>](composite-formatting.md)
