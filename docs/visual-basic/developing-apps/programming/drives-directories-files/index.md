---
title: Zpracování jednotek, adresářů a souborů (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- drives
- drives, processing
- Visual Basic code, file access
- files [Visual Basic], processing
- files [Visual Basic], accessing
- directories [Visual Studio], processing
ms.assetid: f1db14c8-a4fd-4d0b-8323-c7cb29d688c2
ms.openlocfilehash: 0c9c1c787138595f725316a580acda9c5d4d43a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797846"
---
# <a name="processing-drives-directories-and-files-visual-basic"></a><span data-ttu-id="e1a1f-102">Zpracování jednotek, adresářů a souborů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e1a1f-102">Processing Drives, Directories, and Files (Visual Basic)</span></span>
<span data-ttu-id="e1a1f-103">Visual Basic můžete použít ke zpracování jednotek, složek a souborů s `My.Computer.FileSystem` objektu, který poskytuje lepší výkon a je jednodušší než tradiční metody, jako `FileOpen` a `Write` funkcí (i když jsou stále k dispozici.)</span><span class="sxs-lookup"><span data-stu-id="e1a1f-103">You can use Visual Basic to process drives, folders, and files with the `My.Computer.FileSystem` object, which provides better performance and is easier to use than traditional methods such as the `FileOpen` and `Write` functions (although they are still available).</span></span> <span data-ttu-id="e1a1f-104">Následující části popisují tyto metody podrobně.</span><span class="sxs-lookup"><span data-stu-id="e1a1f-104">The following sections discuss these methods in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e1a1f-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="e1a1f-105">In This Section</span></span>  
 [<span data-ttu-id="e1a1f-106">Přístup k souborům v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e1a1f-106">File Access with Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)  
 <span data-ttu-id="e1a1f-107">Tento článek popisuje způsob použití `My.Computer.FileSystem` objektu pro práci se soubory, jednotky a složky.</span><span class="sxs-lookup"><span data-stu-id="e1a1f-107">Discusses how to use the `My.Computer.FileSystem` object to work with files, drives, and folders.</span></span>  
  
 [<span data-ttu-id="e1a1f-108">Základy vstupně-výstupní operace souboru rozhraní .NET Framework a systému souborů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e1a1f-108">Basics of .NET Framework File I/O and the File System (Visual Basic)</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)  
 <span data-ttu-id="e1a1f-109">Poskytuje přehled konceptů vstupně-výstupní operace souboru v rozhraní .NET Framework, včetně datových proudů, izolované úložiště, soubor událostí, atributy souboru a přístup k souborům.</span><span class="sxs-lookup"><span data-stu-id="e1a1f-109">Provides an overview of file I/O concepts in the .NET Framework, including streams, isolated storage, file events, file attributes, and file access.</span></span>  
  
 [<span data-ttu-id="e1a1f-110">Návod: Manipulace se soubory pomocí metod rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e1a1f-110">Walkthrough: Manipulating Files by Using .NET Framework Methods</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)  
 <span data-ttu-id="e1a1f-111">Popisuje způsob použití [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] k manipulaci se soubory a složky.</span><span class="sxs-lookup"><span data-stu-id="e1a1f-111">Demonstrates how to use the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] to manipulate files and folders.</span></span>  
  
 [<span data-ttu-id="e1a1f-112">Návod: Práce se soubory a adresáře v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e1a1f-112">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 <span data-ttu-id="e1a1f-113">Popisuje způsob použití `My.Computer.FileSystem` objekt pro manipulaci se soubory a složky.</span><span class="sxs-lookup"><span data-stu-id="e1a1f-113">Demonstrates how to use the `My.Computer.FileSystem` object to manipulate files and folders.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e1a1f-114">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="e1a1f-114">Related Sections</span></span>  
 [<span data-ttu-id="e1a1f-115">Struktura programu a zásady týkající se kódu</span><span class="sxs-lookup"><span data-stu-id="e1a1f-115">Program Structure and Code Conventions</span></span>](../../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 <span data-ttu-id="e1a1f-116">Obsahuje pokyny pro fyzickou strukturu a vzhled programy.</span><span class="sxs-lookup"><span data-stu-id="e1a1f-116">Provides guidelines for the physical structure and appearance of programs.</span></span>  
  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <span data-ttu-id="e1a1f-117">Referenční dokumentace pro `My.Computer.FileSystem` objektu a její členy.</span><span class="sxs-lookup"><span data-stu-id="e1a1f-117">Reference documentation for the `My.Computer.FileSystem` object and its members.</span></span>
