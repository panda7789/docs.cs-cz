---
title: Jak itetovat prostřednictvím adresářového stromu - C# Programovací průvodce
ms.date: 07/20/2015
helpviewer_keywords:
- iterating through folders [C#]
- file iteration [C#]
ms.assetid: c4be4a75-6b1b-46a7-9d38-bab353091ed7
ms.openlocfilehash: be3931a23e7a88affcf4d0abf617ec00bd35297a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712257"
---
# <a name="how-to-iterate-through-a-directory-tree-c-programming-guide"></a>Jak itetovat prostřednictvím adresářového stromu (C# Programming Guide)
Frázi "iterate adresářový strom" znamená přístup ke každému souboru v každém vnořeném podadresáři pod zadanou kořenovou složku, do libovolné hloubky. Nemusíte nutně otevírat každý soubor. Název souboru nebo podadresáře můžete načíst pouze jako `string`nebo můžete načíst <xref:System.IO.FileInfo?displayProperty=nameWithType> <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> další informace ve formě objektu nebo objektu.  
  
> [!NOTE]
> V systému Windows se zaměnitelně používají termíny "adresář" a "složka". Většina textu dokumentace a uživatelského rozhraní používá termín "složka", ale knihovna tříd rozhraní .NET Framework používá termín "adresář".  
  
 V nejjednodušším případě, ve kterém víte s jistotou, že máte přístupová oprávnění pro `System.IO.SearchOption.AllDirectories` všechny adresáře pod zadaným kořenem, můžete použít příznak. Tento příznak vrátí všechny vnořené podadresáře, které odpovídají zadanému vzoru. Následující příklad ukazuje, jak používat tento příznak.  
  
```csharp  
root.GetDirectories("*.*", System.IO.SearchOption.AllDirectories);  
```  
  
 Slabinou v tomto přístupu je, že pokud některý z <xref:System.IO.DirectoryNotFoundException> podadresářů pod zadaným kořenem způsobí, že a nebo <xref:System.UnauthorizedAccessException>, celá metoda selže a vrátí žádné adresáře. Totéž platí při použití <xref:System.IO.DirectoryInfo.GetFiles%2A> metody. Pokud máte ke zpracování těchto výjimek na konkrétní podsložky, je nutné ručně chodit adresářového stromu, jak je znázorněno v následujících příkladech.  
  
 Při ručním procházení adresářového stromu můžete nejprve zpracovat podadresáře *(předobjednávkový průchod)* nebo soubory jako první *(poobjednávkový průchod).* Pokud provedete předobjednávkový průchod, projdete celý strom pod aktuální složkou před iterace prostřednictvím souborů, které jsou přímo v této složce samotné. Příklady dále v tomto dokumentu provádět post-order traversal, ale můžete snadno upravit tak, aby provést pre-order traversal.  
  
 Další možností je, zda použít rekurze nebo průchod založený na zásobníku. Příklady dále v tomto dokumentu ukazují oba přístupy.  
  
 Pokud máte provádět různé operace se soubory a složkami, můžete modularizovat tyto příklady refaktoringem operace do samostatných funkcí, které můžete vyvolat pomocí jediného delegáta.  
  
> [!NOTE]
> Systémy souborů NTFS mohou obsahovat *body reparse* ve formě *spojovacích bodů*, *symbolických odkazů*a *pevných odkazů*. Metody rozhraní .NET <xref:System.IO.DirectoryInfo.GetFiles%2A> Framework, například a <xref:System.IO.DirectoryInfo.GetDirectories%2A> nevrátí žádné podadresáře pod bodem závažnosti. Toto chování chrání proti riziku vstupu do nekonečné smyčky, když dva body změny zpracování odkazují na sebe. Obecně platí, že při práci s body změny analýzy byste měli být velmi opatrní, abyste zajistili, že neúmyslně neupravujete nebo neodstraníte soubory. Pokud požadujete přesnou kontrolu nad body reparse, použijte platform invoke nebo nativní kód k přímému volání příslušných metod systému souborů Win32.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak chodit adresářového stromu pomocí rekurze. Rekurzivní přístup je elegantní, ale má potenciál způsobit výjimku přetečení zásobníku, pokud je strom adresářů velký a hluboce vnořený.  
  
 Konkrétní výjimky, které jsou zpracovány a konkrétní akce, které jsou prováděny v každém souboru nebo složky, jsou uvedeny pouze jako příklady. Tento kód byste měli upravit tak, aby splňoval vaše specifické požadavky. Další informace naleznete v komentářích v kódu.  
  
 [!code-csharp[csFilesandFolders#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#1)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak iteratovat soubory a složky ve stromu adresářů bez použití rekurze. Tato technika používá <xref:System.Collections.Generic.Stack%601> typ obecné kolekce, což je poslední v prvním out (LIFO) zásobníku.  
  
 Konkrétní výjimky, které jsou zpracovány a konkrétní akce, které jsou prováděny v každém souboru nebo složky, jsou uvedeny pouze jako příklady. Tento kód byste měli upravit tak, aby splňoval vaše specifické požadavky. Další informace naleznete v komentářích v kódu.  
  
 [!code-csharp[csFilesandFolders#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#2)]  
  
 Obecně je příliš časově náročné otestovat každou složku k určení, zda má vaše aplikace oprávnění k jeho otevření. Proto příklad kódu pouze uzavře tuto část operace `try/catch` v bloku. `catch` Blok můžete upravit tak, aby při odepření přístupu ke složce se pokusili zvýšit oprávnění a pak k němu znovu přistupovat. Jako pravidlo pouze zachytit ty výjimky, které můžete zpracovat bez opuštění aplikace v neznámém stavu.  
  
 Pokud je nutné uložit obsah adresářového stromu, buď v paměti nebo na <xref:System.IO.FileSystemInfo.FullName%2A> disk, `string`je nejlepší ukládat pouze vlastnost (typu) pro každý soubor. Tento řetězec pak můžete použít <xref:System.IO.FileInfo> k <xref:System.IO.DirectoryInfo> vytvoření nového nebo objektu podle potřeby nebo otevřít libovolný soubor, který vyžaduje další zpracování.  
  
## <a name="robust-programming"></a>Robustní programování  
 Robustní kód pro iteraci souborů musí brát v úvahu mnoho složitostí systému souborů. Další informace o systému souborů systému Windows naleznete v [tématu přehled systému souborů NTFS](/windows-server/storage/file-server/ntfs-overview).  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO>
- [LINQ a souborové adresáře](../concepts/linq/linq-and-file-directories.md)
- [Systém souborů a registr (Průvodce programováním v C#)](./index.md)
