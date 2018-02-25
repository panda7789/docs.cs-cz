---
title: "Postupy: Iterace v adresářovém stromě (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- iterating through folders [C#]
- file iteration [C#]
ms.assetid: c4be4a75-6b1b-46a7-9d38-bab353091ed7
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7f45bdc4a08922842b079be3ef9d112693ca5d7a
ms.sourcegitcommit: 75a180acb5d8a2dbd4a52915ce8e980749fb1d05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/24/2018
---
# <a name="how-to-iterate-through-a-directory-tree-c-programming-guide"></a>Postupy: Iterace v adresářovém stromě (Průvodce programováním v C#)
Fráze "iterace v adresářovém stromě" znamená přístup každý soubor v každé vnořené podadresáři složce zadaný kořenový na libovolnou hloubku. Nemáte nutně otevřete každý soubor. Název souboru nebo podadresáři jako můžete načíst právě `string`, nebo můžete získat další informace ve formě <xref:System.IO.FileInfo?displayProperty=nameWithType> nebo <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> objektu.  
  
> [!NOTE]
>  V systému Windows jsou podmínky "adresář" a "složka" použít zcela zaměnitelným významem. Většina dokumentace a uživatelské rozhraní text používá termín "složka", ale [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] knihovny tříd se pod pojmem "adresář."  
  
 V nejjednodušším případě, ve kterém nejste jisti, že máte oprávnění k přístupu pro všechny adresáře v rámci zadaného kořenové, můžete použít `System.IO.SearchOption.AllDirectories` příznak. Tento příznak vrátí všechny vnořené podadresáře, které odpovídají zadanému vzoru. Následující příklad ukazuje, jak používat tento příznak.  
  
```csharp  
root.GetDirectories("*.*", System.IO.SearchOption.AllDirectories);  
```  
  
 Slabé místo v tohoto přístupu je, že pokud kterákoli podadresáře v zadaném kořenovém způsobí, že <xref:System.IO.DirectoryNotFoundException> nebo <xref:System.UnauthorizedAccessException>, selže celý metodu a vrátí žádné adresáře. Totéž platí při použití <xref:System.IO.DirectoryInfo.GetFiles%2A> metoda. Pokud máte zpracování těchto výjimek na konkrétní podsložky, musí ručně provede stromu adresářů, jak je znázorněno v následujících příkladech.  
  
 Pokud jste ručně provede v adresářovém stromě, můžete nejdřív zpracovávat podadresáře (*před pořadí traversal*), nebo soubory první (*po pořadí traversal*). Pokud provádíte traversal předběžné pořadí, provede celý strom v aktuální složce před iterace v rámci soubory, které jsou přímo v samotné složce. Příklady později v tomto dokumentu provést po pořadí traversal, ale můžete je provést před pořadí traversal snadno upravit.  
  
 Další možností je, jestli se má používat rekurzi nebo základě zásobníku traversal. Později v tomto dokumentu příkladech obou přístupů.  
  
 Pokud máte k provádění různých operací u souborů a složek, můžete rozčlenění tyto příklady moduly pomocí operace do samostatné funkce, které můžete vyvolat pomocí jednoho delegáta refaktoringu.  
  
> [!NOTE]
>  Systémy souborů NTFS může obsahovat *body rozboru* ve formě *spojovacích bodů*, *symbolické odkazy*, a *pevné odkazy*. Metody rozhraní .NET Framework, jako <xref:System.IO.DirectoryInfo.GetFiles%2A> a <xref:System.IO.DirectoryInfo.GetDirectories%2A> nevrátí jakéhokoliv podadresáře pod bodem rozboru. Toto chování chrání před rizikem zadáním v nekonečné smyčce, při dva body rozboru odkazovat navzájem. Obecně platí by měl buďte velmi opatrní při řešit body rozboru používané k zajištění není neúmyslně upravovat a odstraňovat soubory. Pokud budete potřebovat přesnou kontrolu nad spojovací body, použití vyvolání platformy nebo nativní kód pro volání odpovídající souboru Win32 systému metody přímo.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vás v adresářovém stromě pomocí rekurze. Rekurzivní přístup je elegantní, ale má potenciál být příčinou výjimce přetečení zásobníku, pokud je adresářový strom velké a hluboko vložené.  
  
 Konkrétní výjimky, které jsou zpracovávány a konkrétní akce, které se provádí na každý soubor nebo složku, jsou k dispozici pouze jako příklady. Změňte tento kód podle specifických požadavků. Zobrazte komentáře v kódu pro další informace.  
  
 [!code-csharp[csFilesandFolders#1](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-iterate-through-a-directory-tree_1.cs)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak k iteraci v rámci soubory a složky v adresářovém stromu bez použití rekurze. Tento postup používá obecná <xref:System.Collections.Generic.Stack%601> typu kolekce, který je poslední v první out (LIFO) zásobníku.  
  
 Konkrétní výjimky, které jsou zpracovávány a konkrétní akce, které se provádí na každý soubor nebo složku, jsou k dispozici pouze jako příklady. Změňte tento kód podle specifických požadavků. Zobrazte komentáře v kódu pro další informace.  
  
 [!code-csharp[csFilesandFolders#2](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-iterate-through-a-directory-tree_2.cs)]  
  
 Obecně je příliš zdlouhavý otestovat všechny složky k určení, zda má oprávnění k jeho otevření aplikace. Proto příkladu kódu právě uzavře operace v příslušné části `try/catch` bloku. Můžete upravit `catch` blokovat tak, aby při je odepřen přístup do složky, pokusíte zvýšení oprávnění a poté přistoupit. Platí pouze catch tyto výjimky, které může zpracovat, aniž byste museli opustit vaší aplikace v neznámém stavu.  
  
 Pokud je třeba uložit obsah v adresářovém stromě v paměti nebo na disku, nejlepší možnost je k uložení pouze <xref:System.IO.FileSystemInfo.FullName%2A> vlastnost (typu `string`) pro každý soubor. Pak můžete použít tento řetězec pro vytvoření nového <xref:System.IO.FileInfo> nebo <xref:System.IO.DirectoryInfo> objektu podle potřeby nebo otevřít libovolný soubor, který vyžaduje další zpracování.  
  
## <a name="robust-programming"></a>Robustní programování  
 Kód iterace robustní souboru musí vzít v úvahu mnoho složité kroky systému souborů. Další informace o systému souborů najdete v tématu [technické informace o systému souborů NTFS](https://technet.microsoft.com/library/81cc8a8a-bd32-4786-a849-03245d68d8e4).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IO>  
 [LINQ a souborové adresáře](../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)  
 [Systém souborů a registr (C# Průvodce programováním)](../../../csharp/programming-guide/file-system/index.md)
