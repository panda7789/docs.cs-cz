---
title: 'Řešení potíží: čtení a zápis do textových souborů'
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting file I/O
- writing text to files [Visual Basic], troubleshooting
- troubleshooting Visual Basic, text files
- I/O [Visual Basic], troubleshooting text files
- writing to files [Visual Basic], troubleshooting
- reading text files [Visual Basic], troubleshooting
ms.assetid: a8e9b44d-facb-4718-8c0f-466537171182
ms.openlocfilehash: dbc53ca3cc9ae9b2d14b925f891d0409b2b7debd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74333789"
---
# <a name="troubleshooting-reading-from-and-writing-to-text-files-visual-basic"></a><span data-ttu-id="ceda1-102">Řešení potíží: čtení a zápis do textových souborů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ceda1-102">Troubleshooting: reading from and writing to text files (Visual Basic)</span></span>

<span data-ttu-id="ceda1-103">Toto téma popisuje běžné problémy při práci s textovými soubory a navrhuje přístup ke každému z nich.</span><span class="sxs-lookup"><span data-stu-id="ceda1-103">This topic discusses common problems encountered when working with text files and suggests an approach to each.</span></span>  
  
## <a name="common-problems"></a><span data-ttu-id="ceda1-104">Běžné problémy</span><span class="sxs-lookup"><span data-stu-id="ceda1-104">Common problems</span></span>  

 <span data-ttu-id="ceda1-105">Mezi nejčastější problémy při práci s textovými soubory patří výjimky zabezpečení, kódování souborů nebo neplatné cesty.</span><span class="sxs-lookup"><span data-stu-id="ceda1-105">The most common issues encountered when working with text files include security exceptions, file encodings, or invalid paths.</span></span>  
  
### <a name="security-exceptions"></a><span data-ttu-id="ceda1-106">Výjimky zabezpečení</span><span class="sxs-lookup"><span data-stu-id="ceda1-106">Security exceptions</span></span>  

 <span data-ttu-id="ceda1-107">A <xref:System.Security.SecurityException> je vyvolána, když dojde k chybě zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="ceda1-107">A <xref:System.Security.SecurityException> is thrown when a security error occurs.</span></span> <span data-ttu-id="ceda1-108">To je často důsledkem toho, že uživatel i min. nemá potřebná oprávnění, která mohou být vyřešena přidáním oprávnění nebo prací se soubory v izolovaném úložišti.</span><span class="sxs-lookup"><span data-stu-id="ceda1-108">This is often a result of the user lacking necessary permissions, which may be solved by adding permissions or working with files in isolated storage.</span></span>  
  
### <a name="file-encodings"></a><span data-ttu-id="ceda1-109">Kódování souborů</span><span class="sxs-lookup"><span data-stu-id="ceda1-109">File encodings</span></span>  

 <span data-ttu-id="ceda1-110">Kódování souborů, označované také jako kódování znaků, určují, jak mají při zpracování textu představovat znaky.</span><span class="sxs-lookup"><span data-stu-id="ceda1-110">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="ceda1-111">Neočekávané znaky v textovém souboru mohou být důsledkem nesprávného kódování.</span><span class="sxs-lookup"><span data-stu-id="ceda1-111">Unexpected characters in a text file may result from incorrect encoding.</span></span> <span data-ttu-id="ceda1-112">U většiny souborů může být jedno kódování vhodnější než jiné, pokud jde o znaky jazyka, které může nebo nemůže zpracovat, ačkoli unicode je obvykle upřednostňováno.</span><span class="sxs-lookup"><span data-stu-id="ceda1-112">For most files, one encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span> <span data-ttu-id="ceda1-113">Další informace naleznete v [tématu Kódování souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) a <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="ceda1-113">For more information, see [File Encodings](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) and <xref:System.Text.Encoding>.</span></span>  
  
### <a name="incorrect-paths"></a><span data-ttu-id="ceda1-114">Nesprávné cesty</span><span class="sxs-lookup"><span data-stu-id="ceda1-114">Incorrect paths</span></span>  

 <span data-ttu-id="ceda1-115">Při analýzě cest souboru, zejména relativní cesty, je snadné zadat nesprávná data.</span><span class="sxs-lookup"><span data-stu-id="ceda1-115">When parsing file paths, particularly relative paths, it is easy to supply the wrong data.</span></span> <span data-ttu-id="ceda1-116">Mnoho problémů lze opravit tím, že se ujistíte, že poskytujete správnou cestu.</span><span class="sxs-lookup"><span data-stu-id="ceda1-116">Many problems can be corrected by making sure you are supplying the correct path.</span></span> <span data-ttu-id="ceda1-117">Další informace naleznete v [tématu How to: Parse File Paths](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).</span><span class="sxs-lookup"><span data-stu-id="ceda1-117">For more information, see [How to: Parse File Paths](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceda1-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="ceda1-118">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [<span data-ttu-id="ceda1-119">Čtení ze souborů</span><span class="sxs-lookup"><span data-stu-id="ceda1-119">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="ceda1-120">Zápis do souborů</span><span class="sxs-lookup"><span data-stu-id="ceda1-120">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
- [<span data-ttu-id="ceda1-121">Analýza textových souborů pomocí objektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="ceda1-121">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
