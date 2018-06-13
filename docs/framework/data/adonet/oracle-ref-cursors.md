---
title: Kurzory REF Oracle
ms.date: 03/30/2017
ms.assetid: c6b25b8b-0bdd-41b2-9c7c-661f070c2247
ms.openlocfilehash: 7aae9b2e4b39cf164a93ba82212b5705f583d761
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758721"
---
# <a name="oracle-ref-cursors"></a>Kurzory REF Oracle
Zprostředkovatel dat .NET Framework pro Oracle podporuje Oracle **REF kurzor** datového typu. Při použití zprostředkovatele dat pro práci s kurzory REF Oracle, měli byste zvážit následující chování.  
  
> [!NOTE]
>  Některé chování se liší od zprostředkovatele Microsoft OLE DB pro Oracle (MSDAORA).  
  
-   Z důvodů výkonu poskytovatele dat Oracle nemá vazbu automaticky **REF kurzor** datové typy, jako je tomu MSDAORA, pokud je výslovně určit.  
  
-   Poskytovatel dat nepodporuje žádné řídicí sekvence ODBC, včetně řídicí {třídy resultset} slouží k zadání parametry REF KURZORU.  
  
-   K provedení uložené procedury, jež vrátí REF kurzory, je nutné definovat parametry v <xref:System.Data.OracleClient.OracleParameterCollection> s <xref:System.Data.OracleClient.OracleType> z **kurzor** a <xref:System.Data.OracleClient.OracleParameter.Direction%2A> z **výstup**. Zprostředkovatel dat podporuje jako výstupní parametry pouze vazby REF kurzory. Zprostředkovatel nepodporuje REF kurzory jako vstupní parametry.  
  
-   Získání <xref:System.Data.OracleClient.OracleDataReader> z parametru hodnota není podporována. Hodnoty jsou typu <xref:System.DBNull> po provedení příkazu.  
  
-   Jediným **CommandBehavior** hodnota výčtu, která funguje s kurzory REF (například při volání metody <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) je **CloseConnection**; všechny další se ignorují.  
  
-   Pořadí REF kurzory v **připojení OracleDataReader** v řádu parametrů v závisí **OracleParameterCollection**. <xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> Vlastnost je ignorována.  
  
-   PL/SQL **tabulky** datový typ není podporován. REF kurzory jsou však efektivnější. Pokud je nutné použít **tabulky** datový typ, použijte zprostředkovatele technologie OLE DB .NET dat s MSDAORA.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Příklady REF CURSOR](../../../../docs/framework/data/adonet/ref-cursor-examples.md)  
 Obsahuje tři příklady, které ukazují použití REF kurzory.  
  
 [Parametry REF CURSOR v čtečce OracleDataReader](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)  
 Ukazuje, jak provést PL/SQL uložené procedury, která vrátí parametr REF kurzor a přečte hodnotu jako **připojení OracleDataReader**.  
  
 [Načítání dat z více typů REF CURSOR pomocí čtečky OracleDataReader](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)  
 Ukazuje, jak provést PL/SQL uložené procedury, která vrátí dva parametry REF kurzor a přečte hodnoty pomocí **připojení OracleDataReader**.  
  
 [Naplnění datové sady pomocí jednoho nebo více typů REF CURSOR](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)  
 Ukazuje, jak provést PL/SQL uložené procedury, která vrátí dva parametry REF kurzor a výplní <xref:System.Data.DataSet> s řádky, které jsou vráceny.  
  
## <a name="see-also"></a>Viz také  
 [Oracle a ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
