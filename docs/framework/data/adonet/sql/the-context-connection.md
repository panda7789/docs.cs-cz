---
title: Kontextové připojení
ms.date: 03/30/2017
ms.assetid: e443ca86-9243-4234-a822-ed10a53a9de0
ms.openlocfilehash: 26578d0c6a5e4553e57673561f94090b9a1fd1a5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791509"
---
# <a name="the-context-connection"></a>Kontextové připojení
Problémem interního přístupu k datům je poměrně běžný scénář. To znamená, že chcete získat přístup ke stejnému serveru, na kterém je spuštěna uložená procedura nebo funkce společného jazykového modulu runtime (CLR). Jednou z možností je vytvořit připojení pomocí <xref:System.Data.SqlClient.SqlConnection>, zadat připojovací řetězec, který odkazuje na místní server, a otevřít připojení. K tomu je potřeba zadat přihlašovací údaje pro přihlášení. Připojení je v jiné relaci databáze než uložená procedura nebo funkce, může mít různé `SET` možnosti, je v samostatné transakci, nezobrazuje vaše dočasné tabulky a tak dále. Pokud je vaše spravovaná uložená procedura nebo kód funkce prováděna v procesu SQL Server, je to proto, že někdo připojený k tomuto serveru a spustil příkaz SQL k jeho vyvolání. Pravděpodobně budete chtít, aby uložená procedura nebo funkce běžely v kontextu tohoto připojení, spolu s transakcí, `SET` možnostmi a tak dále. Označuje se jako připojení kontextu.  
  
 Připojení kontextu umožňuje spustit příkazy jazyka Transact-SQL ve stejném kontextu, jaký byl váš kód vyvolán na prvním místě. Podrobnější informace najdete v tématu verze SQL Server Knihy online pro verzi SQL Server, kterou používáte.  
  
 **SQL Server Books Online**  
  
1. [Kontextové připojení](https://go.microsoft.com/fwlink/?LinkId=115395)  
  
## <a name="see-also"></a>Viz také:

- [Přehled ADO.NET](../ado-net-overview.md)
