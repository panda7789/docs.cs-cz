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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348882"
---
# <a name="file-encodings-visual-basic"></a><span data-ttu-id="51a73-102">Kódování souborů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="51a73-102">File Encodings (Visual Basic)</span></span>

<span data-ttu-id="51a73-103">File encodings, also known as character encodings, specify how to represent characters when text processing.</span><span class="sxs-lookup"><span data-stu-id="51a73-103">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="51a73-104">One encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span><span class="sxs-lookup"><span data-stu-id="51a73-104">One encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span>

<span data-ttu-id="51a73-105">When reading from or writing to files, improperly matching file encodings may result in exceptions or incorrect results.</span><span class="sxs-lookup"><span data-stu-id="51a73-105">When reading from or writing to files, improperly matching file encodings may result in exceptions or incorrect results.</span></span>

## <a name="types-of-encodings"></a><span data-ttu-id="51a73-106">Types of Encodings</span><span class="sxs-lookup"><span data-stu-id="51a73-106">Types of Encodings</span></span>

<span data-ttu-id="51a73-107">Unicode is the preferred encoding when working with files.</span><span class="sxs-lookup"><span data-stu-id="51a73-107">Unicode is the preferred encoding when working with files.</span></span> <span data-ttu-id="51a73-108">Unicode is a worldwide character-encoding standard that uses 16-bit code values to represent all the characters used in modern computing, including technical symbols and special characters used in publishing.</span><span class="sxs-lookup"><span data-stu-id="51a73-108">Unicode is a worldwide character-encoding standard that uses 16-bit code values to represent all the characters used in modern computing, including technical symbols and special characters used in publishing.</span></span>

<span data-ttu-id="51a73-109">Previous character-encoding standards consisted of traditional character sets, such as the Windows ANSI character set that uses 8-bit code values, or combinations of 8-bit values, to represent the characters used in a specific language or geographical region.</span><span class="sxs-lookup"><span data-stu-id="51a73-109">Previous character-encoding standards consisted of traditional character sets, such as the Windows ANSI character set that uses 8-bit code values, or combinations of 8-bit values, to represent the characters used in a specific language or geographical region.</span></span>

## <a name="encoding-class"></a><span data-ttu-id="51a73-110">Encoding Class</span><span class="sxs-lookup"><span data-stu-id="51a73-110">Encoding Class</span></span>

<span data-ttu-id="51a73-111">The <xref:System.Text.Encoding> class represents a character encoding.</span><span class="sxs-lookup"><span data-stu-id="51a73-111">The <xref:System.Text.Encoding> class represents a character encoding.</span></span> <span data-ttu-id="51a73-112">This table lists the type of encodings available and describes each.</span><span class="sxs-lookup"><span data-stu-id="51a73-112">This table lists the type of encodings available and describes each.</span></span>

|<span data-ttu-id="51a73-113">Name</span><span class="sxs-lookup"><span data-stu-id="51a73-113">Name</span></span>|<span data-ttu-id="51a73-114">Popis</span><span class="sxs-lookup"><span data-stu-id="51a73-114">Description</span></span>|
|---|---|
|<xref:System.Text.ASCIIEncoding>|<span data-ttu-id="51a73-115">Represents an ASCII character encoding of Unicode characters.</span><span class="sxs-lookup"><span data-stu-id="51a73-115">Represents an ASCII character encoding of Unicode characters.</span></span>|
|<xref:System.Text.UnicodeEncoding>|<span data-ttu-id="51a73-116">Represents a UTF-16 encoding of Unicode characters.</span><span class="sxs-lookup"><span data-stu-id="51a73-116">Represents a UTF-16 encoding of Unicode characters.</span></span>|
|<xref:System.Text.UTF32Encoding>|<span data-ttu-id="51a73-117">Represents a UTF-32 encoding of Unicode characters.</span><span class="sxs-lookup"><span data-stu-id="51a73-117">Represents a UTF-32 encoding of Unicode characters.</span></span>|
|<xref:System.Text.UTF7Encoding>|<span data-ttu-id="51a73-118">Represents a UTF-7 encoding of Unicode characters.</span><span class="sxs-lookup"><span data-stu-id="51a73-118">Represents a UTF-7 encoding of Unicode characters.</span></span>|
|<xref:System.Text.UTF8Encoding>|<span data-ttu-id="51a73-119">Represents a UTF-8 encoding of Unicode characters.</span><span class="sxs-lookup"><span data-stu-id="51a73-119">Represents a UTF-8 encoding of Unicode characters.</span></span>|

## <a name="see-also"></a><span data-ttu-id="51a73-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="51a73-120">See also</span></span>

- [<span data-ttu-id="51a73-121">Čtení ze souborů</span><span class="sxs-lookup"><span data-stu-id="51a73-121">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="51a73-122">Zápis do souborů</span><span class="sxs-lookup"><span data-stu-id="51a73-122">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
