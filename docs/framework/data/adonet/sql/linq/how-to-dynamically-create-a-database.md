---
title: 'Postupy: Dynamické vytvoření databáze'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb7f23c4-4572-4c38-9898-a287807d070c
ms.openlocfilehash: a73efb334fddc7e0bbfbaca53f0d5026105dd22c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597031"
---
# <a name="how-to-dynamically-create-a-database"></a><span data-ttu-id="2aa66-102">Postupy: Dynamické vytvoření databáze</span><span class="sxs-lookup"><span data-stu-id="2aa66-102">How to: Dynamically Create a Database</span></span>
<span data-ttu-id="2aa66-103">V technologii LINQ to SQL objektový model je namapována na relační databáze.</span><span class="sxs-lookup"><span data-stu-id="2aa66-103">In LINQ to SQL, an object model is mapped to a relational database.</span></span> <span data-ttu-id="2aa66-104">Mapování je povolit pomocí podle atributů mapování nebo souboru externí mapování k popisu struktury relační databáze.</span><span class="sxs-lookup"><span data-stu-id="2aa66-104">Mapping is enabled by using attribute-based mapping or an external mapping file to describe the structure of the relational database.</span></span> <span data-ttu-id="2aa66-105">V obou případech je dostatek informací o relační databázi, můžete vytvořit novou instanci používat databázi <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="2aa66-105">In both scenarios, there is enough information about the relational database that you can create a new instance of the database using the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="2aa66-106"><xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> Metoda vytvoří replika databáze rozsah informace kódovaný v objektovém modelu.</span><span class="sxs-lookup"><span data-stu-id="2aa66-106">The <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method creates a replica of the database only to the extent of the information encoded in the object model.</span></span> <span data-ttu-id="2aa66-107">Mapování souborů a atributy z objektového modelu nemusí kódování všechno o struktuře existující databázi.</span><span class="sxs-lookup"><span data-stu-id="2aa66-107">Mapping files and attributes from your object model might not encode everything about the structure of an existing database.</span></span> <span data-ttu-id="2aa66-108">Informace o mapování neobsahuje představují obsah uživatelsky definovaných funkcí, uložené procedury, triggery, nebo kontrola omezení.</span><span class="sxs-lookup"><span data-stu-id="2aa66-108">Mapping information does not represent the contents of user-defined functions, stored procedures, triggers, or check constraints.</span></span> <span data-ttu-id="2aa66-109">Toto chování je dostatečná pro širokou škálu databází.</span><span class="sxs-lookup"><span data-stu-id="2aa66-109">This behavior is sufficient for a variety of databases.</span></span>  
  
 <span data-ttu-id="2aa66-110">Můžete použít <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metoda v jakémkoli počtu scénářů, zejména v případě, že zprostředkovatel známé dat, jako je Microsoft SQL Server 2008 je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="2aa66-110">You can use the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method in any number of scenarios, especially if a known data provider like Microsoft SQL Server 2008 is available.</span></span> <span data-ttu-id="2aa66-111">Typické scénáře zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="2aa66-111">Typical scenarios include the following:</span></span>  
  
-   <span data-ttu-id="2aa66-112">Vytváříte aplikaci, která se automaticky nainstaluje na systému zákazníky.</span><span class="sxs-lookup"><span data-stu-id="2aa66-112">You are building an application that automatically installs itself on a customer system.</span></span>  
  
-   <span data-ttu-id="2aa66-113">Sestavujete klientské aplikace, která potřebuje místní databáze pro uložení stavu offline.</span><span class="sxs-lookup"><span data-stu-id="2aa66-113">You are building a client application that needs a local database to save its offline state.</span></span>  
  
 <span data-ttu-id="2aa66-114">Můžete také použít <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metoda s SQL serverem pomocí souboru .mdf nebo název katalogu, v závislosti na tom, aby váš připojovací řetězec.</span><span class="sxs-lookup"><span data-stu-id="2aa66-114">You can also use the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method with SQL Server by using an .mdf file or a catalog name, depending on your connection string.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="2aa66-115">použití připojovacího řetězce k definování databáze, kterou chcete vytvořit, a na serveru, který se má vytvořit databázi.</span><span class="sxs-lookup"><span data-stu-id="2aa66-115">uses the connection string to define the database to be created and on which server the database is to be created.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2aa66-116">Kdykoli je to možné, použijte integrované zabezpečení Windows pro připojení k databázi tak, aby hesla nejsou vyžadovány v připojovacím řetězci.</span><span class="sxs-lookup"><span data-stu-id="2aa66-116">Whenever possible, use Windows Integrated Security to connect to the database so that passwords are not required in the connection string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2aa66-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="2aa66-117">Example</span></span>  
 <span data-ttu-id="2aa66-118">Následující kód obsahuje příklad toho, jak vytvořit novou databázi s názvem MyDVDs.mdf.</span><span class="sxs-lookup"><span data-stu-id="2aa66-118">The following code provides an example of how to create a new database named MyDVDs.mdf.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#5)]
 [!code-vb[DLinqSubmittingChanges#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="2aa66-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="2aa66-119">Example</span></span>  
 <span data-ttu-id="2aa66-120">Objektový model můžete použít k vytvoření databáze následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="2aa66-120">You can use the object model to create a database by doing the following:</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#6)]
 [!code-vb[DLinqSubmittingChanges#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="2aa66-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="2aa66-121">Example</span></span>  
 <span data-ttu-id="2aa66-122">Při vytváření aplikace, které automaticky nainstaluje sám systému zákazníků, najdete v článku Pokud databáze již existuje a umístěte jej před vytvořením nového.</span><span class="sxs-lookup"><span data-stu-id="2aa66-122">When building an application that automatically installs itself on a  customer system, see if the database already exists and drop it before creating a new one.</span></span> <span data-ttu-id="2aa66-123"><xref:System.Data.Linq.DataContext> Třída poskytuje <xref:System.Data.Linq.DataContext.DatabaseExists%2A> a <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> metody, které vám pomůžou se tento proces.</span><span class="sxs-lookup"><span data-stu-id="2aa66-123">The <xref:System.Data.Linq.DataContext> class provides the <xref:System.Data.Linq.DataContext.DatabaseExists%2A> and <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> methods to help you with this process.</span></span>  
  
 <span data-ttu-id="2aa66-124">Následující příklad ukazuje jeden způsob, jakým tyto metody slouží k implementaci tohoto přístupu:</span><span class="sxs-lookup"><span data-stu-id="2aa66-124">The following example shows one way these methods can be used to implement this approach:</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#7)]
 [!code-vb[DLinqSubmittingChanges#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="2aa66-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2aa66-125">See also</span></span>
- [<span data-ttu-id="2aa66-126">Mapování na základě atributů</span><span class="sxs-lookup"><span data-stu-id="2aa66-126">Attribute-Based Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)
- [<span data-ttu-id="2aa66-127">Externí mapování</span><span class="sxs-lookup"><span data-stu-id="2aa66-127">External Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)
- [<span data-ttu-id="2aa66-128">Mapování typů SQL a CLR</span><span class="sxs-lookup"><span data-stu-id="2aa66-128">SQL-CLR Type Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
- [<span data-ttu-id="2aa66-129">Základní informace</span><span class="sxs-lookup"><span data-stu-id="2aa66-129">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [<span data-ttu-id="2aa66-130">Vytvoření a odeslání změn dat</span><span class="sxs-lookup"><span data-stu-id="2aa66-130">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
