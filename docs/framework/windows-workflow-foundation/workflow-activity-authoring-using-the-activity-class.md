---
title: Vytváření aktivit pracovního postupu pomocí třídy Activity
ms.date: 03/30/2017
ms.assetid: 7b7b1c66-f093-43c3-b4d1-7173b46516da
ms.openlocfilehash: 1bec10b6ae9fb43319cfb6acbf59133e1acca09c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755503"
---
# <a name="workflow-activity-authoring-using-the-activity-class"></a>Vytváření aktivit pracovního postupu pomocí třídy Activity
Základní způsob, jak vytvořit aktivity pomocí Windows Workflow Foundation (WF) v [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] je vytvořit třídu, která dědí z <xref:System.Activities.Activity> , který vytvoří funkce sestavte vlastní aktivity nebo aktivity [integrované Knihovna aktivit](net-framework-4-5-built-in-activity-library.md). Toto téma ukazuje, jak vytvořit aktivitu, která zapisuje dvě zprávy do konzoly.

### <a name="to-create-a-custom-activity-using-the-activity-designer"></a>Chcete-li vytvořit vlastní aktivitu pomocí návrháře aktivit

1. Open Visual Studio 2012.

2. Vyberte soubor, nový, projekt. Vyberte **Workflow 4.0** pod **Visual C#** v **typy projektů** okna a vyberte **v2010** uzlu. Vyberte **knihovny aktivit** v **šablony** okna. Název nového projektu HelloActivity.

3. Otevřete novou aktivitu.  Přetáhněte <xref:System.Activities.Statements.Sequence> aktivitu z panelu nástrojů na plochu návrháře.

4. Přetáhněte <xref:System.Activities.Statements.WriteLine> aktivitu <xref:System.Activities.Statements.Sequence> aktivity. Zadejte `"Hello World"` (pomocí nabídky) do **Text** pole.

5. Přetáhněte druhý <xref:System.Activities.Statements.WriteLine> aktivitu <xref:System.Activities.Statements.Sequence> aktivitu pod první z nich. Zadejte `"Goodbye"` (pomocí nabídky) do **Text** pole.
