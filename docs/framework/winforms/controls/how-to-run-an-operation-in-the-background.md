---
title: 'Postupy: Spuštění operace na pozadí'
description: Naučte se používat třídu BackgroundWorker ke spuštění časově náročného model Windows Forms operace na pozadí.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- background tasks
- forms [Windows Forms], multithreading
- forms [Windows Forms], background operations
- background threads
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], background operations
- background operations
ms.assetid: 5b56e2aa-dc05-444f-930c-2d7b23f9ad5b
ms.openlocfilehash: 6b2a97f5acf1e906dfe141aee62e99a4e50dca9f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621571"
---
# <a name="how-to-run-an-operation-in-the-background"></a>Postupy: Spuštění operace na pozadí
Pokud máte operaci, která bude trvat dlouhou dobu, a nechcete ve svém uživatelském rozhraní způsobovat prodlevy, můžete použít <xref:System.ComponentModel.BackgroundWorker> třídu ke spuštění operace v jiném vlákně.  
  
 Následující příklad kódu ukazuje, jak spustit časově náročnou operaci na pozadí. Formulář obsahuje tlačítka **Spustit** a **Storno** . Kliknutím na tlačítko **Spustit** spusťte asynchronní operaci. Kliknutím na tlačítko **Storno** zastavíte spuštěnou asynchronní operaci. Výsledek každé operace se zobrazí v <xref:System.Windows.Forms.MessageBox> .  
  
 Existuje Rozsáhlá podpora pro tento úkol v aplikaci Visual Studio.  
  
 Viz také [Návod: spuštění operace na pozadí](walkthrough-running-an-operation-in-the-background.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.ComponentModel.BackgroundWorker.Example#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.Example#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System, System. Drawing a System. Windows. Forms.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [Postupy: Implementace formuláře, který používá operaci na pozadí](how-to-implement-a-form-that-uses-a-background-operation.md)
- [Komponenta BackgroundWorker](backgroundworker-component.md)
