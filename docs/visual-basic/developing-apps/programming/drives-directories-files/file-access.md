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
ms.openlocfilehash: 3b2042862ae81a52d62374e35a456766ed47edc9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401729"
---
# <a name="file-access-with-visual-basic"></a><span data-ttu-id="9ce67-102">Přístup k souborům v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9ce67-102">File Access with Visual Basic</span></span>

<span data-ttu-id="9ce67-103">`My.Computer.FileSystem`Objekt poskytuje nástroje pro práci se soubory a složkami.</span><span class="sxs-lookup"><span data-stu-id="9ce67-103">The `My.Computer.FileSystem` object provides tools for working with files and folders.</span></span> <span data-ttu-id="9ce67-104">Jeho vlastnosti, metody a události umožňují vytvořit, kopírovat, přesunout, prozkoumat a odstranit soubory a složky.</span><span class="sxs-lookup"><span data-stu-id="9ce67-104">Its properties, methods, and events allow you to create, copy, move, investigate, and delete files and folders.</span></span> <span data-ttu-id="9ce67-105">`My.Computer.FileSystem`poskytuje lepší výkon než starší funkce ( `FileOpen` , `FileClose` ,, `Input` , `InputString` atd `LineInput` .), které jsou k dispozici Visual Basic z důvodu zpětné kompatibility.</span><span class="sxs-lookup"><span data-stu-id="9ce67-105">`My.Computer.FileSystem` provides better performance than the legacy functions (`FileOpen`, `FileClose`, `Input`, `InputString`, `LineInput`, etc.) that are provided by Visual Basic for backward compatibility.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9ce67-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="9ce67-106">In This Section</span></span>  

 [<span data-ttu-id="9ce67-107">Čtení ze souborů</span><span class="sxs-lookup"><span data-stu-id="9ce67-107">Reading from Files</span></span>](reading-from-files.md)  
 <span data-ttu-id="9ce67-108">Vypisuje témata, která se týkají použití `My.Computer.FileSystem` objektu ke čtení ze souborů.</span><span class="sxs-lookup"><span data-stu-id="9ce67-108">Lists topics dealing with using the `My.Computer.FileSystem` object to read from files</span></span>  
  
 [<span data-ttu-id="9ce67-109">Zápis do souborů</span><span class="sxs-lookup"><span data-stu-id="9ce67-109">Writing to Files</span></span>](writing-to-files.md)  
 <span data-ttu-id="9ce67-110">Vypisuje témata, která se týkají použití `My.Computer.FileSystem` objektu k zápisu do souborů.</span><span class="sxs-lookup"><span data-stu-id="9ce67-110">Lists topics dealing with using the `My.Computer.FileSystem` object to write to files</span></span>  
  
 [<span data-ttu-id="9ce67-111">Vytváření, odstraňování a přesouvání souborů a adresářů</span><span class="sxs-lookup"><span data-stu-id="9ce67-111">Creating, Deleting, and Moving Files and Directories</span></span>](creating-deleting-and-moving-files-and-directories.md)  
 <span data-ttu-id="9ce67-112">Obsahuje seznam témat, která se týkají použití `My.Computer.FileSystem` objektu k vytváření, kopírování, odstraňování a přesouvání souborů a složek.</span><span class="sxs-lookup"><span data-stu-id="9ce67-112">Lists topics dealing with using the `My.Computer.FileSystem` object to creating, copying, deleting and moving files and folders.</span></span>  
  
 [<span data-ttu-id="9ce67-113">Analýza textových souborů pomocí objektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="9ce67-113">Parsing Text Files with the TextFieldParser Object</span></span>](parsing-text-files-with-the-textfieldparser-object.md)  
 <span data-ttu-id="9ce67-114">Popisuje, jak použít `TextFieldReader` k analýze textových souborů, jako jsou protokoly.</span><span class="sxs-lookup"><span data-stu-id="9ce67-114">Discusses how to use the `TextFieldReader` to parse text files such as logs.</span></span>  
  
 [<span data-ttu-id="9ce67-115">Kódování souborů</span><span class="sxs-lookup"><span data-stu-id="9ce67-115">File Encodings</span></span>](file-encodings.md)  
 <span data-ttu-id="9ce67-116">Popisuje kódování souborů a jejich použití.</span><span class="sxs-lookup"><span data-stu-id="9ce67-116">Describes file encodings and their use.</span></span>  
  
 [<span data-ttu-id="9ce67-117">Návod: Práce se soubory a adresáři v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9ce67-117">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](walkthrough-manipulating-files-and-directories.md)  
 <span data-ttu-id="9ce67-118">Ukazuje, jak vytvořit nástroj, který hlásí informace o souborech a složkách.</span><span class="sxs-lookup"><span data-stu-id="9ce67-118">Demonstrates how to create a utility that reports information about files and folders.</span></span>  
  
 [<span data-ttu-id="9ce67-119">Řešení potíží: Čtení z textových souborů a zápis do nich</span><span class="sxs-lookup"><span data-stu-id="9ce67-119">Troubleshooting: Reading from and Writing to Text Files</span></span>](troubleshooting-reading-from-and-writing-to-text-files.md)  
 <span data-ttu-id="9ce67-120">Zobrazí seznam běžných problémů zjištěných při čtení a zápisu do textových souborů a navrhuje pro každé z nich nápravná opatření.</span><span class="sxs-lookup"><span data-stu-id="9ce67-120">Lists common problems encountered when reading and writing to text files, and suggests remedies for each.</span></span>
