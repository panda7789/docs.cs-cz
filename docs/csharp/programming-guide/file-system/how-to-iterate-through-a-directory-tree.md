---
title: 'Postupy: Iterace v adresářovém stromě - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- iterating through folders [C#]
- file iteration [C#]
ms.assetid: c4be4a75-6b1b-46a7-9d38-bab353091ed7
ms.openlocfilehash: 29f52728f0bfa9e78253fc2b39583e89f53198d6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61710800"
---
# <a name="how-to-iterate-through-a-directory-tree-c-programming-guide"></a>Postupy: Iterace v adresářovém stromu (C# Průvodce programováním v)
Fráze "iterace v adresářovém stromu" znamená, že pro přístup k každý soubor v každé vnořené podadresáři uvedený kořenový adresář na libovolnou hloubku. Nemáte nutně otevřete každý soubor. Můžete načíst jenom název souboru nebo podadresáře jako `string`, nebo můžete získat další informace ve formě <xref:System.IO.FileInfo?displayProperty=nameWithType> nebo <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> objektu.  
  
> [!NOTE]
>  Ve Windows jsou podmínky "directory" a "složku" používat Zaměnitelně. Většina dokumentace a uživatelské rozhraní text používá termín "složku", ale [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] knihovny tříd používá termín "adresáře."  
  
 V nejjednodušší případ, ve které nejste jisti, že máte oprávnění k přístupu pro všechny adresáře zadaného kořenu, můžete použít `System.IO.SearchOption.AllDirectories` příznak. Tento příznak vrátí vnořené podadresářů, které odpovídají zadanému vzoru. Následující příklad ukazuje, jak pomocí tohoto příznaku.  
  
```csharp  
root.GetDirectories("*.*", System.IO.SearchOption.AllDirectories);  
```  
  
 Slabé stránky v rámci tohoto přístupu je, že pokud některý z podadresáře v zadaném kořeni způsobí, že <xref:System.IO.DirectoryNotFoundException> nebo <xref:System.UnauthorizedAccessException>, celou metodu selže a vrátí žádné adresáře. Totéž platí při použití <xref:System.IO.DirectoryInfo.GetFiles%2A> metody. Pokud je potřeba zpracovat tyto výjimky konkrétní podsložek, musí ručně projít strom adresářové struktury, jak je znázorněno v následujícím příkladu.  
  
 Pokud ručně projít adresářovém stromu, můžete zpracovávat podadresáře nejprve (*předběžná objednávka procházení*), nebo soubory první (*pořadí po přechod zálohovaných*). Pokud provádíte procházení předběžná objednávka, provedou celý strom v aktuální složce před iterace soubory, které jsou přímo v samotné složce. Příklady dále v tomto dokumentu provést pořadí po přechod zálohovaných, ale můžete snadno upravit tak, aby provádět předběžná objednávka procházení.  
  
 Další možností je, zda se má použít rekurze nebo procházení založené na zásobníku. Příklady dále v tomto dokumentu se zobrazí oba přístupy.  
  
 Pokud máte k provádění různých operací se soubory a složky, můžete tyto příklady modularizaci refaktoringem operace do samostatné funkce, které lze vyvolat pomocí jediného delegáta.  
  
> [!NOTE]
>  Systémy souborů NTFS může obsahovat *body rozboru* ve formě *spojovacích bodů*, *symbolické odkazy*, a *pevné odkazy*. Metody rozhraní .NET Framework jako <xref:System.IO.DirectoryInfo.GetFiles%2A> a <xref:System.IO.DirectoryInfo.GetDirectories%2A> nevrátí všech podadresářích pod bodem rozboru. Toto chování se chrání před rizikem zadávání do nekonečné smyčky, pokud dva body rozboru používané k sobě navzájem. By měla obecně platí, buďte extrémně opatrní při řešil spojovacích bodů k zajištění, že nejsou neúmyslně upravíte nebo odstraníte soubory. Pokud potřebujete mít naprostou kontrolu nad body rozboru, použití vyvolání platformy i nativní kód do metody systému přímo volat odpovídající souboru Win32.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak procházet stromu adresáře pomocí rekurze. Rekurzivní přístup je elegantní, ale má potenciál způsobit výjimku přetečení zásobníku, pokud je adresářový strom velké a hluboce vnořený.  
  
 Konkrétní výjimky, které jsou zpracovány a konkrétní akce, které se provádí pro každý soubor nebo složku, jsou k dispozici pouze jako příklady. Upravte tento kód podle svých specifických požadavků. Komentáře v kódu pro další informace.  
  
 [!code-csharp[csFilesandFolders#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#1)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak k iteraci v rámci souborů a složek v adresářovém stromu bez použití rekurze. Tuto techniku používá Obecné <xref:System.Collections.Generic.Stack%601> typ kolekce, který se nachází poslední v zásobníku-first-out (LIFO).  
  
 Konkrétní výjimky, které jsou zpracovány a konkrétní akce, které se provádí pro každý soubor nebo složku, jsou k dispozici pouze jako příklady. Upravte tento kód podle svých specifických požadavků. Komentáře v kódu pro další informace.  
  
 [!code-csharp[csFilesandFolders#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#2)]  
  
 Obecně je příliš časově náročné otestovat všechny složky, které slouží k určení, jestli vaše aplikace má oprávnění k jeho otevření. Proto v příkladu kódu právě obklopuje operace v této části `try/catch` bloku. Můžete upravit `catch` blokovat tak, že když je odepřen přístup do složky, pokusíte zvýšení úrovně oprávnění a pak ho znovu přístup. Zpravidla zachycujte pouze takové výjimky, které dokáže zpracovat bez opuštění vaší aplikace v neznámém stavu.  
  
 Pokud musíte uložit obsah strom adresářové struktury v paměti nebo na disku, nejlepší možností je uložit pouze <xref:System.IO.FileSystemInfo.FullName%2A> vlastnosti (typu `string`) pro každý soubor. Potom můžete tento řetězec použít k vytvoření nového <xref:System.IO.FileInfo> nebo <xref:System.IO.DirectoryInfo> objektu podle potřeby, nebo otevřete každý soubor, který vyžaduje další zpracování.  
  
## <a name="robust-programming"></a>Robustní programování  
 Kód iterace robustní souboru musí vzít v úvahu mnoho složitostí systému souborů. Další informace o systému souborů Windows, naleznete v tématu [přehled systému souborů NTFS](/windows-server/storage/file-server/ntfs-overview).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO>
- [LINQ a souborové adresáře](../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
- [Systém souborů a registr (C# Programming Guide)](../../../csharp/programming-guide/file-system/index.md)
