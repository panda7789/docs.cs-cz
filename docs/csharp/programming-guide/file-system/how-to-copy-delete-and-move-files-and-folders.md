---
title: 'Postupy: Kopírování, odstraňování a přesouvání souborů a složek – C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: dd32798062dbfc9a10acd27ce51d8d5dd3b164f6
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590090"
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a>Postupy: Kopírování, odstraňování a přesouvání souborů a složek (C# Průvodce programováním)
Následující příklady ukazují, jak kopírovat, přesunout a odstraňovat <xref:System.IO.File?displayProperty=nameWithType>soubory a složky synchronním způsobem pomocí <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> tříd, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>a z <xref:System.IO?displayProperty=nameWithType> oboru názvů. Tyto příklady neposkytují indikátor průběhu ani žádné jiné uživatelské rozhraní. Pokud chcete zadat standardní dialogové okno průběhu, přečtěte si téma [How to: Slouží k zadání dialogového okna průběhu pro operace](how-to-provide-a-progress-dialog-box-for-file-operations.md)se soubory.  
  
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
- [Průvodce programováním v jazyce C#](../index.md)
- [Systém souborů a registr (C# Průvodce programováním)](index.md)
- [Postupy: Zadání dialogového okna průběhu pro operace se soubory](how-to-provide-a-progress-dialog-box-for-file-operations.md)
- [Vstup/výstup souborů a streamů](../../../standard/io/index.md)
- [Obecné vstupně-výstupní úlohy](../../../standard/io/common-i-o-tasks.md)
