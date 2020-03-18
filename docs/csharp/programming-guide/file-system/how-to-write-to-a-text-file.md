---
title: Jak psát do textového souboru - C# Programovací průvodce
ms.date: 07/20/2015
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
ms.openlocfilehash: ac16fb971eae5654a55e2f1753d78a6458f03315
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712244"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a>Jak psát do textového souboru (C# Programming Guide)
Tyto příklady znázorňují různé způsoby zápisu textu do souboru. První dva příklady používají statické <xref:System.IO.File?displayProperty=nameWithType> metody pohodlí na třídě `IEnumerable<string>` zapsat každý prvek any a řetězec do textového souboru. Příklad 3 ukazuje, jak přidat text do souboru, když je třeba zpracovat každý řádek jednotlivě při zápisu do souboru. Příklady 1-3 přepsat veškerý existující obsah v souboru, ale příklad 4 ukazuje, jak připojit text k existujícímu souboru.  
  
 Tyto příklady všechny zápis y řetězcové literály do souborů. Pokud chcete formátovat text napsaný do <xref:System.String.Format%2A> souboru, použijte metodu nebo funkci [interpolace řetězce](../../language-reference/tokens/interpolated.md) C#.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csFilesandFolders#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#3)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
- Soubor existuje a je určen jen pro čtení.  
  
- Název cesty je pravděpodobně příliš dlouhý.  
  
- Disk je pravděpodobně plný.  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Systém souborů a registr (Průvodce programováním v C#)](./index.md)
- [Ukázka: Uložení kolekce do úložiště aplikací](https://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
