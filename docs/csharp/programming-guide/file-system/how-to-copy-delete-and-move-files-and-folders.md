---
title: Postup kopírování, odstraňování a přesouvání souborů a složek – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: 234e534ef081d3ab527d307b9d3f1756783ad5ac
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635558"
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a>Postup kopírování, odstraňování a přesouvání souborů a složek (C# Průvodce programováním)
Následující příklady ukazují, jak kopírovat, přesunout a odstraňovat soubory a složky synchronním způsobem pomocí tříd <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>a <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> z oboru názvů <xref:System.IO?displayProperty=nameWithType>. Tyto příklady neposkytují indikátor průběhu ani žádné jiné uživatelské rozhraní. Pokud chcete zadat standardní dialogové okno průběhu, přečtěte si téma [jak poskytnout dialogové okno průběhu pro operace se soubory](how-to-provide-a-progress-dialog-box-for-file-operations.md).  
  
 Pomocí <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> můžete poskytnout události, které vám umožní vypočítat průběh při práci na více souborech. Další možností je použít vyvolání platformy pro volání relevantních metod, které se týkají souborů v prostředí Windows Shell. Informace o asynchronním provádění těchto operací se soubory najdete v tématu [asynchronní vstupně-výstupní](../../../standard/io/asynchronous-file-i-o.md)operace se soubory.  
  
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
- [Postup poskytnutí dialogového okna průběhu pro operace se soubory](how-to-provide-a-progress-dialog-box-for-file-operations.md)
- [Vstup/výstup souborů a datových proudů](../../../standard/io/index.md)
- [Obecné vstupně-výstupní úlohy](../../../standard/io/common-i-o-tasks.md)
