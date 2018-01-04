---
title: "Binární a velké hodnoty dat systému SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 015003becc47910b875629f021a9e196ba8445f3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="sql-server-binary-and-large-value-data"></a><span data-ttu-id="6c192-102">Binární a velké hodnoty dat systému SQL Server</span><span class="sxs-lookup"><span data-stu-id="6c192-102">SQL Server Binary and Large-Value Data</span></span>
<span data-ttu-id="6c192-103">SQL Server poskytuje `max` specifikátor, který rozbalí úložnou kapacitu `varchar`, `nvarchar`, a `varbinary` datové typy.</span><span class="sxs-lookup"><span data-stu-id="6c192-103">SQL Server provides the `max` specifier, which expands the storage capacity of the `varchar`, `nvarchar`, and `varbinary` data types.</span></span> <span data-ttu-id="6c192-104">`varchar(max)`, `nvarchar(max)`, a `varbinary(max)` se souhrnně označují jako *velké hodnoty datové typy*.</span><span class="sxs-lookup"><span data-stu-id="6c192-104">`varchar(max)`, `nvarchar(max)`, and `varbinary(max)` are collectively called *large-value data types*.</span></span> <span data-ttu-id="6c192-105">Typy dat velké hodnoty můžete použít k uložení až 2 ^ 31-1 bajtů dat.</span><span class="sxs-lookup"><span data-stu-id="6c192-105">You can use the large-value data types to store up to 2^31-1 bytes of data.</span></span>  
  
 <span data-ttu-id="6c192-106">SQL Server 2008 zavádí FILESTREAM atribut, který není typu data, ale spíš atribut, který může být definováno na sloupci, což velké hodnoty data k uložení v systému souborů místo v databázi.</span><span class="sxs-lookup"><span data-stu-id="6c192-106">SQL Server 2008 introduces the FILESTREAM attribute, which is not a data type, but rather an attribute that can be defined on a column, allowing large-value data to be stored on the file system instead of in the database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6c192-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="6c192-107">In This Section</span></span>  
 [<span data-ttu-id="6c192-108">Úprava vysokých (maximálních) hodnot v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6c192-108">Modifying Large-Value (max) Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/modifying-large-value-max-data.md)  
 <span data-ttu-id="6c192-109">Popisuje, jak pracovat s typy dat velké hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6c192-109">Describes how to work with the large-value data types.</span></span>  
  
 [<span data-ttu-id="6c192-110">Data FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="6c192-110">FILESTREAM Data</span></span>](../../../../../docs/framework/data/adonet/sql/filestream-data.md)  
 <span data-ttu-id="6c192-111">Popisuje, jak pracovat s daty velké hodnoty, které jsou uložené v systému SQL Server 2008 s atributem FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="6c192-111">Describes how to work with large-value data stored in SQL Server 2008 with the FILESTREAM attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c192-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="6c192-112">See Also</span></span>  
 [<span data-ttu-id="6c192-113">Datové typy SQL Serveru a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6c192-113">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [<span data-ttu-id="6c192-114">Operace dat na SQL Serveru v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6c192-114">SQL Server Data Operations in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 [<span data-ttu-id="6c192-115">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6c192-115">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="6c192-116">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="6c192-116">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
