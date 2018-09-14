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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 09c112374458b70a464291e898e9a880c8679773
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45592981"
---
# <a name="how-to-find-existing-files-and-directories-in-isolated-storage"></a>Postupy: Hledání existujících souborů a adresářů v izolovaném úložišti
Chcete-li vyhledat adresář v izolovaném úložišti, použijte <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> metody. Tato metoda přebírá řetězec, který představuje vzor hledání. Jedním znakem (?) a více znak (*) můžete použít zástupné znaky v vzor hledání, ale zástupné znaky musí být uvedena v poslední části názvu. Například `directory1/*ect*` je platný hledaný řetězec, ale `*ect*/directory2` není.  
  
 Chcete-li vyhledat soubor, použijte <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> metody. Omezení zástupných znaků v řetězci pro vyhledávání, které se vztahuje na <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> platí také pro <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.  
  
 Ani jeden z těchto metod je rekurzivní. <xref:System.IO.IsolatedStorage.IsolatedStorageFile> třída neposkytuje žádné metody pro zobrazení seznamu všech adresářů a souborů v úložišti. Rekurzivní metody jsou však uvedeny v následujícím příkladu kódu.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak vytváření souborů a adresářů v izolovaném úložišti. Nejprve je úložiště, které je izolováno podle uživatele, domény a sestavení načten a umístí do `isoStore` proměnné. <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> Metoda se používá k několika různým adresářům, nastavení a <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> konstruktor vytvoří některé soubory v těchto adresářích. Kód poté prochází výsledky `GetAllDirectories` metody. Tato metoda používá <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> najít všechny názvy adresářů v aktuálním adresáři. Tyto názvy jsou uloženy v poli a potom `GetAllDirectories` zavolá sama sebe, předávání v každém adresáři se nenašel. V důsledku toho jsou všechny názvy adresářů vrátí ve formě pole. V dalším kroku kód volá `GetAllFiles` metody. Tato metoda volá `GetAllDirectories` Pokud chcete zjistit, názvy všech adresářů a poté zkontroluje každý adresář pro soubory pomocí <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> metody. Výsledek se vrátí v poli pro zobrazení.  
  
 [!code-cpp[Conceptual.IsolatedStorage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source8.cpp#9)]
 [!code-csharp[Conceptual.IsolatedStorage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source8.cs#9)]
 [!code-vb[Conceptual.IsolatedStorage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source8.vb#9)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
- [Izolované úložiště](../../../docs/standard/io/isolated-storage.md)
