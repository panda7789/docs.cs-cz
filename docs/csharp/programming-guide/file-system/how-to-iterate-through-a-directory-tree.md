---
title: Postup iterace prostřednictvím adresářového stromu – Průvodce programováním v C#
ms.date: 07/20/2015
helpviewer_keywords:
- iterating through folders [C#]
- file iteration [C#]
ms.assetid: c4be4a75-6b1b-46a7-9d38-bab353091ed7
ms.openlocfilehash: 24a6225527becb0b896017616e2661ab8247c74c
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241601"
---
# <a name="how-to-iterate-through-a-directory-tree-c-programming-guide"></a>Postup iterace v adresářovém stromu (Průvodce programováním v C#)
Fráze "iterace stromu adresářů" znamená přístup ke každému souboru v každém vnořeném podadresáři v zadané kořenové složce, a to v jakékoli hloubce. Nemusíte nutně otevírat jednotlivé soubory. Můžete jednoduše načíst název souboru nebo podadresáře jako `string` , nebo můžete načíst další informace ve formě <xref:System.IO.FileInfo?displayProperty=nameWithType> <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> objektu nebo.  
  
> [!NOTE]
> V systému Windows se výrazy "adresář" a "složka" používají zaměnitelné. Většina dokumentace a text uživatelského rozhraní používá termín "složka", ale knihovny tříd .NET používají pojem "adresář".  
  
 V nejjednodušším případě, ve kterém víte, že máte přístupová oprávnění ke všem adresářům v zadaném kořenu, můžete použít `System.IO.SearchOption.AllDirectories` příznak. Tento příznak vrátí všechny vnořené podadresáře, které odpovídají zadanému vzoru. Následující příklad ukazuje, jak použít tento příznak.  
  
```csharp  
root.GetDirectories("*.*", System.IO.SearchOption.AllDirectories);  
```  
  
 Slabé stránky v tomto přístupu je to, že pokud některý z podadresářů v rámci zadaného kořenu způsobí <xref:System.IO.DirectoryNotFoundException> nebo <xref:System.UnauthorizedAccessException> , pak celá metoda neproběhne a nevrátí žádné adresáře. Totéž platí, pokud použijete <xref:System.IO.DirectoryInfo.GetFiles%2A> metodu. Pokud je nutné tyto výjimky zpracovat u konkrétních podsložek, je nutné ručně projít adresářový strom, jak je znázorněno v následujících příkladech.  
  
 Když ručně provedete strom adresářů, můžete nejprve zpracovat podadresáře (*před procházením*) nebo nejprve soubory (*Procházet po objednání*). Pokud provedete předběžné pořadí procházení, provedete celý strom v rámci aktuální složky před iterací souborů, které jsou přímo v této složce. Příklady dále v tomto dokumentu provádějí procházení po jednotlivých objednávkách, ale můžete je snadno upravit, aby se prováděly předběžné pořadí procházení.  
  
 Další možností je, zda použít rekurzi nebo procházení založené na zásobníku. Příklady níže v tomto dokumentu ukazují oba přístupy.  
  
 Pokud potřebujete provést různé operace se soubory a složkami, můžete naplánovat modularizaci tyto příklady refaktoringem operace do samostatných funkcí, které můžete vyvolat pomocí jednoho delegáta.  
  
> [!NOTE]
> Systémy souborů NTFS můžou obsahovat *body rozboru* ve formě *spojovacích bodů*, *symbolických odkazů*a *pevných odkazů*. Metody .NET, jako například <xref:System.IO.DirectoryInfo.GetFiles%2A> a, nebudou <xref:System.IO.DirectoryInfo.GetDirectories%2A> vracet žádné podadresáře v rámci spojovacího bodu. Toto chování chrání před rizikem vstupu do nekonečné smyčky, když dva body rozboru odkazují na sebe navzájem. Obecně platí, že byste měli při práci s body rozboru použít extrémní opatrnost, abyste se ujistili, že neúmyslně neupravují ani neodstraňují soubory. Pokud potřebujete přesnou kontrolu nad body rozboru, použijte vyvolání nebo nativní kód platformy k přímému volání odpovídajících metod systému souborů Win32.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak projít adresářový strom pomocí rekurze. Rekurzivní přístup je elegantní, ale má potenciál způsobit výjimku přetečení zásobníku, pokud je strom adresáře velký a hluboko vnořený.  
  
 Konkrétní výjimky, které jsou zpracovávány, a konkrétní akce, které jsou provedeny u jednotlivých souborů nebo složek, jsou uvedeny pouze jako příklady. Tento kód byste měli upravit tak, aby splňoval vaše konkrétní požadavky. Další informace najdete v komentářích v kódu.  
  
 [!code-csharp[csFilesandFolders#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#1)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak iterovat soubory a složky ve stromu adresářů bez použití rekurze. Tato technika používá typ obecné <xref:System.Collections.Generic.Stack%601> kolekce, což je poslední v zásobníku LIFO.  
  
 Konkrétní výjimky, které jsou zpracovávány, a konkrétní akce, které jsou provedeny u jednotlivých souborů nebo složek, jsou uvedeny pouze jako příklady. Tento kód byste měli upravit tak, aby splňoval vaše konkrétní požadavky. Další informace najdete v komentářích v kódu.  
  
 [!code-csharp[csFilesandFolders#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#2)]  
  
 Je obvykle příliš časově náročná na testování každé složky, aby bylo možné určit, zda má vaše aplikace oprávnění k jejímu otevření. Proto příklad kódu pouze obklopuje část operace v `try/catch` bloku. Blok můžete změnit `catch` tak, aby při odepření přístupu ke složce se pokusili zvýšit oprávnění a pak k nim znovu získat přístup. Jako pravidlo Zachyťte pouze ty výjimky, které lze zpracovat bez ukončení aplikace v neznámém stavu.  
  
 Pokud je nutné uložit obsah stromu adresáře, buď v paměti nebo na disku, je nejlepší možností uložit pouze <xref:System.IO.FileSystemInfo.FullName%2A> vlastnost (typu `string` ) pro každý soubor. Pak můžete použít tento řetězec k vytvoření nového <xref:System.IO.FileInfo> <xref:System.IO.DirectoryInfo> objektu nebo v případě potřeby, nebo otevřít libovolný soubor, který vyžaduje další zpracování.  
  
## <a name="robust-programming"></a>Robustní programování  
 Robustní kód pro iteraci souborů musí brát v úvahu mnoho složitých operací systému souborů. Další informace o systému souborů systému Windows najdete v tématu [Přehled systému souborů NTFS](/windows-server/storage/file-server/ntfs-overview).  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO>
- [LINQ a souborové adresáře](../concepts/linq/linq-and-file-directories.md)
- [Systém souborů a registr (Průvodce programováním v C#)](./index.md)
