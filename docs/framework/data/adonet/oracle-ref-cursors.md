---
title: Soubory Oracle REF CURSOR
ms.date: 03/30/2017
ms.assetid: c6b25b8b-0bdd-41b2-9c7c-661f070c2247
ms.openlocfilehash: 5443c409bd3c73e91969db6424a4f86f1a16ed72
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516311"
---
# <a name="oracle-ref-cursors"></a>Soubory Oracle REF CURSOR
Zprostředkovatel dat .NET Framework pro Oracle podporuje Oracle **REF CURSOR** datového typu. Při použití zprostředkovatele dat pro práci se soubory Oracle REF CURSOR, měli byste zvážit následující chování.  
  
> [!NOTE]
>  Některá chování se liší od těch, které zprostředkovatel Microsoft OLE DB pro Oracle (MSDAORA).  
  
-   Z důvodů výkonu Data Provider pro Oracle nemá vazbu automaticky **REF CURSOR** datové typy, stejně jako MSDAORA, pokud je explicitně neurčíte.  
  
-   Poskytovatel dat nepodporuje žádné ODBC řídicí sekvence, včetně řídicí {třídy resultset} používá k určení parametry REF CURSOR.  
  
-   K provedení uložené procedury, která vrací typů REF CURSOR, je nutné definovat parametry <xref:System.Data.OracleClient.OracleParameterCollection> s <xref:System.Data.OracleClient.OracleType> z **kurzor** a <xref:System.Data.OracleClient.OracleParameter.Direction%2A> z **výstup**. Zprostředkovatel dat podporuje jako výstupní parametry pouze vazby typů REF CURSOR. Zprostředkovatel nepodporuje typů REF CURSOR jako vstupní parametry.  
  
-   Získání <xref:System.Data.OracleClient.OracleDataReader> z parametru hodnota není podporována. Hodnoty jsou typu <xref:System.DBNull> po spuštění příkazu.  
  
-   Jediná **CommandBehavior** hodnota výčtu, která funguje s typů REF CURSOR (například při volání metody <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) je **CloseConnection**; případné další se ignorují.  
  
-   Pořadí typů REF CURSOR v **připojení OracleDataReader** pořadí parametrů v závisí **OracleParameterCollection**. <xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> Vlastnost se ignoruje.  
  
-   PL/SQL **tabulky** datový typ není podporován. Typů REF CURSOR jsou však efektivnější. Pokud je nutné použít **tabulky** datový typ, použijte zprostředkovatele OLE DB .NET Data Provider s MSDAORA.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Příklady REF CURSOR](../../../../docs/framework/data/adonet/ref-cursor-examples.md)  
 Obsahuje tři příklady, které ukazují používání typů REF CURSOR.  
  
 [Parametry REF CURSOR v čtečce OracleDataReader](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)  
 Ukazuje, jak provést PL/uložené procedury SQL, který vrací parametr REF CURSOR a přečte hodnotu jako **připojení OracleDataReader**.  
  
 [Načítání dat z více typů REF CURSOR pomocí čtečky OracleDataReader](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)  
 Ukazuje, jak provést PL/SQL uložené procedury, která vrací dva parametry REF CURSOR a čte hodnoty pomocí **připojení OracleDataReader**.  
  
 [Naplnění datové sady pomocí jednoho nebo více typů REF CURSOR](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)  
 Ukazuje, jak provést PL/SQL uložené procedury, která vrací dva parametry REF CURSOR a doplní <xref:System.Data.DataSet> s řádky, které jsou vráceny.  
  
## <a name="see-also"></a>Viz také  
 [Oracle a ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
