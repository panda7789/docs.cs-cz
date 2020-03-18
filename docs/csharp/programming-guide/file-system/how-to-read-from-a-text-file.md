---
title: Jak číst z textového souboru - C# Programovací průvodce
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705012"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a>Jak číst z textového souboru (C# Programming Guide)
Tento příklad přečte obsah textového souboru <xref:System.IO.File.ReadAllText%2A> <xref:System.IO.File.ReadAllLines%2A> pomocí <xref:System.IO.File?displayProperty=nameWithType> statických metod a z třídy.  
  
Příklad, který <xref:System.IO.StreamReader>používá , naleznete [v tématu Jak číst textový soubor po jednom řádku](./how-to-read-a-text-file-one-line-at-a-time.md).
  
> [!NOTE]
> Soubory, které jsou použity v tomto příkladu jsou vytvořeny v tématu [Jak zapisovat do textového souboru](./how-to-write-to-a-text-file.md).
  
## <a name="example"></a>Příklad  
 [!code-csharp[csFilesandFolders#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#4)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Zkopírujte kód a vložte jej do aplikace konzoly C#.  
  
Pokud nepoužíváte textové soubory z [jak zapisovat do textového souboru](./how-to-write-to-a-text-file.md), nahraďte argument `ReadAllText` a `ReadAllLines` příslušnou cestou a názvem souboru v počítači.
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
- Soubor neexistuje nebo neexistuje v zadaném umístění. Zkontrolujte cestu a pravopis názvu souboru.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Při určování obsahu souboru nespoléhejte na název souboru. Například soubor `myFile.cs` nemusí být zdrojový soubor Jazyka C#.  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO?displayProperty=nameWithType>
- [Programovací příručka jazyka C#](../index.md)
- [Systém souborů a registr (Průvodce programováním v C#)](./index.md)
