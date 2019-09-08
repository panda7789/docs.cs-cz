---
title: Příklady REF CURSOR
ms.date: 03/30/2017
ms.assetid: c257da03-c6c9-4cf8-b591-b7740a962c40
ms.openlocfilehash: 24830452e6d1ab11605ffa88a925fbc55c80b9bf
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794704"
---
# <a name="ref-cursor-examples"></a>Příklady REF CURSOR
Příklady REFERENČNÍch ukazatelů se skládají z následujících tří příkladů Visual Basic společnosti Microsoft, které ukazují použití odkazů REF.  
  
|Ukázka|Popis|  
|------------|-----------------|  
|[Parametry REF CURSOR v čtečce OracleDataReader](ref-cursor-parameters-in-an-oracledatareader.md)|Tento příklad provede uloženou proceduru PL/SQL, která vrací parametr REF CURSOR a přečte hodnotu jako <xref:System.Data.OracleClient.OracleDataReader>.|  
|[Načítání dat z více typů REF CURSOR pomocí čtečky OracleDataReader](retrieving-data-from-multiple-ref-cursors.md)|Tento příklad provede uloženou proceduru PL/SQL, která vrátí dva parametry REF CURSOR a přečte hodnoty pomocí **OracleDataReader**.|  
|[Naplnění datové sady pomocí jednoho nebo více typů REF CURSOR](filling-a-dataset-using-one-or-more-ref-cursors.md)|Tento příklad provede uloženou proceduru PL/SQL, která vrátí dva parametry REF CURSOR a vyplní <xref:System.Data.DataSet> řádky, které jsou vráceny.|  
  
 Chcete-li použít tyto příklady, budete pravděpodobně muset vytvořit tabulky Oracle a musíte vytvořit balíček PL/SQL a tělo balíčku.  
  
## <a name="creating-the-oracle-tables"></a>Vytváření tabulek Oracle  
 V těchto příkladech se používají tabulky definované ve schématu Oracle Scott/tygr. Schéma Oracle Scott/tygr je součástí většiny instalací Oracle. Pokud toto schéma neexistuje, můžete k vytvoření tabulek a indexů používaných v těchto příkladech použít soubor příkazů SQL v {OracleHome} \rdbms\admin\scott.SQL.  
  
## <a name="creating-the-oracle-package-and-package-body"></a>Vytvoření balíčku a textu balíčku Oracle  
 Tyto příklady vyžadují následující balíček PL/SQL a tělo balíčku na vašem serveru. Na serveru Oracle vytvořte následující balíček Oracle.  
  
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
  
 Na serveru Oracle vytvořte následující text balíčku Oracle.  
  
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

- [Soubory Oracle REF CURSOR](oracle-ref-cursors.md)
- [Přehled ADO.NET](ado-net-overview.md)
