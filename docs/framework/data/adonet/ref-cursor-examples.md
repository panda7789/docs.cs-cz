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
# <a name="ref-cursor-examples"></a><span data-ttu-id="c5158-102">Příklady REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="c5158-102">REF CURSOR Examples</span></span>
<span data-ttu-id="c5158-103">Příklady REFERENČNÍch ukazatelů se skládají z následujících tří příkladů Visual Basic společnosti Microsoft, které ukazují použití odkazů REF.</span><span class="sxs-lookup"><span data-stu-id="c5158-103">The REF CURSOR examples are comprised of the following three Microsoft Visual Basic examples that demonstrate using REF CURSORs.</span></span>  
  
|<span data-ttu-id="c5158-104">Ukázka</span><span class="sxs-lookup"><span data-stu-id="c5158-104">Sample</span></span>|<span data-ttu-id="c5158-105">Popis</span><span class="sxs-lookup"><span data-stu-id="c5158-105">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c5158-106">Parametry REF CURSOR v čtečce OracleDataReader</span><span class="sxs-lookup"><span data-stu-id="c5158-106">REF CURSOR Parameters in an OracleDataReader</span></span>](ref-cursor-parameters-in-an-oracledatareader.md)|<span data-ttu-id="c5158-107">Tento příklad provede uloženou proceduru PL/SQL, která vrací parametr REF CURSOR a přečte hodnotu jako <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="c5158-107">This example executes a PL/SQL stored procedure that returns a REF CURSOR parameter, and reads the value as an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>|  
|[<span data-ttu-id="c5158-108">Načítání dat z více typů REF CURSOR pomocí čtečky OracleDataReader</span><span class="sxs-lookup"><span data-stu-id="c5158-108">Retrieving Data from Multiple REF CURSORs Using an OracleDataReader</span></span>](retrieving-data-from-multiple-ref-cursors.md)|<span data-ttu-id="c5158-109">Tento příklad provede uloženou proceduru PL/SQL, která vrátí dva parametry REF CURSOR a přečte hodnoty pomocí **OracleDataReader**.</span><span class="sxs-lookup"><span data-stu-id="c5158-109">This example executes a PL/SQL stored procedure that returns two REF CURSOR parameters, and reads the values using an **OracleDataReader**.</span></span>|  
|[<span data-ttu-id="c5158-110">Naplnění datové sady pomocí jednoho nebo více typů REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="c5158-110">Filling a DataSet Using One or More REF CURSORs</span></span>](filling-a-dataset-using-one-or-more-ref-cursors.md)|<span data-ttu-id="c5158-111">Tento příklad provede uloženou proceduru PL/SQL, která vrátí dva parametry REF CURSOR a vyplní <xref:System.Data.DataSet> řádky, které jsou vráceny.</span><span class="sxs-lookup"><span data-stu-id="c5158-111">This example executes a PL/SQL stored procedure that returns two REF CURSOR parameters, and fills a <xref:System.Data.DataSet> with the rows that are returned.</span></span>|  
  
 <span data-ttu-id="c5158-112">Chcete-li použít tyto příklady, budete pravděpodobně muset vytvořit tabulky Oracle a musíte vytvořit balíček PL/SQL a tělo balíčku.</span><span class="sxs-lookup"><span data-stu-id="c5158-112">To use these examples, you may need to create the Oracle tables, and you must create a PL/SQL package and package body.</span></span>  
  
## <a name="creating-the-oracle-tables"></a><span data-ttu-id="c5158-113">Vytváření tabulek Oracle</span><span class="sxs-lookup"><span data-stu-id="c5158-113">Creating the Oracle Tables</span></span>  
 <span data-ttu-id="c5158-114">V těchto příkladech se používají tabulky definované ve schématu Oracle Scott/tygr.</span><span class="sxs-lookup"><span data-stu-id="c5158-114">These examples use tables that are defined in the Oracle Scott/Tiger schema.</span></span> <span data-ttu-id="c5158-115">Schéma Oracle Scott/tygr je součástí většiny instalací Oracle.</span><span class="sxs-lookup"><span data-stu-id="c5158-115">The Oracle Scott/Tiger schema is included with most Oracle installations.</span></span> <span data-ttu-id="c5158-116">Pokud toto schéma neexistuje, můžete k vytvoření tabulek a indexů používaných v těchto příkladech použít soubor příkazů SQL v {OracleHome} \rdbms\admin\scott.SQL.</span><span class="sxs-lookup"><span data-stu-id="c5158-116">If this schema does not exist, you can use the SQL commands file in {OracleHome}\rdbms\admin\scott.sql to create the tables and indexes used by these examples.</span></span>  
  
## <a name="creating-the-oracle-package-and-package-body"></a><span data-ttu-id="c5158-117">Vytvoření balíčku a textu balíčku Oracle</span><span class="sxs-lookup"><span data-stu-id="c5158-117">Creating the Oracle Package and Package Body</span></span>  
 <span data-ttu-id="c5158-118">Tyto příklady vyžadují následující balíček PL/SQL a tělo balíčku na vašem serveru.</span><span class="sxs-lookup"><span data-stu-id="c5158-118">These examples require the following PL/SQL package and package body on your server.</span></span> <span data-ttu-id="c5158-119">Na serveru Oracle vytvořte následující balíček Oracle.</span><span class="sxs-lookup"><span data-stu-id="c5158-119">Create the following Oracle package on the Oracle server.</span></span>  
  
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
  
 <span data-ttu-id="c5158-120">Na serveru Oracle vytvořte následující text balíčku Oracle.</span><span class="sxs-lookup"><span data-stu-id="c5158-120">Create the following Oracle package body on the Oracle server.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c5158-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c5158-121">See also</span></span>

- [<span data-ttu-id="c5158-122">Soubory Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="c5158-122">Oracle REF CURSORs</span></span>](oracle-ref-cursors.md)
- [<span data-ttu-id="c5158-123">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c5158-123">ADO.NET Overview</span></span>](ado-net-overview.md)
