---
title: Požadavky na systém pro Zprostředkovatel dat .NET Framework pro Oracle
ms.date: 03/30/2017
ms.assetid: 054f76b9-1737-43f0-8160-84a00a387217
ms.openlocfilehash: b64a84b8d8246bae9028a6ca710f0a62cc85bf79
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894376"
---
# <a name="system-requirements-for-the-net-framework-data-provider-for-oracle"></a>Požadavky na systém pro Zprostředkovatel dat .NET Framework pro Oracle
Zprostředkovatel dat .NET Framework pro Oracle vyžaduje součásti MDAC (Microsoft Data Access Components) verze 2,6 nebo novější. Je doporučeno rozhraní MDAC 2,8 SP1.  
  
 Je také nutné mít nainstalovaného klienta Oracle 8i Release 3 (8.1.7) nebo novější.  
  
 Klientský software Oracle před verzí Oracle 9i nemá přístup k databázím UTF16, protože UTF16 je nová funkce v Oracle 9i. Chcete-li tuto funkci používat, je nutné upgradovat klientský software na Oracle 9i nebo novější.  
  
## <a name="working-with-the-data-provider-for-oracle-and-unicode-data"></a>Práce s Zprostředkovatel dat pro data Oracle a Unicode  
 Následující seznam uvádí problémy týkající se sady Unicode, které byste měli zvážit při práci s .NET Framework Zprostředkovatel dat pro klientské knihovny Oracle a Oracle. Další informace najdete v dokumentaci k Oracle.  
  
### <a name="setting-the-unicode-value-in-a-connection-string-attribute"></a>Nastavení hodnoty Unicode v atributu připojovacího řetězce  
 Při práci s Oracle můžete použít atribut připojovací řetězec.  
  
`Unicode=True`
  
 pro inicializaci klientských knihoven Oracle v režimu UTF-16. To způsobí, že klientské knihovny Oracle přijmou UTF-16 (což je velmi podobné UCS-2) místo vícebajtových řetězců. To umožňuje Zprostředkovatel dat pro Oracle vždycky pracovat s jakoukoli znakovou stránkou Oracle bez nutnosti dalšího překladu. Tato konfigurace funguje jenom v případě, že používáte klienty Oracle 9i ke komunikaci s databází Oracle 9i s použitím alternativní znakové sady AL16UTF16. Když klient Oracle 9i komunikuje se serverem Oracle 9i, pro převod hodnot **CommandText** v kódování Unicode na příslušnou vícebajtovou znakovou sadu, kterou používá server Oracle9i, se vyžaduje další prostředky. K tomu může dojít, když víte, že máte bezpečnou konfiguraci přidáním `Unicode=True` do připojovacího řetězce.  
  
### <a name="mixing-versions-of-oracle-client-and-oracle-server"></a>Kombinování verzí klientů Oracle a Oracle serveru  
 Klienti Oracle 8i nemají přístup k datům **nchar**, **NVARCHAR2**nebo **NCLOB** v databázích Oracle 9i, pokud je jako národní znaková sada serveru zadána jako AL16UTF16 (výchozí nastavení pro Oracle 9i). Vzhledem k tomu, že podpora znakové sady UTF-16 nebyla zavedena do Oracle 9i, klienti Oracle 8i je nemohou přečíst.  
  
### <a name="working-with-utf-8-data"></a>Práce s daty UTF-8  
 Chcete-li nastavit alternativní znakovou sadu, nastavte klíč registru HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\HOMEID\NLS_LANG na UTF8. Další informace najdete v poznámkách k instalaci Oracle na vaší platformě. Výchozím nastavením je primární znaková sada pro jazyk, ze kterého instalujete klientský software Oracle. Pokud nenastavíte jazyk tak, aby odpovídal národní jazykové znakové sadě databáze, ke které se připojujete, způsobí, že vazby parametrů a sloupců odesílají nebo přijímají data ve znakové sadě primární databáze, nikoli v národní znakové sadě.  
  
### <a name="oraclelob-can-only-update-full-characters"></a>Vlastnost OracleLob může aktualizovat jenom celé znaky.  
 Z důvodu <xref:System.Data.OracleClient.OracleLob> použitelnosti objekt dědí z třídy Stream .NET Framework a poskytuje metody **ReadByte** a **Metoda WriteByte** . Implementuje také metody, jako je například **CopyTo** a **Erase**, které fungují v sekcích objektů **společnosti** Oracle. Naproti tomu klientský software Oracle poskytuje řadu rozhraní API pro práci se znakem **LOB**s (**datový typ CLOB** a **NCLOB**). Tato rozhraní API však fungují pouze na všech znacích. Z důvodu tohoto rozdílu používá Zprostředkovatel dat pro Oracle podporu pro **čtení** a **ReadByte** pro práci s daty UTF-16 v bajtovém formátu. Jiné metody objektu **vlastnost OracleLob** však umožňují pouze operace s úplnými znaky.  
  
## <a name="see-also"></a>Viz také:

- [Oracle a ADO.NET](oracle-and-adonet.md)
- [Přehled ADO.NET](ado-net-overview.md)
