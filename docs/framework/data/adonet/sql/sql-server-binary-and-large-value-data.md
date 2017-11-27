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
ms.openlocfilehash: 9065f467cd353c17471db2c0d67001a188459819
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="sql-server-binary-and-large-value-data"></a><span data-ttu-id="b7f4c-102">Binární a velké hodnoty dat systému SQL Server</span><span class="sxs-lookup"><span data-stu-id="b7f4c-102">SQL Server Binary and Large-Value Data</span></span>
<span data-ttu-id="b7f4c-103">SQL Server poskytuje `max` specifikátor, který rozbalí úložnou kapacitu `varchar`, `nvarchar`, a `varbinary` datové typy.</span><span class="sxs-lookup"><span data-stu-id="b7f4c-103">SQL Server provides the `max` specifier, which expands the storage capacity of the `varchar`, `nvarchar`, and `varbinary` data types.</span></span> <span data-ttu-id="b7f4c-104">`varchar(max)`, `nvarchar(max)`, a `varbinary(max)` se souhrnně označují jako *velké hodnoty datové typy*.</span><span class="sxs-lookup"><span data-stu-id="b7f4c-104">`varchar(max)`, `nvarchar(max)`, and `varbinary(max)` are collectively called *large-value data types*.</span></span> <span data-ttu-id="b7f4c-105">Typy dat velké hodnoty můžete použít k uložení až 2 ^ 31-1 bajtů dat.</span><span class="sxs-lookup"><span data-stu-id="b7f4c-105">You can use the large-value data types to store up to 2^31-1 bytes of data.</span></span>  
  
 <span data-ttu-id="b7f4c-106">SQL Server 2008 zavádí FILESTREAM atribut, který není typu data, ale spíš atribut, který může být definováno na sloupci, což velké hodnoty data k uložení v systému souborů místo v databázi.</span><span class="sxs-lookup"><span data-stu-id="b7f4c-106">SQL Server 2008 introduces the FILESTREAM attribute, which is not a data type, but rather an attribute that can be defined on a column, allowing large-value data to be stored on the file system instead of in the database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b7f4c-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b7f4c-107">In This Section</span></span>  
 [<span data-ttu-id="b7f4c-108">Úprava dat (max) velké hodnoty v technologii ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b7f4c-108">Modifying Large-Value (max) Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/modifying-large-value-max-data.md)  
 <span data-ttu-id="b7f4c-109">Popisuje, jak pracovat s typy dat velké hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b7f4c-109">Describes how to work with the large-value data types.</span></span>  
  
 [<span data-ttu-id="b7f4c-110">FILESTREAM Data</span><span class="sxs-lookup"><span data-stu-id="b7f4c-110">FILESTREAM Data</span></span>](../../../../../docs/framework/data/adonet/sql/filestream-data.md)  
 <span data-ttu-id="b7f4c-111">Popisuje, jak pracovat s daty velké hodnoty, které jsou uložené v systému SQL Server 2008 s atributem FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="b7f4c-111">Describes how to work with large-value data stored in SQL Server 2008 with the FILESTREAM attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7f4c-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="b7f4c-112">See Also</span></span>  
 [<span data-ttu-id="b7f4c-113">Data serveru SQL typy a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b7f4c-113">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [<span data-ttu-id="b7f4c-114">Operace dat serveru SQL v technologii ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b7f4c-114">SQL Server Data Operations in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 [<span data-ttu-id="b7f4c-115">Načítání a upravovat Data v technologii ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b7f4c-115">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="b7f4c-116">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="b7f4c-116">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
