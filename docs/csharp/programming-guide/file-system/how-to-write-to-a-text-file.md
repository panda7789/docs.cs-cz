---
title: "Postupy: Zápis do textového souboru (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c576536947cdb4984d6e5ce67c8377fe23b354c7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a>Postupy: Zápis do textového souboru (Průvodce programováním v C#)
Tyto příklady znázorňují různé způsoby zápisu textu do souboru.  První dva příklady používají statické usnadňující metody na <xref:System.IO.File?displayProperty=nameWithType> třída pro psaní každý prvek žádné rozhraní IEnumerable\<řetězec > a řetězec do textového souboru.  Příklad 3 ukazuje, jak přidat text do souboru při každém řádku jednotlivě zpracovat, protože zapisovat do souboru.  Příklady 1 – 3 přepsat všechny existující obsah v souboru, ale příklad 4 ukazuje, jak přidat text do existující soubor.  
  
 Tyto příklady všechny textové literály zápis do souborů, ale více pravděpodobně budete chtít použít <xref:System.String.Format%2A> metoda, která má mnoho ovládacích prvků pro zápis různé typy hodnot zarovnané vlevo nebo vpravo v poli, s nebo bez odsazení a tak dále.  Můžete také použít jazyka C# [řetězec interpolace](../../../csharp/language-reference/keywords/interpolated-strings.md) funkce.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csFilesandFolders#3](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-write-to-a-text-file_1.cs)]  
  
 Tyto příklady všechny textové literály zápis do souborů, ale více pravděpodobně budete chtít použít <xref:System.String.Format%2A> metoda, která má mnoho ovládacích prvků pro zápis různé typy hodnot zarovnané vlevo nebo vpravo v poli, s nebo bez odsazení a tak dále.  Můžete také použít jazyka C# [řetězec interpolace](../../../csharp/language-reference/keywords/interpolated-strings.md) funkce.  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
-   Soubor existuje a je určen jen pro čtení.  
  
-   Název cesty je pravděpodobně příliš dlouhý.  
  
-   Disk je pravděpodobně plný.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Systém souborů a registr (C# Průvodce programováním)](../../../csharp/programming-guide/file-system/index.md)  
 [Ukázka: Uložit kolekci do úložiště aplikací](http://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
