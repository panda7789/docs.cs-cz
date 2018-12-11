---
title: 'Postupy: Zápis do textového souboru – C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
ms.openlocfilehash: e753f10acd33234d7f5e0c1a4203125ab880e2ae
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237139"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a>Postupy: Zápis do textového souboru (C# Průvodce programováním v)
Tyto příklady znázorňují různé způsoby zápisu textu do souboru. První dva příklady používají statické pohodlí metody <xref:System.IO.File?displayProperty=nameWithType> třídu pro zápis každý prvek žádné `IEnumerable<string>` a řetězce do textového souboru. Příklad 3 ukazuje, jak přidat text do souboru, když máte při psaní do souboru zpracovávat každý řádek zvlášť. Příklady 1 – 3 přepisují veškerý existující obsah v souboru, ale příkladu 4 se dozvíte, jak lze připojit text k existujícímu souboru.  
  
 Všechny tyto příklady zapisují řetězcové literály do souborů. Pokud chcete k formátování textu zapsána do souboru, použijte <xref:System.String.Format%2A> metody nebo C# [interpolace](../../../csharp/language-reference/tokens/interpolated.md) funkce.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csFilesandFolders#3](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-write-to-a-text-file_1.cs)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
-   Soubor existuje a je určen jen pro čtení.  
  
-   Název cesty je pravděpodobně příliš dlouhý.  
  
-   Disk je pravděpodobně plný.  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Systém souborů a registr (C# Programming Guide)](../../../csharp/programming-guide/file-system/index.md)  
- [Ukázka: Uložení kolekce do úložiště aplikací](https://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
