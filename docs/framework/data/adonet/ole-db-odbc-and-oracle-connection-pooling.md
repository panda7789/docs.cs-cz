---
title: Sdružování připojení OLE DB, ODBC a Oracle
ms.date: 03/30/2017
ms.assetid: 2bd83b1e-3ea9-43c4-bade-d9cdb9bbbb04
ms.openlocfilehash: 7c17863facd962583e0da03e810c9a8150cda0a6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208888"
---
# <a name="ole-db-odbc-and-oracle-connection-pooling"></a>Sdružování připojení OLE DB, ODBC a Oracle
Sdružování připojení může výrazně zlepšit výkon a škálovatelnost aplikace. Tato část popisuje sdružování pro zprostředkovatele dat .NET Framework pro OLE DB, ODBC a Oracle.  
  
## <a name="connection-pooling-for-oledb"></a>Pro OleDb sdružování připojení  
 Zprostředkovatel dat .NET Framework pro OLE DB fondu automaticky pomocí technologie OLE DB relace sdružování připojení. Argumenty řetězce připojení slouží k povolení nebo zakázání služeb OLE DB, včetně sdružování. Například následující připojovací řetězec zakáže sdružování relace technologie OLE DB a automatický zápis do transakce.  
  
```  
Provider=SQLOLEDB;OLE DB Services=-4;Data Source=localhost;Integrated Security=SSPI;  
```  
  
 Doporučujeme vám vždy zavřít nebo vyřadit připojení po dokončení jeho použití k vrácení připojení do fondu. Připojení, které nebyly uzavřeny explicitně nemůže získat vrácen do fondu. Například připojení, který má nepřejdou mimo rozsah, ale který ještě nebyl uzavřen explicitně pouze vrátí se do fondu připojení Pokud bylo dosaženo maximální velikosti fondu připojení je stále platný.  
  
 Další informace o relaci OLE DB nebo sdílení prostředků ve fondech, jakož i jak zakázat sdružování tak, že přepíšete výchozích hodnot služby zprostředkovatele OLE DB, najdete v článku [Příručka programátora technologie OLE DB](https://go.microsoft.com/fwlink/?linkid=45232).  
  
## <a name="connection-pooling-for-odbc"></a>Sdružování pro Odbc  
 Sdružování připojení zprostředkovatele dat .NET Framework pro ODBC se spravuje pomocí Správce ovladačů ODBC, který se používá pro připojení a nemá vliv zprostředkovatele dat .NET Framework pro ODBC.  
  
 Chcete-li povolit nebo zakázat sdružování připojení, otevřete **správce zdrojů dat ODBC** ve složce Nástroje pro správu ovládacích panelů. **Sdružování připojení** kartě můžete zadat parametry pro každý nainstalovaný ovladač ODBC sdružování připojení. Všimněte si, že změny sdružování připojení pro určitý ovladač ODBC ovlivňují všechny aplikace, které používají tento ovladač ODBC.  
  
## <a name="connection-pooling-for-oracleclient"></a>Sdružování připojení ke OracleClient  
 Zprostředkovatel dat .NET Framework pro Oracle poskytuje klientské aplikace ADO.NET sdružování připojení automaticky. Můžete také zadat několik modifikátory připojovací řetězec pro řízení chování sdružování připojení (viz "Řízení připojení sdružování s připojovací řetězec klíčová slova," dále v tomto tématu).  
  
### <a name="pool-creation-and-assignment"></a>Vytvoření fondu a přiřazení  
 Po otevření připojení se vytvoří fond připojení podle přesně odpovídající algoritmus, který přidruží připojovací řetězec v připojení k fondu. Každý fond připojení souvisí s distinct připojovací řetězec. Při otevření nové připojení připojovací řetězec není přesná shoda do existujícího fondu, je vytvořen nový fond.  
  
 Po vytvoření sdružení připojení nejsou zničeny, dokud se ukončí aktivní proces. Správa fondů neaktivní nebo je prázdný používá jen několik systémových prostředků.  
  
### <a name="connection-addition"></a>Přidání připojení  
 Fond připojení se vytvoří pro každý jedinečných připojovací řetězec. Při vytvoření fondu jsou více objektů připojení vytvořen a přidán do fondu tak, aby velikost požadavek na minimální fond není splněna. Připojení se přidají do fondu podle potřeby až do maximální velikosti fondu.  
  
 Když <xref:System.Data.OracleClient.OracleConnection> je požadován objekt, se získávají z fondu, pokud je k dispozici použitelné připojení. Má být použitelná, připojení nesmí aktuálně nevyužitá, nemají odpovídající kontext transakce nebo být přidružen k žádnému kontextu transakce a máte platné připojení k serveru.  
  
 Pokud bylo dosaženo maximální velikosti fondu a není k dispozici žádné použitelné připojení, je požadavek ve frontě. Pro sdružování připojení splňuje tyto požadavky podle přerozdělení připojení při jejich vydání zpět do fondu. Připojení se vydávají zpět do fondu, pokud jsou ukončen nebo odstraněn.  
  
### <a name="connection-removal"></a>Odstranění připojení  
 Pro sdružování připojení Odebere připojení z fondu po nečinnosti delší dobu, nebo pokud pro sdružování zjistí, že připojení k serveru bylo porušeno. Všimněte si, že to lze zjistit pouze po pokusu o komunikaci se serverem. Pokud připojení není nalezen, který není připojený k serveru, je označena jako neplatná. Pro sdružování připojení pravidelně kontroluje sdružení připojení hledáte objekty, které byly vydány do fondu a jsou označena jako neplatná. Potom se trvale odeberou tato připojení.  
  
 Existuje-li připojení k serveru, který chybí, můžete toto připojení vykreslit z fondu, pokud nebyl rozpoznán přerušená připojení a označena jako neplatná pro sdružování připojení. Pokud k tomu dojde, je vygenerována výjimka. Aby bylo možné uvolnit zpět do fondu však musí stále ukončete připojení.  
  
 Nevolejte `Close` nebo `Dispose` na `Connection`, `DataReader`, nebo jakýkoli jiný spravovaný objekt v `Finalize` metoda vaší třídy. V finalizační metodu jenom uvolnění nespravovaných prostředků, které vaše třída vlastní přímo. Pokud vaše třída není vlastníkem jakýchkoliv nespravovaných prostředků, nezahrnujte `Finalize` metoda v definici třídy. Další informace najdete v tématu [uvolňování](../../../../docs/standard/garbage-collection/index.md).  
  
### <a name="transaction-support"></a>Podpora transakcí  
 Připojení jsou vykreslovány vedle z fondu a kontext přiřazené na základě transakce. Kontextu žádajícího vlákna a přiřazené připojení se musí shodovat. Proto se každý fond připojení je ve skutečnosti rozdělená na připojení s kontextem žádné transakce související s nimi a do *N* pododdíly, že každý obsahuje spojení s konkrétní transakce kontextu.  
  
 Když je připojení ukončeno, uvolní se zpět do fondu a do příslušné dělení na základě jeho kontextu transakce. Proto můžete zavřít připojení bez dojde k chybě, i když distribuované transakce je stále čekající na vyřízení. To umožňuje potvrzení nebo přerušení distribuovaných transakcí kdykoli později.  
  
### <a name="controlling-connection-pooling-with-connection-string-keywords"></a>Řízení sdružování připojení s klíčovými slovy připojovací řetězec  
 <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> Vlastnost <xref:System.Data.OracleClient.OracleConnection> objekt podporuje dvojice klíč/hodnota řetězce připojení, které lze použít k úpravě chování logiky sdružování připojení.  
  
 V následující tabulce jsou popsány <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> hodnoty můžete použít k úpravě chování sdružování připojení.  
  
|Name|Výchozí|Popis|  
|----------|-------------|-----------------|  
|`Connection Lifetime`|0|Při připojení je vrácen do fondu, jeho čas vytvoření porovnán s aktuálním časem a připojení je zničen, pokud tohoto časového intervalu (v sekundách) překročí hodnotu zadanou pomocí `Connection Lifetime`. To je užitečné v clusterovaných konfiguracích vynutit rozložení zátěže mezi spuštěný server a server jenom do režimu online.<br /><br /> Hodnota nula (0) způsobí, že připojení ve fondu má maximální časový limit.|  
|`Enlist`|"true"|Když `true`, pro sdružování připojení v aktuálním kontextu transakce vytvoření vlákna automaticky personálního pokud existuje kontextu transakce.|  
|`Max Pool Size`|100|Maximální počet připojení povolených ve fondu.|  
|`Min Pool Size`|0|Minimální počet připojení udržována ve fondu.|  
|`Pooling`|"true"|Když `true`, připojení je vykreslen z příslušného fondu nebo v případě potřeby vytvořen a přidán do příslušného fondu.|  
  
## <a name="see-also"></a>Viz také:

- [Sdružování připojení](../../../../docs/framework/data/adonet/connection-pooling.md)
- [Čítače výkonu](../../../../docs/framework/data/adonet/performance-counters.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
