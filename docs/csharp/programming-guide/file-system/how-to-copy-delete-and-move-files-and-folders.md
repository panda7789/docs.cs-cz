---
title: 'Postupy: Kopírování, odstraňování a přesouvání souborů a složek (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: 5debb2cbfa5ada45447e280169b9fe66d1a15a53
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a>Postupy: Kopírování, odstraňování a přesouvání souborů a složek (Průvodce programováním v C#)
Následující příklady ukazují, jak kopírovat, přesunout a odstranit soubory a složky synchronním způsobem pomocí <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, a <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> třídy z <xref:System.IO?displayProperty=nameWithType> oboru názvů. Tyto příklady neposkytují indikátor průběhu nebo jiné uživatelské rozhraní. Pokud byste chtěli poskytnout dialogového okna průběhu standardní, přečtěte si téma [postupy: poskytnutí dialogového okna průběhu pro operace se soubory](how-to-provide-a-progress-dialog-box-for-file-operations.md).  
  
 Použití <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> zajistit události, které vám umožní vypočítat průběh při fungování na několik souborů. Další možností je použít platformy vyvolání pro volání metody příslušné soubory v prostředí systému Windows. Informace o tom, jak provést tyto operace se soubory asynchronně najdete v tématu [asynchronní vstup-výstup souboru](https://msdn.microsoft.com/library/kztecsys).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje postup kopírování souborů a adresářů.  
  
 [!code-csharp[csFilesandFolders#7](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_1.cs)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak k přesouvání souborů a adresářů.  
  
 [!code-csharp[csFilesandFolders#8](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_2.cs)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak k odstraňování souborů a adresářů.  
  
 [!code-csharp[csFilesandFolders#9](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_3.cs)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IO?displayProperty=nameWithType>  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Systém souborů a registr (C# Průvodce programováním)](index.md)  
 [Postupy: Poskytnutí dialogového okna průběhu pro operace se soubory](how-to-provide-a-progress-dialog-box-for-file-operations.md)  
 [Vstup/výstup souborů a streamů](https://msdn.microsoft.com/library/k3352a4t)  
 [Obecné vstupně-výstupní úlohy](https://msdn.microsoft.com/library/ms404278)
