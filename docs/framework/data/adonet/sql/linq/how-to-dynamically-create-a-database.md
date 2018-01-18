---
title: "Postupy: vytvoření dynamicky databáze"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: fb7f23c4-4572-4c38-9898-a287807d070c
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f92d34276855a7b7473dd15dd3828c4ea91c64d1
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-dynamically-create-a-database"></a><span data-ttu-id="1bfce-102">Postupy: vytvoření dynamicky databáze</span><span class="sxs-lookup"><span data-stu-id="1bfce-102">How to: Dynamically Create a Database</span></span>
<span data-ttu-id="1bfce-103">V technologii LINQ to SQL objektový model je namapována na relační databázi.</span><span class="sxs-lookup"><span data-stu-id="1bfce-103">In LINQ to SQL, an object model is mapped to a relational database.</span></span> <span data-ttu-id="1bfce-104">Mapování je povolený pomocí mapování na základě atributů nebo soubor externí mapování k popisu struktury relační databáze.</span><span class="sxs-lookup"><span data-stu-id="1bfce-104">Mapping is enabled by using attribute-based mapping or an external mapping file to describe the structure of the relational database.</span></span> <span data-ttu-id="1bfce-105">V obou případech je dostatek informací o relační databázi, můžete vytvořit novou instanci databáze pomocí <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="1bfce-105">In both scenarios, there is enough information about the relational database that you can create a new instance of the database using the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="1bfce-106"><xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> Metoda vytváří repliku databáze rozsah informace kódovaný v objektovém modelu.</span><span class="sxs-lookup"><span data-stu-id="1bfce-106">The <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method creates a replica of the database only to the extent of the information encoded in the object model.</span></span> <span data-ttu-id="1bfce-107">Mapování soubory a atributy z modelu objektu nemusí zakódovat všechno, co o struktuře existující databázi.</span><span class="sxs-lookup"><span data-stu-id="1bfce-107">Mapping files and attributes from your object model might not encode everything about the structure of an existing database.</span></span> <span data-ttu-id="1bfce-108">Informace o mapování nemá představují obsah uživatelsky definované funkce, uložené procedury, triggery, nebo omezení check.</span><span class="sxs-lookup"><span data-stu-id="1bfce-108">Mapping information does not represent the contents of user-defined functions, stored procedures, triggers, or check constraints.</span></span> <span data-ttu-id="1bfce-109">Toto chování je dostatečné pro různé databáze.</span><span class="sxs-lookup"><span data-stu-id="1bfce-109">This behavior is sufficient for a variety of databases.</span></span>  
  
 <span data-ttu-id="1bfce-110">Můžete použít <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metoda v libovolný počet scénářů, hlavně pokud zprostředkovatele dat známé jako je Microsoft SQL Server 2008 je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="1bfce-110">You can use the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method in any number of scenarios, especially if a known data provider like Microsoft SQL Server 2008 is available.</span></span> <span data-ttu-id="1bfce-111">Typické scénáře patří:</span><span class="sxs-lookup"><span data-stu-id="1bfce-111">Typical scenarios include the following:</span></span>  
  
-   <span data-ttu-id="1bfce-112">Vytváříte aplikaci, která automaticky nainstaluje systému zákazníka.</span><span class="sxs-lookup"><span data-stu-id="1bfce-112">You are building an application that automatically installs itself on a customer system.</span></span>  
  
-   <span data-ttu-id="1bfce-113">Vytváříte klientská aplikace vyžadující místní databáze pro uložení stavu offline.</span><span class="sxs-lookup"><span data-stu-id="1bfce-113">You are building a client application that needs a local database to save its offline state.</span></span>  
  
 <span data-ttu-id="1bfce-114">Můžete také <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metoda s SQL serverem pomocí souboru .mdf nebo název katalogu, v závislosti na připojovací řetězec.</span><span class="sxs-lookup"><span data-stu-id="1bfce-114">You can also use the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method with SQL Server by using an .mdf file or a catalog name, depending on your connection string.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="1bfce-115">používá připojovací řetězec k definování databáze, který se má vytvořit a na serveru, který má být vytvořen databáze.</span><span class="sxs-lookup"><span data-stu-id="1bfce-115"> uses the connection string to define the database to be created and on which server the database is to be created.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1bfce-116">Kdykoli je to možné, použijte integrované zabezpečení systému Windows pro připojení k databázi tak, aby hesla nejsou potřebné v připojovacím řetězci.</span><span class="sxs-lookup"><span data-stu-id="1bfce-116">Whenever possible, use Windows Integrated Security to connect to the database so that passwords are not required in the connection string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bfce-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="1bfce-117">Example</span></span>  
 <span data-ttu-id="1bfce-118">Následující kód představuje příklad, jak vytvořit novou databázi s názvem MyDVDs.mdf.</span><span class="sxs-lookup"><span data-stu-id="1bfce-118">The following code provides an example of how to create a new database named MyDVDs.mdf.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#5)]
 [!code-vb[DLinqSubmittingChanges#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="1bfce-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="1bfce-119">Example</span></span>  
 <span data-ttu-id="1bfce-120">K vytvoření databáze pomocí následujícího postupu můžete v objektovém modelu:</span><span class="sxs-lookup"><span data-stu-id="1bfce-120">You can use the object model to create a database by doing the following:</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#6)]
 [!code-vb[DLinqSubmittingChanges#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="1bfce-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="1bfce-121">Example</span></span>  
 <span data-ttu-id="1bfce-122">Při vytváření aplikace, který automaticky nainstaluje sám systému zákazníka, najdete v části Pokud databázi již existuje a umístěte jej před vytvořením nového.</span><span class="sxs-lookup"><span data-stu-id="1bfce-122">When building an application that automatically installs itself on a  customer system, see if the database already exists and drop it before creating a new one.</span></span> <span data-ttu-id="1bfce-123"><xref:System.Data.Linq.DataContext> Třída poskytuje <xref:System.Data.Linq.DataContext.DatabaseExists%2A> a <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> metody, které vám pomohou s tímto procesem.</span><span class="sxs-lookup"><span data-stu-id="1bfce-123">The <xref:System.Data.Linq.DataContext> class provides the <xref:System.Data.Linq.DataContext.DatabaseExists%2A> and <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> methods to help you with this process.</span></span>  
  
 <span data-ttu-id="1bfce-124">Následující příklad ukazuje jeden ze způsobů, které tyto metody lze použít k implementaci tohoto přístupu:</span><span class="sxs-lookup"><span data-stu-id="1bfce-124">The following example shows one way these methods can be used to implement this approach:</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#7)]
 [!code-vb[DLinqSubmittingChanges#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="1bfce-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="1bfce-125">See Also</span></span>  
 [<span data-ttu-id="1bfce-126">Mapování na základě atributů</span><span class="sxs-lookup"><span data-stu-id="1bfce-126">Attribute-Based Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)  
 [<span data-ttu-id="1bfce-127">Externí mapování</span><span class="sxs-lookup"><span data-stu-id="1bfce-127">External Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)  
 [<span data-ttu-id="1bfce-128">Mapování typů SQL a CLR</span><span class="sxs-lookup"><span data-stu-id="1bfce-128">SQL-CLR Type Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)  
 [<span data-ttu-id="1bfce-129">Základní informace</span><span class="sxs-lookup"><span data-stu-id="1bfce-129">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [<span data-ttu-id="1bfce-130">Vytvoření a odeslání změn dat</span><span class="sxs-lookup"><span data-stu-id="1bfce-130">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
