---
title: Binární a vysoké hodnoty dat serveru SQL Server
ms.date: 03/30/2017
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.openlocfilehash: 9ebbe23dfbcac7825ce449dd40f62b921d13ab4a
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/16/2018
ms.locfileid: "45683268"
---
# <a name="sql-server-binary-and-large-value-data"></a><span data-ttu-id="b315e-102">Binární a vysoké hodnoty dat serveru SQL Server</span><span class="sxs-lookup"><span data-stu-id="b315e-102">SQL Server Binary and Large-Value Data</span></span>
<span data-ttu-id="b315e-103">SQL Server poskytuje `max` specifikátor, který rozbalí úložnou kapacitu `varchar`, `nvarchar`, a `varbinary` datové typy.</span><span class="sxs-lookup"><span data-stu-id="b315e-103">SQL Server provides the `max` specifier, which expands the storage capacity of the `varchar`, `nvarchar`, and `varbinary` data types.</span></span> <span data-ttu-id="b315e-104">`varchar(max)`, `nvarchar(max)`, a `varbinary(max)` se společně nazývají *velké hodnoty datových typů*.</span><span class="sxs-lookup"><span data-stu-id="b315e-104">`varchar(max)`, `nvarchar(max)`, and `varbinary(max)` are collectively called *large-value data types*.</span></span> <span data-ttu-id="b315e-105">Velké hodnoty datové typy, které můžete použít k uložení až 2 ^ 31-1 bajtů.</span><span class="sxs-lookup"><span data-stu-id="b315e-105">You can use the large-value data types to store up to 2^31-1 bytes of data.</span></span>  
  
 <span data-ttu-id="b315e-106">SQL Server 2008 představuje atribut FILESTREAM, což není typ dat, ale místo toho atribut, který může být definovaný na sloupci, dat. velké hodnoty uložené v systému souborů namísto v databázi.</span><span class="sxs-lookup"><span data-stu-id="b315e-106">SQL Server 2008 introduces the FILESTREAM attribute, which is not a data type, but rather an attribute that can be defined on a column, allowing large-value data to be stored on the file system instead of in the database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b315e-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b315e-107">In This Section</span></span>  
 [<span data-ttu-id="b315e-108">Úprava vysokých (maximálních) hodnot v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b315e-108">Modifying Large-Value (max) Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/modifying-large-value-max-data.md)  
 <span data-ttu-id="b315e-109">Popisuje způsob práce s typy dat vysoké hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b315e-109">Describes how to work with the large-value data types.</span></span>  
  
 [<span data-ttu-id="b315e-110">Data FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="b315e-110">FILESTREAM Data</span></span>](../../../../../docs/framework/data/adonet/sql/filestream-data.md)  
 <span data-ttu-id="b315e-111">Popisuje, jak pracovat s daty velké hodnoty uložené v systému SQL Server 2008 s atributem FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="b315e-111">Describes how to work with large-value data stored in SQL Server 2008 with the FILESTREAM attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b315e-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="b315e-112">See Also</span></span>  
 [<span data-ttu-id="b315e-113">Datové typy SQL Serveru a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b315e-113">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [<span data-ttu-id="b315e-114">Operace dat na SQL Serveru v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b315e-114">SQL Server Data Operations in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 [<span data-ttu-id="b315e-115">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b315e-115">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="b315e-116">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="b315e-116">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
