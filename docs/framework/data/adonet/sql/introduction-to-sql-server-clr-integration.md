---
title: "Úvod do integrace modulu CLR SQL serveru"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 551d2290-ed80-49be-b377-44b32444da1c
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e816339770cfea66e65157ddbb230d0aeeff35be
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="introduction-to-sql-server-clr-integration"></a>Úvod do integrace modulu CLR SQL serveru
Common language runtime (CLR) jsou srdcem rozhraní Microsoft .NET Framework a poskytuje prostředí pro spuštění pro všechny kód rozhraní .NET Framework. Kód, který běží v rámci modulu CLR se označuje jako spravovaného kódu. Modul CLR poskytuje různé funkce a služby jsou nezbytné pro spuštění programu, včetně kompilace za běhu (JIT), přidělování a správě paměti, vynucování bezpečnost typů, výjimek, vlákno správy a zabezpečení.  
  
 Pomocí modulu CLR hostované v systému Microsoft SQL Server (označovaný jako integrace modulu CLR) můžete vytvořit uložené procedury, triggery, uživatelem definovaných funkcích, uživatelem definované typy a uživatelem definovaných agregacích ve spravovaném kódu. Protože spravovaný kód zkompiluje do nativního kódu před spuštění, můžete dosáhnout zvýšení výkonu v některých scénářích.  
  
 Spravovaný kód používá zabezpečení přístupu kódu (CAS), odkazů na kód a aplikační domény, aby se zabránilo sestavení z provádění některých operací. SQL Server používá k zabezpečení spravovaného kódu a nedošlo k ohrožení zabezpečení operačního systému nebo na serveru databáze certifikační Autority.  
  
 Tato část poskytuje jenom dostatek informací, abyste mohli začít programování s integrace modulu CLR SQL serveru a není určen jako komplexní. Podrobnější informace najdete v tématu verze SQL Server Books Online pro verzi systému SQL Server, kterou používáte.  
  
 **SQL Server Books Online**  
  
-   [Běžné Přehled integrace Language Runtime (CLR)](http://go.microsoft.com/fwlink/?LinkId=115242)  
  
## <a name="enabling-clr-integration"></a>Povolení integrace modulu CLR  
 Běžné funkce integrace language runtime (CLR) ve výchozím nastavení v systému Microsoft SQL Server a musí být povolena, aby bylo možné používat objekty, které jsou implementovány pomocí integrace modulu CLR. Pokud chcete povolit integraci modulu CLR pomocí jazyka Transact-SQL, použijte `clr enabled` možnost `sp_configure` uložené procedury, jak je znázorněno:  
  
```  
sp_configure 'clr enabled', 1  
GO  
RECONFIGURE  
GO  
```  
  
 Integrace modulu CLR můžete zakázat nastavením `clr enabled` možnost na hodnotu 0. Pokud zakážete integrace modulu CLR, SQL Server zastaví provádění všechny rutiny modulu CLR a uvolní všechny domény aplikace.  
  
 Podrobnější informace najdete v tématu verze SQL Server Books Online pro verzi systému SQL Server, kterou používáte.  
  
 **SQL Server Books Online**  
  
-   [Povolení integrace modulu CLR](http://go.microsoft.com/fwlink/?LinkId=115230)  
  
## <a name="deploying-a-clr-assembly"></a>Nasazení sestavení CLR  
 Jakmile metod modulu CLR byly testovány a ověřit na testovacím serveru, lze rozdělit na produkční servery pomocí skriptu nasazení. Skript nasazení lze vytvořit ručně nebo pomocí SQL Server Management Studio. Podrobnější informace najdete v tématu verze SQL Server Books Online pro verzi systému SQL Server, kterou používáte.  
  
 **SQL Server Books Online**  
  
1.  [Nasazení databázové objekty CLR](http://go.microsoft.com/fwlink/?LinkId=115232)  
  
## <a name="clr-integration-security"></a>Zabezpečení integrace modulu CLR  
 Model zabezpečení integrace systému Microsoft SQL Server pomocí rozhraní Microsoft .NET Framework common language runtime (CLR) spravuje a zabezpečuje přístupu mezi různé typy CLR a bez CLR objektů, které jsou spuštěné v systému SQL Server. Tyto objekty může volat příkazu Transact-SQL nebo jiný objekt CLR běžícího na serveru.  
  
 Podrobnější informace najdete v tématu verze SQL Server Books Online pro verzi systému SQL Server, kterou používáte.  
  
 **SQL Server Books Online**  
  
-   [Zabezpečení integrace modulu CLR](http://go.microsoft.com/fwlink/?LinkId=115234)  
  
## <a name="debugging-a-clr-assembly"></a>Ladění sestavení CLR  
 Microsoft SQL Server poskytuje podporu pro ladění jazyka Transact-SQL a common language runtime (CLR) objekty v databázi. Ladění funguje napříč jazyky: uživatelé mohou kroku bezproblémově do CLR objekty z jazyka Transact-SQL a naopak.  
  
 Podrobnější informace najdete v tématu verze SQL Server Books Online pro verzi systému SQL Server, kterou používáte.  
  
 **SQL Server Books Online**  
  
-   [Ladění databázové objekty CLR](http://go.microsoft.com/fwlink/?LinkId=115236)  
  
## <a name="see-also"></a>Viz také  
 [Vytváření objektů serveru SQL Server 2005 ve spravovaném kódu](http://msdn.microsoft.com/en-us/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [Zabezpečení přístupu ke kódu a ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
