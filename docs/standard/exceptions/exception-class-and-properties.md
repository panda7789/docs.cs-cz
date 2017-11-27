---
title: "Třída a vlastnosti výjimky"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exceptions, Exception class
- Exception class
ms.assetid: e2e1f8c4-e7b4-467d-9a66-13c90861221d
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 253a9846e484aa4e54c3433b0bbc8623519bbb7e
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2017
---
# <a name="exception-class-and-properties"></a><span data-ttu-id="fc558-102">Třída a vlastnosti výjimky</span><span class="sxs-lookup"><span data-stu-id="fc558-102">Exception class and properties</span></span>

<span data-ttu-id="fc558-103"><xref:System.Exception> Třída je základní třída, ze které dědí výjimky.</span><span class="sxs-lookup"><span data-stu-id="fc558-103">The <xref:System.Exception> class is the base class from which exceptions inherit.</span></span> <span data-ttu-id="fc558-104">Například <xref:System.InvalidCastException> hierarchie tříd je následující:</span><span class="sxs-lookup"><span data-stu-id="fc558-104">For example, the <xref:System.InvalidCastException> class hierarchy is as follows:</span></span>

```
Object
  Exception
    SystemException
       InvalidCastException
```

<span data-ttu-id="fc558-105"><xref:System.Exception> Třída má následující vlastnosti, které vám pomohou zajistit pochopení výjimku jednodušší.</span><span class="sxs-lookup"><span data-stu-id="fc558-105">The <xref:System.Exception> class has the following properties that help make understanding an exception easier.</span></span>

| <span data-ttu-id="fc558-106">Název vlastnosti</span><span class="sxs-lookup"><span data-stu-id="fc558-106">Property Name</span></span> | <span data-ttu-id="fc558-107">Popis</span><span class="sxs-lookup"><span data-stu-id="fc558-107">Description</span></span> |
| ------------- | ----------- |
| <xref:System.Exception.Data> | <span data-ttu-id="fc558-108"><xref:System.Collections.IDictionary> , Obsahuje libovolná data v páry klíč hodnota.</span><span class="sxs-lookup"><span data-stu-id="fc558-108">An <xref:System.Collections.IDictionary> that holds arbitrary data in key-value pairs.</span></span> |
| <xref:System.Exception.HelpLink> | <span data-ttu-id="fc558-109">Adresa URL (nebo název URN) můžete podržet souboru nápovědy, který poskytuje podrobné informace o příčině výjimky.</span><span class="sxs-lookup"><span data-stu-id="fc558-109">Can hold a URL (or URN) to a help file that provides extensive information about the cause of an exception.</span></span> |
| <xref:System.Exception.InnerException> | <span data-ttu-id="fc558-110">Tuto vlastnost lze použít k vytvoření a zachování řadu výjimky během zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="fc558-110">This property can be used to create and preserve a series of exceptions during exception handling.</span></span> <span data-ttu-id="fc558-111">Můžete ho vytvořit novou výjimku, která obsahuje dříve zachycení výjimky.</span><span class="sxs-lookup"><span data-stu-id="fc558-111">You can use it to create a new exception that contains previously caught exceptions.</span></span> <span data-ttu-id="fc558-112">Původní výjimka se dají zachytit druhou výjimkou v <xref:System.Exception.InnerException> vlastnosti, což umožňuje kód, který zpracovává druhou výjimku zjistit další informace.</span><span class="sxs-lookup"><span data-stu-id="fc558-112">The original exception can be captured by the second exception in the <xref:System.Exception.InnerException> property, allowing code that handles the second exception to examine the additional information.</span></span> <span data-ttu-id="fc558-113">Předpokládejme například, že máte metodu, která přijímá argument, který je v nesprávném formátu.</span><span class="sxs-lookup"><span data-stu-id="fc558-113">For example, suppose you have a method that receives an argument that's improperly formatted.</span></span>  <span data-ttu-id="fc558-114">Kód se pokusí načíst argument, ale je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="fc558-114">The code tries to read the argument, but an exception is thrown.</span></span> <span data-ttu-id="fc558-115">Metoda zachytí výjimky a vyvolá výjimku <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="fc558-115">The method catches the exception and throws a <xref:System.FormatException>.</span></span> <span data-ttu-id="fc558-116">Pokud chcete zlepšit volajícího schopnosti určit důvod, proč je vyvolána výjimka, je někdy žádoucí, aby metoda catch výjimka vyvolaná objektem pomocnou rutinou a poté vyvolat výjimku více popisuje chybu, která proběhla.</span><span class="sxs-lookup"><span data-stu-id="fc558-116">To improve the caller's ability to determine the reason an exception is thrown, it is sometimes desirable for a method to catch an exception thrown by a helper routine and then throw an exception more indicative of the error that has occurred.</span></span> <span data-ttu-id="fc558-117">Mohou být vytvořeny nové a smysluplnější výjimky, které lze nastavit odkaz na informacích o vnitřní výjimce původní výjimku.</span><span class="sxs-lookup"><span data-stu-id="fc558-117">A new and more meaningful exception can be created, where the inner exception reference can be set to the original exception.</span></span> <span data-ttu-id="fc558-118">Tato smysluplnější výjimka může být vyvolána pak volajícímu.</span><span class="sxs-lookup"><span data-stu-id="fc558-118">This more meaningful exception can then be thrown to the caller.</span></span> <span data-ttu-id="fc558-119">Všimněte si, že pomocí této funkce můžete vytvořit řadu propojených výjimek, který končí výjimku, která byla vyvolána jako první.</span><span class="sxs-lookup"><span data-stu-id="fc558-119">Note that with this functionality, you can create a series of linked exceptions that ends with the exception that was thrown first.</span></span> |
| <xref:System.Exception.Message> | <span data-ttu-id="fc558-120">Obsahuje podrobné informace o příčině výjimky.</span><span class="sxs-lookup"><span data-stu-id="fc558-120">Provides details about the cause of an exception.</span></span>
| <xref:System.Exception.Source> | <span data-ttu-id="fc558-121">Získá nebo nastaví název aplikace nebo objekt, který způsobuje chybu.</span><span class="sxs-lookup"><span data-stu-id="fc558-121">Gets or sets the name of the application or the object that causes the error.</span></span> |
| <xref:System.Exception.StackTrace>| <span data-ttu-id="fc558-122">Obsahuje trasování zásobníku, který slouží k určení, kde došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="fc558-122">Contains a stack trace that can be used to determine where an error occurred.</span></span> <span data-ttu-id="fc558-123">Trasování zásobníku zahrnuje zdrojový soubor název a číslo řádku, pokud ladicí informace je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="fc558-123">The stack trace includes the source file name and program line number if debugging information is available.</span></span> |

<span data-ttu-id="fc558-124">Většina tříd, které dědí od <xref:System.Exception> neimplementuje další členy nebo dodatečných funkcí; jednoduše dědí z <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="fc558-124">Most of the classes that inherit from <xref:System.Exception> do not implement additional members or provide additional functionality; they simply inherit from <xref:System.Exception>.</span></span> <span data-ttu-id="fc558-125">Proto nejdůležitější informace o výjimce naleznete v hierarchii třídy výjimek, název výjimky a informace obsažené v výjimce.</span><span class="sxs-lookup"><span data-stu-id="fc558-125">Therefore, the most important information for an exception can be found in the hierarchy of exception classes, the exception name, and the information contained in the exception.</span></span>

<span data-ttu-id="fc558-126">Doporučujeme, abyste throw a catch pouze objekty, které jsou odvozeny od <xref:System.Exception>, ale můžete vyvolat libovolný objekt, který je odvozen od <xref:System.Object> třída jako výjimku.</span><span class="sxs-lookup"><span data-stu-id="fc558-126">We recommend that you throw and catch only objects that derive from <xref:System.Exception>, but you can throw any object that derives from the <xref:System.Object> class as an exception.</span></span> <span data-ttu-id="fc558-127">Všimněte si, že ne všechny jazyky podporují vyvolávání a zachycování objekty, které není odvozena od <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="fc558-127">Note that not all languages support throwing and catching objects that do not derive from <xref:System.Exception>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="fc558-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="fc558-128">See Also</span></span>  
[<span data-ttu-id="fc558-129">Výjimky</span><span class="sxs-lookup"><span data-stu-id="fc558-129">Exceptions</span></span>](index.md)
