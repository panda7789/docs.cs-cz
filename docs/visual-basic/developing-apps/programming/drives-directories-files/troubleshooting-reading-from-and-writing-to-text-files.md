---
title: 'Troubleshooting: reading from and writing to text files'
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
# <a name="troubleshooting-reading-from-and-writing-to-text-files-visual-basic"></a><span data-ttu-id="6d3b5-102">Troubleshooting: reading from and writing to text files (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6d3b5-102">Troubleshooting: reading from and writing to text files (Visual Basic)</span></span>

<span data-ttu-id="6d3b5-103">This topic discusses common problems encountered when working with text files and suggests an approach to each.</span><span class="sxs-lookup"><span data-stu-id="6d3b5-103">This topic discusses common problems encountered when working with text files and suggests an approach to each.</span></span>  
  
## <a name="common-problems"></a><span data-ttu-id="6d3b5-104">Common problems</span><span class="sxs-lookup"><span data-stu-id="6d3b5-104">Common problems</span></span>  

 <span data-ttu-id="6d3b5-105">The most common issues encountered when working with text files include security exceptions, file encodings, or invalid paths.</span><span class="sxs-lookup"><span data-stu-id="6d3b5-105">The most common issues encountered when working with text files include security exceptions, file encodings, or invalid paths.</span></span>  
  
### <a name="security-exceptions"></a><span data-ttu-id="6d3b5-106">Security exceptions</span><span class="sxs-lookup"><span data-stu-id="6d3b5-106">Security exceptions</span></span>  

 <span data-ttu-id="6d3b5-107">A <xref:System.Security.SecurityException> is thrown when a security error occurs.</span><span class="sxs-lookup"><span data-stu-id="6d3b5-107">A <xref:System.Security.SecurityException> is thrown when a security error occurs.</span></span> <span data-ttu-id="6d3b5-108">This is often a result of the user lacking necessary permissions, which may be solved by adding permissions or working with files in isolated storage.</span><span class="sxs-lookup"><span data-stu-id="6d3b5-108">This is often a result of the user lacking necessary permissions, which may be solved by adding permissions or working with files in isolated storage.</span></span>  
  
### <a name="file-encodings"></a><span data-ttu-id="6d3b5-109">File encodings</span><span class="sxs-lookup"><span data-stu-id="6d3b5-109">File encodings</span></span>  

 <span data-ttu-id="6d3b5-110">File encodings, also known as character encodings, specify how to represent characters when text processing.</span><span class="sxs-lookup"><span data-stu-id="6d3b5-110">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="6d3b5-111">Unexpected characters in a text file may result from incorrect encoding.</span><span class="sxs-lookup"><span data-stu-id="6d3b5-111">Unexpected characters in a text file may result from incorrect encoding.</span></span> <span data-ttu-id="6d3b5-112">For most files, one encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span><span class="sxs-lookup"><span data-stu-id="6d3b5-112">For most files, one encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span> <span data-ttu-id="6d3b5-113">For more information, see [File Encodings](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) and <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="6d3b5-113">For more information, see [File Encodings](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) and <xref:System.Text.Encoding>.</span></span>  
  
### <a name="incorrect-paths"></a><span data-ttu-id="6d3b5-114">Incorrect paths</span><span class="sxs-lookup"><span data-stu-id="6d3b5-114">Incorrect paths</span></span>  

 <span data-ttu-id="6d3b5-115">When parsing file paths, particularly relative paths, it is easy to supply the wrong data.</span><span class="sxs-lookup"><span data-stu-id="6d3b5-115">When parsing file paths, particularly relative paths, it is easy to supply the wrong data.</span></span> <span data-ttu-id="6d3b5-116">Many problems can be corrected by making sure you are supplying the correct path.</span><span class="sxs-lookup"><span data-stu-id="6d3b5-116">Many problems can be corrected by making sure you are supplying the correct path.</span></span> <span data-ttu-id="6d3b5-117">For more information, see [How to: Parse File Paths](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).</span><span class="sxs-lookup"><span data-stu-id="6d3b5-117">For more information, see [How to: Parse File Paths](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d3b5-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6d3b5-118">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [<span data-ttu-id="6d3b5-119">Čtení ze souborů</span><span class="sxs-lookup"><span data-stu-id="6d3b5-119">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="6d3b5-120">Zápis do souborů</span><span class="sxs-lookup"><span data-stu-id="6d3b5-120">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
- [<span data-ttu-id="6d3b5-121">Analýza textových souborů pomocí objektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="6d3b5-121">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
