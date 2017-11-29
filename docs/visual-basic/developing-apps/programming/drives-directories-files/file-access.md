---
title: "Přístup k souborům v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9929061feeccee31028056bc93f0f0a2f119eb4e
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="file-access-with-visual-basic"></a><span data-ttu-id="f4fb8-102">Přístup k souborům v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f4fb8-102">File Access with Visual Basic</span></span>
<span data-ttu-id="f4fb8-103">`My.Computer.FileSystem` Objekt poskytuje nástroje pro práci se soubory a složky.</span><span class="sxs-lookup"><span data-stu-id="f4fb8-103">The `My.Computer.FileSystem` object provides tools for working with files and folders.</span></span> <span data-ttu-id="f4fb8-104">Jeho vlastnosti, metod a události umožňují vytvářet, kopírovat, přesunout, prozkoumat a odstraňovat soubory a složky.</span><span class="sxs-lookup"><span data-stu-id="f4fb8-104">Its properties, methods, and events allow you to create, copy, move, investigate, and delete files and folders.</span></span> <span data-ttu-id="f4fb8-105">`My.Computer.FileSystem`poskytuje lepší výkon než starší verze funkce (`FileOpen`, `FileClose`, `Input`, `InputString`, `LineInput`atd), jsou poskytovány [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] z důvodu zpětné kompatibility.</span><span class="sxs-lookup"><span data-stu-id="f4fb8-105">`My.Computer.FileSystem` provides better performance than the legacy functions (`FileOpen`, `FileClose`, `Input`, `InputString`, `LineInput`, etc.) that are provided by [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] for backward compatibility.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f4fb8-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="f4fb8-106">In This Section</span></span>  
 [<span data-ttu-id="f4fb8-107">Čtení ze souborů</span><span class="sxs-lookup"><span data-stu-id="f4fb8-107">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 <span data-ttu-id="f4fb8-108">Obsahuje seznam témat týkajících se použití `My.Computer.FileSystem` objektu určeného ke čtení ze souborů</span><span class="sxs-lookup"><span data-stu-id="f4fb8-108">Lists topics dealing with using the `My.Computer.FileSystem` object to read from files</span></span>  
  
 [<span data-ttu-id="f4fb8-109">Zápis do souborů</span><span class="sxs-lookup"><span data-stu-id="f4fb8-109">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)  
 <span data-ttu-id="f4fb8-110">Obsahuje seznam témat týkajících se použití `My.Computer.FileSystem` objekt pro zápis do souborů</span><span class="sxs-lookup"><span data-stu-id="f4fb8-110">Lists topics dealing with using the `My.Computer.FileSystem` object to write to files</span></span>  
  
 [<span data-ttu-id="f4fb8-111">Vytváření, odstraňování a přesouvání souborů a adresářů</span><span class="sxs-lookup"><span data-stu-id="f4fb8-111">Creating, Deleting, and Moving Files and Directories</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)  
 <span data-ttu-id="f4fb8-112">Obsahuje seznam témat týkajících se použití `My.Computer.FileSystem` objektu pro vytváření, kopírování, odstraňování a přesouvání souborů a složek.</span><span class="sxs-lookup"><span data-stu-id="f4fb8-112">Lists topics dealing with using the `My.Computer.FileSystem` object to creating, copying, deleting and moving files and folders.</span></span>  
  
 [<span data-ttu-id="f4fb8-113">Analýza textových souborů pomocí objektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="f4fb8-113">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)  
 <span data-ttu-id="f4fb8-114">Popisuje postup použití `TextFieldReader` Analýza textových souborů, jako jsou protokoly.</span><span class="sxs-lookup"><span data-stu-id="f4fb8-114">Discusses how to use the `TextFieldReader` to parse text files such as logs.</span></span>  
  
 [<span data-ttu-id="f4fb8-115">Kódování souborů</span><span class="sxs-lookup"><span data-stu-id="f4fb8-115">File Encodings</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)  
 <span data-ttu-id="f4fb8-116">Popisuje kódování souborů a jejich použití.</span><span class="sxs-lookup"><span data-stu-id="f4fb8-116">Describes file encodings and their use.</span></span>  
  
 [<span data-ttu-id="f4fb8-117">Návod: Manipulace se soubory a adresáře v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f4fb8-117">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 <span data-ttu-id="f4fb8-118">Ukazuje, jak vytvořit nástroj, který hlásí informace o souborech a složkách.</span><span class="sxs-lookup"><span data-stu-id="f4fb8-118">Demonstrates how to create a utility that reports information about files and folders.</span></span>  
  
 [<span data-ttu-id="f4fb8-119">Řešení potíží: Čtení a zápis do textových souborů</span><span class="sxs-lookup"><span data-stu-id="f4fb8-119">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)  
 <span data-ttu-id="f4fb8-120">Jsou uvedeny běžné problémy při čtení a zápis do textových souborů a navrhne opravy pro každé.</span><span class="sxs-lookup"><span data-stu-id="f4fb8-120">Lists common problems encountered when reading and writing to text files, and suggests remedies for each.</span></span>
