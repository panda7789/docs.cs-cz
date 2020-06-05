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
ms.openlocfilehash: 8af4160d09f39f2622a007aef793173d614a8b44
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406622"
---
# <a name="troubleshooting-reading-from-and-writing-to-text-files-visual-basic"></a><span data-ttu-id="32a66-102">Řešení potíží: čtení z textových souborů a zápis do nich (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="32a66-102">Troubleshooting: reading from and writing to text files (Visual Basic)</span></span>

<span data-ttu-id="32a66-103">Toto téma popisuje běžné problémy zjištěné při práci s textovými soubory a navrhuje přístup k jednotlivým.</span><span class="sxs-lookup"><span data-stu-id="32a66-103">This topic discusses common problems encountered when working with text files and suggests an approach to each.</span></span>  
  
## <a name="common-problems"></a><span data-ttu-id="32a66-104">Běžné problémy</span><span class="sxs-lookup"><span data-stu-id="32a66-104">Common problems</span></span>  

 <span data-ttu-id="32a66-105">Nejběžnější problémy, ke kterým došlo při práci s textovými soubory, zahrnují výjimky zabezpečení, kódování souborů nebo neplatné cesty.</span><span class="sxs-lookup"><span data-stu-id="32a66-105">The most common issues encountered when working with text files include security exceptions, file encodings, or invalid paths.</span></span>  
  
### <a name="security-exceptions"></a><span data-ttu-id="32a66-106">Výjimky zabezpečení</span><span class="sxs-lookup"><span data-stu-id="32a66-106">Security exceptions</span></span>  

 <span data-ttu-id="32a66-107"><xref:System.Security.SecurityException>Výjimka je vyvolána, když dojde k chybě zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="32a66-107">A <xref:System.Security.SecurityException> is thrown when a security error occurs.</span></span> <span data-ttu-id="32a66-108">To často vede k tomu, že uživatel nemá potřebná oprávnění, která se můžou vyřešit přidáváním oprávnění nebo práci se soubory v izolovaném úložišti.</span><span class="sxs-lookup"><span data-stu-id="32a66-108">This is often a result of the user lacking necessary permissions, which may be solved by adding permissions or working with files in isolated storage.</span></span>  
  
### <a name="file-encodings"></a><span data-ttu-id="32a66-109">Kódování souborů</span><span class="sxs-lookup"><span data-stu-id="32a66-109">File encodings</span></span>  

 <span data-ttu-id="32a66-110">Kódování souborů, označovaná také jako kódování znaků, určují způsob reprezentace znaků při zpracování textu.</span><span class="sxs-lookup"><span data-stu-id="32a66-110">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="32a66-111">Neočekávané znaky v textovém souboru mohou být způsobeny nesprávným kódováním.</span><span class="sxs-lookup"><span data-stu-id="32a66-111">Unexpected characters in a text file may result from incorrect encoding.</span></span> <span data-ttu-id="32a66-112">U většiny souborů může být jedno kódování vhodnější než jiné z důvodu toho, které znaky jazyka může nebo nemůže zpracovat, i když je standardu Unicode obvykle upřednostňovaný.</span><span class="sxs-lookup"><span data-stu-id="32a66-112">For most files, one encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span> <span data-ttu-id="32a66-113">Další informace naleznete v tématu [kódování souborů](file-encodings.md) a <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="32a66-113">For more information, see [File Encodings](file-encodings.md) and <xref:System.Text.Encoding>.</span></span>  
  
### <a name="incorrect-paths"></a><span data-ttu-id="32a66-114">Nesprávné cesty</span><span class="sxs-lookup"><span data-stu-id="32a66-114">Incorrect paths</span></span>  

 <span data-ttu-id="32a66-115">Při analýze cest k souborům, zejména relativních cest, je snadné zadávat nesprávná data.</span><span class="sxs-lookup"><span data-stu-id="32a66-115">When parsing file paths, particularly relative paths, it is easy to supply the wrong data.</span></span> <span data-ttu-id="32a66-116">Mnohé problémy se dají opravit tím, že zadáte správnou cestu.</span><span class="sxs-lookup"><span data-stu-id="32a66-116">Many problems can be corrected by making sure you are supplying the correct path.</span></span> <span data-ttu-id="32a66-117">Další informace najdete v tématu [Postup: analýza cest k souborům](how-to-parse-file-paths.md).</span><span class="sxs-lookup"><span data-stu-id="32a66-117">For more information, see [How to: Parse File Paths](how-to-parse-file-paths.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32a66-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="32a66-118">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [<span data-ttu-id="32a66-119">Čtení ze souborů</span><span class="sxs-lookup"><span data-stu-id="32a66-119">Reading from Files</span></span>](reading-from-files.md)
- [<span data-ttu-id="32a66-120">Zápis do souborů</span><span class="sxs-lookup"><span data-stu-id="32a66-120">Writing to Files</span></span>](writing-to-files.md)
- [<span data-ttu-id="32a66-121">Analýza textových souborů pomocí objektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="32a66-121">Parsing Text Files with the TextFieldParser Object</span></span>](parsing-text-files-with-the-textfieldparser-object.md)
