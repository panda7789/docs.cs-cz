---
title: "Různé datové typy (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Object data type [Visual Basic], data types
- data types [Visual Basic], choosing
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b6bb86bb6d203aa4e6bdded27a4cb78a8155ddec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="miscellaneous-data-types-visual-basic"></a><span data-ttu-id="6b9aa-102">Různé datové typy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6b9aa-102">Miscellaneous Data Types (Visual Basic)</span></span>
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="6b9aa-103">poskytuje několik typů dat, které nejsou orientované na číslic nebo znaků.</span><span class="sxs-lookup"><span data-stu-id="6b9aa-103"> supplies several data types that are not oriented toward numbers or characters.</span></span> <span data-ttu-id="6b9aa-104">Místo toho budou se týkají specializované data, jako Ano/ne hodnoty, hodnoty data a času a adresy objektu.</span><span class="sxs-lookup"><span data-stu-id="6b9aa-104">Instead, they deal with specialized data such as yes/no values, date/time values, and object addresses.</span></span>  
  
 <span data-ttu-id="6b9aa-105">Pro tabulka zobrazující porovnání vedle sebe [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] datové typy, najdete v části [datové typy](../../../../visual-basic/language-reference/data-types/data-type-summary.md).</span><span class="sxs-lookup"><span data-stu-id="6b9aa-105">For a table showing a side-by-side comparison of the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] data types, see [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md).</span></span>  
  
## <a name="boolean-type"></a><span data-ttu-id="6b9aa-106">Typem logická hodnota</span><span class="sxs-lookup"><span data-stu-id="6b9aa-106">Boolean Type</span></span>  
 <span data-ttu-id="6b9aa-107">[Datový typ Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) je bez znaménka hodnota, který je považován za buď `True` nebo `False`.</span><span class="sxs-lookup"><span data-stu-id="6b9aa-107">The [Boolean Data Type](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) is an unsigned value that is interpreted as either `True` or `False`.</span></span> <span data-ttu-id="6b9aa-108">Šířku dat závisí na implementující platformy.</span><span class="sxs-lookup"><span data-stu-id="6b9aa-108">Its data width depends on the implementing platform.</span></span> <span data-ttu-id="6b9aa-109">Pokud proměnná může obsahovat pouze hodnoty dvou stavů například true nebo false, Ano/Ne, nebo zapnutí nebo vypnutí, deklarujte ji jako `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="6b9aa-109">If a variable can contain only two-state values such as true/false, yes/no, or on/off, declare it as `Boolean`.</span></span>  
  
## <a name="date-type"></a><span data-ttu-id="6b9aa-110">Date – typ</span><span class="sxs-lookup"><span data-stu-id="6b9aa-110">Date Type</span></span>  
 <span data-ttu-id="6b9aa-111">[Date – datový typ](../../../../visual-basic/language-reference/data-types/date-data-type.md) je 64 bitů hodnotu, která obsahuje informace o datu a času.</span><span class="sxs-lookup"><span data-stu-id="6b9aa-111">The [Date Data Type](../../../../visual-basic/language-reference/data-types/date-data-type.md) is a 64-bit value that holds both date and time information.</span></span> <span data-ttu-id="6b9aa-112">Každý přírůstek představuje 100 nanosekundách uplynulý čas od začátku (12:00:00) z 1. ledna roku 1 v gregoriánském kalendáři.</span><span class="sxs-lookup"><span data-stu-id="6b9aa-112">Each increment represents 100 nanoseconds of elapsed time since the beginning (12:00 AM) of January 1 of the year 1 in the Gregorian calendar.</span></span> <span data-ttu-id="6b9aa-113">Pokud proměnná může obsahovat hodnotu data a hodnotu čas, deklarujte ji jako `Date`.</span><span class="sxs-lookup"><span data-stu-id="6b9aa-113">If a variable can contain a date value, a time value, or both, declare it as `Date`.</span></span>  
  
## <a name="object-type"></a><span data-ttu-id="6b9aa-114">Typ objektu</span><span class="sxs-lookup"><span data-stu-id="6b9aa-114">Object Type</span></span>  
 <span data-ttu-id="6b9aa-115">[Object – datový typ](../../../../visual-basic/language-reference/data-types/object-data-type.md) 32-bit adresa, která odkazuje na instanci objektu v rámci vaší aplikace nebo v nějaké jiné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="6b9aa-115">The [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) is a 32-bit address that points to an object instance within your application or in some other application.</span></span> <span data-ttu-id="6b9aa-116">`Object` Proměnná může označovat libovolného objektu rozpozná aplikace, nebo se data jakéhokoli datového typu.</span><span class="sxs-lookup"><span data-stu-id="6b9aa-116">An `Object` variable can refer to any object your application recognizes, or to data of any data type.</span></span> <span data-ttu-id="6b9aa-117">To zahrnuje i *typů hodnot*, jako například `Integer`, `Boolean`a struktura instance, a *odkazové typy*, které jsou instancemi třídy objekty vytvořené ze třídy, jako `String`a <xref:System.Windows.Forms.Form>a pole instance.</span><span class="sxs-lookup"><span data-stu-id="6b9aa-117">This includes both *value types*, such as `Integer`, `Boolean`, and structure instances, and *reference types*, which are instances of objects created from classes such as `String` and <xref:System.Windows.Forms.Form>, and array instances.</span></span>  
  
 <span data-ttu-id="6b9aa-118">Pokud proměnná obsahuje ukazatel na instanci třídy, která si nejste jisti v době kompilace nebo může ukazovat na data z různých datových typů, deklarujte ji jako `Object`.</span><span class="sxs-lookup"><span data-stu-id="6b9aa-118">If a variable stores a pointer to an instance of a class that you do not know at compile time, or if it can point to data of various data types, declare it as `Object`.</span></span>  
  
 <span data-ttu-id="6b9aa-119">Výhodou `Object` datový typ je, že je můžete použít k ukládání dat jakéhokoli datového typu.</span><span class="sxs-lookup"><span data-stu-id="6b9aa-119">The advantage of the `Object` data type is that you can use it to store data of any data type.</span></span> <span data-ttu-id="6b9aa-120">Nevýhodou je, být účtovány další operace, které trvat delší dobu spuštění a aby vaše aplikace provést něco pomalejší.</span><span class="sxs-lookup"><span data-stu-id="6b9aa-120">The disadvantage is that you incur extra operations that take more execution time and make your application perform slower.</span></span> <span data-ttu-id="6b9aa-121">Pokud používáte `Object` proměnná pro typy hodnot, platit *zabalení* a *rozbalení*.</span><span class="sxs-lookup"><span data-stu-id="6b9aa-121">If you use an `Object` variable for value types, you incur *boxing* and *unboxing*.</span></span> <span data-ttu-id="6b9aa-122">Pokud ho používáte pro odkazové typy, způsobit *pozdní vazby*.</span><span class="sxs-lookup"><span data-stu-id="6b9aa-122">If you use it for reference types, you incur *late binding*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b9aa-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="6b9aa-123">See Also</span></span>  
 [<span data-ttu-id="6b9aa-124">Znaky typu</span><span class="sxs-lookup"><span data-stu-id="6b9aa-124">Type Characters</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [<span data-ttu-id="6b9aa-125">Základní datové typy</span><span class="sxs-lookup"><span data-stu-id="6b9aa-125">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [<span data-ttu-id="6b9aa-126">Číselné datové typy</span><span class="sxs-lookup"><span data-stu-id="6b9aa-126">Numeric Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)  
 [<span data-ttu-id="6b9aa-127">Znakové datové typy</span><span class="sxs-lookup"><span data-stu-id="6b9aa-127">Character Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)  
 [<span data-ttu-id="6b9aa-128">Řešení potíží s datové typy</span><span class="sxs-lookup"><span data-stu-id="6b9aa-128">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="6b9aa-129">Statické a pozdní vazby</span><span class="sxs-lookup"><span data-stu-id="6b9aa-129">Early and Late Binding</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
