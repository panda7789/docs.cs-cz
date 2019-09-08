---
title: 'Postupy: Dynamické vytvoření databáze'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb7f23c4-4572-4c38-9898-a287807d070c
ms.openlocfilehash: 4cadf20cdadb39483f26a29619cae058eac47e50
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793660"
---
# <a name="how-to-dynamically-create-a-database"></a><span data-ttu-id="ce829-102">Postupy: Dynamické vytvoření databáze</span><span class="sxs-lookup"><span data-stu-id="ce829-102">How to: Dynamically Create a Database</span></span>
<span data-ttu-id="ce829-103">V LINQ to SQL objektový model je namapován na relační databázi.</span><span class="sxs-lookup"><span data-stu-id="ce829-103">In LINQ to SQL, an object model is mapped to a relational database.</span></span> <span data-ttu-id="ce829-104">Mapování je povoleno pomocí mapování založeného na atributech nebo souboru externího mapování pro popis struktury relační databáze.</span><span class="sxs-lookup"><span data-stu-id="ce829-104">Mapping is enabled by using attribute-based mapping or an external mapping file to describe the structure of the relational database.</span></span> <span data-ttu-id="ce829-105">V obou scénářích je k dispozici dostatek informací o relační databázi, kterou můžete vytvořit novou instanci databáze pomocí <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="ce829-105">In both scenarios, there is enough information about the relational database that you can create a new instance of the database using the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="ce829-106"><xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> Metoda vytvoří repliku databáze pouze v rozsahu informací zakódovaných v objektovém modelu.</span><span class="sxs-lookup"><span data-stu-id="ce829-106">The <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method creates a replica of the database only to the extent of the information encoded in the object model.</span></span> <span data-ttu-id="ce829-107">Mapování souborů a atributů z objektového modelu nemusí zakódovat vše o struktuře existující databáze.</span><span class="sxs-lookup"><span data-stu-id="ce829-107">Mapping files and attributes from your object model might not encode everything about the structure of an existing database.</span></span> <span data-ttu-id="ce829-108">Informace o mapování nepředstavuje obsah uživatelsky definovaných funkcí, uložených procedur, triggerů nebo omezení CHECK.</span><span class="sxs-lookup"><span data-stu-id="ce829-108">Mapping information does not represent the contents of user-defined functions, stored procedures, triggers, or check constraints.</span></span> <span data-ttu-id="ce829-109">Toto chování je dostatečné pro nejrůznější databáze.</span><span class="sxs-lookup"><span data-stu-id="ce829-109">This behavior is sufficient for a variety of databases.</span></span>  
  
 <span data-ttu-id="ce829-110"><xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> Metodu můžete použít v jakémkoli počtu scénářů, zejména pokud je k dispozici známý poskytovatel dat, jako je Microsoft SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="ce829-110">You can use the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method in any number of scenarios, especially if a known data provider like Microsoft SQL Server 2008 is available.</span></span> <span data-ttu-id="ce829-111">Mezi typické scénáře patří následující:</span><span class="sxs-lookup"><span data-stu-id="ce829-111">Typical scenarios include the following:</span></span>  
  
- <span data-ttu-id="ce829-112">Vytváříte aplikaci, která se automaticky nainstaluje do zákaznického systému.</span><span class="sxs-lookup"><span data-stu-id="ce829-112">You are building an application that automatically installs itself on a customer system.</span></span>  
  
- <span data-ttu-id="ce829-113">Vytváříte klientskou aplikaci, která potřebuje místní databázi pro uložení stavu offline.</span><span class="sxs-lookup"><span data-stu-id="ce829-113">You are building a client application that needs a local database to save its offline state.</span></span>  
  
 <span data-ttu-id="ce829-114"><xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> Metodu můžete také použít s SQL Server pomocí souboru. MDF nebo názvu katalogu v závislosti na vašem připojovacím řetězci.</span><span class="sxs-lookup"><span data-stu-id="ce829-114">You can also use the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method with SQL Server by using an .mdf file or a catalog name, depending on your connection string.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="ce829-115">pomocí připojovacího řetězce definuje databázi, která se má vytvořit, a na kterých serveru se databáze má vytvořit.</span><span class="sxs-lookup"><span data-stu-id="ce829-115">uses the connection string to define the database to be created and on which server the database is to be created.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ce829-116">Kdykoli je to možné, použijte integrované zabezpečení systému Windows pro připojení k databázi, aby se v připojovacím řetězci nevyžadovala hesla.</span><span class="sxs-lookup"><span data-stu-id="ce829-116">Whenever possible, use Windows Integrated Security to connect to the database so that passwords are not required in the connection string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce829-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="ce829-117">Example</span></span>  
 <span data-ttu-id="ce829-118">Následující kód poskytuje příklad vytvoření nové databáze s názvem MyDVDs. mdf.</span><span class="sxs-lookup"><span data-stu-id="ce829-118">The following code provides an example of how to create a new database named MyDVDs.mdf.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#5)]
 [!code-vb[DLinqSubmittingChanges#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="ce829-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="ce829-119">Example</span></span>  
 <span data-ttu-id="ce829-120">Objektový model můžete použít k vytvoření databáze pomocí následujícího postupu:</span><span class="sxs-lookup"><span data-stu-id="ce829-120">You can use the object model to create a database by doing the following:</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#6)]
 [!code-vb[DLinqSubmittingChanges#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="ce829-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="ce829-121">Example</span></span>  
 <span data-ttu-id="ce829-122">Při sestavování aplikace, která se automaticky nainstaluje do systému zákazníka, si přečtěte téma, jestli databáze už existuje, a vyřaďte ji ještě předtím, než vytvoříte novou.</span><span class="sxs-lookup"><span data-stu-id="ce829-122">When building an application that automatically installs itself on a  customer system, see if the database already exists and drop it before creating a new one.</span></span> <span data-ttu-id="ce829-123">Třída poskytuje metody<xref:System.Data.Linq.DataContext.DeleteDatabase%2A> a, které vám pomůžou s tímto procesem. <xref:System.Data.Linq.DataContext.DatabaseExists%2A> <xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="ce829-123">The <xref:System.Data.Linq.DataContext> class provides the <xref:System.Data.Linq.DataContext.DatabaseExists%2A> and <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> methods to help you with this process.</span></span>  
  
 <span data-ttu-id="ce829-124">Následující příklad ukazuje jeden ze způsobů, jak lze tyto metody použít k implementaci tohoto přístupu:</span><span class="sxs-lookup"><span data-stu-id="ce829-124">The following example shows one way these methods can be used to implement this approach:</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#7)]
 [!code-vb[DLinqSubmittingChanges#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="ce829-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ce829-125">See also</span></span>

- [<span data-ttu-id="ce829-126">Mapování na základě atributů</span><span class="sxs-lookup"><span data-stu-id="ce829-126">Attribute-Based Mapping</span></span>](attribute-based-mapping.md)
- [<span data-ttu-id="ce829-127">Externí mapování</span><span class="sxs-lookup"><span data-stu-id="ce829-127">External Mapping</span></span>](external-mapping.md)
- [<span data-ttu-id="ce829-128">Mapování typů SQL a CLR</span><span class="sxs-lookup"><span data-stu-id="ce829-128">SQL-CLR Type Mapping</span></span>](sql-clr-type-mapping.md)
- [<span data-ttu-id="ce829-129">Základní informace</span><span class="sxs-lookup"><span data-stu-id="ce829-129">Background Information</span></span>](background-information.md)
- [<span data-ttu-id="ce829-130">Vytvoření a odeslání změn dat</span><span class="sxs-lookup"><span data-stu-id="ce829-130">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
