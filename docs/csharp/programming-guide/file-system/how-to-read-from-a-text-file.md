---
title: Jak číst z textového souboru – C# Průvodce programováním
ms.date: 07/20/2015
f1_keywords:
- StreamReader.ReadToEnd
helpviewer_keywords:
- text files, writing to
- reading text files
- reading data, text files
- text files, reading
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
ms.openlocfilehash: d401a1d1bb2c6fccb203c440f367bd14c80e70e3
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705012"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a>Čtení z textového souboru (C# Průvodce programováním)
Tento příklad přečte obsah textového souboru pomocí statických metod <xref:System.IO.File.ReadAllText%2A> a <xref:System.IO.File.ReadAllLines%2A> z třídy <xref:System.IO.File?displayProperty=nameWithType>.  
  
Příklad, který používá <xref:System.IO.StreamReader>, najdete v tématu [jak číst textový soubor po jednom řádku](./how-to-read-a-text-file-one-line-at-a-time.md).
  
> [!NOTE]
> Soubory, které jsou použity v tomto příkladu, jsou vytvořeny v tématu [jak zapisovat do textového souboru](./how-to-write-to-a-text-file.md).
  
## <a name="example"></a>Příklad  
 [!code-csharp[csFilesandFolders#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#4)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Zkopírujte kód a vložte ho do C# konzolové aplikace.  
  
Pokud nepoužíváte textové soubory z [postupu zápisu do textového souboru](./how-to-write-to-a-text-file.md), nahraďte argument `ReadAllText` a `ReadAllLines` odpovídající cestou a názvu souboru v počítači.
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
- Soubor neexistuje nebo neexistuje v zadaném umístění. Zkontrolujte cestu a pravopis názvu souboru.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Nespoléhá na název souboru k určení obsahu souboru. Například soubor `myFile.cs` nemusí být C# zdrojový soubor.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO?displayProperty=nameWithType>
- [Průvodce programováním v jazyce C#](../index.md)
- [Systém souborů a registr (C# Průvodce programováním)](./index.md)
