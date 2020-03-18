---
title: 'Postupy: Získávání úložišť pro izolované úložiště'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- stores, obtaining
- storing data using isolated storage, obtaining stores
- isolated storage, obtaining stores
- data stores, obtaining
- data storage using isolated storage, obtaining stores
ms.assetid: fcb6b178-d526-47c4-b029-e946f880f9db
ms.openlocfilehash: 7104ba665f60c2d55217a2d8628c85f6e469ad6f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75706928"
---
# <a name="how-to-obtain-stores-for-isolated-storage"></a>Postupy: Získávání úložišť pro izolované úložiště
Izolované úložiště zpřístupňuje virtuální systém souborů v rámci datového prostoru. Třída <xref:System.IO.IsolatedStorage.IsolatedStorageFile> poskytuje řadu metod pro interakci s izolované úložiště. Chcete-li vytvořit <xref:System.IO.IsolatedStorage.IsolatedStorageFile> a načíst úložiště, poskytuje tři statické metody:  
  
- <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>vrátí úložiště, které je izolováno uživatelem a sestavením.  
  
- <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>vrátí úložiště, které je izolováno podle domény a sestavení.  
  
     Obě metody načíst úložiště, které patří do kódu, ze kterého jsou volány.  
  
- Statická <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metoda vrátí izolované úložiště, které je určeno předáním v kombinaci parametrů oboru.  
  
 Následující kód vrátí úložiště, které je izolováno uživatelem, sestavením a doménou.  
  
 [!code-cpp[Conceptual.IsolatedStorage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#6)]
 [!code-csharp[Conceptual.IsolatedStorage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#6)]
 [!code-vb[Conceptual.IsolatedStorage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#6)]  
  
 Tuto metodu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> můžete použít k určení, že úložiště by se mělo přemíslat s cestovním uživatelským profilem. Podrobnosti o tom, jak toto nastavení nastavit, naleznete [v tématu Typy izolace](../../../docs/standard/io/types-of-isolation.md).  
  
 Izolované obchody získané z různých sestavení jsou ve výchozím nastavení různé obchody. Můžete přistupovat k úložišti jiného sestavení nebo domény předáním v sestavení <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> nebo doméně důkazy v parametrech metody. To vyžaduje oprávnění k přístupu k izolovanému úložišti podle identity domény aplikace. Další informace naleznete <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> v metodě přetížení.  
  
 , <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>a <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metody vrátí <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objekt. Chcete-li se rozhodnout, který typ izolace je pro vaši situaci nejvhodnější, naleznete v [tématu Typy izolace](../../../docs/standard/io/types-of-isolation.md). Pokud máte izolovaný objekt souboru úložiště, můžete použít metody izolovaného úložiště ke čtení, zápisu, vytváření a odstraňování souborů a adresářů.  
  
 Neexistuje žádný mechanismus, který brání <xref:System.IO.IsolatedStorage.IsolatedStorageFile> kód předávací objekt do kódu, který nemá dostatečný přístup k získání samotného úložiště. Identity domény a sestavení a oprávnění izolovaného úložiště <xref:System.IO.IsolatedStorage.IsolatedStorage> jsou kontrolovány pouze v <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>případě, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> že je získán odkaz na objekt, obvykle v metodě , nebo metodě. Ochrana odkazů <xref:System.IO.IsolatedStorage.IsolatedStorageFile> na objekty je proto odpovědnost kódu, který používá tyto odkazy.  
  
## <a name="example"></a>Příklad  
 Následující kód poskytuje jednoduchý příklad třídy získání úložiště, které je izolováno uživatelem a sestavení. Kód lze změnit načíst úložiště, které je izolováno uživatelem, doménou a sestavením přidáním <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType> argumentů, které <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metoda předá.  
  
 Po spuštění kódu můžete potvrdit, že obchod byl vytvořen zadáním **StoreAdm /LIST** na příkazovém řádku. To spustí [nástroj izolované úložiště (Storeadm.exe)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md) a zobrazí seznam všech aktuálních izolovaných úložišť pro uživatele.  
  
 [!code-cpp[Conceptual.IsolatedStorage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#7)]
 [!code-csharp[Conceptual.IsolatedStorage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#7)]
 [!code-vb[Conceptual.IsolatedStorage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#7)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageScope>
- [Izolované úložiště](../../../docs/standard/io/isolated-storage.md)
- [Typy izolace](../../../docs/standard/io/types-of-isolation.md)
- [Sestavení v .NET](../assembly/index.md)
