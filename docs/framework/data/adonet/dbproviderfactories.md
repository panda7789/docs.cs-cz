---
title: DbProviderFactories
ms.date: 03/30/2017
ms.assetid: 2a8e2640-3a49-42a1-a3a9-b43026907ae1
ms.openlocfilehash: e3ea9e3d083314f8df25f9edadbd1a18f1227293
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784099"
---
# <a name="dbproviderfactories"></a><span data-ttu-id="f3c2b-102">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="f3c2b-102">DbProviderFactories</span></span>
<span data-ttu-id="f3c2b-103">Obor názvů poskytuje třídy pro vytváření <xref:System.Data.Common.DbProviderFactory> instancí pro práci s konkrétními zdroji dat. <xref:System.Data.Common></span><span class="sxs-lookup"><span data-stu-id="f3c2b-103">The <xref:System.Data.Common> namespace provides classes for creating <xref:System.Data.Common.DbProviderFactory> instances to work with specific data sources.</span></span> <span data-ttu-id="f3c2b-104">Když vytvoříte <xref:System.Data.Common.DbProviderFactory> instanci a předáte informace o poskytovateli dat `DbProviderFactory` , může určit správný objekt připojení silného typu, který se bude vracet na základě informací, které byly poskytnuty.</span><span class="sxs-lookup"><span data-stu-id="f3c2b-104">When you create a <xref:System.Data.Common.DbProviderFactory> instance and pass it information about the data provider, the `DbProviderFactory` can determine the correct, strongly typed connection object to return based on the information it has been provided.</span></span>  
  
 <span data-ttu-id="f3c2b-105">Od .NET Framework verze 4 nejsou <xref:System.Data.Odbc>poskytovatelé dat <xref:System.Data.SqlClient>, jako jsou, <xref:System.Data.OleDb>, a <xref:System.Data.OracleClient> , již v souboru Machine. config uvedeny, ale vlastní zprostředkovatelé budou dále uvedeni v seznamu.</span><span class="sxs-lookup"><span data-stu-id="f3c2b-105">Beginning in the .NET Framework version 4, data providers such as <xref:System.Data.Odbc>, <xref:System.Data.OleDb>, <xref:System.Data.SqlClient>, and <xref:System.Data.OracleClient> are no longer listed in machine.config file, but custom providers will continue to be listed there.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f3c2b-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="f3c2b-106">In This Section</span></span>  
 [<span data-ttu-id="f3c2b-107">Přehled modelu objektu pro vytváření</span><span class="sxs-lookup"><span data-stu-id="f3c2b-107">Factory Model Overview</span></span>](factory-model-overview.md)  
 <span data-ttu-id="f3c2b-108">Poskytuje přehled vzoru návrhu a programovacího rozhraní pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="f3c2b-108">Provides an overview of the factory design pattern and programming interface.</span></span>  
  
 [<span data-ttu-id="f3c2b-109">Získání DbProviderFactory</span><span class="sxs-lookup"><span data-stu-id="f3c2b-109">Obtaining a DbProviderFactory</span></span>](obtaining-a-dbproviderfactory.md)  
 <span data-ttu-id="f3c2b-110">Ukazuje, jak zobrazit seznam nainstalovaných zprostředkovatelů dat a <xref:System.Data.Common.DbConnection> vytvořit `DbProviderFactory`z.</span><span class="sxs-lookup"><span data-stu-id="f3c2b-110">Demonstrates how to list the installed data providers and create a <xref:System.Data.Common.DbConnection> from a `DbProviderFactory`.</span></span>  
  
 [<span data-ttu-id="f3c2b-111">DbConnection, DbCommand a DbException</span><span class="sxs-lookup"><span data-stu-id="f3c2b-111">DbConnection, DbCommand and DbException</span></span>](dbconnection-dbcommand-and-dbexception.md)  
 <span data-ttu-id="f3c2b-112">Ukazuje, jak vytvořit <xref:System.Data.Common.DbCommand> a a <xref:System.Data.Common.DbDataReader>jak zpracovávat chyby dat pomocí. <xref:System.Data.Common.DbException></span><span class="sxs-lookup"><span data-stu-id="f3c2b-112">Demonstrates how to create a <xref:System.Data.Common.DbCommand> and <xref:System.Data.Common.DbDataReader>, and how to handle data errors using <xref:System.Data.Common.DbException>.</span></span>  
  
 [<span data-ttu-id="f3c2b-113">Úpravy dat přes DbDataAdapter</span><span class="sxs-lookup"><span data-stu-id="f3c2b-113">Modifying Data with a DbDataAdapter</span></span>](modifying-data-with-a-dbdataadapter.md)  
 <span data-ttu-id="f3c2b-114">Ukazuje, jak použít <xref:System.Data.Common.DbCommandBuilder> <xref:System.Data.Common.DbDataAdapter> s a k načtení a úpravě dat.</span><span class="sxs-lookup"><span data-stu-id="f3c2b-114">Demonstrates how to use a <xref:System.Data.Common.DbCommandBuilder> with a <xref:System.Data.Common.DbDataAdapter> to retrieve and modify data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3c2b-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f3c2b-115">See also</span></span>

- [<span data-ttu-id="f3c2b-116">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f3c2b-116">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="f3c2b-117">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f3c2b-117">ADO.NET Overview</span></span>](ado-net-overview.md)
