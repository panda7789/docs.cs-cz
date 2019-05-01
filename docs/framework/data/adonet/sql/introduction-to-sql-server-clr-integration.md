---
title: Úvod k integraci modulu CLR na SQL Serveru
ms.date: 03/30/2017
ms.assetid: 551d2290-ed80-49be-b377-44b32444da1c
ms.openlocfilehash: dc7d19bf361ed5fcda1fd5edf64eeb5e4ce15a71
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033875"
---
# <a name="introduction-to-sql-server-clr-integration"></a>Úvod k integraci modulu CLR na SQL Serveru
Common language runtime (CLR) je základem rozhraní Microsoft .NET Framework a poskytuje prostředí pro spuštění pro veškerý kód rozhraní .NET Framework. Kód, který běží v rámci modulu CLR se označuje jako spravovaný kód. CLR poskytuje různé funkce a služby potřebné pro spuštění programu, včetně kompilace just-in-time (JIT), přidělování a správu paměti a vynucuje bezpečnost typů, zpracování výjimek, správa vláken a zabezpečení.  
  
 S modulem CLR hostované v systému Microsoft SQL Server (označované jako integrace modulu CLR) můžete vytvořit uložené procedury, aktivační události, uživatelem definovaných funkcích, uživatelem definované typy a uživatelem definovaných agregacích ve spravovaném kódu. Protože spravovaný kód se zkompiluje do nativního kódu před provedením, můžete dosáhnout zvýšení výkonu v některých scénářích.  
  
 Spravovat kód používá zabezpečení přístupu kódu (CAS), odkazů na kód a aplikační domény, aby se zabránilo sestavení z provádění některých operací. Aby zabezpečení spravovaného kódu a nedošlo k ohrožení zabezpečení operačního systému nebo na serveru databáze používá systém SQL Server certifikační Autority.  
  
 Tato část poskytuje pouze dostatek informací, jak začít programovat díky integraci modulu CLR SQL serveru a není určena být vyčerpávající. Podrobnější informace najdete v tématu verze SQL Server Books Online pro verzi SQL serveru, který používáte.  
  
 **SQL Server Books Online**  
  
- [Integrace přehled modelu Common Language Runtime (CLR)](https://go.microsoft.com/fwlink/?LinkId=115242)  
  
## <a name="enabling-clr-integration"></a>Povolení integrace modulu CLR  
 Běžné funkce integrace language runtime (CLR) je vypnuto ve výchozím nastavení v systému Microsoft SQL Server a musí být povolené, aby bylo možné používat objekty, které jsou implementovány pomocí integrace modulu CLR. Chcete-li povolit integraci modulu CLR pomocí příkazů jazyka Transact-SQL, použijte `clr enabled` možnost `sp_configure` uložené procedury, jak je znázorněno:  
  
```  
sp_configure 'clr enabled', 1  
GO  
RECONFIGURE  
GO  
```  
  
 Integrace modulu CLR může zakázat nastavením `clr enabled` možnost na hodnotu 0. Při zakázání integrace modulu CLR SQL serveru zastaví provádění všechny rutiny v modulu CLR a uvolní všechny aplikační domény.  
  
 Podrobnější informace najdete v tématu verze SQL Server Books Online pro verzi SQL serveru, který používáte.  
  
 **SQL Server Books Online**  
  
- [Povolení integrace modulu CLR](https://go.microsoft.com/fwlink/?LinkId=115230)  
  
## <a name="deploying-a-clr-assembly"></a>Nasazení sestavení CLR  
 Jakmile základě metod modulu CLR byly testovány a ověřit na testovací server, můžete distribuovat do provozní servery s použitím skriptu nasazení. Skript nasazení můžete vygenerovat ručně nebo pomocí SQL Server Management Studio. Podrobnější informace najdete v tématu verze SQL Server Books Online pro verzi SQL serveru, který používáte.  
  
 **SQL Server Books Online**  
  
1. [Nasazení modulu CLR databázové objekty](https://go.microsoft.com/fwlink/?LinkId=115232)  
  
## <a name="clr-integration-security"></a>Zabezpečení integrace CLR  
 Model zabezpečení integrace systému Microsoft SQL Server pomocí rozhraní Microsoft .NET Framework common language runtime (CLR) spravuje a chrání přístup mezi různými typy objektů CLR a modulu CLR v rámci serveru SQL Server. Tyto objekty mohou být volány příkazu jazyka Transact-SQL nebo jiný objekt CLR spuštěná na serveru.  
  
 Podrobnější informace najdete v tématu verze SQL Server Books Online pro verzi SQL serveru, který používáte.  
  
 **SQL Server Books Online**  
  
- [Zabezpečení integrace CLR](https://go.microsoft.com/fwlink/?LinkId=115234)  
  
## <a name="debugging-a-clr-assembly"></a>Ladění sestavení CLR  
 Microsoft SQL Server poskytuje podporu pro ladění jazyka Transact-SQL a common language runtime (CLR) objekty v databázi. Ladění napříč jazyky funguje: uživatelé můžou kroku bez problémů do CLR objekty z příkazů jazyka Transact-SQL a naopak.  
  
 Podrobnější informace najdete v tématu verze SQL Server Books Online pro verzi SQL serveru, který používáte.  
  
 **SQL Server Books Online**  
  
- [Ladění CLR databázové objekty](https://go.microsoft.com/fwlink/?LinkId=115236)  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení přístupu ke kódu a ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
