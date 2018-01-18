---
title: "Kolekcemi schémat OLE DB"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 33e794559abd7f619f7431683f06e59705b57d41
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="ole-db-schema-collections"></a>Kolekcemi schémat OLE DB
Tato část popisuje podporu kolekci schématu pro zprostředkovatele OLE DB pro Microsoft SQL Server, Oracle a Microsoft Jet.  
  
## <a name="microsoft-sql-server-ole-db-provider"></a>Zprostředkovatel Microsoft SQL Server OLE DB  
 Microsoft SQL Server OLE DB ovladač podporuje následující kolekce konkrétní schématu kromě běžných kolekcemi schémat:  
  
-   Tabulky  
  
-   Sloupce  
  
-   Procedury  
  
-   ProcedureParameters  
  
-   Catalog  
  
-   Indexy  
  
### <a name="tables"></a>Tabulky  
  
|columnName|Datový typ|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|TABLE_TYPE|String|  
|TABLE_GUID|Identifikátor GUID|  
|POPIS|String|  
|TABLE_PROPID|Int64|  
|DATE_CREATED|DateTime|  
|DATE_MODIFIED|DateTime|  
  
### <a name="columns"></a>Sloupce  
  
|columnName|Datový typ|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|COLUMN_NAME|String|  
|COLUMN_GUID|Identifikátor GUID|  
|COLUMN_PROPID|Int64|  
|ORDINAL_POSITION|Int64|  
|COLUMN_HASDEFAULT|Boolean|  
|COLUMN_DEFAULT|String|  
|COLUMN_FLAGS|Int64|  
|IS_NULLABLE|Boolean|  
|DATA_TYPE|Int32|  
|TYPE_GUID|Identifikátor GUID|  
|CHARACTER_MAXIMUM_LENGTH|Int64|  
|CHARACTER_OCTET_LENGTH|Int64|  
|NUMERIC_PRECISION|Int32|  
|NUMERIC_SCALE|Int16|  
|DATETIME_PRECISION|Int64|  
|CHARACTER_SET_CATALOG|String|  
|CHARACTER_SET_SCHEMA|String|  
|CHARACTER_SET_NAME|String|  
|COLLATION_CATALOG|String|  
|COLLATION_SCHEMA|String|  
|COLLATION_NAME|String|  
|DOMAIN_CATALOG|String|  
|DOMAIN_SCHEMA|String|  
|DOMAIN_NAME|String|  
|POPIS|String|  
|COLUMN_LCID|Int32|  
|COLUMN_COMPFLAGS|Int32|  
|COLUMN_SORTID|Int32|  
|COLUMN_TDSCOLLATION|Byte[]|  
|IS_COMPUTED|Boolean|  
  
### <a name="procedures"></a>Procedury  
  
|columnName|Datový typ|  
|----------------|--------------|  
|PROCEDURE_CATALOG|String|  
|PROCEDURE_SCHEMA|String|  
|PROCEDURE_NAME|String|  
|PROCEDURE_TYPE|Int16|  
|PROCEDURE_DEFINITION|String|  
|POPIS|String|  
|DATE_CREATED|DateTime|  
|DATE_MODIFIED|DateTime|  
  
### <a name="procedureparameters"></a>ProcedureParameters  
  
|columnName|Datový typ|  
|----------------|--------------|  
|PROCEDURE_CATALOG|String|  
|PROCEDURE_SCHEMA|String|  
|PROCEDURE_NAME|String|  
|PARAMETER_NAME|String|  
|ORDINAL_POSITION|Int32|  
|PARAMETER_TYPE|Int32|  
|PARAMETER_HASDEFAULT|Boolean|  
|PARAMETER_DEFAULT|String|  
|IS_NULLABLE|Boolean|  
|DATA_TYPE|Int32|  
|CHARACTER_MAXIMUM_LENGTH|Int64|  
|CHARACTER_OCTET_LENGTH|Int64|  
|NUMERIC_PRECISION|Int32|  
|NUMERIC_SCALE|Int16|  
|POPIS|String|  
|TYPE_NAME|String|  
|LOCAL_TYPE_NAME|String|  
  
### <a name="catalog"></a>Catalog  
  
|columnName|Datový typ|  
|----------------|--------------|  
|CATALOG_NAME|String|  
|POPIS|String|  
  
### <a name="indexes"></a>Indexy  
  
|columnName|Datový typ|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|INDEX_CATALOG|String|  
|INDEX_SCHEMA|String|  
|INDEX_NAME|String|  
|PRIMARY_KEY|Boolean|  
|JEDINEČNÉ|Boolean|  
|CLUSTERED|Boolean|  
|TYP|Int32|  
|FILL_FACTOR|Int32|  
|INITIAL_SIZE|Int32|  
|NULLS|Int32|  
|SORT_BOOKMARKS|Boolean|  
|AUTO_UPDATE|Boolean|  
|NULL_COLLATION|Int32|  
|ORDINAL_POSITION|Int64|  
|COLUMN_NAME|String|  
|COLUMN_GUID|Identifikátor GUID|  
|COLUMN_PROPID|Int64|  
|KOLACE|Int16|  
|MOHUTNOST|Desetinné číslo|  
|STRÁNKY|Int32|  
|FILTER_CONDITION|String|  
|INTEGROVANÉ|Boolean|  
  
## <a name="microsoft-oracle-ole-db-provider"></a>Zprostředkovatel OLE DB Microsoft Oracle  
 Oracle OLE DB ovladače Microsoft podporuje následující kolekce konkrétní schématu kromě běžných kolekcemi schémat:  
  
-   Tabulky  
  
-   Sloupce  
  
-   Procedury  
  
-   ProcedureColumns  
  
-   ProcedureParameters  
  
-   zobrazení  
  
-   Indexy  
  
### <a name="tables"></a>Tabulky  
  
|columnName|Datový typ|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|TABLE_TYPE|String|  
|TABLE_GUID|Identifikátor GUID|  
|POPIS|String|  
|TABLE_PROPID|Int64|  
|DATE_CREATED|DateTime|  
|DATE_MODIFIED|DateTime|  
  
### <a name="columns"></a>Sloupce  
  
|columnName|Datový typ|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|COLUMN_NAME|String|  
|COLUMN_GUID|Identifikátor GUID|  
|COLUMN_PROPID|Int64|  
|ORDINAL_POSITION|Int64|  
|COLUMN_HASDEFAULT|Boolean|  
|COLUMN_DEFAULT|String|  
|COLUMN_FLAGS|Int64|  
|IS_NULLABLE|Boolean|  
|DATA_TYPE|Int32|  
|TYPE_GUID|Identifikátor GUID|  
|CHARACTER_MAXIMUM_LENGTH|Int64|  
|CHARACTER_OCTET_LENGTH|Int64|  
|NUMERIC_PRECISION|Int32|  
|NUMERIC_SCALE|Int16|  
|DATETIME_PRECISION|Int64|  
|CHARACTER_SET_CATALOG|String|  
|CHARACTER_SET_SCHEMA|String|  
|CHARACTER_SET_NAME|String|  
|COLLATION_CATALOG|String|  
|COLLATION_SCHEMA|String|  
|COLLATION_NAME|String|  
|DOMAIN_CATALOG|String|  
|DOMAIN_SCHEMA|String|  
|DOMAIN_NAME|String|  
|POPIS|String|  
  
### <a name="procedures"></a>Procedury  
  
|columnName|Datový typ|  
|----------------|--------------|  
|PROCEDURE_CATALOG|String|  
|PROCEDURE_SCHEMA|String|  
|PROCEDURE_NAME|String|  
|PROCEDURE_TYPE|Int16|  
|PROCEDURE_DEFINITION|String|  
|POPIS|String|  
|DATE_CREATED|DateTime|  
|DATE_MODIFIED|DateTime|  
  
### <a name="procedurecolumns"></a>ProcedureColumns  
  
|columnName|Datový typ|  
|----------------|--------------|  
|PROCEDURE_CATALOG|String|  
|PROCEDURE_SCHEMA|String|  
|PROCEDURE_NAME|String|  
|COLUMN_NAME|String|  
|COLUMN_GUID|Identifikátor GUID|  
|COLUMN_PROPID|Int64|  
|ROWSET_NUMBER|Int64|  
|ORDINAL_POSITION|Int64|  
|IS_NULLABLE|Boolean|  
|DATA_TYPE|Int32|  
|TYPE_GUID|Identifikátor GUID|  
|CHARACTER_MAXIMUM_LENGTH|Int64|  
|CHARACTER_OCTET_LENGTH|Int64|  
|NUMERIC_PRECISION|Int32|  
|NUMERIC_SCALE|Int16|  
|POPIS|String|  
|PŘETÍŽENÍ|Int16|  
  
### <a name="views"></a>zobrazení  
  
|columnName|Datový typ|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|VIEW_DEFINITION|String|  
|CHECK_OPTION|Boolean|  
|IS_UPDATABLE|Boolean|  
|POPIS|String|  
|DATE_CREATED|DateTime|  
|DATE_MODIFIED|DateTime|  
  
### <a name="indexes"></a>Indexy  
  
|columnName|Datový typ|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|INDEX_CATALOG|String|  
|INDEX_SCHEMA|String|  
|INDEX_NAME|String|  
|PRIMARY_KEY|Boolean|  
|JEDINEČNÉ|Boolean|  
|CLUSTERED|Boolean|  
|TYP|Int32|  
|FILL_FACTOR|Int32|  
|INITIAL_SIZE|Int32|  
|NULLS|Int32|  
|SORT_BOOKMARKS|Boolean|  
|AUTO_UPDATE|Boolean|  
|NULL_COLLATION|Int32|  
|ORDINAL_POSITION|Int64|  
|COLUMN_NAME|String|  
|COLUMN_GUID|Identifikátor GUID|  
|COLUMN_PROPID|Int64|  
|KOLACE|Int16|  
|MOHUTNOST|Desetinné číslo|  
|STRÁNKY|Int32|  
|FILTER_CONDITION|String|  
|INTEGROVANÉ|Boolean|  
  
## <a name="microsoft-jet-ole-db-provider"></a>Zprostředkovatel Microsoft Jet OLE DB  
 Microsoft Jet OLE DB ovladač podporuje následující kolekce konkrétní schématu kromě běžných kolekcemi schémat:  
  
-   Tabulky  
  
-   Sloupce  
  
-   Procedury  
  
-   zobrazení  
  
-   Indexy  
  
### <a name="tables"></a>Tabulky  
  
|columnName|Datový typ|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|TABLE_TYPE|String|  
|TABLE_GUID|Identifikátor GUID|  
|POPIS|String|  
|TABLE_PROPID|Int64|  
|DATE_CREATED|DateTime|  
|DATE_MODIFIED|DateTime|  
  
### <a name="columns"></a>Sloupce  
  
|columnName|Datový typ|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|COLUMN_NAME|String|  
|COLUMN_GUID|Identifikátor GUID|  
|COLUMN_PROPID|Int64|  
|ORDINAL_POSITION|Int64|  
|COLUMN_HASDEFAULT|Boolean|  
|COLUMN_DEFAULT|String|  
|COLUMN_FLAGS|Int64|  
|IS_NULLABLE|Boolean|  
|DATA_TYPE|Int32|  
|TYPE_GUID|Identifikátor GUID|  
|CHARACTER_MAXIMUM_LENGTH|Int64|  
|CHARACTER_OCTET_LENGTH|Int64|  
|NUMERIC_PRECISION|Int32|  
|NUMERIC_SCALE|Int16|  
|DATETIME_PRECISION|Int64|  
|CHARACTER_SET_CATALOG|String|  
|CHARACTER_SET_SCHEMA|String|  
|CHARACTER_SET_NAME|String|  
|COLLATION_CATALOG|String|  
|COLLATION_SCHEMA|String|  
|COLLATION_NAME|String|  
|DOMAIN_CATALOG|String|  
|DOMAIN_SCHEMA|String|  
|DOMAIN_NAME|String|  
|POPIS|String|  
  
### <a name="procedures"></a>Procedury  
  
|columnName|Datový typ|  
|----------------|--------------|  
|PROCEDURE_CATALOG|String|  
|PROCEDURE_SCHEMA|String|  
|PROCEDURE_NAME|String|  
|PROCEDURE_TYPE|Int16|  
|PROCEDURE_DEFINITION|String|  
|POPIS|String|  
|DATE_CREATED|DateTime|  
|DATE_MODIFIED|DateTime|  
  
### <a name="views"></a>zobrazení  
  
|columnName|Datový typ|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|VIEW_DEFINITION|String|  
|CHECK_OPTION|Boolean|  
|IS_UPDATABLE|Boolean|  
|POPIS|String|  
|DATE_CREATED|DateTime|  
|DATE_MODIFIED|DateTime|  
  
### <a name="indexes"></a>Indexy  
  
|columnName|Datový typ|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|INDEX_CATALOG|String|  
|INDEX_SCHEMA|String|  
|INDEX_NAME|String|  
|PRIMARY_KEY|Boolean|  
|JEDINEČNÉ|Boolean|  
|CLUSTERED|Boolean|  
|TYP|Int32|  
|FILL_FACTOR|Int32|  
|INITIAL_SIZE|Int32|  
|NULLS|Int32|  
|SORT_BOOKMARKS|Boolean|  
|AUTO_UPDATE|Boolean|  
|NULL_COLLATION|Int32|  
|ORDINAL_POSITION|Int64|  
|COLUMN_NAME|String|  
|COLUMN_GUID|Identifikátor GUID|  
|COLUMN_PROPID|Int64|  
|KOLACE|Int16|  
|MOHUTNOST|Desetinné číslo|  
|STRÁNKY|Int32|  
|FILTER_CONDITION|String|  
|INTEGROVANÉ|Boolean|  
  
## <a name="see-also"></a>Viz také  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
