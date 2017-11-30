---
title: "Řešení potíží: čtení a zápis do textových souborů (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- troubleshooting file I/O
- writing text to files [Visual Basic], troubleshooting
- troubleshooting Visual Basic, text files
- I/O [Visual Basic], troubleshooting text files
- writing to files [Visual Basic], troubleshooting
- reading text files [Visual Basic], troubleshooting
ms.assetid: a8e9b44d-facb-4718-8c0f-466537171182
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e836f79cd05dbaa180cc7bf5413ce57004e3500b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="troubleshooting-reading-from-and-writing-to-text-files-visual-basic"></a><span data-ttu-id="6af24-102">Řešení potíží: čtení a zápis do textových souborů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6af24-102">Troubleshooting: reading from and writing to text files (Visual Basic)</span></span>
<span data-ttu-id="6af24-103">Toto téma popisuje běžné problémy při práci s textem soubory a navrhne jejich řešení.</span><span class="sxs-lookup"><span data-stu-id="6af24-103">This topic discusses common problems encountered when working with text files and suggests an approach to each.</span></span>  
  
## <a name="common-problems"></a><span data-ttu-id="6af24-104">Běžné problémy</span><span class="sxs-lookup"><span data-stu-id="6af24-104">Common problems</span></span>  
 <span data-ttu-id="6af24-105">Většina běžných potíží při práci s textovými soubory zahrnovat výjimky zabezpečení, kódování souborů nebo neplatné cesty.</span><span class="sxs-lookup"><span data-stu-id="6af24-105">The most common issues encountered when working with text files include security exceptions, file encodings, or invalid paths.</span></span>  
  
### <a name="security-exceptions"></a><span data-ttu-id="6af24-106">Výjimky zabezpečení</span><span class="sxs-lookup"><span data-stu-id="6af24-106">Security exceptions</span></span>  
 <span data-ttu-id="6af24-107">A <xref:System.Security.SecurityException> se vyvolá, když dojde k chybě zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="6af24-107">A <xref:System.Security.SecurityException> is thrown when a security error occurs.</span></span> <span data-ttu-id="6af24-108">Toto je často výsledek nedostatečných oprávnění, což může být vyřešen přidáním oprávnění nebo práce se soubory v izolovaném úložišti uživatele.</span><span class="sxs-lookup"><span data-stu-id="6af24-108">This is often a result of the user lacking necessary permissions, which may be solved by adding permissions or working with files in isolated storage.</span></span>  
  
### <a name="file-encodings"></a><span data-ttu-id="6af24-109">Kódování souborů</span><span class="sxs-lookup"><span data-stu-id="6af24-109">File encodings</span></span>  
 <span data-ttu-id="6af24-110">Kódování souborů, také známé jako kódování znaků, určete, jak představují znaky při zpracování textu.</span><span class="sxs-lookup"><span data-stu-id="6af24-110">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="6af24-111">Neočekávané znaků v textovém souboru může být důsledkem nesprávné kódování.</span><span class="sxs-lookup"><span data-stu-id="6af24-111">Unexpected characters in a text file may result from incorrect encoding.</span></span> <span data-ttu-id="6af24-112">Většina souborů jeden kódování může být vhodnější než oproti jinému z hlediska jazykové symboly může nebo nemůže zpracovat, i když je obvykle upřednostňované kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="6af24-112">For most files, one encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span> <span data-ttu-id="6af24-113">Další informace najdete v tématu [kódování souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) a <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="6af24-113">For more information, see [File Encodings](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) and <xref:System.Text.Encoding>.</span></span>  
  
### <a name="incorrect-paths"></a><span data-ttu-id="6af24-114">Nesprávné cesty</span><span class="sxs-lookup"><span data-stu-id="6af24-114">Incorrect paths</span></span>  
 <span data-ttu-id="6af24-115">Při analýze cesty k souborům, zejména relativní cesty, je snadné k poskytování chybná data.</span><span class="sxs-lookup"><span data-stu-id="6af24-115">When parsing file paths, particularly relative paths, it is easy to supply the wrong data.</span></span> <span data-ttu-id="6af24-116">Mnoho problémů může být vyřešen tím, že zajistí, že zadáváte správnou cestu.</span><span class="sxs-lookup"><span data-stu-id="6af24-116">Many problems can be corrected by making sure you are supplying the correct path.</span></span> <span data-ttu-id="6af24-117">Další informace najdete v tématu [postupy: Analýza cest k souborům](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).</span><span class="sxs-lookup"><span data-stu-id="6af24-117">For more information, see [How to: Parse File Paths](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6af24-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="6af24-118">See also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 [<span data-ttu-id="6af24-119">Čtení ze souborů</span><span class="sxs-lookup"><span data-stu-id="6af24-119">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 [<span data-ttu-id="6af24-120">Zápis do souborů</span><span class="sxs-lookup"><span data-stu-id="6af24-120">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)  
 [<span data-ttu-id="6af24-121">Analýza textových souborů pomocí objektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="6af24-121">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
