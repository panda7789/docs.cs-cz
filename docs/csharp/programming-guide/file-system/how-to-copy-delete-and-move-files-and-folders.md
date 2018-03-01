---
title: "Postupy: Kopírování, odstraňování a přesouvání souborů a složek (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 56383873674998fc0d6417a2abf4fa72e498f08f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Systém souborů a registr (C# Průvodce programováním)](index.md)  
 [Postupy: poskytnutí dialogového okna průběhu pro operace se soubory](how-to-provide-a-progress-dialog-box-for-file-operations.md)  
 [Vstupně-výstupních souborů a proudů](https://msdn.microsoft.com/library/k3352a4t)  
 [Běžné vstupně-výstupní úlohy](https://msdn.microsoft.com/library/ms404278)
