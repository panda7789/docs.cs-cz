---
ms.openlocfilehash: 809ca85b347fabc44573e2e0c5a43261d68590d3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621103"
---
### <a name="workflow-sql-persistence-adds-primary-key-clusters-and-disallows-null-values-in-some-columns"></a>Trvalost pracovního postupu SQL přidává clustery primárního klíče a v některých sloupcích nepovoluje hodnoty null.

#### <a name="details"></a>Podrobnosti

Počínaje .NET Framework 4,7 jsou tabulky vytvořené pro úložiště instancí SQL pracovního postupu (SWIS) pomocí skriptu SqlWorkflowInstanceStoreSchema. SQL, který používá clusterované primární klíče. Z tohoto důvodu identity nepodporují <code>null</code> hodnoty. Tato změna nemá vliv na operaci SWIS. Aktualizace byly provedeny pro podporu SQL Server transakční replikace.

#### <a name="suggestion"></a>Návrh

Pro tuto změnu je nutné použít soubor SQL SqlWorkflowInstanceStoreSchemaUpgrade. SQL pro existující instalace. Nové instalace databáze budou automaticky mít změnu.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4,7|
|Typ|Modul runtime|
