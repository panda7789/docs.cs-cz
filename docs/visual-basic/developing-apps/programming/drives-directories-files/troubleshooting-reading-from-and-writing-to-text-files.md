---
title: 'Řešení potíží: čtení a zápis do textových souborů (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting file I/O
- writing text to files [Visual Basic], troubleshooting
- troubleshooting Visual Basic, text files
- I/O [Visual Basic], troubleshooting text files
- writing to files [Visual Basic], troubleshooting
- reading text files [Visual Basic], troubleshooting
ms.assetid: a8e9b44d-facb-4718-8c0f-466537171182
ms.openlocfilehash: 5650298da99f8bc9a25c7d7ceea11a8a5bf968fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587523"
---
# <a name="troubleshooting-reading-from-and-writing-to-text-files-visual-basic"></a><span data-ttu-id="4a866-102">Řešení potíží: čtení a zápis do textových souborů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4a866-102">Troubleshooting: reading from and writing to text files (Visual Basic)</span></span>
<span data-ttu-id="4a866-103">Toto téma popisuje běžné problémy při práci s textem soubory a navrhne jejich řešení.</span><span class="sxs-lookup"><span data-stu-id="4a866-103">This topic discusses common problems encountered when working with text files and suggests an approach to each.</span></span>  
  
## <a name="common-problems"></a><span data-ttu-id="4a866-104">Běžné problémy</span><span class="sxs-lookup"><span data-stu-id="4a866-104">Common problems</span></span>  
 <span data-ttu-id="4a866-105">Většina běžných potíží při práci s textovými soubory zahrnovat výjimky zabezpečení, kódování souborů nebo neplatné cesty.</span><span class="sxs-lookup"><span data-stu-id="4a866-105">The most common issues encountered when working with text files include security exceptions, file encodings, or invalid paths.</span></span>  
  
### <a name="security-exceptions"></a><span data-ttu-id="4a866-106">Výjimky zabezpečení</span><span class="sxs-lookup"><span data-stu-id="4a866-106">Security exceptions</span></span>  
 <span data-ttu-id="4a866-107">A <xref:System.Security.SecurityException> se vyvolá, když dojde k chybě zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4a866-107">A <xref:System.Security.SecurityException> is thrown when a security error occurs.</span></span> <span data-ttu-id="4a866-108">Toto je často výsledek nedostatečných oprávnění, což může být vyřešen přidáním oprávnění nebo práce se soubory v izolovaném úložišti uživatele.</span><span class="sxs-lookup"><span data-stu-id="4a866-108">This is often a result of the user lacking necessary permissions, which may be solved by adding permissions or working with files in isolated storage.</span></span>  
  
### <a name="file-encodings"></a><span data-ttu-id="4a866-109">Kódování souborů</span><span class="sxs-lookup"><span data-stu-id="4a866-109">File encodings</span></span>  
 <span data-ttu-id="4a866-110">Kódování souborů, také známé jako kódování znaků, určete, jak představují znaky při zpracování textu.</span><span class="sxs-lookup"><span data-stu-id="4a866-110">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="4a866-111">Neočekávané znaků v textovém souboru může být důsledkem nesprávné kódování.</span><span class="sxs-lookup"><span data-stu-id="4a866-111">Unexpected characters in a text file may result from incorrect encoding.</span></span> <span data-ttu-id="4a866-112">Většina souborů jeden kódování může být vhodnější než oproti jinému z hlediska jazykové symboly může nebo nemůže zpracovat, i když je obvykle upřednostňované kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="4a866-112">For most files, one encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span> <span data-ttu-id="4a866-113">Další informace najdete v tématu [kódování souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) a <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="4a866-113">For more information, see [File Encodings](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) and <xref:System.Text.Encoding>.</span></span>  
  
### <a name="incorrect-paths"></a><span data-ttu-id="4a866-114">Nesprávné cesty</span><span class="sxs-lookup"><span data-stu-id="4a866-114">Incorrect paths</span></span>  
 <span data-ttu-id="4a866-115">Při analýze cesty k souborům, zejména relativní cesty, je snadné k poskytování chybná data.</span><span class="sxs-lookup"><span data-stu-id="4a866-115">When parsing file paths, particularly relative paths, it is easy to supply the wrong data.</span></span> <span data-ttu-id="4a866-116">Mnoho problémů může být vyřešen tím, že zajistí, že zadáváte správnou cestu.</span><span class="sxs-lookup"><span data-stu-id="4a866-116">Many problems can be corrected by making sure you are supplying the correct path.</span></span> <span data-ttu-id="4a866-117">Další informace najdete v tématu [postupy: Analýza cest k souborům](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).</span><span class="sxs-lookup"><span data-stu-id="4a866-117">For more information, see [How to: Parse File Paths](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a866-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="4a866-118">See also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 [<span data-ttu-id="4a866-119">Čtení ze souborů</span><span class="sxs-lookup"><span data-stu-id="4a866-119">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 [<span data-ttu-id="4a866-120">Zápis do souborů</span><span class="sxs-lookup"><span data-stu-id="4a866-120">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)  
 [<span data-ttu-id="4a866-121">Analýza textových souborů pomocí objektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="4a866-121">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
