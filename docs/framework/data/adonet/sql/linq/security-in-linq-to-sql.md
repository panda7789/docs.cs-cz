---
title: Zabezpečení v technologii LINQ to SQL
ms.date: 03/30/2017
ms.assetid: d49787f7-414e-4c71-aa33-80a5895536b1
ms.openlocfilehash: b2c7de75295722da643d64ff22bc769e0633629d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33364392"
---
# <a name="security-in-linq-to-sql"></a>Zabezpečení v technologii LINQ to SQL
Rizika zabezpečení jsou vždy k dispozici, při připojení k databázi. I když technologie LINQ to SQL může zahrnovat některých nových způsobech pracovat s daty v systému SQL Server, neposkytuje žádné další bezpečnostní mechanismy.  
  
## <a name="access-control-and-authentication"></a>Řízení přístupu a ověřování  
 Technologie LINQ to SQL nemá vlastní mechanismy modelu nebo ověřování uživatele. Používejte k řízení přístupu k databázi, databázových tabulek, zobrazení a uložených procedur, které jsou mapované na objektový model zabezpečení SQL serveru. Udělení přístupu minimální požadované uživatelům a vyžadovat silná hesla pro ověření uživatele.  
  
## <a name="mapping-and-schema-information"></a>Mapování a informace o schématu  
 SQL CLR typ mapování a databáze informace o schématu v modelu objektu nebo externí mapování souboru je k dispozici pro všechny s přístupem k těmto souborům v systému souborů. Předpokládejme, že bude k dispozici všem, kdo má přístup k modelu objektu nebo externí mapování souboru informace o schématu. Abyste zabránili rozšiřujících přístupu k informace o schématu, použijte k zabezpečení zdrojové soubory a soubory mapování mechanismy zabezpečení souboru.  
  
## <a name="connection-strings"></a>Připojovací řetězce  
 Použití hesel v připojovací řetězce je nutno kdykoli je to možné. Jenom je připojovací řetězec ohrožení zabezpečení v sobě, ale připojovací řetězec může také přidat ve formátu prostého textu objektový model nebo externí mapování souboru při pomocí nástroje příkazového řádku Návrhář relací objektů nebo SQLMetal. Každý, kdo má přístup k modelu objektu nebo externí mapování souboru prostřednictvím systému souborů by mohli zobrazit heslo připojení (Pokud je zahrnutý v připojovacím řetězci).  
  
 Chcete-li minimalizovat těchto rizik, použijte integrované zabezpečení vytvoření důvěryhodných připojení se serverem SQL Server. Pomocí tohoto přístupu nemáte uložit heslo v připojovacím řetězci. Další informace najdete v tématu [zabezpečení SQL serveru](../../../../../../docs/framework/data/adonet/sql/sql-server-security.md).  
  
 Chybí integrované zabezpečení bude potřeba textové heslo v připojovacím řetězci. Nejlepší způsob, jak pomoc se zabezpečením připojovací řetězec, ve vzestupném pořadí rizika, vypadá takto:  
  
-   Použijte integrované zabezpečení.  
  
-   Zabezpečené připojovací řetězce s hesly a minimalizovat předávání kolem připojovací řetězce.  
  
-   Použití <xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType> třída místo připojovací řetězec, protože se omezuje trvání ohrožení. Technologie LINQ to SQL <xref:System.Data.Linq.DataContext?displayProperty=nameWithType> může vytvořit instanci třídy pomocí <xref:System.Data.SqlClient.SqlConnection>.  
  
-   Minimalizovat životnosti a touch bodů pro všechny řetězce připojení.  
  
## <a name="see-also"></a>Viz také  
 [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [Nejčastější dotazy](../../../../../../docs/framework/data/adonet/sql/linq/frequently-asked-questions.md)
