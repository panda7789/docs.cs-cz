---
title: Zabezpečení v LINQ to SQL
ms.date: 03/30/2017
ms.assetid: d49787f7-414e-4c71-aa33-80a5895536b1
ms.openlocfilehash: 6af073a86b0feaba2fdcd9facd9474bb334096e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62036995"
---
# <a name="security-in-linq-to-sql"></a>Zabezpečení v LINQ to SQL
Bezpečnostní rizika jsou vždy k dispozici, když se připojíte k databázi. I když LINQ to SQL může zahrnovat některé nové způsoby, jak pracovat s daty v systému SQL Server, neposkytuje žádné další bezpečnostní mechanismy.  
  
## <a name="access-control-and-authentication"></a>Řízení přístupu a ověřování  
 Technologie LINQ to SQL nemá vlastní mechanismy modelu nebo ověřování uživatelů. Pomocí zabezpečení SQL serveru můžete řídit přístup k databázi, databázové tabulky, zobrazení a uložených procedur, které jsou mapovány na objektový model. Udělit minimální požadovaný přístup pro uživatele a vyžadovat silná hesla k ověřování uživatelů.  
  
## <a name="mapping-and-schema-information"></a>Mapování a informace o schématu  
 V systému souborů je k dispozici pro všechny s přístupem k těmto souborům SQL a CLR databáze a mapování schématu informace o typu v objektovém modelu nebo externí mapování souboru. Předpokládejme, že bude k dispozici všem, kdo má přístup k modelu objektu nebo externí mapování souboru informací o schématu. Aby se zabránilo další rozšíření přístup na informace o schématu, použijte mechanismy zabezpečení souboru k zabezpečení zdrojových souborů a souborů mapování.  
  
## <a name="connection-strings"></a>Připojovací řetězce  
 Použití hesel v připojovacích řetězcích mělo by se vyhnout, kdykoli je to možné. Nejenže je připojovací řetězec ohrožení zabezpečení v sama o sobě, ale připojovací řetězec může také přidat ve formátu prostého textu objektový model nebo externí mapování souboru při použití nástroje příkazového řádku Návrhář relací objektů nebo SQLMetal. Každý, kdo má přístup k modelu objektu nebo externí mapování souboru prostřednictvím systému souborů (Pokud je zahrnutý v připojovacím řetězci) viděl heslo připojení.  
  
 Chcete-li minimalizovat rizika, používejte integrované zabezpečení pro důvěryhodného připojení se serverem SQL Server. Když použijete tento přístup, není nutné ukládat hesla v připojovacím řetězci. Další informace najdete v tématu [SQL Server – zabezpečení](../../../../../../docs/framework/data/adonet/sql/sql-server-security.md).  
  
 Chybí integrované zabezpečení bude potřeba heslo prostého textu v připojovacím řetězci. Nejlepší způsob, jak zabezpečit připojovací řetězec, ve vzestupném pořadí podle rizika, vypadá takto:  
  
- Použijte integrované zabezpečení.  
  
- Zabezpečený připojovací řetězce s hesly a minimalizovat předávání kolem připojovací řetězce.  
  
- Použití <xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType> třídy místo připojovacího řetězce, protože omezuje trvání vystavení. Technologie LINQ to SQL <xref:System.Data.Linq.DataContext?displayProperty=nameWithType> můžete vytvořit instanci třídy pomocí <xref:System.Data.SqlClient.SqlConnection>.  
  
- Minimalizovat životnosti a dotykového ovládání bodů pro všechny řetězce připojení.  
  
## <a name="see-also"></a>Viz také:

- [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [Nejčastější dotazy](../../../../../../docs/framework/data/adonet/sql/linq/frequently-asked-questions.md)
