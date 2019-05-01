---
title: Přístup k souborům v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- file access
- files [Visual Basic], input and output
- file access, Visual Basic
- files [Visual Basic], I/O
- file I/O classes
- data [Visual Basic], accessing from files
- files [Visual Basic], accessing
- file access, using components
- My.Computer.FileSystem object, accessing files
- I/O [Visual Basic]
- sequential access
ms.assetid: 231533bf-d049-4345-befa-3fb78fe6517d
ms.openlocfilehash: f9cbb255dea8c6915951b5099f40bfd0ba66c8aa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61960290"
---
# <a name="file-access-with-visual-basic"></a><span data-ttu-id="82c9e-102">Přístup k souborům v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="82c9e-102">File Access with Visual Basic</span></span>
<span data-ttu-id="82c9e-103">`My.Computer.FileSystem` Objekt poskytuje nástroje pro práci se soubory a složky.</span><span class="sxs-lookup"><span data-stu-id="82c9e-103">The `My.Computer.FileSystem` object provides tools for working with files and folders.</span></span> <span data-ttu-id="82c9e-104">Jeho vlastnosti, metody a události vám umožňují vytvořit, kopírovat, přesunout, prozkoumat a odstraňování souborů a složek.</span><span class="sxs-lookup"><span data-stu-id="82c9e-104">Its properties, methods, and events allow you to create, copy, move, investigate, and delete files and folders.</span></span> <span data-ttu-id="82c9e-105">`My.Computer.FileSystem` poskytuje lepší výkon než starší verze funkcí (`FileOpen`, `FileClose`, `Input`, `InputString`, `LineInput`atd), které jsou k dispozici v jazyce Visual Basic z důvodu zpětné kompatibility.</span><span class="sxs-lookup"><span data-stu-id="82c9e-105">`My.Computer.FileSystem` provides better performance than the legacy functions (`FileOpen`, `FileClose`, `Input`, `InputString`, `LineInput`, etc.) that are provided by Visual Basic for backward compatibility.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="82c9e-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="82c9e-106">In This Section</span></span>  
 [<span data-ttu-id="82c9e-107">Čtení ze souborů</span><span class="sxs-lookup"><span data-stu-id="82c9e-107">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 <span data-ttu-id="82c9e-108">Obsahuje témata týkající se použití `My.Computer.FileSystem` objektu určeného ke čtení ze souborů</span><span class="sxs-lookup"><span data-stu-id="82c9e-108">Lists topics dealing with using the `My.Computer.FileSystem` object to read from files</span></span>  
  
 [<span data-ttu-id="82c9e-109">Zápis do souborů</span><span class="sxs-lookup"><span data-stu-id="82c9e-109">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)  
 <span data-ttu-id="82c9e-110">Obsahuje témata týkající se použití `My.Computer.FileSystem` objekt k zápisu do souborů</span><span class="sxs-lookup"><span data-stu-id="82c9e-110">Lists topics dealing with using the `My.Computer.FileSystem` object to write to files</span></span>  
  
 [<span data-ttu-id="82c9e-111">Vytváření, odstraňování a přesouvání souborů a adresářů</span><span class="sxs-lookup"><span data-stu-id="82c9e-111">Creating, Deleting, and Moving Files and Directories</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)  
 <span data-ttu-id="82c9e-112">Obsahuje témata týkající se použití `My.Computer.FileSystem` objektu pro vytváření, kopírování, odstraňování a přesouvání souborů a složek.</span><span class="sxs-lookup"><span data-stu-id="82c9e-112">Lists topics dealing with using the `My.Computer.FileSystem` object to creating, copying, deleting and moving files and folders.</span></span>  
  
 [<span data-ttu-id="82c9e-113">Analýza textových souborů pomocí objektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="82c9e-113">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)  
 <span data-ttu-id="82c9e-114">Tento článek popisuje způsob použití `TextFieldReader` analyzovat textové soubory, jako jsou protokoly.</span><span class="sxs-lookup"><span data-stu-id="82c9e-114">Discusses how to use the `TextFieldReader` to parse text files such as logs.</span></span>  
  
 [<span data-ttu-id="82c9e-115">Kódování souborů</span><span class="sxs-lookup"><span data-stu-id="82c9e-115">File Encodings</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)  
 <span data-ttu-id="82c9e-116">Popisuje kódování souborů a jejich použití.</span><span class="sxs-lookup"><span data-stu-id="82c9e-116">Describes file encodings and their use.</span></span>  
  
 [<span data-ttu-id="82c9e-117">Návod: Práce se soubory a adresáře v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="82c9e-117">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 <span data-ttu-id="82c9e-118">Ukazuje, jak vytvořit nástroj, který hlásí informace o souborech a složkách.</span><span class="sxs-lookup"><span data-stu-id="82c9e-118">Demonstrates how to create a utility that reports information about files and folders.</span></span>  
  
 [<span data-ttu-id="82c9e-119">Odstraňování potíží: Čtení a zápis do textových souborů</span><span class="sxs-lookup"><span data-stu-id="82c9e-119">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)  
 <span data-ttu-id="82c9e-120">Uvádí běžné problémy vzniklé při čtení a zápis do textových souborů a navrhne nápravná opatření pro každý.</span><span class="sxs-lookup"><span data-stu-id="82c9e-120">Lists common problems encountered when reading and writing to text files, and suggests remedies for each.</span></span>
