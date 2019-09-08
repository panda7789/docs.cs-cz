---
title: Zabezpečení v LINQ to SQL
ms.date: 03/30/2017
ms.assetid: d49787f7-414e-4c71-aa33-80a5895536b1
ms.openlocfilehash: f1ebf2f72fbfe3b27b9fbfd41f0dd65c70103620
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781183"
---
# <a name="security-in-linq-to-sql"></a>Zabezpečení v LINQ to SQL
Bezpečnostní rizika jsou vždy přítomna při připojení k databázi. I když LINQ to SQL může zahrnovat některé nové způsoby práce s daty v SQL Server, neposkytuje žádné další mechanismy zabezpečení.  
  
## <a name="access-control-and-authentication"></a>Access Control a ověřování  
 LINQ to SQL nemá vlastní uživatelský model nebo ověřovací mechanismy. Pomocí SQL Server zabezpečení můžete řídit přístup k databázi, databázovým tabulkám, zobrazením a uloženým procedurám, které jsou namapovány na objektový model. Udělte minimálnímu požadovanému přístupu uživatelům a vyžadovat silná hesla pro ověřování uživatelů.  
  
## <a name="mapping-and-schema-information"></a>Mapování a informace o schématu  
 Mapování typů SQL-CLR a informace o schématu databáze v objektovém modelu nebo externím souboru mapování jsou k dispozici pro všechny s přístupem k souborům v systému souborů. Předpokládejte, že informace o schématu budou k dispozici všem uživatelům, kteří mají přístup k objektovému modelu nebo externímu souboru mapování. Aby nedocházelo k širšímu přístupu k informacím o schématu, použijte mechanismy zabezpečení souborů k zabezpečení zdrojových souborů a souborů mapování.  
  
## <a name="connection-strings"></a>Připojovací řetězce  
 Pokud je to možné, měli byste se vyhnout používání hesel v připojovacích řetězcích. Pouze připojovací řetězec je bezpečnostním řetězcem, který má své právo napravo, ale připojovací řetězec může být také přidán jako nešifrovaný text do objektového modelu nebo externího mapování souboru při použití Návrhář relací objektů nebo nástroje příkazového řádku SQLMetal. Kdokoli, kdo má přístup k objektovému modelu nebo k souboru externího mapování přes systém souborů, může zobrazit heslo připojení (Pokud je součástí připojovacího řetězce).  
  
 K minimalizaci takových rizik použijte integrované zabezpečení a vytvořte důvěryhodné připojení pomocí SQL Server. Pomocí tohoto přístupu není nutné ukládat heslo do připojovacího řetězce. Další informace najdete v tématu [SQL Server Security](../sql-server-security.md).  
  
 V případě nepřítomnosti integrovaného zabezpečení bude v připojovacím řetězci potřeba heslo pro vymazání textu. Nejlepším způsobem, jak přispět k zabezpečení připojovacího řetězce, je ve vzestupném pořadí rizika následující:  
  
- Použijte integrované zabezpečení.  
  
- Zabezpečte připojovací řetězce s hesly a minimalizujte předávání řetězců připojení.  
  
- Místo připojovacího řetězce použijte třídu,protožeomezujedobutrváníexpozice.<xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType> Pro třídu <xref:System.Data.Linq.DataContext?displayProperty=nameWithType> LINQ to SQL lze vytvořit instanci <xref:System.Data.SqlClient.SqlConnection>pomocí.  
  
- Minimalizujte životnost a dotykové body pro všechny připojovací řetězce.  
  
## <a name="see-also"></a>Viz také:

- [Základní informace](background-information.md)
- [Nejčastější dotazy](frequently-asked-questions.md)
