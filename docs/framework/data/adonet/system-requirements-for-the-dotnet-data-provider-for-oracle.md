---
title: Systémové požadavky pro zprostředkovatele dat rozhraní .NET Framework pro oracle
ms.date: 03/30/2017
ms.assetid: 054f76b9-1737-43f0-8160-84a00a387217
ms.openlocfilehash: dab3378d3022c01c674640201a67f3bdbb4f571f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174248"
---
# <a name="system-requirements-for-the-net-framework-data-provider-for-oracle"></a>Systémové požadavky pro zprostředkovatele dat rozhraní .NET Framework pro oracle

Zprostředkovatel dat rozhraní .NET Framework pro společnost Oracle vyžaduje součásti Microsoft Data Access Components (MDAC) verze 2.6 nebo novější. Doporučuje se aktualizace MDAC 2.8 SP1.  
  
 Musíte mít také oracle 8i verze 3 (8.1.7) klienta nebo novější nainstalován.  
  
 Software Oracle Client před verzí Oracle 9i nemá přístup k databázím UTF16, protože UTF16 je v aplikaci Oracle 9i novou funkcí. Chcete-li tuto funkci používat, je nutné upgradovat klientský software na systém Oracle 9i nebo novější.  
  
## <a name="working-with-the-data-provider-for-oracle-and-unicode-data"></a>Spolupráce s poskytovatelem dat pro oracle a unicode data  

Následuje seznam problémů souvisejících s kódováním Unicode, které byste měli zvážit při práci s poskytovatelem dat rozhraní .NET Framework pro klientské knihovny Oracle a Oracle. Další informace naleznete v dokumentaci k řešení Oracle.  
  
### <a name="setting-the-unicode-value-in-a-connection-string-attribute"></a>Nastavení hodnoty Unicode v atributu připojovacího řetězce  

Při práci se společností Oracle můžete použít atribut připojovacího řetězce  
  
`Unicode=True`
  
inicializovat klientské knihovny Oracle v režimu UTF-16. To způsobí, že klientské knihovny Oracle přijmout UTF-16 (což je velmi podobné UCS-2) namísto vícebajtových řetězců. To umožňuje poskytovateli dat pro společnost Oracle vždy pracovat s jakoukoli znakovou stránkou Oracle bez další překladové práce. Tato konfigurace funguje pouze v případě, že používáte klienty Oracle 9i ke komunikaci s databází Oracle 9i s alternativní znakovou sadou AL16UTF16. Když klient Oracle 9i komunikuje se serverem Oracle 9i, jsou k převodu hodnot Unicode **CommandText** na příslušnou vícebajtovou znakovou sadu, kterou server Oracle9i používá, vyžadovány další prostředky. Tomu se lze vyhnout, pokud víte, že `Unicode=True` máte bezpečnou konfiguraci přidáním do připojovacího řetězce.  
  
### <a name="mixing-versions-of-oracle-client-and-oracle-server"></a>Míchání verzí řešení Oracle Client a Oracle Server  

Klienti Oracle 8i nemají přístup k datům **NCHAR**, **NVARCHAR2**nebo **NCLOB** v databázích Oracle 9i, pokud je národní znaková sada serveru zadána jako AL16UTF16 (výchozí nastavení pro oracle 9i). Vzhledem k tomu, že podpora znakové sady UTF-16 nebyla zavedena, dokud oracle 9i, klienti Oracle 8i ji nemohou přečíst.  
  
### <a name="working-with-utf-8-data"></a>Práce s daty UTF-8  

Chcete-li nastavit alternativní znakovou sadu, nastavte klíč registru HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\HOMEID\NLS_LANG na UTF8. Další informace naleznete v poznámkách k instalaci oracle na platformě. Výchozí nastavení je primární znaková sada jazyka, ze kterého instalujete software Oracle Client. Nenastavíjazyk tak, aby odpovídal národní jazykové znakové sady databáze, ke které se připojujete, způsobí, že vazby parametrů a sloupců budou odesílat nebo přijímat data v primární znakové sadě databáze, nikoli v národní znakové sadě.  
  
### <a name="oraclelob-can-only-update-full-characters"></a>OracleLob může aktualizovat pouze úplné znaky.  

Z důvodů použitelnosti <xref:System.Data.OracleClient.OracleLob> objekt dědí z třídy .NET Framework Stream a poskytuje **metody ReadByte** a **WriteByte.** Implementuje také metody, jako je **CopyTo** a **Erase**, které pracují na částech objektů Oracle **LOB.** Naproti tomu klientský software Oracle poskytuje řadu api pro práci s znakem **LOB**s (**CLOB** a **NCLOB).** Tato řešení API však fungují pouze na úplných znacích. Z důvodu tohoto rozdílu zprostředkovatel dat pro Oracle implementuje podporu pro **čtení** a **ReadByte** pro práci s daty UTF-16 v bajt-moudrý způsobem. Ostatní metody **OracleLob** objektu však povolit pouze operace s plným znakem.  
  
## <a name="see-also"></a>Viz také

- [Oracle a ADO.NET](oracle-and-adonet.md)
- [Přehled ADO.NET](ado-net-overview.md)
