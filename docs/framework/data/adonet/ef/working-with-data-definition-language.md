---
title: Práce s jazykem DDL (Data Description Language)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec50083d-44f4-4093-9b23-5eacd601f96e
ms.openlocfilehash: 83d6fc1294f6aa37389db9e517b02866ef000b50
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854221"
---
# <a name="working-with-data-definition-language"></a><span data-ttu-id="8f04a-102">Práce s jazykem DDL (Data Description Language)</span><span class="sxs-lookup"><span data-stu-id="8f04a-102">Working with Data Definition Language</span></span>
<span data-ttu-id="8f04a-103">Počínaje verzí .NET Framework 4 podporuje Entity Framework jazyk DDL (Data Definition Language).</span><span class="sxs-lookup"><span data-stu-id="8f04a-103">Starting with the .NET Framework version 4, the Entity Framework supports data definition language (DDL).</span></span> <span data-ttu-id="8f04a-104">To vám umožní vytvořit nebo odstranit instanci databáze založenou na připojovacím řetězci a metadatech modelu úložiště (SSDL).</span><span class="sxs-lookup"><span data-stu-id="8f04a-104">This allows you to create or delete a database instance based on the connection string and the metadata of the storage (SSDL) model.</span></span>  
  
 <span data-ttu-id="8f04a-105">Následující metody pro <xref:System.Data.Objects.ObjectContext> použití připojovacího řetězce a obsahu SSDL k provedení následujících akcí: vytvořit nebo odstranit databázi, ověřit, zda databáze existuje, a zobrazit generovaný skript DDL:</span><span class="sxs-lookup"><span data-stu-id="8f04a-105">The following methods on the <xref:System.Data.Objects.ObjectContext> use the connection string and the SSDL content to accomplish the following: create or delete the database, check whether the database exists, and view the generated DDL script:</span></span>  
  
- <xref:System.Data.Objects.ObjectContext.CreateDatabase%2A>  
  
- <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A>  
  
- <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A>  
  
- <xref:System.Data.Objects.ObjectContext.CreateDatabaseScript%2A>  
  
> [!NOTE]
> <span data-ttu-id="8f04a-106">Spuštění příkazů DDL předpokládá dostatečná oprávnění.</span><span class="sxs-lookup"><span data-stu-id="8f04a-106">Executing the DDL commands assumes sufficient permissions.</span></span>  
  
 <span data-ttu-id="8f04a-107">Výše uvedené metody přenesly většinu práce na základního poskytovatele dat ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="8f04a-107">The methods previously listed delegate most of the work to the underlying ADO.NET data provider.</span></span> <span data-ttu-id="8f04a-108">Je zodpovědností poskytovatele, aby bylo zajištěno, že konvence vytváření názvů používané pro generování databázových objektů je konzistentní s konvencemi použitými pro dotazování a aktualizace.</span><span class="sxs-lookup"><span data-stu-id="8f04a-108">It is the provider’s responsibility to ensure that the naming convention used to generate database objects is consistent with conventions used for querying and updates.</span></span>  
  
 <span data-ttu-id="8f04a-109">Následující příklad ukazuje, jak vygenerovat databázi na základě existujícího modelu.</span><span class="sxs-lookup"><span data-stu-id="8f04a-109">The following example shows you how to generate the database based on the existing model.</span></span> <span data-ttu-id="8f04a-110">Také přidá nový objekt entity do kontextu objektu a uloží jej do databáze.</span><span class="sxs-lookup"><span data-stu-id="8f04a-110">It also adds a new entity object to the object context and then saves it to the database.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="8f04a-111">Procedury</span><span class="sxs-lookup"><span data-stu-id="8f04a-111">Procedures</span></span>  
  
### <a name="to-define-a-database-based-on-the-existing-model"></a><span data-ttu-id="8f04a-112">Definování databáze na základě existujícího modelu</span><span class="sxs-lookup"><span data-stu-id="8f04a-112">To define a database based on the existing model</span></span>  
  
1. <span data-ttu-id="8f04a-113">Vytvořte konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8f04a-113">Create a console application.</span></span>  
  
2. <span data-ttu-id="8f04a-114">Přidejte do své aplikace existující model.</span><span class="sxs-lookup"><span data-stu-id="8f04a-114">Add an existing model to your application.</span></span>  
  
    1. <span data-ttu-id="8f04a-115">Přidejte prázdný model s názvem `SchoolModel`.</span><span class="sxs-lookup"><span data-stu-id="8f04a-115">Add an empty model named `SchoolModel`.</span></span> <span data-ttu-id="8f04a-116">Chcete-li vytvořit prázdný model, přečtěte si téma [postupy: Vytvoří nový soubor](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100)) . edmx.</span><span class="sxs-lookup"><span data-stu-id="8f04a-116">To create an empty model, see the [How to: Create a New .edmx File](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100)) topic.</span></span>  
  
     <span data-ttu-id="8f04a-117">Do projektu se přidá soubor SchoolModel. edmx.</span><span class="sxs-lookup"><span data-stu-id="8f04a-117">The SchoolModel.edmx file is added to your project.</span></span>  
  
    1. <span data-ttu-id="8f04a-118">Zkopírujte obsah koncepčního, úložiště a mapování pro školní model z tématu [školní model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) .</span><span class="sxs-lookup"><span data-stu-id="8f04a-118">Copy the conceptual, storage, and mapping content for the School model from the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) topic.</span></span>  
  
    2. <span data-ttu-id="8f04a-119">Otevřete soubor SchoolModel. edmx a vložte obsah do `edmx:Runtime` značek.</span><span class="sxs-lookup"><span data-stu-id="8f04a-119">Open the SchoolModel.edmx file and paste the content within the `edmx:Runtime` tags.</span></span>  
  
3. <span data-ttu-id="8f04a-120">Do funkce Main přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="8f04a-120">Add the following code to your main function.</span></span> <span data-ttu-id="8f04a-121">Kód inicializuje připojovací řetězec k vašemu databázovému serveru, zobrazí skript DDL, vytvoří databázi, přidá novou entitu do kontextu a uloží změny do databáze.</span><span class="sxs-lookup"><span data-stu-id="8f04a-121">The code initializes the connection string to your database server, views the DDL script, creates the database, adds a new entity to the context, and saves the changes to the database.</span></span>  
  
     [!code-csharp[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/csharp/VS_Snippets_Data/DP ObjectServices Concepts/CS/Source.cs#ddl)]
     [!code-vb[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP ObjectServices Concepts/VB/Source.vb#ddl)]
