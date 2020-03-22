---
title: Kódování souborů
ms.date: 07/20/2015
helpviewer_keywords:
- character encodings
- files [Visual Basic], encoding
- Unicode, file encoding
- file encoding
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
ms.openlocfilehash: 52770187568d0ba0f54ec36ee2c3d754a9b4d9a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348882"
---
# <a name="file-encodings-visual-basic"></a><span data-ttu-id="3b0e8-102">Kódování souborů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b0e8-102">File Encodings (Visual Basic)</span></span>

<span data-ttu-id="3b0e8-103">Kódování souborů, označované také jako kódování znaků, určují, jak mají při zpracování textu představovat znaky.</span><span class="sxs-lookup"><span data-stu-id="3b0e8-103">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="3b0e8-104">Jedno kódování může být vhodnější než jiné, pokud jde o jazyk, který může nebo nemůže zpracovat, ačkoli Unicode je obvykle upřednostňován.</span><span class="sxs-lookup"><span data-stu-id="3b0e8-104">One encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span>

<span data-ttu-id="3b0e8-105">Při čtení nebo zápisu do souborů může mít nesprávně odpovídající kódování souborů za následek výjimky nebo nesprávné výsledky.</span><span class="sxs-lookup"><span data-stu-id="3b0e8-105">When reading from or writing to files, improperly matching file encodings may result in exceptions or incorrect results.</span></span>

## <a name="types-of-encodings"></a><span data-ttu-id="3b0e8-106">Typy kódování</span><span class="sxs-lookup"><span data-stu-id="3b0e8-106">Types of Encodings</span></span>

<span data-ttu-id="3b0e8-107">Unicode je upřednostňované kódování při práci se soubory.</span><span class="sxs-lookup"><span data-stu-id="3b0e8-107">Unicode is the preferred encoding when working with files.</span></span> <span data-ttu-id="3b0e8-108">Unicode je celosvětový standard kódování znaků, který používá 16bitové kódové hodnoty k reprezentaci všech znaků používaných v moderním výpočetním prostředí, včetně technických symbolů a speciálních znaků používaných při publikování.</span><span class="sxs-lookup"><span data-stu-id="3b0e8-108">Unicode is a worldwide character-encoding standard that uses 16-bit code values to represent all the characters used in modern computing, including technical symbols and special characters used in publishing.</span></span>

<span data-ttu-id="3b0e8-109">Předchozí standardy kódování znaků se skládaly z tradičních znakových sad, jako je například znaková sada Systému Windows ANSI, která používá 8bitové kódové hodnoty nebo kombinace 8bitových hodnot k reprezentaci znaků používaných v určitém jazyce nebo zeměpisné oblasti.</span><span class="sxs-lookup"><span data-stu-id="3b0e8-109">Previous character-encoding standards consisted of traditional character sets, such as the Windows ANSI character set that uses 8-bit code values, or combinations of 8-bit values, to represent the characters used in a specific language or geographical region.</span></span>

## <a name="encoding-class"></a><span data-ttu-id="3b0e8-110">Třída kódování</span><span class="sxs-lookup"><span data-stu-id="3b0e8-110">Encoding Class</span></span>

<span data-ttu-id="3b0e8-111">Třída <xref:System.Text.Encoding> představuje kódování znaků.</span><span class="sxs-lookup"><span data-stu-id="3b0e8-111">The <xref:System.Text.Encoding> class represents a character encoding.</span></span> <span data-ttu-id="3b0e8-112">V této tabulce je uveden typ kódování, která jsou k dispozici, a popisuje každé kódování.</span><span class="sxs-lookup"><span data-stu-id="3b0e8-112">This table lists the type of encodings available and describes each.</span></span>

|<span data-ttu-id="3b0e8-113">Name (Název)</span><span class="sxs-lookup"><span data-stu-id="3b0e8-113">Name</span></span>|<span data-ttu-id="3b0e8-114">Popis</span><span class="sxs-lookup"><span data-stu-id="3b0e8-114">Description</span></span>|
|---|---|
|<xref:System.Text.ASCIIEncoding>|<span data-ttu-id="3b0e8-115">Představuje znak ASCII kódování znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="3b0e8-115">Represents an ASCII character encoding of Unicode characters.</span></span>|
|<xref:System.Text.UnicodeEncoding>|<span data-ttu-id="3b0e8-116">Představuje kódování UTF-16 znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="3b0e8-116">Represents a UTF-16 encoding of Unicode characters.</span></span>|
|<xref:System.Text.UTF32Encoding>|<span data-ttu-id="3b0e8-117">Představuje kódování UTF-32 znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="3b0e8-117">Represents a UTF-32 encoding of Unicode characters.</span></span>|
|<xref:System.Text.UTF7Encoding>|<span data-ttu-id="3b0e8-118">Představuje kódování UTF-7 znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="3b0e8-118">Represents a UTF-7 encoding of Unicode characters.</span></span>|
|<xref:System.Text.UTF8Encoding>|<span data-ttu-id="3b0e8-119">Představuje kódování UTF-8 znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="3b0e8-119">Represents a UTF-8 encoding of Unicode characters.</span></span>|

## <a name="see-also"></a><span data-ttu-id="3b0e8-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="3b0e8-120">See also</span></span>

- [<span data-ttu-id="3b0e8-121">Čtení ze souborů</span><span class="sxs-lookup"><span data-stu-id="3b0e8-121">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="3b0e8-122">Zápis do souborů</span><span class="sxs-lookup"><span data-stu-id="3b0e8-122">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
