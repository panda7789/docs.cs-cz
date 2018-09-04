---
title: 'Postupy: Kopírování, odstraňování a přesouvání souborů a složek (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: ea7e23f03f4321644eb2484b3965a0de3f180c47
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43504532"
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a>Postupy: Kopírování, odstraňování a přesouvání souborů a složek (Průvodce programováním v C#)
Následující příklady ukazují, jak zkopírovat, přesunout a odstranit soubory a složky v synchronním způsobem pomocí <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, a <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> třídy z <xref:System.IO?displayProperty=nameWithType> oboru názvů. Tyto příklady neposkytují indikátor průběhu nebo jiných uživatelské rozhraní. Pokud chcete poskytnout dialogového okna průběhu standardní, přečtěte si téma [postupy: poskytnutí dialogového okna průběhu pro operace se soubory](how-to-provide-a-progress-dialog-box-for-file-operations.md).  
  
 Použití <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> poskytnout události, které vám umožní výpočtu průběhu při provozu na více souborů. Další možností je používat platformu vyvolání pro volání metody relevantní vztahující se k souboru v prostředí Windows. Informace o tom, jak provádět tyto operace se soubory asynchronně, naleznete v tématu [asynchronní vstupně-výstupní operace souboru](https://msdn.microsoft.com/library/kztecsys).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak kopírovat soubory a adresáře.  
  
 [!code-csharp[csFilesandFolders#7](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_1.cs)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak přesunout soubory a adresáře.  
  
 [!code-csharp[csFilesandFolders#8](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_2.cs)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak odstraňovat soubory a adresáře.  
  
 [!code-csharp[csFilesandFolders#9](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_3.cs)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO?displayProperty=nameWithType>  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Systém souborů a registr (C# Programming Guide)](index.md)  
- [Postupy: Poskytnutí dialogového okna průběhu pro operace se soubory](how-to-provide-a-progress-dialog-box-for-file-operations.md)  
- [Vstup/výstup souborů a streamů](https://msdn.microsoft.com/library/k3352a4t)  
- [Obecné vstupně-výstupní úlohy](https://msdn.microsoft.com/library/ms404278)
