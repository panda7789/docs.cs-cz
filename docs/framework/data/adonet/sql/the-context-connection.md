---
title: Kontextové připojení
ms.date: 03/30/2017
ms.assetid: e443ca86-9243-4234-a822-ed10a53a9de0
ms.openlocfilehash: e237bb53c699fd4bf051876a378c31b73a038502
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451808"
---
# <a name="the-context-connection"></a>Kontextové připojení
Problémem interního přístupu k datům je poměrně běžný scénář. To znamená, že chcete získat přístup ke stejnému serveru, na kterém je spuštěna uložená procedura nebo funkce společného jazykového modulu runtime (CLR). Jednou z možností je vytvořit připojení pomocí <xref:System.Data.SqlClient.SqlConnection>, zadat připojovací řetězec, který odkazuje na místní server, a otevřít připojení. K tomu je potřeba zadat přihlašovací údaje pro přihlášení. Připojení je v jiné relaci databáze než uložená procedura nebo funkce, může se jednat o různé možnosti `SET`, je v samostatné transakci, nevidí vaše dočasné tabulky a tak dále. Pokud je vaše spravovaná uložená procedura nebo kód funkce prováděna v procesu SQL Server, je to proto, že někdo připojený k tomuto serveru a spustil příkaz SQL k jeho vyvolání. Pravděpodobně budete chtít, aby uložená procedura nebo funkce běžely v kontextu tohoto připojení, spolu s transakcí, `SET` možností a tak dále. Označuje se jako připojení kontextu.  
  
 Připojení kontextu umožňuje spustit příkazy jazyka Transact-SQL ve stejném kontextu, jaký byl váš kód vyvolán na prvním místě. Podrobnější informace najdete v tématu verze SQL Server Knihy online pro verzi SQL Server, kterou používáte.  
  
 **Dokumentace SQL Serveru**  
  
1. [Kontextové připojení](/sql/relational-databases/clr-integration/data-access/context-connection)  
  
## <a name="see-also"></a>Viz také

- [Přehled ADO.NET](../ado-net-overview.md)
