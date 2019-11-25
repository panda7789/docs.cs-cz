---
title: 'Postupy: Hledání podadresářů pomocí specifického vzoru'
ms.date: 07/20/2015
helpviewer_keywords:
- pattern matching
- folders, finding
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
ms.openlocfilehash: c8e13598080139cafabffb2e17d0a3b99c37dc5d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348771"
---
# <a name="how-to-find-subdirectories-with-a-specific-pattern-in-visual-basic"></a>Postupy: Hledání podadresářů pomocí specifického vzoru v jazyce Visual Basic

The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> method returns a read-only collection of strings representing the path names for the subdirectories in a directory. You can use the `wildCards` parameter to specify a specific pattern. If you would like to include the contents of subdirectories in the search, set the `searchType` parameter to `SearchOption.SearchAllSubDirectories`.

An empty collection is returned if no directories matching the specified pattern are found.

## <a name="to-find-subdirectories-with-a-specific-pattern"></a>To find subdirectories with a specific pattern

Use the `GetDirectories` method, supplying the name and path of the directory you want to search. The following example returns all the directories in the directory structure that contain the word "Logs" in their name, and adds them to `ListBox1`.

[!code-vb[VbVbcnFileAccess#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnFileAccess/VB/Class1.vb#1)]

## <a name="robust-programming"></a>Robustní programování

Následující podmínky mohou způsobit výjimku:

- The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).

- The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).

- One or more of the specified wildcard characters is `Nothing`, an empty string, or contains only spaces (<xref:System.ArgumentNullException>).

- `directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).

- `directory` points to an existing file (<xref:System.IO.IOException>).

- The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).

- A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).

- The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).

- The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>
- [Postupy: Hledání souborů pomocí specifického vzoru](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
