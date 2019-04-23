---
title: Binární a vysoké hodnoty na SQL Serveru
ms.date: 03/30/2017
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.openlocfilehash: 4b7a3f16726d6363cd702fb912bb7be281a25000
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59192963"
---
# <a name="sql-server-binary-and-large-value-data"></a><span data-ttu-id="de272-102">Binární a vysoké hodnoty na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="de272-102">SQL Server Binary and Large-Value Data</span></span>
<span data-ttu-id="de272-103">SQL Server poskytuje `max` specifikátor, který rozbalí úložnou kapacitu `varchar`, `nvarchar`, a `varbinary` datové typy.</span><span class="sxs-lookup"><span data-stu-id="de272-103">SQL Server provides the `max` specifier, which expands the storage capacity of the `varchar`, `nvarchar`, and `varbinary` data types.</span></span> <span data-ttu-id="de272-104">`varchar(max)`, `nvarchar(max)`, a `varbinary(max)` se společně nazývají *velké hodnoty datových typů*.</span><span class="sxs-lookup"><span data-stu-id="de272-104">`varchar(max)`, `nvarchar(max)`, and `varbinary(max)` are collectively called *large-value data types*.</span></span> <span data-ttu-id="de272-105">Velké hodnoty datové typy, které můžete použít k uložení až 2 ^ 31-1 bajtů.</span><span class="sxs-lookup"><span data-stu-id="de272-105">You can use the large-value data types to store up to 2^31-1 bytes of data.</span></span>  
  
 <span data-ttu-id="de272-106">SQL Server 2008 představuje atribut FILESTREAM, což není typ dat, ale místo toho atribut, který může být definovaný na sloupci, dat. velké hodnoty uložené v systému souborů namísto v databázi.</span><span class="sxs-lookup"><span data-stu-id="de272-106">SQL Server 2008 introduces the FILESTREAM attribute, which is not a data type, but rather an attribute that can be defined on a column, allowing large-value data to be stored on the file system instead of in the database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="de272-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="de272-107">In This Section</span></span>  
 [<span data-ttu-id="de272-108">Úprava vysokých (maximálních) hodnot v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="de272-108">Modifying Large-Value (max) Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/modifying-large-value-max-data.md)  
 <span data-ttu-id="de272-109">Popisuje způsob práce s typy dat vysoké hodnoty.</span><span class="sxs-lookup"><span data-stu-id="de272-109">Describes how to work with the large-value data types.</span></span>  
  
 [<span data-ttu-id="de272-110">Data FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="de272-110">FILESTREAM Data</span></span>](../../../../../docs/framework/data/adonet/sql/filestream-data.md)  
 <span data-ttu-id="de272-111">Popisuje, jak pracovat s daty velké hodnoty uložené v systému SQL Server 2008 s atributem FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="de272-111">Describes how to work with large-value data stored in SQL Server 2008 with the FILESTREAM attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de272-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="de272-112">See also</span></span>

- [<span data-ttu-id="de272-113">Datové typy SQL Serveru a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="de272-113">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)
- [<span data-ttu-id="de272-114">Operace dat na SQL Serveru v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="de272-114">SQL Server Data Operations in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)
- [<span data-ttu-id="de272-115">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="de272-115">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [<span data-ttu-id="de272-116">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="de272-116">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
