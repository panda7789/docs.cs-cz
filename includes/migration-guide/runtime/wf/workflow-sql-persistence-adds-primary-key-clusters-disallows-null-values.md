---
ms.openlocfilehash: 566a3e0455b30e901b09be88b4256ffe67bdc2b5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236201"
---
### <a name="workflow-sql-persistence-adds-primary-key-clusters-and-disallows-null-values-in-some-columns"></a><span data-ttu-id="d2031-101">Trvalost pracovního postupu SQL přidá primární klíč clusterů a nepovoluje hodnoty null v některé sloupce</span><span class="sxs-lookup"><span data-stu-id="d2031-101">Workflow SQL persistence adds primary key clusters and disallows null values in some columns</span></span>

|   |   |
|---|---|
|<span data-ttu-id="d2031-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="d2031-102">Details</span></span>|<span data-ttu-id="d2031-103">Od verze rozhraní .NET Framework 4.7, tabulky vytvořené pro SQL pracovního postupu Instance Store (SWIS) skriptem SqlWorkflowInstanceStoreSchema.sql používat clusterovaný primární klíče.</span><span class="sxs-lookup"><span data-stu-id="d2031-103">Starting with the .NET Framework 4.7, the tables created for the SQL Workflow Instance Store (SWIS) by the SqlWorkflowInstanceStoreSchema.sql script use clustered primary keys.</span></span> <span data-ttu-id="d2031-104">Z toho důvodu se nepodporují identity <code>null</code> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d2031-104">Because of this, identities do not support <code>null</code> values.</span></span> <span data-ttu-id="d2031-105">Operace SWIS neovlivní tato změna.</span><span class="sxs-lookup"><span data-stu-id="d2031-105">The operation of SWIS is not impacted by this change.</span></span> <span data-ttu-id="d2031-106">Aktualizace byly provedeny na podporu transakční replikace systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d2031-106">The updates were made to support SQL Server Transactional Replication.</span></span>|
|<span data-ttu-id="d2031-107">Doporučení</span><span class="sxs-lookup"><span data-stu-id="d2031-107">Suggestion</span></span>|<span data-ttu-id="d2031-108">Pokud chcete vyzkoušet tuto změnu se musí použít soubor SQL SqlWorkflowInstanceStoreSchemaUpgrade.sql stávajících zařízení.</span><span class="sxs-lookup"><span data-stu-id="d2031-108">The SQL file SqlWorkflowInstanceStoreSchemaUpgrade.sql must be applied to existing installations in order to experience this change.</span></span> <span data-ttu-id="d2031-109">Nové instalace databáze automaticky budou mít změny.</span><span class="sxs-lookup"><span data-stu-id="d2031-109">New database installations will automatically have the change.</span></span>|
|<span data-ttu-id="d2031-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="d2031-110">Scope</span></span>|<span data-ttu-id="d2031-111">Edge</span><span class="sxs-lookup"><span data-stu-id="d2031-111">Edge</span></span>|
|<span data-ttu-id="d2031-112">Version</span><span class="sxs-lookup"><span data-stu-id="d2031-112">Version</span></span>|<span data-ttu-id="d2031-113">4.7</span><span class="sxs-lookup"><span data-stu-id="d2031-113">4.7</span></span>|
|<span data-ttu-id="d2031-114">Type</span><span class="sxs-lookup"><span data-stu-id="d2031-114">Type</span></span>|<span data-ttu-id="d2031-115">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="d2031-115">Runtime</span></span>|
