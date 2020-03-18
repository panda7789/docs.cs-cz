---
title: Kopírování, odstraňování a přesouvání souborů a složek – Průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: 662f0ab3b9e69aa8bfb0085f42f577b850029e4d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712270"
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a>Kopírování, odstraňování a přesouvání souborů a složek (Průvodce programováním jazyka C#)
Následující příklady ukazují, jak kopírovat, přesouvat a odstraňovat soubory <xref:System.IO.File?displayProperty=nameWithType>a <xref:System.IO.Directory?displayProperty=nameWithType> <xref:System.IO.FileInfo?displayProperty=nameWithType>složky <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> synchronním <xref:System.IO?displayProperty=nameWithType> způsobem pomocí aplikace , , a tříd z oboru názvů. Tyto příklady neposkytují indikátor průběhu ani jiné uživatelské rozhraní. Pokud chcete poskytnout standardní dialogové okno průběhu, přečtěte si informace [o tom, jak poskytnout dialogové okno průběhu pro operace se soubory](how-to-provide-a-progress-dialog-box-for-file-operations.md).  
  
 Slouží <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> k poskytnutí událostí, které vám umožní vypočítat průběh při práci s více soubory. Dalším přístupem je použití platformy invoke k volání příslušných metod souvisejících se souborem v prostředí Windows. Informace o tom, jak provádět tyto operace se soubory asynchronně, naleznete [v tématu Asynchronní vstupně-vstupně-nevstupně-to .](../../../standard/io/asynchronous-file-i-o.md)  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak kopírovat soubory a adresáře.  
  
 [!code-csharp[csFilesandFolders#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#7)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak přesunout soubory a adresáře.  
  
 [!code-csharp[csFilesandFolders#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#8)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak odstranit soubory a adresáře.  
  
 [!code-csharp[csFilesandFolders#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#9)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO?displayProperty=nameWithType>
- [Programovací příručka jazyka C#](../index.md)
- [Systém souborů a registr (Průvodce programováním v C#)](index.md)
- [Jak zobrazit dialogové okno průběhu pro operace se soubory](how-to-provide-a-progress-dialog-box-for-file-operations.md)
- [I/O souborů a proudů](../../../standard/io/index.md)
- [Obecné vstupně-výstupní úlohy](../../../standard/io/common-i-o-tasks.md)
