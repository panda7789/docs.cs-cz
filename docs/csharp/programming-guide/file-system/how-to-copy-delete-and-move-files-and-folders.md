---
title: 'Postupy: Kopírování, odstranění a přesunutí souborů a složek - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: 609e14141538543c9318efbd4899ec16967cc23f
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972064"
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a>Postupy: Kopírování, odstraňování a přesouvání souborů a složek (C# Průvodce programováním v)
Následující příklady ukazují, jak zkopírovat, přesunout a odstranit soubory a složky v synchronním způsobem pomocí <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, a <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> třídy z <xref:System.IO?displayProperty=nameWithType> oboru názvů. Tyto příklady neposkytují indikátor průběhu nebo jiných uživatelské rozhraní. Pokud chcete poskytnout dialogového okna průběhu standardní, přečtěte si téma [jak: Poskytnutí dialogového okna průběhu pro operace se soubory](how-to-provide-a-progress-dialog-box-for-file-operations.md).  
  
 Použití <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> poskytnout události, které vám umožní výpočtu průběhu při provozu na více souborů. Další možností je používat platformu vyvolání pro volání metody relevantní vztahující se k souboru v prostředí Windows. Informace o tom, jak provádět tyto operace se soubory asynchronně, naleznete v tématu [asynchronní vstupně-výstupní operace souboru](../../../standard/io/asynchronous-file-i-o.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak kopírovat soubory a adresáře.  
  
 [!code-csharp[csFilesandFolders#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#7)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak přesunout soubory a adresáře.  
  
 [!code-csharp[csFilesandFolders#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#8)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak odstraňovat soubory a adresáře.  
  
 [!code-csharp[csFilesandFolders#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#9)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO?displayProperty=nameWithType>
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Systém souborů a registr (C# Programming Guide)](index.md)
- [Postupy: Poskytnutí dialogového okna průběhu pro operace se soubory](how-to-provide-a-progress-dialog-box-for-file-operations.md)
- [Vstup/výstup souborů a streamů](../../../standard/io/index.md)
- [Obecné vstupně-výstupní úlohy](../../../standard/io/common-i-o-tasks.md)
