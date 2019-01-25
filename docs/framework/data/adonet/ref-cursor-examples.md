---
title: Příklady REF CURSOR
ms.date: 03/30/2017
ms.assetid: c257da03-c6c9-4cf8-b591-b7740a962c40
ms.openlocfilehash: 00e1cd1b9c13514979ee22b32996d35e1bd1c3e2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54615345"
---
# <a name="ref-cursor-examples"></a>Příklady REF CURSOR
Příklady REF CURSOR se skládají z následující tři příklady Microsoft Visual Basic, které ukazují používání typů REF CURSOR.  
  
|Ukázka|Popis|  
|------------|-----------------|  
|[Parametry REF CURSOR v čtečce OracleDataReader](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)|Tento příklad spustí PL/uložené procedury SQL, který vrací parametr REF CURSOR a přečte hodnotu jako <xref:System.Data.OracleClient.OracleDataReader>.|  
|[Načítání dat z více typů REF CURSOR pomocí čtečky OracleDataReader](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)|Tento příklad spustí PL/SQL uložené procedury, která vrací dva parametry REF CURSOR a čte hodnoty pomocí **připojení OracleDataReader**.|  
|[Naplnění datové sady pomocí jednoho nebo více typů REF CURSOR](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)|Tento příklad spustí PL/SQL uložené procedury, která vrací dva parametry REF CURSOR a doplní <xref:System.Data.DataSet> s řádky, které jsou vráceny.|  
  
 Pokud chcete použít tyto příklady, budete muset vytvořit tabulky Oracle a je nutné vytvořit balíček PL/SQL a tělo balíčku.  
  
## <a name="creating-the-oracle-tables"></a>Vytváření tabulek Oracle  
 Tyto příklady použití tabulek, které jsou definovány ve schématu Oracle Scott/tygr. Oracle Scott/Tiger schématu je součástí většiny instalací Oracle. Pokud toto schéma neexistuje, můžete použít soubor příkazů SQL v {OracleHome}\rdbms\admin\scott.sql vytvářet tabulky a indexy, které používají tyto příklady.  
  
## <a name="creating-the-oracle-package-and-package-body"></a>Vytváření balíčku Oracle a tělo balíčku  
 Tyto příklady vyžadují následující balíček PL/SQL a tělo balíčku na serveru. Vytvořte následující balíček Oracle na serveru Oracle.  
  
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
  
 Vytvořte následující tělo balíčku Oracle na serveru Oracle.  
  
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
  
## <a name="see-also"></a>Viz také:
- [Soubory Oracle REF CURSOR](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
