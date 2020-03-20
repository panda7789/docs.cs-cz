---
ms.openlocfilehash: 566a3e0455b30e901b09be88b4256ffe67bdc2b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802511"
---
### <a name="workflow-sql-persistence-adds-primary-key-clusters-and-disallows-null-values-in-some-columns"></a><span data-ttu-id="92dd9-101">Trvalosti SQL pracovního postupu přidá clustery primárního klíče a v některých sloupcích zakáže hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="92dd9-101">Workflow SQL persistence adds primary key clusters and disallows null values in some columns</span></span>

|   |   |
|---|---|
|<span data-ttu-id="92dd9-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="92dd9-102">Details</span></span>|<span data-ttu-id="92dd9-103">Počínaje rozhraním .NET Framework 4.7 používají tabulky vytvořené pro úložiště instancí pracovního postupu SQL (SWIS) skriptem SqlWorkflowInstanceStoreSchema.sql primární klíče.</span><span class="sxs-lookup"><span data-stu-id="92dd9-103">Starting with the .NET Framework 4.7, the tables created for the SQL Workflow Instance Store (SWIS) by the SqlWorkflowInstanceStoreSchema.sql script use clustered primary keys.</span></span> <span data-ttu-id="92dd9-104">Z tohoto důvodu identity <code>null</code> nepodporují hodnoty.</span><span class="sxs-lookup"><span data-stu-id="92dd9-104">Because of this, identities do not support <code>null</code> values.</span></span> <span data-ttu-id="92dd9-105">Provoz SWIS není touto změnou ovlivněn.</span><span class="sxs-lookup"><span data-stu-id="92dd9-105">The operation of SWIS is not impacted by this change.</span></span> <span data-ttu-id="92dd9-106">Aktualizace byly provedeny pro podporu transakční replikace serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="92dd9-106">The updates were made to support SQL Server Transactional Replication.</span></span>|
|<span data-ttu-id="92dd9-107">Návrh</span><span class="sxs-lookup"><span data-stu-id="92dd9-107">Suggestion</span></span>|<span data-ttu-id="92dd9-108">Aby bylo možné tuto změnu provést, musí být soubor SQL SqlWorkflowInstanceStoreSchemaUpgrade.sql použit pro existující instalace.</span><span class="sxs-lookup"><span data-stu-id="92dd9-108">The SQL file SqlWorkflowInstanceStoreSchemaUpgrade.sql must be applied to existing installations in order to experience this change.</span></span> <span data-ttu-id="92dd9-109">Nové instalace databáze budou mít automaticky změnu.</span><span class="sxs-lookup"><span data-stu-id="92dd9-109">New database installations will automatically have the change.</span></span>|
|<span data-ttu-id="92dd9-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="92dd9-110">Scope</span></span>|<span data-ttu-id="92dd9-111">Edge</span><span class="sxs-lookup"><span data-stu-id="92dd9-111">Edge</span></span>|
|<span data-ttu-id="92dd9-112">Version</span><span class="sxs-lookup"><span data-stu-id="92dd9-112">Version</span></span>|<span data-ttu-id="92dd9-113">4.7</span><span class="sxs-lookup"><span data-stu-id="92dd9-113">4.7</span></span>|
|<span data-ttu-id="92dd9-114">Typ</span><span class="sxs-lookup"><span data-stu-id="92dd9-114">Type</span></span>|<span data-ttu-id="92dd9-115">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="92dd9-115">Runtime</span></span>|
