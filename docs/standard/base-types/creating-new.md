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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 477791a0d62186b6cb88d0fae3aa9b4e38b3ef35
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43870107"
---
# <a name="creating-new-strings-in-net"></a><span data-ttu-id="f991a-102">Vytváření nových řetězců v .NET</span><span class="sxs-lookup"><span data-stu-id="f991a-102">Creating New Strings in .NET</span></span>
<span data-ttu-id="f991a-103">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Umožňuje řetězců, které mají být vytvořené pomocí jednoduchého přiřazení a také přetížení konstruktoru třídy pro podporu vytváření řetězců pomocí několika různých parametrů.</span><span class="sxs-lookup"><span data-stu-id="f991a-103">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] allows strings to be created using simple assignment, and also overloads a class constructor to support string creation using a number of different parameters.</span></span> <span data-ttu-id="f991a-104">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Také poskytuje několik metod <xref:System.String?displayProperty=nameWithType> třídu, která vytvořit nový řetězec kombinací několika řetězcích, polích řetězce, objekty nebo objekty.</span><span class="sxs-lookup"><span data-stu-id="f991a-104">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] also provides several methods in the <xref:System.String?displayProperty=nameWithType> class that create new string objects by combining several strings, arrays of strings, or objects.</span></span>  
  
## <a name="creating-strings-using-assignment"></a><span data-ttu-id="f991a-105">Vytváření řetězců pomocí přiřazení</span><span class="sxs-lookup"><span data-stu-id="f991a-105">Creating Strings Using Assignment</span></span>  
 <span data-ttu-id="f991a-106">Nejjednodušší způsob, jak vytvořit novou <xref:System.String> objekt slouží k přiřazení řetězcový literál <xref:System.String> objektu.</span><span class="sxs-lookup"><span data-stu-id="f991a-106">The easiest way to create a new <xref:System.String> object is simply to assign a string literal to a <xref:System.String> object.</span></span>  
  
## <a name="creating-strings-using-a-class-constructor"></a><span data-ttu-id="f991a-107">Vytváření řetězců pomocí konstruktoru třídy</span><span class="sxs-lookup"><span data-stu-id="f991a-107">Creating Strings Using a Class Constructor</span></span>  
 <span data-ttu-id="f991a-108">Můžete použít přetížení <xref:System.String> konstruktoru třídy pro vytvoření řetězce z pole znaků.</span><span class="sxs-lookup"><span data-stu-id="f991a-108">You can use overloads of the <xref:System.String> class constructor to create strings from character arrays.</span></span> <span data-ttu-id="f991a-109">Můžete také vytvořit nový řetězec tak, že duplikujete určitý znak zadaného počtu opakování.</span><span class="sxs-lookup"><span data-stu-id="f991a-109">You can also create a new string by duplicating a particular character a specified number of times.</span></span>  
  
## <a name="methods-that-return-strings"></a><span data-ttu-id="f991a-110">Metody, které vracejí řetězce</span><span class="sxs-lookup"><span data-stu-id="f991a-110">Methods that Return Strings</span></span>  
 <span data-ttu-id="f991a-111">Následující tabulka uvádí několik užitečných metod, které vrací nové objekty.</span><span class="sxs-lookup"><span data-stu-id="f991a-111">The following table lists several useful methods that return new string objects.</span></span>  
  
|<span data-ttu-id="f991a-112">Název metody</span><span class="sxs-lookup"><span data-stu-id="f991a-112">Method name</span></span>|<span data-ttu-id="f991a-113">Použití</span><span class="sxs-lookup"><span data-stu-id="f991a-113">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|<span data-ttu-id="f991a-114">Vytvoří na základě sady vstupních objektů formátovaný řetězec.</span><span class="sxs-lookup"><span data-stu-id="f991a-114">Builds a formatted string from a set of input objects.</span></span>|  
|<xref:System.String.Concat%2A?displayProperty=nameWithType>|<span data-ttu-id="f991a-115">Vytvoří řetězce ze dvou nebo více řetězců.</span><span class="sxs-lookup"><span data-stu-id="f991a-115">Builds strings from two or more strings.</span></span>|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|<span data-ttu-id="f991a-116">Vytvoří nový řetězec kombinací pole řetězců.</span><span class="sxs-lookup"><span data-stu-id="f991a-116">Builds a new string by combining an array of strings.</span></span>|  
|<xref:System.String.Insert%2A?displayProperty=nameWithType>|<span data-ttu-id="f991a-117">Vytvoří nový řetězec vložením řetězce do určeného indexu existujícího řetězce.</span><span class="sxs-lookup"><span data-stu-id="f991a-117">Builds a new string by inserting a string into the specified index of an existing string.</span></span>|  
|<xref:System.String.CopyTo%2A?displayProperty=nameWithType>|<span data-ttu-id="f991a-118">Zkopíruje do zadané pozice v poli znaků zadané znaky v řetězci.</span><span class="sxs-lookup"><span data-stu-id="f991a-118">Copies specified characters in a string into a specified position in an array of characters.</span></span>|  
  
### <a name="format"></a><span data-ttu-id="f991a-119">Formát</span><span class="sxs-lookup"><span data-stu-id="f991a-119">Format</span></span>  
 <span data-ttu-id="f991a-120">Můžete použít **String.Format** metodu pro vytvoření formátovaných řetězců a řetězit řetězce představující více objektů.</span><span class="sxs-lookup"><span data-stu-id="f991a-120">You can use the **String.Format** method to create formatted strings and concatenate strings representing multiple objects.</span></span> <span data-ttu-id="f991a-121">Libovolný objekt předaný této metodě automaticky převede na řetězec.</span><span class="sxs-lookup"><span data-stu-id="f991a-121">This method automatically converts any passed object into a string.</span></span> <span data-ttu-id="f991a-122">Například, pokud aplikace vyžaduje zobrazení **Int32** hodnotu a **data a času** hodnotu pro uživatele, můžete snadno sestavit řetězec představující tyto hodnoty pomocí **formátu**metody.</span><span class="sxs-lookup"><span data-stu-id="f991a-122">For example, if your application must display an **Int32** value and a **DateTime** value to the user, you can easily construct a string to represent these values using the **Format** method.</span></span> <span data-ttu-id="f991a-123">Informace o formátování konvence tuto metodu použít, najdete v části na [složené formátování](../../../docs/standard/base-types/composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="f991a-123">For information about formatting conventions used with this method, see the section on [composite formatting](../../../docs/standard/base-types/composite-formatting.md).</span></span>  
  
 <span data-ttu-id="f991a-124">V následujícím příkladu **formátu** metodu pro vytvoření řetězce, který používá proměnnou celého čísla.</span><span class="sxs-lookup"><span data-stu-id="f991a-124">The following example uses the **Format** method to create a string that uses an integer variable.</span></span>  
  
 [!code-csharp[Strings.Creating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#1)]
 [!code-vb[Strings.Creating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#1)]  
  
 <span data-ttu-id="f991a-125">V tomto příkladu<xref:System.DateTime.Now%2A?displayProperty=nameWithType> zobrazuje aktuální datum a čas způsobem určené jazykové verze přidružené k aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="f991a-125">In this example,<xref:System.DateTime.Now%2A?displayProperty=nameWithType> displays the current date and time in a manner specified by the culture associated with the current thread.</span></span>  
  
### <a name="concat"></a><span data-ttu-id="f991a-126">concat</span><span class="sxs-lookup"><span data-stu-id="f991a-126">Concat</span></span>  
 <span data-ttu-id="f991a-127">**String.Concat** metodu je možné snadno vytvořit nový objekt řetězce ze dvou nebo více existujících objektů.</span><span class="sxs-lookup"><span data-stu-id="f991a-127">The **String.Concat** method can be used to easily create a new string object from two or more existing objects.</span></span> <span data-ttu-id="f991a-128">Poskytuje nezávislým na jazyku způsob, jak zřetězení řetězců.</span><span class="sxs-lookup"><span data-stu-id="f991a-128">It provides a language-independent way to concatenate strings.</span></span> <span data-ttu-id="f991a-129">Tato metoda přijímá jakoukoli třídu, která je odvozena z **System.Object**.</span><span class="sxs-lookup"><span data-stu-id="f991a-129">This method accepts any class that derives from **System.Object**.</span></span> <span data-ttu-id="f991a-130">Následující příklad vytvoří řetězec ze dvou existujících řetězcových objektů a oddělovacích znaků.</span><span class="sxs-lookup"><span data-stu-id="f991a-130">The following example creates a string from two existing string objects and a separating character.</span></span>  
  
 [!code-csharp[Strings.Creating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#2)]
 [!code-vb[Strings.Creating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#2)]  
  
### <a name="join"></a><span data-ttu-id="f991a-131">Join</span><span class="sxs-lookup"><span data-stu-id="f991a-131">Join</span></span>  
 <span data-ttu-id="f991a-132">**String.Join** metoda vytvoří nový řetězec z pole řetězců a oddělovacího řetězce.</span><span class="sxs-lookup"><span data-stu-id="f991a-132">The **String.Join** method creates a new string from an array of strings and a separator string.</span></span> <span data-ttu-id="f991a-133">Tato metoda je užitečná, pokud chcete řetězení více řetězců společně, vytvoření seznamu odděleného čárkami.</span><span class="sxs-lookup"><span data-stu-id="f991a-133">This method is useful if you want to concatenate multiple strings together, making a list perhaps separated by a comma.</span></span>  
  
 <span data-ttu-id="f991a-134">Následující příklad používá mezeru vytvořit vazbu pole řetězců.</span><span class="sxs-lookup"><span data-stu-id="f991a-134">The following example uses a space to bind a string array.</span></span>  
  
 [!code-csharp[Strings.Creating#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#3)]
 [!code-vb[Strings.Creating#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#3)]  
  
### <a name="insert"></a><span data-ttu-id="f991a-135">Insert</span><span class="sxs-lookup"><span data-stu-id="f991a-135">Insert</span></span>  
 <span data-ttu-id="f991a-136">**String.Insert** metoda vytvoří nový řetězec vložením řetězce do zadané pozice v jiném řetězci.</span><span class="sxs-lookup"><span data-stu-id="f991a-136">The **String.Insert** method creates a new string by inserting a string into a specified position in another string.</span></span> <span data-ttu-id="f991a-137">Tato metoda používá index založený na nule.</span><span class="sxs-lookup"><span data-stu-id="f991a-137">This method uses a zero-based index.</span></span> <span data-ttu-id="f991a-138">V následujícím příkladu vloží řetězec na páté index pozice `MyString` a vytvoří nový řetězec s touto hodnotou.</span><span class="sxs-lookup"><span data-stu-id="f991a-138">The following example inserts a string into the fifth index position of `MyString` and creates a new string with this value.</span></span>  
  
 [!code-csharp[Strings.Creating#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#4)]
 [!code-vb[Strings.Creating#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#4)]  
  
### <a name="copyto"></a><span data-ttu-id="f991a-139">CopyTo</span><span class="sxs-lookup"><span data-stu-id="f991a-139">CopyTo</span></span>  
 <span data-ttu-id="f991a-140">**String.CopyTo** metoda zkopíruje částí řetězce na pole znaků.</span><span class="sxs-lookup"><span data-stu-id="f991a-140">The **String.CopyTo** method copies portions of a string into an array of characters.</span></span> <span data-ttu-id="f991a-141">Můžete určit index začátku řetězce a počet znaků, které se mají zkopírovat.</span><span class="sxs-lookup"><span data-stu-id="f991a-141">You can specify both the beginning index of the string and the number of characters to be copied.</span></span> <span data-ttu-id="f991a-142">Tato metoda přebírá index zdroje, pole znaků, cílový index a počet znaků, které mají kopírovat.</span><span class="sxs-lookup"><span data-stu-id="f991a-142">This method takes the source index, an array of characters, the destination index, and the number of characters to copy.</span></span> <span data-ttu-id="f991a-143">Všechny indexy jsou počítány od nuly.</span><span class="sxs-lookup"><span data-stu-id="f991a-143">All indexes are zero-based.</span></span>  
  
 <span data-ttu-id="f991a-144">V následujícím příkladu **CopyTo** metoda kopírování znaků slova "Hello" v řetězci objektu na první pozici indexu pole znaků.</span><span class="sxs-lookup"><span data-stu-id="f991a-144">The following example uses the **CopyTo** method to copy the characters of the word "Hello" from a string object to the first index position of an array of characters.</span></span>  
  
 [!code-csharp[Strings.Creating#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#5)]
 [!code-vb[Strings.Creating#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="f991a-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f991a-145">See also</span></span>

- [<span data-ttu-id="f991a-146">Základní operace s řetězci</span><span class="sxs-lookup"><span data-stu-id="f991a-146">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)  
- [<span data-ttu-id="f991a-147">Složené formátování</span><span class="sxs-lookup"><span data-stu-id="f991a-147">Composite Formatting</span></span>](../../../docs/standard/base-types/composite-formatting.md)
