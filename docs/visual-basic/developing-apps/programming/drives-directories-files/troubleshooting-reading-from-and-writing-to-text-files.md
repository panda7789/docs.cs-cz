---
title: 'Řešení potíží: čtení z textových souborů a zápis do nich'
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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333789"
---
# <a name="troubleshooting-reading-from-and-writing-to-text-files-visual-basic"></a><span data-ttu-id="bbc09-102">Řešení potíží: čtení z textových souborů a zápis do nich (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bbc09-102">Troubleshooting: reading from and writing to text files (Visual Basic)</span></span>

<span data-ttu-id="bbc09-103">Toto téma popisuje běžné problémy zjištěné při práci s textovými soubory a navrhuje přístup k jednotlivým.</span><span class="sxs-lookup"><span data-stu-id="bbc09-103">This topic discusses common problems encountered when working with text files and suggests an approach to each.</span></span>  
  
## <a name="common-problems"></a><span data-ttu-id="bbc09-104">Běžné problémy</span><span class="sxs-lookup"><span data-stu-id="bbc09-104">Common problems</span></span>  

 <span data-ttu-id="bbc09-105">Nejběžnější problémy, ke kterým došlo při práci s textovými soubory, zahrnují výjimky zabezpečení, kódování souborů nebo neplatné cesty.</span><span class="sxs-lookup"><span data-stu-id="bbc09-105">The most common issues encountered when working with text files include security exceptions, file encodings, or invalid paths.</span></span>  
  
### <a name="security-exceptions"></a><span data-ttu-id="bbc09-106">Výjimky zabezpečení</span><span class="sxs-lookup"><span data-stu-id="bbc09-106">Security exceptions</span></span>  

 <span data-ttu-id="bbc09-107"><xref:System.Security.SecurityException> je vyvolána, když dojde k chybě zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="bbc09-107">A <xref:System.Security.SecurityException> is thrown when a security error occurs.</span></span> <span data-ttu-id="bbc09-108">To často vede k tomu, že uživatel nemá potřebná oprávnění, která se můžou vyřešit přidáváním oprávnění nebo práci se soubory v izolovaném úložišti.</span><span class="sxs-lookup"><span data-stu-id="bbc09-108">This is often a result of the user lacking necessary permissions, which may be solved by adding permissions or working with files in isolated storage.</span></span>  
  
### <a name="file-encodings"></a><span data-ttu-id="bbc09-109">Kódování souborů</span><span class="sxs-lookup"><span data-stu-id="bbc09-109">File encodings</span></span>  

 <span data-ttu-id="bbc09-110">Kódování souborů, označovaná také jako kódování znaků, určují způsob reprezentace znaků při zpracování textu.</span><span class="sxs-lookup"><span data-stu-id="bbc09-110">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="bbc09-111">Neočekávané znaky v textovém souboru mohou být způsobeny nesprávným kódováním.</span><span class="sxs-lookup"><span data-stu-id="bbc09-111">Unexpected characters in a text file may result from incorrect encoding.</span></span> <span data-ttu-id="bbc09-112">U většiny souborů může být jedno kódování vhodnější než jiné z důvodu toho, které znaky jazyka může nebo nemůže zpracovat, i když je standardu Unicode obvykle upřednostňovaný.</span><span class="sxs-lookup"><span data-stu-id="bbc09-112">For most files, one encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span> <span data-ttu-id="bbc09-113">Další informace najdete v tématu [kódování souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) a <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="bbc09-113">For more information, see [File Encodings](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) and <xref:System.Text.Encoding>.</span></span>  
  
### <a name="incorrect-paths"></a><span data-ttu-id="bbc09-114">Nesprávné cesty</span><span class="sxs-lookup"><span data-stu-id="bbc09-114">Incorrect paths</span></span>  

 <span data-ttu-id="bbc09-115">Při analýze cest k souborům, zejména relativních cest, je snadné zadávat nesprávná data.</span><span class="sxs-lookup"><span data-stu-id="bbc09-115">When parsing file paths, particularly relative paths, it is easy to supply the wrong data.</span></span> <span data-ttu-id="bbc09-116">Mnohé problémy se dají opravit tím, že zadáte správnou cestu.</span><span class="sxs-lookup"><span data-stu-id="bbc09-116">Many problems can be corrected by making sure you are supplying the correct path.</span></span> <span data-ttu-id="bbc09-117">Další informace najdete v tématu [Postup: analýza cest k souborům](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).</span><span class="sxs-lookup"><span data-stu-id="bbc09-117">For more information, see [How to: Parse File Paths](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbc09-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bbc09-118">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [<span data-ttu-id="bbc09-119">Čtení ze souborů</span><span class="sxs-lookup"><span data-stu-id="bbc09-119">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="bbc09-120">Zápis do souborů</span><span class="sxs-lookup"><span data-stu-id="bbc09-120">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
- [<span data-ttu-id="bbc09-121">Analýza textových souborů pomocí objektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="bbc09-121">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
