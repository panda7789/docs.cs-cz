---
title: 'Postupy: Příprava na vyčerpání volného prostoru pomocí izolovaného úložiště'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data stores, quotas
- isolated storage, quotas
- quantity of isolated storage used
- limit on isolated storage used
- stores, quotas
- stores, out of space conditions
- data storage using isolated storage, quotas
- storing data using isolated storage, quotas
- space remaining in isolated storage
- data stores, out of space conditions
- storing data using isolated storage, out of space conditions
- quotas for isolated storage
- isolated storage, out of space conditions
- data storage using isolated storage, out of space conditions
ms.assetid: e35d4535-3732-421e-b1a3-37412e036145
ms.openlocfilehash: 5666019e1a65880221261ef5ad704f82c37263b2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708112"
---
# <a name="how-to-anticipate-out-of-space-conditions-with-isolated-storage"></a>Postupy: Příprava na vyčerpání volného prostoru pomocí izolovaného úložiště

Kód, který používá izolované úložiště, je omezen [kvótou,](../../../docs/standard/io/isolated-storage.md#quotas) která určuje maximální velikost datového oddílu, ve kterém existují soubory a adresáře izolovaného úložiště. Kvóta je definována zásadami zabezpečení a je konfigurovatelná správci. Pokud je při pokusu o zápis dat překročena maximální povolená velikost, je vyvolána <xref:System.IO.IsolatedStorage.IsolatedStorageException> výjimka a operace se nezdaří. To pomáhá zabránit škodlivým útokům odmítnutí služby, které by mohly způsobit, že aplikace odmítne požadavky, protože je vyplněno úložiště dat.

Chcete-li zjistit, zda daný pokus o zápis je <xref:System.IO.IsolatedStorage.IsolatedStorage> pravděpodobné, že selhání <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>z <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>tohoto <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>důvodu, třída poskytuje tři vlastnosti jen pro čtení: , a . Tyto vlastnosti můžete použít k určení, zda zápis do úložiště způsobí překročení maximální povolené velikosti úložiště. Mějte na paměti, že izolované úložiště lze přistupovat souběžně; Proto při výpočtu množství zbývající úložiště, úložný prostor může být spotřebována v době, kdy se pokusíte zapsat do úložiště. Maximální velikost úložiště však můžete použít k určení, zda má být dosaženo horního limitu dostupného úložiště.

Vlastnost <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> závisí na důkazy ze sestavení pracovat správně. Z tohoto důvodu byste měli načíst tuto vlastnost <xref:System.IO.IsolatedStorage.IsolatedStorageFile> pouze <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>u <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> objektů, které byly vytvořeny pomocí metody , nebo nebo. <xref:System.IO.IsolatedStorage.IsolatedStorageFile>objekty, které byly vytvořeny jiným způsobem (například <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> objekty, které byly vráceny z metody) nevrátí přesnou maximální velikost.

## <a name="example"></a>Příklad

Následující příklad kódu získá izolované úložiště, vytvoří několik souborů <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> a načte vlastnost. Zbývající místo je hlášeno v bajtů.

[!code-cpp[Conceptual.IsolatedStorage#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source7.cpp#8)]
[!code-csharp[Conceptual.IsolatedStorage#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source7.cs#8)]
[!code-vb[Conceptual.IsolatedStorage#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source7.vb#8)]

## <a name="see-also"></a>Viz také

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Izolované úložiště](../../../docs/standard/io/isolated-storage.md)
- [Postupy: Získávání úložišť pro izolované úložiště](../../../docs/standard/io/how-to-obtain-stores-for-isolated-storage.md)
