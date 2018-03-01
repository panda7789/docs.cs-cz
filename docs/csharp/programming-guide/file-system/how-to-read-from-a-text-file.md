---
title: "Postupy: Čtení z textového souboru (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- StreamReader.ReadToEnd
helpviewer_keywords:
- text files, writing to
- reading text files
- reading data, text files
- text files, reading
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d2af6102ac6793b4612a6fbc41f8c50189cc24d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a>Postupy: Čtení z textového souboru (Průvodce programováním v C#)
Tento příklad načte obsah textového souboru s použitím statické metody <xref:System.IO.File.ReadAllText%2A> a <xref:System.IO.File.ReadAllLines%2A> z <xref:System.IO.File?displayProperty=nameWithType> třídy.  
  
 Pro příklad, který používá <xref:System.IO.StreamReader>, najdete v části [postupy: čtení textového souboru řádcích současně](../../../csharp/programming-guide/file-system/how-to-read-a-text-file-one-line-at-a-time.md).  
  
> [!NOTE]
>  Soubory, které se používají v tomto příkladu jsou vytvořené v tomto tématu [postupy: zápis do textového souboru](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csFilesandFolders#4](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-read-from-a-text-file_1.cs)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Zkopírujte kód a vložte jej do konzolovou aplikaci C#.  
  
 Pokud nepoužíváte textové soubory z [postupy: zápis do textového souboru](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md), nahraďte argument `ReadAllText` a `ReadAllLines` s odpovídající název a cesta k souboru ve vašem počítači.  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
-   Soubor neexistuje nebo neexistuje v zadaném umístění. Zkontrolujte cestu a správnost názvu souboru.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Nespoléhejte na název souboru k určení obsahu souboru. Například soubor `myFile.cs` nemusí být zdrojový soubor C#.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IO?displayProperty=nameWithType>  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Systém souborů a registr (C# Průvodce programováním)](../../../csharp/programming-guide/file-system/index.md)
