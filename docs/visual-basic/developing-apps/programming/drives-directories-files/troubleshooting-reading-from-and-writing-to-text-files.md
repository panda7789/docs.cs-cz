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
ms.openlocfilehash: cc0ec3c624fc4f47a0ef8594669ba120e6628e82
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54684395"
---
# <a name="troubleshooting-reading-from-and-writing-to-text-files-visual-basic"></a><span data-ttu-id="cefd2-102">Řešení potíží: čtení a zápis do textových souborů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cefd2-102">Troubleshooting: reading from and writing to text files (Visual Basic)</span></span>
<span data-ttu-id="cefd2-103">Toto téma popisuje běžné problémy vzniklé při práci s textem soubory a navrhne přístup ke každému.</span><span class="sxs-lookup"><span data-stu-id="cefd2-103">This topic discusses common problems encountered when working with text files and suggests an approach to each.</span></span>  
  
## <a name="common-problems"></a><span data-ttu-id="cefd2-104">Běžné problémy</span><span class="sxs-lookup"><span data-stu-id="cefd2-104">Common problems</span></span>  
 <span data-ttu-id="cefd2-105">Nejběžnějších problémů při práci s textovými soubory zahrnují bezpečnostním výjimkám, kódování souborů nebo neplatné cesty.</span><span class="sxs-lookup"><span data-stu-id="cefd2-105">The most common issues encountered when working with text files include security exceptions, file encodings, or invalid paths.</span></span>  
  
### <a name="security-exceptions"></a><span data-ttu-id="cefd2-106">Výjimky zabezpečení</span><span class="sxs-lookup"><span data-stu-id="cefd2-106">Security exceptions</span></span>  
 <span data-ttu-id="cefd2-107">A <xref:System.Security.SecurityException> je vyvolána, když dojde k chybě zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="cefd2-107">A <xref:System.Security.SecurityException> is thrown when a security error occurs.</span></span> <span data-ttu-id="cefd2-108">To je často důsledkem nedostatečných oprávnění, která může vyřešit přidáním oprávnění nebo práce se soubory v izolovaném úložišti uživatele.</span><span class="sxs-lookup"><span data-stu-id="cefd2-108">This is often a result of the user lacking necessary permissions, which may be solved by adding permissions or working with files in isolated storage.</span></span>  
  
### <a name="file-encodings"></a><span data-ttu-id="cefd2-109">Kódování souborů</span><span class="sxs-lookup"><span data-stu-id="cefd2-109">File encodings</span></span>  
 <span data-ttu-id="cefd2-110">Kódování souborů, označované také jako kódování znaků, určete, jak reprezentaci znaků při zpracování textu.</span><span class="sxs-lookup"><span data-stu-id="cefd2-110">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="cefd2-111">Z nesprávné kódování může způsobit neočekávané znaky do textového souboru.</span><span class="sxs-lookup"><span data-stu-id="cefd2-111">Unexpected characters in a text file may result from incorrect encoding.</span></span> <span data-ttu-id="cefd2-112">Pro většinu souborů kódování může být vhodnější před jiným z hlediska znaků jazyka může nebo nemůže zpracovat, i když je obvykle ve formátu Unicode.</span><span class="sxs-lookup"><span data-stu-id="cefd2-112">For most files, one encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span> <span data-ttu-id="cefd2-113">Další informace najdete v tématu [kódování souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) a <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="cefd2-113">For more information, see [File Encodings](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) and <xref:System.Text.Encoding>.</span></span>  
  
### <a name="incorrect-paths"></a><span data-ttu-id="cefd2-114">Nesprávné cesty</span><span class="sxs-lookup"><span data-stu-id="cefd2-114">Incorrect paths</span></span>  
 <span data-ttu-id="cefd2-115">Při analýze cesty k souborům, zejména relativní cesty, je snadné slouží k poskytování chybná data.</span><span class="sxs-lookup"><span data-stu-id="cefd2-115">When parsing file paths, particularly relative paths, it is easy to supply the wrong data.</span></span> <span data-ttu-id="cefd2-116">Mnoho problémů může být vyřešen a ujistěte se, že zadáváte správnou cestu.</span><span class="sxs-lookup"><span data-stu-id="cefd2-116">Many problems can be corrected by making sure you are supplying the correct path.</span></span> <span data-ttu-id="cefd2-117">Další informace najdete v tématu [jak: Analýza cest k souborům](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).</span><span class="sxs-lookup"><span data-stu-id="cefd2-117">For more information, see [How to: Parse File Paths](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cefd2-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cefd2-118">See also</span></span>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [<span data-ttu-id="cefd2-119">Čtení ze souborů</span><span class="sxs-lookup"><span data-stu-id="cefd2-119">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="cefd2-120">Zápis do souborů</span><span class="sxs-lookup"><span data-stu-id="cefd2-120">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
- [<span data-ttu-id="cefd2-121">Analýza textových souborů pomocí objektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="cefd2-121">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
