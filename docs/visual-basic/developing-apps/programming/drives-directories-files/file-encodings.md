---
title: "Kódování souborů (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- character encodings
- files [Visual Basic], encoding
- Unicode, file encoding
- file encoding
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: deaab4371ab0d5d15c627bfd6352a7090bf08024
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="file-encodings-visual-basic"></a><span data-ttu-id="51f1b-102">Kódování souborů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="51f1b-102">File Encodings (Visual Basic)</span></span>
<span data-ttu-id="51f1b-103">Kódování souborů, také známé jako kódování znaků, určete, jak představují znaky při zpracování textu.</span><span class="sxs-lookup"><span data-stu-id="51f1b-103">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="51f1b-104">Jeden kódování může být vhodnější než oproti jinému z hlediska jazykové symboly může nebo nemůže zpracovat, i když je obvykle upřednostňované kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="51f1b-104">One encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span>  
  
 <span data-ttu-id="51f1b-105">Při čtení nebo zápis do souborů, nesprávně odpovídající kódování souborů může vést k výjimky nebo nesprávné výsledky.</span><span class="sxs-lookup"><span data-stu-id="51f1b-105">When reading from or writing to files, improperly matching file encodings may result in exceptions or incorrect results.</span></span>  
  
## <a name="types-of-encodings"></a><span data-ttu-id="51f1b-106">Typy kódování</span><span class="sxs-lookup"><span data-stu-id="51f1b-106">Types of Encodings</span></span>  
 <span data-ttu-id="51f1b-107">Unicode je upřednostňované kódování při práci se soubory.</span><span class="sxs-lookup"><span data-stu-id="51f1b-107">Unicode is the preferred encoding when working with files.</span></span> <span data-ttu-id="51f1b-108">Unicode je po celém světě standard kódování znaků, který používá kódu 16bitové hodnoty k reprezentaci všech znaků použitých v moderní computing, včetně technických symbolů a speciální znaky, které jsou používány publikování.</span><span class="sxs-lookup"><span data-stu-id="51f1b-108">Unicode is a worldwide character-encoding standard that uses 16-bit code values to represent all the characters used in modern computing, including technical symbols and special characters used in publishing.</span></span>  
  
 <span data-ttu-id="51f1b-109">Předchozí standardy kódování znaků se skládal z tradiční znakových sad, jako je například znakovou sadu Windows ANSI, který používá hodnoty 8bitové kódu nebo kombinace 8bitové hodnoty k reprezentaci znaky použít v určitém jazyce nebo geografické oblasti.</span><span class="sxs-lookup"><span data-stu-id="51f1b-109">Previous character-encoding standards consisted of traditional character sets, such as the Windows ANSI character set that uses 8-bit code values, or combinations of 8-bit values, to represent the characters used in a specific language or geographical region.</span></span>  
  
## <a name="encoding-class"></a><span data-ttu-id="51f1b-110">Kódování – třída</span><span class="sxs-lookup"><span data-stu-id="51f1b-110">Encoding Class</span></span>  
 <span data-ttu-id="51f1b-111"><xref:System.Text.Encoding> Třída představuje kódování znaků.</span><span class="sxs-lookup"><span data-stu-id="51f1b-111">The <xref:System.Text.Encoding> class represents a character encoding.</span></span> <span data-ttu-id="51f1b-112">Tato tabulka uvádí typ kódování, které jsou k dispozici a popisuje všechny.</span><span class="sxs-lookup"><span data-stu-id="51f1b-112">This table lists the type of encodings available and describes each.</span></span>  
  
|<span data-ttu-id="51f1b-113">Název</span><span class="sxs-lookup"><span data-stu-id="51f1b-113">Name</span></span>|<span data-ttu-id="51f1b-114">Popis</span><span class="sxs-lookup"><span data-stu-id="51f1b-114">Description</span></span>|
|---|---|    
|<xref:System.Text.ASCIIEncoding>|<span data-ttu-id="51f1b-115">Představuje kódování znaků ASCII znaky Unicode.</span><span class="sxs-lookup"><span data-stu-id="51f1b-115">Represents an ASCII character encoding of Unicode characters.</span></span>|  
|<xref:System.Text.UnicodeEncoding>|<span data-ttu-id="51f1b-116">Představuje kódování UTF-16 znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="51f1b-116">Represents a UTF-16 encoding of Unicode characters.</span></span>|  
|<xref:System.Text.UTF32Encoding>|<span data-ttu-id="51f1b-117">Představuje kódování znaků Unicode UTF-32.</span><span class="sxs-lookup"><span data-stu-id="51f1b-117">Represents a UTF-32 encoding of Unicode characters.</span></span>|  
|<xref:System.Text.UTF7Encoding>|<span data-ttu-id="51f1b-118">Představuje kódování znaků Unicode UTF-7.</span><span class="sxs-lookup"><span data-stu-id="51f1b-118">Represents a UTF-7 encoding of Unicode characters.</span></span>|  
|<xref:System.Text.UTF8Encoding>|<span data-ttu-id="51f1b-119">Představuje kódování znaků Unicode UTF-8.</span><span class="sxs-lookup"><span data-stu-id="51f1b-119">Represents a UTF-8 encoding of Unicode characters.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="51f1b-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="51f1b-120">See Also</span></span>  
 [<span data-ttu-id="51f1b-121">Čtení ze souborů</span><span class="sxs-lookup"><span data-stu-id="51f1b-121">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 [<span data-ttu-id="51f1b-122">Zápis do souborů</span><span class="sxs-lookup"><span data-stu-id="51f1b-122">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
