---
title: Jak číst z textového souboru – Průvodce programováním v C#
description: Naučte se číst z textového souboru pomocí statických metod z třídy File. Podívejte se na příklad kódu a zobrazte další dostupné prostředky.
ms.date: 07/20/2015
f1_keywords:
- StreamReader.ReadToEnd
helpviewer_keywords:
- text files, writing to
- reading text files
- reading data, text files
- text files, reading
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
ms.openlocfilehash: 80ac6f8412f456b23d05ee87882dca8e16a132c3
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301655"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a>Jak číst z textového souboru (Průvodce programováním v C#)
Tento příklad přečte obsah textového souboru pomocí statických metod <xref:System.IO.File.ReadAllText%2A> a <xref:System.IO.File.ReadAllLines%2A> od <xref:System.IO.File?displayProperty=nameWithType> třídy.  
  
Příklad, který používá <xref:System.IO.StreamReader> , najdete v tématu [jak číst textový soubor po jednom řádku](./how-to-read-a-text-file-one-line-at-a-time.md).
  
> [!NOTE]
> Soubory, které jsou použity v tomto příkladu, jsou vytvořeny v tématu [jak zapisovat do textového souboru](./how-to-write-to-a-text-file.md).
  
## <a name="example"></a>Příklad  
 [!code-csharp[csFilesandFolders#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#4)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Zkopírujte kód a vložte ho do konzolové aplikace v jazyce C#.  
  
Pokud nepoužíváte textové soubory z [postupu zápisu do textového souboru](./how-to-write-to-a-text-file.md), nahraďte argument `ReadAllText` a `ReadAllLines` odpovídající cestou a názvem souboru v počítači.
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
- Soubor neexistuje nebo neexistuje v zadaném umístění. Zkontrolujte cestu a pravopis názvu souboru.  
  
## <a name="net-security"></a>Zabezpečení .NET  
 Nespoléhá na název souboru k určení obsahu souboru. Například soubor nemusí `myFile.cs` být zdrojový soubor C#.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO?displayProperty=nameWithType>
- [Průvodce programováním v C#](../index.md)
- [Systém souborů a registr (Průvodce programováním v C#)](./index.md)
