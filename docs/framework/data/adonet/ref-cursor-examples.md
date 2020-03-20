---
title: Příklady REF CURSOR
ms.date: 03/30/2017
ms.assetid: c257da03-c6c9-4cf8-b591-b7740a962c40
ms.openlocfilehash: dc82648ff5a565c9b4d6fa593433ee1e22249d93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149132"
---
# <a name="ref-cursor-examples"></a>Příklady REF CURSOR
Příklady REF CURSOR se skládají z následujících tří příkladů jazyka Microsoft Visual Basic, které ukazují použití REF CURSORs.  
  
|Ukázka|Popis|  
|------------|-----------------|  
|[Parametry REF CURSOR v čtečce OracleDataReader](ref-cursor-parameters-in-an-oracledatareader.md)|Tento příklad spustí uloženou proceduru PL/SQL, která vrací parametr <xref:System.Data.OracleClient.OracleDataReader>REF CURSOR a přečte hodnotu jako .|  
|[Načítání dat z více typů REF CURSOR pomocí čtečky OracleDataReader](retrieving-data-from-multiple-ref-cursors.md)|Tento příklad spustí uloženou proceduru PL/SQL, která vrací dva parametry REF CURSOR a přečte hodnoty pomocí **aplikace OracleDataReader**.|  
|[Naplnění datové sady pomocí jednoho nebo více typů REF CURSOR](filling-a-dataset-using-one-or-more-ref-cursors.md)|Tento příklad spustí uloženou proceduru PL/SQL, která vrací dva <xref:System.Data.DataSet> parametry REF CURSOR a vyplní řádky, které jsou vráceny.|  
  
 Chcete-li použít tyto příklady, může být nutné vytvořit tabulky Oracle a je nutné vytvořit balíček PL/SQL a text balíčku.  
  
## <a name="creating-the-oracle-tables"></a>Vytváření tabulek Oracle  
 Tyto příklady používají tabulky, které jsou definovány ve schématu Oracle Scott/Tiger. Schéma Oracle Scott/Tiger je součástí většiny instalací oracle. Pokud toto schéma neexistuje, můžete k vytvoření tabulek a indexů používaných v těchto příkladech použít soubor příkazů SQL v {OracleHome}\rdbms\admin\scott.sql.  
  
## <a name="creating-the-oracle-package-and-package-body"></a>Vytvoření balíčku Oracle a tělo balíčku  
 Tyto příklady vyžadují následující PL/SQL balíček a text balíčku na serveru. Vytvořte na serveru Oracle následující balíček Oracle.  
  
```sql
CREATE OR REPLACE PACKAGE CURSPKG AS
    TYPE T_CURSOR IS REF CURSOR;
    PROCEDURE OPEN_ONE_CURSOR (N_EMPNO IN NUMBER,
                               IO_CURSOR IN OUT T_CURSOR);
    PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,
                                DEPTCURSOR OUT T_CURSOR);  
END CURSPKG;  
/
```  
  
 Vytvořte na serveru Oracle následující text balíčku Oracle.  
  
```sql
CREATE OR REPLACE PACKAGE BODY CURSPKG AS  
    PROCEDURE OPEN_ONE_CURSOR (N_EMPNO IN NUMBER,  
                               IO_CURSOR IN OUT T_CURSOR)  
    IS
        V_CURSOR T_CURSOR;
    BEGIN
        IF N_EMPNO <> 0
        THEN  
             OPEN V_CURSOR FOR
             SELECT EMP.EMPNO, EMP.ENAME, DEPT.DEPTNO, DEPT.DNAME
                  FROM EMP, DEPT
                  WHERE EMP.DEPTNO = DEPT.DEPTNO
                  AND EMP.EMPNO = N_EMPNO;  
  
        ELSE
             OPEN V_CURSOR FOR
             SELECT EMP.EMPNO, EMP.ENAME, DEPT.DEPTNO, DEPT.DNAME
                  FROM EMP, DEPT
                  WHERE EMP.DEPTNO = DEPT.DEPTNO;  
  
        END IF;  
        IO_CURSOR := V_CURSOR;
    END OPEN_ONE_CURSOR;
  
    PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,  
                                DEPTCURSOR OUT T_CURSOR)  
    IS
        V_CURSOR1 T_CURSOR;
        V_CURSOR2 T_CURSOR;
    BEGIN
        OPEN V_CURSOR1 FOR SELECT * FROM EMP;  
        OPEN V_CURSOR2 FOR SELECT * FROM DEPT;  
        EMPCURSOR  := V_CURSOR1;
        DEPTCURSOR := V_CURSOR2;
    END OPEN_TWO_CURSORS;
END CURSPKG;  
/  
```  
  
## <a name="see-also"></a>Viz také

- [Soubory Oracle REF CURSOR](oracle-ref-cursors.md)
- [Přehled ADO.NET](ado-net-overview.md)
