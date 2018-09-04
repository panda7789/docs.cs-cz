---
title: 'Postupy: Inicializace slovníku pomocí inicializátoru kolekce (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: 566acd21fb17247e7f5e42eb0eaa41b0beda6672
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43520617"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a><span data-ttu-id="bbfa4-102">Postupy: Inicializace slovníku pomocí inicializátoru kolekce (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="bbfa4-102">How to: Initialize a Dictionary with a Collection Initializer (C# Programming Guide)</span></span>
<span data-ttu-id="bbfa4-103">A <xref:System.Collections.Generic.Dictionary`2> obsahuje kolekci dvojic klíč/hodnota.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-103">A <xref:System.Collections.Generic.Dictionary`2> contains a collection of key/value pairs.</span></span> <span data-ttu-id="bbfa4-104">Jeho <xref:System.Collections.Generic.Dictionary`2.Add*> metoda přebírá dva parametry, jeden pro klíč a jeden pro hodnotu.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-104">Its <xref:System.Collections.Generic.Dictionary`2.Add*> method takes two parameters, one for the key and one for the value.</span></span> <span data-ttu-id="bbfa4-105">Inicializace <xref:System.Collections.Generic.Dictionary`2>, nebo jakoukoli kolekci jehož `Add` metoda přijímá několik parametrů, uzavřete do složených závorek každou sadu parametrů, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-105">To initialize a <xref:System.Collections.Generic.Dictionary`2>, or any collection whose `Add` method takes multiple parameters, enclose each set of parameters in braces as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbfa4-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="bbfa4-106">Example</span></span>  
 <span data-ttu-id="bbfa4-107">V následujícím příkladu kódu <xref:System.Collections.Generic.Dictionary`2> je inicializován pomocí instance typu `StudentName`.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-107">In the following code example, a <xref:System.Collections.Generic.Dictionary`2> is initialized with instances of type `StudentName`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-a-dictionary-with-a-collection-initializer_1.cs)]  
  
 <span data-ttu-id="bbfa4-108">Všimněte si dvě dvojice složených závorek v jednotlivých prvcích objektu kolekce.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-108">Note the two pairs of braces in each element of the collection.</span></span> <span data-ttu-id="bbfa4-109">Vnitřní závorky uzavřete inicializátor objektu pro `StudentName`, a uzavřete inicializátor pro dvojice klíč/hodnota, která se přidá do vnějšího složené závorky `students` <xref:System.Collections.Generic.Dictionary`2>.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-109">The innermost braces enclose the object initializer for the `StudentName`, and the outermost braces enclose the initializer for the key/value pair that will be added to the `students`<xref:System.Collections.Generic.Dictionary`2>.</span></span> <span data-ttu-id="bbfa4-110">Nakonec celé kolekce inicializátor slovníku uzavřen ve složených závorkách.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-110">Finally, the whole collection initializer for the dictionary is enclosed in braces.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bbfa4-111">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="bbfa4-111">Compiling the Code</span></span>  
 <span data-ttu-id="bbfa4-112">Tento kód spustit, zkopírujte a vložte třídy v jazyce Visual C# projekt konzolové aplikace, který nebyl vytvořen v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-112">To run this code, copy and paste the class into a Visual C# console application project that has been created in Visual Studio.</span></span> <span data-ttu-id="bbfa4-113">Ve výchozím nastavení, tento projekt zaměřen na verzi 3.5 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], a obsahuje odkaz na System.Core.dll a using pro System.Linq.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-113">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it has a reference to System.Core.dll and a using directive for System.Linq.</span></span> <span data-ttu-id="bbfa4-114">Pokud z projektu chybí jeden nebo více z těchto požadavků, můžete je přidat ručně.</span><span class="sxs-lookup"><span data-stu-id="bbfa4-114">If one or more of these requirements are missing from the project, you can add them manually.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbfa4-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="bbfa4-115">See Also</span></span>

- [<span data-ttu-id="bbfa4-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="bbfa4-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="bbfa4-117">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="bbfa4-117">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
