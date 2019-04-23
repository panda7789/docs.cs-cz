---
ms.openlocfilehash: 566a3e0455b30e901b09be88b4256ffe67bdc2b5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981720"
---
### <a name="workflow-sql-persistence-adds-primary-key-clusters-and-disallows-null-values-in-some-columns"></a>Trvalost pracovního postupu SQL přidá primární klíč clusterů a nepovoluje hodnoty null v některé sloupce

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.7, tabulky vytvořené pro SQL pracovního postupu Instance Store (SWIS) skriptem SqlWorkflowInstanceStoreSchema.sql používat clusterovaný primární klíče. Z toho důvodu se nepodporují identity <code>null</code> hodnoty. Operace SWIS neovlivní tato změna. Aktualizace byly provedeny na podporu transakční replikace systému SQL Server.|
|Doporučení|Pokud chcete vyzkoušet tuto změnu se musí použít soubor SQL SqlWorkflowInstanceStoreSchemaUpgrade.sql stávajících zařízení. Nové instalace databáze automaticky budou mít změny.|
|Rozsah|Edge|
|Version|4.7|
|Type|Modul runtime|
