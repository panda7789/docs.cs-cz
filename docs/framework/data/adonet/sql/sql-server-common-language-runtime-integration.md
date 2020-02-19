---
title: Integrace CLR (Common Language Runtime) na SQL Serveru
ms.date: 03/30/2017
ms.assetid: c7a324c4-160d-44c2-b593-641af06eca61
ms.openlocfilehash: 12ae15d72644e314aa694f8d169bc8f45fa284a2
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452341"
---
# <a name="sql-server-common-language-runtime-integration"></a>Integrace CLR (Common Language Runtime) na SQL Serveru
SQL Server 2005 zavedl integraci komponenty modulu CLR (Common Language Runtime) .NET Framework pro systém Microsoft Windows. To znamená, že můžete zapisovat uložené procedury, triggery, uživatelsky definované typy, uživatelsky definované funkce, uživatelsky definované agregace a streamovat funkce vracející tabulku pomocí libovolného .NET Framework jazyka, včetně Microsoft Visual Basic .NET a Microsoft Visual C#. Obor názvů <xref:Microsoft.SqlServer.Server> obsahuje sadu nových aplikačních programovacích rozhraní (API), aby spravovaný kód mohl komunikovat s prostředím Microsoft SQL Server.  
  
 V této části jsou popsány funkce a chování, které jsou specifické pro SQL Server integraci modulu CLR (Common Language Runtime) a SQL Server specifických rozšíření pro ADO.NET.  
  
 Tato část je určena pouze k tomu, aby poskytovala dostatek informací, aby bylo možné začít programovat s SQL Server integrací CLR a není určeno pro komplexní. Podrobnější informace najdete v tématu verze SQL Server Knihy online pro verzi SQL Server, kterou používáte.  
  
 **Dokumentace SQL Serveru**  
  
1. [Koncepce programování pro integraci modulu CLR (Common Language Runtime)](/sql/relational-databases/clr-integration/common-language-runtime-clr-integration-programming-concepts)  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Úvod k integraci modulu CLR na SQL Serveru](introduction-to-sql-server-clr-integration.md)  
 Poskytuje Úvod do SQL Server integrace modulu CLR. Obsahuje odkazy na další témata.  
  
 [Uživatelem definované funkce CLR](clr-user-defined-functions.md)  
 Popisuje, jak implementovat a používat různé typy funkcí CLR: agregační funkce s hodnotami Table, skalární a uživatelsky definované agregační funkce.  
  
 [Uživatelem definované typy CLR](clr-user-defined-types.md)  
 Popisuje, jak implementovat a používat uživatelsky definované typy CLR. Obsahuje odkazy na další témata.  
  
 [Uložené procedury CLR](clr-stored-procedures.md)  
 Popisuje, jak implementovat a používat uložené procedury modulu CLR. Obsahuje odkazy na další témata.  
  
 [Aktivační procedury CLR](clr-triggers.md)  
 Popisuje, jak implementovat a používat triggery modulu CLR. Obsahuje odkazy na další témata.  
  
 [Kontextové připojení](the-context-connection.md)  
 Popisuje připojení kontextu.  
  
 [Chování ADO.NET specifické pro proces SQL Serveru](sql-server-in-process-specific-behavior-of-adonet.md)  
 Popisuje SQL Server v rámci procesu specifická rozšíření ADO.NET a připojení kontextu. Obsahuje odkazy na další témata.  
  
## <a name="see-also"></a>Viz také

- [SQL Server a ADO.NET](index.md)
- [Přehled ADO.NET](../ado-net-overview.md)
