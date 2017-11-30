---
title: "Zpracování jednotek, adresářů a souborů (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- drives
- drives, processing
- Visual Basic code, file access
- files [Visual Basic], processing
- files [Visual Basic], accessing
- directories [Visual Studio], processing
ms.assetid: f1db14c8-a4fd-4d0b-8323-c7cb29d688c2
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 27a5c3c389860cdc29c4263edbff492738ffe565
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="processing-drives-directories-and-files-visual-basic"></a><span data-ttu-id="1d9c1-102">Zpracování jednotek, adresářů a souborů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d9c1-102">Processing Drives, Directories, and Files (Visual Basic)</span></span>
<span data-ttu-id="1d9c1-103">Můžete použít [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] ke zpracování jednotek, složek a souborů pomocí `My.Computer.FileSystem` objekt, který poskytuje lepší výkon a je jednodušší než tradiční metody, jako `FileOpen` a `Write` funkce (i když jsou stále k dispozici.)</span><span class="sxs-lookup"><span data-stu-id="1d9c1-103">You can use [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] to process drives, folders, and files with the `My.Computer.FileSystem` object, which provides better performance and is easier to use than traditional methods such as the `FileOpen` and `Write` functions (although they are still available).</span></span> <span data-ttu-id="1d9c1-104">Následující části popisují tyto metody podrobně.</span><span class="sxs-lookup"><span data-stu-id="1d9c1-104">The following sections discuss these methods in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1d9c1-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="1d9c1-105">In This Section</span></span>  
 [<span data-ttu-id="1d9c1-106">Přístup k souborům v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1d9c1-106">File Access with Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)  
 <span data-ttu-id="1d9c1-107">Popisuje postup použití `My.Computer.FileSystem` objekt pro práci se soubory, jednotky a složky.</span><span class="sxs-lookup"><span data-stu-id="1d9c1-107">Discusses how to use the `My.Computer.FileSystem` object to work with files, drives, and folders.</span></span>  
  
 [<span data-ttu-id="1d9c1-108">Základní informace o souborech vstupně-výstupních operací a systému souborů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d9c1-108">Basics of .NET Framework File I/O and the File System (Visual Basic)</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)  
 <span data-ttu-id="1d9c1-109">Poskytuje přehled konceptů vstupně-výstupních souborů v rozhraní .NET Framework, včetně datových proudů, izolované úložiště, události souboru, atributy souboru a přístup k souborům.</span><span class="sxs-lookup"><span data-stu-id="1d9c1-109">Provides an overview of file I/O concepts in the .NET Framework, including streams, isolated storage, file events, file attributes, and file access.</span></span>  
  
 [<span data-ttu-id="1d9c1-110">Návod: Manipulace se soubory pomocí metod rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1d9c1-110">Walkthrough: Manipulating Files by Using .NET Framework Methods</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)  
 <span data-ttu-id="1d9c1-111">Ukazuje, jak používat [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] k manipulaci se soubory a složky.</span><span class="sxs-lookup"><span data-stu-id="1d9c1-111">Demonstrates how to use the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] to manipulate files and folders.</span></span>  
  
 [<span data-ttu-id="1d9c1-112">Návod: Manipulace se soubory a adresáře v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1d9c1-112">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 <span data-ttu-id="1d9c1-113">Ukazuje, jak používat `My.Computer.FileSystem` objektu k manipulaci se soubory a složky.</span><span class="sxs-lookup"><span data-stu-id="1d9c1-113">Demonstrates how to use the `My.Computer.FileSystem` object to manipulate files and folders.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1d9c1-114">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="1d9c1-114">Related Sections</span></span>  
 [<span data-ttu-id="1d9c1-115">Struktura programu a pravidla týkající se kódu</span><span class="sxs-lookup"><span data-stu-id="1d9c1-115">Program Structure and Code Conventions</span></span>](../../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 <span data-ttu-id="1d9c1-116">Poskytuje pokyny pro fyzickou strukturu a vzhled programů.</span><span class="sxs-lookup"><span data-stu-id="1d9c1-116">Provides guidelines for the physical structure and appearance of programs.</span></span>  
  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <span data-ttu-id="1d9c1-117">Referenční dokumentace pro `My.Computer.FileSystem` objektu a její členy.</span><span class="sxs-lookup"><span data-stu-id="1d9c1-117">Reference documentation for the `My.Computer.FileSystem` object and its members.</span></span>
