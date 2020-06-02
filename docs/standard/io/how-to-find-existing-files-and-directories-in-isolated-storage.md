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
ms.openlocfilehash: ec1d1fbdefdad3ec0dd2c07fbc1278e4d1d217c6
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291848"
---
# <a name="how-to-find-existing-files-and-directories-in-isolated-storage"></a>Postupy: Hledání existujících souborů a adresářů v izolovaném úložišti

Chcete-li vyhledat adresář v izolovaném úložišti, použijte <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> metodu. Tato metoda přebírá řetězec, který představuje vzor hledání. Ve vzoru vyhledávání můžete použít zástupné znaky s jedním znakem (?) i více znaky ( \* ), ale zástupné znaky se musí objevit v poslední části názvu. Například `directory1/*ect*` je platný hledaný řetězec, ale není `*ect*/directory2` .  
  
 Chcete-li vyhledat soubor, použijte <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> metodu. Omezení pro zástupné znaky ve vyhledávacích řetězcích, které platí pro, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> platí také pro <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> .  
  
 Ani jedna z těchto metod není rekurzivní; <xref:System.IO.IsolatedStorage.IsolatedStorageFile>Třída neposkytuje žádné metody pro výpis všech adresářů nebo souborů ve vašem úložišti. Nicméně rekurzivní metody jsou uvedeny v následujícím příkladu kódu.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak vytvořit soubory a adresáře v izolovaném úložišti. Nejprve se načte úložiště, které je izolované pro uživatele, doménu a sestavení, a umístí je do `isoStore` proměnné. <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A>Metoda se používá k nastavení několika různých adresářů a <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> konstruktor vytvoří některé soubory v těchto adresářích. Kód pak projde výsledky `GetAllDirectories` metody. Tato metoda používá <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> k vyhledání všech názvů adresářů v aktuálním adresáři. Tyto názvy jsou uloženy v poli a následně se `GetAllDirectories` zavolají do každého adresáře, který nalezl. V důsledku toho jsou všechny názvy adresářů vráceny v poli. Dále kód volá `GetAllFiles` metodu. Tato metoda volá `GetAllDirectories` k zjištění názvů všech adresářů a pak zkontroluje každý adresář pro soubory pomocí <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> metody. Výsledek je vrácen v poli pro zobrazení.  
  
 [!code-cpp[Conceptual.IsolatedStorage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source8.cpp#9)]
 [!code-csharp[Conceptual.IsolatedStorage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source8.cs#9)]
 [!code-vb[Conceptual.IsolatedStorage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source8.vb#9)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Izolované úložiště](isolated-storage.md)
