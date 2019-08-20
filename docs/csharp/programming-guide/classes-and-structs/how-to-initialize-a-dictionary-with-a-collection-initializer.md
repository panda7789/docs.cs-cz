---
title: Postup inicializace slovníku pomocí inicializátoru kolekce – C# Průvodce programováním
ms.custom: seodec18
ms.date: 12/20/2018
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: 22f80365b974df66999ac68f7bc2a9ffa7d445a5
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596817"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a><span data-ttu-id="72be9-102">Postup inicializace slovníku pomocí inicializátoru kolekce (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="72be9-102">How to initialize a dictionary with a collection initializer (C# Programming Guide)</span></span>

<span data-ttu-id="72be9-103"><xref:System.Collections.Generic.Dictionary%602> Obsahuje kolekci párů klíč/hodnota.</span><span class="sxs-lookup"><span data-stu-id="72be9-103">A <xref:System.Collections.Generic.Dictionary%602> contains a collection of key/value pairs.</span></span> <span data-ttu-id="72be9-104">Jeho <xref:System.Collections.Generic.Dictionary%602.Add*> metoda přijímá dva parametry, jednu pro klíč a jednu pro hodnotu.</span><span class="sxs-lookup"><span data-stu-id="72be9-104">Its <xref:System.Collections.Generic.Dictionary%602.Add*> method takes two parameters, one for the key and one for the value.</span></span> <span data-ttu-id="72be9-105">Jedním ze způsobů <xref:System.Collections.Generic.Dictionary%602>, jak inicializovat nebo jakékoli kolekce, `Add` jejichž metoda přijímá více parametrů, je uzavřít každou sadu parametrů do složených závorek, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="72be9-105">One way to initialize a <xref:System.Collections.Generic.Dictionary%602>, or any collection whose `Add` method takes multiple parameters, is to enclose each set of parameters in braces as shown in the following example.</span></span> <span data-ttu-id="72be9-106">Další možností je použít inicializátor indexu, který je také znázorněn v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="72be9-106">Another option is to use an index initializer, also shown in the following example.</span></span>

## <a name="example"></a><span data-ttu-id="72be9-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="72be9-107">Example</span></span>

<span data-ttu-id="72be9-108">V následujícím příkladu <xref:System.Collections.Generic.Dictionary%602> kódu je inicializována s instancemi typu `StudentName`.</span><span class="sxs-lookup"><span data-stu-id="72be9-108">In the following code example, a <xref:System.Collections.Generic.Dictionary%602> is initialized with instances of type `StudentName`.</span></span>  <span data-ttu-id="72be9-109">První inicializace používá `Add` metodu se dvěma argumenty.</span><span class="sxs-lookup"><span data-stu-id="72be9-109">The first initialization uses the `Add` method with two arguments.</span></span> <span data-ttu-id="72be9-110">Kompilátor vygeneruje volání `Add` pro každou `int` dvojici klíčů a `StudentName` hodnot.</span><span class="sxs-lookup"><span data-stu-id="72be9-110">The compiler generates a call to `Add` for each of the pairs of `int` keys and `StudentName` values.</span></span> <span data-ttu-id="72be9-111">Druhý používá metodu `Dictionary` Public pro čtení/zápis třídy:</span><span class="sxs-lookup"><span data-stu-id="72be9-111">The second uses a public read / write indexer method of the `Dictionary` class:</span></span>

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToDictionaryInitializer.cs#HowToDictionaryInitializer)]  

<span data-ttu-id="72be9-112">Všimněte si dvou párů složených závorek v každém elementu kolekce v první deklaraci.</span><span class="sxs-lookup"><span data-stu-id="72be9-112">Note the two pairs of braces in each element of the collection in the first declaration.</span></span> <span data-ttu-id="72be9-113">Nejvnitřnější složené závorky ohraničují inicializátor objektu pro `StudentName`a vnější složené závorky mají k dispozici inicializátor pro dvojici klíč/hodnota, která bude přidána `students` <xref:System.Collections.Generic.Dictionary%602>do.</span><span class="sxs-lookup"><span data-stu-id="72be9-113">The innermost braces enclose the object initializer for the `StudentName`, and the outermost braces enclose the initializer for the key/value pair that will be added to the `students` <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="72be9-114">Nakonec je celý inicializátor kolekce pro slovník uzavřený ve složených závorkách.</span><span class="sxs-lookup"><span data-stu-id="72be9-114">Finally, the whole collection initializer for the dictionary is enclosed in braces.</span></span> <span data-ttu-id="72be9-115">Při druhé inicializaci je levá strana přiřazení klíč a pravá strana je hodnota s použitím inicializátoru objektu pro `StudentName`.</span><span class="sxs-lookup"><span data-stu-id="72be9-115">In the second initialization, the left side of the assignment is the key and the right side is the value, using an object initializer for `StudentName`.</span></span>

## <a name="see-also"></a><span data-ttu-id="72be9-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="72be9-116">See also</span></span>

- [<span data-ttu-id="72be9-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="72be9-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="72be9-118">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="72be9-118">Object and Collection Initializers</span></span>](./object-and-collection-initializers.md)
