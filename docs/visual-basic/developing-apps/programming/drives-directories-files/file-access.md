---
title: Přístup k souborům
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
ms.openlocfilehash: 22bcd0f1f3acb0c0ad899b83ad2d879ead948f12
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348898"
---
# <a name="file-access-with-visual-basic"></a><span data-ttu-id="73ca8-102">Přístup k souborům v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="73ca8-102">File Access with Visual Basic</span></span>

<span data-ttu-id="73ca8-103">Objekt `My.Computer.FileSystem` poskytuje nástroje pro práci se soubory a složkami.</span><span class="sxs-lookup"><span data-stu-id="73ca8-103">The `My.Computer.FileSystem` object provides tools for working with files and folders.</span></span> <span data-ttu-id="73ca8-104">Jeho vlastnosti, metody a události umožňují vytvářet, kopírovat, přesouvat, zkoumat a odstraňovat soubory a složky.</span><span class="sxs-lookup"><span data-stu-id="73ca8-104">Its properties, methods, and events allow you to create, copy, move, investigate, and delete files and folders.</span></span> <span data-ttu-id="73ca8-105">`My.Computer.FileSystem`poskytuje lepší výkon než`FileOpen`starší `FileClose` `Input`funkce `InputString` `LineInput`( , , , , , , atd.), které jsou poskytovány v jazyce Visual Basic pro zpětnou kompatibilitu.</span><span class="sxs-lookup"><span data-stu-id="73ca8-105">`My.Computer.FileSystem` provides better performance than the legacy functions (`FileOpen`, `FileClose`, `Input`, `InputString`, `LineInput`, etc.) that are provided by Visual Basic for backward compatibility.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="73ca8-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="73ca8-106">In This Section</span></span>  

 [<span data-ttu-id="73ca8-107">Čtení ze souborů</span><span class="sxs-lookup"><span data-stu-id="73ca8-107">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 <span data-ttu-id="73ca8-108">Uvádí témata týkající `My.Computer.FileSystem` se použití objektu ke čtení ze souborů.</span><span class="sxs-lookup"><span data-stu-id="73ca8-108">Lists topics dealing with using the `My.Computer.FileSystem` object to read from files</span></span>  
  
 [<span data-ttu-id="73ca8-109">Zápis do souborů</span><span class="sxs-lookup"><span data-stu-id="73ca8-109">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)  
 <span data-ttu-id="73ca8-110">Uvádí témata týkající `My.Computer.FileSystem` se použití objektu k zápisu do souborů.</span><span class="sxs-lookup"><span data-stu-id="73ca8-110">Lists topics dealing with using the `My.Computer.FileSystem` object to write to files</span></span>  
  
 [<span data-ttu-id="73ca8-111">Vytváření, odstraňování a přesouvání souborů a adresářů</span><span class="sxs-lookup"><span data-stu-id="73ca8-111">Creating, Deleting, and Moving Files and Directories</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)  
 <span data-ttu-id="73ca8-112">Uvádí témata týkající `My.Computer.FileSystem` se použití objektu k vytváření, kopírování, mazání a přesouvání souborů a složek.</span><span class="sxs-lookup"><span data-stu-id="73ca8-112">Lists topics dealing with using the `My.Computer.FileSystem` object to creating, copying, deleting and moving files and folders.</span></span>  
  
 [<span data-ttu-id="73ca8-113">Analýza textových souborů pomocí objektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="73ca8-113">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)  
 <span data-ttu-id="73ca8-114">Popisuje, jak pomocí `TextFieldReader` analyzovat textové soubory, jako jsou protokoly.</span><span class="sxs-lookup"><span data-stu-id="73ca8-114">Discusses how to use the `TextFieldReader` to parse text files such as logs.</span></span>  
  
 [<span data-ttu-id="73ca8-115">Kódování souborů</span><span class="sxs-lookup"><span data-stu-id="73ca8-115">File Encodings</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)  
 <span data-ttu-id="73ca8-116">Popisuje kódování souborů a jejich použití.</span><span class="sxs-lookup"><span data-stu-id="73ca8-116">Describes file encodings and their use.</span></span>  
  
 [<span data-ttu-id="73ca8-117">Návod: Práce se soubory a adresáři v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="73ca8-117">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 <span data-ttu-id="73ca8-118">Ukazuje, jak vytvořit nástroj, který hlásí informace o souborech a složkách.</span><span class="sxs-lookup"><span data-stu-id="73ca8-118">Demonstrates how to create a utility that reports information about files and folders.</span></span>  
  
 [<span data-ttu-id="73ca8-119">Řešení potíží: Čtení z textových souborů a zápis do nich</span><span class="sxs-lookup"><span data-stu-id="73ca8-119">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)  
 <span data-ttu-id="73ca8-120">Uvádí běžné problémy, ke kterým došlo při čtení a zápisu do textových souborů, a navrhuje opravné prostředky pro každý z nich.</span><span class="sxs-lookup"><span data-stu-id="73ca8-120">Lists common problems encountered when reading and writing to text files, and suggests remedies for each.</span></span>
