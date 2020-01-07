---
title: Postup zápisu do textového souboru – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
ms.openlocfilehash: c0b6646e0d7f453dc9021a7470a3671f11ea0653
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635415"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a>Zápis do textového souboru (C# Průvodce programováním)
Tyto příklady znázorňují různé způsoby zápisu textu do souboru. První dva příklady používají statické praktické metody pro třídu <xref:System.IO.File?displayProperty=nameWithType> k zápisu každého prvku `IEnumerable<string>` a řetězce do textového souboru. Příklad 3 ukazuje, jak přidat text do souboru, když je potřeba zpracovat jednotlivé řádky jednotlivě při zápisu do souboru. Příklady 1-3 přepisují veškerý existující obsah v souboru, ale příklad 4 ukazuje, jak připojit text k existujícímu souboru.  
  
 Tyto příklady všechny zapisují řetězcové literály do souborů. Pokud chcete naformátovat text zapsaný do souboru, použijte funkci <xref:System.String.Format%2A> nebo C# [řetězcové interpolace](../../language-reference/tokens/interpolated.md) .  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csFilesandFolders#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#3)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
- Soubor existuje a je určen jen pro čtení.  
  
- Název cesty je pravděpodobně příliš dlouhý.  
  
- Disk je pravděpodobně plný.  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Systém souborů a registr (C# Průvodce programováním)](./index.md)
- [Ukázka: uložení kolekce do úložiště aplikace](https://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
