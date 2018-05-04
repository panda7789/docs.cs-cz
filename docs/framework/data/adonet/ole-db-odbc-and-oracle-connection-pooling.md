---
title: OLE DB, rozhraní ODBC a Oracle připojení sdružování
ms.date: 03/30/2017
ms.assetid: 2bd83b1e-3ea9-43c4-bade-d9cdb9bbbb04
ms.openlocfilehash: 2e42b52bb75008fd34f3e4bef1788626d96368bc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ole-db-odbc-and-oracle-connection-pooling"></a>OLE DB, rozhraní ODBC a Oracle připojení sdružování
Sdružování připojení může výrazně zvýšit výkon a škálovatelnost vaší aplikace. Tato část popisuje sdružování pro zprostředkovatele dat .NET Framework pro OLE DB, rozhraní ODBC a Oracle.  
  
## <a name="connection-pooling-for-oledb"></a>Sdružování připojení ke OleDb  
 Zprostředkovatel dat .NET Framework pro OLE DB fondu automaticky pomocí technologie OLE DB relace sdružování připojení. Argumenty řetězce připojení slouží k povolení nebo zakázání služby rozhraní OLE DB včetně sdružování. Například následující připojovací řetězec zakáže sdružování relací OLE DB a automatický zápis do transakce.  
  
```  
Provider=SQLOLEDB;OLE DB Services=-4;Data Source=localhost;Integrated Security=SSPI;  
```  
  
 Doporučujeme vždy zavřete nebo metodu dispose připojení po ukončení práce cílem vrátit připojení do fondu. Připojení, které nejsou výslovně nemusí získat vrátí do fondu. Například připojení, která byla mimo rozsah, ale který ještě nebyl uzavřen explicitně pouze vrátí do fondu připojení Pokud byl dosažen maximální počet a připojení je stále platný.  
  
 Další informace o relaci OLE DB nebo sdílení prostředků ve fondech, a o tom, jak zakázat sdružování přepsáním výchozích hodnot služby zprostředkovatele OLE DB, najdete v článku [OLE DB – Příručka pro vývojáře](http://go.microsoft.com/fwlink/?linkid=45232).  
  
## <a name="connection-pooling-for-odbc"></a>Sdružování připojení ke rozhraní Odbc  
 Sdružování připojení pro zprostředkovatele dat .NET Framework pro ODBC je spravovat pomocí Správce ovladačů ODBC používaný pro připojení a nemá vliv zprostředkovatele dat .NET Framework pro ODBC.  
  
 Chcete-li povolit nebo zakázat sdružování připojení, otevřete **správce zdrojů dat ODBC** ve složce Nástroje pro správu v Ovládacích panelech. **Sdružování připojení** kartě můžete zadat parametry pro každý nainstalovaný ovladač ODBC sdružování připojení. Všimněte si, že změny sdružování připojení pro určitý ovladač ODBC ovlivní všechny aplikace, které používají tento ovladač ODBC.  
  
 Další informace o sdružování připojení ODBC najdete v tématu [informace: často výzva otázky o sdružování připojení ODBC](http://support.microsoft.com/kb/169470).  
  
## <a name="connection-pooling-for-oracleclient"></a>Pro OracleClient sdružování připojení  
 Zprostředkovatel dat .NET Framework pro Oracle poskytuje sdružování připojení automaticky pro klientské aplikace ADO.NET. Můžete také zadat několik modifikátory řetězec připojení k řízení chování sdružování připojení (viz dále v tomto tématu "Řízení připojení sdružování s připojovací řetězec klíčová slova,").  
  
### <a name="pool-creation-and-assignment"></a>Vytvoření fondu a přiřazení  
 Po otevření připojení se vytvoří fond připojení podle přesný odpovídající algoritmu, který přidruží fondu připojovací řetězec v připojení. Každý fond připojení je přidružen odlišné připojovací řetězec. Když je otevřít nové připojení, pokud připojovací řetězec není přesnou shodu na existující fond, vytvoří se nový fond.  
  
 Po vytvoření připojení fondy nejsou zničený, dokud aktivní proces skončí. Zachování neaktivní nebo prázdný fondů používá jen několik systémové prostředky.  
  
### <a name="connection-addition"></a>Přidání připojení  
 Fond připojení se vytvoří pro každý jedinečný připojovací řetězec. Při vytváření fondu více objektů připojení jsou vytvořen a přidán do fondu, aby je nesplňuje požadavek na minimální fondu velikost. Připojení se přidají do fondu, podle potřeby až k maximální velikosti fondu.  
  
 Když <xref:System.Data.OracleClient.OracleConnection> je požadován objekt, se získávají z fondu, pokud je k dispozici použitelné připojení. Být použitelná, připojení nesmí aktuálně nevyužitá, mají odpovídající kontext transakce nebo být přidružen k žádnému kontextu transakce a mít platný odkaz na serveru.  
  
 Pokud byl dosažen maximální počet a není k dispozici žádné použitelné připojení, požadavek ve frontě. Pro sdružování připojení splňuje tyto požadavky pomocí změna přidělování připojení při jejich vydání zpět do fondu. Připojení jsou vydávány zpět do fondu, když jsou uzavřeny nebo zlikvidován.  
  
### <a name="connection-removal"></a>Odebrání připojení  
 Po jejím nečinnosti delší dobu, nebo pokud pro sdružování zjistí, že má bylo porušeno připojení se serverem pro sdružování připojení Odebere připojení z fondu. Všimněte si, že to bude možné zjišťovat až po pokusu o komunikaci se serverem. Pokud se najde připojení, který je už připojený k serveru, je označena jako neplatná. Pro sdružování připojení pravidelně kontroluje připojení fondy vyhledávání pro objekty, které byly vydány do fondu a jsou označené jako neplatné. Pak se trvale odebrat tato připojení.  
  
 Pokud existuje připojení k serveru, který má smazán, můžete toto připojení čerpají z fondu, pokud nebyl zjištěn poškozený připojení a označena jako neplatná pro sdružování připojení. V takovém případě se vygeneruje výjimku. Připojení však musíte zavřít Chcete-li ji uvolnit zpět do fondu.  
  
 Nevolejte `Close` nebo `Dispose` na `Connection`, `DataReader`, nebo jiné spravovaného objektu v `Finalize` metoda vaší třídy. V finalizační metodu vydání pouze nespravovaných prostředků, které vlastní třídu přímo. Pokud vaše třída nevlastní žádné nespravovaných prostředků, nezahrnujte `Finalize` metoda v definici vaší třídy. Další informace najdete v tématu [uvolňování paměti](../../../../docs/standard/garbage-collection/index.md).  
  
### <a name="transaction-support"></a>Podpora transakcí  
 Připojení jsou vykreslovány z fondu a kontext přiřazené na základě transakce. Kontext požadavku vlákno a přiřazené připojení musí shodovat. Proto každý fond připojení je ve skutečnosti rozděleno na připojení s žádný kontext transakce související s nimi a do *N* dílčích dělení, že každý obsahovat připojení s kontextem konkrétní transakce.  
  
 Když je připojení ukončeno, jeho vydání zpět do fondu a do příslušné pododdíl na základě jeho kontextu transakce. Proto můžete zavřít připojení bez generování chybu, i když je stále distribuovanou transakci čekající na vyřízení. To umožňuje potvrzení nebo přerušení distribuovanou transakci později.  
  
### <a name="controlling-connection-pooling-with-connection-string-keywords"></a>Řízení sdružování připojení s klíčovými slovy řetězec připojení  
 <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> Vlastnost <xref:System.Data.OracleClient.OracleConnection> objekt podporuje dvojice klíč/hodnota řetězce připojení, které lze použít k úpravě chování logiky sdružování připojení.  
  
 V následující tabulce jsou popsány <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> hodnoty můžete upravit chování sdružování připojení.  
  
|Název|Výchozí|Popis|  
|----------|-------------|-----------------|  
|`Connection Lifetime`|0|Pokud připojení se vrátí do fondu, doba jejího vytvoření je porovnána s aktuální čas a zničen připojení, pokud tento časový interval (v sekundách) překročí hodnotu zadanou pomocí `Connection Lifetime`. To je užitečné v clusterovaných konfiguracích vynutit vyrovnávání zátěže mezi spuštěný server a server právě uvést do režimu online.<br /><br /> Hodnota nula (0) způsobí, že ve fondu připojení tak, aby měl maximální časový limit.|  
|`Enlist`|hodnotu true.|Když `true`, pro sdružování automaticky využívá připojení v aktuálním kontextu transakce vytvoření vlákna, pokud existuje kontextu transakce.|  
|`Max Pool Size`|100|Maximální počet připojení povolených ve fondu.|  
|`Min Pool Size`|0|Minimální počet připojení udržují ve fondu.|  
|`Pooling`|hodnotu true.|Když `true`, je připojení čerpají z odpovídajícímu fondu adres, nebo v případě potřeby vytvořen a přidán do fondu vhodné.|  
  
## <a name="see-also"></a>Viz také  
 [Sdružování připojení](../../../../docs/framework/data/adonet/connection-pooling.md)  
 [Čítače výkonu](../../../../docs/framework/data/adonet/performance-counters.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
