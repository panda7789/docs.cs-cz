---
title: Oracle a ADO.NET
description: Seznamte se s funkcemi a chováním .NET Framework Zprostředkovatel dat pro Oracle, který poskytuje přístup k databázi Oracle pomocí rozhraní volání Oracle.
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: 8757352a7444fad802ea88ba58e0fe643c86cbb8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286686"
---
# <a name="oracle-and-adonet"></a>Oracle a ADO.NET
> [!NOTE]
> Typy v <xref:System.Data.OracleClient> jsou zastaralé. Typy zůstanou podporované v aktuální verzi rozhraní of.NET Framework, ale v budoucí verzi se odeberou. Microsoft doporučuje, abyste použili poskytovatele Oracle od jiného výrobce.  
  
 Tato část popisuje funkce a chování, které jsou specifické pro Zprostředkovatel dat .NET Framework pro Oracle.  
  
 Zprostředkovatel dat .NET Framework pro Oracle poskytuje přístup k databázi Oracle pomocí rozhraní Oracle Call Interface (OCI), které poskytuje klientský software Oracle. Funkce poskytovatele dat je navržena tak, aby byla podobná poskytovateli .NET Framework dat pro SQL Server, OLE DB a ODBC.  
  
 Chcete-li použít Zprostředkovatel dat .NET Framework pro Oracle, musí aplikace odkazovat na <xref:System.Data.OracleClient> obor názvů následujícím způsobem:  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 Při kompilaci kódu je také nutné zahrnout odkaz na knihovnu DLL. Například pokud kompilujete program v jazyce C#, příkazový řádek by měl obsahovat:  
  
```console
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Požadavky na systém](system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 Popisuje požadavky na použití Zprostředkovatel dat .NET Framework pro Oracle a popisuje několik problémů, které je potřeba při použití použít.  
  
 [Soubory Oracle BFILE](oracle-bfiles.md)  
 Popisuje <xref:System.Data.OracleClient.OracleBFile> třídu, která se používá pro práci s datovým typem Oracle BFILE.  
  
 [Soubory Oracle LOB](oracle-lobs.md)  
 Popisuje <xref:System.Data.OracleClient.OracleLob> třídu, která se používá pro práci s datovými typy společnosti Oracle LOB.  
  
 [Soubory Oracle REF CURSOR](oracle-ref-cursors.md)  
 Popisuje podporu pro datový typ referenčního kurzoru Oracle REF.  
  
 [Typy Oracle](oracletypes.md)  
 Popisuje struktury, které můžete použít pro práci s datovými typy Oracle, včetně <xref:System.Data.OracleClient.OracleNumber> a <xref:System.Data.OracleClient.OracleString> .  
  
 [Sekvence Oracle](oracle-sequences.md)  
 Popisuje podporu pro načtení hodnot sekvence Oracle vygenerovaných serverem klíčů.  
  
 [Mapování datových typů Oracle](oracle-data-type-mappings.md)  
 Zobrazí seznam datových typů Oracle a jejich mapování na <xref:System.Data.OracleClient.OracleDataReader> .  
  
 [Distribuované transakce Oracle](oracle-distributed-transactions.md)  
 Popisuje, jak <xref:System.Data.OracleClient.OracleConnection> objekt automaticky zařadí do existující distribuované transakce, pokud určuje, že je transakce aktivní.  
  
## <a name="related-sections"></a>Související oddíly  
 [Zabezpečení aplikací ADO.NET](securing-ado-net-applications.md)  
 Popisuje postupy zabezpečeného kódování při použití ADO.NET.  
  
 [Datové sady, datové tabulky a datová zobrazení](./dataset-datatable-dataview/index.md)  
 Popisuje, jak vytvořit a používat `DataSets` , zadat `DataSets` , `DataTables` a `DataViews` .  
  
 [Načítání a úpravy dat v ADO.NET](retrieving-and-modifying-data.md)  
 Popisuje, jak pracovat s daty v ADO.NET.  
  
 [SQL Server a ADO.NET](./sql/index.md)  
 Popisuje, jak pracovat s funkcemi a funkcemi, které jsou specifické pro SQL Server.  
  
 [DbProviderFactories](dbproviderfactories.md)  
 Popisuje obecné třídy, které umožňují napsat kód nezávislý na poskytovateli v ADO.NET.  
  
## <a name="see-also"></a>Viz také

- [ADO.NET](index.md)
- [Přehled ADO.NET](ado-net-overview.md)
