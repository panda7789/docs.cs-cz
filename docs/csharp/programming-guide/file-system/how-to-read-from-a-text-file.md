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
ms.openlocfilehash: 2b98f24da7f13ae752f248eb8f26c75c1d47a824
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923956"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a>Postupy: Čtení z textového souboru (C# Průvodce programováním)
Tento příklad přečte obsah textového souboru pomocí statických metod <xref:System.IO.File.ReadAllText%2A> a <xref:System.IO.File.ReadAllLines%2A> od <xref:System.IO.File?displayProperty=nameWithType> třídy.  
  
 Příklad použití <xref:System.IO.StreamReader>naleznete v tématu [How to: Přečtěte si textový soubor po](./how-to-read-a-text-file-one-line-at-a-time.md)jednom řádku.  
  
> [!NOTE]
> Soubory, které jsou použity v tomto příkladu, jsou vytvořeny v tématu [How to: Zápis do textového souboru](./how-to-write-to-a-text-file.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csFilesandFolders#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#4)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Zkopírujte kód a vložte ho do C# konzolové aplikace.  
  
 Pokud nepoužíváte textové soubory z [tématu Postupy: Zapište do textového souboru](./how-to-write-to-a-text-file.md), nahraďte `ReadAllText` argument a `ReadAllLines` odpovídající cestou a názvem souboru v počítači.  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
- Soubor neexistuje nebo neexistuje v zadaném umístění. Zkontrolujte cestu a pravopis názvu souboru.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Nespoléhá na název souboru k určení obsahu souboru. Soubor `myFile.cs` může být například C# zdrojový soubor.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO?displayProperty=nameWithType>
- [Průvodce programováním v jazyce C#](../index.md)
- [Systém souborů a registr (C# Průvodce programováním)](./index.md)
