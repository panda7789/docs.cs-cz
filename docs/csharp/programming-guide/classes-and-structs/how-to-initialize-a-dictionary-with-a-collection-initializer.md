---
title: Způsob inicializace slovníku pomocí inicializátoru kolekce - C# Průvodce programováním pro službu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: 42deee85b3a425531ddadfa96cfaff6d342d1221
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243878"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a><span data-ttu-id="8d707-102">Způsob inicializace slovníku pomocí inicializátoru kolekce (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="8d707-102">How to initialize a dictionary with a collection initializer (C# Programming Guide)</span></span>

<span data-ttu-id="8d707-103">A <xref:System.Collections.Generic.Dictionary%602> obsahuje kolekci dvojic klíč/hodnota.</span><span class="sxs-lookup"><span data-stu-id="8d707-103">A <xref:System.Collections.Generic.Dictionary%602> contains a collection of key/value pairs.</span></span> <span data-ttu-id="8d707-104">Jeho <xref:System.Collections.Generic.Dictionary%602.Add*> metoda přebírá dva parametry, jeden pro klíč a jeden pro hodnotu.</span><span class="sxs-lookup"><span data-stu-id="8d707-104">Its <xref:System.Collections.Generic.Dictionary%602.Add*> method takes two parameters, one for the key and one for the value.</span></span> <span data-ttu-id="8d707-105">Inicializace <xref:System.Collections.Generic.Dictionary%602>, nebo jakoukoli kolekci jehož `Add` metoda přijímá několik parametrů, uzavřete do složených závorek každou sadu parametrů, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8d707-105">To initialize a <xref:System.Collections.Generic.Dictionary%602>, or any collection whose `Add` method takes multiple parameters, enclose each set of parameters in braces as shown in the following example.</span></span>

## <a name="example"></a><span data-ttu-id="8d707-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="8d707-106">Example</span></span>

<span data-ttu-id="8d707-107">V následujícím příkladu kódu <xref:System.Collections.Generic.Dictionary%602> je inicializován pomocí instance typu `StudentName`.</span><span class="sxs-lookup"><span data-stu-id="8d707-107">In the following code example, a <xref:System.Collections.Generic.Dictionary%602> is initialized with instances of type `StudentName`.</span></span>  
  
[!code-csharp[csProgGuideLINQ#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-a-dictionary-with-a-collection-initializer_1.cs)]

<span data-ttu-id="8d707-108">Všimněte si dvě dvojice složených závorek v jednotlivých prvcích objektu kolekce.</span><span class="sxs-lookup"><span data-stu-id="8d707-108">Note the two pairs of braces in each element of the collection.</span></span> <span data-ttu-id="8d707-109">Vnitřní závorky uzavřete inicializátor objektu pro `StudentName`, a uzavřete inicializátor pro dvojice klíč/hodnota, která se přidá do vnějšího složené závorky `students` <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="8d707-109">The innermost braces enclose the object initializer for the `StudentName`, and the outermost braces enclose the initializer for the key/value pair that will be added to the `students` <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="8d707-110">Nakonec celé kolekce inicializátor slovníku uzavřen ve složených závorkách.</span><span class="sxs-lookup"><span data-stu-id="8d707-110">Finally, the whole collection initializer for the dictionary is enclosed in braces.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="8d707-111">Kompilování kódu</span><span class="sxs-lookup"><span data-stu-id="8d707-111">Compiling the code</span></span>

<span data-ttu-id="8d707-112">Tento kód spustit, zkopírujte a vložte třídy v jazyce Visual C# projekt konzolové aplikace, který nebyl vytvořen v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8d707-112">To run this code, copy and paste the class into a Visual C# console application project that has been created in Visual Studio.</span></span> <span data-ttu-id="8d707-113">Ve výchozím nastavení, tento projekt zaměřen na verzi 3.5 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], a obsahuje odkaz na System.Core.dll a using pro System.Linq.</span><span class="sxs-lookup"><span data-stu-id="8d707-113">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it has a reference to System.Core.dll and a using directive for System.Linq.</span></span> <span data-ttu-id="8d707-114">Pokud z projektu chybí jeden nebo více z těchto požadavků, můžete je přidat ručně.</span><span class="sxs-lookup"><span data-stu-id="8d707-114">If one or more of these requirements are missing from the project, you can add them manually.</span></span>

## <a name="see-also"></a><span data-ttu-id="8d707-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8d707-115">See also</span></span>

- [<span data-ttu-id="8d707-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="8d707-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="8d707-117">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="8d707-117">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
