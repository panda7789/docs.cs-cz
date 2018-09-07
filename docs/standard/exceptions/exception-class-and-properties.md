---
title: Třída a vlastnosti výjimky
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, Exception class
- Exception class
ms.assetid: e2e1f8c4-e7b4-467d-9a66-13c90861221d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 283b3b1aa0d56b50b6f9e67b66de3e0b68ae2331
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44075517"
---
# <a name="exception-class-and-properties"></a><span data-ttu-id="77a74-102">Třída a vlastnosti výjimky</span><span class="sxs-lookup"><span data-stu-id="77a74-102">Exception class and properties</span></span>

<span data-ttu-id="77a74-103"><xref:System.Exception> Třída je základní třída, ze kterého dědí výjimky.</span><span class="sxs-lookup"><span data-stu-id="77a74-103">The <xref:System.Exception> class is the base class from which exceptions inherit.</span></span> <span data-ttu-id="77a74-104">Například <xref:System.InvalidCastException> hierarchie tříd je takto:</span><span class="sxs-lookup"><span data-stu-id="77a74-104">For example, the <xref:System.InvalidCastException> class hierarchy is as follows:</span></span>

```
Object
  Exception
    SystemException
       InvalidCastException
```

<span data-ttu-id="77a74-105"><xref:System.Exception> Třída má následující vlastnosti, které usnadňují porozumění výjimku jednodušší.</span><span class="sxs-lookup"><span data-stu-id="77a74-105">The <xref:System.Exception> class has the following properties that help make understanding an exception easier.</span></span>

| <span data-ttu-id="77a74-106">Název vlastnosti</span><span class="sxs-lookup"><span data-stu-id="77a74-106">Property Name</span></span> | <span data-ttu-id="77a74-107">Popis</span><span class="sxs-lookup"><span data-stu-id="77a74-107">Description</span></span> |
| ------------- | ----------- |
| <xref:System.Exception.Data> | <span data-ttu-id="77a74-108"><xref:System.Collections.IDictionary> Libovolná data, která obsahuje v párech klíč hodnota.</span><span class="sxs-lookup"><span data-stu-id="77a74-108">An <xref:System.Collections.IDictionary> that holds arbitrary data in key-value pairs.</span></span> |
| <xref:System.Exception.HelpLink> | <span data-ttu-id="77a74-109">Adresa URL (nebo URN) může obsahovat soubor nápovědy, která poskytuje podrobné informace o příčině výjimky.</span><span class="sxs-lookup"><span data-stu-id="77a74-109">Can hold a URL (or URN) to a help file that provides extensive information about the cause of an exception.</span></span> |
| <xref:System.Exception.InnerException> | <span data-ttu-id="77a74-110">Tato vlastnost slouží k vytvoření a zachovat řadu výjimek během zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="77a74-110">This property can be used to create and preserve a series of exceptions during exception handling.</span></span> <span data-ttu-id="77a74-111">Můžete ho vytvořit novou výjimku, která obsahuje dříve zachycené výjimky.</span><span class="sxs-lookup"><span data-stu-id="77a74-111">You can use it to create a new exception that contains previously caught exceptions.</span></span> <span data-ttu-id="77a74-112">Původní výjimku můžete zaznamenat druhou výjimkou v <xref:System.Exception.InnerException> vlastnosti, což umožňuje kód, který zpracovává druhou výjimkou zjistit další informace.</span><span class="sxs-lookup"><span data-stu-id="77a74-112">The original exception can be captured by the second exception in the <xref:System.Exception.InnerException> property, allowing code that handles the second exception to examine the additional information.</span></span> <span data-ttu-id="77a74-113">Předpokládejme například, že měl odpovídající metodu, která přijímá argument, který je v nesprávném formátu.</span><span class="sxs-lookup"><span data-stu-id="77a74-113">For example, suppose you have a method that receives an argument that's improperly formatted.</span></span>  <span data-ttu-id="77a74-114">Kód se pokusí načíst argument, ale dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="77a74-114">The code tries to read the argument, but an exception is thrown.</span></span> <span data-ttu-id="77a74-115">Metoda zachytí výjimku a vyvolá výjimku <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="77a74-115">The method catches the exception and throws a <xref:System.FormatException>.</span></span> <span data-ttu-id="77a74-116">Pokud chcete zlepšit volajícího schopnost určit důvod, proč je vyvolána výjimka, je někdy žádoucí, aby metoda zachytit výjimku vyvolanou pomocná rutina a poté vyvolají výjimku více naznačuje, že došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="77a74-116">To improve the caller's ability to determine the reason an exception is thrown, it is sometimes desirable for a method to catch an exception thrown by a helper routine and then throw an exception more indicative of the error that has occurred.</span></span> <span data-ttu-id="77a74-117">Nelze vytvořit nové a lépe vystihuje výjimky, kde lze nastavit odkaz na vnitřní výjimku v původní výjimky.</span><span class="sxs-lookup"><span data-stu-id="77a74-117">A new and more meaningful exception can be created, where the inner exception reference can be set to the original exception.</span></span> <span data-ttu-id="77a74-118">Toto lépe vystihuje výjimky mohou být vyvolány pak volajícímu.</span><span class="sxs-lookup"><span data-stu-id="77a74-118">This more meaningful exception can then be thrown to the caller.</span></span> <span data-ttu-id="77a74-119">Všimněte si, že tuto funkci, můžete vytvořit řadu propojené výjimek, který končí výjimku, která byla vyvolána jako první.</span><span class="sxs-lookup"><span data-stu-id="77a74-119">Note that with this functionality, you can create a series of linked exceptions that ends with the exception that was thrown first.</span></span> |
| <xref:System.Exception.Message> | <span data-ttu-id="77a74-120">Obsahuje podrobné informace o příčině výjimky.</span><span class="sxs-lookup"><span data-stu-id="77a74-120">Provides details about the cause of an exception.</span></span>
| <xref:System.Exception.Source> | <span data-ttu-id="77a74-121">Získá nebo nastaví název aplikace nebo objekt, který způsobuje chybu.</span><span class="sxs-lookup"><span data-stu-id="77a74-121">Gets or sets the name of the application or the object that causes the error.</span></span> |
| <xref:System.Exception.StackTrace>| <span data-ttu-id="77a74-122">Obsahuje trasování zásobníku, který slouží k určení, kde došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="77a74-122">Contains a stack trace that can be used to determine where an error occurred.</span></span> <span data-ttu-id="77a74-123">Trasování zásobníku zahrnuje zdrojový soubor název a číslo řádku, pokud informace o ladění je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="77a74-123">The stack trace includes the source file name and program line number if debugging information is available.</span></span> |

<span data-ttu-id="77a74-124">Většina tříd, které dědí <xref:System.Exception> implementovat další členy nebo poskytnutí dalších funkcí; jednoduše dědí z <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="77a74-124">Most of the classes that inherit from <xref:System.Exception> do not implement additional members or provide additional functionality; they simply inherit from <xref:System.Exception>.</span></span> <span data-ttu-id="77a74-125">Proto nejdůležitější informace o výjimce najdete v hierarchii tříd výjimek, název výjimky a informace obsažené ve výjimce.</span><span class="sxs-lookup"><span data-stu-id="77a74-125">Therefore, the most important information for an exception can be found in the hierarchy of exception classes, the exception name, and the information contained in the exception.</span></span>

<span data-ttu-id="77a74-126">Doporučujeme, abyste throw a catch pouze objekty, které jsou odvozeny z <xref:System.Exception>, ale může vyvolat libovolný objekt, který je odvozen od <xref:System.Object> třídu jako výjimku.</span><span class="sxs-lookup"><span data-stu-id="77a74-126">We recommend that you throw and catch only objects that derive from <xref:System.Exception>, but you can throw any object that derives from the <xref:System.Object> class as an exception.</span></span> <span data-ttu-id="77a74-127">Všimněte si, že nepodporují všechny jazyky vyvolávání a zachycování objekty, které nejsou odvozeny z <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="77a74-127">Note that not all languages support throwing and catching objects that do not derive from <xref:System.Exception>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="77a74-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="77a74-128">See also</span></span>

- [<span data-ttu-id="77a74-129">Výjimky</span><span class="sxs-lookup"><span data-stu-id="77a74-129">Exceptions</span></span>](index.md)
