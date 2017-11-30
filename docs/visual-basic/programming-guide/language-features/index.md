---
title: Funkce jazyka Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, elements of
- Visual Basic code
ms.assetid: b0b21730-298c-47e6-9a2f-cc81f628067b
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f7074206baa51259592cca3fdc224d99438791f9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="visual-basic-language-features"></a><span data-ttu-id="4b7b7-102">Funkce jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4b7b7-102">Visual Basic Language Features</span></span>
<span data-ttu-id="4b7b7-103">Následující témata zavádět a popisují nezbytné součásti [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], objektově orientovaný programovací jazyk.</span><span class="sxs-lookup"><span data-stu-id="4b7b7-103">The following topics introduce and discuss the essential components of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], an object-oriented programming language.</span></span> <span data-ttu-id="4b7b7-104">Po vytvoření uživatelského rozhraní pro vaše aplikace pomocí formuláře a ovládací prvky, budete muset psát kód, který definuje chování aplikace.</span><span class="sxs-lookup"><span data-stu-id="4b7b7-104">After creating the user interface for your application using forms and controls, you need to write the code that defines the application's behavior.</span></span> <span data-ttu-id="4b7b7-105">Stejně jako u moderní programovací jazyk, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] podporuje mnoho běžných programovací konstrukce a jazykové elementy.</span><span class="sxs-lookup"><span data-stu-id="4b7b7-105">As with any modern programming language, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] supports a number of common programming constructs and language elements.</span></span>  
  
 <span data-ttu-id="4b7b7-106">Pokud máte naprogramovaný, tak v jiných jazycích, velká část uvedenými v této části vám mohou připadat seznámit.</span><span class="sxs-lookup"><span data-stu-id="4b7b7-106">If you have programmed in other languages, much of the material covered in this section might seem familiar.</span></span> <span data-ttu-id="4b7b7-107">Zatímco většina konstrukce jsou podobné jako v jiných jazycích, povaze událostmi řízené [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] zavádí některé jemně lišit.</span><span class="sxs-lookup"><span data-stu-id="4b7b7-107">While most of the constructs are similar to those in other languages, the event-driven nature of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] introduces some subtle differences.</span></span>  
  
 <span data-ttu-id="4b7b7-108">Pokud jste ještě programování, materiály v této části slouží jako úvodem do základních stavebních bloků pro psaní kódu.</span><span class="sxs-lookup"><span data-stu-id="4b7b7-108">If you are new to programming, the material in this section serves as an introduction to the basic building blocks for writing code.</span></span> <span data-ttu-id="4b7b7-109">Jakmile porozumíte základům, můžete vytvořit výkonné aplikace pomocí [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4b7b7-109">Once you understand the basics, you can create powerful applications using [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4b7b7-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="4b7b7-110">In This Section</span></span>  
 [<span data-ttu-id="4b7b7-111">Pole</span><span class="sxs-lookup"><span data-stu-id="4b7b7-111">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 <span data-ttu-id="4b7b7-112">Popisuje provádění kódu kompaktnější a výkonné deklarování a použití polí, které uchovávat více souvisejících hodnot.</span><span class="sxs-lookup"><span data-stu-id="4b7b7-112">Discusses making your code more compact and powerful by declaring and using arrays, which hold multiple related values.</span></span>  
  
 [<span data-ttu-id="4b7b7-113">Inicializátory kolekcí</span><span class="sxs-lookup"><span data-stu-id="4b7b7-113">Collection Initializers</span></span>](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
 <span data-ttu-id="4b7b7-114">Popisuje Inicializátory kolekcí, které vám umožní vytvořit kolekci a jeho naplnění počáteční sadu hodnot.</span><span class="sxs-lookup"><span data-stu-id="4b7b7-114">Describes collection initializers, which enable you to create a collection and populate it with an initial set of values.</span></span>  
  
 [<span data-ttu-id="4b7b7-115">Konstanty a výčty</span><span class="sxs-lookup"><span data-stu-id="4b7b7-115">Constants and Enumerations</span></span>](../../../visual-basic/programming-guide/language-features/constants-enums/index.md)  
 <span data-ttu-id="4b7b7-116">Popisuje, ukládání neměnné hodnoty pro opakované použití, včetně sady souvisejících hodnot konstant.</span><span class="sxs-lookup"><span data-stu-id="4b7b7-116">Discusses storing unchanging values for repeated use, including sets of related constant values.</span></span>  
  
 [<span data-ttu-id="4b7b7-117">Tok řízení</span><span class="sxs-lookup"><span data-stu-id="4b7b7-117">Control Flow</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 <span data-ttu-id="4b7b7-118">Ukazuje, jak regulovat tok provádění vašeho programu.</span><span class="sxs-lookup"><span data-stu-id="4b7b7-118">Shows how to regulate the flow of your program's execution.</span></span>  
  
 [<span data-ttu-id="4b7b7-119">Datové typy</span><span class="sxs-lookup"><span data-stu-id="4b7b7-119">Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 <span data-ttu-id="4b7b7-120">Popisuje, jaké druhy dat mohou být uloženy programovací element a jak jsou uložena data.</span><span class="sxs-lookup"><span data-stu-id="4b7b7-120">Describes what kinds of data a programming element can hold and how that data is stored.</span></span>  
  
 [<span data-ttu-id="4b7b7-121">Deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="4b7b7-121">Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/index.md)  
 <span data-ttu-id="4b7b7-122">Zahrnuje programovací elementy můžou deklarovat, jejich názvy a vlastnosti, a jak kompilátor přeloží odkazy na ně.</span><span class="sxs-lookup"><span data-stu-id="4b7b7-122">Covers programming elements you can declare, their names and characteristics, and how the compiler resolves references to them.</span></span>  
  
 [<span data-ttu-id="4b7b7-123">Delegáti</span><span class="sxs-lookup"><span data-stu-id="4b7b7-123">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 <span data-ttu-id="4b7b7-124">Poskytuje úvod do Delegáti a jak se používají v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4b7b7-124">Provides an introduction to delegates and how they are used in Visual Basic.</span></span>  
  
 [<span data-ttu-id="4b7b7-125">Statické a pozdní vazby</span><span class="sxs-lookup"><span data-stu-id="4b7b7-125">Early and Late Binding</span></span>](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)  
 <span data-ttu-id="4b7b7-126">Popisuje vazbu, která se provádí pomocí kompilátoru při přiřazení objektu k proměnné objektu a rozdíly mezi objekty časné vazby a pozdní vazbu.</span><span class="sxs-lookup"><span data-stu-id="4b7b7-126">Describes binding, which is performed by the compiler when an object is assigned to an object variable, and the differences between early-bound and late-bound objects.</span></span>  
  
 [<span data-ttu-id="4b7b7-127">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="4b7b7-127">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)  
 <span data-ttu-id="4b7b7-128">Poskytuje přehled chyby syntaxe, chyby a logické chyby.</span><span class="sxs-lookup"><span data-stu-id="4b7b7-128">Provides an overview of syntax errors, run-time errors, and logic errors.</span></span>  
  
 [<span data-ttu-id="4b7b7-129">Události</span><span class="sxs-lookup"><span data-stu-id="4b7b7-129">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)  
 <span data-ttu-id="4b7b7-130">Ukazuje, jak deklarace a používání událostí.</span><span class="sxs-lookup"><span data-stu-id="4b7b7-130">Shows how to declare and use events.</span></span>  
  
 [<span data-ttu-id="4b7b7-131">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="4b7b7-131">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)  
 <span data-ttu-id="4b7b7-132">Popisuje, co jsou rozhraní a jak je můžete využít ve svých aplikacích.</span><span class="sxs-lookup"><span data-stu-id="4b7b7-132">Describes what interfaces are and how you can use them in your applications.</span></span>  
  
 [<span data-ttu-id="4b7b7-133">LINQ</span><span class="sxs-lookup"><span data-stu-id="4b7b7-133">LINQ</span></span>](../../../visual-basic/programming-guide/language-features/linq/index.md)  
 <span data-ttu-id="4b7b7-134">Obsahuje odkazy na témata, která zavést [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] funkce a programování.</span><span class="sxs-lookup"><span data-stu-id="4b7b7-134">Provides links to topics that introduce [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] features and programming.</span></span>  
  
 [<span data-ttu-id="4b7b7-135">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="4b7b7-135">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 <span data-ttu-id="4b7b7-136">Poskytuje přehled objekty a třídy, jak se používají, jejich vztahů s sebou a vlastnosti, metod a událostí, které vystavují.</span><span class="sxs-lookup"><span data-stu-id="4b7b7-136">Provides an overview of objects and classes, how they are used, their relationships to each other, and the properties, methods, and events they expose.</span></span>  
  
 [<span data-ttu-id="4b7b7-137">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="4b7b7-137">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 <span data-ttu-id="4b7b7-138">Popisuje elementy kódu, které pracují s hodnotu za ruku prvky, jak efektivně používat a jak kombinovat jim poskytne nové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4b7b7-138">Describes the code elements that manipulate value-holding elements, how to use them efficiently, and how to combine them to yield new values.</span></span>  
  
 [<span data-ttu-id="4b7b7-139">Postupy</span><span class="sxs-lookup"><span data-stu-id="4b7b7-139">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 <span data-ttu-id="4b7b7-140">Popisuje `Sub`, `Function`, `Property`, a `Operator` postupy, jakož i Pokročilá témata například rekurzivní a přetížené procedury.</span><span class="sxs-lookup"><span data-stu-id="4b7b7-140">Describes `Sub`, `Function`, `Property`, and `Operator` procedures, as well as advanced topics such as recursive and overloaded procedures.</span></span>  
  
 [<span data-ttu-id="4b7b7-141">Příkazy</span><span class="sxs-lookup"><span data-stu-id="4b7b7-141">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 <span data-ttu-id="4b7b7-142">Popisuje příkazy deklarace a spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="4b7b7-142">Describes declaration and executable statements.</span></span>  
  
 [<span data-ttu-id="4b7b7-143">Řetězce</span><span class="sxs-lookup"><span data-stu-id="4b7b7-143">Strings</span></span>](../../../visual-basic/programming-guide/language-features/strings/index.md)  
 <span data-ttu-id="4b7b7-144">Obsahuje odkazy na témata, která popisují základní koncepty o používání řetězců v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4b7b7-144">Provides links to topics that describe the basic concepts about using strings in Visual Basic.</span></span>  
  
 [<span data-ttu-id="4b7b7-145">Proměnné</span><span class="sxs-lookup"><span data-stu-id="4b7b7-145">Variables</span></span>](../../../visual-basic/programming-guide/language-features/variables/index.md)  
 <span data-ttu-id="4b7b7-146">Představuje proměnné a popisuje jejich použití v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4b7b7-146">Introduces variables and describes how to use them in Visual Basic.</span></span>  
  
 [<span data-ttu-id="4b7b7-147">XML</span><span class="sxs-lookup"><span data-stu-id="4b7b7-147">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)  
 <span data-ttu-id="4b7b7-148">Obsahuje odkazy na témata, které popisují, jak používat XML v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4b7b7-148">Provides links to topics that describe how to use XML in Visual Basic.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4b7b7-149">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="4b7b7-149">Related Sections</span></span>  
 [<span data-ttu-id="4b7b7-150">Kolekce</span><span class="sxs-lookup"><span data-stu-id="4b7b7-150">Collections</span></span>](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)  
 <span data-ttu-id="4b7b7-151">Popisuje některé typy kolekcí, které jsou poskytovány rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4b7b7-151">Describes some of the types of collections that are provided by the .NET Framework.</span></span> <span data-ttu-id="4b7b7-152">Demonstruje použití jednoduchých kolekcí a kolekcí dvojic klíč/hodnota.</span><span class="sxs-lookup"><span data-stu-id="4b7b7-152">Demonstrates how to use simple collections and collections of key/value pairs.</span></span>  
  
 [<span data-ttu-id="4b7b7-153">Referenční dokumentace jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4b7b7-153">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)  
 <span data-ttu-id="4b7b7-154">Poskytuje referenční informace o různých aspektech [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programování.</span><span class="sxs-lookup"><span data-stu-id="4b7b7-154">Provides reference information on various aspects of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programming.</span></span>
