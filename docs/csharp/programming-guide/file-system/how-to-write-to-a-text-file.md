---
title: Jak zapisovat do textového souboru – Průvodce programováním v C#
description: Naučte se, jak napsat textový soubor pomocí jazyka C#. Podívejte se na několik příkladů kódu a zobrazte další dostupné prostředky.
ms.date: 07/20/2015
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
ms.openlocfilehash: 4108163121d56268b810121ca3ae2b2c1338aeab
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301642"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a>Zápis do textového souboru (Průvodce programováním v C#)
Tyto příklady znázorňují různé způsoby zápisu textu do souboru. První dva příklady používají statické pohodlí pro <xref:System.IO.File?displayProperty=nameWithType> třídu pro zápis každého prvku libovolného `IEnumerable<string>` a řetězce do textového souboru. Příklad 3 ukazuje, jak přidat text do souboru, když je potřeba zpracovat jednotlivé řádky jednotlivě při zápisu do souboru. Příklady 1-3 přepisují veškerý existující obsah v souboru, ale příklad 4 ukazuje, jak připojit text k existujícímu souboru.  
  
 Tyto příklady všechny zapisují řetězcové literály do souborů. Pokud chcete naformátovat text zapsaný do souboru, použijte <xref:System.String.Format%2A> funkci nebo [řetězcové interpolace](../../language-reference/tokens/interpolated.md) v jazyce C#.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csFilesandFolders#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#3)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
- Soubor existuje a je určen jen pro čtení.  
  
- Název cesty je pravděpodobně příliš dlouhý.  
  
- Disk je pravděpodobně plný.  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v C#](../index.md)
- [Systém souborů a registr (Průvodce programováním v C#)](./index.md)
- [Ukázka: uložení kolekce do úložiště aplikace](https://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
