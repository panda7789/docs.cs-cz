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
- quanitity of isolated storage used
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 16b12a1ab274a63b8d190278d6312d36a61efe16
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44207717"
---
# <a name="how-to-anticipate-out-of-space-conditions-with-isolated-storage"></a>Postupy: Příprava na vyčerpání volného prostoru pomocí izolovaného úložiště
Kód, který používá izolované úložiště je omezen [kvóty](../../../docs/standard/io/isolated-storage.md#quotas) , která určuje maximální velikost pro datové přihrádky, ve kterém izolované úložiště souborů a adresářů existovat. Kvóta je definována v zásadách zabezpečení a je možné konfigurovat správci. Pokud je maximální povolená velikost je překročena, při pokusu o zápis dat, <xref:System.IO.IsolatedStorage.IsolatedStorageException> je vyvolána výjimka a operace se nezdaří. To pomáhá zabránit nebezpečné útoky s cílem odepření služeb, které by mohly způsobit, že aplikace odmítnout požadavky, protože úložný prostor zaplněný.  
  
 Při určování, zda je pravděpodobné, že z tohoto důvodu nezdaří pokus o zápis <xref:System.IO.IsolatedStorage.IsolatedStorage> třída poskytuje tři vlastnosti jen pro čtení: <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>, a <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>. Tyto vlastnosti můžete použít k určení, zda zápis do úložiště způsobí, že maximální povolenou velikost úložiště bude překročena. Uvědomte si, že izolované úložiště může přistupovat souběžně; Proto když můžete vypočítat množství zbývající úložiště, v prostoru úložiště by mohly spotřebovat čas, kdy se pokusíte o zápis do úložiště. Můžete však použít maximální velikost úložiště sloužící k určení, zda horního limitu úložiště k dispozici je asi tím dosáhnout.  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> Vlastnost závisí na důkazy od sestavení fungovalo správně. Z tohoto důvodu byste tuto vlastnost načíst pouze na <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objekty, které byly vytvořeny pomocí <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, nebo <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metody. <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objekty, které byly vytvořeny žádným jiným způsobem (například objekty, které byly vráceny z <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> metoda), nevrátí přesné maximální velikost.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu získá izolované úložiště, vytvoří několik souborů a načte <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> vlastnost. Zbývající velikost je uveden v bajtech.  
  
 [!code-cpp[Conceptual.IsolatedStorage#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source7.cpp#8)]
 [!code-csharp[Conceptual.IsolatedStorage#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source7.cs#8)]
 [!code-vb[Conceptual.IsolatedStorage#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source7.vb#8)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
- [Izolované úložiště](../../../docs/standard/io/isolated-storage.md)  
- [Postupy: Získávání úložišť pro izolované úložiště](../../../docs/standard/io/how-to-obtain-stores-for-isolated-storage.md)
