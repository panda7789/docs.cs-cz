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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61960183"
---
# <a name="file-encodings-visual-basic"></a><span data-ttu-id="576d6-102">Kódování souborů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="576d6-102">File Encodings (Visual Basic)</span></span>
<span data-ttu-id="576d6-103">Kódování souborů, označované také jako kódování znaků, určete, jak reprezentaci znaků při zpracování textu.</span><span class="sxs-lookup"><span data-stu-id="576d6-103">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="576d6-104">Kódování může být vhodnější před jiným z hlediska znaků jazyka může nebo nemůže zpracovat, i když je obvykle ve formátu Unicode.</span><span class="sxs-lookup"><span data-stu-id="576d6-104">One encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span>  
  
 <span data-ttu-id="576d6-105">Při čtení nebo zápis do souborů, nesprávně odpovídající kódování souborů může způsobit výjimky nebo nesprávné výsledky.</span><span class="sxs-lookup"><span data-stu-id="576d6-105">When reading from or writing to files, improperly matching file encodings may result in exceptions or incorrect results.</span></span>  
  
## <a name="types-of-encodings"></a><span data-ttu-id="576d6-106">Typy kódování</span><span class="sxs-lookup"><span data-stu-id="576d6-106">Types of Encodings</span></span>  
 <span data-ttu-id="576d6-107">Kódování Unicode je upřednostňovaný kódování při práci se soubory.</span><span class="sxs-lookup"><span data-stu-id="576d6-107">Unicode is the preferred encoding when working with files.</span></span> <span data-ttu-id="576d6-108">Kódování Unicode je po celém světě standard kódování znaků, která používá kód 16bitové hodnoty k reprezentaci všech znaků moderní výpočet, včetně technických symbolů a speciální znaky, které se používá při publikování.</span><span class="sxs-lookup"><span data-stu-id="576d6-108">Unicode is a worldwide character-encoding standard that uses 16-bit code values to represent all the characters used in modern computing, including technical symbols and special characters used in publishing.</span></span>  
  
 <span data-ttu-id="576d6-109">Předchozí standardy kódování znaků se skládal z tradičních znakových sad, jako je například znakovou sadu Windows ANSI, která používá kód 8bitové hodnoty nebo kombinace 8bitové hodnoty k reprezentaci znaků používaných pro konkrétní jazyk nebo geografické oblasti.</span><span class="sxs-lookup"><span data-stu-id="576d6-109">Previous character-encoding standards consisted of traditional character sets, such as the Windows ANSI character set that uses 8-bit code values, or combinations of 8-bit values, to represent the characters used in a specific language or geographical region.</span></span>  
  
## <a name="encoding-class"></a><span data-ttu-id="576d6-110">Kódování třídy</span><span class="sxs-lookup"><span data-stu-id="576d6-110">Encoding Class</span></span>  
 <span data-ttu-id="576d6-111"><xref:System.Text.Encoding> Třída představuje kódování znaků.</span><span class="sxs-lookup"><span data-stu-id="576d6-111">The <xref:System.Text.Encoding> class represents a character encoding.</span></span> <span data-ttu-id="576d6-112">Tato tabulka uvádí typ kódování, které jsou k dispozici a popisuje všechny.</span><span class="sxs-lookup"><span data-stu-id="576d6-112">This table lists the type of encodings available and describes each.</span></span>  
  
|<span data-ttu-id="576d6-113">Název</span><span class="sxs-lookup"><span data-stu-id="576d6-113">Name</span></span>|<span data-ttu-id="576d6-114">Popis</span><span class="sxs-lookup"><span data-stu-id="576d6-114">Description</span></span>|
|---|---|    
|<xref:System.Text.ASCIIEncoding>|<span data-ttu-id="576d6-115">Představuje kódování znaků ASCII znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="576d6-115">Represents an ASCII character encoding of Unicode characters.</span></span>|  
|<xref:System.Text.UnicodeEncoding>|<span data-ttu-id="576d6-116">Představuje kódování UTF-16 znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="576d6-116">Represents a UTF-16 encoding of Unicode characters.</span></span>|  
|<xref:System.Text.UTF32Encoding>|<span data-ttu-id="576d6-117">Představuje kódování UTF-32 znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="576d6-117">Represents a UTF-32 encoding of Unicode characters.</span></span>|  
|<xref:System.Text.UTF7Encoding>|<span data-ttu-id="576d6-118">Představuje kódování UTF-7 znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="576d6-118">Represents a UTF-7 encoding of Unicode characters.</span></span>|  
|<xref:System.Text.UTF8Encoding>|<span data-ttu-id="576d6-119">Představuje kódování UTF-8 znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="576d6-119">Represents a UTF-8 encoding of Unicode characters.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="576d6-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="576d6-120">See also</span></span>

- [<span data-ttu-id="576d6-121">Čtení ze souborů</span><span class="sxs-lookup"><span data-stu-id="576d6-121">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="576d6-122">Zápis do souborů</span><span class="sxs-lookup"><span data-stu-id="576d6-122">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
