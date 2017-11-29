---
title: "Kolekce schématu rozhraní ODBC"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 889e84db39af1257d709ef049e18d4397ea700d0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="odbc-schema-collections"></a>Kolekce schématu rozhraní ODBC
Tato část popisuje podporu kolekci schématu pro ovladače ODBC pro Microsoft SQL Server, Oracle a Microsoft Jet.  
  
## <a name="microsoft-sql-server-odbc-driver"></a>Ovladač ODBC Microsoft SQL Server  
 Ovladač ODBC Microsoft SQL Server podporuje následující kolekce konkrétní schématu kromě běžných kolekcemi schémat:  
  
-   Tabulky  
  
-   Indexy  
  
-   Sloupce  
  
-   Procedury  
  
-   ProcedureColumns  
  
-   ProcedureParameters  
  
-   zobrazení  
  
### <a name="tables-and-views"></a>Tabulky a zobrazení  
  
|columnName|Datový typ|  
|----------------|--------------|  
|TABLE_CAT|String|  
|TABLE_SCHEM|String|  
|TABLE_NAME|String|  
|TABLE_TYPE|String|  
|POZNÁMKY|String|  
  
### <a name="indexes"></a>Indexy  
  
|columnName|Datový typ|  
|----------------|--------------|  
|TABLE_CAT|String|  
|TABLE_SCHEM|String|  
|TABLE_NAME|String|  
|NON_UNIQUE|Int16|  
|INDEX_QUALIFIER|String|  
|INDEX_NAME|String|  
|TYP|Int16|  
|ORDINAL_POSITION|Int16|  
|COLUMN_NAME|String|  
|ASC_OR_DESC|String|  
|CARDINATLITY|Int32|  
|STRÁNKY|Int32|  
|FILTER_CONDITION|String|  
|SS_TYPE_SCHEMA|String|  
|SS_DATA_TYPE|Byte|  
  
### <a name="columns"></a>Sloupce  
  
|columnName|Datový typ|  
|----------------|--------------|  
|TABLE_CAT|String|  
|TABLE_SCHEM|String|  
|TABLE_NAME|String|  
|COLUMN_NAME|String|  
|DATA_TYPE|Int16|  
|TYPE_NAME|String|  
|COLUMN_SIZE|Int32|  
|BUFFER_LENGTH|Int32|  
|DECIMAL_DIGITS|Int16|  
|NUM_PREC_RADIX|Int16|  
|S MOŽNOU HODNOTOU NULL|Int16|  
|POZNÁMKY|String|  
|COLUMN_DEF|String|  
|SQL_DATA_TYPE|Int16|  
|SQL_DATETIME_SUB|Int16|  
|CHAR_OCTET_LENGTH|Int32|  
|ORDINAL_POSITION|Int32|  
|IS_NULLABLE|String|  
|SS_TYPE_CATALOG|String|  
|SS_TYPE_SCHEMA|String|  
|SS_DATA_TYPE|Byte|  
  
### <a name="procedures"></a>Procedury  
  
|columnName|Datový typ|  
|----------------|--------------|  
|PROCEDURE_CAT|String|  
|PROCEDURE_SCHEM|String|  
|PROCEDURE_NAME|String|  
|NUM_INPUT_PARAMS|Int32|  
|NUM_OUTPUT_PARAMS|Int32|  
|NUM_RESULT_SETS|Int32|  
|POZNÁMKY|String|  
|PROCEDURE_TYPE|Int16|  
  
### <a name="procedurecolumns"></a>ProcedureColumns  
  
|columnName|Datový typ|  
|----------------|--------------|  
|PROCEDURE_CAT|String|  
|PROCEDURE_SCHEM|String|  
|PROCEDURE_NAME|String|  
|COLUMN_NAME|String|  
|COLUMN_TYPE|Int16|  
|DATA_TYPE|Int16|  
|TYPE_NAME|String|  
|COLUMN_SIZE|Int32|  
|BUFFER_LENGTH|Int32|  
|DECIMAL_DIGITS|Int16|  
|NUM_PREC_RADIX|Int16|  
|S MOŽNOU HODNOTOU NULL|Int16|  
|POZNÁMKY|String|  
|COLUMN_DEF|String|  
|SQL_DATA_TYPE|Int16|  
|SQL_DATETIME_SUB|Int16|  
|CHAR_OCTET_LENGTH|Int32|  
|ORDINAL_POSITION|Int32|  
|IS_NULLABLE|String|  
|SS_TYPE_CATALOG|String|  
|SS_TYPE_SCHEMA|String|  
|SS_DATA_TYPE|Byte|  
  
### <a name="procedureparameters"></a>ProcedureParameters  
  
|columnName|Datový typ|  
|----------------|--------------|  
|PROCEDURE_CAT|String|  
|PROCEDURE_SCHEM|String|  
|PROCEDURE_NAME|String|  
|COLUMN_NAME|String|  
|COLUMN_TYPE|Int16|  
|DATA_TYPE|Int16|  
|TYPE_NAME|String|  
|COLUMN_SIZE|Int32|  
|BUFFER_LENGTH|Int32|  
|DECIMAL_DIGITS|Int16|  
|NUM_PREC_RADIX|Int16|  
|S MOŽNOU HODNOTOU NULL|Int16|  
|POZNÁMKY|String|  
|COLUMN_DEF|String|  
|SQL_DATA_TYPE|Int16|  
|SQL_DATETIME_SUB|Int16|  
|CHAR_OCTET_LENGTH|Int32|  
|ORDINAL_POSITION|Int32|  
|IS_NULLABLE|String|  
|SS_TYPE_CATALOG|String|  
|SS_TYPE_SCHEMA|String|  
|SS_DATA_TYPE|Byte|  
  
## <a name="microsoft-oracle-odbc-driver"></a>Ovladač ODBC Microsoft Oracle  
 Ovladač ODBC Microsoft SQL Server Oracle podporuje následující kolekce konkrétní schématu kromě běžných kolekcemi schémat:  
  
-   Tabulky  
  
-   Sloupce  
  
-   Procedury  
  
-   ProcedureColumns  
  
-   ProcedureParameters  
  
-   zobrazení  
  
-   Indexy  
  
### <a name="tables-and-views"></a>Tabulky a zobrazení  
  
|columnName|Datový typ|  
|----------------|--------------|  
|TABLE_QUALIFIER|String|  
|TABLE_OWNER|String|  
|TABLE_NAME|String|  
|TABLE_TYPE|String|  
|POZNÁMKY|String|  
  
### <a name="columns"></a>Sloupce  
  
|columnName|Datový typ|  
|----------------|--------------|  
|TABLE_QUALIFIER|String|  
|TABLE_OWNER|String|  
|TABLE_NAME|String|  
|COLUMN_NAME|String|  
|DATA_TYPE|Int16|  
|TYPE_NAME|String|  
|PŘESNOST|Int32|  
|DÉLKA|Int32|  
|ŠKÁLOVÁNÍ|Int16|  
|ZÁKLAD –|Int16|  
|S MOŽNOU HODNOTOU NULL|Int16|  
|POZNÁMKY|String|  
|ORDINAL_POSITION|Int32|  
  
### <a name="procedures"></a>Procedury  
  
|columnName|Datový typ|  
|----------------|--------------|  
|PROCEDURE_QUALIFIER|String|  
|PROCEDURE_OWNER|String|  
|PROCEDURE_NAME|String|  
|NUM_INPUT_PARAMS|Int16|  
|NUM_OUTPUT_PARAMS|Int16|  
|NUM_RESULT_SETS|Int16|  
|POZNÁMKY|String|  
|PROCEDURE_TYPE|Int16|  
  
### <a name="procedurecolumns"></a>ProcedureColumns  
  
|columnName|Datový typ|  
|----------------|--------------|  
|PROCEDURE_QUALIFIER|String|  
|PROCEDURE_OWNER|String|  
|PROCEDURE_NAME|String|  
|COLUMN_NAME|String|  
|COLUMN_TYPE|Int16|  
|DATA_TYPE|Int16|  
|TYPE_NAME|String|  
|PŘESNOST|Int32|  
|DÉLKA|Int32|  
|ŠKÁLOVÁNÍ|Int16|  
|ZÁKLAD –|Int16|  
|S MOŽNOU HODNOTOU NULL|Int16|  
|POZNÁMKY|String|  
|PŘETÍŽENÍ|Int32|  
|ORDINAL_POSITION|Int32|  
  
## <a name="microsoft-jet-odbc-driver"></a>Ovladač ODBC Microsoft Jet  
 Ovladač ODBC Microsoft Jet podporuje následující kolekce konkrétní schématu kromě běžných kolekcemi schémat:  
  
-   Tabulky  
  
-   Indexy  
  
-   Sloupce  
  
-   Procedury  
  
-   ProcedureColumns  
  
-   ProcedureParameters  
  
-   zobrazení  
  
### <a name="tables-and-views"></a>Tabulky a zobrazení  
  
|columnName|Datový typ|  
|----------------|--------------|  
|TABLE_QUALIFIER|String|  
|TABLE_OWNER|String|  
|TABLE_NAME|String|  
|TABLE_TYPE|String|  
|POZNÁMKY|String|  
  
### <a name="columns"></a>Sloupce  
  
|columnName|Datový typ|  
|----------------|--------------|  
|TABLE_QUALIFIER|String|  
|TABLE_OWNER|String|  
|TABLE_NAME|String|  
|COLUMN_NAME|String|  
|DATA_TYPE|Int16|  
|TYPE_NAME|String|  
|PŘESNOST|Int32|  
|DÉLKA|Int32|  
|ŠKÁLOVÁNÍ|Int16|  
|ZÁKLAD –|Int16|  
|S MOŽNOU HODNOTOU NULL|Int16|  
|POZNÁMKY|String|  
|ORDINAL_POSITION|Int32|  
  
### <a name="procedures"></a>Procedury  
  
|columnName|Datový typ|  
|----------------|--------------|  
|PROCEDURE_QUALIFIER|String|  
|PROCEDURE_OWNER|String|  
|PROCEDURE_NAME|String|  
|NUM_INPUT_PARAMS|Int16|  
|NUM_OUTPUT_PARAMS|Int16|  
|NUM_RESULT_SETS|Int16|  
|POZNÁMKY|String|  
|PROCEDURE_TYPE|Int16|  
  
### <a name="procedurecolumns"></a>ProcedureColumns  
  
|columnName|Datový typ|  
|----------------|--------------|  
|PROCEDURE_QUALIFIER|String|  
|PROCEDURE_OWNER|String|  
|PROCEDURE_NAME|String|  
|COLUMN_NAME|String|  
|COLUMN_TYPE|Int16|  
|DATA_TYPE|Int16|  
|TYPE_NAME|String|  
|PŘESNOST|Int32|  
|DÉLKA|Int32|  
|ŠKÁLOVÁNÍ|Int16|  
|ZÁKLAD –|Int16|  
|S MOŽNOU HODNOTOU NULL|Int16|  
|POZNÁMKY|String|  
|PŘETÍŽENÍ|Int32|  
|ORDINAL_POSITION|Int32|  
  
### <a name="procedureparameters"></a>ProcedureParameters  
  
|columnName|Datový typ|  
|----------------|--------------|  
|PROCEDURE_CAT|String|  
|PROCEDURE_SCHEM|String|  
|PROCEDURE_NAME|String|  
|COLUMN_NAME|String|  
|COLUMN_TYPE|Int16|  
|DATA_TYPE|Int16|  
|TYPE_NAME|String|  
|COLUMN_SIZE|Int32|  
|BUFFER_LENGTH|Int32|  
|DECIMAL_DIGITS|Int16|  
|NUM_PREC_RADIX|Int16|  
|S MOŽNOU HODNOTOU NULL|Int16|  
|POZNÁMKY|String|  
|COLUMN_DEF|String|  
|SQL_DATA_TYPE|Int16|  
|SQL_DATETIME_SUB|Int16|  
|CHAR_OCTET_LENGTH|Int32|  
|ORDINAL_POSITION|Int32|  
|IS_NULLABLE|String|  
  
## <a name="see-also"></a>Viz také  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
