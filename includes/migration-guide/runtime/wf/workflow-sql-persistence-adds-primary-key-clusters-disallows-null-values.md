---
ms.openlocfilehash: 809ca85b347fabc44573e2e0c5a43261d68590d3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621103"
---
### <a name="workflow-sql-persistence-adds-primary-key-clusters-and-disallows-null-values-in-some-columns"></a><span data-ttu-id="505de-101">Trvalost pracovního postupu SQL přidává clustery primárního klíče a v některých sloupcích nepovoluje hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="505de-101">Workflow SQL persistence adds primary key clusters and disallows null values in some columns</span></span>

#### <a name="details"></a><span data-ttu-id="505de-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="505de-102">Details</span></span>

<span data-ttu-id="505de-103">Počínaje .NET Framework 4,7 jsou tabulky vytvořené pro úložiště instancí SQL pracovního postupu (SWIS) pomocí skriptu SqlWorkflowInstanceStoreSchema. SQL, který používá clusterované primární klíče.</span><span class="sxs-lookup"><span data-stu-id="505de-103">Starting with the .NET Framework 4.7, the tables created for the SQL Workflow Instance Store (SWIS) by the SqlWorkflowInstanceStoreSchema.sql script use clustered primary keys.</span></span> <span data-ttu-id="505de-104">Z tohoto důvodu identity nepodporují <code>null</code> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="505de-104">Because of this, identities do not support <code>null</code> values.</span></span> <span data-ttu-id="505de-105">Tato změna nemá vliv na operaci SWIS.</span><span class="sxs-lookup"><span data-stu-id="505de-105">The operation of SWIS is not impacted by this change.</span></span> <span data-ttu-id="505de-106">Aktualizace byly provedeny pro podporu SQL Server transakční replikace.</span><span class="sxs-lookup"><span data-stu-id="505de-106">The updates were made to support SQL Server Transactional Replication.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="505de-107">Návrh</span><span class="sxs-lookup"><span data-stu-id="505de-107">Suggestion</span></span>

<span data-ttu-id="505de-108">Pro tuto změnu je nutné použít soubor SQL SqlWorkflowInstanceStoreSchemaUpgrade. SQL pro existující instalace.</span><span class="sxs-lookup"><span data-stu-id="505de-108">The SQL file SqlWorkflowInstanceStoreSchemaUpgrade.sql must be applied to existing installations in order to experience this change.</span></span> <span data-ttu-id="505de-109">Nové instalace databáze budou automaticky mít změnu.</span><span class="sxs-lookup"><span data-stu-id="505de-109">New database installations will automatically have the change.</span></span>

| <span data-ttu-id="505de-110">Name</span><span class="sxs-lookup"><span data-stu-id="505de-110">Name</span></span>    | <span data-ttu-id="505de-111">Hodnota</span><span class="sxs-lookup"><span data-stu-id="505de-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="505de-112">Rozsah</span><span class="sxs-lookup"><span data-stu-id="505de-112">Scope</span></span>   |<span data-ttu-id="505de-113">Edge</span><span class="sxs-lookup"><span data-stu-id="505de-113">Edge</span></span>|
|<span data-ttu-id="505de-114">Verze</span><span class="sxs-lookup"><span data-stu-id="505de-114">Version</span></span>|<span data-ttu-id="505de-115">4,7</span><span class="sxs-lookup"><span data-stu-id="505de-115">4.7</span></span>|
|<span data-ttu-id="505de-116">Typ</span><span class="sxs-lookup"><span data-stu-id="505de-116">Type</span></span>|<span data-ttu-id="505de-117">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="505de-117">Runtime</span></span>|
