---
title: Binární a vysoké hodnoty na SQL Serveru
ms.date: 03/30/2017
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.openlocfilehash: 4d941ad6b7865112b45fd8c20ad89e9236e17b9d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791684"
---
# <a name="sql-server-binary-and-large-value-data"></a><span data-ttu-id="ba57a-102">Binární a vysoké hodnoty na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="ba57a-102">SQL Server Binary and Large-Value Data</span></span>
<span data-ttu-id="ba57a-103">SQL Server poskytuje `max` specifikátor, který rozšiřuje kapacitu `varchar`úložiště, `nvarchar`a `varbinary` datové typy.</span><span class="sxs-lookup"><span data-stu-id="ba57a-103">SQL Server provides the `max` specifier, which expands the storage capacity of the `varchar`, `nvarchar`, and `varbinary` data types.</span></span> <span data-ttu-id="ba57a-104">`varchar(max)`, `nvarchar(max)` a`varbinary(max)` jsou souhrnně označovány jako *datové typy velkých hodnot*.</span><span class="sxs-lookup"><span data-stu-id="ba57a-104">`varchar(max)`, `nvarchar(max)`, and `varbinary(max)` are collectively called *large-value data types*.</span></span> <span data-ttu-id="ba57a-105">Datové typy s velkými hodnotami můžete použít k ukládání až 2 ^ 31-1 bajtů dat.</span><span class="sxs-lookup"><span data-stu-id="ba57a-105">You can use the large-value data types to store up to 2^31-1 bytes of data.</span></span>  
  
 <span data-ttu-id="ba57a-106">SQL Server 2008 zavádí atribut FILESTREAM, který není datovým typem, ale spíše atribut, který může být definován ve sloupci a umožňuje uložení velkých hodnot do systému souborů místo do databáze.</span><span class="sxs-lookup"><span data-stu-id="ba57a-106">SQL Server 2008 introduces the FILESTREAM attribute, which is not a data type, but rather an attribute that can be defined on a column, allowing large-value data to be stored on the file system instead of in the database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ba57a-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="ba57a-107">In This Section</span></span>  
 [<span data-ttu-id="ba57a-108">Úprava vysokých (maximálních) hodnot v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ba57a-108">Modifying Large-Value (max) Data in ADO.NET</span></span>](modifying-large-value-max-data.md)  
 <span data-ttu-id="ba57a-109">Popisuje, jak pracovat s datovými typy s velkými hodnotami.</span><span class="sxs-lookup"><span data-stu-id="ba57a-109">Describes how to work with the large-value data types.</span></span>  
  
 [<span data-ttu-id="ba57a-110">Data FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="ba57a-110">FILESTREAM Data</span></span>](filestream-data.md)  
 <span data-ttu-id="ba57a-111">Popisuje, jak pracovat s daty ve velkých hodnotách, které jsou uloženy v SQL Server 2008 s atributem FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="ba57a-111">Describes how to work with large-value data stored in SQL Server 2008 with the FILESTREAM attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba57a-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ba57a-112">See also</span></span>

- [<span data-ttu-id="ba57a-113">Datové typy SQL Serveru a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ba57a-113">SQL Server Data Types and ADO.NET</span></span>](sql-server-data-types.md)
- [<span data-ttu-id="ba57a-114">Operace dat na SQL Serveru v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ba57a-114">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)
- [<span data-ttu-id="ba57a-115">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ba57a-115">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="ba57a-116">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ba57a-116">ADO.NET Overview</span></span>](../ado-net-overview.md)
