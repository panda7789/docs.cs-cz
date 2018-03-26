---
title: 'Postupy: Inicializace slovníku pomocí inicializátoru kolekce (Průvodce programováním v C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
caps.latest.revision: ''
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8b8de5fb85a839d52ad00ad552ef823d9817e9b7
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2018
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a><span data-ttu-id="6000d-102">Postupy: Inicializace slovníku pomocí inicializátoru kolekce (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="6000d-102">How to: Initialize a Dictionary with a Collection Initializer (C# Programming Guide)</span></span>
<span data-ttu-id="6000d-103">A <xref:System.Collections.Generic.Dictionary`2> obsahuje kolekci dvojic klíč/hodnota.</span><span class="sxs-lookup"><span data-stu-id="6000d-103">A <xref:System.Collections.Generic.Dictionary`2> contains a collection of key/value pairs.</span></span> <span data-ttu-id="6000d-104">Jeho <xref:System.Collections.Generic.Dictionary`2.Add*> metoda přebírá dva parametry: jeden pro klíč a jeden pro hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6000d-104">Its <xref:System.Collections.Generic.Dictionary`2.Add*> method takes two parameters, one for the key and one for the value.</span></span> <span data-ttu-id="6000d-105">K chybě při inicializaci <xref:System.Collections.Generic.Dictionary`2>, nebo jakoukoli kolekci, jejichž `Add` metoda přijímá několik parametrů, uzavřete každou sadu parametrů do složených závorek, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="6000d-105">To initialize a <xref:System.Collections.Generic.Dictionary`2>, or any collection whose `Add` method takes multiple parameters, enclose each set of parameters in braces as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6000d-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="6000d-106">Example</span></span>  
 <span data-ttu-id="6000d-107">V následujícím příkladu kódu <xref:System.Collections.Generic.Dictionary`2> je inicializovat pomocí instance typu `StudentName`.</span><span class="sxs-lookup"><span data-stu-id="6000d-107">In the following code example, a <xref:System.Collections.Generic.Dictionary`2> is initialized with instances of type `StudentName`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-a-dictionary-with-a-collection-initializer_1.cs)]  
  
 <span data-ttu-id="6000d-108">Všimněte si dvě dvojice složených závorek v každý prvek kolekce.</span><span class="sxs-lookup"><span data-stu-id="6000d-108">Note the two pairs of braces in each element of the collection.</span></span> <span data-ttu-id="6000d-109">Nejvnitřnější složené závorky uzavřete inicializátoru objektu pro `StudentName`, a nejkrajnější složené závorky uzavřete inicializátoru pro dvojice klíč/hodnota, který bude přidán do `students` <xref:System.Collections.Generic.Dictionary`2>.</span><span class="sxs-lookup"><span data-stu-id="6000d-109">The innermost braces enclose the object initializer for the `StudentName`, and the outermost braces enclose the initializer for the key/value pair that will be added to the `students`<xref:System.Collections.Generic.Dictionary`2>.</span></span> <span data-ttu-id="6000d-110">Nakonec inicializátoru celou kolekci pro slovník je uzavřené do složených závorek.</span><span class="sxs-lookup"><span data-stu-id="6000d-110">Finally, the whole collection initializer for the dictionary is enclosed in braces.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6000d-111">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="6000d-111">Compiling the Code</span></span>  
 <span data-ttu-id="6000d-112">Pokud chcete spustit tento kód, zkopírujte a vložte třídy do Visual C# projektu konzolové aplikace vytvořené v [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6000d-112">To run this code, copy and paste the class into a Visual C# console application project that has been created in [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)].</span></span> <span data-ttu-id="6000d-113">Ve výchozím nastavení, tento projekt zaměřen na verzi 3.5 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], a obsahuje odkaz na System.Core.dll a pomocí direktivy pro System.Linq.</span><span class="sxs-lookup"><span data-stu-id="6000d-113">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it has a reference to System.Core.dll and a using directive for System.Linq.</span></span> <span data-ttu-id="6000d-114">Pokud z projektu chybí jeden nebo více z těchto požadavků, můžete je přidat ručně.</span><span class="sxs-lookup"><span data-stu-id="6000d-114">If one or more of these requirements are missing from the project, you can add them manually.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6000d-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="6000d-115">See Also</span></span>  
 [<span data-ttu-id="6000d-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="6000d-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6000d-117">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="6000d-117">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
