---
title: Požadavky na systém pro zprostředkovatele dat .NET Framework pro Oracle
ms.date: 03/30/2017
ms.assetid: 054f76b9-1737-43f0-8160-84a00a387217
ms.openlocfilehash: cc3fc61c5adebf67b1203897579b2f959cbc0546
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54670867"
---
# <a name="system-requirements-for-the-net-framework-data-provider-for-oracle"></a>Požadavky na systém pro zprostředkovatele dat .NET Framework pro Oracle
Zprostředkovatel dat .NET Framework pro Oracle vyžaduje Microsoft Data Access Components (MDAC) verze 2.6 nebo novější. Doporučuje se MDAC 2.8 SP1.  
  
 Musíte také mít klienta Oracle 8i verze 3 (8.1.7) nebo novější.  
  
 Klientský software Oracle před verzí Oracle 9i nemá přístup k UTF16 databáze, protože UTF16 je nová funkce v Oracle 9i. Chcete-li tuto funkci používat, je nutné upgradovat software klienta Oracle 9i nebo novější.  
  
## <a name="working-with-the-data-provider-for-oracle-and-unicode-data"></a>Práce s Data Provider pro Oracle a Data v kódování Unicode  
 Tady je seznam problémů souvisejících s kódováním Unicode, byste měli zvážit při práci s zprostředkovatele dat .NET Framework pro Oracle nebo Oracle klientské knihovny. Další informace najdete v dokumentaci Oracle.  
  
### <a name="setting-the-unicode-value-in-a-connection-string-attribute"></a>Nastavením této hodnoty kódování Unicode v atribut připojovacího řetězce  
 Při práci s databázemi Oracle, můžete použít atribut připojovacího řetězce  
  
```  
Unicode=True   
```  
  
 Inicializace knihoven klienta Oracle v režimu UTF-16. To způsobí, že klienta Oracle knihovny tak, aby přijímal UTF-16 (což je velmi podobný UCS-2) namísto vícebajtové řetězce. To umožňuje Data Provider pro Oracle vždy pracovat jakákoli Oracle znaková stránka bez překladu další práce. Tato konfigurace funguje jenom v případě Oracle 9i klienti používají ke komunikaci s databází Oracle 9i s alternativní znakovou sadu AL16UTF16. Pokud klienta Oracle 9i komunikuje se serverem 9i Oracle, další prostředky, je potřeba převést Unicode **CommandText** hodnoty pro příslušnou vícebajtovou znakovou sadu, která Oracle9i server používá. Toho se lze vyvarovat, když víte, že máte bezpečné konfiguraci tak, že přidáte `Unicode=True` připojovací řetězec.  
  
### <a name="mixing-versions-of-oracle-client-and-oracle-server"></a>Kombinace verzí klienta Oracle nebo Oracle Server  
 Oracle 8i klienti nemají přístup k **NCHAR**, **NVARCHAR2**, nebo **NCLOB** data v databázích Oracle 9i, když na server národní znaková sada je zadán jako AL16UTF16 () Výchozí nastavení pro Oracle 9i). Protože Podpora znakové sady UTF-16 se zavedl až do Oracle Oracle nepřečtete klienti 8i, 9i.  
  
### <a name="working-with-utf-8-data"></a>Práce s daty UTF-8  
 Pokud chcete nastavit alternativní znaková sada, nastavte HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\HOMEID\NLS_LANG klíč registru na UTF8. Na vaší platformě pro další informace najdete v poznámkách k instalaci Oracle. Ve výchozím nastavení je primární znakové sady jazyka, ze kterého instalujete software klienta Oracle. Nastavit jazyk tak, aby odpovídaly národních jazyků znakovou sadu databáze, ke kterému se připojujete způsobí, že parametr a ve sloupci vazby na odeslání nebo příjem dat v primární databázi znaková sada, není nastaveno národní znak.  
  
### <a name="oraclelob-can-only-update-full-characters"></a>OracleLob může aktualizovat pouze úplné znaků.  
 Z důvodů použitelnosti <xref:System.Data.OracleClient.OracleLob> objekt dědí z třídy rozhraní .NET Framework Stream a poskytuje **ReadByte** a **Metoda WriteByte** metody. Také implementuje metody, jako například **CopyTo** a **vymazat**, který pracovat na oddíly Oracle **LOB** objekty. Naproti tomu klientský software Oracle poskytuje několik rozhraní API pro práci s znak **LOB**s (**datový typ CLOB** a **NCLOB**). Tato rozhraní API by ale fungovat pouze úplné znaků. Vzhledem k tomuto rozdílu Data Provider pro Oracle implementuje podporu pro **čtení** a **ReadByte** pro práci s daty UTF-16 byte-wise způsobem. Ale jiné metody **OracleLob** objektu povolit pouze znak celé operace.  
  
## <a name="see-also"></a>Viz také:
- [Oracle a ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
