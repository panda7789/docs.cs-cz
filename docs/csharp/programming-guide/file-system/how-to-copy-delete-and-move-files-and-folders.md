---
title: Postup kopírování, odstraňování a přesouvání souborů a složek – Průvodce programováním v C#
description: Naučte se kopírovat, odstraňovat a přesouvat soubory a složky pomocí tříd File, Directory, FileInfo a DirectoryInfo.
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: 208502651080f4fd614e34d1bf5b088dfb1207a6
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303358"
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a>Postup kopírování, odstraňování a přesouvání souborů a složek (Průvodce programováním v C#)
Následující příklady ukazují, jak kopírovat, přesunout a odstraňovat soubory a složky synchronním způsobem pomocí <xref:System.IO.File?displayProperty=nameWithType> <xref:System.IO.Directory?displayProperty=nameWithType> tříd,, a <xref:System.IO.FileInfo?displayProperty=nameWithType> <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> z <xref:System.IO?displayProperty=nameWithType> oboru názvů. Tyto příklady neposkytují indikátor průběhu ani žádné jiné uživatelské rozhraní. Pokud chcete zadat standardní dialogové okno průběhu, přečtěte si téma [jak poskytnout dialogové okno průběhu pro operace se soubory](how-to-provide-a-progress-dialog-box-for-file-operations.md).  
  
 Slouží <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> k poskytnutí událostí, které vám umožní vypočítat průběh při práci na více souborech. Další možností je použít vyvolání platformy pro volání relevantních metod, které se týkají souborů v prostředí Windows Shell. Informace o asynchronním provádění těchto operací se soubory najdete v tématu [asynchronní vstupně-výstupní](../../../standard/io/asynchronous-file-i-o.md)operace se soubory.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak kopírovat soubory a adresáře.  
  
 [!code-csharp[csFilesandFolders#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#7)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak přesunout soubory a adresáře.  
  
 [!code-csharp[csFilesandFolders#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#8)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak odstranit soubory a adresáře.  
  
 [!code-csharp[csFilesandFolders#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#9)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO?displayProperty=nameWithType>
- [Průvodce programováním v C#](../index.md)
- [Systém souborů a registr (Průvodce programováním v C#)](index.md)
- [Jak zobrazit dialogové okno průběhu pro operace se soubory](how-to-provide-a-progress-dialog-box-for-file-operations.md)
- [Vstupně-výstupní operace se soubory a datovým proudem](../../../standard/io/index.md)
- [Běžné vstupně-výstupní úlohy](../../../standard/io/common-i-o-tasks.md)
