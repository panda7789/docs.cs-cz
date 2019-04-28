---
title: Práce s jazykem DDL (Data Description Language)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec50083d-44f4-4093-9b23-5eacd601f96e
ms.openlocfilehash: 75a214ad1099bf48dcb2c2d3b36bf07dc0524f8d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763916"
---
# <a name="working-with-data-definition-language"></a><span data-ttu-id="11119-102">Práce s jazykem DDL (Data Description Language)</span><span class="sxs-lookup"><span data-stu-id="11119-102">Working with Data Definition Language</span></span>
<span data-ttu-id="11119-103">Počínaje [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] verze 4, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] podporuje jazyk pro definování dat (DDL).</span><span class="sxs-lookup"><span data-stu-id="11119-103">Starting with the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] version 4, the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] supports data definition language (DDL).</span></span> <span data-ttu-id="11119-104">To umožňuje vytvořit nebo odstranit instanci databáze na základě připojovacího řetězce a metadata modelu úložiště (SSDL).</span><span class="sxs-lookup"><span data-stu-id="11119-104">This allows you to create or delete a database instance based on the connection string and the metadata of the storage (SSDL) model.</span></span>  
  
 <span data-ttu-id="11119-105">Následující metody u <xref:System.Data.Objects.ObjectContext> můžete provádět následující připojovací řetězec a obsah souborů SSDL: vytvoření nebo odstranění databáze, zkontrolujte, jestli databáze existuje a zobrazit vygenerovaný skript jazyka DDL:</span><span class="sxs-lookup"><span data-stu-id="11119-105">The following methods on the <xref:System.Data.Objects.ObjectContext> use the connection string and the SSDL content to accomplish the following: create or delete the database, check whether the database exists, and view the generated DDL script:</span></span>  
  
- <xref:System.Data.Objects.ObjectContext.CreateDatabase%2A>  
  
- <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A>  
  
- <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A>  
  
- <xref:System.Data.Objects.ObjectContext.CreateDatabaseScript%2A>  
  
> [!NOTE]
>  <span data-ttu-id="11119-106">Provádění příkazů DDL předpokládá dostatečná oprávnění.</span><span class="sxs-lookup"><span data-stu-id="11119-106">Executing the DDL commands assumes sufficient permissions.</span></span>  
  
 <span data-ttu-id="11119-107">Výše uvedených metod delegáta většinu práce, kterou podkladového zprostředkovatele dat ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="11119-107">The methods previously listed delegate most of the work to the underlying ADO.NET data provider.</span></span> <span data-ttu-id="11119-108">Je poskytovatele povinností ujistit se, že zásady vytváření názvů sloužící ke generování databázové objekty je v souladu s konvencemi použitými pro dotazování a aktualizace.</span><span class="sxs-lookup"><span data-stu-id="11119-108">It is the provider’s responsibility to ensure that the naming convention used to generate database objects is consistent with conventions used for querying and updates.</span></span>  
  
 <span data-ttu-id="11119-109">Následující příklad ukazuje, jak vytvořit databázi na základě existující modelu.</span><span class="sxs-lookup"><span data-stu-id="11119-109">The following example shows you how to generate the database based on the existing model.</span></span> <span data-ttu-id="11119-110">Také přidá nový objekt entity v kontextu objektu a uloží jej do databáze.</span><span class="sxs-lookup"><span data-stu-id="11119-110">It also adds a new entity object to the object context and then saves it to the database.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="11119-111">Procedury</span><span class="sxs-lookup"><span data-stu-id="11119-111">Procedures</span></span>  
  
#### <a name="to-define-a-database-based-on-the-existing-model"></a><span data-ttu-id="11119-112">Chcete-li definovat databáze založené na existující model</span><span class="sxs-lookup"><span data-stu-id="11119-112">To define a database based on the existing model</span></span>  
  
1. <span data-ttu-id="11119-113">Vytvořte konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="11119-113">Create a console application.</span></span>  
  
2. <span data-ttu-id="11119-114">Přidáte existující model pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="11119-114">Add an existing model to your application.</span></span>  
  
    1. <span data-ttu-id="11119-115">Přidat prázdný model s názvem `SchoolModel`.</span><span class="sxs-lookup"><span data-stu-id="11119-115">Add an empty model named `SchoolModel`.</span></span> <span data-ttu-id="11119-116">Chcete-li vytvořit prázdný model, najdete v článku [jak: Vytvořit nový edmx soubor](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100)) tématu.</span><span class="sxs-lookup"><span data-stu-id="11119-116">To create an empty model, see the [How to: Create a New .edmx File](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100)) topic.</span></span>  
  
     <span data-ttu-id="11119-117">Soubor SchoolModel.edmx je přidán do projektu.</span><span class="sxs-lookup"><span data-stu-id="11119-117">The SchoolModel.edmx file is added to your project.</span></span>  
  
    1. <span data-ttu-id="11119-118">Zkopírujte koncepční, úložiště a mapování obsahu pro model školní ze [školní modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) tématu.</span><span class="sxs-lookup"><span data-stu-id="11119-118">Copy the conceptual, storage, and mapping content for the School model from the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) topic.</span></span>  
  
    2. <span data-ttu-id="11119-119">Otevřete soubor SchoolModel.edmx a vložte obsah v rámci `edmx:Runtime` značky.</span><span class="sxs-lookup"><span data-stu-id="11119-119">Open the SchoolModel.edmx file and paste the content within the `edmx:Runtime` tags.</span></span>  
  
3. <span data-ttu-id="11119-120">Přidejte následující kód do hlavní funkce.</span><span class="sxs-lookup"><span data-stu-id="11119-120">Add the following code to your main function.</span></span> <span data-ttu-id="11119-121">Kód inicializuje řetězec připojení k vašemu databázovému serveru, zobrazení skriptu jazyka DDL, vytvoří databázi, přidá nové entity v kontextu a uloží změny do databáze.</span><span class="sxs-lookup"><span data-stu-id="11119-121">The code initializes the connection string to your database server, views the DDL script, creates the database, adds a new entity to the context, and saves the changes to the database.</span></span>  
  
     [!code-csharp[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/csharp/VS_Snippets_Data/DP ObjectServices Concepts/CS/Source.cs#ddl)]
     [!code-vb[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP ObjectServices Concepts/VB/Source.vb#ddl)]
