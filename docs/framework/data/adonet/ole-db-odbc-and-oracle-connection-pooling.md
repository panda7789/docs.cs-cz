---
title: Sdružování připojení OLE DB, ODBC a Oracle
ms.date: 03/30/2017
ms.assetid: 2bd83b1e-3ea9-43c4-bade-d9cdb9bbbb04
ms.openlocfilehash: 7552f4a95af51774071f0a4017637570d648dd86
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929258"
---
# <a name="ole-db-odbc-and-oracle-connection-pooling"></a>Sdružování připojení OLE DB, ODBC a Oracle
Připojení sdružování můžou významně zlepšit výkon a škálovatelnost vaší aplikace. Tato část popisuje sdružování připojení pro poskytovatele .NET Framework dat pro OLE DB, ODBC a Oracle.  
  
## <a name="connection-pooling-for-oledb"></a>Sdružování připojení pro OleDb  
 Zprostředkovatel dat .NET Framework pro OLE DB automaticky poolují připojení pomocí sdružování relací OLE DB. Argumenty připojovacího řetězce se dají použít k povolení nebo zakázání OLE DBch služeb, včetně sdružování. Například následující připojovací řetězec zakáže OLE DB sdružování relací a automatické zařazení transakce.  
  
```  
Provider=SQLOLEDB;OLE DB Services=-4;Data Source=localhost;Integrated Security=SSPI;  
```  
  
 Doporučujeme, abyste připojení vždy zavřeli nebo odstranili, až ho dokončíte, aby se mohlo vrátit připojení ke fondu. Připojení, která nejsou explicitně uzavřena, se nemusí vrátit do fondu. Například připojení, které se odchází z oboru, ale které nebylo explicitně uzavřeno, bude vráceno do fondu připojení pouze v případě, že byla dosažena maximální velikost fondu a připojení je stále platné.  
  
 Další informace o OLE DB relace nebo sdružování prostředků a o tom, jak zakázat sdružování přepsáním výchozích nastavení služby OLE DB poskytovatele, najdete v [příručce pro programátory OLE DB](https://go.microsoft.com/fwlink/?linkid=45232).  
  
## <a name="connection-pooling-for-odbc"></a>Sdružování připojení pro rozhraní ODBC  
 Sdružování připojení pro .NET Framework Zprostředkovatel dat pro rozhraní ODBC spravuje správce ovladačů ODBC, který se používá pro připojení a není ovlivněn .NET Framework Zprostředkovatel dat pro rozhraní ODBC.  
  
 Chcete-li povolit nebo zakázat sdružování připojení, otevřete **Správce zdrojů dat ODBC** ve složce Nástroje pro správu v Ovládacích panelech. Karta **sdružování připojení** umožňuje zadat parametry sdružování připojení pro každý nainstalovaný ovladač ODBC. Všimněte si, že změny sdružování připojení pro určitý ovladač ODBC mají vliv na všechny aplikace, které používají daný ovladač ODBC.  
  
## <a name="connection-pooling-for-oracleclient"></a>Sdružování připojení pro OracleClient  
 Zprostředkovatel dat .NET Framework pro Oracle poskytuje pro klientskou aplikaci ADO.NET automatické sdružování připojení. Můžete také dodat několik modifikátorů připojovacího řetězce pro řízení chování sdružování připojení (viz "řízení sdružování připojení pomocí klíčových slov připojovacího řetězce" dále v tomto tématu).  
  
### <a name="pool-creation-and-assignment"></a>Vytvoření a přiřazení fondu  
 Po otevření připojení se vytvoří fond připojení založený na přesně odpovídajícím algoritmu, který přidruží fond k připojovacímu řetězci v připojení. Každý fond připojení je přidružený k jedinečnému připojovacímu řetězci. Pokud se při otevření nového připojení nejedná o přesný řetězec odpovídající existujícímu fondu, vytvoří se nový fond.  
  
 Po vytvoření fondy připojení nebudou zničeny, dokud se neukončí aktivní proces. Údržba neaktivních nebo prázdných fondů používá hodně systémových prostředků.  
  
### <a name="connection-addition"></a>Přidání připojení  
 U každého jedinečného připojovacího řetězce se vytvoří fond připojení. Při vytvoření fondu se vytvoří víc objektů připojení a přidají se do fondu, aby se splnil minimální požadavek na velikost fondu. Připojení se do fondu přidají podle potřeby až do maximální velikosti fondu.  
  
 Když je <xref:System.Data.OracleClient.OracleConnection> objekt požadován, získá se z fondu, pokud je k dispozici použitelné připojení. Aby bylo možné připojení použít, musí být aktuálně nepoužitelné, mít odpovídající kontext transakce nebo nemusí být přidruženo k žádnému kontextu transakce a musí obsahovat platný odkaz na server.  
  
 Pokud byla dosažena maximální velikost fondu a není k dispozici žádné použitelné připojení, je požadavek zařazen do fronty. Pooler připojení splňuje tyto požadavky tím, že je znovu přidělí, protože se uvolní do fondu. Připojení se uvolní zpátky do fondu, když se zavřou nebo odstraněly.  
  
### <a name="connection-removal"></a>Odebrání připojení  
 Připojení Pooler Odebere připojení z fondu poté, co bylo delší dobu nečinné, nebo pokud Pooler zjistí, že spojení se serverem bylo přerušeno. Počítejte s tím, že se dá zjistit až po pokusu o komunikaci se serverem. Pokud se zjistí připojení, které už není připojené k serveru, je označený jako neplatný. Připojení Pooler pravidelně prohledává fondy připojení, které hledají objekty, které byly vydány do fondu, a jsou označeny jako neplatné. Tato připojení se pak trvale odeberou.  
  
 Pokud připojení existuje na serveru, který zmizel, může být toto připojení vykresleno z fondu, pokud Pooler připojení nerozpoznalo vážné připojení a označil ho jako neplatný. Pokud k tomu dojde, je vygenerována výjimka. Je však nutné připojení ukončit, aby bylo možné ho uvolnit zpátky do fondu.  
  
 `Close` Nevolejte nebo `Dispose` na `Connection`, `Finalize` nebo na jiný spravovaný objekt v metodě vaší třídy. `DataReader` V finalizační metodě pouze uvolní nespravované prostředky, které vaše třída vlastní. Pokud vaše třída nevlastní žádné nespravované prostředky, `Finalize` nezahrnujte metodu do definice třídy. Další informace najdete v tématu [uvolňování paměti](../../../standard/garbage-collection/index.md).  
  
### <a name="transaction-support"></a>Podpora transakcí  
 Připojení jsou vykreslena z fondu a přiřazena na základě kontextu transakce. Kontext žádajícího vlákna a přiřazeného připojení se musí shodovat. Proto každý fond připojení je ve skutečnosti rozdělen na připojení bez kontextu transakce, který je k nim přidružen, a do *N* dílčích dělení, které obsahují připojení s konkrétním kontextem transakce.  
  
 Když je připojení ukončeno, je uvolněno zpátky do fondu a do příslušného dílčího dělení na základě jeho transakčního kontextu. Proto můžete připojení zavřít bez vygenerování chyby, i když distribuovaná transakce stále čeká na vyřízení. Díky tomu můžete distribuovanou transakci potvrdit nebo přerušit v pozdějším čase.  
  
### <a name="controlling-connection-pooling-with-connection-string-keywords"></a>Řízení sdružování připojení pomocí klíčových slov připojovacího řetězce  
 <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> Vlastnost<xref:System.Data.OracleClient.OracleConnection> objektu podporuje páry klíč/hodnota připojovacího řetězce, které lze použít k úpravě chování logiky sdružování připojení.  
  
 Následující tabulka popisuje <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> hodnoty, které můžete použít k úpravě chování sdružování připojení.  
  
|Name|Výchozí|Popis|  
|----------|-------------|-----------------|  
|`Connection Lifetime`|0|Při vrácení připojení do fondu se jeho čas vytvoření porovná s aktuálním časem a připojení je zničeno, pokud časový rozsah (v sekundách) překračuje hodnotu zadanou parametrem `Connection Lifetime`. To je užitečné v clusterovaných konfiguracích, aby vynutilo vyrovnávání zatížení mezi běžícím serverem a serverem, který je právě online.<br /><br /> Hodnota nula (0) způsobí maximální časový limit připojení ve fondu.|  
|`Enlist`|podmínka|Když `true`, Pooler automaticky zařadí připojení v kontextu aktuálního transakce vlákna vytváření, pokud existuje kontext transakce.|  
|`Max Pool Size`|100|Maximální počet připojení povolených ve fondu.|  
|`Min Pool Size`|0|Minimální počet připojení udržovaných ve fondu.|  
|`Pooling`|podmínka|Když `true`se připojení vykreslí z příslušného fondu nebo v případě potřeby se vytvoří a přidá do příslušného fondu.|  
  
## <a name="see-also"></a>Viz také:

- [Sdružování připojení](../../../../docs/framework/data/adonet/connection-pooling.md)
- [Čítače výkonu](../../../../docs/framework/data/adonet/performance-counters.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
