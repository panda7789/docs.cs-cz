---
title: Odpovědnosti vývojáře při přepisu výchozího chování
ms.date: 03/30/2017
ms.assetid: c6909ddd-e053-46a8-980c-0e12a9797be1
ms.openlocfilehash: 12ea526d71946cdc7ab821f5e38948fcbb57d158
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59184766"
---
# <a name="responsibilities-of-the-developer-in-overriding-default-behavior"></a>Odpovědnosti vývojáře při přepisu výchozího chování
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nevynucuje následující požadavky, ale chování není definováno, pokud nejsou splněné tyto požadavky.  
  
-   Přepsání metody nesmějí provádět volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A> nebo <xref:System.Data.Linq.Table%601.Attach%2A>. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vyvolá výjimku, pokud tyto metody jsou volány v to metoda override.  
  
-   Přepsání metody nelze použít ke spuštění, potvrďte nebo ukončit transakci. <xref:System.Data.Linq.DataContext.SubmitChanges%2A> Operace v rámci transakce. Vnitřní vnořenou transakci může narušovat vnější transakci. Přepsání metody zatížení můžete spustit transakci, až poté, co určují, že operace neprobíhá v <xref:System.Transactions.Transaction>.  
  
-   Přepsání metody se očekává postupujte podle příslušných optimistického řízení souběžnosti mapování. Metoda přepsání je předpokládáno vyvolání <xref:System.Data.Linq.ChangeConflictException> nastane, pokud došlo ke konfliktu optimistického řízení souběžnosti. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tak, že můžete správně zpracovat tuto výjimku zachytí <xref:System.Data.Linq.DataContext.SubmitChanges%2A> možnost k dispozici na <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.  
  
-   Vytvořit (`Insert`) a `Update` přepsání metody se očekávají zpět hodnoty pro sloupce databáze vygenerovala odpovídající členů objektu po úspěšném dokončení operace.  
  
     Například pokud `Order.OrderID` je mapována na sloupec identity (*autoincrement* primární klíč), pak bude `InsertOrder()` přepsání metody musí načíst ID generovaných databází a nastavte `Order.OrderID` člen tohoto ID. Obdobně členy časové razítko se musí aktualizovat na databáze vygenerovala razítku abyste měli jistotu, že aktualizované objekty jsou konzistentní vzhledem k aplikacím. Chyba šíření hodnot generovaných databází může způsobit nekonzistence mezi databází a objekty sledován pomocí funkce <xref:System.Data.Linq.DataContext>.  
  
-   Zodpovídá za uživatele k vyvolání správné dynamického rozhraní API. Například v aktualizaci přepsat metodu, jenom <xref:System.Data.Linq.DataContext.ExecuteDynamicUpdate%2A> může být volána. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zjistit nebo ověřte, zda vyvolané dynamické metody odpovídá příslušné operace. Pokud je volána metodou nepoužitelných (například <xref:System.Data.Linq.DataContext.ExecuteDynamicDelete%2A> objektu aktualizovat), nejsou výsledky definovány.  
  
-   Nakonec přepsání metody by měl provádět uvedené operace. Sémantika [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] operace, jako jsou předběžné načítání, odložené načítání, a <xref:System.Data.Linq.DataContext.SubmitChanges%2A>) vyžadují se příslušná přepsání poskytovat uvedené služby. Například zatížení přepsání, která právě bez kontroly, že obsah v databázi pravděpodobně povede k nekonzistentní data vrací prázdnou kolekci.  
  
## <a name="see-also"></a>Viz také:

- [Přizpůsobení operací vložení, aktualizace a odstranění](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
