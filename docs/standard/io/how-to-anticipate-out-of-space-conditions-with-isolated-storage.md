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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708112"
---
# <a name="how-to-anticipate-out-of-space-conditions-with-isolated-storage"></a>Postupy: Příprava na vyčerpání volného prostoru pomocí izolovaného úložiště

Kód, který používá izolované úložiště, je omezený [kvótou](../../../docs/standard/io/isolated-storage.md#quotas) , která určuje maximální velikost datového oddílu, ve kterém existují izolované soubory úložiště a adresáře. Kvóta je definována zásadami zabezpečení a správci je můžou konfigurovat. Pokud při pokusu o zápis dat dojde k překročení maximální povolené velikosti, je vyvolána výjimka <xref:System.IO.IsolatedStorage.IsolatedStorageException> a operace se nezdařila. To pomáhá zabránit škodlivým útokům při odepření služby, které by mohly způsobit zamítnutí požadavků, protože úložiště dat je vyplněno.

Aby bylo možné určit, zda se daný pokus o zápis pravděpodobně z tohoto důvodu nezdaří, třída <xref:System.IO.IsolatedStorage.IsolatedStorage> poskytuje tři vlastnosti jen pro čtení: <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>a <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>. Tyto vlastnosti můžete použít k určení, jestli zápis do úložiště způsobí překročení maximální povolené velikosti úložiště. Pamatujte na to, že izolované úložiště je možné používat souběžně; Proto když počítáte množství zbývajících úložišť, může být prostor úložiště spotřebovaný při pokusu o zápis do úložiště. Můžete ale použít maximální velikost úložiště, která vám pomůže určit, jestli se má dosáhnout horní meze dostupného úložiště.

Vlastnost <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> závisí na tom, že legitimace sestavení správně funguje. Z tohoto důvodu byste měli tuto vlastnost načíst pouze v <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objektů, které byly vytvořeny pomocí metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>nebo <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>. <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objektů, které byly vytvořeny jakýmkoli jiným způsobem (například objekty, které byly vráceny z metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A>), nevrátí přesnou maximální velikost.

## <a name="example"></a>Příklad

Následující příklad kódu získá izolované úložiště, vytvoří několik souborů a načte vlastnost <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>. Zbývající místo je hlášeno v bajtech.

[!code-cpp[Conceptual.IsolatedStorage#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source7.cpp#8)]
[!code-csharp[Conceptual.IsolatedStorage#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source7.cs#8)]
[!code-vb[Conceptual.IsolatedStorage#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source7.vb#8)]

## <a name="see-also"></a>Viz také:

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Izolované úložiště](../../../docs/standard/io/isolated-storage.md)
- [Postupy: Získávání úložišť pro izolované úložiště](../../../docs/standard/io/how-to-obtain-stores-for-isolated-storage.md)
