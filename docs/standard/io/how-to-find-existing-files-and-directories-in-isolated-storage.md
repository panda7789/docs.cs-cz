---
title: 'Postupy: Hledání existujících souborů a adresářů v izolovaném úložišti'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- stores, finding files and directories
- locating files in isolated storage file
- directories [.NET Framework], isolated storage
- isolated storage, finding files and directories
- data storage using isolated storage, finding files and directories
- files [.NET Framework], isolated storage
- data stores, finding files and directories
- locating directories in isolated storage file
- storing data using isolated storage, finding files and directories
ms.assetid: eb28458a-6161-4e7a-9ada-30ef93761b5c
ms.openlocfilehash: dfebcc9acf0b699f898c106921d15ce0294bc5d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75707130"
---
# <a name="how-to-find-existing-files-and-directories-in-isolated-storage"></a>Postupy: Hledání existujících souborů a adresářů v izolovaném úložišti

Chcete-li vyhledat adresář v izolovaném úložišti, použijte metodu. <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> Tato metoda trvá řetězec, který představuje vzor hledání. Ve vzorku hledání můžete použít znakové znaky\*(?) i znaky s více znaky , ale zástupné znaky se musí objevit v poslední části názvu. Například `directory1/*ect*` je platný vyhledávací řetězec, ale `*ect*/directory2` není.  
  
 Chcete-li vyhledat soubor, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> použijte metodu. Omezení zástupných znaků ve vyhledávacích řetězcích, které <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>platí také pro .  
  
 Ani jedna z těchto metod není rekurzivní; třída <xref:System.IO.IsolatedStorage.IsolatedStorageFile> neposkytuje žádné metody pro výpis všech adresářů nebo souborů ve vašem obchodě. Rekurzivní metody jsou však zobrazeny v následujícím příkladu kódu.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak vytvořit soubory a adresáře v izolovaném úložišti. Nejprve úložiště, které je izolováno pro uživatele, doménu `isoStore` a sestavení, je načteno a umístěno do proměnné. Metoda <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> se používá k nastavení několika různých adresářů a <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> konstruktor vytvoří některé soubory v těchto adresářích. Kód pak smyčky prostřednictvím výsledků `GetAllDirectories` metody. Tato metoda <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> používá k vyhledání všech názvů adresářů v aktuálním adresáři. Tyto názvy jsou uloženy `GetAllDirectories` v poli a pak volá sám, předávání v každém adresáři, který našel. V důsledku toho jsou všechny názvy adresářů vráceny v poli. Dále kód volá `GetAllFiles` metodu. Tato metoda `GetAllDirectories` volá zjistit názvy všech adresářů a potom zkontroluje každý <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> adresář pro soubory pomocí metody. Výsledek je vrácen v poli pro zobrazení.  
  
 [!code-cpp[Conceptual.IsolatedStorage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source8.cpp#9)]
 [!code-csharp[Conceptual.IsolatedStorage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source8.cs#9)]
 [!code-vb[Conceptual.IsolatedStorage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source8.vb#9)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Izolované úložiště](../../../docs/standard/io/isolated-storage.md)
