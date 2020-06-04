---
title: Kódování souborů
ms.date: 07/20/2015
helpviewer_keywords:
- character encodings
- files [Visual Basic], encoding
- Unicode, file encoding
- file encoding
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
ms.openlocfilehash: f906b2f2d747a7950c70a24549bbf5423e5b87b4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401742"
---
# <a name="file-encodings-visual-basic"></a><span data-ttu-id="157a6-102">Kódování souborů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="157a6-102">File Encodings (Visual Basic)</span></span>

<span data-ttu-id="157a6-103">Kódování souborů, označovaná také jako kódování znaků, určují způsob reprezentace znaků při zpracování textu.</span><span class="sxs-lookup"><span data-stu-id="157a6-103">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="157a6-104">Jedno kódování může být vhodnější než jiné, a to z toho smyslu, které znaky jazyka může nebo nemůže zpracovat, i když je obvykle upřednostňovaný Unicode.</span><span class="sxs-lookup"><span data-stu-id="157a6-104">One encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span>

<span data-ttu-id="157a6-105">Při čtení nebo zapisování do souborů může nesprávně odpovídat kódování souborů způsobit výjimky nebo nesprávné výsledky.</span><span class="sxs-lookup"><span data-stu-id="157a6-105">When reading from or writing to files, improperly matching file encodings may result in exceptions or incorrect results.</span></span>

## <a name="types-of-encodings"></a><span data-ttu-id="157a6-106">Typy kódování</span><span class="sxs-lookup"><span data-stu-id="157a6-106">Types of Encodings</span></span>

<span data-ttu-id="157a6-107">Unicode je preferované kódování při práci se soubory.</span><span class="sxs-lookup"><span data-stu-id="157a6-107">Unicode is the preferred encoding when working with files.</span></span> <span data-ttu-id="157a6-108">Unicode je celosvětový standard kódování znaků, který používá 16bitové hodnoty kódu pro reprezentaci všech znaků používaných v moderních výpočetních prostředích, včetně technických symbolů a speciálních znaků používaných při publikování.</span><span class="sxs-lookup"><span data-stu-id="157a6-108">Unicode is a worldwide character-encoding standard that uses 16-bit code values to represent all the characters used in modern computing, including technical symbols and special characters used in publishing.</span></span>

<span data-ttu-id="157a6-109">Předchozí standardy kódování znaků se skládají z tradičních znakových sad, jako je například znaková sada Windows ANSI, která používá 8bitové hodnoty kódu, nebo kombinace 8 bitových hodnot, které reprezentují znaky používané v konkrétním jazyce nebo geografické oblasti.</span><span class="sxs-lookup"><span data-stu-id="157a6-109">Previous character-encoding standards consisted of traditional character sets, such as the Windows ANSI character set that uses 8-bit code values, or combinations of 8-bit values, to represent the characters used in a specific language or geographical region.</span></span>

## <a name="encoding-class"></a><span data-ttu-id="157a6-110">Encoding – třída</span><span class="sxs-lookup"><span data-stu-id="157a6-110">Encoding Class</span></span>

<span data-ttu-id="157a6-111"><xref:System.Text.Encoding>Třída představuje kódování znaků.</span><span class="sxs-lookup"><span data-stu-id="157a6-111">The <xref:System.Text.Encoding> class represents a character encoding.</span></span> <span data-ttu-id="157a6-112">Tato tabulka uvádí typy dostupných kódování a popisuje je.</span><span class="sxs-lookup"><span data-stu-id="157a6-112">This table lists the type of encodings available and describes each.</span></span>

|<span data-ttu-id="157a6-113">Name</span><span class="sxs-lookup"><span data-stu-id="157a6-113">Name</span></span>|<span data-ttu-id="157a6-114">Description</span><span class="sxs-lookup"><span data-stu-id="157a6-114">Description</span></span>|
|---|---|
|<xref:System.Text.ASCIIEncoding>|<span data-ttu-id="157a6-115">Představuje kódování znaků ASCII znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="157a6-115">Represents an ASCII character encoding of Unicode characters.</span></span>|
|<xref:System.Text.UnicodeEncoding>|<span data-ttu-id="157a6-116">Představuje kódování UTF-16 znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="157a6-116">Represents a UTF-16 encoding of Unicode characters.</span></span>|
|<xref:System.Text.UTF32Encoding>|<span data-ttu-id="157a6-117">Představuje kódování UTF-32 znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="157a6-117">Represents a UTF-32 encoding of Unicode characters.</span></span>|
|<xref:System.Text.UTF7Encoding>|<span data-ttu-id="157a6-118">Představuje kódování UTF-7 znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="157a6-118">Represents a UTF-7 encoding of Unicode characters.</span></span>|
|<xref:System.Text.UTF8Encoding>|<span data-ttu-id="157a6-119">Představuje kódování UTF-8 znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="157a6-119">Represents a UTF-8 encoding of Unicode characters.</span></span>|

## <a name="see-also"></a><span data-ttu-id="157a6-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="157a6-120">See also</span></span>

- [<span data-ttu-id="157a6-121">Čtení ze souborů</span><span class="sxs-lookup"><span data-stu-id="157a6-121">Reading from Files</span></span>](reading-from-files.md)
- [<span data-ttu-id="157a6-122">Zápis do souborů</span><span class="sxs-lookup"><span data-stu-id="157a6-122">Writing to Files</span></span>](writing-to-files.md)
