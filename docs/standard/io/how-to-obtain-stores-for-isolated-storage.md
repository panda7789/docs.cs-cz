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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 604aabbff8554416d6794ff0b87188fb5bcc3185
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-obtain-stores-for-isolated-storage"></a>Postupy: Získávání úložišť pro izolované úložiště
Izolované úložiště zpřístupní virtuálním souborovém systému v rámci datový prostor. <xref:System.IO.IsolatedStorage.IsolatedStorageFile> Třída poskytuje několik metod pro interakci s izolované úložiště. Vytvoření a načtení úložiště, <xref:System.IO.IsolatedStorage.IsolatedStorageFile> poskytuje tři statické metody:  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> vrátí úložiště, která je izolovaná podle uživatele a sestavení.  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> vrátí úložiště, která je izolovaná podle domény a sestavení.  
  
     Obě metody načíst úložiště, které patří do kódu, ze které se nazývají.  
  
-   Statickou metodu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> vrátí izolované úložiště, které je určeno předáním kombinace parametrů rozsahu.  
  
 Následující kód vrátí úložiště, která je izolovaná uživatelem, sestavení a domény.  
  
 [!code-cpp[Conceptual.IsolatedStorage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#6)]
 [!code-csharp[Conceptual.IsolatedStorage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#6)]
 [!code-vb[Conceptual.IsolatedStorage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#6)]  
  
 Můžete použít <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metoda k určení, že úložiště spolu s cestovní profil uživatele. Podrobnosti o tom, jak nastavit tuto možnost najdete v tématu [typy izolace](../../../docs/standard/io/types-of-isolation.md).  
  
 Izolované úložiště získané v rámci různých sestavení jsou ve výchozím nastavení různých úložišť. V sestavení nebo domény důkaz v parametrech získáváte přístup úložišti domény nebo jiném sestavení předáním <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metoda. To vyžaduje oprávnění pro přístup k izolovanému úložišti podle identity domény aplikace. Další informace najdete v tématu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> přetížení metody.  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, A <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metody vrací <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objektu. Pomoc při rozhodování, který typ izolace je nejvhodnější pro vaši situaci, najdete v tématu [typy izolace](../../../docs/standard/io/types-of-isolation.md). Až budete mít objekt souboru izolovaného úložiště, můžete použít metody izolovaného úložiště pro čtení, zápisu, vytvořte a odstraňování souborů a adresářů.  
  
 Neexistuje žádný mechanismus, který zabrání předávání kódu <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objekt, který má kód, který nemá dostatečný přístup k získání samotného úložiště. Identity domény a sestavení a oprávnění izolovaného úložiště se kontroluje jenom v případě, že odkaz na <xref:System.IO.IsolatedStorage.IsolatedStorage> objekt získán, obvykle v <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, nebo <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metoda. Ochrana odkazů na <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objekty zodpovídá, tedy kód, který používá tyto odkazy.  
  
## <a name="example"></a>Příklad  
 Následující kód poskytuje jednoduchý příklad třídy pro získání úložiště, která je izolovaná podle uživatele a sestavení. Kód můžete změnit tak, aby načíst úložiště, která je izolovaná uživatele, domény a sestavení přidáním <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType> na argumenty, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> předává metoda.  
  
 Po spuštění kódu můžete potvrdit, že úložiště bylo vytvořeno zadáním **StoreAdm/list** na příkazovém řádku. Toto spouští [Nástroj izolovaného úložiště (Storeadm.exe)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md) a obsahuje všechna aktuální izolované úložiště pro uživatele.  
  
 [!code-cpp[Conceptual.IsolatedStorage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#7)]
 [!code-csharp[Conceptual.IsolatedStorage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#7)]
 [!code-vb[Conceptual.IsolatedStorage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#7)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageScope>  
 [Izolované úložiště](../../../docs/standard/io/isolated-storage.md)  
 [Typy izolace](../../../docs/standard/io/types-of-isolation.md)  
 [Sestavení v modulu CLR (Common Language Runtime)](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
