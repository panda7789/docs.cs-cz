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
ms.openlocfilehash: d6fbc78c379951e05869a433875d057c49d44594
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969263"
---
# <a name="how-to-obtain-stores-for-isolated-storage"></a>Postupy: Získávání úložišť pro izolované úložiště
Izolované úložiště zpřístupňuje virtuální systém souborů v datovém oddílu. <xref:System.IO.IsolatedStorage.IsolatedStorageFile> Třída poskytuje řadu metod pro interakci s izolovaným úložištěm. Chcete-li vytvořit a načíst <xref:System.IO.IsolatedStorage.IsolatedStorageFile> úložiště, nabízí tři statické metody:  
  
- <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>vrátí úložiště, které je izolované uživatelem a sestavením.  
  
- <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>vrátí úložiště, které je izolované podle domény a sestavení.  
  
     Obě metody načtou úložiště, které patří do kódu, ze kterého jsou volány.  
  
- Statická metoda <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> vrací izolované úložiště, které je určeno předáním kombinace parametrů oboru.  
  
 Následující kód vrátí úložiště, které je izolované uživatelem, sestavením a doménou.  
  
 [!code-cpp[Conceptual.IsolatedStorage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#6)]
 [!code-csharp[Conceptual.IsolatedStorage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#6)]
 [!code-vb[Conceptual.IsolatedStorage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#6)]  
  
 Tuto <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metodu můžete použít k určení, že by úložiště mělo roaming s cestovním profilem uživatele. Podrobnosti o tom, jak tento postup nastavit, najdete v tématu [typy izolace](../../../docs/standard/io/types-of-isolation.md).  
  
 Izolované obchody získané v různých sestaveních jsou ve výchozím nastavení různými obchody. Můžete získat přístup k úložišti jiného sestavení nebo domény předáním do sestavení nebo legitimace domény v parametrech <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metody. To vyžaduje oprávnění pro přístup k izolovanému úložišti pomocí identity aplikační domény. Další informace naleznete v tématu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> přetížení metody.  
  
 Metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>a vrací<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> objekt<xref:System.IO.IsolatedStorage.IsolatedStorageFile> . K tomu, abyste se mohli rozhodnout, který typ izolace je pro vaši situaci nejvhodnější, přečtěte si téma [typy izolace](../../../docs/standard/io/types-of-isolation.md). Pokud máte izolovaný objekt úložiště, můžete použít metody izolovaného úložiště ke čtení, zápisu, vytváření a odstraňování souborů a adresářů.  
  
 Neexistuje žádný mechanismus, který brání kódu v předání <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objektu do kódu, který nemá dostatečný přístup k získání samotného úložiště. Identity domény a sestavení a oprávnění izolovaného úložiště jsou kontrolovány pouze <xref:System.IO.IsolatedStorage.IsolatedStorage> <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>v případě, že je získán odkaz na objekt, obvykle v metodě <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> , <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>nebo. Ochrana odkazů na <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objekty je proto odpovědností kódu, který používá tyto odkazy.  
  
## <a name="example"></a>Příklad  
 Následující kód poskytuje jednoduchý příklad třídy, která získá úložiště izolované uživatelem a sestavením. Kód může být změněn tak, aby načetl úložiště izolované uživatelem, doménou a sestavením přidáním <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType> k argumentům <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> , které Metoda projde.  
  
 Po spuštění kódu se můžete ujistit, že se vytvořilo úložiště, a to zadáním **Storeadm/list** do příkazového řádku. Spustí se [Nástroj izolovaného úložiště (Storeadm. exe)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md) a vypíše všechna aktuální izolovaná úložiště pro daného uživatele.  
  
 [!code-cpp[Conceptual.IsolatedStorage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#7)]
 [!code-csharp[Conceptual.IsolatedStorage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#7)]
 [!code-vb[Conceptual.IsolatedStorage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#7)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageScope>
- [Izolované úložiště](../../../docs/standard/io/isolated-storage.md)
- [Typy izolace](../../../docs/standard/io/types-of-isolation.md)
- [Sestavení v .NET](../assembly/index.md)
