---
ms.openlocfilehash: 566a3e0455b30e901b09be88b4256ffe67bdc2b5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61664902"
---
### <a name="workflow-sql-persistence-adds-primary-key-clusters-and-disallows-null-values-in-some-columns"></a><span data-ttu-id="c296f-101">Trvalost pracovního postupu SQL přidá primární klíč clusterů a nepovoluje hodnoty null v některé sloupce</span><span class="sxs-lookup"><span data-stu-id="c296f-101">Workflow SQL persistence adds primary key clusters and disallows null values in some columns</span></span>

|   |   |
|---|---|
|<span data-ttu-id="c296f-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="c296f-102">Details</span></span>|<span data-ttu-id="c296f-103">Od verze rozhraní .NET Framework 4.7, tabulky vytvořené pro SQL pracovního postupu Instance Store (SWIS) skriptem SqlWorkflowInstanceStoreSchema.sql používat clusterovaný primární klíče.</span><span class="sxs-lookup"><span data-stu-id="c296f-103">Starting with the .NET Framework 4.7, the tables created for the SQL Workflow Instance Store (SWIS) by the SqlWorkflowInstanceStoreSchema.sql script use clustered primary keys.</span></span> <span data-ttu-id="c296f-104">Z toho důvodu se nepodporují identity <code>null</code> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c296f-104">Because of this, identities do not support <code>null</code> values.</span></span> <span data-ttu-id="c296f-105">Operace SWIS neovlivní tato změna.</span><span class="sxs-lookup"><span data-stu-id="c296f-105">The operation of SWIS is not impacted by this change.</span></span> <span data-ttu-id="c296f-106">Aktualizace byly provedeny na podporu transakční replikace systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c296f-106">The updates were made to support SQL Server Transactional Replication.</span></span>|
|<span data-ttu-id="c296f-107">Doporučení</span><span class="sxs-lookup"><span data-stu-id="c296f-107">Suggestion</span></span>|<span data-ttu-id="c296f-108">Pokud chcete vyzkoušet tuto změnu se musí použít soubor SQL SqlWorkflowInstanceStoreSchemaUpgrade.sql stávajících zařízení.</span><span class="sxs-lookup"><span data-stu-id="c296f-108">The SQL file SqlWorkflowInstanceStoreSchemaUpgrade.sql must be applied to existing installations in order to experience this change.</span></span> <span data-ttu-id="c296f-109">Nové instalace databáze automaticky budou mít změny.</span><span class="sxs-lookup"><span data-stu-id="c296f-109">New database installations will automatically have the change.</span></span>|
|<span data-ttu-id="c296f-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="c296f-110">Scope</span></span>|<span data-ttu-id="c296f-111">Edge</span><span class="sxs-lookup"><span data-stu-id="c296f-111">Edge</span></span>|
|<span data-ttu-id="c296f-112">Version</span><span class="sxs-lookup"><span data-stu-id="c296f-112">Version</span></span>|<span data-ttu-id="c296f-113">4.7</span><span class="sxs-lookup"><span data-stu-id="c296f-113">4.7</span></span>|
|<span data-ttu-id="c296f-114">Type</span><span class="sxs-lookup"><span data-stu-id="c296f-114">Type</span></span>|<span data-ttu-id="c296f-115">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="c296f-115">Runtime</span></span>|
