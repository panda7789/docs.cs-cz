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
# <a name="ref-cursor-examples"></a><span data-ttu-id="a31be-102">Příklady REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="a31be-102">REF CURSOR Examples</span></span>
<span data-ttu-id="a31be-103">Příklady REF CURSOR se skládají z následujících tří příkladů jazyka Microsoft Visual Basic, které ukazují použití REF CURSORs.</span><span class="sxs-lookup"><span data-stu-id="a31be-103">The REF CURSOR examples are comprised of the following three Microsoft Visual Basic examples that demonstrate using REF CURSORs.</span></span>  
  
|<span data-ttu-id="a31be-104">Ukázka</span><span class="sxs-lookup"><span data-stu-id="a31be-104">Sample</span></span>|<span data-ttu-id="a31be-105">Popis</span><span class="sxs-lookup"><span data-stu-id="a31be-105">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a31be-106">Parametry REF CURSOR v čtečce OracleDataReader</span><span class="sxs-lookup"><span data-stu-id="a31be-106">REF CURSOR Parameters in an OracleDataReader</span></span>](ref-cursor-parameters-in-an-oracledatareader.md)|<span data-ttu-id="a31be-107">Tento příklad spustí uloženou proceduru PL/SQL, která vrací parametr <xref:System.Data.OracleClient.OracleDataReader>REF CURSOR a přečte hodnotu jako .</span><span class="sxs-lookup"><span data-stu-id="a31be-107">This example executes a PL/SQL stored procedure that returns a REF CURSOR parameter, and reads the value as an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>|  
|[<span data-ttu-id="a31be-108">Načítání dat z více typů REF CURSOR pomocí čtečky OracleDataReader</span><span class="sxs-lookup"><span data-stu-id="a31be-108">Retrieving Data from Multiple REF CURSORs Using an OracleDataReader</span></span>](retrieving-data-from-multiple-ref-cursors.md)|<span data-ttu-id="a31be-109">Tento příklad spustí uloženou proceduru PL/SQL, která vrací dva parametry REF CURSOR a přečte hodnoty pomocí **aplikace OracleDataReader**.</span><span class="sxs-lookup"><span data-stu-id="a31be-109">This example executes a PL/SQL stored procedure that returns two REF CURSOR parameters, and reads the values using an **OracleDataReader**.</span></span>|  
|[<span data-ttu-id="a31be-110">Naplnění datové sady pomocí jednoho nebo více typů REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="a31be-110">Filling a DataSet Using One or More REF CURSORs</span></span>](filling-a-dataset-using-one-or-more-ref-cursors.md)|<span data-ttu-id="a31be-111">Tento příklad spustí uloženou proceduru PL/SQL, která vrací dva <xref:System.Data.DataSet> parametry REF CURSOR a vyplní řádky, které jsou vráceny.</span><span class="sxs-lookup"><span data-stu-id="a31be-111">This example executes a PL/SQL stored procedure that returns two REF CURSOR parameters, and fills a <xref:System.Data.DataSet> with the rows that are returned.</span></span>|  
  
 <span data-ttu-id="a31be-112">Chcete-li použít tyto příklady, může být nutné vytvořit tabulky Oracle a je nutné vytvořit balíček PL/SQL a text balíčku.</span><span class="sxs-lookup"><span data-stu-id="a31be-112">To use these examples, you may need to create the Oracle tables, and you must create a PL/SQL package and package body.</span></span>  
  
## <a name="creating-the-oracle-tables"></a><span data-ttu-id="a31be-113">Vytváření tabulek Oracle</span><span class="sxs-lookup"><span data-stu-id="a31be-113">Creating the Oracle Tables</span></span>  
 <span data-ttu-id="a31be-114">Tyto příklady používají tabulky, které jsou definovány ve schématu Oracle Scott/Tiger.</span><span class="sxs-lookup"><span data-stu-id="a31be-114">These examples use tables that are defined in the Oracle Scott/Tiger schema.</span></span> <span data-ttu-id="a31be-115">Schéma Oracle Scott/Tiger je součástí většiny instalací oracle.</span><span class="sxs-lookup"><span data-stu-id="a31be-115">The Oracle Scott/Tiger schema is included with most Oracle installations.</span></span> <span data-ttu-id="a31be-116">Pokud toto schéma neexistuje, můžete k vytvoření tabulek a indexů používaných v těchto příkladech použít soubor příkazů SQL v {OracleHome}\rdbms\admin\scott.sql.</span><span class="sxs-lookup"><span data-stu-id="a31be-116">If this schema does not exist, you can use the SQL commands file in {OracleHome}\rdbms\admin\scott.sql to create the tables and indexes used by these examples.</span></span>  
  
## <a name="creating-the-oracle-package-and-package-body"></a><span data-ttu-id="a31be-117">Vytvoření balíčku Oracle a tělo balíčku</span><span class="sxs-lookup"><span data-stu-id="a31be-117">Creating the Oracle Package and Package Body</span></span>  
 <span data-ttu-id="a31be-118">Tyto příklady vyžadují následující PL/SQL balíček a text balíčku na serveru.</span><span class="sxs-lookup"><span data-stu-id="a31be-118">These examples require the following PL/SQL package and package body on your server.</span></span> <span data-ttu-id="a31be-119">Vytvořte na serveru Oracle následující balíček Oracle.</span><span class="sxs-lookup"><span data-stu-id="a31be-119">Create the following Oracle package on the Oracle server.</span></span>  
  
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
  
 <span data-ttu-id="a31be-120">Vytvořte na serveru Oracle následující text balíčku Oracle.</span><span class="sxs-lookup"><span data-stu-id="a31be-120">Create the following Oracle package body on the Oracle server.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a31be-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="a31be-121">See also</span></span>

- [<span data-ttu-id="a31be-122">Soubory Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="a31be-122">Oracle REF CURSORs</span></span>](oracle-ref-cursors.md)
- [<span data-ttu-id="a31be-123">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a31be-123">ADO.NET Overview</span></span>](ado-net-overview.md)
