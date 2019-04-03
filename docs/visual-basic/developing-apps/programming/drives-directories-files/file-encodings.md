---
title: Kódování souborů (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- character encodings
- files [Visual Basic], encoding
- Unicode, file encoding
- file encoding
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
ms.openlocfilehash: c22e8046a8b88890f25bc6b671825eb6d68ec6b8
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814000"
---
# <a name="file-encodings-visual-basic"></a><span data-ttu-id="a2e82-102">Kódování souborů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2e82-102">File Encodings (Visual Basic)</span></span>
<span data-ttu-id="a2e82-103">Kódování souborů, označované také jako kódování znaků, určete, jak reprezentaci znaků při zpracování textu.</span><span class="sxs-lookup"><span data-stu-id="a2e82-103">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="a2e82-104">Kódování může být vhodnější před jiným z hlediska znaků jazyka může nebo nemůže zpracovat, i když je obvykle ve formátu Unicode.</span><span class="sxs-lookup"><span data-stu-id="a2e82-104">One encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span>  
  
 <span data-ttu-id="a2e82-105">Při čtení nebo zápis do souborů, nesprávně odpovídající kódování souborů může způsobit výjimky nebo nesprávné výsledky.</span><span class="sxs-lookup"><span data-stu-id="a2e82-105">When reading from or writing to files, improperly matching file encodings may result in exceptions or incorrect results.</span></span>  
  
## <a name="types-of-encodings"></a><span data-ttu-id="a2e82-106">Typy kódování</span><span class="sxs-lookup"><span data-stu-id="a2e82-106">Types of Encodings</span></span>  
 <span data-ttu-id="a2e82-107">Kódování Unicode je upřednostňovaný kódování při práci se soubory.</span><span class="sxs-lookup"><span data-stu-id="a2e82-107">Unicode is the preferred encoding when working with files.</span></span> <span data-ttu-id="a2e82-108">Kódování Unicode je po celém světě standard kódování znaků, která používá kód 16bitové hodnoty k reprezentaci všech znaků moderní výpočet, včetně technických symbolů a speciální znaky, které se používá při publikování.</span><span class="sxs-lookup"><span data-stu-id="a2e82-108">Unicode is a worldwide character-encoding standard that uses 16-bit code values to represent all the characters used in modern computing, including technical symbols and special characters used in publishing.</span></span>  
  
 <span data-ttu-id="a2e82-109">Předchozí standardy kódování znaků se skládal z tradičních znakových sad, jako je například znakovou sadu Windows ANSI, která používá kód 8bitové hodnoty nebo kombinace 8bitové hodnoty k reprezentaci znaků používaných pro konkrétní jazyk nebo geografické oblasti.</span><span class="sxs-lookup"><span data-stu-id="a2e82-109">Previous character-encoding standards consisted of traditional character sets, such as the Windows ANSI character set that uses 8-bit code values, or combinations of 8-bit values, to represent the characters used in a specific language or geographical region.</span></span>  
  
## <a name="encoding-class"></a><span data-ttu-id="a2e82-110">Kódování třídy</span><span class="sxs-lookup"><span data-stu-id="a2e82-110">Encoding Class</span></span>  
 <span data-ttu-id="a2e82-111"><xref:System.Text.Encoding> Třída představuje kódování znaků.</span><span class="sxs-lookup"><span data-stu-id="a2e82-111">The <xref:System.Text.Encoding> class represents a character encoding.</span></span> <span data-ttu-id="a2e82-112">Tato tabulka uvádí typ kódování, které jsou k dispozici a popisuje všechny.</span><span class="sxs-lookup"><span data-stu-id="a2e82-112">This table lists the type of encodings available and describes each.</span></span>  
  
|<span data-ttu-id="a2e82-113">Název</span><span class="sxs-lookup"><span data-stu-id="a2e82-113">Name</span></span>|<span data-ttu-id="a2e82-114">Popis</span><span class="sxs-lookup"><span data-stu-id="a2e82-114">Description</span></span>|
|---|---|    
|<xref:System.Text.ASCIIEncoding>|<span data-ttu-id="a2e82-115">Představuje kódování znaků ASCII znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="a2e82-115">Represents an ASCII character encoding of Unicode characters.</span></span>|  
|<xref:System.Text.UnicodeEncoding>|<span data-ttu-id="a2e82-116">Představuje kódování UTF-16 znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="a2e82-116">Represents a UTF-16 encoding of Unicode characters.</span></span>|  
|<xref:System.Text.UTF32Encoding>|<span data-ttu-id="a2e82-117">Představuje kódování UTF-32 znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="a2e82-117">Represents a UTF-32 encoding of Unicode characters.</span></span>|  
|<xref:System.Text.UTF7Encoding>|<span data-ttu-id="a2e82-118">Představuje kódování UTF-7 znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="a2e82-118">Represents a UTF-7 encoding of Unicode characters.</span></span>|  
|<xref:System.Text.UTF8Encoding>|<span data-ttu-id="a2e82-119">Představuje kódování UTF-8 znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="a2e82-119">Represents a UTF-8 encoding of Unicode characters.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a2e82-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a2e82-120">See also</span></span>

- [<span data-ttu-id="a2e82-121">Čtení ze souborů</span><span class="sxs-lookup"><span data-stu-id="a2e82-121">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="a2e82-122">Zápis do souborů</span><span class="sxs-lookup"><span data-stu-id="a2e82-122">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
