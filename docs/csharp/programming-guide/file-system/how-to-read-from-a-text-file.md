---
title: 'Postupy: Čtení z textového souboru – C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- StreamReader.ReadToEnd
helpviewer_keywords:
- text files, writing to
- reading text files
- reading data, text files
- text files, reading
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
ms.openlocfilehash: 67e98750af589a3deb5e9d0d51f8b1204fdaad84
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240304"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a>Postupy: Čtení z textového souboru (C# Průvodce programováním v)
Tento příklad přečte obsah textového souboru s použitím statické metody <xref:System.IO.File.ReadAllText%2A> a <xref:System.IO.File.ReadAllLines%2A> z <xref:System.IO.File?displayProperty=nameWithType> třídy.  
  
 Příklad, který používá <xref:System.IO.StreamReader>, naleznete v tématu [jak: Přečíst textový soubor jeden řádek v čase](../../../csharp/programming-guide/file-system/how-to-read-a-text-file-one-line-at-a-time.md).  
  
> [!NOTE]
>  Soubory, které se používají v tomto příkladu se vytvoří v tématu [jak: Zápis do textového souboru](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csFilesandFolders#4](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-read-from-a-text-file_1.cs)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Zkopírujte kód a vložte ho do konzolové aplikace jazyka C#.  
  
 Pokud nepoužíváte textových souborů z [jak: Zápis do textového souboru](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md), nahraďte argument `ReadAllText` a `ReadAllLines` s odpovídající název a cesta k souboru ve vašem počítači.  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
-   Soubor neexistuje, nebo neexistuje v zadaném umístění. Zkontrolujte cestu a zadání názvu souboru.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Nespoléhejte na název souboru můžete zjistit obsah souboru. Například soubor `myFile.cs` nemusí být zdrojový soubor jazyka C#.  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO?displayProperty=nameWithType>  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Systém souborů a registr (C# Programming Guide)](../../../csharp/programming-guide/file-system/index.md)
