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
# <a name="ref-cursor-examples"></a><span data-ttu-id="000b2-102">Příklady REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="000b2-102">REF CURSOR Examples</span></span>
<span data-ttu-id="000b2-103">Příklady REF CURSOR se skládají z následující tři příklady Microsoft Visual Basic, které ukazují používání typů REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="000b2-103">The REF CURSOR examples are comprised of the following three Microsoft Visual Basic examples that demonstrate using REF CURSORs.</span></span>  
  
|<span data-ttu-id="000b2-104">Ukázka</span><span class="sxs-lookup"><span data-stu-id="000b2-104">Sample</span></span>|<span data-ttu-id="000b2-105">Popis</span><span class="sxs-lookup"><span data-stu-id="000b2-105">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="000b2-106">Parametry REF CURSOR v čtečce OracleDataReader</span><span class="sxs-lookup"><span data-stu-id="000b2-106">REF CURSOR Parameters in an OracleDataReader</span></span>](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)|<span data-ttu-id="000b2-107">Tento příklad spustí PL/uložené procedury SQL, který vrací parametr REF CURSOR a přečte hodnotu jako <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="000b2-107">This example executes a PL/SQL stored procedure that returns a REF CURSOR parameter, and reads the value as an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>|  
|[<span data-ttu-id="000b2-108">Načítání dat z více typů REF CURSOR pomocí čtečky OracleDataReader</span><span class="sxs-lookup"><span data-stu-id="000b2-108">Retrieving Data from Multiple REF CURSORs Using an OracleDataReader</span></span>](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)|<span data-ttu-id="000b2-109">Tento příklad spustí PL/SQL uložené procedury, která vrací dva parametry REF CURSOR a čte hodnoty pomocí **připojení OracleDataReader**.</span><span class="sxs-lookup"><span data-stu-id="000b2-109">This example executes a PL/SQL stored procedure that returns two REF CURSOR parameters, and reads the values using an **OracleDataReader**.</span></span>|  
|[<span data-ttu-id="000b2-110">Naplnění datové sady pomocí jednoho nebo více typů REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="000b2-110">Filling a DataSet Using One or More REF CURSORs</span></span>](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)|<span data-ttu-id="000b2-111">Tento příklad spustí PL/SQL uložené procedury, která vrací dva parametry REF CURSOR a doplní <xref:System.Data.DataSet> s řádky, které jsou vráceny.</span><span class="sxs-lookup"><span data-stu-id="000b2-111">This example executes a PL/SQL stored procedure that returns two REF CURSOR parameters, and fills a <xref:System.Data.DataSet> with the rows that are returned.</span></span>|  
  
 <span data-ttu-id="000b2-112">Pokud chcete použít tyto příklady, budete muset vytvořit tabulky Oracle a je nutné vytvořit balíček PL/SQL a tělo balíčku.</span><span class="sxs-lookup"><span data-stu-id="000b2-112">To use these examples, you may need to create the Oracle tables, and you must create a PL/SQL package and package body.</span></span>  
  
## <a name="creating-the-oracle-tables"></a><span data-ttu-id="000b2-113">Vytváření tabulek Oracle</span><span class="sxs-lookup"><span data-stu-id="000b2-113">Creating the Oracle Tables</span></span>  
 <span data-ttu-id="000b2-114">Tyto příklady použití tabulek, které jsou definovány ve schématu Oracle Scott/tygr.</span><span class="sxs-lookup"><span data-stu-id="000b2-114">These examples use tables that are defined in the Oracle Scott/Tiger schema.</span></span> <span data-ttu-id="000b2-115">Oracle Scott/Tiger schématu je součástí většiny instalací Oracle.</span><span class="sxs-lookup"><span data-stu-id="000b2-115">The Oracle Scott/Tiger schema is included with most Oracle installations.</span></span> <span data-ttu-id="000b2-116">Pokud toto schéma neexistuje, můžete použít soubor příkazů SQL v {OracleHome}\rdbms\admin\scott.sql vytvářet tabulky a indexy, které používají tyto příklady.</span><span class="sxs-lookup"><span data-stu-id="000b2-116">If this schema does not exist, you can use the SQL commands file in {OracleHome}\rdbms\admin\scott.sql to create the tables and indexes used by these examples.</span></span>  
  
## <a name="creating-the-oracle-package-and-package-body"></a><span data-ttu-id="000b2-117">Vytváření balíčku Oracle a tělo balíčku</span><span class="sxs-lookup"><span data-stu-id="000b2-117">Creating the Oracle Package and Package Body</span></span>  
 <span data-ttu-id="000b2-118">Tyto příklady vyžadují následující balíček PL/SQL a tělo balíčku na serveru.</span><span class="sxs-lookup"><span data-stu-id="000b2-118">These examples require the following PL/SQL package and package body on your server.</span></span> <span data-ttu-id="000b2-119">Vytvořte následující balíček Oracle na serveru Oracle.</span><span class="sxs-lookup"><span data-stu-id="000b2-119">Create the following Oracle package on the Oracle server.</span></span>  
  
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
  
 <span data-ttu-id="000b2-120">Vytvořte následující tělo balíčku Oracle na serveru Oracle.</span><span class="sxs-lookup"><span data-stu-id="000b2-120">Create the following Oracle package body on the Oracle server.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="000b2-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="000b2-121">See also</span></span>
- [<span data-ttu-id="000b2-122">Soubory Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="000b2-122">Oracle REF CURSORs</span></span>](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)
- [<span data-ttu-id="000b2-123">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="000b2-123">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
