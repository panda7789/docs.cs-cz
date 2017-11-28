---
title: "Vytváření nových řetězců v .NET"
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
helpviewer_keywords:
- CopyTo method
- Join method
- Format method
- Concat method
- strings [.NET Framework], creating
- Insert method
ms.assetid: 06fdf123-2fac-4459-8904-eb48ab908a30
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d000cd88fc9ee9fd48ef25e9bb4982688564a2a0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="creating-new-strings-in-net"></a><span data-ttu-id="c06e6-102">Vytváření nových řetězců v .NET</span><span class="sxs-lookup"><span data-stu-id="c06e6-102">Creating New Strings in .NET</span></span>
<span data-ttu-id="c06e6-103">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Umožňuje vytvoření jednoduché přiřazení řetězců a také přetížení konstruktoru třídy pro podporu vytváření řetězců pomocí několika různých parametrů.</span><span class="sxs-lookup"><span data-stu-id="c06e6-103">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] allows strings to be created using simple assignment, and also overloads a class constructor to support string creation using a number of different parameters.</span></span> <span data-ttu-id="c06e6-104">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Také poskytuje několik metod <xref:System.String?displayProperty=nameWithType> třídu, která vytvořit nový řetězec sloučením několika řetězců, pole řetězců, objekty nebo objekty.</span><span class="sxs-lookup"><span data-stu-id="c06e6-104">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] also provides several methods in the <xref:System.String?displayProperty=nameWithType> class that create new string objects by combining several strings, arrays of strings, or objects.</span></span>  
  
## <a name="creating-strings-using-assignment"></a><span data-ttu-id="c06e6-105">Vytváření řetězců pomocí přiřazení</span><span class="sxs-lookup"><span data-stu-id="c06e6-105">Creating Strings Using Assignment</span></span>  
 <span data-ttu-id="c06e6-106">Nejjednodušší způsob, jak vytvořit nový <xref:System.String> objekt je jednoduše přiřadit řetězcový literál <xref:System.String> objektu.</span><span class="sxs-lookup"><span data-stu-id="c06e6-106">The easiest way to create a new <xref:System.String> object is simply to assign a string literal to a <xref:System.String> object.</span></span>  
  
## <a name="creating-strings-using-a-class-constructor"></a><span data-ttu-id="c06e6-107">Vytváření řetězců pomocí konstruktoru třídy</span><span class="sxs-lookup"><span data-stu-id="c06e6-107">Creating Strings Using a Class Constructor</span></span>  
 <span data-ttu-id="c06e6-108">Můžete použít přetížení metody <xref:System.String> třída – konstruktor k vytvoření řetězce z pole znaků.</span><span class="sxs-lookup"><span data-stu-id="c06e6-108">You can use overloads of the <xref:System.String> class constructor to create strings from character arrays.</span></span> <span data-ttu-id="c06e6-109">Nový řetězec také vytvoříte duplikování určitého znaku zadaného počtu opakování.</span><span class="sxs-lookup"><span data-stu-id="c06e6-109">You can also create a new string by duplicating a particular character a specified number of times.</span></span>  
  
## <a name="methods-that-return-strings"></a><span data-ttu-id="c06e6-110">Metody, které vracejí řetězce</span><span class="sxs-lookup"><span data-stu-id="c06e6-110">Methods that Return Strings</span></span>  
 <span data-ttu-id="c06e6-111">Následující tabulka uvádí několik užitečných metod, které vracejí nové objekty řetězec.</span><span class="sxs-lookup"><span data-stu-id="c06e6-111">The following table lists several useful methods that return new string objects.</span></span>  
  
|<span data-ttu-id="c06e6-112">Název metody</span><span class="sxs-lookup"><span data-stu-id="c06e6-112">Method name</span></span>|<span data-ttu-id="c06e6-113">Použití</span><span class="sxs-lookup"><span data-stu-id="c06e6-113">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|<span data-ttu-id="c06e6-114">Vytvoří formátovaný řetězec ze sady vstupní objektů.</span><span class="sxs-lookup"><span data-stu-id="c06e6-114">Builds a formatted string from a set of input objects.</span></span>|  
|<xref:System.String.Concat%2A?displayProperty=nameWithType>|<span data-ttu-id="c06e6-115">Vytvoří řetězce ze dvou nebo více řetězců.</span><span class="sxs-lookup"><span data-stu-id="c06e6-115">Builds strings from two or more strings.</span></span>|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|<span data-ttu-id="c06e6-116">Vytvoří nový řetězec kombinováním pole řetězců.</span><span class="sxs-lookup"><span data-stu-id="c06e6-116">Builds a new string by combining an array of strings.</span></span>|  
|<xref:System.String.Insert%2A?displayProperty=nameWithType>|<span data-ttu-id="c06e6-117">Vytvoří nový řetězec vložením řetězce zadaný index existující řetězec.</span><span class="sxs-lookup"><span data-stu-id="c06e6-117">Builds a new string by inserting a string into the specified index of an existing string.</span></span>|  
|<xref:System.String.CopyTo%2A?displayProperty=nameWithType>|<span data-ttu-id="c06e6-118">Kopíruje zadané znaky v řetězci na zadané pozici v pole znaků.</span><span class="sxs-lookup"><span data-stu-id="c06e6-118">Copies specified characters in a string into a specified position in an array of characters.</span></span>|  
  
### <a name="format"></a><span data-ttu-id="c06e6-119">Formát</span><span class="sxs-lookup"><span data-stu-id="c06e6-119">Format</span></span>  
 <span data-ttu-id="c06e6-120">Můžete použít **String.Format** metoda pro vytvoření formátované řetězce a zřetězení řetězců představující více objektů.</span><span class="sxs-lookup"><span data-stu-id="c06e6-120">You can use the **String.Format** method to create formatted strings and concatenate strings representing multiple objects.</span></span> <span data-ttu-id="c06e6-121">Tato metoda automaticky převede jakýkoli předaný objekt na řetězec.</span><span class="sxs-lookup"><span data-stu-id="c06e6-121">This method automatically converts any passed object into a string.</span></span> <span data-ttu-id="c06e6-122">Například, pokud aplikace vyžaduje zobrazení **Int32** hodnotu a **data a času** hodnotu pro uživatele, můžete snadno vytvořit řetězec představující tyto hodnoty pomocí **formátu**metoda.</span><span class="sxs-lookup"><span data-stu-id="c06e6-122">For example, if your application must display an **Int32** value and a **DateTime** value to the user, you can easily construct a string to represent these values using the **Format** method.</span></span> <span data-ttu-id="c06e6-123">Informace o konvencích formátování použitého tuto metodu, najdete v části na [složené formátování](../../../docs/standard/base-types/composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="c06e6-123">For information about formatting conventions used with this method, see the section on [composite formatting](../../../docs/standard/base-types/composite-formatting.md).</span></span>  
  
 <span data-ttu-id="c06e6-124">Následující příklad používá **formát** metodu pro vytvoření řetězec, který používá proměnnou celé číslo.</span><span class="sxs-lookup"><span data-stu-id="c06e6-124">The following example uses the **Format** method to create a string that uses an integer variable.</span></span>  
  
 [!code-csharp[Strings.Creating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#1)]
 [!code-vb[Strings.Creating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#1)]  
  
 <span data-ttu-id="c06e6-125">V tomto příkladu<xref:System.DateTime.Now%2A?displayProperty=nameWithType> zobrazuje aktuální datum a čas způsobem určeného jazykovou verzi spojenou s aktuálním vláknem.</span><span class="sxs-lookup"><span data-stu-id="c06e6-125">In this example,<xref:System.DateTime.Now%2A?displayProperty=nameWithType> displays the current date and time in a manner specified by the culture associated with the current thread.</span></span>  
  
### <a name="concat"></a><span data-ttu-id="c06e6-126">concat</span><span class="sxs-lookup"><span data-stu-id="c06e6-126">Concat</span></span>  
 <span data-ttu-id="c06e6-127">**String.Concat** metoda lze snadno vytvořit nový objekt řetězec ze dvou nebo více existujících objektů.</span><span class="sxs-lookup"><span data-stu-id="c06e6-127">The **String.Concat** method can be used to easily create a new string object from two or more existing objects.</span></span> <span data-ttu-id="c06e6-128">Poskytuje způsob nezávislé na jazyku ke zřetězení řetězců.</span><span class="sxs-lookup"><span data-stu-id="c06e6-128">It provides a language-independent way to concatenate strings.</span></span> <span data-ttu-id="c06e6-129">Tato metoda přijímá všechny třídu odvozenou od **System.Object**.</span><span class="sxs-lookup"><span data-stu-id="c06e6-129">This method accepts any class that derives from **System.Object**.</span></span> <span data-ttu-id="c06e6-130">Následující příklad vytvoří řetězec ze dvou existujících objektů řetězce a znak dělicí.</span><span class="sxs-lookup"><span data-stu-id="c06e6-130">The following example creates a string from two existing string objects and a separating character.</span></span>  
  
 [!code-csharp[Strings.Creating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#2)]
 [!code-vb[Strings.Creating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#2)]  
  
### <a name="join"></a><span data-ttu-id="c06e6-131">Join</span><span class="sxs-lookup"><span data-stu-id="c06e6-131">Join</span></span>  
 <span data-ttu-id="c06e6-132">**String.Join** metoda vytvoří nový řetězec z pole řetězce a řetězec oddělovače.</span><span class="sxs-lookup"><span data-stu-id="c06e6-132">The **String.Join** method creates a new string from an array of strings and a separator string.</span></span> <span data-ttu-id="c06e6-133">Tato metoda je užitečná, pokud chcete řetězení více řetězců společně, vytváření seznamu odděleného čárkami.</span><span class="sxs-lookup"><span data-stu-id="c06e6-133">This method is useful if you want to concatenate multiple strings together, making a list perhaps separated by a comma.</span></span>  
  
 <span data-ttu-id="c06e6-134">Následující příklad používá mezeru pro vazbu pole řetězců.</span><span class="sxs-lookup"><span data-stu-id="c06e6-134">The following example uses a space to bind a string array.</span></span>  
  
 [!code-csharp[Strings.Creating#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#3)]
 [!code-vb[Strings.Creating#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#3)]  
  
### <a name="insert"></a><span data-ttu-id="c06e6-135">Insert</span><span class="sxs-lookup"><span data-stu-id="c06e6-135">Insert</span></span>  
 <span data-ttu-id="c06e6-136">**String.Insert** metoda vytvoří nový řetězec vložením řetězec na zadané pozici v jiném řetězci.</span><span class="sxs-lookup"><span data-stu-id="c06e6-136">The **String.Insert** method creates a new string by inserting a string into a specified position in another string.</span></span> <span data-ttu-id="c06e6-137">Tato metoda používá index počítaný od nuly.</span><span class="sxs-lookup"><span data-stu-id="c06e6-137">This method uses a zero-based index.</span></span> <span data-ttu-id="c06e6-138">Následující příklad vloží řetězec na pozici indexu páté `MyString` a vytvoří nový řetězec s touto hodnotou.</span><span class="sxs-lookup"><span data-stu-id="c06e6-138">The following example inserts a string into the fifth index position of `MyString` and creates a new string with this value.</span></span>  
  
 [!code-csharp[Strings.Creating#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#4)]
 [!code-vb[Strings.Creating#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#4)]  
  
### <a name="copyto"></a><span data-ttu-id="c06e6-139">CopyTo</span><span class="sxs-lookup"><span data-stu-id="c06e6-139">CopyTo</span></span>  
 <span data-ttu-id="c06e6-140">**String.CopyTo** metoda zkopíruje části řetězce na pole znaků.</span><span class="sxs-lookup"><span data-stu-id="c06e6-140">The **String.CopyTo** method copies portions of a string into an array of characters.</span></span> <span data-ttu-id="c06e6-141">Zadaný index začátku řetězce a počet znaků, které se mají zkopírovat.</span><span class="sxs-lookup"><span data-stu-id="c06e6-141">You can specify both the beginning index of the string and the number of characters to be copied.</span></span> <span data-ttu-id="c06e6-142">Tato metoda přebírá index zdroje, pole znaků, cílový index a počet znaků pro kopírování.</span><span class="sxs-lookup"><span data-stu-id="c06e6-142">This method takes the source index, an array of characters, the destination index, and the number of characters to copy.</span></span> <span data-ttu-id="c06e6-143">Všechny indexy jsou od nuly.</span><span class="sxs-lookup"><span data-stu-id="c06e6-143">All indexes are zero-based.</span></span>  
  
 <span data-ttu-id="c06e6-144">Následující příklad používá **CopyTo** metoda kopírování znaků slova "Hello" v řetězci objektu do první pozici indexu pole znaků.</span><span class="sxs-lookup"><span data-stu-id="c06e6-144">The following example uses the **CopyTo** method to copy the characters of the word "Hello" from a string object to the first index position of an array of characters.</span></span>  
  
 [!code-csharp[Strings.Creating#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#5)]
 [!code-vb[Strings.Creating#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="c06e6-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="c06e6-145">See Also</span></span>  
 [<span data-ttu-id="c06e6-146">Základní operace s řetězci</span><span class="sxs-lookup"><span data-stu-id="c06e6-146">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)  
 [<span data-ttu-id="c06e6-147">Složené formátování</span><span class="sxs-lookup"><span data-stu-id="c06e6-147">Composite Formatting</span></span>](../../../docs/standard/base-types/composite-formatting.md)
