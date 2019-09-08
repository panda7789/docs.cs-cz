---
title: Odpovědnosti vývojáře při přepisu výchozího chování
ms.date: 03/30/2017
ms.assetid: c6909ddd-e053-46a8-980c-0e12a9797be1
ms.openlocfilehash: 4bfb108e81f64ea368c6bcc846553eb1af5c23b1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792737"
---
# <a name="responsibilities-of-the-developer-in-overriding-default-behavior"></a>Odpovědnosti vývojáře při přepisu výchozího chování
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nevynutil následující požadavky, ale chování není definováno, pokud tyto požadavky nejsou splněny.  
  
- Přetěžující metoda nesmí volat <xref:System.Data.Linq.DataContext.SubmitChanges%2A> nebo <xref:System.Data.Linq.Table%601.Attach%2A>. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]vyvolá výjimku, pokud jsou tyto metody volány v metodě přepsání.  
  
- Metody přepsání nelze použít ke spuštění, potvrzení nebo zastavení transakce. <xref:System.Data.Linq.DataContext.SubmitChanges%2A> Operace se provádí v rámci transakce. Vnitřní vnořená transakce může kolidovat s vnější transakcí. Metody přepsání zatížení mohou spustit transakci až poté, co určí, že operace není prováděna v <xref:System.Transactions.Transaction>.  
  
- Pro metody přepsání se očekává, že budou následovat příslušné mapování optimistické souběžnosti. Metoda override se očekává, že vyvolá výjimku <xref:System.Data.Linq.ChangeConflictException> , když dojde ke konfliktu optimistické souběžnosti. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]zachycuje tuto výjimku, aby bylo možné správně zpracovat <xref:System.Data.Linq.DataContext.SubmitChanges%2A> možnost, která <xref:System.Data.Linq.DataContext.SubmitChanges%2A>je k dispozici na.  
  
- V případě`Insert`úspěšného `Update` dokončení operace se očekává, že metoda Create () a override přetéká zpátky hodnoty pro sloupce generované databáze pro odpovídající členy objektu.  
  
     Pokud `Order.OrderID` je například namapována na sloupec identity (*AutoIncrement* Primary Key `InsertOrder()` ), metoda override musí načíst ID vygenerované `Order.OrderID` databází a nastavit člena na toto ID. Podobně je nutné aktualizovat členy časových razítek na základě hodnot časových razítek generovaných databází, aby se zajistilo konzistence aktualizovaných objektů. Selhání šíření hodnot generovaných databází může způsobit nekonzistenci mezi databází a objekty, které jsou <xref:System.Data.Linq.DataContext>sledovány.  
  
- Je zodpovědností uživatele vyvolat správné dynamické rozhraní API. Například v metodě přepsání aktualizace <xref:System.Data.Linq.DataContext.ExecuteDynamicUpdate%2A> lze volat pouze. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nedetekuje ani neověřuje, zda vyvolaná dynamická metoda odpovídá příslušné operaci. Pokud je volána nepoužitelnou metoda (například <xref:System.Data.Linq.DataContext.ExecuteDynamicDelete%2A> pro objekt, který má být aktualizován), nejsou výsledky definovány.  
  
- Nakonec se očekává, že tato operace provede uvedenou operaci. Sémantika [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] operací, jako je Eager načítání, odložené načítání a <xref:System.Data.Linq.DataContext.SubmitChanges%2A>), vyžaduje přepsání k poskytnutí uvedené služby. Například přepsání zatížení, které vrací jenom prázdnou kolekci bez kontroly obsahu v databázi, může vést k nekonzistentním datům.  
  
## <a name="see-also"></a>Viz také:

- [Přizpůsobení operací vložení, aktualizace a odstranění](customizing-insert-update-and-delete-operations.md)
