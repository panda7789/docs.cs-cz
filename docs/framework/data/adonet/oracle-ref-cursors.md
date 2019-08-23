---
title: Soubory Oracle REF CURSOR
ms.date: 03/30/2017
ms.assetid: c6b25b8b-0bdd-41b2-9c7c-661f070c2247
ms.openlocfilehash: 7c6b326b15a2af58da9206adf28070e57fec600c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963504"
---
# <a name="oracle-ref-cursors"></a>Soubory Oracle REF CURSOR
Zprostředkovatel dat .NET Framework pro Oracle podporuje datový typ **textový kurzor Oracle ref** . Pokud používáte zprostředkovatele dat pro práci s REFERENČNÍmi KURZORy Oracle, měli byste zvážit následující chování.  
  
> [!NOTE]
> Některé chování se liší od Zprostředkovatel Microsoft OLE DB pro Oracle (MADAORA).  
  
- Z důvodů výkonu Zprostředkovatel dat pro Oracle automaticky navazovat datové typy **REF CURSOR** , jako madaora, pokud je explicitně neurčíte.  
  
- Zprostředkovatel dat nepodporuje žádné řídicí sekvence ODBC, včetně řídicího panelu {resultset}, který slouží k zadání parametrů REF CURSOR.  
  
- Chcete-li spustit uloženou proceduru, která vrací referenční kurzory, je nutné definovat <xref:System.Data.OracleClient.OracleParameterCollection> parametry v <xref:System.Data.OracleClient.OracleType> prvku s kurzorem <xref:System.Data.OracleClient.OracleParameter.Direction%2A> a **výstupem**. Zprostředkovatel dat podporuje vazby referenčních odkazů pouze jako výstupní parametry. Zprostředkovatel nepodporuje referenční KURZORy jako vstupní parametry.  
  
- Získání hodnoty <xref:System.Data.OracleClient.OracleDataReader> z parametru není podporováno. Hodnoty jsou typu <xref:System.DBNull> po provedení příkazu.  
  
- Jediná hodnota výčtu **CommandBehavior** , která funguje s referenčními kurzory (například při volání <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>), je **CloseConnection**; všechny ostatní jsou ignorovány.  
  
- Pořadí REFERENČNÍch KURZORů v **OracleDataReader** závisí na pořadí parametrů v **OracleParameterCollection**. <xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> Vlastnost je ignorována.  
  
- Datový typ **tabulka** PL/SQL není podporován. Nicméně referenční KURZORy jsou efektivnější. Pokud je nutné použít datový typ **tabulka** , použijte OLE DB .NET zprostředkovatel dat s madaora.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Příklady REF CURSOR](../../../../docs/framework/data/adonet/ref-cursor-examples.md)  
 Obsahuje tři příklady, které ukazují použití REF CURSOR.  
  
 [Parametry REF CURSOR v čtečce OracleDataReader](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)  
 Ukazuje, jak spustit uloženou proceduru PL/SQL, která vrací parametr REF CURSOR, a přečte hodnotu jako **OracleDataReader**.  
  
 [Načítání dat z více typů REF CURSOR pomocí čtečky OracleDataReader](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)  
 Ukazuje, jak spustit uloženou proceduru PL/SQL, která vrací dva parametry REF CURSOR a přečte hodnoty pomocí **OracleDataReader**.  
  
 [Naplnění datové sady pomocí jednoho nebo více typů REF CURSOR](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)  
 Ukazuje, jak spustit uloženou proceduru PL/SQL, která vrací dva parametry REF CURSOR a vyplní <xref:System.Data.DataSet> řádky, které jsou vráceny.  
  
## <a name="see-also"></a>Viz také:

- [Oracle a ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
