---
title: Kolekce schémat ODBC
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: 072a9cd365031cd5660d1824bc229d459abc5af8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54525830"
---
# <a name="odbc-schema-collections"></a>Kolekce schémat ODBC
Tato část popisuje kolekci podpora schématu pro ovladače ODBC pro Microsoft SQL Server, Oracle a Microsoft Jet.  
  
## <a name="microsoft-sql-server-odbc-driver"></a>Ovladač ODBC Microsoft SQL Server  
 Ovladače ODBC Microsoft SQL Server podporuje následující kolekce určité schéma kromě společné kolekce schémat:  
  
-   Tabulky  
  
-   Indexy  
  
-   Sloupce  
  
-   Procedury  
  
-   ProcedureColumns  
  
-   ProcedureParameters  
  
-   Zobrazení  
  
### <a name="tables-and-views"></a>Tabulky a zobrazení  
  
|Názevsloupce|DataType|  
|----------------|--------------|  
|TABLE_CAT|String|  
|TABLE_SCHEM|String|  
|TABLE_NAME|String|  
|TABLE_TYPE|String|  
|POZNÁMKY|String|  
  
### <a name="indexes"></a>Indexy  
  
|Názevsloupce|DataType|  
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
  
|Názevsloupce|DataType|  
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
|S POVOLENOU HODNOTOU NULL|Int16|  
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
  
|Názevsloupce|DataType|  
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
  
|Názevsloupce|DataType|  
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
|S POVOLENOU HODNOTOU NULL|Int16|  
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
  
|Názevsloupce|DataType|  
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
|S POVOLENOU HODNOTOU NULL|Int16|  
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
 Ovladače ODBC Microsoft SQL Server Oracle podporuje následující kolekce určité schéma kromě společné kolekce schémat:  
  
-   Tabulky  
  
-   Sloupce  
  
-   Procedury  
  
-   ProcedureColumns  
  
-   ProcedureParameters  
  
-   Zobrazení  
  
-   Indexy  
  
### <a name="tables-and-views"></a>Tabulky a zobrazení  
  
|Názevsloupce|DataType|  
|----------------|--------------|  
|TABLE_QUALIFIER|String|  
|TABLE_OWNER|String|  
|TABLE_NAME|String|  
|TABLE_TYPE|String|  
|POZNÁMKY|String|  
  
### <a name="columns"></a>Sloupce  
  
|Názevsloupce|DataType|  
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
|RADIX|Int16|  
|S POVOLENOU HODNOTOU NULL|Int16|  
|POZNÁMKY|String|  
|ORDINAL_POSITION|Int32|  
  
### <a name="procedures"></a>Procedury  
  
|Názevsloupce|DataType|  
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
  
|Názevsloupce|DataType|  
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
|RADIX|Int16|  
|S POVOLENOU HODNOTOU NULL|Int16|  
|POZNÁMKY|String|  
|PŘETÍŽENÍ|Int32|  
|ORDINAL_POSITION|Int32|  
  
## <a name="microsoft-jet-odbc-driver"></a>Ovladač ODBC Microsoft Jet  
 Ovladač ODBC Microsoft Jet podporuje následující kolekce určité schéma kromě společné kolekce schémat:  
  
-   Tabulky  
  
-   Indexy  
  
-   Sloupce  
  
-   Procedury  
  
-   ProcedureColumns  
  
-   ProcedureParameters  
  
-   Zobrazení  
  
### <a name="tables-and-views"></a>Tabulky a zobrazení  
  
|Názevsloupce|DataType|  
|----------------|--------------|  
|TABLE_QUALIFIER|String|  
|TABLE_OWNER|String|  
|TABLE_NAME|String|  
|TABLE_TYPE|String|  
|POZNÁMKY|String|  
  
### <a name="columns"></a>Sloupce  
  
|Názevsloupce|DataType|  
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
|RADIX|Int16|  
|S POVOLENOU HODNOTOU NULL|Int16|  
|POZNÁMKY|String|  
|ORDINAL_POSITION|Int32|  
  
### <a name="procedures"></a>Procedury  
  
|Názevsloupce|DataType|  
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
  
|Názevsloupce|DataType|  
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
|RADIX|Int16|  
|S POVOLENOU HODNOTOU NULL|Int16|  
|POZNÁMKY|String|  
|PŘETÍŽENÍ|Int32|  
|ORDINAL_POSITION|Int32|  
  
### <a name="procedureparameters"></a>ProcedureParameters  
  
|Názevsloupce|DataType|  
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
|S POVOLENOU HODNOTOU NULL|Int16|  
|POZNÁMKY|String|  
|COLUMN_DEF|String|  
|SQL_DATA_TYPE|Int16|  
|SQL_DATETIME_SUB|Int16|  
|CHAR_OCTET_LENGTH|Int32|  
|ORDINAL_POSITION|Int32|  
|IS_NULLABLE|String|  
  
## <a name="see-also"></a>Viz také:
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
