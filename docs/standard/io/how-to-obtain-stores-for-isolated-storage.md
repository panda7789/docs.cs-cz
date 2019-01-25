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
ms.openlocfilehash: 0968443af28e2d403b08a1af50846e7a1369db49
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54524569"
---
# <a name="how-to-obtain-stores-for-isolated-storage"></a>Postupy: Získávání úložišť pro izolované úložiště
Izolované úložiště poskytuje virtuální systém souborů v rámci datové přihrádky. <xref:System.IO.IsolatedStorage.IsolatedStorageFile> Třída poskytuje několik metod pro interakci s izolované úložiště. K vytvoření a načtení úložišť, <xref:System.IO.IsolatedStorage.IsolatedStorageFile> poskytuje tři statické metody:  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> vrátí úložiště, které je izolováno podle uživatele a sestavení.  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> vrátí úložiště, která je izolovaná podle domény a sestavení.  
  
     Obě metody načíst úložiště, které patří do kódu, ve kterém jsou volány.  
  
-   Statická metoda <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> vrátí izolované úložiště, které je určeno předáním kombinací parametry oboru.  
  
 Následující kód vrátí úložiště, které je izolováno podle uživatele, sestavení a domény.  
  
 [!code-cpp[Conceptual.IsolatedStorage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#6)]
 [!code-csharp[Conceptual.IsolatedStorage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#6)]
 [!code-vb[Conceptual.IsolatedStorage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#6)]  
  
 Můžete použít <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metody k určení, že úložiště spolu s cestovní profil uživatele. Podrobnosti o tom, jak nastavit tuto možnost najdete v tématu [typy izolace](../../../docs/standard/io/types-of-isolation.md).  
  
 Izolované úložiště získané v rámci různých sestaveních jsou ve výchozím nastavení různých obchodech. Úložišti domény nebo jiném sestavení se zpřístupní po předání v legitimaci sestavení nebo domény v parametrech <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metody. To vyžaduje oprávnění pro přístup k izolovanému úložišti podle identity domény aplikace. Další informace najdete v tématu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> přetížení metody.  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, A <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metody vrátit <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objektu. Abyste mohli rozhodnout, jaký typ izolace je nejvhodnější pro vaši situaci, naleznete v tématu [typy izolace](../../../docs/standard/io/types-of-isolation.md). Až budete mít objekt souboru izolovaného úložiště, můžete použít metody izolovaného úložiště pro čtení, zápis, vytvářet a odstraňovat soubory a adresáře.  
  
 Neexistuje žádný mechanismus, který zabrání předání kódu <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objekt na kód, který nemá dostatečný přístup k získání samotného úložiště. Domény a sestavení identit a oprávnění izolovaného úložiště jsou kontrolovány pouze v případě, že odkaz na <xref:System.IO.IsolatedStorage.IsolatedStorage> objekt získán, obvykle v <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, nebo <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metody. Ochrana odkazů na <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objekty zodpovídá, proto kód, který používá tyto odkazy.  
  
## <a name="example"></a>Příklad  
 Následující kód nabízí jednoduchý příklad třídy získání úložiště, které je izolováno podle uživatele a sestavení. Kód lze změnit pro načtení úložiště, které je izolováno podle uživatele, domény a sestavení tak, že přidáte <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType> na argumenty, které <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metoda předává.  
  
 Po spuštění kódu můžete potvrdit, že úložiště bylo vytvořeno zadáním **/list StoreAdm** na příkazovém řádku. Toto řešení běží [Nástroj izolovaného úložiště (Storeadm.exe)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md) a jsou uvedeny všechny aktuální izolované úložiště pro uživatele.  
  
 [!code-cpp[Conceptual.IsolatedStorage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#7)]
 [!code-csharp[Conceptual.IsolatedStorage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#7)]
 [!code-vb[Conceptual.IsolatedStorage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#7)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageScope>
- [Izolované úložiště](../../../docs/standard/io/isolated-storage.md)
- [Typy izolace](../../../docs/standard/io/types-of-isolation.md)
- [Sestavení v modulu CLR (Common Language Runtime)](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
